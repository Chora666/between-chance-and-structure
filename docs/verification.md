# Verification notes

## Static review: 5 November 2026

The documentation update was checked against the saved project files:

- All six `.maxpat` files parse as JSON.
- The VCV archive opens and contains 58 modules across 17 plugins.
- Saved plugin versions match the [environment manifest](environment.md).
- Scene-bed indices are 1–5, 6–10 and 11–15; IDM role indices cover 1–57.
- All eight sample directories exist and contain no distributed sample audio.
- Local Markdown links and images resolve.
- The report contains 55 PDF pages.

## Author confirmation: 5 November 2026

The author confirmed that the project operates normally and requested publication of the
documentation update without additional listening/recording acceptance tests or a new
interface screenshot. This is an author confirmation, not a new runtime test by the
assistant. No additional runtime tests were performed for this documentation update.

## Optional checks for a fresh setup

These checks are a reference for future installations, not prerequisites for pushing this
documentation update. Record date, operator, machine, application/plugin versions, supplied sample counts and any
Max Console or Rack errors with the results. Use a fresh clone outside any existing Max
search path so local files cannot conceal missing dependencies.

| Check | Procedure and expected result |
|---|---|
| Fresh setup | Install documented dependencies; open Rack then Max; no missing-module or abstraction errors |
| Empty sample folders | Before adding audio, inspect the Console and test start/stop; record missing-buffer messages and which synthesis layers remain audible |
| Replacement pools | Supply the documented counts and roles; inspect `polybuffer~` lists for correct indices and scene/IDM groups |
| Forest / Evolve | Run through all five states; check beds, foreground events, pitched voices and percussion; STOP ends transport |
| Rain / Evolve | Run through all five states; check Rain beds and orchestration; STOP ends transport |
| Steampunk / Evolve | Run through all five states; check mechanical beds and percussion; STOP ends transport |
| Timed mode | Test each scene at 60 s and 600 s; record actual duration, state progression and automatic stop behavior |
| User audio | Import a stereo WAV within 60–600 s; confirm `UserAudioReady`, detected duration and playback; CLEAR FILE restores internal beds on next run |
| Recording | Prepare RECORD before START; test Timed and Evolve; reopen resulting WAV to confirm stereo content, duration and clean ending |
| Cancel / restart | Abort a timed recording with CANCEL RECORD, then start another run; record transport and recording behavior |
| Extended run | Run Evolve for at least 25 minutes; record dropouts, stuck notes, CPU issues and any manual level changes |
| Public media | Open all six README media links signed out; confirm video/audio playback and correct content |

For any future failure, record the scene, mode, duration, reproduction steps, Console messages
and expected versus observed behavior.
