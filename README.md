# SONARA DAW + ORPHEUS AI: The Unified Production Intelligence System

> **Organization:** SAMPLESOCIETY
> **Project:** SONARA DAW & ORPHEUS AI — Standalone Audio Workstation & Intelligence Core
> **Status:** Strategic Blueprint / Full System Architecture
> **Last Updated:** April 2026

---

## Table of Contents

| Section | Description |
|---------|-------------|
| [Vision & Core Philosophy](#vision--core-philosophy) | The 6 foundational principles behind every architectural decision |
| [Core Application Type](#core-application-type) | What SONARA is, what it is not, and what it must match |
| [Audio Hardware Support](#audio-hardware-support) | Full hardware compatibility matrix |
| [Audio Interface Implementation](#audio-interface-implementation) | I/O feature requirements |
| [Control Surface Support](#control-surface-support) | MIDI, MPE, Mackie, HUI, Stream Deck |
| [Audio Engine Architecture](#audio-engine-architecture) | C++/JUCE core, real-time safety, plugin formats |
| [Full DAW Feature Absorption Matrix](#full-daw-feature-absorption-matrix) | FL Studio, Ableton, Studio One, Logic, Pro Tools, Reason, Cubase/Nuendo, Reaper, Bitwig |
| [AI Tool Absorption Matrix](#ai-tool-absorption-matrix) | Synthesizer V, Melodyne, iZotope RX, Ozone, Vocoflex, Lalal.ai, Kontakt |
| [ORPHEUS AI Architecture](#orpheus-ai-architecture) | Sub-agent roster, inference modes, NLI routing |
| [ORPHEUS Full Feature List](#orpheus-full-feature-list) | All 13 capability categories |
| [ORPHEUS Command Examples](#orpheus-command-examples) | Natural language commands and expected behaviors |
| [Stock Plugin Suite](#stock-plugin-suite) | Instruments, mixing plugins, AI plugins |
| [Extended Feature Specifications](#extended-feature-specifications) | Spatial audio, post-production, collaboration, notation, live performance |
| [Global Tech Stack](#global-tech-stack) | Full implementation technology table |
| [End-to-End Workflow](#end-to-end-workflow) | 10-step production lifecycle |
| [CodeSpring Implementation Roadmap](#codespring-implementation-roadmap) | 6-phase build plan with deliverables |
| [Target Product Goal](#target-product-goal) | What SONARA replaces, what ORPHEUS becomes |
| [Deep Dive Documents](#deep-dive-documents) | All internal spec and architecture files |

---

## Vision & Core Philosophy

SONARA is the apex desktop audio environment for SAMPLESOCIETY. It is designed as a standalone, natively compiled, high-performance Digital Audio Workstation that absorbs the entire modern music production lifecycle into a single organism.

Its identity is not built around "just hosting plugins" — its identity is built around **creative acceleration and unified intelligence**. It exists to replace the fragmented ecosystem of DAWs, standalone AI generators, spectral repair tools, and mastering suites with ONE cohesive platform.

### The 6 Core Principles

1. **Native Performance is Sovereign**: No browser wrappers, no Electron shells. The C++ audio thread is sacred and must remain lock-free, allocation-free, and real-time safe at all times.
2. **Intelligence is Integrated, Not Bolted On**: ORPHEUS AI is not a chatbot sidebar; it is a multi-modal agent embedded directly into the routing matrix, piano roll, mixer, and timeline.
3. **Audio is Elastic**: Time, pitch, and formants are fully malleable. Time stretching and key analysis are foundational capabilities, not afterthoughts.
4. **Repair Before Enhancement**: Spectral editing, dialogue isolation, and artifact removal exist natively in the timeline before any processing chain is applied.
5. **Spatial by Default**: Stereo is a legacy format. Object-based Dolby Atmos and binaural rendering are native bus types, not third-party add-ons.
6. **Collaboration is Real-Time**: Project files are fluid. Cloud sync and real-time multi-user editing are built into the core session protocol.

---

## Core Application Type

SONARA is a **fully native desktop DAW application** built for professional audio production on Windows and macOS.

### SONARA is NOT:
- A browser-based DAW
- An Electron-only wrapper application
- A simple plugin host shell
- A cloud-only AI platform

### SONARA MUST operate with the performance and depth of:

| Reference DAW | Key Capability Absorbed |
|:---|:---|
| Ableton Live | Session View, Warping, Follow Actions, MPE |
| Image-Line FL Studio | Piano Roll, Pattern Workflow, Per-Note Expression |
| Avid Pro Tools | Recording Reliability, Playlist Comping, Post-Production |
| Apple Logic Pro | Smart Controls, Flex Time, Score Editor, Stock Plugins |
| PreSonus Studio One | ARA Workflow, Project Page, Scratch Pads, Take Comping |
| Steinberg Cubase / Nuendo | Expression Maps, Chord Track, VariAudio, ADR, Surround |
| Cockos REAPER | Scripting API, Deep Customization, Lightweight Efficiency |
| Bitwig Studio | Modulation System, Hybrid Devices, Per-Note Expression |
| Reason Studios Reason | Virtual Rack, Cable Routing, Combinators |

### Platform Requirements

The application must install locally and run as a native executable on both **Windows** and **macOS**, with all project files fully cross-platform compatible. Core capabilities include low-latency real-time audio processing, professional multi-track recording, external hardware integration, advanced plugin hosting (VST3, AU, CLAP, ARA2), comprehensive MIDI and MPE device support, high-performance DSP processing, GPU acceleration for UI rendering and specific DSP tasks, hybrid AI inference (local on-device plus cloud offloading), spatial audio (Dolby Atmos, binaural), video sync for post-production and film scoring, and real-time collaboration capabilities.

---

## Audio Hardware Support

| Hardware Category | Required Support Level | Notes |
|:---|:---|:---|
| USB Audio Interfaces | Full | Class-compliant and custom driver |
| Thunderbolt Interfaces | Full | Ultra-low latency optimization |
| PCIe Audio Interfaces | Full | High channel count DSP systems |
| Aggregate Devices (Mac) | Full | Seamless multi-device clocking |
| ASIO Drivers (Windows) | Full | Direct hardware access |
| CoreAudio (macOS) | Full | Native Apple audio framework |
| WASAPI (Windows) | Full | Modern Windows audio API |
| MIDI Controllers | Full | Plug-and-play mapping |
| MPE Controllers | Full | Polyphonic expression (ROLI, LinnStrument, etc.) |
| Control Surfaces | Full | Extensive protocol support |
| Motorized Faders | Full | Two-way parameter feedback |
| External DSP Hardware | Planned | UAD, Antelope, Apogee DSP integration |
| Digital Consoles | Planned | Large format mixing desk integration |
| ADAT Devices | Planned | Optical I/O expansion |
| Dante Audio Networking | Future | Audio over IP (AoIP) for large studio setups |
| AVB Networking | Future | Audio Video Bridging standard |

---

## Audio Interface Implementation

| Feature | Required Implementation | Description |
|:---|:---|:---|
| Input Device Selection | Device browser | Clear, unified device selection matrix |
| Output Device Selection | Device browser | Clear, unified device selection matrix |
| Sample Rate Switching | Real-time supported | On-the-fly conversion and hardware sync |
| Buffer Size Adjustment | Adjustable from DAW | Direct control without opening driver panels |
| Multi-Input Recording | Unlimited | Limited only by hardware and disk speed |
| Multi-Output Routing | Unlimited | Complex busing and hardware sends |
| Input Monitoring | Low latency | Direct DAW monitoring with minimal delay |
| Direct Monitoring Integration | Supported | Hardware-level zero-latency monitoring |
| Device Hot Swapping | Supported | Plug/unplug interfaces without crashing |
| Clock Sync Detection | Supported | Automatic internal/external clock resolution |
| Audio Driver Error Recovery | Automatic | Silent restart of engine on driver dropout |
| Device Profile Saving | Supported | Save global hardware setups |
| Per-Project Interface Recall | Supported | Projects remember their specific I/O mapping |

---

## Control Surface Support

| Hardware / Protocol | Support Level | Notes |
|:---|:---|:---|
| MIDI Keyboards | Full | Auto-mapping and scriptable |
| Pad Controllers | Full | Drum rack and clip launching integration |
| MPE Controllers | Full | High-resolution multi-dimensional control |
| Launchpads | Full | Session view and step sequencing |
| Push-style Controllers | Full | Deep hardware-to-DAW display integration |
| Mackie Control Protocol | Full | Industry standard transport and faders |
| HUI Protocol | Full | Legacy professional surface support |
| Stream Deck | Full | Native plugin for macro and workflow triggers |
| TouchOSC | Planned | Tablet/mobile custom interfaces |
| OSC Protocol | Planned | Open Sound Control for advanced networking |
| EuCon | Future | Avid high-end control surface protocol |

---

## Audio Engine Architecture

### Core Engine Requirements

| System | Required Implementation | Description |
|:---|:---|:---|
| Language | C++ 20 | Core engine for maximum performance |
| DSP Framework | JUCE 8 | Industry-standard audio application framework |
| Audio Threading | Real-time safe | Lock-free, wait-free algorithms |
| Buffering | Multi-buffer architecture | Optimized for varied block sizes |
| Plugin Sandbox | Yes | Isolate plugins via IPC to prevent DAW crashes |
| Low Latency Monitoring | Yes | Direct hardware integration for recording |
| Offline Rendering | Yes | Faster-than-real-time mixdowns |
| Multi-Core Rendering | Yes | Intelligent track and bus load distribution |
| GPU-Assisted Processing | Planned | Offload UI rendering and AI/DSP tasks |
| Dynamic Resource Allocation | Yes | Disable processing on silent tracks |
| Sample Accurate Automation | Yes | Frame-perfect parameter modulation |
| Sample Accurate Editing | Yes | Zero-crossing detection and precise slicing |
| Plugin Delay Compensation | Yes | Automatic alignment of parallel chains |
| Freeze/Bounce System | Yes | Render tracks to audio to free resources |
| Autosave Recovery | Yes | Background state saving without dropouts |

### Plugin Format Support

| Format | Support Level | Notes |
|:---|:---|:---|
| VST3 | Full | Primary plugin format for Windows and macOS |
| AU (Audio Units) | Full | Native macOS plugin format |
| CLAP | Full | Modern open-source format with superior multi-threading |
| ARA2 | Full | Deep integration for pitch/time editors (Melodyne, VocALign) |
| AAX | Future | Avid Pro Tools format (requires Avid licensing) |

### Advanced Engine Capabilities

| Capability | Description |
|:---|:---|
| Neural Network Inference | Real-time and offline execution of AI models (ONNX Runtime / TensorRT) |
| Spatial Audio / Dolby Atmos | Object-based audio rendering, binaural monitoring, multi-channel busing (7.1.4, 9.1.6) |
| Video Sync Engine | Frame-accurate video playback with SMPTE timecode support |
| Unified Modulation System | Advanced per-device and global modulation routing |
| Real-Time Collaboration | Shared session state over local network or cloud |
| Time Stretching Engine | Phase vocoder + granular synthesis: Rhythmic (transient-preserving), Tonal (phase-coherent), Complex (polyphonic) |
| Key & Tempo Analysis | Real-time structural analysis of imported audio, auto-mapping to session grid and Chord Track |
| Formant Preservation | Independent pitch/formant control to prevent artifacts during extreme transposition |

### Real-Time Safety Constraints

To prevent audio dropouts (glitches/pops), the audio thread MUST adhere to strict real-time constraints at all times:

- **No Memory Allocation**: No `new`, `malloc`, or `std::vector::push_back` on the audio thread.
- **No Blocking I/O**: No file reading/writing or network requests during `processBlock`.
- **No Priority Inversion**: Avoid mutexes that might block the audio thread waiting for the UI thread. Use lock-free ring buffers for all UI-to-audio communication.
- **No System Calls**: Avoid `sleep()`, `printf()`, or any OS-level blocking calls.
- **Lock-Free Data Structures**: All parameter changes from the UI thread must pass through a lock-free FIFO queue before reaching the audio thread.

---

## Full DAW Feature Absorption Matrix

### A. FL Studio Implementation

| FL Studio Feature | SONARA Base Implementation | ORPHEUS Enhancement |
|:---|:---|:---|
| Fast Piano Roll | GPU accelerated piano roll engine | AI-assisted MIDI editing and melody generation |
| Slide Notes | Universal pitch slide system | Genre-aware glide shaping |
| Ghost Notes | Cross-track ghost rendering | Harmonic collision analysis |
| Note Coloring | Harmonic/track grouping | Emotional color mapping |
| Pattern Workflow | Hybrid clip-pattern system | AI arrangement building |
| Chord Stamps | Chord generation engine | Advanced reharmonization and voice leading |
| Strum Tool | Humanized timing engine | Guitar realism system |
| Randomizer | Controlled variation engine | Intelligent mutation and variation generation |
| Per-Note Expression | MPE/per-note automation | Emotion-aware phrasing |
| Fast Sequencing | Quick-draw MIDI editing | AI loop generation |

### B. Ableton Live Implementation

| Ableton Feature | SONARA Base Implementation | ORPHEUS Enhancement |
|:---|:---|:---|
| Session View | Clip-launch environment | AI live performance generation and adaptive sets |
| Arrangement View | Linear timeline | AI structural arrangement and transition building |
| Warping | Advanced warp engine | Phrase-aware time stretching |
| Audio Stretching | Multi-algorithm engine (Rhythmic, Tonal, Complex) | Artifact reduction AI |
| Instrument Racks | Rack architecture | AI rack generation and layered sound design |
| Effect Racks | Parallel chain routing | Auto FX chain building based on sonic goals |
| Macros | Universal parameter mapping | Intelligent macro assignment |
| Follow Actions | Rule-trigger engine | Adaptive sequencing and generative logic |
| MPE Support | Full MPE editing | AI expression generation |
| Ableton Link | Tempo sync protocol | Real-time live performance sync |

### C. Studio One Implementation

| Studio One Feature | SONARA Base Implementation | ORPHEUS Enhancement |
|:---|:---|:---|
| ARA Workflow | Native embedded note editing | AI vocal correction and timing |
| Melodyne Integration | Internal pitch engine | Emotion-preserving tuning |
| Drag & Drop | Unified drag system | Contextual smart routing |
| Project Page | Mastering workspace | AI mastering assistant |
| Scratch Pads | Alternate arrangements | AI arrangement comparison and scoring |
| Take Comping | Take lane system | Best-take scoring AI |
| Clip Gain | Real-time gain editing | AI vocal leveling |

### D. Logic Pro Implementation

| Logic Feature | SONARA Base Implementation | ORPHEUS Enhancement |
|:---|:---|:---|
| Smart Controls | Macro abstraction system | AI parameter learning |
| Flex Time | Elastic timing engine | Groove-aware correction |
| Flex Pitch | Pitch blob editing | Emotion-preserving tuning |
| Automation Workflow | Unified automation lanes | Auto automation generation |
| CPU Optimization | Dynamic resource manager | AI load balancing |
| Stock Plugins | Native DSP suite | Adaptive presets |
| Score Editor | Full notation environment | AI orchestration and standard music notation |
| Drummer Track | AI drummer engine | Drummer personality modeling |
| Environment | Visual MIDI routing | AI-generated MIDI processing chains |

### E. Pro Tools Implementation

| Pro Tools Feature | SONARA Base Implementation | ORPHEUS Enhancement |
|:---|:---|:---|
| Recording Reliability | Professional recording engine | Session diagnostics |
| Audio Editing | Sample-accurate editing | Smart cleanup |
| Playlist Comping | Take management system | AI comp generation |
| Crossfades | Batch fade engine | Automatic fade logic |
| Routing | Advanced mixer architecture | Auto bus organization |
| Post Production | Video sync support | AI dialog cleanup and automated ADR |
| Elastic Audio | Time-stretching engine | Phrase-aware stretching |
| Clip Groups | Grouped clip management | AI grouping by instrument family |

### F. Reason Implementation

| Reason Feature | SONARA Base Implementation | ORPHEUS Enhancement |
|:---|:---|:---|
| Virtual Rack | Modular signal environment | AI modular generation |
| Cable Routing | Optional visual routing | Auto-routing logic |
| Combinators | Multi-device containers | AI chain building |
| Custom Actions | Workflow automation system | Natural-language macros |
| CV Modulation | Control voltage routing | AI modulation mapping |

### G. Cubase / Nuendo Implementation

| Cubase/Nuendo Feature | SONARA Base Implementation | ORPHEUS Enhancement |
|:---|:---|:---|
| Expression Maps | Articulation mapping engine | AI articulation selection |
| Score Editor | Notation environment | AI orchestration and standard music notation |
| Chord Track | Harmonic engine | Adaptive reharmonization |
| VariAudio | Embedded vocal editor | Intelligent vocal correction |
| Surround Sound | Multi-channel audio buses (7.1, 7.1.4, 9.1.6) | AI Dolby Atmos spatial mixing |
| ADR System | Automated Dialog Replacement workflow | AI speech-to-text marker generation |
| MixConsole | Advanced routing matrix | AI gain staging and bus organization |
| Logical Editor | Rule-based MIDI processing | AI-generated MIDI transformations |
| Render in Place | Track freezing and bouncing | AI-assisted stem preparation |

### H. Reaper Implementation

| Reaper Feature | SONARA Base Implementation | ORPHEUS Enhancement |
|:---|:---|:---|
| Lightweight Efficiency | Modular runtime loading | AI optimization |
| Scripting | Internal scripting API (Python/Lua) | AI-generated scripts for custom workflows |
| Deep Customization | Workspace engine | Personalized layouts based on user habits |
| Item-Based Editing | Clip-centric editing model | AI clip organization |
| Flexible Routing | Unlimited send/receive matrix | AI routing suggestions |
| ReaScript | Full scripting environment | ORPHEUS-generated automation scripts |

### I. Bitwig Studio Implementation

| Bitwig Feature | SONARA Base Implementation | ORPHEUS Enhancement |
|:---|:---|:---|
| Modulation System | Universal modulation graph | AI modulation generation |
| Hybrid Devices | Device abstraction layer | AI chain mutation |
| Per-Note Expression | Expression lane engine | Emotional expression mapping |
| The Grid | Modular synthesis environment | AI patch generation |
| Note Expression | Per-note parameter editing | AI performance shaping |
| Clip Launcher | Session view with follow actions | AI generative clip sequencing |

---

## AI Tool Absorption Matrix

### A. Synthesizer V / ACE Studio Features (Vocal Synthesis)

| Feature | SONARA Base Implementation | ORPHEUS Enhancement |
|:---|:---|:---|
| AI Singing | Neural vocal synthesis | Context-aware singing generation |
| Phoneme Editing | Editable phoneme timeline | Auto pronunciation correction |
| Breath Editing | Breath lane system | Natural breath generation |
| Emotion Curves | Emotion automation graph | Genre-aware emotion shaping |
| Vibrato Editing | Vibrato modulation lane | Adaptive realism |
| Timing Editing | Syllable timing editor | Groove-aware timing |
| Vocal Layers | Harmony stack engine | Auto harmony generation |
| Vocal Transition Smoothing | Transition engine | Emotional phrase continuity |
| Singer Management | Voice model manager | AI singer blending and morphing |
| Multilingual Singing | Language phoneme engine | Accent adaptation |
| Dynamic Expression | Expression curves | Emotional realism |

### B. Melodyne Features (Pitch/Timing Correction)

| Feature | SONARA Base Implementation | ORPHEUS Enhancement |
|:---|:---|:---|
| Pitch Blobs | Native note editing | Emotional pitch retention |
| Polyphonic Editing | Multi-note editor | Harmonic separation AI |
| Formant Editing | Formant lanes | Character preservation |
| Timing Editing | Timing graph editor | Groove-aware correction |
| Vibrato Editing | Vibrato shaping | Human realism |
| Dynamics Editing | Amplitude editing | AI leveling |
| DNA Direct Note Access | Polyphonic audio-to-MIDI | Chord extraction and reharmonization |

### C. iZotope RX Features (Audio Repair)

| Feature | SONARA Base Implementation | ORPHEUS Enhancement |
|:---|:---|:---|
| De-Noise | AI noise reduction | Context-aware cleanup |
| De-Click | Spectral click repair | Batch restoration |
| De-Hum | Hum profile engine | Auto hum detection |
| Spectral Repair | Spectrogram editor with lasso selection | AI reconstruction of missing frequencies |
| Mouth Click Removal | Artifact cleaner | Vocal cleanup automation |
| Clipping Repair | Clipping restoration | Dynamic rebuild |
| Dialogue Isolation | Source separation | AI voice extraction |
| De-Reverb | Reverb tail reduction | Room acoustics removal |
| De-Plosive | Plosive transient removal | Broadcast-quality vocal cleanup |
| Ambience Match | Room tone matching | Seamless edit point blending |

### D. LANDR / Ozone / Sonible Features (Mixing & Mastering)

| Feature | SONARA Base Implementation | ORPHEUS Enhancement |
|:---|:---|:---|
| AI Mastering | Mastering engine | Adaptive mastering (Ozone 11 style) |
| Tonal Balance | Frequency analysis | Reference matching |
| LUFS Targeting | Loudness engine | Platform-aware mastering (Spotify -14, Apple -16, YouTube -14, Broadcast -23) |
| Stereo Analysis | Stereo imaging tools | Spatial enhancement |
| Dynamic Analysis | Compression advisor | Intelligent balancing (smart:EQ 4 / Sonible style) |
| Frequency Masking | Masking detection | Dynamic EQ auto-resolution |
| Limiter Intelligence | Transparent limiting | True peak compliance (-1 dBTP) |

### E. Vocoflex Features (Voice Morphing)

| Feature | SONARA Base Implementation | ORPHEUS Enhancement |
|:---|:---|:---|
| Voice Morphing | Neural morph engine | Emotion retention |
| Timbre Transfer | Timbre transformation | Style-aware conversion |
| Gender Conversion | Formant remapping | Natural transitions |
| Accent Adaptation | Pronunciation layer | AI dialect shaping |

### F. Lalal.ai / RipX / Suno / Udio Features (Generation & Separation)

| Feature | SONARA Base Implementation | ORPHEUS Enhancement |
|:---|:---|:---|
| Stem Splitting | Multi-band source separation (Vocals, Drums, Bass, Other, Piano, Guitar) | Intelligent reconstruction |
| Instrument Isolation | Source separation | Harmonic rebuilding |
| Note Extraction | Audio note mapping | Performance reconstruction |
| Stem Manipulation | Stem editor | AI remix assistance |
| Full Track Generation | Audio codec generation | Text-to-audio integration (Suno/Udio style) |

### G. Kontakt / Omnisphere / EastWest / Superior Drummer Features

| Feature | SONARA Base Implementation | ORPHEUS Enhancement |
|:---|:---|:---|
| Multisampling | Advanced sampler engine | AI articulation selection |
| Round Robins | Variation system | Human realism |
| Velocity Layers | Dynamic sample engine | Emotion-aware dynamics |
| Legato Transitions | Transition engine | Phrase-aware rendering |
| Drum Humanization | Groove realism | Drummer personality modeling |
| Orchestral Articulations | Articulation maps | AI orchestration |
| Hybrid Synthesis | Multi-engine synths | AI sound design |

---

## ORPHEUS AI Architecture

ORPHEUS is not a single model. It is an orchestrated swarm of specialized sub-agents, each with a defined role, inference mode, and hardware requirement. The Natural Language Interface (NLI) layer parses user intent and routes commands to the correct sub-model.

### ORPHEUS Sub-Agent Roster

| Sub-Agent | Primary Role | Inference Mode | VRAM Requirement |
|:---|:---|:---|:---|
| **ORPHEUS-NLI** | Natural Language Interface. Parses text/voice commands and routes to tools. | Local (Quantized LLM) | 4 GB |
| **ORPHEUS-Vocal** | Neural vocal synthesis, phoneme generation, and emotion-preserving tuning. | Local / Cloud | 8 GB |
| **ORPHEUS-Mix** | Analyzes frequency masking, suggests EQ cuts, and balances dynamics. | Local (ONNX) | 2 GB |
| **ORPHEUS-Master** | Applies limiting, tonal balance, and targets specific LUFS levels per platform. | Local (ONNX) | 2 GB |
| **ORPHEUS-Stem** | High-fidelity source separation (Vocals, Drums, Bass, Other, Piano, Guitar). | Local (GPU) / Cloud | 8 GB |
| **ORPHEUS-Arrange** | Generates song structures, transitions, fills, and riser automation. | Cloud | Cloud |
| **ORPHEUS-Harmony** | Generates chords, voice leading, and multi-part vocal harmonies. | Local | 2 GB |
| **ORPHEUS-Repair** | AI de-noise, de-click, de-hum, de-reverb, and spectral reconstruction. | Local (ONNX) | 4 GB |
| **ORPHEUS-Performer** | MIDI micro-timing and velocity humanization. Drummer personality modeling. | Local | 1 GB |
| **ORPHEUS-Replace** | Audio-to-MIDI conversion and instrument sound substitution. | Local / Cloud | 4 GB |

### Inference Strategy

ORPHEUS uses a hybrid local/cloud inference strategy. Low-latency tasks (EQ analysis, pitch correction, NLI routing) run locally via ONNX Runtime or TensorRT. Heavy compute tasks (stem separation, full track generation, large vocal synthesis models) are offloaded to cloud inference when a local GPU with sufficient VRAM is not available. The system automatically detects available hardware and routes accordingly, with a user-configurable preference for privacy-first local-only operation.

### ORPHEUS IPC Bridge

```
User Text/Voice Input
        │
        ▼
ORPHEUS-NLI (Intent Parser)
        │
        ▼
Sub-Model Router ──────────────────────────────────────────────────────┐
        │                                                               │
   Local Inference                                              Cloud Inference
   (ONNX / TensorRT)                                           (FastAPI / PyTorch)
        │                                                               │
        └───────────────────────────────────────────────────────────────┘
                                    │
                                    ▼
                        DAW Engine IPC Bridge
                                    │
                                    ▼
                        AudioProcessorGraph (C++ / JUCE)
```

---

## ORPHEUS Full Feature List

ORPHEUS MUST SUPPORT the following capability categories:

| Capability Category | Features |
|:---|:---|
| DAW Control | Routing, track creation, fades, plugin loading, bussing, session organization |
| MIDI Intelligence | Melody generation, harmony, orchestration, voice leading, chord progression generation |
| Vocal Intelligence | Singing synthesis, harmonies, tuning, timing editing, breath generation |
| Mix Intelligence | EQ suggestions, frequency masking resolution, balancing, dynamic control |
| Arrangement Intelligence | Song structure generation, transition building, riser automation, fill generation |
| Performance Intelligence | Human realism, groove extraction, articulation switching, drummer personality |
| Workflow Automation | Macro chains, reusable workflows, custom script generation (Python/Lua) |
| Audio Repair | Cleanup, restoration, de-noising, de-clicking, de-humming, spectral reconstruction |
| Session Management | Organization, naming, coloring, template generation, bus routing |
| Plugin Intelligence | Plugin parameter manipulation, smart macro assignment, preset generation |
| Memory Systems | User workflow learning, personalized UI adaptation, session history |
| Educational Assistance | Explain edits, music theory analysis, mix breakdowns, production tutorials |
| Live Assistance | Real-time AI accompaniment, adaptive backing tracks, live looping intelligence |

---

## ORPHEUS Command Examples

| Command | Expected System Behavior |
|:---|:---|
| *"Tune these vocals naturally."* | Pitch correction applied while preserving emotional formants and vibrato. |
| *"Make this sound cinematic."* | Adds orchestral layers, applies spatial depth/reverb, and widens the stereo image. |
| *"Generate neo-soul chords."* | Creates an advanced harmonic progression with 7ths, 9ths, and specific voice leading. |
| *"Fix mud in the mix."* | Analyzes frequency masking in the 200–500 Hz range and applies dynamic EQ correction. |
| *"Replace these strings with realistic strings."* | Extracts MIDI from audio and reconstructs the performance using high-quality multisamples with proper articulations. |
| *"Create harmonies."* | Analyzes the lead vocal and chord track to generate 3-part backing harmonies. |
| *"Humanize these drums."* | Applies micro-timing shifts and velocity variations based on a modeled drummer personality. |
| *"Master this for Spotify."* | Applies limiting, EQ, and compression to hit -14 LUFS with -1 dBTP true peak. |
| *"Organize this session."* | Automatically routes tracks to busses, applies standard naming conventions, and color-codes by instrument group. |
| *"Extract the vocals from this sample."* | Runs the AI stem splitter to isolate the vocal track with minimal artifacts. |
| *"Write a chord progression in the style of D'Angelo."* | Generates a neo-soul harmonic progression with characteristic extensions and voice leading. |
| *"Transcribe this audio to MIDI."* | Converts audio performance to editable MIDI notes with velocity and timing preserved. |
| *"Fix the noise in this recording."* | Profiles the noise floor and applies spectral subtraction to remove background noise. |
| *"Make this mix wider."* | Applies mid/side processing and binaural widening while preserving mono compatibility. |
| *"Generate a drum fill for this transition."* | Analyzes the groove and generates a contextually appropriate fill leading into the next section. |

---

## Stock Plugin Suite

### A. Instruments

| Plugin | Function | Description |
|:---|:---|:---|
| SONARA Synth One | Wavetable synth | High-resolution wavetable engine with deep modulation |
| SONARA Analog | Analog synth | Virtual analog modeling with non-linear drift |
| SONARA FM | FM synth | 6-operator frequency modulation synthesizer |
| SONARA Granular | Granular synthesis | Real-time audio mangling and texture generation |
| SONARA Orchestra | Orchestral workstation | Deep-sampled strings, brass, and woodwinds |
| SONARA Drums | Drum workstation | Acoustic and electronic drum kits with built-in sequencing |
| SONARA Bass | Bass engine | Hybrid physical modeling and sample-based bass |
| SONARA Piano | Piano engine | Modeled acoustic grand and upright pianos |
| SONARA Sampler | Deep sampler | Multi-layer, round-robin capable sampling engine |
| SONARA Choir | Choir engine | Symphonic and intimate vocal ensembles |

### B. Mixing Plugins

| Plugin | Function | Description |
|:---|:---|:---|
| SONARA EQ | Dynamic EQ | Transparent and linear phase equalization |
| SONARA Comp | Compressor | VCA, FET, and Opto circuit models |
| SONARA MB | Multiband processing | Precise crossover multi-band compression/expansion |
| SONARA Verb | Reverb | Algorithmic and convolution reverb engine |
| SONARA Delay | Delay | Tape, analog, and digital delay algorithms |
| SONARA Tape | Tape saturation | Authentic tape machine emulation with wow/flutter |
| SONARA Spatial | Stereo imaging | Mid/Side processing and binaural widening |
| SONARA Console | Console emulation | Classic mixing desk summing and crosstalk |
| SONARA Transient | Transient shaper | Attack/sustain control for drums and percussion |
| SONARA Gate | Noise gate | Intelligent gating with sidechain filtering |

### C. AI Plugins (ORPHEUS Powered)

| Plugin | Function | Description |
|:---|:---|:---|
| ORPHEUS Mix | AI mixing | Intelligent track balancing and masking resolution |
| ORPHEUS Master | AI mastering | Target-based mastering chains |
| ORPHEUS Vocal | Vocal cleanup | Automated de-breath, de-click, and leveling |
| ORPHEUS Harmony | Harmony generation | Real-time backing vocal generation |
| ORPHEUS Arrange | Arrangement generation | Structural block building and transition fills |
| ORPHEUS Performer | Human realism | MIDI micro-timing and velocity humanization |
| ORPHEUS Replace | Instrument replacement | Audio-to-MIDI and sound substitution |
| ORPHEUS Stem | Stem splitting | High-fidelity audio source separation |

---

## Extended Feature Specifications

### Spatial Audio & Immersive Production

| Feature | Description |
|:---|:---|
| Dolby Atmos Renderer | Native object-based audio renderer with binaural monitoring |
| 3D Panner | Visual 3D panning interface for object-based mixing |
| Binaural Monitoring | Headphone-based monitoring of immersive mixes |
| Multi-Channel Busing | Support for 7.1, 7.1.4, 9.1.6 and custom channel configurations |
| ADM Export | Audio Definition Model file export for broadcast delivery |

### Video & Post-Production

| Feature | Description |
|:---|:---|
| Video Track | Import and playback of video files (H.264, ProRes, etc.) |
| SMPTE Timecode | Frame-accurate synchronization with external video systems |
| ADR System | Automated Dialog Replacement with cue sheet generation |
| Foley Workspace | Dedicated workspace for sound design and foley |
| Loudness Compliance | Broadcast loudness standards (EBU R128, ATSC A/85) |

### Collaboration & Cloud

| Feature | Description |
|:---|:---|
| Real-Time Collaboration | Multiple users editing the same session simultaneously |
| Cloud Project Sync | Automatic backup and version history to cloud storage |
| Stem Sharing | Export and share stems directly from the DAW |
| Session Comments | Timestamped comment system for remote feedback |

### Notation & Score

| Feature | Description |
|:---|:---|
| Score Editor | Full music notation editor integrated into the DAW |
| MIDI-to-Notation | Automatic conversion of MIDI to readable sheet music |
| Notation Export | Export to MusicXML, PDF, and other notation formats |
| Playback from Score | Direct audio playback from the notation editor |

### Live Performance

| Feature | Description |
|:---|:---|
| Setlist Manager | Organize and sequence songs for live performance |
| Ableton Link | Sync tempo with other applications and hardware |
| MIDI Clock Output | Sync external hardware sequencers and drum machines |
| Live Looping | Real-time audio and MIDI loop recording and overdubbing |

---

## Global Tech Stack

| Category | Technology | Purpose |
|:---|:---|:---|
| **Core Engine** | C++ 20 / JUCE 8 | Real-time audio processing, DSP graph, UI framework |
| **Plugin Formats** | VST3, AU, CLAP, ARA2 | Third-party extension hosting and deep integration |
| **Local AI Inference** | ONNX Runtime / TensorRT | Zero-latency execution of EQ, pitch, and NLI models |
| **Cloud AI Inference** | Python 3.11, FastAPI, PyTorch | Heavy compute (stem separation, full track generation) |
| **Scripting API** | Python 3.11, Lua | User macros, custom workflows, AI-generated scripts |
| **Graphics/UI** | OpenGL / Metal / Vulkan | GPU-accelerated rendering for Piano Roll and Spectrogram |
| **Database/State** | SQLite | Local session metadata, asset indexing, and user memory |
| **Collaboration** | WebSockets, gRPC | Real-time multi-user editing and state synchronization |
| **AI Orchestration** | LangGraph / PydanticAI | ORPHEUS NLI routing and sub-model orchestration |
| **Voice Synthesis** | VITS2 / DiffSinger / ONNX | Neural singing and speech synthesis models |
| **Stem Separation** | Demucs v4 / HTDemucs | High-fidelity 6-stem audio source separation |
| **Pitch Correction** | Custom phase vocoder | Real-time pitch shifting with formant preservation |
| **Time Stretching** | Phase vocoder + granular | Rhythmic, tonal, and complex algorithm modes |
| **Notation** | LilyPond / MusicXML | Score rendering and notation export |

---

## End-to-End Workflow

**The SONARA Production Lifecycle:**

1. **Ideation**: User inputs a text prompt to ORPHEUS-Arrange to generate a basic chord progression and drum groove.
2. **Recording**: User records live guitar. The Engine handles low-latency monitoring via direct hardware integration.
3. **Analysis**: The Elastic Audio Domain detects the tempo and key of the guitar, locking it to the session grid and Chord Track.
4. **Vocal Synthesis**: User types lyrics into ORPHEUS-Vocal. A neural voice model generates the lead vocal with correct phonemes and emotion curves.
5. **Repair**: User notices background hum in the guitar recording. ORPHEUS-Repair profiles the noise floor and removes it via the Spectrogram editor.
6. **Arrangement**: User drags a chorus block in the Arranger. ORPHEUS automatically generates a riser and drum fill for the transition.
7. **Mixing**: User asks ORPHEUS-Mix to "fix the mud." The AI detects masking between the bass and kick in the 200–400 Hz range and applies dynamic EQ.
8. **Spatialization**: User opens the 3D Panner and automates a synth lead to move across the listener's head in Dolby Atmos.
9. **Mastering**: User selects "Spotify Target." ORPHEUS-Master applies limiting to hit -14 LUFS with -1 dBTP true peak.
10. **Delivery**: The project is exported as a stereo master, Dolby Atmos ADM file, and individual stems, then automatically uploaded to the SAMPLESOCIETY cloud.

---

## CodeSpring Implementation Roadmap

For the CodeSpring orchestrator, follow these phases to build the SONARA architecture in order. Each phase has a concrete deliverable that must be verified before moving to the next.

### Phase 1: C++ Foundation & Engine Core
1. Initialize the JUCE 8 project structure for Windows and macOS.
2. Implement the `AudioDeviceManager` and `AudioProcessorGraph` with multi-core load balancing.
3. Build the plugin sandbox using IPC (Inter-Process Communication) for VST3 and CLAP isolation.
4. Implement the lock-free ring buffer for UI-to-audio thread communication.
5. **Deliverable**: A standalone app that passes audio from input to output with zero glitches and can load a VST3 plugin without crashing the host if the plugin faults.

### Phase 2: Timeline, Elastic Audio & Key Analysis
1. Build the Arrangement View UI (Tracks, Clips, Transport, Automation Lanes).
2. Integrate the phase vocoder for time stretching (Rhythmic, Tonal, Complex modes) with formant preservation.
3. Implement real-time key and tempo analysis algorithms using onset detection and chroma features.
4. Build the Chord Track as a global harmonic ruler that MIDI and Audio clips can lock to.
5. **Deliverable**: Ability to import audio, detect its key and tempo, stretch it to the session BPM, and pitch-shift it without artifacts.

### Phase 3: MIDI, Piano Roll & Plugin Ecosystem
1. Build the GPU-accelerated Piano Roll with MPE support, ghost notes, and per-note expression lanes.
2. Implement the Score Editor with bidirectional MIDI-to-notation conversion and MusicXML export.
3. Build the Session View (clip launcher) and Follow Actions engine.
4. Implement the Modulation Graph for universal parameter routing.
5. **Deliverable**: Ability to sequence MIDI, view it as notation, launch clips in session view, and modulate any parameter from any source.

### Phase 4: ORPHEUS AI Integration
1. Embed ONNX Runtime into the C++ engine for local model execution.
2. Implement the Natural Language Interface (NLI) routing layer using a quantized local LLM.
3. Connect ORPHEUS-Mix, ORPHEUS-Vocal, ORPHEUS-Repair, and ORPHEUS-Performer sub-models.
4. Build the FastAPI cloud inference bridge for ORPHEUS-Stem and ORPHEUS-Arrange.
5. **Deliverable**: The DAW responds to text commands and executes AI audio processing. "Fix the mud" applies dynamic EQ. "Tune these vocals" applies pitch correction.

### Phase 5: Spatial, Spectral, Repair & Post-Production
1. Implement the Spectrogram rendering and spectral editing tools (lasso selection, AI interpolation).
2. Integrate the Dolby Atmos object renderer, 3D Panner, and binaural monitoring.
3. Build the Video Track with SMPTE timecode sync and ADR cue sheet generation.
4. Implement broadcast loudness compliance (EBU R128, ATSC A/85).
5. **Deliverable**: A fully featured, professional-grade, immersive audio workstation capable of post-production delivery.

### Phase 6: Collaboration, Cloud & Stock Plugin Suite
1. Implement real-time collaboration via WebSockets and gRPC session state sync.
2. Build cloud project backup, version history, and stem sharing.
3. Implement the full Stock Plugin Suite (10 instruments, 10 mixing plugins, 8 AI plugins).
4. Build the Python/Lua scripting API for user workflow automation.
5. **Deliverable**: A complete, shippable production environment with all native instruments, AI plugins, and multi-user collaboration.

---

## Target Product Goal

SONARA should replace the need for:

| Replaced Tool Category | Examples |
|:---|:---|
| Multiple DAWs | Ableton, FL Studio, Logic, Pro Tools, Cubase |
| Multiple AI generators | Suno, Udio, ACE Studio, Synthesizer V |
| Multiple vocal tools | Melodyne, Auto-Tune, VocALign |
| Multiple mastering tools | LANDR, Ozone, smart:EQ |
| Multiple orchestration suites | Kontakt, EastWest, Spitfire |
| Multiple stem separation tools | Lalal.ai, RipX, Demucs |
| Multiple harmonic plugins | Scaler, Captain Chords |
| Multiple workflow automation systems | Custom scripts, macros, third-party utilities |

ORPHEUS should function as:

| Role | Capability |
|:---|:---|
| Producer | Generates arrangements, chord progressions, and song structures |
| Engineer | Mixes, masters, repairs audio, and manages routing |
| Arranger | Builds transitions, fills, and structural blocks |
| Assistant | Executes natural language commands across all DAW functions |
| Orchestrator | Generates and arranges orchestral parts with correct articulations |
| Vocal Editor | Tunes, synthesizes, harmonizes, and repairs vocal performances |
| Workflow Operator | Automates repetitive tasks via scripts and macro chains |
| Intelligent DAW Controller | Learns user habits and adapts the interface over time |

**Inside ONE unified desktop production environment.**

---

## Deep Dive Documents

This repository contains detailed research, architecture, and specification documents. Use the links below to navigate directly to specific areas of the SONARA DAW platform.

### 🌟 The Master Blueprint
* [**SONARA_MASTER_SPEC.md**](./SONARA_MASTER_SPEC.md) — The definitive full hardware, DAW, AI, and engine implementation specification with all tables.
* [**ROADMAP.md**](./ROADMAP.md) — The 7-phase development roadmap with milestones.
* [**CONTRIBUTING.md**](./CONTRIBUTING.md) — Code standards, real-time safety rules, and PR process.

### 🏛️ Architecture & Engine
* [**architecture/engine_spec.md**](./architecture/engine_spec.md) — The C++/JUCE core, multi-threading model, and plugin sandboxing architecture.
* [**architecture/orpheus_ai_spec.md**](./architecture/orpheus_ai_spec.md) — The ORPHEUS sub-model routing, IPC bridge, and inference strategy.
* [**ai_models/model_registry.md**](./ai_models/model_registry.md) — Hardware requirements, VRAM budgets, and formats for all AI models.

### 🎛️ Features & Workflows
* [**features/piano_roll_spec.md**](./features/piano_roll_spec.md) — GPU rendering, MPE, ghost notes, and AI melody generation.
* [**features/mixer_spec.md**](./features/mixer_spec.md) — Routing matrix, busing, sidechain, and AI gain staging.
* [**features/vocal_engine_spec.md**](./features/vocal_engine_spec.md) — Pitch blobs, formant editing, phoneme timeline, and neural synthesis.
* [**features/arrangement_view_spec.md**](./features/arrangement_view_spec.md) — Comping, clip gain, take lanes, and AI structural generation.

### 📋 Domain Documentation
* [**docs/01_Core_Features.md**](./docs/01_Core_Features.md) — Core identity, platform requirements, and hardware support.
* [**docs/02_Audio_Engine.md**](./docs/02_Audio_Engine.md) — Engine architecture, real-time safety, and plugin formats.
* [**docs/03_DAW_Absorption.md**](./docs/03_DAW_Absorption.md) — Full DAW feature absorption matrix across all reference DAWs.
* [**docs/04_AI_Absorption.md**](./docs/04_AI_Absorption.md) — AI tool absorption matrix across all reference AI tools.
* [**docs/05_ORPHEUS_Features.md**](./docs/05_ORPHEUS_Features.md) — ORPHEUS capability categories and command examples.
* [**docs/06_Stock_Plugins.md**](./docs/06_Stock_Plugins.md) — Complete stock instrument and effects plugin suite.

### 🔌 Extensibility
* [**plugins/plugin_dev_guide.md**](./plugins/plugin_dev_guide.md) — JUCE templates and the ORPHEUS integration API (`IOrpheusControllable`).
* [**scripts/README.md**](./scripts/README.md) — Python and Lua scripting API for session automation and ORPHEUS commands.

---

**SONARA DAW + ORPHEUS AI — Built by SAMPLESOCIETY. Designed for the future of audio.**
