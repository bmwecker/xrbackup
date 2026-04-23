# 🌌 Advanced Web AR Framework (Portable Backup)

This repository is a **comprehensive technical backup** of a high-fidelity, cross-platform Augmented Reality (AR) web application. It is designed to be fully portable, decoupled from any local environment, and ready to be "loaded" by any AI coding agent.

## 🚀 The Mission
The goal of this framework is to provide a single-file, zero-dependency (using CDN) AR experience that works flawlessly on iOS (Quick Look), Android (WebXR), and older devices (Magic Window fallback).

---

## 📁 Repository Structure

### 1. [Core Application (`core/index.html`)](core/index.html)
The heart of the project. A monolithic HTML5 file containing:
- **Three.js Engine**: Custom rendering loop.
- **WebXR Logic**: Real-world hit-testing for Android.
- **iOS Fallback**: Integration with Apple's native AR Quick Look.
- **i18n System**: Dynamic multi-language support (English, Russian, Hebrew) with native **RTL support**.
- **UI/UX Layer**: Premium Glassmorphism design system on a pure black background.

### 2. [Configuration & Deployment (`config/`)](config/)
- **`config/_headers`**: Critical security and MIME-type headers for Cloudflare/Netlify/Vercel.
- **`config/render.yaml`**: Deployment blueprint for Render.com, ensuring `.usdz` files are served correctly.

---

## 💡 Key Technical Patterns (For AI Agents)

### 🧩 Pattern A: The Triple-Tier AR Entry
The code implements a robust discovery logic:
1. **iOS Check**: If `isIOS`, it displays a native "AR Quick Look" badge.
2. **WebXR Check**: If supported, it attempts to initialize an `immersive-ar` session with `hit-test`.
3. **Legacy Fallback**: If neither works, it combines the device's camera feed (`getUserMedia`) with gyroscope data (`deviceorientation`) to create a "Magic Window".

### 🌍 Pattern B: Localization with RTL
Instead of separate pages, use a centralized `i18n` dictionary. 
**Crucial for Hebrew**: 
- Setting `document.dir = 'rtl'` is mandatory.
- Use `data-i18n` attributes for easy text swapping without affecting DOM structure.

### 🎨 Pattern C: Premium Glassmorphism
To achieve the "premium" feel requested:
- **Background**: Always `#000000`.
- **Frosted Glass**: `backdrop-filter: blur(10px)` + `rgba(255,255,255,0.05)`.
- **Transitions**: Every screen change must be smoothed with `opacity` transitions.

### 📦 Pattern D: Asset Normalization
Never trust the scale of an exported `.glb`. The code includes a normalization function that:
1. Computes the `Box3` of the model.
2. Centers it.
3. Scales it relative to the real world (e.g., 1.2 meters high).
4. Anchors the bottom to `y=0`.

---

## 🛠 How to Use This Backup
If you are an agent taking over this project:
1. **Read `core/index.html`**: It contains the complete logic with line-by-line pedagogical comments.
2. **Setup Server**: Use the files in `config/` to ensure your server doesn't block the AR viewer.
3. **Asset Swap**: Replace `mesh.glb` and `model.usdz` in your project root. The code will handle centering and scaling automatically.

---
*Backup Version: 2.0 (High Fidelity)*
*Decoupled from local storage. References: [XR Backup Repo](https://github.com/bmwecker/xrbackup.git)*
