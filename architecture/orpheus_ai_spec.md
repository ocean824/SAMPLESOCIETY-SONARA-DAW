# ORPHEUS AI Architecture Specification

## 1. Overview

ORPHEUS is the artificial intelligence core of SONARA, acting as a multi-modal production assistant. It is not a single model, but a collection of specialized neural networks and language models orchestrated by a central routing layer.

## 2. Model Architecture

### 2.1 Natural Language Interface (NLI)
The entry point for all user commands. A fine-tuned large language model (LLM) interprets natural language instructions and routes them to the appropriate specialized model.

**Responsibilities:**
* Parse user intent from text or voice input.
* Decompose complex commands into atomic DAW operations.
* Maintain session context (e.g., "make it louder" refers to the currently selected track).

### 2.2 Specialized Sub-Models

| Sub-Model | Task | Inference Mode |
| :--- | :--- | :--- |
| **ORPHEUS-Vocal** | Pitch correction, vocal synthesis, formant editing | Local (ONNX Runtime) |
| **ORPHEUS-Mix** | EQ analysis, dynamic balancing, masking detection | Local (ONNX Runtime) |
| **ORPHEUS-Master** | Loudness targeting, limiting, tonal balance | Local (ONNX Runtime) |
| **ORPHEUS-Stem** | Source separation (vocals, drums, bass, other) | Cloud or Local (GPU required) |
| **ORPHEUS-Arrange** | Song structure generation, transition building | Cloud |
| **ORPHEUS-Harmony** | Chord generation, voice leading, harmony stacking | Local (ONNX Runtime) |
| **ORPHEUS-Performer** | MIDI humanization, groove extraction, articulation | Local (ONNX Runtime) |
| **ORPHEUS-Repair** | Noise reduction, de-clicking, spectral repair | Local (ONNX Runtime) |

### 2.3 Inference Strategy

ORPHEUS uses a hybrid inference strategy to balance latency and quality:

* **Local Inference:** Time-sensitive tasks (real-time pitch correction, EQ analysis) run on-device using ONNX Runtime. Requires a modern CPU; GPU acceleration via CUDA/Metal is supported.
* **Cloud Inference:** Computationally heavy tasks (stem separation, full arrangement generation) are offloaded to SAMPLESOCIETY's cloud API. Requires an internet connection and a valid SONARA subscription.

## 3. Memory & Learning System

ORPHEUS maintains a persistent user profile that learns:
* Preferred mixing styles and EQ curves.
* Frequently used plugin chains and macro assignments.
* Genre and workflow preferences.
* Custom command aliases and shortcuts.

This profile is stored locally and optionally synced to the cloud.

## 4. Integration with the Audio Engine

ORPHEUS communicates with the SONARA audio engine via a dedicated inter-process communication (IPC) bridge. This ensures that AI inference never blocks the real-time audio thread.

```
[User Input] --> [ORPHEUS NLI] --> [Sub-Model Router]
                                        |
                    +-------------------+-------------------+
                    |                                       |
              [Local Inference]                    [Cloud Inference]
                    |                                       |
              [ONNX Runtime]                     [SAMPLESOCIETY API]
                    |                                       |
                    +-------------------+-------------------+
                                        |
                              [DAW Engine IPC Bridge]
                                        |
                              [AudioProcessorGraph]
```
