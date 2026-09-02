# Prompt templates for figure assets

Use these as starting points, then replace the bracketed fields with the figure brief and the selected style preset. Keep one visual role per generation request. Exact labels, axes, legends, and scientific curves belong in the SVG, not in the prompt. Do not write “realistic” unless the style decision actually selected the scientific-realistic or technical-3D preset.

## Realistic cutout

```text
Create a publication-quality [selected style preset / medium] cutout of [subject] performing [action], viewed from [camera/view direction].
Match the neighboring figure assets: [line quality or material treatment / lighting / palette / level of abstraction]. Show the complete subject, including [hands, device, wires, relevant context], with generous transparent margins on every side. Keep the pose and orientation [details]. No text, labels, chart, logo, watermark, or decorative background. Output a true transparent PNG suitable for compositing.
```

For an edit of an existing local asset, state exactly what must be preserved (identity, pose, clothing, camera angle) and what may change (background removal, missing edge completion, scale). Supply the local path through the image-generation tool according to its attachment rules; do not silently regenerate unrelated details.

## Video/task frame

```text
Create a [selected style preset / medium] [aspect-ratio] video frame showing [concrete action/object] at [stage of process].
Use the same camera or graphic construction, surface, lighting, and color treatment as these companion frames: [brief continuity notes]. Compose the subject so it remains legible inside a fixed rectangular crop. No captions, UI, timestamps, logos, watermark, or invented scientific annotations.
```

Generate variants that differ in the intended process state, not in camera geometry. Fit each accepted frame into the pre-existing SVG clip rectangle; never let a generated frame redefine panel widths.

## Small task icon

```text
Create a clean, [selected style preset / medium] compact visual icon for [task/concept], centered in a square transparent canvas. Use [object/action] as the unmistakable cue, with [palette and stroke/detail constraints] matching the figure. No words, letters, arrows, logo, watermark, or extra objects; leave safe padding around the silhouette.
```

If a symbol can be expressed with simple SVG geometry (clock, skip chevrons, arrow, bracket, bin), draw it in SVG instead of generating it. This keeps the icon sharp and its proportions editable.

## Constrained revision

```text
Edit only [named asset and defect]. Preserve every other visible detail: [identity, pose, colors, camera, crop, neighboring negative space]. Fix [specific defect] and add safe margins so the complete subject is visible. Do not alter text, axes, chart traces, panel boundaries, or any other asset. No new text, logo, watermark, or background.
```

After generation, record the prompt, local output path, dimensions, color mode/alpha status, generation mode, and a checksum in the project’s prompt or asset manifest. Treat the output as a candidate until it passes the full-size and target-column checks.

## Experimental-result brief (do not send the chart to ImageGen)

Use this as a handoff to the project's plotting/SVG layer:

```text
Claim: [one sentence]
Question/archetype: [comparison | convergence | ablation | sensitivity | distribution | trade-off | error matrix | signal/map | qualitative grid | user study | efficiency]
Data source + commit/hash: [path]
Observation unit and n: [subject/example/seed/...]
Metric and units/direction: [name, unit, higher/lower is better]
Aggregation + uncertainty: [mean/median; SD/SEM/CI/bootstrap; interval level]
Axes/domain/transform: [x, y, limits, zero/reference]
Baseline and proposed-method mapping: [neutral/accent, marker/line styles]
Palette family/name/version: [qualitative/sequential/diverging; HEX or sampling rule]
Panel order and shared scales: [layout]
Evidence that must remain exact: [points, bars, intervals, traces, cells, table values]
```

The plotting code must render every item under “Evidence that must remain exact.” ImageGen can be called separately for a clearly non-quantitative context asset, using one of the selected style presets, but it must not be asked to redraw this chart, its labels, or its data.
