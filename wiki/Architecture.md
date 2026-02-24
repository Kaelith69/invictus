# Architecture

This page provides a deep technical breakdown of the Invictus system architecture, component design, threading model, and internal data structures.

---

## 🏗️ High-Level Overview

Invictus is structured around two primary classes:

| Class | File | Responsibility |
|---|---|---|
| `LieDetectorApp` | `invictus.py` | GUI presentation layer, user interactions, threading orchestration |
| `EnhancedLieDetector` | `invictus.py` | All detection logic: landmark extraction, metric calculation, ML inference |

These two classes communicate through a shared lock and the standard Tkinter `after()` event scheduling mechanism.

---

## 🧩 Layer Breakdown

### Layer 1 — Presentation (LieDetectorApp)

The GUI is built with **Tkinter** (`ttk` themed widgets) and laid out in a two-panel design:

```
LieDetectorApp (root: Tk, 1280×720)
│
├── main_frame (ttk.Frame)
│   ├── left_panel
│   │   ├── video_frame       ← ttk.LabelFrame, contains video_label (ttk.Label)
│   │   ├── control_frame     ← ttk.LabelFrame
│   │   │   ├── btn_frame     ← Start/Baseline/Analysis/Stop/Save buttons
│   │   │   ├── settings_frame← Duration, Sensitivity, Question inputs
│   │   │   └── progress_bar  ← ttk.Progressbar (linked to progress_var DoubleVar)
│   │   └── (status_bar at root bottom)
│   │
│   └── right_panel
│       ├── metrics_frame     ← Real-time EAR, Asymmetry, Blink, Emotion, Deception labels
│       ├── graph_frame       ← FigureCanvasTkAgg (2-subplot matplotlib figure)
│       └── results_frame     ← tk.Text for post-analysis summary
│
└── status_bar (ttk.Label at root bottom)
```

**Key Tkinter patterns used:**
- `tk.StringVar` / `tk.DoubleVar` — reactive data binding to labels
- `root.after(30, ...)` — periodic GUI refresh (approx. 33Hz)
- `root.protocol("WM_DELETE_WINDOW", app.cleanup)` — graceful shutdown hook

---

### Layer 2 — Concurrency (Background Video Thread)

Video capture and frame processing run in a **daemon thread** to avoid blocking the GUI event loop.

```python
self.video_thread = threading.Thread(target=self._video_loop, daemon=True)
self.video_thread.start()
```

**Thread safety:** All shared state (display frame, current metrics dict, analysis state) is protected by `self._lock = threading.Lock()`. The GUI thread reads these values only inside `with self._lock:` blocks.

**Communication model:**

```
Video Thread                     GUI Thread (main loop)
────────────                     ──────────────────────
Capture frame                    root.after(30, update_gui)
  → process metrics                 with lock: read latest_frame
  → with lock: write state            → update labels
  → continue loop                     → redraw matplotlib canvas
```

**Frame buffer:** `self.frame_data = deque(maxlen=MAX_FRAMES)` provides bounded storage (10,000 frames max) for post-analysis statistics. When full, oldest entries are automatically evicted.

---

### Layer 3 — Detection Engine (EnhancedLieDetector)

All biometric analysis is encapsulated in `EnhancedLieDetector`. It is instantiated once and reused across sessions.

```
EnhancedLieDetector
│
├── mp.solutions.face_mesh.FaceMesh        ← MediaPipe FaceMesh instance
│   └── process(rgb_frame) → 468 landmarks
│
├── FER(mtcnn=False)                       ← FER emotion classifier
│   └── detect_emotions(rgb_frame)
│
├── RandomForestClassifier (sklearn)       ← Pre-fitted with synthetic data
│   └── predict_proba(feature_vector)
│
├── State
│   ├── baseline: dict                     ← Stored after 10s calibration
│   ├── blink_times: list                  ← Timestamps for 60s rolling rate
│   ├── blink_counter: int                 ← Edge-trigger state
│   ├── last_blink_time: float
│   ├── eye_movement_history: deque        ← (left_center, right_center) tuples
│   ├── landmark_history: deque            ← Recent frames of 468-point lists
│   └── microexpression_window: int        ← Frames to check (default 5)
│
└── Configuration
    ├── sensitivity: float (0.1–1.0)
    └── blink_threshold: float             ← Set to 0.7 × baseline EAR
```

---

## 🔬 Component Deep Dives

### MediaPipe FaceMesh Integration

```python
mp_face_mesh = mp.solutions.face_mesh
self.face_mesh = mp_face_mesh.FaceMesh(
    max_num_faces=1,
    refine_landmarks=True,
    min_detection_confidence=0.5,
    min_tracking_confidence=0.5
)
```

Frames are:
1. Captured by OpenCV (`cv2.VideoCapture`)
2. Scaled by `FRAME_SCALE = 0.5` for performance
3. Converted `BGR → RGB` before passing to MediaPipe
4. Processed to yield normalized landmark coordinates `(x, y, z)` in `[0.0, 1.0]`
5. Multiplied by frame dimensions `(w, h)` to get pixel coordinates

