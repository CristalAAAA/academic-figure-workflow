# Palette library for scientific figures

Use this library after the chart encoding is fixed. The lists below are starting points with explicit HEX values; they are not a substitute for checking the actual colors on the figure's background, at its final size, in grayscale, and under common color-vision-deficiency (CVD) simulations. Never let hue be the only carrier of a critical result. Do not fetch the linked pages automatically in a normal offline run; open them only when the user has permitted a current venue/palette survey.

For a quick visual scan, open the companion [palette-sheet.svg](../assets/palette-sheet.svg). The sheet is deterministic and contains no external images or fonts.

### Core 10 to try first

To keep the design search small, start with Okabe–Ito; Paul Tol Bright, Muted, or High Contrast; ColorBrewer Set2 or Dark2; Seaborn Colorblind; IBM Carbon categorical; ColorBrewer RdBu; and one continuous family (Viridis, Cividis, or Crameri). ColorBrewer Paired, Tol Vibrant, BrBG, and the Xiaohongshu-inspired accent are optional extensions for a specific relationship or visual brief, not extra colors to put in one legend.

## Choose the palette family first

- **Qualitative**: nominal methods, datasets, classes, or conditions. Hues should be distinguishable, but their order must not imply a ranking.
- **Sequential**: one ordered quantity from low to high. Luminance should change monotonically; add a labeled colorbar and units.
- **Diverging**: signed deviation or two directions around a meaningful center (usually zero or a reference). Put the neutral color at the center and state the center explicitly.
- **Editorial/accent**: backgrounds, callouts, or illustrative layers. These can be fashionable, but must not silently become the encoding for a measured variable.

