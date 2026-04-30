# Contributing to SONARA DAW + ORPHEUS AI

Thank you for your interest in contributing to SONARA. This document outlines the standards and processes for contributing to this project.

## Code of Conduct
All contributors are expected to maintain a professional and respectful environment. Discriminatory, harassing, or otherwise harmful behavior will not be tolerated.

## Development Environment Setup

### Prerequisites
* **C++ Compiler:** MSVC 2022+ (Windows) or Clang 14+ (macOS)
* **JUCE Framework:** Version 8.x or later
* **CMake:** Version 3.25 or later
* **Python:** 3.11+ (for scripting API and AI model tooling)
* **ONNX Runtime:** Latest stable release

### Build Instructions
```bash
# Clone the repository
git clone https://github.com/SAMPLESOCIETY/SAMPLESOCIETY-SONARA-DAW.git
cd SAMPLESOCIETY-SONARA-DAW

# Configure with CMake
cmake -B build -DCMAKE_BUILD_TYPE=Release

# Build
cmake --build build --config Release
```

## Contribution Guidelines

### Branching Strategy
* `main` — Stable, production-ready code.
* `develop` — Active development branch. All feature branches merge here.
* `feature/<name>` — Individual feature branches.
* `fix/<name>` — Bug fix branches.

### Pull Request Process
1. Fork the repository and create your feature branch from `develop`.
2. Ensure your code follows the existing code style (JUCE/Google C++ style guide).
3. Write unit tests for any new functionality.
4. Ensure the audio thread remains real-time safe (no allocations, no blocking I/O).
5. Submit a Pull Request with a clear description of the changes.

### Real-Time Safety
This is the most critical rule for audio engine contributions. Any code that runs on the audio thread MUST be:
* **Allocation-free:** No `new`, `malloc`, `std::vector::push_back` (if it may reallocate), etc.
* **Lock-free:** No mutexes, condition variables, or semaphores.
* **I/O-free:** No file reads/writes, no network calls.

Violations of real-time safety will result in immediate rejection of the Pull Request.
