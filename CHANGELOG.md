# Changelog

All notable changes to **Invictus** will be documented in this file.

Format loosely follows [Keep a Changelog](https://keepachangelog.com/en/1.0.0/).  
Versioning follows [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

---

## [Unreleased]

### Planned
- Audio channel (voice stress analysis) — because one biometric isn't enough paranoia
- Multi-face tracking — for when you're suspicious of multiple people simultaneously
- LSTM-based temporal modeling — the Random Forest is doing its best, okay?
- Packaged executable (`.exe` / `.app`) — for people who don't know what `pip install` means

---

## [1.0.0] — 2024-01-01

### Added
- Initial release of the Invictus lie detection system
- Real-time webcam capture via OpenCV at 0.5× downscale (performance, not laziness)
- MediaPipe FaceMesh integration — 468 3D facial landmarks per frame
- Eye Aspect Ratio (EAR) calculation for blink detection using 6-point geometric formula
- Facial asymmetry scoring — because your face lies even when you don't
- Blink rate tracking with 60-second rolling window
- Eye movement displacement history
- Microexpression detection based on landmark velocity thresholding
- FER emotion classification (7 classes: angry, disgust, fear, happy, sad, surprise, neutral)
- 10-second baseline calibration — the one calm moment before the interrogation begins
- RandomForestClassifier deception scoring with `predict_proba()`
- User-tunable sensitivity slider (0.1–1.0)
- Tkinter GUI with dual-panel layout (video + metrics/graphs)
- Live matplotlib charts embedded in the GUI — because numbers alone aren't dramatic enough
- Post-analysis summary results panel
- CSV and TXT export functionality
- Threading model with `_lock` for thread-safe GUI updates
- Graceful shutdown with `WM_DELETE_WINDOW` protocol handler
- `shape_predictor_68_face_landmarks.dat` support for optional dlib integration
- Full disclaimer on startup — we're not liable, you clicked "OK"

### Fixed
- Fixed bug where reality stopped working (added error handling around MediaPipe initialization)
- Fixed thread leak where video capture never actually stopped (it was just ignoring you)
- Fixed baseline capture completing even when no face was detected (a baseline of nothing is not a baseline)

### Known Issues
- Deception scoring uses synthetically generated training data (real-world validation: pending your personal courage)
- Microexpression detection is sensitive to lighting changes (the app thinks turning off a lamp is suspicious)
- High CPU usage on older hardware — the 468 landmarks aren't going to track themselves

---

## [0.9.0-beta] — 2023-11-15

### Added
- Beta release for internal testing
- Basic webcam integration and frame capture loop
- Prototype EAR blink detection
- Placeholder deception score display
- Early version of the Tkinter GUI layout

### Changed
- Switched from dlib as the primary landmark detector to MediaPipe FaceMesh (dlib requires compiling C++ in 2024, which nobody has time for)

### Fixed
- Fixed crash when webcam was not connected (turns out `None` is not a valid video frame)
- Fixed GUI freezing because someone put the ML inference on the main thread (never again)

---

## [0.1.0-alpha] — 2023-09-01

### Added
- Proof-of-concept script
- OpenCV webcam capture
- Basic eye landmark extraction via dlib
- "Is this person lying?" hardcoded output of "Maybe" (surprisingly accurate)

---

<div align="center">
  <sub>Every version ships with equal parts optimism and caffeine.</sub>
</div>
