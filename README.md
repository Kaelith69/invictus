<div align="center">
  <img src="banner.svg" alt="Invictus Banner" width="900"/>
</div>

<div align="center">

[![Python](https://img.shields.io/badge/Python-3.7%2B-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://python.org)
[![OpenCV](https://img.shields.io/badge/OpenCV-4.5%2B-5C3EE8?style=for-the-badge&logo=opencv&logoColor=white)](https://opencv.org)
[![MediaPipe](https://img.shields.io/badge/MediaPipe-0.8.9%2B-0097A7?style=for-the-badge&logo=google&logoColor=white)](https://mediapipe.dev)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)](LICENSE)
[![Status](https://img.shields.io/badge/Status-Experimental-orange?style=for-the-badge)]()

</div>

---

> ⚠️ **Disclaimer:** This is a research tool only. Lie detection based on facial analysis is not scientifically validated and must **not** be used in legal, professional, or high-stakes contexts. Results are probabilistic and experimental.

---

## 📋 Table of Contents

- [Overview](#-overview)
- [Features](#-features)
- [Architecture](#-architecture)
- [Requirements](#-requirements)
- [Installation](#-installation)
- [Usage Guide](#-usage-guide)
- [Configuration Reference](#-configuration-reference)
- [How It Works](#-how-it-works)
- [Use Cases](#-use-cases)
- [Known Limitations](#-known-limitations)
- [Troubleshooting](#-troubleshooting)
- [Contributing](#-contributing)
- [License](#-license)

---

## 🔍 Overview

**Invictus** is a desktop application that uses real-time facial analysis, computer vision, and machine learning to estimate deception probability. It captures live webcam video, extracts facial biometric metrics frame-by-frame, compares them against a calibrated baseline, and outputs a probabilistic deception score.

The system is built entirely in Python using industry-standard libraries and provides a full graphical user interface (GUI) with live graphs, metrics, and exportable results.

---

## ✨ Features

| Category | Feature |
|---|---|
| 🎥 **Video** | Real-time webcam feed with frame-by-frame processing |
| 👁️ **Eye Tracking** | Eye Aspect Ratio (EAR) calculation for blink analysis |
| 💡 **Blink Detection** | Blink rate tracking (blinks per minute) with edge-triggered counting |
| 🎭 **Emotion** | Dominant emotion detection using FER (Facial Emotion Recognition) |
| 📐 **Asymmetry** | Facial symmetry analysis via landmark geometry |
| ⚡ **Microexpressions** | Rapid landmark velocity change detection |
| 🤖 **ML Model** | Random Forest Classifier for deception probability scoring |
| 📊 **Graphs** | Live and post-analysis matplotlib charts embedded in GUI |
| ⚙️ **Calibration** | 10-second baseline capture with outlier filtering |
| 💾 **Export** | Save results as CSV + text report |
| 🖥️ **GUI** | Full Tkinter desktop interface (1280×720, resizable) |

---

## 🏗️ Architecture

```
┌──────────────────────────────────────────────────────────────┐
│                      LieDetectorApp (GUI)                     │
│                                                               │
│  ┌─────────────┐    ┌──────────────┐    ┌─────────────────┐  │
│  │  Video Feed  │    │   Controls   │    │  Right Panel    │  │
│  │  (640×480)  │    │  + Settings  │    │  Metrics+Graphs │  │
│  └──────┬──────┘    └──────┬───────┘    └────────┬────────┘  │
│         │                  │                     │            │
│  ┌──────▼──────────────────▼─────────────────────▼────────┐  │
│  │               Background Video Thread                   │  │
│  │         (daemon, thread-safe via shared Lock)            │  │
│  └──────────────────────┬───────────────────────────────── ┘  │
└─────────────────────────┼────────────────────────────────────┘
                          │
          ┌───────────────▼──────────────────┐
          │       EnhancedLieDetector         │
          │                                   │
          │  ┌─────────────────────────────┐  │
          │  │    MediaPipe FaceMesh        │  │
          │  │    (468 landmark points)     │  │
          │  └──────────┬──────────────────┘  │
          │             │                     │
          │  ┌──────────▼──────────────────┐  │
          │  │     Metric Extraction        │  │
          │  │  EAR · Asymmetry · Blink     │  │
          │  │  Microexpression · Emotion   │  │
          │  └──────────┬──────────────────┘  │
          │             │                     │
          │  ┌──────────▼──────────────────┐  │
          │  │   Random Forest Classifier   │  │
          │  │   Deception Probability %    │  │
          │  └─────────────────────────────┘  │
          └───────────────────────────────────┘
```

### Data Flow

```
Webcam → OpenCV → Resize (0.5×) → MediaPipe → 468 Landmarks
  → EAR, Asymmetry, Blink Rate, Eye Movement
  → FER Emotion Detection
  → Microexpression Velocity Analysis
  → Baseline Deviation Scoring
  → RandomForest Predict → Deception % → GUI + Graphs
```

---

## 📦 Requirements

### Software

| Package | Version | Purpose |
|---|---|---|
| Python | 3.7+ | Runtime |
| `opencv-python` | ≥ 4.5.0 | Video capture & frame processing |
| `mediapipe` | ≥ 0.8.9 | 468-point facial landmark detection |
| `numpy` | ≥ 1.19.0 | Numerical computations |
| `pillow` | ≥ 8.0.0 | Image conversion for Tkinter display |
| `pandas` | ≥ 1.3.0 | Metrics storage and DataFrame analysis |
| `matplotlib` | ≥ 3.4.0 | Embedded real-time graphs |
| `scikit-learn` | ≥ 0.24.0 | Random Forest Classifier |
| `fer` | ≥ 22.4.0 | Facial Emotion Recognition |
| `tkinter` | built-in | Desktop GUI framework |

### Hardware

| Component | Minimum | Recommended |
|---|---|---|
| CPU | Dual-core 2GHz | Quad-core 3GHz+ |
| RAM | 4 GB | 8 GB+ |
| Webcam | 640×480 capture @ 15fps | 1280×720 capture @ 30fps |
| Display | 1280×720 | 1920×1080 |
| Storage | 200 MB free | 500 MB free |

---

## 🚀 Installation

### 1. Clone the repository

```bash
git clone https://github.com/Kaelith69/invictus.git
cd invictus
```

### 2. Create a virtual environment (recommended)

```bash
# Windows
python -m venv venv
venv\Scripts\activate

# macOS / Linux
python3 -m venv venv
source venv/bin/activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

> **Note:** `tkinter` is included with Python's standard library. If it's missing on Linux, install it with:
> ```bash
> sudo apt-get install python3-tk
> ```

### 4. Verify the facial landmark model

The file `shape_predictor_68_face_landmarks.dat` should be present in the project root (used by optional dlib integration). The primary detection pipeline uses MediaPipe and does not require this file.

### 5. Run the application

```bash
python invictus.py
```

---

## 📖 Usage Guide

### Step 1 — Launch & Disclaimer

Run `python invictus.py`. Accept the disclaimer popup confirming you understand the experimental nature of the tool.

### Step 2 — Start Camera

Click **"Start Camera"**. The webcam feed will appear in the left panel. Ensure:
- Your face is clearly visible and well-lit
- You are 40–80 cm from the camera
- No strong backlighting behind you

### Step 3 — Capture Baseline

Click **"Capture Baseline"** and maintain a **neutral resting expression** for **10 seconds**. The progress bar tracks completion. The baseline establishes your personal normal metrics for:
- Eye Aspect Ratio (EAR)
- Facial asymmetry
- Blink rate

> ⚠️ Baseline quality is critical. Poor lighting or expressions during baseline will skew all subsequent analysis.

### Step 4 — Configure Settings

In the **Settings** panel:

| Setting | Description | Default |
|---|---|---|
| Recording Duration | How long the analysis session lasts (5–300s) | 30 seconds |
| Sensitivity | Scales the deception probability output (0.1–1.0) | 0.7 |
| Question | The question to display during analysis | (empty) |

### Step 5 — Start Analysis

Click **"Start Analysis"**. Real-time metrics appear on the right panel and graphs update live:
- **Top graph:** Deception Probability % over time
- **Bottom graph:** Normalized EAR, facial asymmetry, and blink rate over time

### Step 6 — Review Results

After analysis completes (or after clicking **"Stop"**), the Results panel shows:
- Average deception probability
- Peak deception probability
- Average blink rate
- Average EAR and facial asymmetry
- Most common emotion
- Number of microexpression events

### Step 7 — Save Results

Click **"Save Results"** to export:
- **`results.csv`** — full per-frame metrics data
- **`results_report.txt`** — human-readable summary

---

## ⚙️ Configuration Reference

### Constants (top of `invictus.py`)

| Constant | Default | Description |
|---|---|---|
| `BASELINE_DURATION` | `10` | Baseline capture duration in seconds |
| `MAX_FRAMES` | `10000` | Maximum frames stored in the rolling deque |
| `FRAME_SCALE` | `0.5` | Frame downscale factor for performance |
| `BLINK_MIN_DURATION` | `0.1` | Minimum seconds between registered blinks |
| `VIDEO_WIDTH` | `640` | Display panel width in pixels (frames are resized to this for display) |
| `VIDEO_HEIGHT` | `480` | Display panel height in pixels (frames are resized to this for display) |

### Emotion Weights (in `EnhancedLieDetector`)

These weights modify the deception score based on detected emotion:

| Emotion | Weight | Rationale |
|---|---|---|
| `fear` | +0.4 | Strong deception indicator |
| `surprise` | +0.3 | Moderate indicator |
| `angry` | +0.2 | Moderate indicator |
| `disgust` | +0.2 | Moderate indicator |
| `sad` | +0.1 | Weak indicator |
| `neutral` | 0.0 | No modification |
| `happy` | -0.1 | Slight negative modifier |

---

## 🔬 How It Works

### Eye Aspect Ratio (EAR)

EAR measures eye openness using 6 landmark points per eye:

```
         p2    p3
          \   /
    p1 ----+---- p4
          /   \
         p6    p5

EAR = (||p2-p6|| + ||p3-p5||) / (2 × ||p1-p4||)
```

A low EAR (< threshold) indicates a blink. The threshold is dynamically set to 70% of the baseline EAR.

### Blink Rate

Blinks are counted using **edge-triggered detection**: a blink registers exactly once when the EAR first drops below threshold for 2+ consecutive frames (not repeatedly while closed). Rate = blinks in the last 60 seconds.

### Facial Asymmetry

Asymmetry is computed as the relative difference between left and right distances from the nose tip to each cheek landmark:

```
asymmetry = |dist_left - dist_right| / max(dist_left, dist_right)
```

### Microexpression Detection

Landmark velocities between consecutive frames are computed as the sum of displacements across all 468 points. A microexpression is flagged when any frame's velocity exceeds `2 × sensitivity × mean_velocity`.

### Deception Probability

The Random Forest model receives 5 features:

1. **EAR deviation** — how much current EAR deviates from baseline
2. **Asymmetry score** — asymmetry relative to baseline
3. **Blink deviation** — blink rate deviation from baseline
4. **Eye movement score** — mean displacement of eye centers
5. **Emotion score** — weighted emotion signal

The output probability is scaled by the `sensitivity` setting and clamped to [0, 100]%.

> **Note:** The included model is trained on synthetic data. Production use would require a validated real-world dataset.

---

## 💡 Use Cases

| Use Case | Notes |
|---|---|
| **Research** | Studying correlations between facial signals and truthfulness |
| **Education** | Teaching computer vision and biometric analysis concepts |
| **Prototype Development** | Base for building more sophisticated multimodal systems |
| **Demonstration** | Showcasing real-time ML inference in a desktop application |

---

## ⚠️ Known Limitations

### Technical

- Requires consistent, even lighting (avoid strong shadows or backlighting)
- Face must be clearly visible; glasses, masks, or heavy facial hair reduce accuracy
- Processing delay may occur on systems with CPUs below 2GHz
- Emotion detection via FER may be unreliable on low-resolution or poorly lit faces

### Scientific

- Not validated for legal, professional, or any high-stakes use
- Results are probabilistic and not diagnostic
- Baseline must be captured in the same session and lighting conditions
- Individual physiological differences significantly affect results
- The ML model uses synthetic training data (placeholder)

---

## 🔧 Troubleshooting

| Problem | Likely Cause | Solution |
|---|---|---|
| "Could not open video source" | Webcam not detected or in use | Close other apps using the webcam; check device index (`video_source = 1`) |
| "No face detected" overlay | Face out of frame or poor lighting | Move closer to camera; improve lighting |
| Baseline failed ("not enough data") | No face visible during baseline | Ensure face is clearly detected before clicking Capture Baseline |
| `ImportError: No module named 'fer'` | Missing dependency | Run `pip install fer` |
| `ImportError: No module named 'mediapipe'` | Missing dependency | Run `pip install mediapipe` |
| Tkinter not found (Linux) | Missing system package | Run `sudo apt-get install python3-tk` |
| Very high/low deception scores always | Poor baseline quality | Recapture baseline in neutral, well-lit conditions |
| App freezes on close | Thread shutdown timing | Use the Stop button before closing the window |

---

## 📁 Project Structure

```
invictus/
├── invictus.py                          # Main application (GUI + detection engine)
├── requirements.txt                     # Python dependencies
├── banner.svg                           # Project banner image
├── README.md                            # This documentation
├── shape_predictor_68_face_landmarks.dat # Pre-trained dlib model (optional)
└── .gitignore                           # Git ignore rules
```

---

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. **Fork** the repository
2. **Create** a feature branch: `git checkout -b feature/your-feature`
3. **Make** your changes with clear, minimal commits
4. **Test** your changes locally
5. **Open** a Pull Request with a clear description

### Areas for Improvement

- Replace synthetic ML training data with a validated real-world dataset
- Add LSTM/temporal modeling for sequence-based prediction
- Implement multi-face tracking support
- Add audio analysis (voice stress) as a parallel channel
- Improve microexpression detection with optical flow

---

## 📄 License

This project is licensed under the **MIT License**. See the [LICENSE](LICENSE) file for details.

---

## 🙏 Acknowledgments

- [**MediaPipe**](https://mediapipe.dev/) — Real-time face mesh (468 landmarks)
- [**FER**](https://github.com/justinshenk/fer) — Facial Emotion Recognition library
- [**OpenCV**](https://opencv.org/) — Computer vision and video capture
- [**Scikit-learn**](https://scikit-learn.org/) — Machine learning framework
- [**dlib**](http://dlib.net/) — Shape predictor model

---

<div align="center">
  <sub>Built with ❤️ for research. Use responsibly.</sub>
</div>
