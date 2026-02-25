# Contributing to Invictus 🧠

<div align="center">

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 700 100" width="700">
  <defs>
    <linearGradient id="cBg" x1="0%" y1="0%" x2="100%" y2="100%">
      <stop offset="0%" style="stop-color:#0f0c29"/>
      <stop offset="100%" style="stop-color:#1a1040"/>
    </linearGradient>
    <linearGradient id="cAccent" x1="0%" y1="0%" x2="100%" y2="0%">
      <stop offset="0%" style="stop-color:#7C3AED"/>
      <stop offset="50%" style="stop-color:#2563EB"/>
      <stop offset="100%" style="stop-color:#06B6D4"/>
    </linearGradient>
  </defs>
  <rect width="700" height="100" fill="url(#cBg)" rx="10"/>
  <text x="350" y="42" text-anchor="middle" font-family="Arial, sans-serif" font-size="24" font-weight="800" fill="white" letter-spacing="4">CONTRIBUTING</text>
  <rect x="120" y="52" width="460" height="2" fill="url(#cAccent)" rx="1"/>
  <text x="350" y="74" text-anchor="middle" font-family="Arial, sans-serif" font-size="12" fill="#a8b2d8" letter-spacing="2">Make Invictus better. We dare you.</text>
</svg>

</div>

---

First of all — thank you for even *reading* this file. Most people just open a PR, break everything, and disappear. You are already in the top 10%.

Found a bug? **Congratulations, you are now part of the development team.**

---

## 🚀 Ways to Contribute

- 🐛 **Bug reports** — You found something broken. Good. Tell us.
- ✨ **Feature requests** — You have an idea. Even better. Open an issue.
- 🔧 **Code contributions** — You wrote a fix. We love you. Open a PR.
- 📖 **Documentation** — You spotted a typo. Please fix it. We're only human.
- 🧪 **Testing** — You actually ran the thing and wrote tests. Hero status.

---

## 🛠️ Development Setup

```bash
git clone https://github.com/Kaelith69/invictus.git
cd invictus
python -m venv venv
source venv/bin/activate   # Windows: venv\Scripts\activate
pip install -r requirements.txt
python invictus.py
```

If this fails, read the error message. Read it again. Then check [Troubleshooting](wiki/Troubleshooting.md).

---

## 📋 Contribution Workflow

1. **Fork** the repository (top-right corner, the button that looks like a fork)
2. **Create a branch** — name it something descriptive:
   ```bash
   git checkout -b fix/blink-rate-overcounting
   git checkout -b feature/audio-stress-analysis
   ```
3. **Make your changes** — small, focused, atomic commits are chef's kiss
4. **Test locally** — run `python invictus.py` and make sure you haven't summoned chaos
5. **Open a Pull Request** — fill in the template, explain what you did and why

---

## ✅ Code Style

- Follow [PEP 8](https://peps.python.org/pep-0008/). Your IDE probably already does this for you.
- Use `black` for formatting: `black invictus.py`
- Use `flake8` for linting: `flake8 invictus.py`
- Keep functions focused. If a function is doing 5 things, it's actually 5 functions pretending to be one.
- Add docstrings to new classes and public methods.

---

## 🐛 Reporting Bugs

Before opening an issue, please check that:
- You are using Python 3.7+
- All dependencies from `requirements.txt` are installed
- You've tried turning it off and on again

**What to include in your bug report:**
- OS and Python version
- Full error traceback (copy-paste, don't screenshot)
- Steps to reproduce — "it just broke" is not steps to reproduce
- What you expected vs. what actually happened

---

## 💡 Feature Requests

Open an issue tagged `enhancement`. Describe:
- What you want
- Why you want it
- How you imagine it working

The wilder the idea, the more we want to hear it. (Within reason. No, we are not adding Bluetooth.)

---

## 🔀 Pull Request Guidelines

- PRs should target the `main` branch
- Keep PRs focused — one feature or fix per PR
- Include a description of what changed and why
- If you're touching detection logic, explain the behavioral impact
- Reference any related issues: `Fixes #42`

We review PRs within a reasonable human timeframe. Not immediately. We also have webcams watching us.

---

## 🚫 What We Won't Accept

- Code that introduces network calls (this is a local-only tool by design)
- Features that store or transmit biometric data off-device
- Breaking changes without discussion
- Pull requests titled "misc fixes" with 47 unrelated changes

---

## 🧑‍⚖️ Code of Conduct

Be respectful. Be constructive. Don't be the person who leaves a one-line comment saying "this is wrong" with no explanation. We're all just people trying to make a lie detector using a webcam, which is already absurd enough.

---

## 📄 License

By contributing, you agree that your contributions will be licensed under the [MIT License](LICENSE).

---

<div align="center">
  <sub>Built with ❤️ and questionable decision-making.</sub>
</div>
