# SONARA DAW + ORPHEUS AI: The Unified Production Intelligence System

> **Organization:** SAMPLESOCIETY
> **Project:** SONARA DAW & ORPHEUS AI — Standalone Audio Workstation & Intelligence Core
> **Status:** Strategic Blueprint / Full System Architecture
> **Last Updated:** April 2026

---

## Table of Contents
1. [Vision & Core Philosophy](#vision--core-philosophy)
2. [The 12+ Domain Architecture](#the-12-domain-architecture)
3. [Global Tech Stack](#global-tech-stack)
4. [Audio Engine & DSP Framework](#audio-engine--dsp-framework)
5. [ORPHEUS AI Sub-Agent Architecture](#orpheus-ai-sub-agent-architecture)
6. [Advanced DAW Capabilities](#advanced-daw-capabilities)
7. [End-to-End Workflow](#end-to-end-workflow)
8. [CodeSpring Implementation Roadmap](#codespring-implementation-roadmap)
9. [Deep Dive Documents](#deep-dive-documents)

---

## Vision & Core Philosophy

SONARA is the apex desktop audio environment for SAMPLESOCIETY. It is designed as a standalone, natively compiled, high-performance Digital Audio Workstation (DAW) that absorbs the entire modern music production lifecycle.

Its identity is not built around "just hosting plugins" — its identity is built around **creative acceleration and unified intelligence**. It exists to replace the fragmented ecosystem of DAWs, standalone AI generators, spectral repair tools, and mastering suites with ONE cohesive organism.

### The 6 Core Principles
1. **Native Performance is Sovereign**: No browser wrappers, no Electron shells. The C++ audio thread is sacred and must remain lock-free, allocation-free, and real-time safe.
2. **Intelligence is Integrated, Not Bolted On**: ORPHEUS AI is not a chatbot; it is a multi-modal agent embedded directly into the routing matrix, piano roll, and mixer.
3. **Audio is Elastic**: Time, pitch, and formants are fully malleable. Time stretching and key analysis are foundational, not afterthoughts.
4. **Repair Before Enhancement**: Spectral editing, dialogue isolation, and artifact removal exist natively in the timeline.
5. **Spatial by Default**: Stereo is a legacy format. Object-based Dolby Atmos and binaural rendering are native bus types.
6. **Collaboration is Real-Time**: Project files are fluid. Cloud sync and real-time multi-user editing are built into the core protocol.

---

## The 12+ Domain Architecture

SONARA is not a simple sequencer. It is an organism built from tightly connected domains that handle everything from low-level DSP to cloud-based neural synthesis.

### 1. The Hardware & I/O Domain
Handles the physical interface. Supports USB, Thunderbolt, PCIe, ASIO, CoreAudio, and WASAPI. Manages aggregate devices, real-time sample rate switching, and automatic driver error recovery without crashing the engine.

### 2. The Engine & Routing Domain
The C++ JUCE core. Manages the `AudioProcessorGraph`, multi-core load balancing, and plugin sandboxing (VST3, AU, CLAP, ARA2). Ensures that if a third-party plugin faults, the sandbox dies, but the DAW survives.

### 3. The Elastic Audio Domain
Handles all time and pitch manipulation.
- **Time Stretching**: Multi-algorithm engine (transient-preserving for drums, tonal-preserving for vocals, polyphonic for full mixes).
- **Key & Tempo Analysis**: Real-time structural analysis of imported audio, automatically mapping it to the session grid and chord track.

### 4. The Arrangement & Timeline Domain
The linear canvas. Supports clip-based editing, take lanes (comping), batch crossfades, clip gain, and scratch pads (alternate arrangements). Integrates a full video sync engine with SMPTE timecode for post-production.

### 5. The MIDI & Notation Domain
The composition layer.
- **Piano Roll**: GPU-accelerated, MPE-ready, with universal pitch slide and harmonic collision highlighting.
- **Score Editor**: Full standard music notation, bidirectional MIDI-to-notation conversion, and MusicXML export.

### 6. The Vocal & Spectral Domain
The surgical layer.
- **Vocal Tuning**: Melodyne-style pitch blobs, formant editing, and polyphonic separation.
- **Spectral Repair**: iZotope RX-style spectrogram editing, AI de-noise, de-click, and dialogue isolation.

### 7. The Mixing & Spatial Domain
The summing layer. Features unlimited tracks/busses, sidechain routing, and a visual routing matrix.
- **Spatial Audio**: Native Dolby Atmos object renderer, 3D panner, and 7.1.4/9.1.6 busing.

### 8. The ORPHEUS Synthesis Domain
The generative layer. Neural vocal synthesis (Synthesizer V style), phoneme editing, breath generation, and full-track audio codec generation (Suno/Udio style) executed via local ONNX or cloud API.

### 9. The ORPHEUS Mix & Master Domain
The analytical layer. Smart EQ masking resolution, dynamic balancing, and LUFS-targeted AI mastering for specific platforms (Spotify, Apple Music, Broadcast).

### 10. The ORPHEUS Decision & Logic Domain
The orchestrator. A local LLM (Natural Language Interface) that parses user intent (e.g., *"Make this sound cinematic"*) and routes the command to the correct sub-model (MIDI generation, FX routing, etc.).

### 11. The Control Surface Domain
The tactile layer. Deep, bi-directional integration with MIDI keyboards, MPE controllers (ROLI), Mackie Control, HUI, and Stream Deck macros.

### 12. The Collaboration & Cloud Domain
The multiplayer layer. Real-time session syncing, remote stem sharing, timestamped feedback comments, and cloud version history.

---

## Global Tech Stack

SONARA relies on a modern, high-performance tech stack to execute its architecture:

| Category | Technology | Purpose |
|----------|------------|---------|
| **Core Engine** | C++ 20 / JUCE 8 | Real-time audio processing, DSP graph, UI framework |
| **Plugin Formats** | VST3, AU, CLAP, ARA2 | Third-party extension hosting and deep integration |
| **Local AI Inference** | ONNX Runtime / TensorRT | Zero-latency execution of EQ, pitch, and NLI models |
| **Cloud AI Inference** | Python, FastAPI, PyTorch | Heavy compute (Stem separation, full track generation) |
| **Scripting API** | Python 3.11, Lua | User macros, custom workflows, AI-generated scripts |
| **Graphics/UI** | OpenGL / Metal / Vulkan | GPU-accelerated rendering for Piano Roll and Spectrogram |
| **Database/State** | SQLite | Local session metadata, asset indexing, and user memory |
| **Collaboration** | WebSockets, gRPC | Real-time multi-user editing and state synchronization |

---

## Audio Engine & DSP Framework

### Real-Time Safety Constraints
To prevent audio dropouts (glitches/pops), the audio thread MUST adhere to strict real-time constraints:
* **No Memory Allocation**: No `new`, `malloc`, or `std::vector::push_back` on the audio thread.
* **No Blocking I/O**: No file reading/writing or network requests during `processBlock`.
* **No Priority Inversion**: Avoid mutexes that might block the audio thread waiting for the UI thread. Use lock-free ring buffers.

### Time Stretching & Pitch Shifting
SONARA implements a state-of-the-art phase vocoder and granular synthesis engine.
- **Rhythmic Mode**: Preserves transient sharpness for drums and percussion.
- **Tonal Mode**: Preserves phase coherence for vocals and monophonic instruments.
- **Complex Mode**: High-fidelity polyphonic stretching for full mixes.
- **Formant Preservation**: Independent control over pitch and formants to prevent the "chipmunk" effect during extreme transposition.

### Key Analysis & Chord Track
- **Real-Time Detection**: Imported audio is instantly analyzed for key, scale, and tempo.
- **Chord Track**: A global harmonic ruler. MIDI and Audio clips can be locked to the Chord Track, automatically reharmonizing (pitch-shifting/transposing) when the global chord changes.

---

## ORPHEUS AI Sub-Agent Architecture

ORPHEUS is not a single model; it is an orchestrated swarm of specialized sub-agents.

| Sub-Agent | Primary Role | Inference Mode |
|---|---|---|
| **ORPHEUS-NLI** | Natural Language Interface. Parses text/voice commands and routes to tools. | Local (Quantized) |
| **ORPHEUS-Vocal** | Neural vocal synthesis, phoneme generation, and emotion-preserving tuning. | Local / Cloud |
| **ORPHEUS-Mix** | Analyzes frequency masking, suggests EQ cuts, and balances dynamics. | Local |
| **ORPHEUS-Master** | Applies limiting, tonal balance, and targets specific LUFS levels. | Local |
| **ORPHEUS-Stem** | High-fidelity source separation (Vocals, Drums, Bass, Other). | Local (GPU) / Cloud |
| **ORPHEUS-Arrange**| Generates song structures, transitions, and fills based on motifs. | Cloud |
| **ORPHEUS-Harmony**| Generates chords, voice leading, and multi-part vocal harmonies. | Local |
| **ORPHEUS-Repair** | AI de-noise, de-click, de-hum, and spectral reconstruction. | Local |

---

## Advanced DAW Capabilities

### Spectral Editing (The iZotope RX Absorption)
SONARA features a native Spectrogram view within the audio clip editor. Users can visually identify and lasso unwanted artifacts (sirens, mouth clicks, fret noise) and apply AI-driven spectral repair to interpolate the missing data from surrounding frequencies.

### Notation & Scoring (The Cubase/Sibelius Absorption)
A full Score Editor is integrated. MIDI data is instantly transcribed into standard music notation. Supports articulations, dynamics, lyrics, and expression maps. Changes in the Score Editor reflect instantly in the Piano Roll, and vice versa.

### Spatial Audio (The Dolby Atmos Absorption)
Stereo is no longer the limit. SONARA includes a native object-based renderer.
- **3D Panner**: Place audio objects in a 3D hemisphere.
- **Binaural Downmix**: Monitor complex 7.1.4 Atmos mixes on standard headphones.
- **ADM Export**: Deliver broadcast-ready Audio Definition Model files directly to streaming services.

---

## End-to-End Workflow

**The SONARA Production Lifecycle:**
1. **Ideation**: User inputs a text prompt to ORPHEUS-Arrange to generate a basic chord progression and drum groove.
2. **Recording**: User records live guitar. The Engine handles low-latency monitoring.
3. **Analysis**: The Elastic Audio Domain detects the tempo and key of the guitar, locking it to the grid.
4. **Vocal Synthesis**: User types lyrics into ORPHEUS-Vocal. A neural voice model generates the lead vocal.
5. **Repair**: User notices background hum in the guitar. ORPHEUS-Repair analyzes the noise profile and removes it via the Spectrogram.
6. **Arrangement**: User drags a chorus block in the Arranger. ORPHEUS automatically generates a riser and drum fill for the transition.
7. **Mixing**: User asks ORPHEUS-Mix to "fix the mud." The AI detects masking between the bass and kick and applies dynamic EQ.
8. **Spatialization**: User opens the 3D Panner and automates a synth lead to fly over the listener's head in Dolby Atmos.
9. **Mastering**: User selects "Spotify Target." ORPHEUS-Master applies limiting to hit -14 LUFS.
10. **Delivery**: The project is exported, and stems are automatically uploaded to the SAMPLESOCIETY cloud.

---

## CodeSpring Implementation Roadmap

For the CodeSpring orchestrator, follow these phases to build the SONARA architecture:

### Phase 1: The C++ Foundation & CodeSpring Setup
1. Initialize the JUCE 8 project structure.
2. Implement the `AudioDeviceManager` and `AudioProcessorGraph`.
3. Set up the CodeSpring PRD synchronization and mindmap generation.
4. **Deliverable**: A standalone app that can pass audio from input to output with zero latency.

### Phase 2: The Timeline & Elastic Audio
1. Build the Arrangement View UI (Tracks, Clips, Transport).
2. Integrate the phase vocoder for time stretching and pitch shifting.
3. Implement real-time key and tempo analysis algorithms.
4. **Deliverable**: Ability to import audio, stretch it to tempo, and pitch-shift it without artifacts.

### Phase 3: The MIDI & Plugin Sandbox
1. Build the GPU-accelerated Piano Roll.
2. Implement the IPC (Inter-Process Communication) plugin sandbox for VST3 and CLAP.
3. Build the Stock Plugin Suite scaffolding.
4. **Deliverable**: Ability to load third-party synths, sequence them via MIDI, and prevent crashes.

### Phase 4: ORPHEUS AI Integration
1. Embed ONNX Runtime into the C++ engine.
2. Implement the Natural Language Interface (NLI) routing layer.
3. Connect the ORPHEUS-Mix, ORPHEUS-Vocal, and ORPHEUS-Repair sub-models.
4. **Deliverable**: The DAW can respond to text commands and execute AI audio processing locally.

### Phase 5: Spatial, Spectral, and Score
1. Implement the Spectrogram rendering and spectral editing tools.
2. Build the Score Editor and MIDI-to-notation transcription logic.
3. Integrate the Dolby Atmos object renderer and 3D panner.
4. **Deliverable**: A fully featured, professional-grade, immersive audio workstation.

---

## Deep Dive Documents

This repository contains detailed research, architecture, and specification documents. Use the links below to navigate directly to specific areas of the SONARA DAW platform.

### 🌟 The Master Blueprint
* [**SONARA_MASTER_SPEC.md**](./SONARA_MASTER_SPEC.md) — The definitive 12-domain implementation blueprint with tech stack, instructions, and transferable architecture patterns.
* [**ROADMAP.md**](./ROADMAP.md) — The 7-phase development roadmap.
* [**CONTRIBUTING.md**](./CONTRIBUTING.md) — Code standards and real-time safety rules.

### 🏛️ Architecture & Engine
* [**architecture/engine_spec.md**](./architecture/engine_spec.md) — The C++/JUCE core, multi-threading, and plugin sandboxing.
* [**architecture/orpheus_ai_spec.md**](./architecture/orpheus_ai_spec.md) — The ORPHEUS sub-model routing and inference strategy.
* [**ai_models/model_registry.md**](./ai_models/model_registry.md) — Hardware requirements and formats for all AI models.

### 🎛️ Features & Workflows
* [**features/piano_roll_spec.md**](./features/piano_roll_spec.md) — GPU rendering, MPE, and AI melody generation.
* [**features/mixer_spec.md**](./features/mixer_spec.md) — Routing, busing, and AI gain staging.
* [**features/vocal_engine_spec.md**](./features/vocal_engine_spec.md) — Pitch blobs, phoneme editing, and neural synthesis.
* [**features/arrangement_view_spec.md**](./features/arrangement_view_spec.md) — Comping, clip gain, and AI structural generation.

### 🔌 Extensibility
* [**plugins/plugin_dev_guide.md**](./plugins/plugin_dev_guide.md) — JUCE templates and the ORPHEUS integration API.
* [**scripts/README.md**](./scripts/README.md) — Python and Lua scripting API for session automation.
* [**docs/06_Stock_Plugins.md**](./docs/06_Stock_Plugins.md) — The complete list of native instruments and effects.

---

**SONARA DAW + ORPHEUS AI — Built by SAMPLESOCIETY. Designed for the future of audio.**
