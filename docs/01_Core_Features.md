# 1. CORE APPLICATION TYPE & HARDWARE SUPPORT

## 1.1 Core Identity
SONARA is a fully native desktop DAW application designed for maximum performance, stability, and professional audio production.

**SONARA is NOT:**
* A browser-based DAW
* An Electron-only wrapper software
* A simple plugin host shell
* A cloud-only AI platform

**SONARA MUST operate with the fluidity, depth, and reliability of industry standards such as:**
* Ableton Live
* Image-Line FL Studio
* Avid Technology Pro Tools
* Apple Inc. Logic Pro
* PreSonus Studio One
* Steinberg Cubase / Nuendo
* Cockos REAPER
* Bitwig Studio

**Platform Support:**
The software must install and run locally as native executables on both **Windows** and **macOS**, ensuring cross-platform compatibility for all project files.

**Core Capabilities:**
* Low-latency real-time audio processing
* Professional multi-track recording
* Deep external hardware integration
* Advanced plugin hosting (VST3, AU, CLAP, ARA2)
* Comprehensive MIDI and MPE device support
* High-performance DSP processing
* GPU acceleration for UI rendering and specific computational tasks
* Hybrid AI inference (Local on-device processing + Cloud offloading)

---

## 1.2 Audio Hardware Support

SONARA MUST SUPPORT a wide array of professional audio interfaces and protocols.

| Hardware Category | Required Support Level | Notes |
| :--- | :--- | :--- |
| **USB Audio Interfaces** | Full support | Class-compliant and custom drivers |
| **Thunderbolt Interfaces** | Full support | Ultra-low latency optimization |
| **PCIe Audio Interfaces** | Full support | High channel count DSP systems |
| **Aggregate Devices (Mac)** | Full support | Seamless multi-device clocking |
| **ASIO Drivers (Windows)** | Full support | Direct hardware access |
| **CoreAudio (macOS)** | Full support | Native Apple audio framework |
| **WASAPI (Windows)** | Full support | Modern Windows audio |
| **MIDI Controllers** | Full support | Plug-and-play mapping |
| **MPE Controllers** | Full support | Polyphonic expression (e.g., ROLI, LinnStrument) |
| **Control Surfaces** | Full support | Extensive protocol support |
| **Motorized Faders** | Full support | Two-way parameter feedback |
| **External DSP Hardware** | Planned | Integration with UAD, Antelope, etc. |
| **Digital Consoles** | Planned | Large format mixing desk integration |
| **ADAT Devices** | Planned | Optical expansion |
| **Dante Audio Networking** | Future | Audio over IP (AoIP) |
| **AVB Networking** | Future | Audio Video Bridging |

---

## 1.3 Audio Interface Implementation Features

The interface handling must be robust, reliable, and user-friendly.

| Feature | Required Implementation | Description |
| :--- | :--- | :--- |
| **Input/Output Selection** | Device browser | Clear, unified device selection matrix |
| **Sample Rate Switching** | Real-time supported | On-the-fly conversion and hardware sync |
| **Buffer Size Adjustment** | Adjustable from DAW | Direct control without opening driver panels |
| **Multi-Input Recording** | Unlimited | Limited only by hardware and disk speed |
| **Multi-Output Routing** | Unlimited | Complex busing and hardware sends |
| **Input Monitoring** | Low latency | Direct DAW monitoring with minimal delay |
| **Direct Monitoring Integration** | Supported | Hardware-level zero-latency monitoring |
| **Device Hot Swapping** | Supported | Plug/unplug interfaces without crashing |
| **Clock Sync Detection** | Supported | Automatic internal/external clock resolution |
| **Audio Driver Error Recovery** | Automatic | Silent restart of engine on driver dropout |
| **Device Profile Saving** | Supported | Save global hardware setups |
| **Per-Project Interface Recall** | Supported | Projects remember their specific I/O mapping |

---

## 1.4 Control Surface & Protocol Support

SONARA must communicate fluently with physical tactile controllers.

| Hardware / Protocol | Support Level | Notes |
| :--- | :--- | :--- |
| **MIDI Keyboards** | Full | Auto-mapping and scriptable |
| **Pad Controllers** | Full | Drum rack and clip launching integration |
| **MPE Controllers** | Full | High-resolution multi-dimensional control |
| **Launchpads** | Full | Session view and step sequencing |
| **Push-style Controllers** | Full | Deep hardware-to-DAW display integration |
| **Mackie Control Protocol** | Full | Industry standard transport and faders |
| **HUI Protocol** | Full | Legacy professional surface support |
| **Stream Deck** | Full | Native plugin for macro and workflow triggers |
| **TouchOSC** | Planned | Tablet/mobile custom interfaces |
| **OSC Protocol** | Planned | Open Sound Control for advanced networking |
| **EuCon** | Future | Avid high-end control surface protocol |
