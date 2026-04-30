# SONARA Audio Engine Architecture Specification

## 1. Overview
The SONARA Audio Engine is a high-performance, low-latency framework designed in C++ using the JUCE framework. It is the backbone of the DAW, handling everything from real-time audio I/O to complex plugin hosting and AI model inference.

## 2. Core Components

### 2.1 AudioDeviceManager
Handles the interface with the operating system's audio drivers (CoreAudio, ASIO, WASAPI). 
* Supports hot-swapping.
* Manages sample rate and buffer size negotiations.

### 2.2 AudioProcessorGraph
The central routing matrix of SONARA.
* Represents tracks, buses, and the master output as nodes.
* Calculates the optimal execution order based on routing dependencies.
* Supports multi-threaded rendering by processing independent branches of the graph concurrently.

### 2.3 Plugin Hosting Sandbox
Third-party plugins (VST3, AU, CLAP) are hosted in separate processes using Inter-Process Communication (IPC).
* **Crash Protection:** If a plugin faults, the sandbox process dies, but the main DAW process continues uninterrupted.
* **Format Support:** Deep integration with the CLAP format for superior multi-threading and non-destructive modulation.

### 2.4 ORPHEUS AI Integration Layer
The bridge between the C++ audio thread and the neural network inference engines.
* **Local Inference:** Utilizes ONNX Runtime or TensorRT for low-latency tasks (e.g., smart EQ, real-time voice morphing).
* **Cloud Offloading:** Handles asynchronous requests for heavy computational tasks (e.g., full track stem separation, high-fidelity vocal synthesis) via secure API calls.

## 3. Real-Time Safety Constraints
To prevent audio dropouts (glitches/pops), the audio thread MUST adhere to strict real-time constraints:
* No memory allocation (`new`/`malloc`) or deallocation on the audio thread.
* No blocking I/O operations (file reading/writing, network requests).
* No priority inversion (avoiding mutexes that might block the audio thread waiting for the UI thread).
* Use of lock-free data structures (e.g., ring buffers) for communicating between the audio and UI threads.
