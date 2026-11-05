# Setup and operating guide

How to open, route, operate and record the system. Software requirements are listed in the
[main README](../README.md); this page is the operating manual.

## 1. Project files

Open the project from the folder as cloned, without changing its internal structure.

| File | Purpose |
|---|---|
| `patch/Between_Chance_and_Structure.maxpat` | Main Max patch |
| `vcv/Between_Chance_and_Structure.vcv` | VCV Rack synthesis patch |
| `patch/bpatch_and_samples/` | Max abstractions and the sample folders |

> The main Max patch refers to files inside `patch/bpatch_and_samples`. Renaming or moving that
> folder may prevent the drum machines, polyphonic sample players or sample libraries from
> loading. The patch and that folder must stay side by side.

## 2. Software and audio requirements

The project documents the following software setup (see the
[environment manifest](environment.md) for author-provided hardware and saved plugin versions):

- Max 9.1.4
- VCV Rack 2.6.6
- BlackHole 16ch
- A physical audio output such as headphones, speakers or an audio interface

The VCV Rack patch uses the following Rack plugins:

```
4ms-ROMplers, 4msCompany, ALMFree, AlrightDevices, Befaco, Bogaudio,
DrumKit, HetrickCV, MindMeldModular, NYSTHI, Submit, SurgeXTRack,
Valley, Venom and trowaSoft
```

Install any missing modules from the VCV Library before opening the Rack patch. The
trowaSoft `cvOSCcv` module is required for communication from Max to VCV Rack.

Before playback, supply replacement WAV files following the
[sample replacement guide](../patch/bpatch_and_samples/samples/README.md). All eight sample
folders ship empty. Scene beds use fixed groups across buffers 1–15; IDM roles use 1–57.
Check counts and loaded order in Max before expecting the complete arrangement.

## 3. First-time audio setup

BlackHole carries the stereo output of VCV Rack back into Max. It should be used as the VCV
output and the Max input, not as the final listening output.

**VCV Rack**

1. Open `vcv/Between_Chance_and_Structure.vcv`.
2. In the Audio Interface module, select Core Audio and BlackHole 16ch.
3. Set the sample rate to 48000 Hz and the block size to 256 samples.
4. Confirm that the main mixer left and right outputs feed BlackHole channels 1 and 2.
5. Leave the five `cvOSCcv` modules active. They receive local OSC data from Max on UDP
   ports 1 and 2.

**Max**

1. Open `patch/Between_Chance_and_Structure.maxpat`.
2. Open Options → Audio Status.
3. Select BlackHole 16ch as the input device.
4. Select headphones, speakers or a physical audio interface as the output device.
5. Use a sample rate of 48000 Hz.
6. Enable audio processing in Max.

The Max patch receives the VCV Rack stereo return through input channels 1 and 2. Do not route
the Max output back into BlackHole unless a separate monitoring setup has been prepared, as
this might create silence or an audio feedback loop.

## 4. Normal startup order

1. Open the VCV Rack patch first.
2. Check that its Audio Interface is still assigned to BlackHole 16ch.
3. Open the main Max patch from inside the complete project folder.
4. Wait briefly for the sample pools and drum-machine abstractions to load.
5. Open Presentation Mode if it is not already visible.
6. Set the master level conservatively and confirm that Max audio is enabled.
7. Choose a scene and an operating mode.
8. Optionally load user audio and prepare recording. Audio should be in the 1–10 minute scope.
9. Press **START**.

## 5. Main interface

**Scene**

- **FOREST** uses forest beds and foreground environmental events.
- **RAIN** uses rain beds and its own tempo choices.
- **STEAMPUNK** uses mechanical material and permits faster tempo choices.

**Mode**

- **EVOLVE** runs continuously and must be stopped manually.
- **TIMED** generates a complete form for the selected duration and stops at the calculated
  endpoint.

**Other controls and displays**

- The duration field is entered in seconds for TIMED mode.
- **Drop Audio Here** imports a stereo audio file.
- **RECORD** prepares a destination for the final stereo recording.
- **CANCEL RECORD** aborts the current timed run.
- **CLEAR FILE** removes the imported user-audio selection.
- **START/STOP** controls the global transport.
- The interface displays BPM, bar, step, formal stage, harmony, Melody output, active
  instrumental layers and overall progress.

## 6. Operating modes

### Evolve mode

EVOLVE is intended for an open-ended performance. The system moves through its formal stages,
changes orchestration and continues into later cycles. Tempo and section material can be
regenerated as the form develops. Press STOP when the performance should end.

### Timed mode

TIMED creates a fixed-duration performance.

1. Select TIMED.
2. Enter the required duration in seconds, or import an audio file and use its detected
   duration.
3. Press START.

The system selects a tempo, estimates the available number of sections and places the formal
stages inside that duration. It stops automatically at the endpoint.

## 7. Importing user audio

An imported stereo file can replace the internal environmental bed while the generated musical
layers continue around it.

1. Drag an uncompressed WAV or AIFF file onto **Drop Audio Here**.
2. Wait for the status to show `UserAudioReady`.
3. The detected file duration is copied to the duration control.
4. Select TIMED if the generated form should follow that duration.
5. Press START. The file follows the global transport.

Press CLEAR FILE to remove the imported file and return to the internal ambient material on the
next run.

## 8. Recording a performance

The recorder captures the complete post-master stereo output. This includes the Max drum, IDM
and soundscape layers, the VCV Rack return and any imported user audio.

1. Configure the scene, mode, duration and optional user audio.
2. Press RECORD before pressing START.
3. Choose a WAV filename and destination in the save dialogue.
4. Press START. Recording begins with the global transport.
5. In TIMED mode, allow the form to reach its endpoint. Recording then stops with the
   transport.
6. In EVOLVE mode, press STOP to finish both playback and recording.

RECORD opens and prepares the output file; it does not start the composition by itself. Use
CANCEL RECORD to abort a timed run. CLEAR FILE applies to imported audio and does not delete a
completed recording.

## 9. Verify a fresh setup

Use the [verification checklist](verification.md) to record scene, mode, import and recording
checks on a new installation. The author has confirmed normal project operation; this
documentation update did not include a new runtime test.