**Landmark indices used:**

| Feature | Indices |
|---|---|
| Left eye (EAR) | 33, 160, 158, 133, 153, 144 |
| Right eye (EAR) | 362, 385, 387, 263, 373, 380 |
| Nose tip | 1 |
| Left cheek | 234 |
| Right cheek | 454 |

---

### EAR Calculation

```python
def calculate_eye_aspect_ratio(self, eye):  # eye = list of 6 (x, y) tuples
    v1 = ||eye[1] - eye[5]||  # vertical distance 1
    v2 = ||eye[2] - eye[4]||  # vertical distance 2
    h  = ||eye[0] - eye[3]||  # horizontal distance
    return (v1 + v2) / (2.0 * h)
```

Final EAR = mean of left and right EAR.

Blink threshold = `0.7 × baseline_EAR`, set after calibration.

---

### Blink Detection (Edge-Triggered)

```python
if ear < blink_threshold:
    blink_counter += 1
    if blink_counter == 2 and (now - last_blink_time) > BLINK_MIN_DURATION:
        blink_times.append(now)   # Record blink event
        last_blink_time = now
else:
    blink_counter = 0             # Reset when eye opens
```

- **Edge trigger**: blink is recorded exactly once (at `counter == 2`)
- **Debounce**: `BLINK_MIN_DURATION = 0.1s` prevents double-counting
- **Rolling rate**: `blink_rate = len([t for t in blink_times if now - t < 60])`

---

### Facial Asymmetry

```python
nose = points[1]
left_cheek = points[234]
right_cheek = points[454]
left_dist = ||nose - left_cheek||
right_dist = ||nose - right_cheek||
asymmetry = |left_dist - right_dist| / max(left_dist, right_dist)
```

Returns a value in `[0, 1]`. A perfectly symmetric face scores `0.0`.

---

### Microexpression Detection

```python
for i in range(1, len(landmark_history)):
    velocity = sum(||p1 - p2|| for p1, p2 in zip(prev_frame, curr_frame))
    velocities.append(velocity)

if max(velocities) > mean(velocities) * 2 * sensitivity:
    return "Sudden Movement"
```

Uses a deque of recent frames (default 5-frame window) for velocity calculation.

---

### Emotion Detection (FER)

```python
result = self.emotion_detector.detect_emotions(rgb_frame)
# result = [{'box': [...], 'emotions': {'angry': 0.1, 'fear': 0.05, ...}}]
dominant = max(emotions, key=emotions.get)
```

**Emotion weights** (applied to deception score):

| Emotion | Weight |
|---|---|
| fear | +0.4 |
| surprise | +0.3 |
| angry | +0.2 |
| disgust | +0.2 |
| sad | +0.1 |
| neutral | 0.0 |
| happy | -0.1 |

---

### Random Forest Classifier

**Feature vector (5 features):**

```python
features = [
    ear_dev,          # |EAR - baseline_EAR| / baseline_EAR
    asymmetry_score,  # asymmetry / (baseline_asymmetry + 0.1)
    blink_dev,        # |blink_rate - baseline_blink| / baseline_blink
    movement_score,   # eye_center_mean_displacement / 10.0
    emotion_score     # from emotion_weights dict
]
```

**Training:**
The model is fitted on synthetic data at startup using `RandomForestClassifier.fit()`. The synthetic dataset uses normally distributed samples with class separation to produce a usable probability estimator.

> **Production note:** Real-world accuracy would require a validated biometric dataset. The synthetic training data is a placeholder.

**Inference:**
```python
prob = model.predict_proba([features])[0][1]  # probability of class 1 (deceptive)
result = min(max(prob * 100 * sensitivity, 0.0), 100.0)
```

---

## 🔄 Calibration (Baseline Capture)

The baseline process:

1. User clicks "Capture Baseline"
2. `is_capturing_baseline = True`, progress bar animates
3. For `BASELINE_DURATION = 10` seconds, each processed frame's metrics are appended to `baseline_data[]`
4. After completion:
   - Outlier filtering (frames with EAR = 0 excluded)
   - Baseline dict computed as column means:
     - `baseline['eye_aspect_ratio']` = mean EAR
     - `baseline['facial_asymmetry']` = mean asymmetry
     - `baseline['blink_rate']` = mean blink rate
   - `blink_threshold = 0.7 × baseline_EAR`

---

## 📊 Graph Rendering

Two matplotlib subplots are embedded in the Tkinter GUI via `FigureCanvasTkAgg`:

- **Axes 0 (top):** Deception probability % over time
- **Axes 1 (bottom):** Normalized EAR, facial asymmetry, blink rate over time

Graphs update every ~30ms via `root.after()` by calling `canvas.draw_idle()`.

---

## 🧵 Shutdown Sequence

```
User closes window
  → root.protocol("WM_DELETE_WINDOW", app.cleanup)
  → app.cleanup():
      self.running = False          # Signal video thread to exit
      self.cap.release()            # Release OpenCV capture
      self.root.destroy()           # Destroy Tkinter window
```

The video thread checks `self.running` each iteration and exits its loop when it becomes `False`.
