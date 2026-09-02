# Topic-driven style catalog

This catalog is a calibration aid, not a collection of venue templates. Conference communities overlap, and a paper's topic, audience, and existing figure language should outweigh a venue stereotype. Inspect a few recent, relevant papers before choosing a preset only when the user permits browsing; otherwise use the paper/repository's local visual language. Borrow principles (hierarchy, density, contrast), not artwork or copyrighted assets.

## Presets

### Analytical / minimal vector

Use for theory, optimization, algorithms, formal models, and quantitative comparisons. Prefer a white or lightly tinted background, geometric modules, one dark neutral plus one to three accent colors, restrained arrowheads, and ample whitespace. Keep equations, axes, ticks, confidence intervals, and curves as editable vector/text objects.

### Minimal flat infographic

Use for motivation, taxonomy, or a coarse-versus-fine comparison where one visual metaphor carries the argument. Use flat silhouettes or simple geometric icons, a small palette, consistent corner radii, and generous spacing. Avoid adding a decorative “middle concept” that has no evidence or mapping.

### Technology / system

Use for information retrieval, recommender systems, LLMs, data platforms, and software pipelines. Use modular cards, cool or neutral accents, explicit data-flow connectors, and restrained device/UI/network cues. Keep modules large enough to read at single-column width; do not turn every implementation detail into a box.

### Scientific realistic

Use for neuroscience, EEG, medicine, human sensing, robotics, and physical experiments. Use realistic or carefully rendered participants, devices, specimens, or scenes only for the physical context; pair them with exact vector plots, axes, and annotations. Mark synthetic imagery as illustrative when it could be mistaken for a measurement. EEG traces, electrode layouts, and numerical summaries must come from data/code or an explicitly labeled schematic.

### Hand-drawn / editorial

Use for behavioral, social, cognitive, educational, or story-led concepts when an informal metaphor improves accessibility. Limit the hand-drawn treatment to the illustrative layer; retain clean vector typography, alignment guides, and quantitative content. Avoid faux handwriting for labels that must be searchable or legible.

### Technical 3D / rendered

Use for hardware, mechanisms, molecules, geometry, and physical systems. Use a controlled camera, simple studio lighting, a quiet background, and a small number of materials. Put callouts, dimensions, and scientific labels in SVG rather than inside the render.

## Venue calibration examples

The following reference sources illustrate recurring patterns, not requirements. Paper links are preferred for research claims; proceedings indexes and tutorial slides are only visual-calibration aids:

- A NeurIPS schematic uses sparse blocks and restrained color to communicate data flow while keeping the structure geometric and label-driven: [Attention Is All You Need, NeurIPS 2017](https://papers.nips.cc/paper_files/paper/2017/file/3f5ee243547dee91fbd053c1c4a845aa-Paper.pdf).
- ICLR/OpenReview papers commonly combine a clean vector architecture with exact scaling/benchmark plots; use the paper's own typography and data rendering as the authority rather than adding pictorial decoration: [An Image is Worth 16x16 Words: Transformers for Image Recognition at Scale, ICLR](https://openreview.net/forum?id=YicbFdNTTy).
- SIGIR proceedings show framework and task-taxonomy diagrams suited to information-retrieval/system narratives: [SIGIR '24 proceedings](https://sigir-2024.github.io/proceedings.html).
- A KDD EEG example pairs a sensor/feature pipeline with EEG-specific scientific content, a useful model for separating realistic context from data-bearing geometry: [EEG-based Early Detection of Epileptic Seizures, KDD 2024](https://kdd2024.kdd.org/wp-content/uploads/2024/07/paper_10.pdf). Treat the preliminary PDF as a reading/principle reference only; do not copy or redistribute its artwork without permission.
- WWW tutorial material uses compact document/person/venue icons and graph connectors for heterogeneous-network explanations: [WWW 2024 tutorial slides](https://www2024.thewebconf.org/docs/tutorial-slides/text-attributed-graph-representation-learning.pdf). The linked PDF is marked “SMU Classification: Restricted”; use it only as a link/principle reference, and do not download, cache, or reuse screenshots without permission.

For data-bearing experimental panels, do not infer a style from an intro schematic. Route the visual question through [experimental-figure-catalog.md](experimental-figure-catalog.md), which records comparison, ablation, uncertainty, distribution, heatmap, efficiency, and qualitative-grid examples from the same venues. Select a palette only after choosing the encoding; use [palette-library.md](palette-library.md) for named HEX sets and continuous-map rules.

### What to record during a permitted venue survey

For each selected paper, record the venue/year, paper/figure URL, figure number or page, the analytical question, chart archetype, panel order, axis/legend treatment, uncertainty treatment, palette family, and the one principle worth adapting. Do not download or commit a paper's raster artwork unless its license and the user's purpose allow it. A survey is complete when it informs a concrete decision; collecting screenshots without a decision adds clutter.

## Selection heuristic

Score the brief on five questions before prompting: (1) Is the claim quantitative or structural? (2) Is a real physical subject/device central? (3) Does realism add evidence or only context? (4) How much abstraction must a first-time reader decode? (5) What style already dominates the paper? Quantitative/structural claims favor analytical or technology styles; a physical subject central to the experiment favors scientific realistic; a human-centered metaphor may justify hand-drawn; a simple comparison favors minimal flat. If scores conflict, choose the plainer style and explain the tradeoff in the brief.

For a mixed figure, assign a style per layer: e.g., scientific-realistic stimulus + analytical EEG trace, or minimal flat icons + technology pipeline. Use a shared palette, scale, and lighting rule so the mixture reads as intentional.
