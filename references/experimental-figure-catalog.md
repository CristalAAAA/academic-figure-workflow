# Experimental-results figure catalog

Use this reference when a figure communicates measured or derived values. It is a catalog of visual questions and reproducible encodings, not a gallery to copy. Public venue papers are calibration examples only: inspect them when the user permits browsing, record the useful principle (hierarchy, density, annotation, or palette), and redraw from the user's data and code.

The venue list is a research snapshot (2026-09-02), not a live feed. Re-check a link and its publication/license metadata before citing it in a manuscript or downloading any asset.

## Start with a data contract

Before choosing a chart, write a one-line claim and fill these fields:

| Field | Required decision |
| --- | --- |
| Observation unit | What one point/bar/cell summarizes (example, user, session, subject, seed, or batch) |
| Metric | Name, units, direction of improvement, valid range, and whether it is absolute, relative, normalized, or log-transformed |
| Aggregation | Mean/median/weighted mean, pooling level, and treatment of missing values/outliers |
| Uncertainty | SD, SEM, confidence/credible interval, bootstrap interval, or quantiles; state the number of runs/subjects `n` |
| Comparison | Baseline, proposed method, paired/unpaired design, statistical test, multiplicity correction, and practical effect size |
| Axis contract | Domain, limits, ticks, transforms, zero reference, and whether categories are ordered |
| Provenance | Data path, plotting script, commit/hash, random seeds, and a machine-readable export used to render the figure |

If one of these is unknown, keep the figure schematic and label it as such; do not reverse-engineer numbers from a raster screenshot.

## Choose by the question, not by fashion

| Scientific question | Preferred first choice | Geometry and annotation | Common failure to reject |
| --- | --- | --- | --- |
| Which method is better on a small set of tasks? | Dot/interval (horizontal is usually easiest to scan) | One row per task, point = estimate, interval = stated uncertainty, a neutral baseline, and one accent for the proposed method; sort only when order is meaningful | Rainbow bars, unlabeled error bars, or a truncated bar axis that exaggerates a small gap |
| How do methods change over time, steps, length, or budget? | Line + uncertainty ribbon | Connect only an ordered x-axis; show median/mean and a run/subject band, log axis only when justified by the data | Smoothed curves without a smoothing note, spaghetti of every run, or categorical points joined by lines |
| Which component or loss term matters? | Ablation dot/interval, slope graph, or compact small multiples | Keep the full model in a stable accent, remove/change one factor at a time, use a shared scale, and order panels by the causal question | Changing several factors in one row, eight colors for eight variants, or treating an ablation as proof of causality |
| How sensitive is the method to two parameters? | Rectangular heatmap or contour map | Put one parameter per axis, annotate the optimum only if it is data-supported, use a monotonic sequential map, and print the numeric grid or colorbar units | Interpolating sparse measurements as if continuous, hiding missing cells, or using a diverging map with no meaningful midpoint |
| How stable or variable are observations? | Box/violin/raincloud plus raw points or ECDF | Show sample count and a robust summary; jitter deterministically and keep a common y-scale across groups | A violin for `n` too small to support a shape, a box with no observations, or a mean-only bar hiding outliers |
| Are two quantities related or is there a trade-off? | Scatter with marginal/context or Pareto frontier | Map each variable to an axis, encode method by marker/line style, show the frontier only when it is defined, and report correlation/fitting choices | Connecting unordered points, implying causation from a fit line, or using a 3-D perspective plot |
| Where do errors occur across classes or conditions? | Confusion/error matrix or normalized stacked bar | State count versus row/column percentage, keep class order fixed, print a colorbar and representative cell values, and use a neutral zero | A heatmap with an unstated normalization, tiny unreadable labels, or red/green as the only distinction |
| What is the spatial, temporal, spectral, or channel structure? | Exact trace, topomap, spectrogram, or 2-D heatmap | Generate the signal/grid from the source data; define time/frequency/channel axes, units, baseline, and color limits; use one scale across comparable panels | Image-generated traces, arbitrary smoothing, inconsistent color limits, or a decorative waveform that is not measured |
| What is the estimated effect relative to a null/reference? | Forest or estimation plot | Plot the estimate and interval on a common effect axis, draw the null/reference line, define each contrast and multiplicity rule, and report the practical effect size | Significance stars without intervals, mixing incompatible contrasts, or treating a non-significant result as evidence of no effect |
| Is a probabilistic model calibrated? | Reliability diagram plus confidence histogram | Bin by predicted confidence, show the ideal diagonal, include bin counts and intervals, and report ECE/Brier or another declared score | Empty/unequal bins, an unlabeled smoothing choice, or a calibration curve with no sample counts |
| How does retrieval/classification quality change with threshold or rank? | ROC/PR, Recall@K, or NDCG@K curve | Keep the operating point and class prevalence visible, use bootstrap bands when available, and state whether curves are macro/micro/pooled | Comparing only AUC under imbalance, hiding the operating point, or connecting unrelated threshold settings |
| Where is an effect located in space or topology? | Coordinate-faithful map/topomap/network overlay | Preserve geometry, mask invalid regions, show a scale bar/reference coordinate, and use a declared baseline-centered color scale | Distorting geography/anatomy to fit a layout, coloring disconnected regions as if adjacent, or omitting the mask/scale |
| Does a qualitative example support the quantitative claim? | Code-generated aligned image/text grid beside the result | Fix the sample selection, crop, ordering, and column widths; label examples outside the images and link them to the metric/panel | AI-generated “evidence,” cherry-picked examples without a rule, or a collage that dominates the measured result |
| What did participants/users choose? | Diverging stacked Likert bars or dot/interval | Keep response order fixed, show `n` and missingness, use a neutral midpoint, and report the aggregation/scale | Treating ordinal responses as precise continuous values without justification or using a pie chart for many items |
| How does accuracy trade against cost, latency, memory, or energy? | Pareto scatter / connected budget curve | Use log axes when ranges span orders of magnitude, annotate units and hardware, and mark dominated points lightly | Hiding the cost axis, mixing hardware settings, or ranking by an unreported composite score |
| Are there many metrics or datasets to report? | Semantic table plus a restrained heatmap or dot matrix | Keep exact values and uncertainty in the table; bold/outline the best only under a declared rule; use a color tint as a locator, not a value replacement | Color-only tables, excessive decimal places, inconsistent rounding, or a “best” cell unsupported by a statistical comparison |

