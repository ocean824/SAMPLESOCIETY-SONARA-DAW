# ORPHEUS AI Model Registry

This document lists all AI models used by ORPHEUS, their tasks, inference modes, and technical requirements.

## Model Registry

| Model ID | Task | Format | Inference Mode | Min VRAM | Min RAM |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `orpheus-vocal-v1` | Pitch correction & vocal synthesis | ONNX | Local | 2 GB | 4 GB |
| `orpheus-mix-v1` | EQ analysis & dynamic balancing | ONNX | Local | 1 GB | 2 GB |
| `orpheus-master-v1` | Loudness targeting & mastering | ONNX | Local | 1 GB | 2 GB |
| `orpheus-stem-v1` | Stem separation (4-stem) | ONNX | Local (GPU) / Cloud | 4 GB | 8 GB |
| `orpheus-stem-v2` | Stem separation (6-stem, high quality) | Cloud | Cloud only | N/A | N/A |
| `orpheus-arrange-v1` | Song structure generation | Cloud | Cloud only | N/A | N/A |
| `orpheus-harmony-v1` | Chord generation & voice leading | ONNX | Local | 1 GB | 2 GB |
| `orpheus-performer-v1` | MIDI humanization & groove | ONNX | Local | 512 MB | 1 GB |
| `orpheus-repair-v1` | Noise reduction & spectral repair | ONNX | Local | 2 GB | 4 GB |
| `orpheus-nli-v1` | Natural language command parsing | ONNX (quantized) | Local | 2 GB | 8 GB |

## Inference Modes

### Local Inference
Models run on-device using ONNX Runtime. Supports:
* **CPU:** All models (performance varies).
* **NVIDIA GPU (CUDA):** Recommended for stem separation and vocal synthesis.
* **Apple Silicon (CoreML / Metal):** Optimized for M1/M2/M3 Macs.

### Cloud Inference
Heavy models are processed on SAMPLESOCIETY's cloud infrastructure. Requires:
* Active internet connection.
* Valid SONARA subscription.
* Results are returned asynchronously and integrated into the session.

## Model Updates
ORPHEUS models are updated automatically in the background when new versions are available. Users can manage model versions in **Preferences > ORPHEUS > Model Manager**.
