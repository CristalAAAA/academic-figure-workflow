# Figure-package contract

Use this layout for every figure that is meant to be edited, reviewed, or
included in a manuscript. Keep the package scoped to one figure and use a
version in the figure ID or filename; do not mix unrelated experiments or
paper-wide assets into it.

```text
figure/<figure-id>/
├── final/
│   ├── <figure-id>.svg       # editable vector export
│   ├── <figure-id>.png       # target-size or specified-DPI raster
│   └── <figure-id>.pdf       # same composition; vector when possible
├── previews/
│   └── <figure-id>_preview.png
├── source/                    # optional when source already lives under repo scripts/
│   └── <figure-id>.py|svg
├── frameworks/               # optional, only for a hand-authored SVG workflow
│   └── <figure-id>_framework.svg
├── assets/
│   ├── imagegen/              # accepted, no-text/no-watermark raster assets
│   └── data/                  # optional deterministic plot exports
├── prompts/
│   ├── asset-*.txt            # exact prompts and generation notes
│   ├── figure-brief.md        # takeaway, storyboard, style decision
│   └── manifest.yaml          # data, provenance, exports, QA
├── archive/                   # superseded versions; never silently overwrite
└── README.md                  # how to regenerate and edit this figure
```

## Source and asset rules

1. Record one canonical composition source. Prefer Python/Matplotlib for dense
   method layouts, aligned curves, or data-bearing panels; use direct SVG when
   it is genuinely the simpler source. If the source lives under repository
   `scripts/`, record its exact path and revision instead of duplicating it.
   The final SVG must contain selectable text and editable vector geometry. It
   may reference local images during development, but also provide a standalone
   variant with sanitized data-URI images (or document the exact portable asset
   directory). Never call a flattened PNG an editable SVG.
2. Every imagegen asset gets its own file and provenance record: prompt,
   generation mode, dimensions, color mode/alpha status, checksum, and the
   intended `data-role`. Reject baked text, watermark, logo, chart, axis, or
   accidental crop. Keep the original and any derivative under versioned names.
3. Every measured curve/table/heatmap records the authorized data path (or
   immutable SHA-256), plotting script and revision, units, aggregation,
   uncertainty, and transform. Prefer imported SVG/PDF paths; if a raster
   export is unavoidable, record native pixels and effective DPI and keep the
   plotting code beside the package.
4. A package README must state the canonical source, interpreter/renderer and
   export command, target physical size, font/fallback, and which layers are
   safe to edit independently. For Matplotlib, retain SVG text with
   `svg.fonttype="none"` and embed TrueType fonts in PDF. The default is Times
   New Roman; any deliberately different display font belongs only to an
   explicitly selected style layer and must be recorded.

## Package-level QA

Before delivery, verify that:

- `final/*.svg`, `final/*.png`, and `final/*.pdf` render the same current
  version and have a tight, known page boundary;
- all local image references resolve (or the standalone SVG is self-contained),
  and no remote URL, script, event handler, external font, or unsafe XML entity
  remains;
- SVG text is present for labels and chart annotations, IDs are unique, and
  numerical marks are traceable to the recorded data/code;
- the target-column raster passes clipping, readability, grayscale, CVD,
  contrast, and effective-DPI checks;
- the manifest has no placeholder paths, hashes, `n: 0`, or `WARN` status for a
  measured final figure; and
- old versions remain in `archive/` when a revision was requested.

If the user asks for only a preview, keep the same source/asset distinction but
may omit final exports until the figure is approved. If the figure is genuinely
raster-only by user choice, label that exception and do not claim editability.
