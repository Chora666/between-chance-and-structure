# Expected sample files

The sample libraries are **not** distributed in this repository: the material comes from
commercial sample packs and field recordings, which cannot be redistributed.

See [PROVENANCE.md](PROVENANCE.md) for where each file came from (source library and
Sound ID) and why the folder cannot be redistributed.

## Supplying replacement audio

The eight folders ship empty. Supply WAV files you recorded or have permission to use,
then reopen the main patch to reload the pools. An empty folder provides no sample audio;
the VCV synthesis is a separate layer and still requires its plugins and audio routing.
The public checkout does not reproduce the full demonstration sound without replacement samples.

`readfolder` assigns numbered buffers. Playback selects those numbers, rather than requesting
individual filenames. **Counts and buffer order matter**, especially in the two fixed pools:

| Folder | Original count | Selection rule / replacement requirement |
|---|---:|---|
| `IDM_samples/` | 57 | Fixed role pools address buffers 1–57; supply 57 files in the role groups below |
| `drums/kick/` | 10 | Selection range follows the loaded count; supply at least one kick |
| `drums/snare/` | 10 | Selection range follows the loaded count; supply at least one snare/clap |
| `drums/hat/` | 10 | Selection range follows the loaded count; supply at least one closed hi-hat |
| `drums/ohat/` | 6 | Selection range follows the loaded count; supply at least one open hi-hat |
| `drums/cymbals/` | 6 | Selection range follows the loaded count; supply at least one cymbal |
| `sceneAmbient/` | 15 | Fixed scene pools address buffers 1–15; supply five beds per scene |
| `sceneEvents/` | 9 | Selection range follows the loaded count; supply at least one foreground event for Forest |

### Fixed buffer groups

| Pool | Buffer indices | Material |
|---|---|---|
| `sceneAmbientBedPool` | 1–5 | Forest beds |
| `sceneAmbientBedPool` | 6–10 | Rain beds |
| `sceneAmbientBedPool` | 11–15 | Steampunk / mechanical beds |
| `idmPercPool` | 1–10 | Foley / clicks |
| `idmPercPool` | 11–20 | Glitches |
| `idmPercPool` | 21–37 | Impacts / metallic sounds |
| `idmPercPool` | 38–47 | Noise bursts |
| `idmPercPool` | 48–57 | Reverse swells |

Use zero-padded names such as `01_forest.wav` through `15_mechanical.wav`, and
`01_foley.wav` through `57_reverse.wav`, to make the intended order easy to inspect.
After loading, open the corresponding `polybuffer~` object in Max and verify its buffer list
against the table; filenames alone do not prove the loaded order. Avoid extra files in the
fixed pools. Fewer files can leave referenced buffers absent; extra files beyond the listed
indices are not selected by the fixed role/scene tables.

Use short one-shots for drums and IDM, longer recordings for looping beds, and short
foreground recordings for events. Use 48 kHz audio to match the documented session setup.
For a first playback check, you can import a stereo WAV through **Drop Audio Here**;
this supplies user audio but does not populate the drum or IDM pools.

The following inventory records the **original 123 files**. It is a reference for their roles
and provenance, not a bundle of downloadable samples.

## `IDM_samples/`