The [ColorBrewer guidance](https://colorbrewer2.org/learnmore/schemes.html) describes the qualitative/sequential/diverging distinction and offers colorblind-safe, print-friendly filters. The [Paul Tol notes](https://sronpersonalpages.nl/~pault/data/colourschemes.pdf) and [Crameri palettes](https://www.fabiocrameri.ch/colourpalettes/) provide additional accessibility and perceptual-order checks.

## Discrete palettes (good first choices for method comparisons)

The HEX order is a suggested default order, not a semantic ranking. Use only as many colors as the figure can distinguish; make the proposed method explicit with position, line weight, or a direct label as well.

### 1. Okabe–Ito / Color Universal Design

**Role:** qualitative, CVD-friendly default for lines and markers (8 colors).

`#000000  #E69F00  #56B4E9  #009E73  #F0E442  #0072B2  #D55E00  #CC79A7`

Source/reference: [Okabe–Ito/CUD reference](https://jfly.uni-koeln.de/color/index.html) and the [Colorblind LaTeX table](https://mirrors.mit.edu/CTAN/macros/latex/contrib/colorblind/colorblind_doc.pdf). Yellow is best paired with a dark outline or marker; do not use it for small text on white.

### 2. Paul Tol Bright

**Role:** qualitative, print- and CVD-conscious line palette (7 colors).

`#4477AA  #EE6677  #228833  #CCBB44  #66CCEE  #AA3377  #BBBBBB`

Source: [Paul Tol, Colour Schemes](https://sronpersonalpages.nl/~pault/data/colourschemes.pdf). The final gray is useful for a control or unavailable condition; verify contrast when lines are thin.

### 3. Paul Tol Muted

**Role:** softer qualitative palette for dense multi-series plots (9 colors).

`#CC6677  #332288  #DDCC77  #117733  #88CCEE  #882255  #44AA99  #999933  #AA4499`

Source: [Paul Tol, Colour Schemes](https://sronpersonalpages.nl/~pault/data/colourschemes.pdf). It is intentionally less vivid and lacks a clear medium blue; use direct labels and line styles when series are numerous.

### 4. Paul Tol High Contrast

**Role:** qualitative, high-contrast/grayscale-friendly three-way comparison.

`#004488  #DDAA33  #BB5566`

Source: [Paul Tol, Colour Schemes](https://sronpersonalpages.nl/~pault/data/colourschemes.pdf). A strong choice for “baseline / competitor / ours”; the luminance separation helps when printed monochrome.

### 5. Paul Tol Vibrant

**Role:** qualitative, high-saturation alternative for a small set of clearly separated series (7 colors).

`#EE7733  #0077BB  #33BBEE  #EE3377  #CC3311  #009988  #BBBBBB`

Source: [Paul Tol, Colour Schemes](https://sronpersonalpages.nl/~pault/data/colourschemes.pdf). It is designed to remain distinguishable for common CVD, but cyan/magenta and the gray can still merge at tiny sizes; add marker/line-style redundancy.

### 6. ColorBrewer Set2

**Role:** qualitative, friendly small-multiple or categorical palette (8 colors).

`#66C2A5  #FC8D62  #8DA0CB  #E78AC3  #A6D854  #FFD92F  #E5C494  #B3B3B3`

Source: [ColorBrewer 2.0](https://colorbrewer2.org/). Pastel colors can disappear in tiny lines; reserve the lighter swatches for fills or larger marks.

### 7. ColorBrewer Dark2

**Role:** qualitative, darker lines and text on a light background (8 colors).

`#1B9E77  #D95F02  #7570B3  #E7298A  #66A61E  #E6AB02  #A6761D  #666666`

Source: [ColorBrewer 2.0](https://colorbrewer2.org/). Good for compact plots where Set2 lacks contrast; the website's CVD/print filters are scheme- and class-count-specific, so test the exact subset used and do not assume every eight-color combination is safe.

### 8. ColorBrewer Paired

**Role:** paired categories (for example, before/after or train/test) with related light/dark hues (12 colors).

`#A6CEE3  #1F78B4  #B2DF8A  #33A02C  #FB9A99  #E31A1C  #FDBF6F  #FF7F00  #CAB2D6  #6A3D9A  #FFFF99  #B15928`

Source: [ColorBrewer 2.0](https://colorbrewer2.org/). Use adjacent pairs only when the pairing is meaningful; otherwise the many hues overload a single legend.

### 9. Seaborn Colorblind

**Role:** qualitative, accessible alternative with a contemporary plotting appearance (10 colors).

`#0173B2  #DE8F05  #029E73  #D55E00  #CC78BC  #CA9161  #FBAFE4  #949494  #ECE133  #56B4E9`

Source: [Seaborn palette documentation](https://seaborn.pydata.org/tutorial/color_palettes.html) and the pinned [v0.13.2 palette definition](https://github.com/mwaskom/seaborn/blob/v0.13.2/seaborn/palettes.py). If a different release is used, record that release and re-run the visual checks. The pale pink and yellow need adequate mark size/outline.

### 10. IBM Carbon categorical

**Role:** categorical palette for technology/system figures and dashboards (use the first `k` colors in the documented order).

`#6929C4  #1192E8  #005D5D  #9F1853  #FA4D56  #570408  #198038  #002D9C  #EE538B  #B28600  #009D9A  #012749  #8A3800  #A56EFF`

Source: [IBM Carbon data-visualization palettes](https://carbondesignsystem.com/data-visualization/color-palettes/). Carbon explicitly curates the sequence for neighboring contrast; do not reorder it casually. Use a neutral gray for controls when possible.

## Ordered and signed palettes

### 11. ColorBrewer RdBu (11-step diverging)

**Role:** negative-to-positive effects around a meaningful neutral midpoint.

`#67001F  #B2182B  #D6604D  #F4A582  #FDDBC7  #F7F7F7  #D1E5F0  #92C5DE  #4393C3  #2166AC  #053061`

Source: [ColorBrewer 2.0](https://colorbrewer2.org/). Center the scale at the declared reference (for example, zero); do not use it for an unordered method legend.

### 12. ColorBrewer BrBG (11-step diverging)

**Role:** signed change where a brown–teal contrast is preferable to red–blue.

`#543005  #8C510A  #BF812D  #DFC27D  #F6E8C3  #F5F5F5  #C7EAE5  #80CDC1  #35978F  #01665E  #003C30`

Source: [ColorBrewer 2.0](https://colorbrewer2.org/). Label the midpoint and use symmetric limits when the scientific comparison is symmetric.

## HEX usable for marks is not automatically usable for text

Most saturated swatches are excellent for a filled region, thick line, or outlined marker but fail as small text on white. In particular, Okabe–Ito yellow/sky blue, ColorBrewer Set2's pale swatches, and the bright end of Viridis need a dark label/outline and sufficient mark area. Put labels in a dark neutral (for example `#222222` or `#333333`) and test graphic contrast against the actual background; do not put white text on a light swatch by habit. As a practical screen, aim for at least 3:1 contrast for non-text graphical marks and roughly 4.5:1 for small text when the venue has no stricter rule, then follow the venue/journal standard.

### 13. Viridis (continuous, 7 sampled anchors)

**Role:** perceptually ordered sequential values, density, intensity, or magnitude.

`#440154  #482878  #3E4989  #31688E  #26828E  #35B779  #FDE725`

Source: [Matplotlib colormap reference](https://matplotlib.org/stable/users/explain/colors/colormaps.html). These are convenient seven-stop anchors; for a continuous map, sample the named `viridis` map in the plotting code rather than hand-interpolating RGB values. Never use the endpoint yellow for tiny labels on white.

### 14. Cividis (continuous, named map)

**Role:** sequential values when CVD robustness and grayscale behavior are especially important.

Use the named `cividis` map in Matplotlib or an equivalent renderer, with a labeled colorbar and fixed limits across panels. See [Matplotlib's colormap reference](https://matplotlib.org/stable/users/explain/colors/colormaps.html). Do not copy a screenshot of a gradient; record the renderer and sampling rule in the manifest.

### 15. Crameri Batlow / Scientific Colour Maps

**Role:** perceptually uniform sequential or cyclic scientific fields, especially maps, spectra, and physical signals.

Choose a named map such as `batlow`, `batlowW`, `lipari`, or `roma` from [Scientific Colour Maps](https://www.fabiocrameri.ch/colourmaps/), record the version, and use the supplied color table. Crameri documents perceptual ordering, CVD, black-and-white, and print behavior; still test the exact background and resolution used in the paper.

## Editorial and Xiaohongshu-inspired accents

### 16. Soft red editorial accent (non-quantitative by default)

**Role:** callouts, section tags, or illustrative backgrounds—not a method ranking or continuous measurement.

`#FF2442  #FFF4F5  #F5F5F5  #333333  #FDBC5F`

`#FF2442` is commonly associated with Xiaohongshu's brand color; the visual treatment (near-white canvas, soft rounding, very light shadow) is summarized in this [third-party design-system reconstruction](https://github.com/nexu-io/open-design/blob/main/design-systems/xiaohongshu/DESIGN.md), not an official scientific standard. Use it only when the paper's topic calls for an editorial accent, credit the inspiration internally, and run the same contrast/CVD/grayscale checks before allowing it into a data-bearing layer. Do not crawl or download platform/user artwork, reproduce a platform logo, or copy another creator's palette board. If the user provides a reference image, confirm that they are authorized to use it and redraw the structural figure in SVG.

## Practical selection recipes

- **Three-way benchmark:** Tol High Contrast or Okabe–Ito first three non-black colors; proposed method gets a consistent outline/weight, baseline is gray.
- **Four to six methods:** Okabe–Ito, Tol Bright, Seaborn Colorblind, or Carbon categorical; direct-label the proposed method and use marker shape/dash as a second channel.
- **Many datasets/tasks:** keep methods fixed by color and use small multiples for datasets; do not assign a new rainbow per panel.
- **Signed effect/ablation delta:** RdBu or BrBG centered at zero, with the numerical zero line and symmetric limits visible.
- **Heatmap/time-frequency/EEG:** Viridis/Cividis for nonnegative power or intensity; a diverging map only for baseline-subtracted signed values; one shared colorbar for comparable panels.
- **Motivation illustration:** the soft-red editorial set can be an accent, while all exact axes and signals remain neutral/vector-clean.

## Accessibility and export gate

1. Simulate protanopia, deuteranopia, and tritanopia; then rasterize at the target column width and inspect grayscale.
2. Check contrast against the actual fill/background and keep line widths/markers large enough for print. Yellow, pale pink, and light cyan often need a dark outline.
3. Repeat the legend mapping in line style, marker, position, or direct labels. Color alone is never the sole encoding for “ours,” “failure,” significance, or a safety-critical state.
4. Keep one primary accent plus neutral baselines; reserve red for a genuinely negative/error state instead of using it merely to make a result look important.
5. Record palette name/version, HEX values or colormap sampling rule, background, CVD/grayscale result, and any custom modification in the figure manifest. If a palette fails, change the palette or encoding—not the data limits—to make it look better.
