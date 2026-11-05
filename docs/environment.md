# Environment and dependencies

## Author-provided machine

The author supplied the following machine details on 5 November 2026:

| Item | Value |
|---|---|
| Computer | 16-inch MacBook Pro |
| Chip | Apple M5 Pro (Apple silicon / arm64) |
| Memory | 64 GB |
| Operating system | macOS Tahoe 26.6.2 |
| Max | 9.1.4, as saved in the Max patches |
| VCV Rack | 2.6.6, as saved in the Rack patch |
| Virtual audio device | BlackHole 16ch |
| Session audio | 48000 Hz, 256-sample Rack block size, stereo channels 1–2 |

Machine details are author-provided context. On 5 November 2026, the author confirmed
normal project operation; no new end-to-end playback test was performed for this documentation update. The Max files record `x64` in their saved application metadata; that does
not establish whether Max was launched natively or through Rosetta on this machine.
The BlackHole driver version was not recorded. Windows and Linux routing have not been
verified for this project.

## Plugin versions saved in the VCV patch

These versions were extracted from `vcv/Between_Chance_and_Structure.vcv`. They describe
the saved session, not minimum compatible versions or a fresh installation test.
There are 58 modules across 17 plugins, including two bundled plugins and 15 external ones.
Install the external plugins from the [VCV Library](https://library.vcvrack.com/).

| Plugin | Saved version | Source |
|---|---|---|
| `4ms-ROMplers` | 2.0.0 | VCV Library |
| `4msCompany` | 2.2.0 | VCV Library |
| `ALMFree` | 2.2.2 | VCV Library |
| `AlrightDevices` | 2.1.0 | VCV Library |
| `Befaco` | 2.11.0 | VCV Library |
| `Bogaudio` | 2.6.47 | VCV Library |
| `Core` | 2.6.6 | Bundled |
| `DrumKit` | 2.0.1 | VCV Library |
| `Fundamental` | 2.6.4 | Bundled |
| `HetrickCV` | 2.5.4 | VCV Library |
| `MindMeldModular` | 2.5.0 | VCV Library |
| `NYSTHI` | 2.4.23 | VCV Library |
| `Submit` | 2.16.0 | VCV Library |
| `SurgeXTRack` | 2.2.9.0 | VCV Library |
| `Valley` | 2.4.5 | VCV Library |
| `Venom` | 2.15.0 | VCV Library |
| `trowaSoft` | 2.0.9 | VCV Library |

The five `trowaSoft/cvOSCcv` modules receive Max control data on local UDP ports 1 and 2.
VCV sends stereo audio through BlackHole to Max input channels 1–2; Max sends the final mix
to the physical output device. Keep the physical output separate from the BlackHole return.

## Reproduction limits

- Commercial sample libraries are omitted. Follow the
  [sample replacement guide](../patch/bpatch_and_samples/samples/README.md) for fixed groups
  and loaded buffer order; substitute audio changes the resulting sound.
- This setup requires both applications, the listed plugins and virtual audio routing.
- Media links point to Google Drive. Signed-out viewing and playback can be checked on a fresh
  setup; static repository checks cannot establish that the media plays.
- See [verification notes](verification.md) for author confirmation and optional fresh-setup checks.
