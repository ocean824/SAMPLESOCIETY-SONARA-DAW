# 2. AUDIO ENGINE ARCHITECTURE

## 2.1 Core Audio Engine Requirements

The foundation of SONARA is a robust, low-latency, real-time safe C++ audio engine.

| System | Required Implementation | Description |
| :--- | :--- | :--- |
| **Language** | C++ | Core engine for maximum performance |
| **DSP Framework** | JUCE | Industry-standard audio application framework |
| **Audio Threading** | Real-time safe | Lock-free, wait-free algorithms |
| **Buffering** | Multi-buffer architecture | Optimized for varied block sizes and DSP loads |
| **Plugin Sandbox** | Yes | Isolate third-party plugins (VST3/AU/CLAP) to prevent DAW crashes |
| **Low Latency Monitoring** | Yes | Direct hardware integration for recording |
| **Offline Rendering** | Yes | Faster-than-real-time mixdowns and stem exports |
| **Multi-Core Rendering** | Yes | Intelligent track and bus load distribution |
| **GPU-Assisted Processing** | Planned | Offload UI rendering and specific AI/DSP tasks |
| **Dynamic Resource Allocation** | Yes | Disable processing on silent tracks to save CPU |
| **Sample Accurate Automation** | Yes | Frame-perfect parameter modulation |
| **Sample Accurate Editing** | Yes | Zero-crossing detection and precise slicing |
| **Plugin Delay Compensation** | Yes | Automatic alignment of parallel processing chains |
| **Freeze/Bounce System** | Yes | Render tracks to audio instantly to free resources |
| **Autosave Recovery** | Yes | Robust background state saving without audio dropouts |

---

## 2.2 Advanced Engine Capabilities (ORPHEUS Enhancements)

The engine must natively support the ORPHEUS AI integration at a deep level.

| Capability | Description | Integration |
| :--- | :--- | :--- |
| **Neural Network Inference** | Real-time and offline execution of AI models (e.g., vocal synthesis, stem separation) | Hybrid Local/Cloud processing depending on user hardware |
| **ARA2 Support** | Audio Random Access integration for advanced pitch/time editors (Melodyne, VocALign) | Deep integration into the clip editor timeline |
| **CLAP Plugin Format** | Support for the modern Clever Audio Plug-in API | Enhanced multi-threading, non-destructive modulation, and faster scanning |
| **Spatial Audio / Dolby Atmos** | Object-based audio rendering, binaural monitoring, and multi-channel busing (7.1.4, 9.1.6) | Native 3D panner and renderer |
| **Video Sync Engine** | Frame-accurate video playback for post-production and film scoring | Integrated video player with SMPTE timecode support |
| **Unified Modulation System** | Advanced per-device and global modulation routing (LFOs, Envelopes, Macros) | Similar to Bitwig Studio's modular approach |

---

## 2.3 Plugin Architecture

SONARA must securely host external plugins while providing a rich internal suite.

* **Supported Formats:** VST3, AU (macOS), CLAP, ARA2
* **Legacy Support:** VST2 is **NOT** supported natively to ensure modern architecture stability (users must rely on wrappers if absolutely necessary).
* **Sandboxing:** Plugins run in isolated processes. A crashed plugin will display a "Plugin Crashed" UI overlay without affecting the main audio thread or other tracks.
* **Auto-Scan:** Fast, background plugin scanning on startup that caches results.
