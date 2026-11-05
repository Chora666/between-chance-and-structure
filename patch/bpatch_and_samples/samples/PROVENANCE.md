# Sample provenance

Where the audio in this project came from, and why the files are not distributed here.

这份表说明每个样本的来源。结论：**除 1 个自录文件外，其余全部来自第三方素材库，不得再分发。**

The authoritative record is [`../../../docs/credits-and-materials.pdf`](../../../docs/credits-and-materials.pdf)
(including per-source Sound IDs). This page only reorganises that record by file, so you can
tell which files you would need to supply yourself.

**Licensing, in one line:** every library below grants use *inside a production* — including
commercial release — but not redistribution of the raw files. Publishing this folder, or a zip
of it, would replace the libraries' own distribution and is not covered by those licences.

---

## 1. `drums/` — 42 one-shots

Prefixes in the filenames identify the source library. Counts are from this repository's
file list; library names are from the credits document.

| Filename prefix | Files | Source library | Copyright holder |
|---|---|---|---|
| `Cymatics - …` | 29 | Cymatics — *King of Beats 2025 Hip-Hop Edition Contest Kit*, *TRAP GODS 2*, *SOLACE Lo-fi Bundle* | Cymatics |
| `PMWT2_…` | 6 | Production Master — *Wild Trap II* (licensed through Black Octopus Sound) | Production Master / Black Octopus |
| `ESE - AURORA - …` | 3 | Epic Sound Effects — *AURORA Cinematic Texture Toolkit* | Epic Sound Effects |
| `IQ_MTD_…` | 2 | IQ Samples — *Melodic Trap DNA* | IQ Samples |
| `DUKB_…` | 2 | Famous Audio — *Dark UK Bass* | Famous Audio |

The credits document's processing note: the drum library holds 42 one-shots — ten kicks, ten
snare/clap sounds, ten closed hi-hats, six open hi-hats and six cymbals.

## 2. `IDM_samples/` — 57 derived sounds

Filenames are descriptive rather than source-specific (`Foley_1.wav`, `Glitch_Data_3.wav`,
`Impact_Texture_5.wav`, `Metallic_Hit_7.wav`, `Noise_Burst_10.wav`, `Reverse_Swell_9.wav`, …),
so **per-file provenance is not recoverable from this repository**.

The credits document records them at the library level: 57 IDM rack sounds created by editing,
reversing, resampling, layering and processing material from these libraries —

1. Soundly — 23 source assets (Foley, footsteps, cloth, UI, electromagnetic noise, metallic and
   cinematic impacts, designed effects); the individual `SND` IDs are retained in the Ableton
   Live project metadata, not in this repository
2. Cymatics
3. 91Vocals — *Lofi Beats and Chill*
4. 91Vocals — *Pink Ash: Lofi House*
5. EDM Templates — *Code Black Midtempo*
6. Samplestar — *Tokyo City Pop Tapes Vol. 2*
7. Oversampled — *Hyperwaves*
8. Prime Loops — *The Lo-Fi Bundle / Lo-Fi Jazz Hop XXL*
9. Prime Loops — *NIGHTISM*
10. Prime Loops — *TAKESHIDO Manga Melodies*
11. Soul Rush Records — *Dark Minimal Liquid DnB*
12. BFB Impacts collection
13. One faucet / water-flow / underwater impact — publisher not recorded
14. One cocktail-shaker / spoon-scrape source — publisher not recorded

## 3. `sceneAmbient/` — 15 long-form beds

These are the Forest / Rain / Steampunk beds. The credits document lists five sources per scene
in the same order as the filenames, so the mapping below is **positional and presumed** — it is
not stated file-by-file in the credits document. Verify against your own download records before
relying on it.

| Files | Presumed source | Confidence |
|---|---|---|
| `Ambient_A_01` | Ear0 (耳聆网) — *Forest Night Ambience*, Sound ID 19048 | positional |
| `Ambient_A_02` | Ear0 — *Wind Blowing Through a Forest*, Sound ID 13135 | positional |
| `Ambient_A_03` | Ear0 — *Forest Environmental Ambience*, Sound ID 15210 | positional |
| `Ambient_A_04` | **Self-recorded field recording** (DJI Pocket 4) | positional |
| `Ambient_A_05` | Soundly — *Rural Orange Plantation Ambience: Birds, Insects, Filtered, Hot Sunny Day, Cotui, Dominican Republic*, SND128693 | positional |
| `Ambient_B_01` | Ear0 — *Rainy Day*, Sound ID 40941 | positional |
| `Ambient_B_02` | Ear0 — *Light Rain*, Sound ID 43524 | positional |
| `Ambient_B_03` | Ear0 — *30-Second Light Rain Sample + Light Rain Droplets*, Sound IDs 19314 and 36692 | positional |
| `Ambient_B_04` | Soundly — *Light Rain on Concrete with Light Wind*, SND47478 | positional |
| `Ambient_B_05` | Soundly — *Light-to-Moderate Rain on Vegetation, Drizzle and Dripping Leaves 02*, SND137616 | positional |
| `Ambient_C_01` | Ear0 — *Rhythmic Industrial Noise*, Sound ID 14901 | positional |
| `Ambient_C_02` | Ear0 — *Industrial Robot-Arm Operation*, Sound ID 17713 | positional |
| `Ambient_C_03` | Ear0 — *Industrial Machinery Noise*, Sound ID 15084 | positional |
| `Ambient_C_04` | Soundly — *Industrial Roadheader: Turn On/Off, Guido Coal Mine 02, Perspective 1*, SND164136 | positional |
| `Ambient_C_05` | Soundly — *Industrial Roadheader: Turn On, Guido Coal Mine, Poland 01*, SND164137 | positional |

`Ambient_A_04` is the only file in the whole sample folder that is confirmed to be the author's
own recording.

## 4. `sceneEvents/` — 9 short events

Files are named by content (`A_Events_01_birds.wav` … `A_Events_09_monkeys.wav`). The credits
document lists six short event sources (Ear0 Sound IDs 20383, 42284, 43052, 20413, 14243 and
Soundly SND164135) without tying them to individual filenames.

**Per-file mapping: not documented.** Four bird files and five monkey files suggest the two
bird/monkey sources were split up, but that is an observation, not a record.

---

## Replacing the samples

`README.md` in this folder lists the original filenames. You do not have to match them: the
Max patch reads these folders with `readfolder`, so any WAV files placed in the same folder
structure will be loaded. The original filenames are listed for reference and for acquiring
the same libraries again.

If you need this project's exact sound, acquire the libraries above — the credits document
contains the Sound IDs needed to find each sound again.