```
Foley_1.wav
Foley_2.wav
Foley_3.wav
Foley_4.wav
Foley_Click_1.wav
Foley_Click_2.wav
Foley_Click_3.wav
Foley_Click_4.wav
Foley_Click_5.wav
Foley_Click_6.wav
Glitch_Data_1.wav
Glitch_Data_2.wav
Glitch_Data_3.wav
Glitch_Data_4.wav
Glitch_digit_1.wav
Glitch_digit_2.wav
Glitch_digit_3.wav
Glitch_digit_4.wav
Glitch_tech_1.wav
Glitch_tech_2.wav
Impact_1.wav
Impact_2.wav
Impact_Texture_1.wav
Impact_Texture_2.wav
Impact_Texture_3.wav
Impact_Texture_4.wav
Impact_Texture_5.wav
Impact_Texture_6.wav
Impact_Texture_7.wav
Metallic_Hit_1.wav
Metallic_Hit_2.wav
Metallic_Hit_3.wav
Metallic_Hit_4.wav
Metallic_Hit_5.wav
Metallic_Hit_6.wav
Metallic_Hit_7.wav
Metallic_Hit_8.wav
Noise_Burst_1.wav
Noise_Burst_10.wav
Noise_Burst_2.wav
Noise_Burst_3.wav
Noise_Burst_4.wav
Noise_Burst_5.wav
Noise_Burst_6.wav
Noise_Burst_7.wav
Noise_Burst_8.wav
Noise_Burst_9.wav
Reverse_Swell_1.wav
Reverse_Swell_10.wav
Reverse_Swell_2.wav
Reverse_Swell_3.wav
Reverse_Swell_4.wav
Reverse_Swell_5.wav
Reverse_Swell_6.wav
Reverse_Swell_7.wav
Reverse_Swell_8.wav
Reverse_Swell_9.wav
```

## `drums/cymbals/`

```
Cymatics - Cymbal (Brute).wav
Cymatics - Cymbal (Coins).wav
Cymatics - Cymbal (Royal).wav
Cymatics - Cymbal (Sizzle).wav
Cymatics - Cymbal (Spike).wav
Cymatics - Cymbal (Stamp).wav
```

## `drums/hat/`

```
Cymatics - Hihat (Akai).wav
Cymatics - Hihat (Backend).wav
Cymatics - Hihat (Crisp).wav
Cymatics - Hihat (Gold).wav
Cymatics - Hihat (Lamar).wav
Cymatics - Hihat (Lazy).wav
Cymatics - Hihat (Slow).wav
PMWT2_Hi-Hat_Garage.wav
PMWT2_Hi-Hat_Metalic.wav
PMWT2_Hi-Hat_Trvp.wav
```

## `drums/kick/`

```
Cymatics - Kick (April).wav
Cymatics - Kick (Brush).wav
Cymatics - Kick (Diamond).wav
Cymatics - Kick (Green).wav
Cymatics - Kick (Imp).wav
Cymatics - Kick (Oldie).wav
Cymatics - Kick (Platinum).wav
Cymatics - Kick (Thief).wav
DUKB_Kick_Delay_FA.wav
IQ_MTD_Kick_03.wav
```

## `drums/ohat/`

```
Cymatics - Open Hat (Bingo).wav
Cymatics - Open Hat (Defender).wav
Cymatics - Open Hat (Lambo).wav
Cymatics - Open Hat (Lever).wav
Cymatics - Open Hat (Machina).wav
Cymatics - Open Hat (Tower).wav
```

## `drums/snare/`

```
Cymatics - Snare (Real).wav
Cymatics - Wet Percussion (Carpet).wav
DUKB_Snare_Iron_FA.wav
ESE - AURORA - Snare - Bjork (Delay).wav
ESE - AURORA - Snare - Clack.wav
ESE - AURORA - Snare - Plock.wav
IQ_MTD_Snare_10.wav
PMWT2_Clap_Mixed.wav
PMWT2_Snare_Kream.wav
PMWT2_Snare_Trvp_Gang.wav
```

## `sceneAmbient/`

```
Ambient_A_01.wav
Ambient_A_02.wav
Ambient_A_03.wav
Ambient_A_04.wav
Ambient_A_05.wav
Ambient_B_01.wav
Ambient_B_02.wav
Ambient_B_03.wav
Ambient_B_04.wav
Ambient_B_05.wav
Ambient_C_01.wav
Ambient_C_02.wav
Ambient_C_03.wav
Ambient_C_04.wav
Ambient_C_05.wav
```

## `sceneEvents/`

```
A_Events_01_birds.wav
A_Events_02_birds.wav
A_Events_03_birds.wav
A_Events_04_birds.wav
A_Events_05_birds.wav
A_Events_06_monkeys.wav
A_Events_07_monkeys.wav
A_Events_08_monkeys.wav
A_Events_09_monkeys.wav
```
