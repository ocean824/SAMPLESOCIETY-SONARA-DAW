# SONARA Scripting API

## Overview
SONARA includes an internal scripting API that allows users and developers to automate workflows, create custom macros, and extend the DAW's functionality.

## Supported Languages
* **Python 3.x** — Primary scripting language for automation and AI model integration.
* **Lua** — Lightweight scripting for real-time performance macros.

## Example: Auto-Organize Session (Python)

```python
import sonara

session = sonara.get_current_session()

# Group all tracks by instrument type
for track in session.tracks:
    if track.type == "audio":
        if "vox" in track.name.lower() or "vocal" in track.name.lower():
            track.color = sonara.Color.BLUE
            track.send_to_bus("Vocals Bus")
        elif "drum" in track.name.lower() or "kick" in track.name.lower():
            track.color = sonara.Color.RED
            track.send_to_bus("Drums Bus")
        elif "bass" in track.name.lower():
            track.color = sonara.Color.GREEN
            track.send_to_bus("Bass Bus")

session.save()
print("Session organized successfully.")
```

## Example: ORPHEUS Command via Script (Python)

```python
import sonara
from sonara.orpheus import OrpheusClient

orpheus = OrpheusClient()
selected_track = sonara.get_selected_track()

# Apply natural language command to selected track
result = orpheus.execute(
    command="Tune these vocals naturally.",
    target=selected_track
)

print(f"ORPHEUS result: {result.status} — {result.message}")
```

## ORPHEUS Script Generation
ORPHEUS can generate custom scripts based on natural language descriptions. Use the command:
> *"Write a script that exports all tracks as individual stems."*

ORPHEUS will generate, validate, and optionally execute the script.
