# Installation

This page provides detailed installation instructions for all supported platforms.

---

## 📋 Prerequisites

| Requirement | Minimum | Notes |
|---|---|---|
| Python | 3.7+ | 3.9+ recommended |
| pip | Latest | Included with Python |
| Git | Any | For cloning |
| Webcam | Any USB/built-in | Required for live analysis |
| RAM | 4 GB | 8 GB recommended |
| CPU | Dual-core 2GHz | Quad-core 3GHz recommended |

---

## 1. Clone the Repository

```bash
git clone https://github.com/Kaelith69/invictus.git
cd invictus
```

---

## 2. Create a Virtual Environment

Using a virtual environment is strongly recommended to isolate dependencies.

### Windows

```powershell
python -m venv venv
venv\Scripts\activate
```

### macOS / Linux

```bash
python3 -m venv venv
source venv/bin/activate
```

You should see `(venv)` in your terminal prompt once activated.

---

## 3. Install Python Dependencies

```bash
pip install -r requirements.txt
```

This installs:

| Package | Purpose |
|---|---|
| `opencv-python` | Webcam capture, frame processing |
| `mediapipe` | 468-point facial landmark detection |
| `numpy` | Numerical operations |
| `pillow` | Image format conversion for Tkinter |
| `pandas` | Per-frame DataFrame storage |
| `matplotlib` | Embedded charts |
| `scikit-learn` | Random Forest classifier |
| `fer` | Facial emotion recognition |
| `dlib` | Optional 68-point shape predictor |
| `imutils` | Optional image utilities |

> **dlib build note:** `dlib` requires a C++ compiler and CMake. See [platform-specific notes](#platform-specific-notes) below.

---

## 4. Install Tkinter (Linux only)

Tkinter is included with Python on Windows and macOS. On Linux:

```bash
# Debian / Ubuntu
sudo apt-get install python3-tk

# Fedora
sudo dnf install python3-tkinter

# Arch Linux
sudo pacman -S tk
```

---

## 5. Verify the Installation

Run a quick dependency check:

```bash
python -c "import cv2, mediapipe, numpy, pandas, matplotlib, sklearn, fer, tkinter; print('All OK')"
```

Expected output:
```
All OK
```

---

## 6. Run the Application

```bash
python invictus.py
```

The application window opens at 1280×720. Accept the disclaimer dialog and proceed.

---

## Platform-Specific Notes

### Windows

- Python 3.7+ from [python.org](https://python.org) includes Tkinter and pip by default.
- For dlib: install [Visual Studio Build Tools](https://visualstudio.microsoft.com/visual-cpp-build-tools/) and [CMake](https://cmake.org/download/) before `pip install dlib`.
- If webcam index 0 fails, try `video_source = 1` in `invictus.py` (line: `self.video_source = 0`).

### macOS

- Install Python via [Homebrew](https://brew.sh): `brew install python`
- Tkinter via Homebrew Python should work out of the box.
- For dlib: `xcode-select --install` to get Clang and build tools.
- Camera permissions: macOS will prompt for webcam access on first run.

### Linux (Ubuntu/Debian)

```bash
sudo apt-get update
sudo apt-get install python3 python3-pip python3-tk cmake build-essential
pip install -r requirements.txt
```

### Linux (Fedora/RHEL)

```bash
sudo dnf install python3 python3-pip python3-tkinter cmake gcc-c++
pip install -r requirements.txt
```

---

## Optional: dlib Facial Landmark Model

The file `shape_predictor_68_face_landmarks.dat` is included in the repository root. It is used by the optional dlib integration, which is not active in the primary detection pipeline (MediaPipe is used instead). No additional download is required.

If you wish to use dlib-based landmark detection in your own extensions:

```bash
pip install dlib
```

---

## Upgrading Dependencies

To upgrade all dependencies to their latest compatible versions:

```bash
pip install --upgrade -r requirements.txt
```

---

## Uninstalling

To remove the virtual environment and all dependencies:

```bash
deactivate
rm -rf venv/   # or on Windows: rmdir /s /q venv
```

---

## Docker (Optional)

A basic containerized setup for development (no webcam passthrough in default Docker):

```dockerfile
FROM python:3.11-slim

RUN apt-get update && apt-get install -y \
    python3-tk \
    libgl1 \
    libglib2.0-0 \
    cmake \
    build-essential \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /app
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

COPY . .
CMD ["python", "invictus.py"]
```

> **Note:** GUI and webcam access in Docker requires X11 forwarding or a virtual display (e.g., Xvfb). This is primarily useful for CI or headless testing.

---

## Troubleshooting Installation

| Error | Cause | Fix |
|---|---|---|
| `ModuleNotFoundError: No module named 'tkinter'` | Tkinter not installed (Linux) | `sudo apt-get install python3-tk` |
| `error: Microsoft Visual C++ 14.0 is required` | Missing C++ tools (Windows, dlib) | Install Visual Studio Build Tools |
| `CMake must be installed` | CMake missing (dlib) | Install CMake and add to PATH |
| `ImportError: libGL.so.1: cannot open shared object file` | Missing OpenGL libs (Linux) | `sudo apt-get install libgl1` |
| `pip: command not found` | pip not in PATH | Use `python -m pip install -r requirements.txt` |
| Slow install of `fer` | TensorFlow download | Allow extra time; use `--no-cache-dir` if disk is limited |
