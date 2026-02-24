# Contributing

Thank you for your interest in contributing to Invictus! This page covers how to set up a development environment, coding standards, and the pull request process.

---

## 🤝 Ways to Contribute

- 🐛 **Bug reports** — File an issue with reproduction steps
- 💡 **Feature requests** — Open an issue describing the use case
- 🔧 **Bug fixes** — Fork, fix, and open a PR
- 🧠 **Algorithm improvements** — Better ML models, detection methods
- 📚 **Documentation** — Improve wiki pages, code comments, README
- 🧪 **Tests** — Add unit tests for detection logic

---

## 🛠️ Development Setup

### 1. Fork and clone

```bash
git clone https://github.com/<your-username>/invictus.git
cd invictus
```

### 2. Create a virtual environment

```bash
python3 -m venv venv
source venv/bin/activate   # Windows: venv\Scripts\activate
```

### 3. Install all dependencies (including dev tools)

```bash
pip install -r requirements.txt
```

Dev tools included in `requirements.txt`:
- `pytest` — testing
- `black` — code formatting
- `flake8` — linting

---

## 📐 Code Style

### Formatter: Black

All Python code must be formatted with **Black** (default settings):

```bash
black invictus.py
```

### Linter: Flake8

Code must pass **flake8** with default rules:

```bash
flake8 invictus.py
```

Common violations to avoid:
- Lines longer than 79 characters (E501)
- Unused imports (F401)
- Undefined names (F821)

### Naming Conventions

Follow existing conventions in the codebase:

| Element | Convention | Example |
|---|---|---|
| Classes | `PascalCase` | `LieDetectorApp` |
| Methods | `snake_case` | `capture_baseline()` |
| Constants | `UPPER_SNAKE_CASE` | `BASELINE_DURATION` |
| Local variables | `snake_case` | `ear_deviation` |
| Private attributes | `_snake_case` | `self._lock` |

---

## 🧪 Testing

Run tests with pytest:

```bash
pytest
```

When adding new features, include tests that cover:
- The happy path (normal operation)
- Edge cases (empty input, zero values, boundary conditions)
- Error handling (missing face, invalid data)

Test files should be placed in a `tests/` directory and named `test_<module>.py`.

**Example test structure:**

```python
# tests/test_detector.py
import pytest
from invictus import EnhancedLieDetector

def test_ear_returns_zero_for_insufficient_points():
    detector = EnhancedLieDetector()
    result = detector.calculate_eye_aspect_ratio([])
    assert result == 0.0

def test_asymmetry_returns_float():
    detector = EnhancedLieDetector()
    # Provide mock 468-point list
    points = [(0, 0)] * 468
    result = detector.calculate_facial_asymmetry(points)
    assert isinstance(result, float)
```

---

## 🌿 Branch Strategy

| Branch | Purpose |
|---|---|
| `main` | Stable, production-ready code |
| `feature/<name>` | New features |
| `fix/<name>` | Bug fixes |
| `docs/<name>` | Documentation updates |
| `refactor/<name>` | Code refactoring without behavior change |

**Create a branch:**

```bash
git checkout -b feature/lstm-temporal-model
```

---

## 📬 Pull Request Process

1. **Fork** the repository and create a branch from `main`.
2. **Make your changes** with focused, atomic commits.
3. **Format** your code with `black`.
4. **Lint** with `flake8`.
5. **Run tests** with `pytest` and ensure all pass.
6. **Update documentation** if your change affects behavior, configuration, or architecture.
7. **Open a Pull Request** with:
   - A clear title describing the change
   - A description of what was changed and why
   - Reference to any related issues (`Fixes #123`)
   - Notes on testing performed

### PR Checklist

- [ ] Code formatted with `black`
- [ ] `flake8` passes with no errors
- [ ] Tests added/updated for the change
- [ ] Documentation updated if behavior changed
- [ ] No new dependencies added without discussion
- [ ] Disclaimer language preserved where relevant

---

## 🔍 Areas Seeking Contributions

These are high-priority areas where contributions are especially welcome:

### 1. Validated ML Dataset
The current `RandomForestClassifier` is trained on synthetic data. Replacing it with a real, ethically sourced, consent-based dataset would be the single biggest improvement to the system.

### 2. LSTM / Temporal Modeling
The current ML model treats each frame independently. A sequence model (LSTM or Transformer) operating on a sliding window of frames would capture temporal patterns.

### 3. Optical Flow for Microexpressions
The current microexpression detector uses simple landmark velocity. Dense optical flow (e.g., `cv2.calcOpticalFlowFarneback`) would provide richer motion information.

### 4. Audio Channel
Adding voice stress analysis (pitch, rate, pauses) as a parallel channel would create a multimodal system. Libraries like `librosa` or `pyaudio` could be used.

### 5. Multi-Face Tracking
MediaPipe supports `max_num_faces > 1`. Extending the GUI to handle multiple concurrent subjects would be a useful addition.

---

## 🚫 Contribution Anti-Patterns

Please avoid:
- Adding dependencies not in `requirements.txt` without discussion
- Removing or weakening the ethical disclaimer
- Claims of validated accuracy without a real dataset
- Breaking the `LieDetectorApp` / `EnhancedLieDetector` separation
- Hardcoding paths or platform-specific assumptions

---

## 📝 Commit Message Style

Use present-tense imperative style:

```
Add LSTM temporal model for deception scoring
Fix blink threshold calculation when baseline EAR is zero
Refactor microexpression detection to use optical flow
Update README with optical flow references
```

---

## 📃 License

By contributing, you agree that your contributions will be licensed under the project's [MIT License](../LICENSE).
