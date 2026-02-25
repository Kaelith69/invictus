<div align="center">

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 900 240" width="900">
  <defs>
    <linearGradient id="heroBg" x1="0%" y1="0%" x2="100%" y2="100%">
      <stop offset="0%" style="stop-color:#0f0c29"/>
      <stop offset="45%" style="stop-color:#1a1040"/>
      <stop offset="100%" style="stop-color:#2d1b69"/>
    </linearGradient>
    <linearGradient id="heroAccent" x1="0%" y1="0%" x2="100%" y2="0%">
      <stop offset="0%" style="stop-color:#7C3AED"/>
      <stop offset="50%" style="stop-color:#2563EB"/>
      <stop offset="100%" style="stop-color:#06B6D4"/>
    </linearGradient>
    <linearGradient id="eyeGrad" x1="0%" y1="0%" x2="100%" y2="100%">
      <stop offset="0%" style="stop-color:#7C3AED"/>
      <stop offset="100%" style="stop-color:#06B6D4"/>
    </linearGradient>
    <filter id="heroGlow">
      <feGaussianBlur stdDeviation="4" result="coloredBlur"/>
      <feMerge><feMergeNode in="coloredBlur"/><feMergeNode in="SourceGraphic"/></feMerge>
    </filter>
    <filter id="softGlow">
      <feGaussianBlur stdDeviation="2" result="coloredBlur"/>
      <feMerge><feMergeNode in="coloredBlur"/><feMergeNode in="SourceGraphic"/></feMerge>
    </filter>
  </defs>
  <!-- Background -->
  <rect width="900" height="240" fill="url(#heroBg)" rx="14"/>
  <!-- Grid overlay -->
  <g stroke="#7C3AED" stroke-width="0.4" opacity="0.12">
    <line x1="0" y1="60" x2="900" y2="60"/>
    <line x1="0" y1="120" x2="900" y2="120"/>
    <line x1="0" y1="180" x2="900" y2="180"/>
    <line x1="180" y1="0" x2="180" y2="240"/>
    <line x1="360" y1="0" x2="360" y2="240"/>
    <line x1="540" y1="0" x2="540" y2="240"/>
    <line x1="720" y1="0" x2="720" y2="240"/>
  </g>
  <!-- Circuit lines left -->
  <g stroke="#7C3AED" stroke-width="1" opacity="0.5">
    <line x1="0" y1="50" x2="90" y2="50"/>
    <line x1="90" y1="50" x2="110" y2="70"/>
    <line x1="110" y1="70" x2="160" y2="70"/>
    <circle cx="110" cy="70" r="3" fill="#7C3AED"/>
    <line x1="0" y1="190" x2="60" y2="190"/>
    <line x1="60" y1="190" x2="80" y2="170"/>
    <line x1="80" y1="170" x2="140" y2="170"/>
    <circle cx="80" cy="170" r="3" fill="#06B6D4"/>
  </g>
  <!-- Circuit lines right -->
  <g stroke="#06B6D4" stroke-width="1" opacity="0.5">
    <line x1="900" y1="50" x2="810" y2="50"/>
    <line x1="810" y1="50" x2="790" y2="70"/>
    <line x1="790" y1="70" x2="740" y2="70"/>
    <circle cx="790" cy="70" r="3" fill="#06B6D4"/>
    <line x1="900" y1="190" x2="840" y2="190"/>
    <line x1="840" y1="190" x2="820" y2="170"/>
    <line x1="820" y1="170" x2="760" y2="170"/>
    <circle cx="820" cy="170" r="3" fill="#7C3AED"/>
  </g>
  <!-- Eye / Scan icon -->
  <g transform="translate(100, 120)" filter="url(#heroGlow)">
    <!-- Outer scan rings -->
    <circle cx="0" cy="0" r="48" fill="none" stroke="#7C3AED" stroke-width="0.8" opacity="0.4" stroke-dasharray="6,4"/>
    <circle cx="0" cy="0" r="38" fill="none" stroke="#2563EB" stroke-width="0.8" opacity="0.3" stroke-dasharray="4,6"/>
    <!-- Eye shape -->
    <ellipse cx="0" cy="0" rx="34" ry="20" fill="none" stroke="url(#eyeGrad)" stroke-width="2.5"/>
    <!-- Iris -->
    <circle cx="0" cy="0" r="12" fill="none" stroke="#06B6D4" stroke-width="2"/>
    <!-- Pupil -->
    <circle cx="0" cy="0" r="5" fill="url(#eyeGrad)"/>
    <!-- Highlight -->
    <circle cx="-4" cy="-4" r="2.5" fill="white" opacity="0.7"/>
    <!-- Corner ticks -->
    <line x1="-34" y1="0" x2="-42" y2="0" stroke="#7C3AED" stroke-width="2"/>
    <line x1="34" y1="0" x2="42" y2="0" stroke="#06B6D4" stroke-width="2"/>
    <line x1="0" y1="-20" x2="0" y2="-28" stroke="#2563EB" stroke-width="2"/>
    <line x1="0" y1="20" x2="0" y2="28" stroke="#2563EB" stroke-width="2"/>
  </g>
  <!-- Title -->
  <text x="480" y="96" text-anchor="middle" font-family="'Segoe UI', Arial, sans-serif"
        font-size="52" font-weight="800" fill="white" letter-spacing="8" filter="url(#heroGlow)">INVICTUS</text>
  <!-- Accent bar -->
  <rect x="240" y="110" width="480" height="3.5" fill="url(#heroAccent)" rx="2"/>
  <!-- Tagline -->
  <text x="480" y="143" text-anchor="middle" font-family="'Segoe UI', Arial, sans-serif"
        font-size="15" fill="#a8b2d8" letter-spacing="5">ADVANCED REAL-TIME LIE DETECTION SYSTEM</text>
  <!-- Sub-tagline -->
  <text x="480" y="170" text-anchor="middle" font-family="'Segoe UI', Arial, sans-serif"
        font-size="12" fill="#6b7db3" letter-spacing="1">Computer Vision · Machine Learning · Biometric Analysis</text>
  <!-- Tech tags -->
  <g font-family="'Segoe UI', Arial, sans-serif" font-size="11">
    <rect x="218" y="192" width="88" height="24" rx="12" fill="#7C3AED" opacity="0.2" stroke="#7C3AED" stroke-width="1"/>
    <text x="262" y="208" text-anchor="middle" fill="#a78bfa">Python 3.7+</text>

    <rect x="316" y="192" width="84" height="24" rx="12" fill="#2563EB" opacity="0.2" stroke="#2563EB" stroke-width="1"/>
    <text x="358" y="208" text-anchor="middle" fill="#60a5fa">MediaPipe</text>

    <rect x="410" y="192" width="72" height="24" rx="12" fill="#06B6D4" opacity="0.2" stroke="#06B6D4" stroke-width="1"/>
    <text x="446" y="208" text-anchor="middle" fill="#67e8f9">OpenCV</text>

    <rect x="492" y="192" width="92" height="24" rx="12" fill="#7C3AED" opacity="0.2" stroke="#7C3AED" stroke-width="1"/>
    <text x="538" y="208" text-anchor="middle" fill="#a78bfa">Scikit-learn</text>

    <rect x="594" y="192" width="50" height="24" rx="12" fill="#2563EB" opacity="0.2" stroke="#2563EB" stroke-width="1"/>
    <text x="619" y="208" text-anchor="middle" fill="#60a5fa">FER</text>

    <rect x="654" y="192" width="70" height="24" rx="12" fill="#06B6D4" opacity="0.2" stroke="#06B6D4" stroke-width="1"/>
    <text x="689" y="208" text-anchor="middle" fill="#67e8f9">Tkinter</text>
  </g>
  <!-- Experimental badge -->
  <g transform="translate(845, 28)">
    <rect x="-46" y="-14" width="92" height="26" rx="13" fill="#7C3AED" opacity="0.85"/>
    <text x="0" y="5" text-anchor="middle" font-family="Arial, sans-serif"
          font-size="10" font-weight="bold" fill="white" letter-spacing="1">EXPERIMENTAL</text>
  </g>
