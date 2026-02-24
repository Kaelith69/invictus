# Invictus Wiki — Home

<div align="center">

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 700 120" width="700">
  <defs>
    <linearGradient id="wBg" x1="0%" y1="0%" x2="100%" y2="100%">
      <stop offset="0%" style="stop-color:#0f0c29"/>
      <stop offset="100%" style="stop-color:#1a1040"/>
    </linearGradient>
    <linearGradient id="wAccent" x1="0%" y1="0%" x2="100%" y2="0%">
      <stop offset="0%" style="stop-color:#7C3AED"/>
      <stop offset="50%" style="stop-color:#2563EB"/>
      <stop offset="100%" style="stop-color:#06B6D4"/>
    </linearGradient>
  </defs>
  <rect width="700" height="120" fill="url(#wBg)" rx="10"/>
  <text x="350" y="52" text-anchor="middle" font-family="'Segoe UI', Arial" font-size="30" font-weight="800" fill="white" letter-spacing="6">INVICTUS</text>
  <rect x="100" y="62" width="500" height="2.5" fill="url(#wAccent)" rx="1"/>
  <text x="350" y="86" text-anchor="middle" font-family="'Segoe UI', Arial" font-size="13" fill="#a8b2d8" letter-spacing="3">ADVANCED REAL-TIME LIE DETECTION SYSTEM</text>
  <text x="350" y="106" text-anchor="middle" font-family="'Segoe UI', Arial" font-size="10" fill="#6b7db3">Computer Vision · Machine Learning · Biometric Analysis · Python</text>
</svg>

</div>

---

Welcome to the **Invictus** project wiki. This wiki provides in-depth documentation for developers, contributors, and researchers who want to understand, extend, or deploy the system.

---

## 📚 Wiki Pages

| Page | Description |
|---|---|
| **[Home](Home)** | This page — overview and navigation |
| **[Architecture](Architecture)** | System design, component breakdown, threading model |
| **[Installation](Installation)** | Detailed setup guide for all platforms |
| **[Usage](Usage)** | Step-by-step usage walkthrough, workflows, and tips |
| **[Privacy](Privacy)** | Data handling, privacy model, compliance notes |
| **[Contributing](Contributing)** | Contribution guidelines, code style, PR process |
| **[Troubleshooting](Troubleshooting)** | Common errors, debugging steps, environment issues |
| **[Roadmap](Roadmap)** | Planned features, priorities, and long-term direction |

---

## 🔍 Project Summary

**Invictus** is a desktop application that analyzes real-time webcam video to estimate deception probability using:

- **MediaPipe FaceMesh** — 468-point 3D facial landmark detection
- **OpenCV** — Webcam capture and frame preprocessing
- **FER** — Deep learning emotion recognition (7 classes)
- **Scikit-learn Random Forest** — Probabilistic deception scoring
- **Tkinter** — Cross-platform desktop GUI

> ⚠️ **Research tool only.** Not validated for legal, clinical, or professional decision-making.

---

## 🏗️ How the System Works (Quick Summary)

```
Webcam Feed
    ↓
OpenCV Frame Capture (0.5× downscale for performance)
    ↓
MediaPipe FaceMesh → 468 3D landmarks
    ↓
Metric Extraction:
  • Eye Aspect Ratio (EAR) — 6 points per eye
  • Facial Asymmetry — nose-to-cheek distances
  • Blink Rate — edge-triggered, 60s rolling window
  • Eye Movement — center displacement history
  • Microexpressions — velocity threshold on 468 points
  • Emotion — FER classifier (fear/surprise/happy/...)
    ↓
Baseline Deviation Scoring (vs. 10s calibration)
    ↓
Random Forest predict_proba() × sensitivity
    ↓
GUI: Live metrics + matplotlib charts + status bar
    ↓
Optional: Export results.csv + results_report.txt
```

---

## 📂 Repository Structure

```
invictus/
├── invictus.py                           # Main application
│   ├── LieDetectorApp (class)            #   GUI layer
│   └── EnhancedLieDetector (class)       #   Detection engine
├── requirements.txt                      # Python dependencies
├── banner.svg                            # Banner graphic
├── shape_predictor_68_face_landmarks.dat # Optional dlib model
├── wiki/                                 # This documentation
└── README.md                             # Project README
```

---

## 🚀 Quick Start

```bash
git clone https://github.com/Kaelith69/invictus.git
cd invictus
pip install -r requirements.txt
python invictus.py
```

See **[Installation](Installation)** for the full setup guide.

---

## ⚡ Key Concepts

| Concept | Explanation |
|---|---|
| **EAR** | Eye Aspect Ratio — geometric ratio of eye openness used to detect blinks |
| **Baseline** | 10-second neutral-expression calibration — all deception scores are deviations from this |
| **Sensitivity** | User-tunable multiplier (0.1–1.0) that scales the final deception probability |
| **Microexpression** | A frame where landmark velocity exceeds 2× the mean across the recent window |
| **Deception Score** | RandomForest probability, scaled by sensitivity, clamped to [0, 100]% |

---

## 🔗 External Resources

- [MediaPipe FaceMesh Documentation](https://google.github.io/mediapipe/solutions/face_mesh.html)
- [FER Library (GitHub)](https://github.com/justinshenk/fer)
- [OpenCV Documentation](https://docs.opencv.org/)
- [Scikit-learn RandomForestClassifier](https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.RandomForestClassifier.html)
- [Tkinter Documentation](https://docs.python.org/3/library/tkinter.html)
