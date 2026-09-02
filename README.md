# Academic Figure Workflow

A Codex skill for publication-ready scientific figures. It separates exact,
reproducible geometry from optional generated illustration:

- SVG or project plotting code owns axes, ticks, labels, legends, alignment,
  curves, tables, and every quantitative mark.
- ImageGen is limited to non-quantitative illustrative assets such as people,
  devices, task icons, and video thumbnails. The selected visual style follows
  the scientific topic (minimal vector, flat infographic, technology/system,
  scientific realistic, hand-drawn/editorial, or technical 3D).
- Experimental figures use a data contract, question-to-chart routing,
  uncertainty/baseline checks, semantic palettes, and target-size QA before
  export to SVG/PNG/PDF.

## Install

Copy this directory into the Codex skills directory:

```text
~/.codex/skills/academic-figure-workflow/
```

It is already installed locally at `/root/.codex/skills/academic-figure-workflow`.
The skill is discoverable automatically and can also be invoked explicitly as
`$academic-figure-workflow`.

## Contents

- `SKILL.md` — routing, SVG/ImageGen boundary, revision protocol, and QA gates.
- `references/experimental-figure-catalog.md` — result-figure archetypes,
  layout recipes, and a permission-gated NeurIPS/ICLR/SIGIR/KDD/WWW sample
  index (survey snapshot: 2026-09-02).
- `references/palette-library.md` — 10+ named qualitative, sequential,
  diverging, and editorial palettes with HEX values and accessibility rules.
- `assets/palette-sheet.svg` — a portable visual swatch sheet.
- `references/figure-manifest.example.yaml` — machine-readable template for
  provenance, data contracts, assets, exports, and QA.

The references are decision aids, not artwork to copy. Re-check paper links,
licenses, and current palette versions before citing or downloading anything.

## Validate

```bash
python /root/.codex/skills/.system/skill-creator/scripts/quick_validate.py \
  /root/.codex/skills/academic-figure-workflow
```

This repository contains no manuscript source, EEG recordings, generated paper
figures, credentials, or private project data. No software/license terms are
asserted beyond the upstream references' own terms.