### Fast routing rules

1. If the x-axis is genuinely ordered, use a line, ribbon, or heatmap. If it is nominal, use points/bars or small multiples and do not connect categories.
2. If the claim is about a difference, show a difference or interval directly; if it is about a distribution, show observations or quantiles rather than only a mean.
3. If there are more than roughly six methods, direct-label the important series, split into small multiples, or use a table. Adding more hues rarely improves reading.
4. Use bars for a few discrete magnitudes when a zero reference is meaningful. Use dots/intervals for close values, signed effects, or non-zero baselines.
5. Use sequential color for low→high, diverging color for negative↔positive around a meaningful center, and qualitative color only for nominal identities. Never use a rainbow/`jet` map for an ordered scientific variable.
6. Redraw every axis, tick, legend, number, interval, and colorbar in the deterministic plotting layer. A raster can be used for context, never for quantitative geometry.

## Reusable layout recipes

### Main benchmark panel

Use a wide horizontal dot/interval plot when the paper's central claim is a small improvement across tasks. Put tasks on rows, share one metric axis, keep baselines gray, highlight the proposed method with one strong color, and add a compact `n`/interval note. If a table is required for exact values, place it below or in the appendix and keep the plot as the visual summary.

### Ablation strip

Use one row or small multiple per factor. Keep the full model in the same x-position and accent across panels; encode removal with a neutral point or dashed outline. A slope graph is useful for two conditions; a dot/interval is safer than a bar when differences are small. Do not imply a causal decomposition when factors interact.

### Convergence and robustness

Plot a central estimate plus a translucent uncertainty band, not a separate line for every seed. State whether the band is across seeds, subjects, or bootstrap resamples. For parameter sensitivity, use a grid/heatmap and retain the measured grid coordinates; do not invent smooth intermediate values.

### Distribution and error analysis

Use a box/violin/raincloud only when the sample supports the shape, and overlay deterministic raw points for small or moderate `n`. For confusion/error matrices, use a single shared colorbar and write “count,” “row %,” or “column %” explicitly. Put the metric that motivates the matrix in a neighboring compact panel rather than burying it in the caption.

### Qualitative evidence grid

Select examples by a recorded rule (random seed, nearest/farthest case, or fixed IDs), render them from the actual dataset/code, and keep identical crops and scales. Put the quantitative result first or give it the larger visual area. Any illustrative or generated image must be marked as illustrative and must not be presented as a measured sample.

### Multi-panel composition

Give every panel one job, label panels `(a)`, `(b)`, … in vector text, align plot boxes, and share x/y limits whenever comparisons require it. Use one legend if the mapping is global; otherwise put a short direct label near each series. Reserve the top-left or first reading position for the paper's primary claim, not an ornamental overview.

