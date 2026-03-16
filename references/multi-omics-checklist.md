# Multi-omics Paper Checklist

For spatial multi-omics studies specifically.

## Data Description
- [ ] Sample sizes per modality per disease group (use Table 1)
- [ ] QC criteria and retention rates per modality
- [ ] Batch correction method and quantitative improvement metric
- [ ] Cross-modality spatial alignment method (e.g., STalign + KDTree)
- [ ] Annotation confidence levels (e.g., MSI Level 2-3 for metabolites)

## Analysis
- [ ] Pseudobulk aggregation for DE (avoid spot-level pseudoreplication)
- [ ] Sample-level statistics (not spot-level) for population inference
- [ ] Multiple testing correction stated (BH FDR)
- [ ] Effect sizes reported alongside p-values
- [ ] Cross-modality validation (same finding confirmed by ≥2 modalities)

## External Validation
- [ ] At least one independent cohort for key findings
- [ ] Clear statement of what was validated and what was not
- [ ] Validation metrics with confidence intervals

## Limitations (MUST include all applicable)
- [ ] Cross-sectional design (no causal inference)
- [ ] Sample size limitations per modality
- [ ] Annotation confidence (putative vs confirmed)
- [ ] Missing QC samples (e.g., no pooled QC for MALDI)
- [ ] Gene panel overlap limitations (e.g., MERFISH 317 genes)
- [ ] Non-significant results honestly reported
