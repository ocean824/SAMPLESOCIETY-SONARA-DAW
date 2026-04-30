# SONARA Piano Roll Specification

## 1. Overview
The SONARA Piano Roll is a GPU-accelerated MIDI editing environment designed for speed, precision, and deep AI integration.

## 2. Core Features

| Feature | Description |
| :--- | :--- |
| **GPU Rendering** | The piano roll canvas is rendered entirely on the GPU for smooth zooming, scrolling, and editing at any scale. |
| **Multi-Track Editing** | View and edit MIDI from multiple tracks simultaneously with ghost note rendering. |
| **Note Coloring** | Notes can be colored by pitch class, velocity, track, or ORPHEUS-assigned emotional value. |
| **Slide Notes** | Universal pitch slide system for creating smooth portamento transitions between notes. |
| **Per-Note Expression** | Full MPE support with per-note pitch bend, pressure, and slide lanes. |
| **Chord Stamps** | One-click chord insertion with support for triads, 7ths, 9ths, 11ths, and custom voicings. |
| **Strum Tool** | Applies humanized timing offsets to chords to simulate strummed string instruments. |
| **Randomizer** | Applies controlled random variation to velocity, timing, and pitch for humanization. |
| **Quick Draw Mode** | Click-and-drag to rapidly paint notes without switching tools. |
| **Scale Highlighting** | Highlights notes in the current key/scale for guided composition. |

## 3. ORPHEUS AI Enhancements

| ORPHEUS Feature | Description |
| :--- | :--- |
| **AI Melody Generation** | Generate a melody based on the current chord track and genre context. |
| **Harmonic Collision Analysis** | Identify and suggest resolutions for notes that clash with the underlying harmony. |
| **Emotional Color Mapping** | ORPHEUS assigns emotional values (tense, resolved, bright, dark) to note regions. |
| **AI Arrangement Building** | Suggest or auto-generate arrangement patterns based on the current MIDI content. |
| **Genre-Aware Glide Shaping** | Automatically shapes slide note curves based on the detected genre. |