</svg>

</div>

<div align="center">

[![Python](https://img.shields.io/badge/Python-3.7%2B-7C3AED?style=for-the-badge&logo=python&logoColor=white)](https://python.org)
[![OpenCV](https://img.shields.io/badge/OpenCV-4.5%2B-2563EB?style=for-the-badge&logo=opencv&logoColor=white)](https://opencv.org)
[![MediaPipe](https://img.shields.io/badge/MediaPipe-0.8.9%2B-06B6D4?style=for-the-badge&logo=google&logoColor=white)](https://mediapipe.dev)
[![Scikit-learn](https://img.shields.io/badge/Scikit--learn-0.24%2B-7C3AED?style=for-the-badge&logo=scikit-learn&logoColor=white)](https://scikit-learn.org)
[![License: MIT](https://img.shields.io/badge/License-MIT-06B6D4?style=for-the-badge)](LICENSE)
[![Status](https://img.shields.io/badge/Status-Experimental-orange?style=for-the-badge)]()

</div>

---

> ⚠️ **Disclaimer:** This is a research tool only. Lie detection based on facial analysis is not scientifically validated and must **not** be used in legal, professional, or high-stakes contexts. Results are probabilistic and experimental.

---

**Invictus** stares at your face with 468 landmarks and goes, *"Hmm, interesting."* It's like having a really judgmental friend who majored in computer vision and never blinks. No cloud. No spying. No Skynet. Just you, your webcam, and a Random Forest that definitely knows you ate the last slice of pizza.

<div align="center">

![Humor](https://media.giphy.com/media/077i6AULCXc0FKTj9s/giphy.gif)

</div>

---

## 📋 Table of Contents

- [Overview](#-overview)
- [Core Capabilities](#-core-capabilities)
- [Architecture](#-architecture)
- [Data Flow](#-data-flow)
- [Technology Stack](#-technology-stack)
- [Features](#-features)
- [Requirements](#-requirements)
- [Installation](#-installation)
- [Usage Guide](#-usage-guide)
- [Configuration Reference](#-configuration-reference)
- [How It Works](#-how-it-works)
- [Performance](#-performance)
- [Project Structure](#-project-structure)
- [Accessibility](#-accessibility)
- [Privacy & Security](#-privacy--security)
- [Roadmap](#-roadmap)
- [Design Principles](#-design-principles)
- [Use Cases](#-use-cases)
- [Known Limitations](#-known-limitations)
- [Troubleshooting](#-troubleshooting)
- [Contributing](#-contributing)
- [License](#-license)

---

## 🔍 Overview

**Invictus** is a desktop application that uses real-time facial analysis, computer vision, and machine learning to estimate deception probability. It captures live webcam video, extracts facial biometric metrics frame-by-frame, compares them against a calibrated personal baseline, and outputs a probabilistic deception score.

The system is built entirely in Python using industry-standard libraries and provides a full graphical user interface (GUI) with live graphs, real-time metrics, and exportable results.

---

## ✨ Core Capabilities

<div align="center">
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 860 320" width="860">
  <defs>
    <linearGradient id="capBg" x1="0%" y1="0%" x2="100%" y2="100%">
      <stop offset="0%" style="stop-color:#0f0c29"/>
      <stop offset="100%" style="stop-color:#1a1040"/>
    </linearGradient>
    <linearGradient id="cap1" x1="0%" y1="0%" x2="100%" y2="100%">
      <stop offset="0%" style="stop-color:#7C3AED"/>
      <stop offset="100%" style="stop-color:#5b21b6"/>
    </linearGradient>
    <linearGradient id="cap2" x1="0%" y1="0%" x2="100%" y2="100%">
      <stop offset="0%" style="stop-color:#2563EB"/>
      <stop offset="100%" style="stop-color:#1d4ed8"/>
    </linearGradient>
    <linearGradient id="cap3" x1="0%" y1="0%" x2="100%" y2="100%">
      <stop offset="0%" style="stop-color:#06B6D4"/>
      <stop offset="100%" style="stop-color:#0891b2"/>
    </linearGradient>
    <filter id="cardGlow">
      <feGaussianBlur stdDeviation="3" result="coloredBlur"/>
      <feMerge><feMergeNode in="coloredBlur"/><feMergeNode in="SourceGraphic"/></feMerge>
    </filter>
  </defs>
  <rect width="860" height="320" fill="url(#capBg)" rx="12"/>

  <!-- Title -->
  <text x="430" y="38" text-anchor="middle" font-family="'Segoe UI', Arial, sans-serif"
        font-size="16" font-weight="700" fill="white" letter-spacing="2">CORE CAPABILITIES</text>
  <rect x="160" y="46" width="540" height="2" fill="url(#heroAccent)" rx="1" opacity="0.6"/>

  <!-- Row 1: 4 cards -->
  <!-- Card 1: Video Analysis -->
  <g transform="translate(30, 70)">
    <rect width="180" height="100" rx="10" fill="#7C3AED" opacity="0.15" stroke="#7C3AED" stroke-width="1.5"/>
    <text x="90" y="30" text-anchor="middle" font-family="Arial" font-size="26" fill="#a78bfa">🎥</text>
    <text x="90" y="58" text-anchor="middle" font-family="'Segoe UI', Arial" font-size="13" font-weight="700" fill="white">Video Analysis</text>
    <text x="90" y="76" text-anchor="middle" font-family="'Segoe UI', Arial" font-size="10" fill="#a8b2d8">Real-time webcam</text>
    <text x="90" y="90" text-anchor="middle" font-family="'Segoe UI', Arial" font-size="10" fill="#a8b2d8">frame processing</text>
  </g>
  <!-- Card 2: Eye Tracking -->
  <g transform="translate(225, 70)">
    <rect width="180" height="100" rx="10" fill="#2563EB" opacity="0.15" stroke="#2563EB" stroke-width="1.5"/>
    <text x="90" y="30" text-anchor="middle" font-family="Arial" font-size="26" fill="#60a5fa">👁️</text>
    <text x="90" y="58" text-anchor="middle" font-family="'Segoe UI', Arial" font-size="13" font-weight="700" fill="white">Eye Tracking</text>
    <text x="90" y="76" text-anchor="middle" font-family="'Segoe UI', Arial" font-size="10" fill="#a8b2d8">EAR · Blink rate</text>
    <text x="90" y="90" text-anchor="middle" font-family="'Segoe UI', Arial" font-size="10" fill="#a8b2d8">movement analysis</text>
  </g>
  <!-- Card 3: Emotion Detection -->
  <g transform="translate(420, 70)">
    <rect width="180" height="100" rx="10" fill="#06B6D4" opacity="0.15" stroke="#06B6D4" stroke-width="1.5"/>
    <text x="90" y="30" text-anchor="middle" font-family="Arial" font-size="26" fill="#67e8f9">🎭</text>
    <text x="90" y="58" text-anchor="middle" font-family="'Segoe UI', Arial" font-size="13" font-weight="700" fill="white">Emotion Detection</text>
    <text x="90" y="76" text-anchor="middle" font-family="'Segoe UI', Arial" font-size="10" fill="#a8b2d8">FER-powered 7-class</text>
    <text x="90" y="90" text-anchor="middle" font-family="'Segoe UI', Arial" font-size="10" fill="#a8b2d8">emotion recognition</text>
  </g>
  <!-- Card 4: ML Scoring -->
  <g transform="translate(615, 70)">
    <rect width="180" height="100" rx="10" fill="#7C3AED" opacity="0.15" stroke="#7C3AED" stroke-width="1.5"/>
    <text x="90" y="30" text-anchor="middle" font-family="Arial" font-size="26" fill="#a78bfa">🤖</text>
    <text x="90" y="58" text-anchor="middle" font-family="'Segoe UI', Arial" font-size="13" font-weight="700" fill="white">ML Scoring</text>
    <text x="90" y="76" text-anchor="middle" font-family="'Segoe UI', Arial" font-size="10" fill="#a8b2d8">Random Forest</text>
    <text x="90" y="90" text-anchor="middle" font-family="'Segoe UI', Arial" font-size="10" fill="#a8b2d8">deception probability</text>
  </g>

  <!-- Row 2: 3 cards centered -->
  <!-- Card 5: Facial Mapping -->
  <g transform="translate(127, 190)">
    <rect width="180" height="100" rx="10" fill="#2563EB" opacity="0.15" stroke="#2563EB" stroke-width="1.5"/>
    <text x="90" y="30" text-anchor="middle" font-family="Arial" font-size="26" fill="#60a5fa">📐</text>
    <text x="90" y="58" text-anchor="middle" font-family="'Segoe UI', Arial" font-size="13" font-weight="700" fill="white">Facial Mapping</text>
    <text x="90" y="76" text-anchor="middle" font-family="'Segoe UI', Arial" font-size="10" fill="#a8b2d8">468-point MediaPipe</text>
    <text x="90" y="90" text-anchor="middle" font-family="'Segoe UI', Arial" font-size="10" fill="#a8b2d8">asymmetry analysis</text>
  </g>
  <!-- Card 6: Microexpressions -->
  <g transform="translate(322, 190)">
    <rect width="180" height="100" rx="10" fill="#06B6D4" opacity="0.15" stroke="#06B6D4" stroke-width="1.5"/>
    <text x="90" y="30" text-anchor="middle" font-family="Arial" font-size="26" fill="#67e8f9">⚡</text>
    <text x="90" y="58" text-anchor="middle" font-family="'Segoe UI', Arial" font-size="13" font-weight="700" fill="white">Microexpressions</text>
    <text x="90" y="76" text-anchor="middle" font-family="'Segoe UI', Arial" font-size="10" fill="#a8b2d8">Velocity-based rapid</text>
    <text x="90" y="90" text-anchor="middle" font-family="'Segoe UI', Arial" font-size="10" fill="#a8b2d8">movement detection</text>
  </g>
  <!-- Card 7: Export & GUI -->
  <g transform="translate(517, 190)">
    <rect width="180" height="100" rx="10" fill="#7C3AED" opacity="0.15" stroke="#7C3AED" stroke-width="1.5"/>
    <text x="90" y="30" text-anchor="middle" font-family="Arial" font-size="26" fill="#a78bfa">📊</text>
    <text x="90" y="58" text-anchor="middle" font-family="'Segoe UI', Arial" font-size="13" font-weight="700" fill="white">Live Dashboard</text>
    <text x="90" y="76" text-anchor="middle" font-family="'Segoe UI', Arial" font-size="10" fill="#a8b2d8">Real-time graphs</text>
    <text x="90" y="90" text-anchor="middle" font-family="'Segoe UI', Arial" font-size="10" fill="#a8b2d8">CSV/report export</text>
  </g>
</svg>
</div>

---

## 🏗️ Architecture

<div align="center">
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 860 440" width="860">
  <defs>
    <linearGradient id="archBg" x1="0%" y1="0%" x2="100%" y2="100%">
      <stop offset="0%" style="stop-color:#0f0c29"/>
      <stop offset="100%" style="stop-color:#1a1040"/>
    </linearGradient>
    <linearGradient id="layer1" x1="0%" y1="0%" x2="100%" y2="0%">
      <stop offset="0%" style="stop-color:#7C3AED" stop-opacity="0.3"/>
      <stop offset="100%" style="stop-color:#7C3AED" stop-opacity="0.1"/>
    </linearGradient>
    <linearGradient id="layer2" x1="0%" y1="0%" x2="100%" y2="0%">
      <stop offset="0%" style="stop-color:#2563EB" stop-opacity="0.3"/>
      <stop offset="100%" style="stop-color:#2563EB" stop-opacity="0.1"/>
    </linearGradient>
    <linearGradient id="layer3" x1="0%" y1="0%" x2="100%" y2="0%">
      <stop offset="0%" style="stop-color:#06B6D4" stop-opacity="0.3"/>
      <stop offset="100%" style="stop-color:#06B6D4" stop-opacity="0.1"/>
    </linearGradient>
    <marker id="arrow" viewBox="0 0 10 10" refX="9" refY="5" markerWidth="6" markerHeight="6" orient="auto">
      <path d="M 0 0 L 10 5 L 0 10 z" fill="#7C3AED"/>
    </marker>
    <marker id="arrow2" viewBox="0 0 10 10" refX="9" refY="5" markerWidth="6" markerHeight="6" orient="auto">
      <path d="M 0 0 L 10 5 L 0 10 z" fill="#2563EB"/>
    </marker>
    <marker id="arrow3" viewBox="0 0 10 10" refX="9" refY="5" markerWidth="6" markerHeight="6" orient="auto">
      <path d="M 0 0 L 10 5 L 0 10 z" fill="#06B6D4"/>
    </marker>
  </defs>
  <rect width="860" height="440" fill="url(#archBg)" rx="12"/>

  <!-- Title -->
  <text x="430" y="34" text-anchor="middle" font-family="'Segoe UI', Arial" font-size="16" font-weight="700" fill="white" letter-spacing="2">SYSTEM ARCHITECTURE</text>
  <rect x="160" y="42" width="540" height="2" fill="#7C3AED" rx="1" opacity="0.7"/>

  <!-- Layer 1: GUI -->
  <rect x="30" y="58" width="800" height="105" rx="10" fill="url(#layer1)" stroke="#7C3AED" stroke-width="1.5"/>
  <text x="46" y="80" font-family="'Segoe UI', Arial" font-size="11" font-weight="700" fill="#a78bfa" letter-spacing="1">PRESENTATION LAYER — LieDetectorApp (Tkinter GUI · 1280×720)</text>

  <rect x="48" y="90" width="218" height="60" rx="8" fill="#7C3AED" opacity="0.25" stroke="#7C3AED" stroke-width="1"/>
  <text x="157" y="116" text-anchor="middle" font-family="'Segoe UI', Arial" font-size="12" font-weight="700" fill="white">Video Feed Panel</text>
  <text x="157" y="133" text-anchor="middle" font-family="'Segoe UI', Arial" font-size="10" fill="#a8b2d8">640 × 480 display</text>

  <rect x="286" y="90" width="218" height="60" rx="8" fill="#7C3AED" opacity="0.25" stroke="#7C3AED" stroke-width="1"/>
  <text x="395" y="116" text-anchor="middle" font-family="'Segoe UI', Arial" font-size="12" font-weight="700" fill="white">Controls &amp; Settings</text>
  <text x="395" y="133" text-anchor="middle" font-family="'Segoe UI', Arial" font-size="10" fill="#a8b2d8">Buttons · Sliders · Input</text>

  <rect x="524" y="90" width="278" height="60" rx="8" fill="#7C3AED" opacity="0.25" stroke="#7C3AED" stroke-width="1"/>
  <text x="663" y="116" text-anchor="middle" font-family="'Segoe UI', Arial" font-size="12" font-weight="700" fill="white">Metrics &amp; Graph Panel</text>
  <text x="663" y="133" text-anchor="middle" font-family="'Segoe UI', Arial" font-size="10" fill="#a8b2d8">Matplotlib canvas · Real-time charts</text>

  <!-- Arrow down to threading -->
  <line x1="430" y1="163" x2="430" y2="183" stroke="#7C3AED" stroke-width="2" marker-end="url(#arrow)"/>

  <!-- Layer 2: Threading -->
  <rect x="30" y="185" width="800" height="60" rx="10" fill="url(#layer2)" stroke="#2563EB" stroke-width="1.5"/>
  <text x="46" y="207" font-family="'Segoe UI', Arial" font-size="11" font-weight="700" fill="#60a5fa" letter-spacing="1">CONCURRENCY LAYER</text>
  <text x="430" y="225" text-anchor="middle" font-family="'Segoe UI', Arial" font-size="12" font-weight="600" fill="white">Background Video Thread  ·  Daemon  ·  threading.Lock (thread-safe)</text>
  <text x="430" y="240" text-anchor="middle" font-family="'Segoe UI', Arial" font-size="10" fill="#a8b2d8">GUI updates via Tkinter after() callbacks · deque(maxlen=10000) frame buffer</text>

  <!-- Arrow down to detection -->
  <line x1="430" y1="245" x2="430" y2="265" stroke="#2563EB" stroke-width="2" marker-end="url(#arrow2)"/>

  <!-- Layer 3: Detection Engine -->
  <rect x="30" y="267" width="800" height="150" rx="10" fill="url(#layer3)" stroke="#06B6D4" stroke-width="1.5"/>
  <text x="46" y="289" font-family="'Segoe UI', Arial" font-size="11" font-weight="700" fill="#67e8f9" letter-spacing="1">DETECTION ENGINE — EnhancedLieDetector</text>

  <!-- Sub-boxes in detection engine -->
  <rect x="48" y="298" width="148" height="104" rx="7" fill="#06B6D4" opacity="0.2" stroke="#06B6D4" stroke-width="1"/>
  <text x="122" y="320" text-anchor="middle" font-family="'Segoe UI', Arial" font-size="11" font-weight="700" fill="white">MediaPipe</text>
  <text x="122" y="336" text-anchor="middle" font-family="'Segoe UI', Arial" font-size="10" fill="#a8b2d8">FaceMesh</text>
  <text x="122" y="352" text-anchor="middle" font-family="'Segoe UI', Arial" font-size="10" fill="#67e8f9">468 landmarks</text>
  <text x="122" y="366" text-anchor="middle" font-family="'Segoe UI', Arial" font-size="9" fill="#a8b2d8">OpenCV capture</text>
  <text x="122" y="380" text-anchor="middle" font-family="'Segoe UI', Arial" font-size="9" fill="#a8b2d8">0.5× resize</text>

  <rect x="210" y="298" width="148" height="104" rx="7" fill="#06B6D4" opacity="0.2" stroke="#06B6D4" stroke-width="1"/>
  <text x="284" y="320" text-anchor="middle" font-family="'Segoe UI', Arial" font-size="11" font-weight="700" fill="white">Metric</text>
  <text x="284" y="336" text-anchor="middle" font-family="'Segoe UI', Arial" font-size="11" font-weight="700" fill="white">Extraction</text>
  <text x="284" y="354" text-anchor="middle" font-family="'Segoe UI', Arial" font-size="10" fill="#a8b2d8">EAR · Asymmetry</text>
  <text x="284" y="369" text-anchor="middle" font-family="'Segoe UI', Arial" font-size="10" fill="#a8b2d8">Blink Rate</text>
  <text x="284" y="384" text-anchor="middle" font-family="'Segoe UI', Arial" font-size="10" fill="#a8b2d8">Eye Movement</text>

  <rect x="372" y="298" width="148" height="104" rx="7" fill="#06B6D4" opacity="0.2" stroke="#06B6D4" stroke-width="1"/>
  <text x="446" y="320" text-anchor="middle" font-family="'Segoe UI', Arial" font-size="11" font-weight="700" fill="white">FER</text>
  <text x="446" y="336" text-anchor="middle" font-family="'Segoe UI', Arial" font-size="11" font-weight="700" fill="white">Emotion Engine</text>
  <text x="446" y="354" text-anchor="middle" font-family="'Segoe UI', Arial" font-size="10" fill="#a8b2d8">7-class detection</text>
  <text x="446" y="369" text-anchor="middle" font-family="'Segoe UI', Arial" font-size="10" fill="#a8b2d8">Weighted scoring</text>
  <text x="446" y="384" text-anchor="middle" font-family="'Segoe UI', Arial" font-size="10" fill="#67e8f9">fear/surprise/...</text>

  <rect x="534" y="298" width="148" height="104" rx="7" fill="#06B6D4" opacity="0.2" stroke="#06B6D4" stroke-width="1"/>
  <text x="608" y="320" text-anchor="middle" font-family="'Segoe UI', Arial" font-size="11" font-weight="700" fill="white">Micro-</text>
  <text x="608" y="336" text-anchor="middle" font-family="'Segoe UI', Arial" font-size="11" font-weight="700" fill="white">expression</text>
  <text x="608" y="354" text-anchor="middle" font-family="'Segoe UI', Arial" font-size="10" fill="#a8b2d8">Velocity analysis</text>
  <text x="608" y="369" text-anchor="middle" font-family="'Segoe UI', Arial" font-size="10" fill="#a8b2d8">468-pt motion</text>
  <text x="608" y="384" text-anchor="middle" font-family="'Segoe UI', Arial" font-size="10" fill="#67e8f9">2× threshold</text>

  <rect x="696" y="298" width="116" height="104" rx="7" fill="#7C3AED" opacity="0.3" stroke="#7C3AED" stroke-width="1.5"/>
  <text x="754" y="320" text-anchor="middle" font-family="'Segoe UI', Arial" font-size="11" font-weight="700" fill="white">Random</text>
  <text x="754" y="336" text-anchor="middle" font-family="'Segoe UI', Arial" font-size="11" font-weight="700" fill="white">Forest</text>
  <text x="754" y="354" text-anchor="middle" font-family="'Segoe UI', Arial" font-size="10" fill="#a78bfa">5 features</text>
  <text x="754" y="369" text-anchor="middle" font-family="'Segoe UI', Arial" font-size="10" fill="#a78bfa">Probability</text>
  <text x="754" y="384" text-anchor="middle" font-family="'Segoe UI', Arial" font-size="10" fill="#a78bfa">0–100%</text>

  <!-- Connectors inside detection layer -->
  <line x1="196" y1="350" x2="210" y2="350" stroke="#06B6D4" stroke-width="1.5" marker-end="url(#arrow3)"/>
  <line x1="358" y1="350" x2="372" y2="350" stroke="#06B6D4" stroke-width="1.5" marker-end="url(#arrow3)"/>
  <line x1="520" y1="350" x2="534" y2="350" stroke="#06B6D4" stroke-width="1.5" marker-end="url(#arrow3)"/>
  <line x1="682" y1="350" x2="696" y2="350" stroke="#06B6D4" stroke-width="1.5" marker-end="url(#arrow3)"/>

  <!-- Baseline annotation -->
  <text x="430" y="428" text-anchor="middle" font-family="'Segoe UI', Arial" font-size="10" fill="#6b7db3">Baseline calibration feeds deviation scores into the Random Forest feature vector</text>
</svg>
</div>

---

## 🔄 Data Flow

<div align="center">
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 860 180" width="860">
  <defs>
    <linearGradient id="dfBg" x1="0%" y1="0%" x2="100%" y2="100%">
      <stop offset="0%" style="stop-color:#0f0c29"/>
      <stop offset="100%" style="stop-color:#1a1040"/>
    </linearGradient>
    <marker id="dfArrow" viewBox="0 0 10 10" refX="9" refY="5" markerWidth="6" markerHeight="6" orient="auto">
      <path d="M 0 0 L 10 5 L 0 10 z" fill="#06B6D4"/>
    </marker>
  </defs>
  <rect width="860" height="180" fill="url(#dfBg)" rx="12"/>

  <!-- Title -->
  <text x="430" y="28" text-anchor="middle" font-family="'Segoe UI', Arial" font-size="14" font-weight="700" fill="white" letter-spacing="2">DATA FLOW PIPELINE</text>

  <!-- Nodes -->
  <g font-family="'Segoe UI', Arial" font-size="10">
    <!-- Webcam -->
    <rect x="14" y="55" width="90" height="56" rx="8" fill="#7C3AED" opacity="0.3" stroke="#7C3AED" stroke-width="1.5"/>
    <text x="59" y="79" text-anchor="middle" font-size="20" fill="#a78bfa">📷</text>
    <text x="59" y="97" text-anchor="middle" fill="white" font-weight="600">Webcam</text>
    <text x="59" y="110" text-anchor="middle" fill="#a8b2d8">USB / built-in</text>

    <line x1="104" y1="83" x2="118" y2="83" stroke="#06B6D4" stroke-width="1.5" marker-end="url(#dfArrow)"/>

    <!-- OpenCV -->
    <rect x="120" y="55" width="90" height="56" rx="8" fill="#2563EB" opacity="0.3" stroke="#2563EB" stroke-width="1.5"/>
    <text x="165" y="79" text-anchor="middle" font-size="18" fill="#60a5fa">🎞️</text>
    <text x="165" y="97" text-anchor="middle" fill="white" font-weight="600">OpenCV</text>
    <text x="165" y="110" text-anchor="middle" fill="#a8b2d8">0.5× resize</text>

    <line x1="210" y1="83" x2="224" y2="83" stroke="#06B6D4" stroke-width="1.5" marker-end="url(#dfArrow)"/>

    <!-- MediaPipe -->
    <rect x="226" y="55" width="100" height="56" rx="8" fill="#06B6D4" opacity="0.25" stroke="#06B6D4" stroke-width="1.5"/>
    <text x="276" y="79" text-anchor="middle" font-size="18" fill="#67e8f9">🗺️</text>
    <text x="276" y="97" text-anchor="middle" fill="white" font-weight="600">MediaPipe</text>
    <text x="276" y="110" text-anchor="middle" fill="#a8b2d8">468 landmarks</text>

    <line x1="326" y1="83" x2="340" y2="83" stroke="#06B6D4" stroke-width="1.5" marker-end="url(#dfArrow)"/>

    <!-- Metric Extraction -->
    <rect x="342" y="44" width="130" height="78" rx="8" fill="#7C3AED" opacity="0.25" stroke="#7C3AED" stroke-width="1.5"/>
    <text x="407" y="68" text-anchor="middle" fill="white" font-size="11" font-weight="700">Metric Extraction</text>
    <text x="407" y="84" text-anchor="middle" fill="#a8b2d8">EAR · Asymmetry</text>
    <text x="407" y="98" text-anchor="middle" fill="#a8b2d8">Blink · Eye Move</text>
    <text x="407" y="112" text-anchor="middle" fill="#a78bfa">+FER emotion</text>

    <line x1="472" y1="83" x2="486" y2="83" stroke="#06B6D4" stroke-width="1.5" marker-end="url(#dfArrow)"/>

    <!-- Baseline Comparison -->
    <rect x="488" y="55" width="108" height="56" rx="8" fill="#2563EB" opacity="0.25" stroke="#2563EB" stroke-width="1.5"/>
    <text x="542" y="78" text-anchor="middle" fill="white" font-size="11" font-weight="700">Baseline</text>
    <text x="542" y="93" text-anchor="middle" fill="white" font-size="11" font-weight="700">Deviation</text>
    <text x="542" y="108" text-anchor="middle" fill="#a8b2d8">5 feature vector</text>

    <line x1="596" y1="83" x2="610" y2="83" stroke="#06B6D4" stroke-width="1.5" marker-end="url(#dfArrow)"/>

    <!-- Random Forest -->
    <rect x="612" y="55" width="108" height="56" rx="8" fill="#06B6D4" opacity="0.25" stroke="#06B6D4" stroke-width="1.5"/>
    <text x="666" y="78" text-anchor="middle" fill="white" font-size="11" font-weight="700">Random</text>
    <text x="666" y="93" text-anchor="middle" fill="white" font-size="11" font-weight="700">Forest</text>
    <text x="666" y="108" text-anchor="middle" fill="#67e8f9">predict_proba()</text>

    <line x1="720" y1="83" x2="734" y2="83" stroke="#06B6D4" stroke-width="1.5" marker-end="url(#dfArrow)"/>

    <!-- Output -->
    <rect x="736" y="44" width="108" height="78" rx="8" fill="#7C3AED" opacity="0.35" stroke="#7C3AED" stroke-width="2"/>
    <text x="790" y="68" text-anchor="middle" fill="white" font-size="11" font-weight="700">GUI Output</text>
    <text x="790" y="84" text-anchor="middle" fill="#a78bfa">Deception %</text>
    <text x="790" y="98" text-anchor="middle" fill="#a8b2d8">Live graphs</text>
    <text x="790" y="112" text-anchor="middle" fill="#a8b2d8">CSV export</text>
  </g>

  <!-- Step labels -->
  <text x="430" y="155" text-anchor="middle" font-family="'Segoe UI', Arial" font-size="10" fill="#6b7db3">Each frame processed in background thread · GUI updates via Tkinter after() · Results exportable as CSV + text report</text>
</svg>
</div>

---

## 🛠️ Technology Stack

| Layer | Technology | Version | Role |
|---|---|---|---|
| **Runtime** | Python | 3.7+ | Core language |
| **Video Capture** | OpenCV (`opencv-python`) | ≥ 4.5.0 | Webcam access, frame preprocessing |
| **Face Landmarks** | MediaPipe | ≥ 0.8.9 | 468-point facial mesh detection |
| **Numerical** | NumPy | ≥ 1.19.0 | Geometric calculations, feature vectors |
| **Data Storage** | Pandas | ≥ 1.3.0 | Per-frame DataFrame, CSV export |
| **Visualization** | Matplotlib | ≥ 3.4.0 | Embedded real-time charts |
| **Machine Learning** | Scikit-learn | ≥ 0.24.0 | Random Forest Classifier |
| **Emotion AI** | FER | ≥ 22.4.0 | Deep-learning emotion recognition |
| **Image I/O** | Pillow | ≥ 8.0.0 | Frame conversion for Tkinter |
| **GUI** | Tkinter | built-in | Desktop application framework |
| **Optional** | dlib | ≥ 19.22.0 | Shape predictor (68-point model) |
| **Optional** | imutils | ≥ 0.5.4 | Image processing utilities |

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
| 🔒 **Thread-safe** | Background video thread with `threading.Lock` |

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
| `VIDEO_WIDTH` | `640` | Display panel width in pixels |
| `VIDEO_HEIGHT` | `480` | Display panel height in pixels |

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

## 📈 Performance

<div align="center">
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 860 200" width="860">
  <defs>
    <linearGradient id="perfBg" x1="0%" y1="0%" x2="100%" y2="100%">
      <stop offset="0%" style="stop-color:#0f0c29"/>
      <stop offset="100%" style="stop-color:#1a1040"/>
    </linearGradient>
    <linearGradient id="barFill1" x1="0%" y1="0%" x2="100%" y2="0%">
      <stop offset="0%" style="stop-color:#7C3AED"/>
      <stop offset="100%" style="stop-color:#06B6D4"/>
    </linearGradient>
    <linearGradient id="barFill2" x1="0%" y1="0%" x2="100%" y2="0%">
      <stop offset="0%" style="stop-color:#2563EB"/>
      <stop offset="100%" style="stop-color:#7C3AED"/>
    </linearGradient>
    <linearGradient id="barFill3" x1="0%" y1="0%" x2="100%" y2="0%">
      <stop offset="0%" style="stop-color:#06B6D4"/>
      <stop offset="100%" style="stop-color:#2563EB"/>
    </linearGradient>
  </defs>
  <rect width="860" height="200" fill="url(#perfBg)" rx="12"/>

  <text x="430" y="30" text-anchor="middle" font-family="'Segoe UI', Arial" font-size="14" font-weight="700" fill="white" letter-spacing="2">PERFORMANCE PROFILE</text>
  <rect x="240" y="38" width="380" height="2" fill="url(#barFill1)" rx="1" opacity="0.6"/>

  <!-- Stat cards -->
  <!-- Card 1: Frame Rate -->
  <rect x="20" y="54" width="190" height="130" rx="10" fill="#7C3AED" opacity="0.15" stroke="#7C3AED" stroke-width="1.5"/>
  <text x="115" y="82" text-anchor="middle" font-family="'Segoe UI', Arial" font-size="36" font-weight="800" fill="#a78bfa">15</text>
  <text x="115" y="100" text-anchor="middle" font-family="'Segoe UI', Arial" font-size="12" fill="#67e8f9">FPS (min spec)</text>
  <rect x="35" y="112" width="160" height="6" rx="3" fill="#1a1040"/>
  <rect x="35" y="112" width="80" height="6" rx="3" fill="url(#barFill1)"/>
  <text x="115" y="140" text-anchor="middle" font-family="'Segoe UI', Arial" font-size="11" fill="#a8b2d8">Processing Rate</text>
  <text x="115" y="158" text-anchor="middle" font-family="'Segoe UI', Arial" font-size="10" fill="#6b7db3">30 FPS on quad-core</text>
  <text x="115" y="174" text-anchor="middle" font-family="'Segoe UI', Arial" font-size="10" fill="#6b7db3">CPU with 0.5× scale</text>

  <!-- Card 2: Landmark Points -->
  <rect x="225" y="54" width="190" height="130" rx="10" fill="#2563EB" opacity="0.15" stroke="#2563EB" stroke-width="1.5"/>
  <text x="320" y="82" text-anchor="middle" font-family="'Segoe UI', Arial" font-size="36" font-weight="800" fill="#60a5fa">468</text>
  <text x="320" y="100" text-anchor="middle" font-family="'Segoe UI', Arial" font-size="12" fill="#67e8f9">Landmarks / Frame</text>
  <rect x="240" y="112" width="160" height="6" rx="3" fill="#1a1040"/>
  <rect x="240" y="112" width="152" height="6" rx="3" fill="url(#barFill2)"/>
  <text x="320" y="140" text-anchor="middle" font-family="'Segoe UI', Arial" font-size="11" fill="#a8b2d8">MediaPipe FaceMesh</text>
  <text x="320" y="158" text-anchor="middle" font-family="'Segoe UI', Arial" font-size="10" fill="#6b7db3">3D face mesh with</text>
  <text x="320" y="174" text-anchor="middle" font-family="'Segoe UI', Arial" font-size="10" fill="#6b7db3">sub-pixel precision</text>

  <!-- Card 3: Memory -->
  <rect x="430" y="54" width="190" height="130" rx="10" fill="#06B6D4" opacity="0.15" stroke="#06B6D4" stroke-width="1.5"/>
  <text x="525" y="82" text-anchor="middle" font-family="'Segoe UI', Arial" font-size="36" font-weight="800" fill="#67e8f9">10K</text>
  <text x="525" y="100" text-anchor="middle" font-family="'Segoe UI', Arial" font-size="12" fill="#67e8f9">Frame Buffer</text>
  <rect x="445" y="112" width="160" height="6" rx="3" fill="#1a1040"/>
  <rect x="445" y="112" width="100" height="6" rx="3" fill="url(#barFill3)"/>
  <text x="525" y="140" text-anchor="middle" font-family="'Segoe UI', Arial" font-size="11" fill="#a8b2d8">Rolling deque limit</text>
  <text x="525" y="158" text-anchor="middle" font-family="'Segoe UI', Arial" font-size="10" fill="#6b7db3">Bounded memory with</text>
  <text x="525" y="174" text-anchor="middle" font-family="'Segoe UI', Arial" font-size="10" fill="#6b7db3">automatic eviction</text>

  <!-- Card 4: Baseline -->
  <rect x="635" y="54" width="205" height="130" rx="10" fill="#7C3AED" opacity="0.15" stroke="#7C3AED" stroke-width="1.5"/>
  <text x="737" y="82" text-anchor="middle" font-family="'Segoe UI', Arial" font-size="36" font-weight="800" fill="#a78bfa">10s</text>
  <text x="737" y="100" text-anchor="middle" font-family="'Segoe UI', Arial" font-size="12" fill="#67e8f9">Calibration Time</text>
  <rect x="650" y="112" width="175" height="6" rx="3" fill="#1a1040"/>
  <rect x="650" y="112" width="58" height="6" rx="3" fill="url(#barFill1)"/>
  <text x="737" y="140" text-anchor="middle" font-family="'Segoe UI', Arial" font-size="11" fill="#a8b2d8">Baseline duration</text>
  <text x="737" y="158" text-anchor="middle" font-family="'Segoe UI', Arial" font-size="10" fill="#6b7db3">Outlier-filtered mean</text>
  <text x="737" y="174" text-anchor="middle" font-family="'Segoe UI', Arial" font-size="10" fill="#6b7db3">per-session only</text>
</svg>
</div>

---

## 📁 Project Structure

```
invictus/
├── invictus.py                           # Main application (GUI + detection engine)
│   ├── LieDetectorApp                    #   GUI layer (Tkinter)
│   └── EnhancedLieDetector               #   Detection engine
├── requirements.txt                      # Python dependencies
├── banner.svg                            # Project banner image
├── README.md                             # This documentation
├── shape_predictor_68_face_landmarks.dat # Pre-trained dlib model (optional)
├── wiki/                                 # Extended documentation
│   ├── Home.md
│   ├── Architecture.md
│   ├── Installation.md
│   ├── Usage.md
│   ├── Privacy.md
│   ├── Contributing.md
│   ├── Troubleshooting.md
│   └── Roadmap.md
└── .gitignore                            # Git ignore rules
```

---

## ♿ Accessibility

- **Resizable window:** The 1280×720 Tkinter GUI is fully resizable to accommodate different display sizes.
- **Screen reader notes:** The application is a desktop GUI and does not provide dedicated screen reader support in its current state. Users relying on assistive technology should be aware of this limitation.
- **Keyboard navigation:** Tkinter's default tab-order navigation is available for all interactive controls.
- **Color contrast:** Status text and metrics are displayed in high-contrast fonts against light-grey backgrounds.
- **Lighting sensitivity:** The system requires adequate facial visibility; users with conditions affecting facial expressiveness should be aware that accuracy may vary significantly.

---

## 🔒 Privacy & Security

- **Fully local processing:** All video, landmark data, and analysis results are processed on-device. No data is sent to external servers.
- **No persistent storage by default:** Webcam frames are held in an in-memory rolling deque and discarded automatically. Results are only written to disk when the user explicitly clicks "Save Results".
- **No telemetry:** The application contains no analytics, crash reporting, or usage tracking.
- **Webcam access:** The application requests access to the system webcam via OpenCV. The user must initiate camera access with the "Start Camera" button.
- **Exported files:** `results.csv` and `results_report.txt` are saved to the current working directory at the user's explicit request. They may contain biometric data and should be handled accordingly.
- **Research use only:** This tool is not validated for use in contexts where privacy laws govern biometric data collection (e.g., GDPR, CCPA, BIPA). Users are responsible for ensuring compliance with applicable regulations.

---

## 🗺️ Roadmap

| Priority | Feature | Description |
|---|---|---|
| 🔴 High | Validated ML dataset | Replace synthetic training data with real-world, ethically sourced dataset |
| 🔴 High | LSTM temporal modeling | Add sequence-based prediction for improved temporal context |
| 🟡 Medium | Optical flow microexpressions | Replace velocity heuristic with dense optical flow for better accuracy |
| 🟡 Medium | Audio channel | Voice stress analysis as a parallel detection channel |
| 🟡 Medium | Multi-face tracking | Support concurrent analysis of multiple subjects |
| 🟢 Low | Configurable models | Plugin architecture for swapping ML backends |
| 🟢 Low | Dark mode GUI | Optional dark theme for the Tkinter interface |
| 🟢 Low | Video file analysis | Support analyzing pre-recorded video files in addition to live webcam |

---

## 🎯 Design Principles

1. **Modularity** — `LieDetectorApp` (GUI) and `EnhancedLieDetector` (engine) are fully separated, allowing independent development and testing.
2. **Thread safety** — All shared state between the video thread and GUI thread is guarded by a `threading.Lock`. GUI updates are dispatched via Tkinter's `after()` mechanism.
3. **Bounded memory** — `deque(maxlen=MAX_FRAMES)` prevents unbounded memory growth during long sessions.
4. **Graceful degradation** — Optional dependencies (dlib, FER) fail silently with defaults. Missing face detection is handled with overlays, not crashes.
5. **Scientific honesty** — Every output is labelled "experimental" and accompanied by disclaimers. The system makes no claims of validated accuracy.
6. **Configurability** — Sensitivity, duration, and detection thresholds are exposed as user-adjustable parameters, not hardcoded.

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
