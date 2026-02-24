# Usage

This page provides a detailed walkthrough of the Invictus application workflow, tips for best results, and an explanation of all outputs.

---

## ⚠️ Important Disclaimer

> This tool is for **research and educational purposes only**. Lie detection based on facial analysis is **not scientifically validated** and produces probabilistic estimates only. Do **not** use this tool in legal, professional, clinical, HR, or any high-stakes context. Results are experimental.

---

## 🚀 Starting the Application

```bash
python invictus.py
```

On launch:
1. The application window opens at **1280×720** (resizable).
2. A **disclaimer dialog** appears — click OK to proceed.
3. All control buttons except "Start Camera" and "Save Results" are initially disabled.

---

## 📋 Full Workflow

### Step 1 — Start Camera

Click **"Start Camera"**.

- OpenCV opens the default webcam (`/dev/video0` on Linux, index 0 on Windows/macOS).
- The live feed appears in the left video panel (640×480 display).
- The **"Capture Baseline"** button becomes active.
- Status bar shows: `Camera started`.

**Tips:**
- Position yourself **40–80 cm** from the camera.
- Ensure **even, frontal lighting** — avoid strong shadows or backlighting.
- Remove objects that obscure your face (scarves, sunglasses, etc.).

If the camera doesn't open, try changing the source:
```python
# In invictus.py, line: self.video_source = 0
self.video_source = 1  # Try index 1 for external webcam
```

---

### Step 2 — Capture Baseline

Click **"Capture Baseline"**.

- Maintain a **neutral, relaxed expression** for **10 seconds**.
- The progress bar fills as the baseline is captured.
- Status bar shows: `Capturing baseline...` → `Baseline captured successfully`.
- The **"Start Analysis"** button becomes active.

**What the baseline captures:**

| Metric | Description |
|---|---|
| `eye_aspect_ratio` | Mean EAR across all baseline frames |
| `facial_asymmetry` | Mean asymmetry score |
| `blink_rate` | Mean blink rate (blinks/minute) |

The baseline also sets `blink_threshold = 0.7 × baseline_EAR`.

**Why this matters:** All deception scores are computed as *deviations from your personal baseline*. A poor-quality baseline (expressions, movement, bad lighting) will produce inaccurate scores throughout the session.

**Recapturing:** Click "Capture Baseline" again at any time to recalibrate.

---

### Step 3 — Configure Settings

In the **Settings** panel:

| Setting | Range | Default | Description |
|---|---|---|---|
| Recording Duration | 5–300 s | 30 s | Duration of the analysis session |
| Sensitivity | 0.1–1.0 | 0.7 | Scales the output deception probability |
| Question | Text | (empty) | Optional label for the session (saved in report) |

**Sensitivity guide:**
- `0.1` — Very conservative; only extreme signals score highly
- `0.5` — Balanced
- `0.7` (default) — Slightly elevated sensitivity
- `1.0` — Maximum sensitivity; small deviations score higher

---

### Step 4 — Start Analysis

Click **"Start Analysis"**.

- The system begins recording and scoring each frame.
- Real-time metrics update in the right panel approximately every 30ms.
- Graphs update live.
- The progress bar shows elapsed time vs. recording duration.
- Analysis stops automatically when the duration expires, or when you click **"Stop"**.

---

### Step 5 — Monitor Real-Time Metrics

The **Real-time Metrics** panel (top-right) shows:

| Metric | Description |
|---|---|
| **Eye Movement (EAR)** | Current Eye Aspect Ratio (higher = more open) |
| **Microexpressions** | "None" or "Sudden Movement" if velocity threshold exceeded |
| **Facial Asymmetry** | Current asymmetry score (0.0 = perfectly symmetric) |
| **Dominant Emotion** | Most likely emotion detected this frame |
| **Blink Rate** | Blinks per minute (rolling 60-second window) |
| **Deception Probability** | Current estimate in % (bold) |

The **Real-time Analysis** graph panel shows:
- **Top subplot:** Deception Probability % over time
- **Bottom subplot:** Normalized EAR, Asymmetry, and Blink Rate over time

---

### Step 6 — Review Post-Analysis Results

After analysis completes, the **Analysis Results** text box shows:

```
Average Deception Probability: XX.X%
Max Deception Probability: XX.X%
Average Blink Rate: XX.X bpm
Average Eye Aspect Ratio: X.XXX
Average Facial Asymmetry: X.XXX
Most Common Emotion: Neutral
Microexpression Events: N
```

> Interpret these values relative to your baseline and environmental conditions. A high deception score in isolation is not meaningful.

---

### Step 7 — Save Results

Click **"Save Results"**.

Two files are written to the **current working directory**:

#### `results.csv`

Per-frame data with columns:

| Column | Type | Description |
|---|---|---|
| `timestamp` | float | Unix timestamp of frame |
| `eye_aspect_ratio` | float | EAR value |
| `facial_asymmetry` | float | Asymmetry score |
| `blink_rate` | int | Blinks/minute at that frame |
| `microexpression` | str | "None" or "Sudden Movement" |
| `emotion` | str | Detected dominant emotion |
| `deception_probability` | float | Deception score 0–100 |

#### `results_report.txt`

Human-readable text summary of the session statistics.

---

## 🔄 Session Reset

To start a new session:
1. Click **"Stop"** if analysis is running.
2. Click **"Capture Baseline"** again to recalibrate.
3. Adjust settings as needed.
4. Click **"Start Analysis"**.

---

## 🎯 Tips for Best Results

| Tip | Reason |
|---|---|
| Use a consistent, neutral background | Reduces MediaPipe tracking noise |
| Ensure frontal, even lighting | FER and EAR accuracy depend on visible facial features |
| Keep your head relatively still during baseline | Landmark motion during baseline inflates microexpression sensitivity |
| Use a high-quality webcam (720p+) | Improves FER emotion detection accuracy |
| Keep face centered in frame | MediaPipe is configured for 1 face; off-center positioning reduces tracking confidence |
| Allow 5–10 seconds before clicking "Start Analysis" after baseline | Gives the system time to settle on your calibrated thresholds |

---

## ⚙️ Advanced: Changing Default Constants

The following constants at the top of `invictus.py` can be edited to customize behavior:

```python
BASELINE_DURATION = 10     # Increase for longer, more stable baselines
MAX_FRAMES = 10000         # Reduce to lower memory usage
FRAME_SCALE = 0.5          # Increase (e.g., 0.75) for higher accuracy, at cost of performance
BLINK_MIN_DURATION = 0.1   # Increase to reduce sensitivity to rapid partial blinks
VIDEO_WIDTH = 640          # Display resolution
VIDEO_HEIGHT = 480
```

---

## 📤 Output File Locations

Both output files are saved to the **directory from which you ran the script**:

```
invictus/
├── results.csv           ← Created after "Save Results"
├── results_report.txt    ← Created after "Save Results"
└── invictus.py
```

To change the output location, modify the `save_results()` method in `LieDetectorApp`.
