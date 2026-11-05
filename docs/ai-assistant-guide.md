# Setup guide for AI assistants

*Written for AI assistants helping a human install and run this project. If you are a person, [the setup guide](setup-guide.md) is the shorter route.*

You are reading this because someone asked you, an AI agent, to help run
**Between Chance and Structure** — a generative ambient music system built in Max/MSP with
pitched synthesis in VCV Rack.

This file tells you what is in the repository, what is missing, what to install, how to
configure audio, and how to verify the result. Follow it in order.

**Read this first, it changes the plan:** Max/MSP and VCV Rack are GUI applications. You
cannot launch them headlessly or hear the output. Your job is to prepare the environment,
run the static checks below, and then guide the human through a handful of GUI steps and
ask them to confirm what they see. Do not claim the audio works — only the human can hear it.

---

## 1. Facts, verified

| Item | Value |
|---|---|
| Repository | `https://github.com/Chora666/between-chance-and-structure` |
| Max version used | 9.1.4 |
| VCV Rack version used | 2.6.6 |
| Sample rate | 48000 Hz, block size 256 |
| Virtual audio device | BlackHole 16ch (developed on macOS) |
| VCV modules | 58 modules across 17 plugins — extract the exact list with the command in §4 |
| Sample requirement | 8 folders, read with `readfolder`; **filenames are never referenced** |
| Media | long videos and audio examples are on Google Drive, not in the repo |

Sizes: the repo is about 10 MB. The patches are `patch/*.maxpat` (4.7 MB) and
`vcv/*.vcv` (11 KB, a zstd-compressed tar containing `patch.json`).

## 2. Clone

```bash
git clone https://github.com/Chora666/between-chance-and-structure.git
cd between-chance-and-structure
```

Nothing needs building. Do not move or rename the numbered folders: the Max patch resolves
`bpatch_and_samples/` relative to its own location.

## 3. Check the sample folders

The patch calls `readfolder Patcher:/bpatch_and_samples/samples/<folder>`, so it loads
whatever audio files are present and never looks for a specific filename. The eight folders
must exist:

```
patch/bpatch_and_samples/samples/
    IDM_samples/        drums/kick/    drums/snare/   drums/hat/
    drums/ohat/         drums/cymbals/ sceneAmbient/  sceneEvents/
```

```bash
cd patch/bpatch_and_samples/samples
for d in IDM_samples drums/kick drums/snare drums/hat drums/ohat drums/cymbals sceneAmbient sceneEvents; do
  printf '%-14s %s\n' "$d" "$(ls "$d"/*.wav 2>/dev/null | wc -l | tr -d ' ')"
done
```

They ship **empty**. That is deliberate: the original audio comes from commercial sample
libraries that cannot be redistributed (`PROVENANCE.md` says which). Three options,
in order of preference:

1. **Run with the human's own audio.** Drop any `.wav` files into the eight folders — the
   system runs, and the sound is whatever they put in. This is the fastest path to a working
   demo and needs no licences.
2. **Reproduce the original sound** by acquiring the libraries listed in
   `PROVENANCE.md` (it gives library names and Sound IDs).
3. Do not download sample libraries from unofficial mirrors.

Original per-folder counts, for reference: `IDM_samples` 57, `drums/kick` 10, `drums/snare`
10, `drums/hat` 10, `drums/ohat` 6, `drums/cymbals` 6, `sceneAmbient` 15, `sceneEvents` 9.

## 4. Check the VCV Rack plugins

The `.vcv` file is a zstd-compressed tar. Extract the requirement list directly from it:

```bash
zstd -dc vcv/Between_Chance_and_Structure.vcv \
  | tar -xOf - patch.json \
  | jq -r '.modules[].plugin' | sort -u
```

Expected output (17 plugins):

```
4ms-ROMplers 4msCompany ALMFree AlrightDevices Befaco Bogaudio Core DrumKit Fundamental
HetrickCV MindMeldModular NYSTHI Submit SurgeXTRack Valley Venom trowaSoft
```

`Core` and `Fundamental` ship with Rack. The other 15 must be installed from the VCV
Library (`https://library.vcvrack.com`) before the patch will open — Rack refuses to load a
patch whose plugins are missing.

Check what is installed:

```bash
# macOS
ls ~/Library/Application\ Support/Rack2/plugins-*/
# Windows
dir "%LOCALAPPDATA%\Rack2\plugins-*"
```

