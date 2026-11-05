# v1.0 release candidate notes

Status: prepared for review; no `v1.0` tag or GitHub Release is created by this document.
The author confirmed normal operation on 5 November 2026 and requested the documentation
update be pushed without additional runtime acceptance tests or a new interface screenshot.
See the [verification notes](verification.md) for the static checks and author confirmation.

## Between Chance and Structure

A generative ambient and lo-fi music system built with Max/MSP and VCV Rack.

- Five-state formal model: STILL, EMERGE, FLOW, BLOOM, DISSOLVE.
- Three scenes: Forest, Rain, Steampunk.
- Evolve and Timed modes, section memory, weighted harmony and voice leading.
- Conditional IDM percussion, user-audio import and stereo recording.
- Max and VCV patches, bilingual overview, 55-page report, architecture diagrams,
  setup instructions and sample provenance notes.

## Setup

Start with the [README](../README.md), [environment manifest](environment.md) and
[sample replacement guide](../patch/bpatch_and_samples/samples/README.md).
The saved session uses Max 9.1.4, VCV Rack 2.6.6 and BlackHole 16ch on macOS.

## Known limitations

- The sample folders ship empty; scene and IDM pools use fixed numbered buffer groups.
  Supply your own permitted audio. The original commercial libraries are not bundled.
- The saved plugin versions are documented; no new runtime test was performed for this documentation update.
- Windows and Linux audio routing have not been verified.
- Demonstration videos and audio are hosted externally on Google Drive.

Code and patches use PolyForm Noncommercial 1.0.0. Documentation and the report use
CC BY-NC 4.0. See [LICENSE](../LICENSE.md) and [NOTICE](../NOTICE.md) for the existing terms.

## Publishing a versioned release

The documentation update can be pushed with the author's confirmation above. A separate
versioned release can be created by tagging the chosen commit as `v1.0` and publishing these
notes with the repository source archive. No additional screenshot is required.
