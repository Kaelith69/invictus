# Privacy

This page describes how Invictus handles data, what is collected, where it is stored, and what users should consider before using the system.

---

## 🔒 Core Privacy Principles

Invictus is designed with the following privacy-first principles:

| Principle | Implementation |
|---|---|
| **Local-only processing** | All video, landmark, and analysis data stays on the user's device |
| **No telemetry** | The application contains no analytics, crash reporting, or usage tracking |
| **No network calls** | The application makes no outbound network requests at runtime |
| **User-initiated export** | Data is only written to disk when the user explicitly clicks "Save Results" |
| **Bounded in-memory storage** | Frame data is stored in a rolling deque and automatically evicted |

---

## 📷 Webcam Data

- The application accesses the system webcam via **OpenCV** (`cv2.VideoCapture`).
- Camera access begins only when the user clicks **"Start Camera"**.
- Raw frames are held in memory and are **never written to disk** unless the user explicitly saves results.
- The rolling frame buffer (`deque(maxlen=10000)`) has a fixed maximum size; once full, the oldest frames are automatically dropped.
- No video recordings are made or stored by the application.

---

## 📊 Biometric Data

The following biometric-derived data is computed per frame:

- Eye Aspect Ratio (EAR)
- Facial asymmetry score
- Blink rate
- Eye movement displacement
- Facial landmark coordinates (468 points, temporary in-memory only)
- Emotion classification (fear, surprise, happy, etc.)
- Deception probability score

**All of this data is transient and in-memory by default.** It is only persisted if the user clicks "Save Results", which writes `results.csv` and `results_report.txt` to the local filesystem.

---

## 💾 Exported Files

When the user saves results, two files are created in the current working directory:

| File | Contents | Sensitivity |
|---|---|---|
| `results.csv` | Per-frame biometric metrics (EAR, asymmetry, blink rate, emotion, deception %) | **Biometric data** |
| `results_report.txt` | Statistical summary of the session | Moderate |

**These files may contain biometric data.** Users are responsible for:
- Storing these files securely.
- Deleting them when no longer needed.
- Obtaining appropriate consent if analyzing third-party subjects.

---

## ⚖️ Legal and Regulatory Considerations

> **Invictus is a research tool and is not designed for compliance with any regulatory framework.**

Users deploying this tool — even informally — should be aware of the following:

### GDPR (EU)
Facial landmark data and emotion scores may constitute **biometric data** under Article 4(14) of the GDPR. Processing biometric data generally requires explicit consent and a lawful basis.

### CCPA (California, US)
Biometric data may fall under the CCPA's definition of personal information. Collection without disclosure may violate the Act.

### BIPA (Illinois, US)
The Illinois Biometric Information Privacy Act regulates the collection of biometric identifiers including facial geometry. Violations carry significant penalties.

### Other jurisdictions
Many other jurisdictions have or are developing biometric data protection laws. Users should consult applicable local law before using this tool on other individuals.

---

## 🧑‍🤝‍🧑 Analyzing Third Parties

If you use Invictus to analyze any person other than yourself:

1. **Obtain explicit, informed consent** before beginning analysis.
2. **Explain what data is collected** and how it will be used.
3. **Do not use results to make decisions** that affect the subject (employment, legal, medical, etc.).
4. **Delete exported data** when the purpose of analysis has been completed.
5. **Consider applicable laws** in your jurisdiction regarding biometric data.

---

## 🔐 Security Considerations

- The application has no authentication or access control. It is a single-user desktop tool.
- Exported CSV/text files are unencrypted plaintext. Apply OS-level file permissions or encryption if handling sensitive data.
- The webcam feed is not encrypted. It is processed entirely in RAM by the local process.
- The application does not validate or sanitize the "Question" text field input, as it is used only for display/export labelling.

---

## 🗑️ Data Deletion

To remove all data associated with a session:

1. Delete `results.csv` and `results_report.txt` from the working directory.
2. Close the application (in-memory data is released on exit).

No persistent databases or log files containing biometric data are created by default.

---

## 📞 Responsible Use Summary

- ✅ Use for personal research and learning
- ✅ Use in controlled, consented research studies
- ✅ Use for educational demonstrations with informed participants
- ❌ Do not use in employment screening
- ❌ Do not use in law enforcement or legal proceedings
- ❌ Do not use to make consequential decisions about individuals
- ❌ Do not deploy without understanding applicable privacy laws
