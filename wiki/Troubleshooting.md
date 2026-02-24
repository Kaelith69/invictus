# Troubleshooting

This page covers common issues encountered when installing, running, or using Invictus, along with diagnostic steps and solutions.

---

## 🛠️ Quick Reference

| Symptom | Likely Cause | Jump To |
|---|---|---|
| Camera won't open | Wrong device index or in use | [Camera Issues](#camera-issues) |
| "No face detected" overlay | Lighting or positioning | [Face Detection Issues](#face-detection-issues) |
| Baseline fails | No face during calibration | [Baseline Issues](#baseline-issues) |
| Import errors | Missing dependencies | [Dependency Issues](#dependency-issues) |
| App freezes or crashes | Thread timing or memory | [Performance & Stability](#performance--stability) |
| Always high/low scores | Poor calibration | [Score Issues](#score-issues) |
| Tkinter display errors | Missing system library | [GUI Issues](#gui-issues) |

---

## 📷 Camera Issues

### "Could not open video source"

**Cause:** OpenCV cannot access the webcam at index 0.

**Solutions:**
1. Close all other applications using the webcam (browsers, video conferencing, etc.).
2. Try a different device index:
   ```python
   # In invictus.py
   self.video_source = 1  # or 2, 3...
   ```
3. On Linux, check webcam permissions:
   ```bash
   ls -la /dev/video*
   sudo usermod -aG video $USER  # Then log out and back in
   ```
4. On Windows, check that the webcam is not disabled in Device Manager.
5. Verify OpenCV can access your camera independently:
   ```python
   import cv2
   cap = cv2.VideoCapture(0)
   print(cap.isOpened())  # Should print True
   cap.release()
   ```

### Camera opens but shows black/blank frame

**Cause:** Webcam initialization delay or driver issue.

**Solution:** Wait 2–3 seconds after clicking "Start Camera". Some webcams have a warm-up period. If persistent, reinstall your webcam driver.

---

## 👁️ Face Detection Issues

### "No face detected" shown in video overlay

**Cause:** MediaPipe FaceMesh cannot locate a face in the current frame.

**Solutions:**
1. Move closer to the camera (aim for 40–80 cm).
2. Improve lighting — use a lamp facing you, not behind you.
3. Ensure your entire face is in the frame, including forehead and chin.
4. Remove obstructions: sunglasses, masks, hoods.
5. Avoid extreme angles (profile view, looking down).
6. Check MediaPipe confidence thresholds (default 0.5):
   ```python
   # In EnhancedLieDetector.__init__, lower if needed:
   self.face_mesh = mp_face_mesh.FaceMesh(
       min_detection_confidence=0.3,  # lower threshold
       min_tracking_confidence=0.3
   )
   ```

### Landmarks jitter excessively

**Cause:** Low-quality webcam, poor lighting, or slow CPU causing dropped frames.

**Solutions:**
- Improve lighting conditions.
- Reduce `FRAME_SCALE` further (e.g., `0.3`) to speed up processing.
- Ensure no other CPU-intensive processes are running.

---

## ⚙️ Baseline Issues

### "Baseline capture failed" or "not enough data"

**Cause:** No face was detected during the 10-second calibration window.

**Solutions:**
1. Ensure your face is clearly detected (green eye outlines visible) **before** clicking "Capture Baseline".
2. Hold still and maintain a neutral expression for the full 10 seconds.
3. Improve lighting and positioning (see [Face Detection Issues](#face-detection-issues)).
4. Recapture: click "Capture Baseline" again.

### Baseline captured but scores seem wrong

**Cause:** Face was moving, expressing emotion, or poorly lit during baseline.

**Solution:** Recapture the baseline in neutral conditions. The baseline is the reference for all subsequent scores — it must reflect your true resting state.

---

## 📦 Dependency Issues

### `ModuleNotFoundError: No module named 'fer'`

```bash
pip install fer
```

### `ModuleNotFoundError: No module named 'mediapipe'`

```bash
pip install mediapipe
```

### `ModuleNotFoundError: No module named 'cv2'`

```bash
pip install opencv-python
```

### `ModuleNotFoundError: No module named 'tkinter'`

Tkinter is a system library, not a pip package.

```bash
# Debian / Ubuntu
sudo apt-get install python3-tk

# Fedora
sudo dnf install python3-tkinter
```

### `ImportError: libGL.so.1: cannot open shared object file` (Linux)

```bash
sudo apt-get install libgl1
```

### `error: Microsoft Visual C++ 14.0 or greater is required` (Windows, dlib)

Install [Visual Studio Build Tools](https://visualstudio.microsoft.com/visual-cpp-build-tools/) with the "C++ build tools" workload, then retry `pip install dlib`.

### TensorFlow/Keras warnings from FER

These are expected and can be suppressed. The `warnings.filterwarnings("ignore")` call at the bottom of `invictus.py` handles most of them.

---

## ⚡ Performance & Stability

### Application is very slow or laggy

**Causes and solutions:**

| Cause | Fix |
|---|---|
| High-resolution webcam input | Reduce `FRAME_SCALE` from 0.5 to 0.3 |
| FER emotion detection overhead | FER uses a neural network; this is expected on slow CPUs |
| Too many background processes | Close other CPU-intensive applications |
| Large frame buffer | Reduce `MAX_FRAMES` from 10000 to 1000 |

### Application freezes when closing

**Cause:** Video thread still running when Tkinter window is destroyed.

**Solution:** Always click **"Stop"** before closing the window. The window close button calls `app.cleanup()` which sets `self.running = False` and releases the camera, but timing issues can occasionally occur.

If it freezes: force-kill the process (`Ctrl+C` in terminal, or Task Manager on Windows).

### Memory usage grows over time

**Cause:** Frame data accumulating in `frame_data` deque.

The deque has `maxlen=MAX_FRAMES` (default 10,000). This bounds memory. If still a concern, reduce `MAX_FRAMES`:
```python
MAX_FRAMES = 1000  # Reduce from default 10000
```

### Graphs stop updating

**Cause:** Matplotlib rendering error or thread timing issue.

**Solution:** Stop and restart the analysis. If persistent, close and reopen the application.

---

## 📊 Score Issues

### Deception probability is always near 0% or 100%

**Most common cause:** Poor baseline quality.

**Solution:**
1. Click "Capture Baseline" again.
2. Ensure neutral expression, good lighting, face clearly visible.
3. Keep sensitivity at default (0.7).

### Scores are erratic / noisy

**Cause:** Unstable webcam feed, variable lighting, or sensitivity too high.

**Solutions:**
- Improve lighting stability.
- Lower sensitivity to 0.3–0.5.
- Ensure face remains centered in frame.

### Emotion always shows "Neutral"

**Cause:** FER requires sufficient face resolution and lighting to detect subtle emotions. At low resolution or in poor lighting, it defaults to Neutral.

**Solution:** Increase webcam resolution and improve lighting. If using `FRAME_SCALE = 0.5`, try raising it to `0.75`.

---

## 🖥️ GUI Issues

### Window appears too small or off-screen

**Solution:** The window opens at 1280×720. If your display is smaller, it will be clipped. Resize or scroll. You can change the default size:
```python
self.root.geometry("1024x600")  # Reduce initial size
```

### Matplotlib graphs appear blank

**Cause:** No analysis data recorded yet, or canvas not refreshing.

**Solution:** Start an analysis session. Graphs populate once data is recorded.

### Buttons remain greyed out

**State machine:**
- "Start Camera" → always active
- "Capture Baseline" → active after camera starts
- "Start Analysis" → active after baseline captured
- "Stop" → active during recording

If a button is unexpectedly disabled, restart the application.

---

## 🐛 Reporting Bugs

When filing a bug report, include:

1. Python version: `python --version`
2. OS and version
3. Full error traceback (copy from terminal)
4. Steps to reproduce the issue
5. Webcam model if relevant to camera issues

File issues at: [https://github.com/Kaelith69/invictus/issues](https://github.com/Kaelith69/invictus/issues)