`trowaSoft/cvOSCcv` is load-bearing: it carries the OSC control data from Max into Rack
(five instances). If it is missing, Max will run but nothing will sound.

Tools used above: `zstd`, `tar`, `jq`. Without `jq`, pipe to
`python3 -c "import sys,json;print(sorted({m['plugin'] for m in json.load(sys.stdin)['modules']}))"`.
Install `zstd` if needed (`brew install zstd` / `apt install zstd`).

## 5. Audio routing

This is the part that fails most often. The chain is:

```
VCV Rack  ──(BlackHole 16ch, ch 1–2)──▶  Max/MSP  ──▶  physical output
                                                (headphones / interface)
```

**VCV Rack**
1. Open `vcv/Between_Chance_and_Structure.vcv`.
2. `Audio Interface` module → driver **Core Audio**, device **BlackHole 16ch**,
   48000 Hz, block size 256.
3. Confirm the main mixer (`MixMasterJr`) left/right outputs feed BlackHole channels 1–2.

**Max**
1. Open `patch/Between_Chance_and_Structure.maxpat`.
2. `Options → Audio Status`: input **BlackHole 16ch**, output **the physical device**.
3. 48000 Hz, and enable audio.

Never route the Max output back into BlackHole — that produces silence or a feedback loop.
BlackHole is macOS-only; on Windows the equivalent is VB-CABLE or ASIO Link Pro, which is
untested with this project. Say so plainly instead of improvising.

## 6. Launch and verify

Order matters: **VCV first, then Max.**

1. VCV Rack open and playing (its level meters move when you touch nothing — check the Rack
   audio status shows the device running).
2. Open the Max patch; wait for the sample pools and drum-machine abstractions to load.
3. Presentation mode; set the master level low; enable Max audio.
4. Choose a scene (Forest / Rain / Steampunk) and a mode (Evolve / Timed).
5. Press **START**.

What the human should see, and what to ask them:

| Ask | Expected |
|---|---|
| "Did Max open any dialog about missing files?" | No |
| "Does the interface show a BPM, bar, step and formal stage?" | Yes, and the stage advances over time |
| "Do the level meters move?" | Yes, on the Max output |
| "Do you hear sound from headphones/speakers?" | Yes |

The five formal states run `STILL → EMERGE → FLOW → BLOOM → DISSOLVE` and then cycle. In
Evolve mode it runs until stopped; in Timed mode you enter a duration (60–600 s) and it stops
itself.

## 7. When it does not work

| Symptom | Cause | Fix |
|---|---|---|
| Patch will not open; Rack complains about plugins | A required plugin is not installed | Install the missing ones from the VCV Library, restart Rack |
| Max opens with missing-file warnings | A sample folder is missing or in the wrong place | Keep the exact folder names; files may be empty but folders must exist |
| Everything runs, but silence | Output routed into BlackHole, or wrong input device in Max | Max input = BlackHole, output = physical device |
| Drums / ambience never trigger | Drum and scene folders are empty | Put some `.wav` files in them |
| Pitch or timing drifts | Sample rates differ between Rack and Max | Both 48000 Hz |
| No OSC response in Rack | `cvOSCcv` not running, or ports blocked | Leave the five `cvOSCcv` modules active; Max sends on UDP |

## 8. Further reading

- [`setup-guide.md`](setup-guide.md) — the operating guide: startup order, interface, importing
  user audio, recording a performance.
- [`../REPORT.pdf`](../REPORT.pdf) — architecture and rationale
  (sections 4.3–4.5 cover the state machine and the synthesis modules).
- [`architecture/`](architecture/) — architecture diagrams; [`credits-and-materials.pdf`](credits-and-materials.pdf)
  for every third-party library.
- Demonstration media (Google Drive): formal demo `RunTime.mov`, technical walkthrough
  `Technical_Walkthrough.mov`, and a 25-minute continuous run — see the media table in the [main README](../README.md).
- [`../README.zh-CN.md`](../README.zh-CN.md) — the same description in Simplified Chinese.

## 9. Your boundaries

- Do not publish, re-upload or bundle third-party sample material; see
  `PROVENANCE.md`.
- Do not edit the report PDF or the licence notices. The code is licensed for
  noncommercial use only; do not suggest commercial deployment without telling the user that a
  separate licence is required.
- Do not claim the system *sounds* right. Static checks and the human's report are all you
  have.
- If a step needs a GUI choice you cannot make, stop and ask — do not guess device names or
  invent menu paths.
