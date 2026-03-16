# Figure Generation for CNS Journals

## CNS Color Palette

CNS journals (Cell/Nature/Science) expect low-saturation, professional colors. Never use fully saturated red/green/blue.

```python
# CNS-style disease group colors
DC = {"CTRL": "#6AA84F", "MASL": "#E69F00", "MASH": "#CC6677"}
# Muted versions for supporting figures
DC_MUTED = {"CTRL": "#A8D5A2", "MASL": "#F5D5A0", "MASH": "#E8B4B8"}
# Accent colors
ACCENT = "#4878A8"    # steel blue
RED_ACCENT = "#CC6677"  # muted rose
GRAY = "#A0A0A0"
```

## Design Rules

| Rule | Why | Bad Example | Fix |
|------|-----|-------------|-----|
| **No single-bar charts** | One bar conveys nothing; always need comparison | Single bar "AUC = 0.82" | Show multiple models/thresholds side by side |
| **No placeholder data** | Reviewers will question data provenance | Hardcoded `[0.5, 0.7, 0.9]` | Read from actual result CSV files |
| **No text overlap** | Unreadable, looks unprofessional | Legend on top of stacked bars | Use `bbox_to_anchor` to move legend outside plot |
| **z-index matters** | Important elements hidden behind others | Median line behind scatter points | Set `zorder=10` for text, `zorder=8` for highlights |
| **Labels must be readable** | ENSG IDs are meaningless to readers | `ENSG00000289754` on axis | Map to gene symbols; skip unmapped features |
| **p-values: contrast with bar color** | Same color = invisible | Blue text on blue bar | Use white text inside bar, or black text outside |
| **Error bars always defined** | Reviewers will ask "SD or SEM?" | Unlabeled error bars | State in caption: "Error bars represent SEM" |
| **Spacing between panels** | Crowded panels look amateurish | `hspace=0.3` | Use `hspace=0.65, wspace=0.60` minimum for 2×3 grids |
| **Figure size** | Too small = unreadable | `figsize=(7.2, 7.5)` for 2×3 | Use `figsize=(7.5, 8.5)` or larger |
| **Delta plot baseline** | A bar at zero looks like missing data | Delta plot with CTRL=0 | Show absolute values, or use dot plots |

## Multi-panel Sizing

```python
# 2×3 grid (most common for CNS main figures)
fig = plt.figure(figsize=(7.5, 8.5))
gs = gridspec.GridSpec(2, 3, figure=fig, hspace=0.65, wspace=0.60)

# 1×3 strip (e.g., Fig 1 overview)
fig, axes = plt.subplots(1, 3, figsize=(7.5, 2.5))
```

## Self-Check After Generation

After generating ALL figures, visually inspect each one for:
- [ ] No empty panels (all panels have real data)
- [ ] No text/label overlap
- [ ] No single-bar charts
- [ ] Legend does not overlap with data
- [ ] Axis labels fully visible (not cut off)
- [ ] Colors are muted/professional (no neon)
- [ ] p-values readable against background
- [ ] Error bars present where applicable
- [ ] Panel letters (a, b, c...) in bold, top-left
