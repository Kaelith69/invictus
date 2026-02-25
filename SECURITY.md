# Security Policy

<div align="center">

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 700 100" width="700">
  <defs>
    <linearGradient id="sBg" x1="0%" y1="0%" x2="100%" y2="100%">
      <stop offset="0%" style="stop-color:#0f0c29"/>
      <stop offset="100%" style="stop-color:#1a1040"/>
    </linearGradient>
    <linearGradient id="sAccent" x1="0%" y1="0%" x2="100%" y2="0%">
      <stop offset="0%" style="stop-color:#7C3AED"/>
      <stop offset="50%" style="stop-color:#2563EB"/>
      <stop offset="100%" style="stop-color:#06B6D4"/>
    </linearGradient>
  </defs>
  <rect width="700" height="100" fill="url(#sBg)" rx="10"/>
  <text x="350" y="42" text-anchor="middle" font-family="Arial, sans-serif" font-size="24" font-weight="800" fill="white" letter-spacing="4">SECURITY POLICY</text>
  <rect x="140" y="52" width="420" height="2" fill="url(#sAccent)" rx="1"/>
  <text x="350" y="74" text-anchor="middle" font-family="Arial, sans-serif" font-size="12" fill="#a8b2d8" letter-spacing="2">Responsible disclosure. No drama.</text>
</svg>

</div>

---

## Supported Versions

| Version | Supported |
|---|---|
| `1.x` (latest) | ✅ Active support |
| `0.9.x` (beta) | ⚠️ Critical fixes only |
| `0.1.x` (alpha) | ❌ Unsupported |

---

## Scope

Invictus is a **local desktop application** with no network connectivity and no remote attack surface. However, security issues that still apply include:

- **Malicious input files** — crafted video files or image inputs that trigger unsafe behavior in OpenCV or PIL
- **Path traversal vulnerabilities** — unsafe file path handling in export or load operations
- **Dependency vulnerabilities** — known CVEs in `opencv-python`, `mediapipe`, `pillow`, `scikit-learn`, `fer`, or any other package listed in `requirements.txt`
- **Privilege escalation** — any scenario where running the application could lead to unintended system access
- **Data exposure bugs** — any bug that causes biometric data to be written to disk or transmitted without user intent

---

## Reporting a Vulnerability

**Please do not open a public GitHub issue for security vulnerabilities.** If you do, someone will see it before we fix it, and that's a bad day for everyone.

### How to Report

1. **Email:** Open a private security advisory via GitHub:
   - Go to the [Security tab](https://github.com/Kaelith69/invictus/security) of this repository
   - Click **"Report a vulnerability"**
   - Fill in the details clearly

2. **What to include:**
   - Description of the vulnerability
   - Steps to reproduce (specific, not "it felt weird")
   - Affected version(s)
   - Potential impact assessment
   - Any suggested fix (optional, but appreciated)

3. **Response timeline:**
   - **Acknowledgement:** Within 72 hours
   - **Initial assessment:** Within 7 days
   - **Fix or remediation plan:** Within 30 days for critical issues

---

## What Happens After You Report

1. We confirm receipt and thank you sincerely
2. We investigate and reproduce the issue
3. We develop and test a fix
4. We release a patched version
5. We credit you in the release notes (unless you prefer anonymity — totally valid)
6. We update this policy if needed

---

## Out of Scope

The following are **not** considered security vulnerabilities for this project:

- The inherent unreliability of lie detection as a concept (that's a philosophy problem, not a security bug)
- Deception scores that are "wrong" — they are probabilistic by design
- UI/UX issues
- Performance problems
- Features you wish existed

---

## Security Design Principles

Invictus is built with a local-first, privacy-respecting design:

| Principle | Status |
|---|---|
| No network connections at runtime | ✅ Enforced |
| No remote telemetry or analytics | ✅ Enforced |
| No biometric data stored without explicit user action | ✅ Enforced |
| Camera activated only on user request | ✅ Enforced |
| All ML inference runs locally | ✅ Enforced |

For full details, see [Privacy Policy](wiki/Privacy.md).

---

## Dependency Vulnerabilities

If you discover a CVE in one of our dependencies, please still report it via the process above. We track dependency updates and will pin or upgrade affected packages as part of our maintenance cycle.

---

<div align="center">
  <sub>Your responsible disclosure keeps the project trustworthy. Thank you.</sub>
</div>
