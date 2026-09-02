# Academic Figure Workflow

Codex skill for building publication-ready scientific figures as editable,
reproducible packages. The canonical composition is an SVG: text, axes,
arrows, legends, and quantitative geometry remain vector/editable; ImageGen is
used only for separate non-quantitative assets with no text, labels, charts, or
watermarks; authorized Python/project code supplies real curves and tables.

Each completed figure should have `final/` (current SVG, PNG, PDF),
`frameworks/` (SVG skeleton and preview), `assets/`, `prompts/` (brief,
provenance, manifest), and `archive/` (superseded versions). Times New Roman
is the default font; an explicitly selected hand-drawn/editorial style may use
a limited display font while scientific labels stay legible and editable.

Run the validator with:

```bash
python /root/.codex/skills/.system/skill-creator/scripts/quick_validate.py \
  /root/.codex/skills/academic-figure-workflow
```
