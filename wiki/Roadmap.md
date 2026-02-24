# Roadmap

This page outlines the planned direction for Invictus, organized by priority and development phase.

---

## 🎯 Vision

Invictus aims to be a comprehensive, extensible research platform for real-time multimodal behavioral analysis. The current version (v1.x) establishes the core pipeline. Future versions will focus on scientific validity, modularity, and extended signal channels.

---

## 🔴 High Priority (Next Release)

### 1. Validated ML Dataset
**Status:** Pending  
**Description:** The current `RandomForestClassifier` is trained on synthetic data. This is the primary limitation of the system's scientific validity.

**Goals:**
- Source or construct an ethically collected, consent-based facial behavior dataset
- Train and evaluate multiple classifiers (Random Forest, SVM, Gradient Boosting)
- Report per-class accuracy, F1, and AUC metrics
- Document dataset provenance, consent process, and limitations

**Acceptance criteria:** Model trained on real data; evaluation metrics publicly documented.

---

### 2. LSTM Temporal Modeling
**Status:** Planned  
**Description:** The current model scores each frame independently, ignoring temporal context. Deceptive behavior often manifests as a *sequence* of signals, not a single frame anomaly.

**Goals:**
- Implement a sliding-window LSTM that takes N consecutive feature vectors as input
- Compare LSTM performance against frame-independent Random Forest baseline
- Allow configurable window size

**Technical approach:**
```python
# Proposed feature pipeline
features_window = deque(maxlen=LSTM_WINDOW)  # e.g., 30 frames
features_window.append(current_frame_features)
if len(features_window) == LSTM_WINDOW:
    prob = lstm_model.predict(np.array(features_window).reshape(1, LSTM_WINDOW, N_FEATURES))
```

---

## 🟡 Medium Priority (Future Releases)

### 3. Optical Flow Microexpressions
**Status:** Planned  
**Description:** Replace the current landmark velocity heuristic with dense optical flow for richer motion analysis.

**Approach:** Use `cv2.calcOpticalFlowFarneback()` on face ROI between consecutive frames. Compute magnitude and direction maps. Detect sudden onset, high-magnitude events as microexpression candidates.

---

### 4. Audio Channel (Voice Stress)
**Status:** Planned  
**Description:** Add a parallel audio analysis channel that processes microphone input for voice stress indicators: fundamental frequency (F0) variation, speech rate, pause frequency, and jitter.

**Libraries:** `pyaudio`, `librosa`, `webrtcvad`

**Integration:** Audio features added as additional columns in the feature vector alongside facial metrics.

---

### 5. Multi-Face Tracking
**Status:** Planned  
**Description:** MediaPipe supports `max_num_faces > 1`. Extend the system to handle multiple concurrent subjects in the same frame, with per-subject metric panels.

**UI change required:** Dynamic right panel that creates metric rows per detected face.

---

### 6. Configurable ML Backend
**Status:** Planned  
**Description:** Introduce a plugin architecture allowing the ML backend to be swapped without modifying core detection code.

```python
class BaseClassifier(ABC):
    @abstractmethod
    def predict(self, features: np.ndarray) -> float: ...

class RandomForestBackend(BaseClassifier): ...
class LSTMBackend(BaseClassifier): ...
class SVMBackend(BaseClassifier): ...
```

---

## 🟢 Low Priority (Long-Term)

### 7. Video File Analysis
**Status:** Planned  
**Description:** Accept pre-recorded video files as input in addition to live webcam.

**Implementation:** Replace `cv2.VideoCapture(0)` with `cv2.VideoCapture(filepath)`. Add file picker UI element.

---

### 8. Dark Mode GUI
**Status:** Planned  
**Description:** Optional dark theme for the Tkinter interface using `ttk.Style` customization.

---

### 9. Report Export (PDF)
**Status:** Considering  
**Description:** Generate a formatted PDF report with summary statistics and embedded graphs using `reportlab` or `fpdf2`.

---

### 10. REST API Mode
**Status:** Considering  
**Description:** A headless mode exposing analysis results via a local HTTP API (e.g., Flask/FastAPI), enabling integration with external tools and dashboards.

---

## 🚫 Out of Scope

The following will **not** be implemented in this project:

- Cloud/server-side processing of biometric data
- Real-time streaming to remote endpoints
- Any feature intended for use in consequential decision-making (hiring, legal, medical)
- Claims of validated lie detection accuracy

---

## 📅 Release History

| Version | Description |
|---|---|
| v1.0 | Initial release — MediaPipe FaceMesh, FER, Random Forest, Tkinter GUI |
| v1.1 | Code quality improvements, linting, thread safety fixes |

---

## 💬 Contributing to the Roadmap

Have an idea? Open an issue at [https://github.com/Kaelith69/invictus/issues](https://github.com/Kaelith69/invictus/issues) with the label `enhancement` and describe:

1. The use case or problem being solved
2. Proposed technical approach
3. Any relevant prior art or libraries
4. Whether you are willing to implement it

All roadmap items are open to community contribution. See [Contributing](Contributing) for how to get started.