## Venue calibration sample index

These are deliberately varied examples from NeurIPS, ICLR, SIGIR, KDD, and WWW. The useful question is “what visual decision can be reused?” rather than “what style belongs to this venue.” Open the links only when the user permits browsing, and check the linked paper's license and figure caption before saving any local reference image.

1. **NeurIPS — architecture/flow schematic.** [Attention Is All You Need (NeurIPS 2017)](https://papers.nips.cc/paper_files/paper/2017/file/3f5ee243547dee91fbd053c1c4a845aa-Paper.pdf), Figures 1–2 use sparse geometric blocks and restrained color to explain a model. Reuse the flow grammar; keep exact equations as text/vector objects.
2. **NeurIPS — uncertainty under shift.** [Can You Trust Your Model's Uncertainty? Evaluating Predictive Uncertainty under Dataset Shift (NeurIPS 2019)](https://papers.nips.cc/paper/2019/file/8558cb408c1d76621371888657d2eb1d-Paper.pdf) is a reference for aligned accuracy/calibration panels and uncertainty summaries. Reuse shared shift axes and explicit uncertainty definitions.
3. **NeurIPS — qualitative grid plus quantitative table.** [Denoising Diffusion Probabilistic Models (NeurIPS 2020)](https://papers.nips.cc/paper/2020/file/4c5bcfec8584af0d967f1ab10179ca4b-Paper.pdf) separates generated-example grids from tables and curves. Reuse the division of labor; never use generated imagery to invent a metric.
4. **NeurIPS — sensitivity curves.** [Towards Deeper Graph Neural Networks with Differentiable Group Normalization (NeurIPS 2020)](https://proceedings.neurips.cc/paper/2020/file/33dd6dba1d56e826aac1cbf23cdcca87-Paper.pdf) is useful for depth/normalization sensitivity plots with a stable method mapping. Keep the x-axis and units explicit.
5. **NeurIPS — rate–distortion and ablation.** [Compression with Bayesian Implicit Neural Representations (COMBINER, NeurIPS 2023)](https://proceedings.neurips.cc/paper_files/paper/2023/file/060b2af0081a460f7f466f7f174d9052-Paper-Conference.pdf), Figures 2–6 separate benchmark curves, ablations, convergence, and heatmap diagnostics. Reuse the one-question-per-panel discipline and data-derived color limits.
6. **ICLR — architecture plus scaling.** [An Image is Worth 16x16 Words: Transformers for Image Recognition at Scale (ICLR 2021)](https://openreview.net/forum?id=YicbFdNTTy) pairs a clean block diagram with scaling/benchmark plots. Reuse shared typography and a clear transition from method to evidence.
7. **ICLR — graph message passing.** [Graph Attention Networks (ICLR 2018)](https://openreview.net/forum?id=rJXMpikCZ) redundantly encodes node/edge roles with shape and color. Reuse the redundancy principle in a conceptual panel, not its exact artwork.
8. **ICLR — calibration.** [Top-label calibration and multiclass-to-binary reductions (ICLR 2022)](https://openreview.net/forum?id=WqoBaaPHS-) uses a reliability-diagram style with a reference diagonal and class-level detail. Reuse the reference line, bin counts, and explicit calibration metric; verify the exact panel composition in the permitted source survey.
9. **ICLR — multi-task evaluation.** [Imitating Graph-Based Planning with Goal-Conditioned Policies (ICLR 2023)](https://openreview.net/pdf?id=6lUEy1J5R7p) combines a planning/policy schematic with evaluations across long-horizon control tasks. Reuse the separation between a conceptual mechanism and data-bearing task panels; keep task names, units, and run aggregation explicit.
10. **SIGIR — behavior distributions and ablation.** [Improving Implicit Feedback-Based Recommendation through Multi-Behavior Alignment (SIGIR 2023)](https://doi.org/10.1145/3539618.3591697) (use the [open author copy](https://eprints.gla.ac.uk/298598/2/298598.pdf) only as a reading mirror) combines behavior distributions, sensitivity/ablation views, and exact tables. Reuse the distinction between exploratory distribution and headline comparison.
11. **SIGIR — physiological timeline and distributions.** [Characterizing Information Seeking Processes with Multiple Physiological Signals (SIGIR 2024)](https://doi.org/10.1145/3626772.3657793) (open [author copy](https://www.danulahettiachchi.com/papers/sigir24.pdf), marked CC BY-ND 4.0) is a useful multimodal reference for phase/timeline alignment and physiological summaries. Read and cite it under its license; do not modify or republish its figures without permission. Keep time axes shared and signals data-derived.
12. **KDD — architecture, benchmark, and ablation.** [AM-GCN official KDD page](https://www.kdd.org/kdd2020/accepted-papers/view/am-gcn-adaptive-multi-channel-graph-convolutional-networks.html) and its [author-hosted PDF](https://pengcui.thumedialab.com/papers/AdaptiveGCN.pdf) separate the system diagram from benchmark tables and component studies. Reuse stable method colors across panels.
13. **KDD — depth/oversmoothing curves.** [Towards Deeper Graph Neural Networks (KDD 2020)](https://www.kdd.org/kdd2020/accepted-papers/view/towards-deeper-graph-neural-networks.html) is a calibration source for ordered-depth performance curves. Keep the depth axis and failure regime visible.
14. **KDD — accuracy–diversity trade-off.** [A Framework for Recommending Accurate and Diverse Items Using Bayesian Graph Convolutional Neural Networks (BGCF)](https://kdd.org/kdd2020/accepted-papers/view/a-framework-for-recommending-accurate-and-diverse-items-using-bayesian-grap.html) motivates Pareto/trade-off plots and uncertainty summaries. Label both objectives and the evaluation protocol.
15. **KDD — signal-specific pipeline.** [EEG-based Early Detection of Epileptic Seizures (KDD 2024)](https://lamarr-institute.org/publication/eeg-based-early-detection-of-epileptic-seizures/) (official [accepted-paper/short-paper PDF](https://kdd2024.kdd.org/wp-content/uploads/2024/07/paper_10.pdf)) pairs an EEG feature/model pipeline with scientific signal content. The preliminary PDF carries a reproduction restriction and placeholder bibliographic fields; use it for reading/principles only, and do not treat it as a canonical DOI record or cache, copy, or redistribute its artwork without permission. Reuse the separation between physical context and exact signal geometry; generate traces from data/code.
16. **WWW — efficiency/scaling.** [NetSMF: Large-Scale Network Embedding as Sparse Matrix Factorization (WWW 2019)](https://www.microsoft.com/en-us/research/publication/netsmf-large-scale-network-embedding-as-sparse-matrix-factorization/) (author [PDF](https://www.microsoft.com/en-us/research/wp-content/uploads/2019/03/www19netsmf.pdf)) uses multi-panel dimension/sparsity/thread/time comparisons. Reuse aligned axes and explicit hardware/runtime units.
17. **WWW — dual-graph recommendation.** [Graph Neural Networks for Social Recommendation (WWW 2019)](https://ira.lib.polyu.edu.hk/bitstream/10397/81232/1/Fan_Graph_neural_networks.pdf) separates a two-graph system schematic from exact recommendation results. The paper is CC-BY; still credit it and redraw rather than copying.
18. **WWW — icon/graph language.** [WWW 2024 text-attributed graph tutorial slides](https://www2024.thewebconf.org/docs/tutorial-slides/text-attributed-graph-representation-learning.pdf) use compact document/person/venue icons and connectors. The linked PDF is marked “SMU Classification: Restricted”; use it only as a link/principle reference, and do not download, cache, or reuse screenshots without permission. Keep measured graph statistics in an exact plot.
19. **WWW — proceedings search index.** [The Web Conference 2024 proceedings archive](https://archives.iw3c2.org/proceedings/www2024/index.html) links research and companion papers. Use it to find a domain-specific result figure when the user's topic is Web/recommendation/IR; record the paper, figure number, and observed principle in `prompts/`.

The sample links are starting points, not an exhaustive ranking. A good local reference set normally contains at least one comparison, one uncertainty plot, one ablation, one calibration or ROC/PR plot, one matrix/heatmap, one qualitative grid, and one domain-specific signal or efficiency plot.

## Result-figure review checklist

- Can a reader state the claim from the plotted marks without reading a long caption?
- Are the data source, unit of observation, `n`, uncertainty definition, and metric units recoverable?
- Are axes, transforms, zero references, colorbars, and normalization explicit?
- Does panel order follow the claim, with common scales and a single method mapping?
- Is the proposed method highlighted once, while baselines remain legible and neutral?
- Would the conclusion survive grayscale, common color-vision-deficiency simulations, and a single-column rasterization?
- Are qualitative examples selected reproducibly and clearly separated from measured evidence?
- Can the exact figure be regenerated from the recorded data/code/hash without ImageGen?

If any answer is “no,” classify the issue as a framework/data-contract blocker before adjusting decoration or palette.
