# SONARA Plugin Development Guide

## 1. Overview
This guide covers the development of native SONARA stock plugins and the standards for hosting third-party plugins.

## 2. Supported Plugin Formats

| Format | Platform | Notes |
| :--- | :--- | :--- |
| **VST3** | Windows, macOS | Primary format. Steinberg VST3 SDK required. |
| **AU (Audio Units)** | macOS only | Apple Audio Unit v3 SDK required. |
| **CLAP** | Windows, macOS | Open-source format. Preferred for new development. |
| **ARA2** | Windows, macOS | Extension for VST3/AU for deep timeline integration. |

## 3. SONARA Native Plugin Architecture

All native SONARA plugins are built using the JUCE framework.

### 3.1 Instrument Plugin Template (JUCE)
```cpp
class SonaraSynthPlugin : public juce::AudioProcessor
{
public:
    SonaraSynthPlugin();
    ~SonaraSynthPlugin() override;

    void prepareToPlay(double sampleRate, int samplesPerBlock) override;
    void releaseResources() override;
    void processBlock(juce::AudioBuffer<float>&, juce::MidiBuffer&) override;

    juce::AudioProcessorEditor* createEditor() override;
    bool hasEditor() const override { return true; }

    const juce::String getName() const override { return "SONARA Synth One"; }
    // ... standard JUCE plugin boilerplate
};
```

### 3.2 Effect Plugin Template (JUCE)
```cpp
class SonaraEQPlugin : public juce::AudioProcessor
{
public:
    SonaraEQPlugin();
    ~SonaraEQPlugin() override;

    void prepareToPlay(double sampleRate, int samplesPerBlock) override;
    void processBlock(juce::AudioBuffer<float>&, juce::MidiBuffer&) override;

    // ORPHEUS AI integration hook
    void applyOrpheusEQSuggestion(const OrpheusEQAnalysis& analysis);

    // ... standard JUCE plugin boilerplate
};
```

## 4. ORPHEUS Plugin Integration API

Native SONARA plugins can expose an ORPHEUS integration interface to receive AI-driven parameter suggestions.

```cpp
class IOrpheusControllable
{
public:
    virtual ~IOrpheusControllable() = default;

    // Called by ORPHEUS to apply a parameter suggestion
    virtual void applyOrpheusSuggestion(const OrpheusSuggestion& suggestion) = 0;

    // Returns a description of all controllable parameters for ORPHEUS
    virtual std::vector<OrpheusParameterDescriptor> getOrpheusParameters() const = 0;
};
```

## 5. Plugin Sandboxing

Third-party plugins are hosted in a separate sandboxed process. Communication between the host and the plugin sandbox uses a shared memory IPC mechanism for low-latency audio data transfer and a message queue for control parameter changes.
