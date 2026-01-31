---

# PRD: "Orchestral Orbits" – Audio-Reactive Celestial Simulator

## 1. Project Overview

A web-based tool that translates audio stems (bass, drums, melody) into N-body planetary simulations. The system will map musical frequencies to physical constants (gravity, mass, velocity) and render the result into a high-quality MP4 video.

## 2. Technical Constraints

* **Environment:** ChromeOS (Linux/Crostini).
* **Performance:** Must use **OffscreenCanvas** or **Headless Rendering** for video export to avoid hardware limitations during real-time playback.
* **Output:** H.264 MP4 (YouTube Standard: 1080p/4K at 30/60fps).

---

## 3. Core Feature Requirements

### A. Audio Analysis & Stem Splitting

* **Input:** User uploads `.mp3`, `.wav`, or `.m4a`.
* **Processing:** Use the **Web Audio API** (specifically `AnalyserNode`) for real-time preview.
* **Sync Logic:** * **Bass/Drums:** Map to "Impulses" (sudden changes in velocity  or explosive force).
* **Harmony:** Map to "Orbital Radius" or "Gravity Constant" .
* **Melody:** Map to "Visual Trails" or "Particle Emission."



### B. The Physics Engine (The "Brain")

* **Algorithm:** 4th Order Runge-Kutta (RK4) or Velocity-Verlet.
* **N-Body Logic:** Every "instrument" is a celestial body. The mass of the "Drum Planet" increases on every beat, pulling the "Melody Satellites" closer.
* **Accuracy:** Must maintain conservation of energy so orbits don't drift unless the music dictates it.

### C. Visual Theming & Shaders

* **Presets:** * **Neon:** High bloom, emissive materials, dark vacuum.
* **Ocean:** Fluid-like trails, soft blues/teals, refraction.
* **Glitch:** Post-processing passes with RGB shift and vertex displacement based on audio distortion.


* **Customization:** Full HEX control for planets, trails, and background starfields.

### D. Export & Rendering (The "Workhorse")

* **Non-Real-Time Rendering:** Since Chromebooks have limited GPUs, the developer must implement a **frame-by-frame capture** (e.g., using `CCapture.js` or `WebCodecs API`).
* **Process:** The simulation runs "offline" (slower than real-time) to ensure every physics calculation and visual frame is captured perfectly before encoding to MP4.

---

## 4. Functional Specifications & User Flow

| Step | Action | Feature Requirement |
| --- | --- | --- |
| **1** | **Upload** | Drag-and-drop audio. Backend/Browser analyzes BPM and frequency bands. |
| **2** | **Configure** | Assign audio bands to physics (e.g., "Bass = Gravity Intensity"). |
| **3** | **Style** | Select "Glitch" theme. Adjust particle trail length. |
| **4** | **Preview** | Lower-resolution WebGL preview (Three.js) for real-time tweaking. |
| **5** | **Render** | Headless render to `.mp4`. |

---

## 5. Developer Implementation Stack (Suggested)

* **Frontend:** React or Vue.js.
* **3D Engine:** `Three.js` (using `ShaderMaterial` for high-performance audio-reactivity).
* **Audio Processing:** `Meyda.js` (for feature extraction like Loudness, Centroid, and Mel-frequency cepstral coefficients).
* **Video Encoding:** `FFmpeg.wasm` (to stitch frames into MP4 locally on the Chromebook).

---

## 6. Physics-to-Music Mapping Logic (for the Dev)

To achieve the "Art" aspect, the developer should use the following mapping:

* **Low Pass Filter (Bass):** Modulates the Mass  of the central "Sun" object.
* **High Pass Filter (Highs):** Modulates the "Emissive Intensity" of the trails.
* **Transients (Drums):** Trigger localized "Gravitational Waves" (distorting space-time grid).

---
