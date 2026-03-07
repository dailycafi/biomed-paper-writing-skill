# Reporting Guidelines for Biomedical Research

This reference documents mandatory reporting guidelines for different study types. Using the correct guideline is essential — many journals require adherence as a condition of submission.

---

## Quick Reference: Which Guideline?

| Study Type | Guideline | Checklist Items | Required By |
|------------|-----------|-----------------|-------------|
| Randomized controlled trial | **CONSORT** | 25 items | Most journals |
| Observational study (cohort, case-control, cross-sectional) | **STROBE** | 22 items | Most journals |
| Systematic review / Meta-analysis | **PRISMA** | 27 items | Most journals |
| Diagnostic accuracy study | **STARD** | 30 items | Most journals |
| Animal research | **ARRIVE** | 21 items | Nature, PLoS, BMJ |
| Case reports | **CARE** | 13 items | Many journals |
| Qualitative research | **SRQR** / **COREQ** | 21/32 items | Some journals |
| Economic evaluation | **CHEERS** | 28 items | Health economics journals |
| Prediction model study | **TRIPOD** | 22 items | Most clinical journals |
| Prediction model with AI/ML | **TRIPOD+AI** | 22 + AI extensions | Journals publishing AI studies |
| Quality improvement | **SQUIRE** | 18 items | QI journals |
| N-of-1 trials | **CENT** | 26 items | Some journals |
| Network meta-analysis | **PRISMA-NMA** | Extended | Most journals |

**Full list**: https://www.equator-network.org/reporting-guidelines/

---

## CONSORT (Randomized Controlled Trials)

### Key Requirements

1. **Title**: Identify as randomised trial
2. **Abstract**: Structured with trial design, methods, results, conclusions
3. **Introduction**: Background, objectives, specific hypotheses
4. **Methods**:
   - Trial design (parallel, crossover, factorial)
   - Participants: eligibility criteria, settings, locations
   - Interventions: precise details for each group
   - Outcomes: primary and secondary, pre-specified
   - Sample size: how determined
   - Randomisation: sequence generation, allocation concealment, implementation
   - Blinding: who was blinded, how
   - Statistical methods: primary analysis, subgroup analyses
5. **Results**:
   - Participant flow (CONSORT diagram REQUIRED)
   - Recruitment dates and follow-up
   - Baseline data (demographics table)
   - Numbers analysed (ITT vs per-protocol)
   - Outcomes with effect sizes and confidence intervals
   - Harms/adverse events
6. **Discussion**: Limitations, generalisability, interpretation
7. **Other**: Registration number, protocol access, funding

### CONSORT Flow Diagram Template

```
Assessed for eligibility (n=...)
        |
        ├── Excluded (n=...)
        |   ├── Not meeting criteria (n=...)
        |   ├── Declined to participate (n=...)
        |   └── Other reasons (n=...)
        |
    Randomized (n=...)
        |
   ┌────┴────┐
   |         |
Allocated to     Allocated to
intervention     control
(n=...)          (n=...)
   |              |
Lost to          Lost to
follow-up        follow-up
(n=...)          (n=...)
   |              |
Analysed         Analysed
(n=...)          (n=...)
```

### Clinical Trial Registration

**Mandatory** for all interventional trials before enrollment of first participant:
- ClinicalTrials.gov (US)
- ISRCTN Registry (UK/international)
- EU Clinical Trials Register
- WHO ICTRP (aggregates all registries)

---

## STROBE (Observational Studies)

### Key Requirements by Study Design

| Item | Cohort | Case-Control | Cross-Sectional |
|------|--------|-------------|-----------------|
| Study design stated | Yes | Yes | Yes |
| Setting described | Yes | Yes | Yes |
| Participants defined | Eligibility, selection, follow-up | Case/control definitions, sources | Selection criteria, sources |
| Variables defined | Exposures, outcomes, confounders | Exposures, outcomes | All measured variables |
| Data sources | How measured | How measured | How measured |
| Bias addressed | Selection, information, confounding | Selection, recall, confounding | Selection, information |
| Sample size | Justified | Justified | Justified |
| Statistical methods | Confounding handling, missing data | Matching, confounders | Missing data handling |
| Results | Numbers at each stage, follow-up time | Numbers in each group | Response rate |
| Main results | Crude and adjusted estimates with CIs | Odds ratios with CIs | Prevalences/means with CIs |

---

## PRISMA (Systematic Reviews & Meta-Analyses)

### Key Requirements

1. **Registration**: Register protocol in PROSPERO before conducting review
2. **Search strategy**: Full electronic search for at least one database (reproducible)
3. **Study selection**: Inclusion/exclusion criteria, PRISMA flow diagram
4. **Data extraction**: Process described, items extracted
5. **Risk of bias**: Tool used (e.g., Cochrane RoB 2, ROBINS-I, Newcastle-Ottawa)
6. **Synthesis**: Methods for combining data, handling heterogeneity
7. **Results**: PRISMA flow diagram, study characteristics, risk of bias assessment, forest plots
8. **Certainty**: GRADE assessment of evidence quality

### PRISMA Flow Diagram

```
Records identified through
database searching (n=...)
        +
Records from other sources (n=...)
        |
    Records after duplicates
    removed (n=...)
        |
    Records screened (n=...)
        ├── Records excluded (n=...)
        |
    Full-text articles
    assessed (n=...)
        ├── Excluded with reasons (n=...)
        |
    Studies included in
    qualitative synthesis (n=...)
        |
    Studies included in
    meta-analysis (n=...)
```

---

## ARRIVE (Animal Research)

### Essential 10 Items

1. **Study design**: Type, experimental unit, randomisation, blinding
2. **Sample size**: Justification (power analysis), number per group
3. **Inclusion/exclusion**: Pre-established criteria for data
4. **Randomisation**: Method used to allocate to groups
5. **Blinding**: Who was blinded (handler, assessor, analyst)
6. **Outcome measures**: Primary and secondary, pre-specified
7. **Statistical methods**: Tests used, unit of analysis, handling of missing data
8. **Experimental animals**: Species, strain, sex, age/weight, source
9. **Experimental procedures**: Detailed for each group (doses, duration, route)
10. **Results**: For each outcome, with measure of precision

### Recommended Items

- Housing and husbandry conditions
- Ethics statement (IACUC approval)
- Adverse events
- Baseline data
- Protocol registration

---

## STARD (Diagnostic Accuracy)

### Key Requirements

1. **Participants**: Eligibility, recruitment, sampling method
2. **Test methods**: Index test and reference standard described in detail
3. **Analysis**: How indeterminate results handled, missing data
4. **Results**: Flow diagram, cross-tabulation (2×2), sensitivity, specificity, predictive values, likelihood ratios with CIs
5. **STARD flow diagram**: Shows patient flow through study

---

## CARE (Case Reports)

### Key Requirements

1. **Title**: "Case report" in title
2. **Patient information**: Demographics, symptoms, history
3. **Clinical findings**: Physical examination, relevant tests
4. **Timeline**: Chronological summary
5. **Diagnostic assessment**: Methods, challenges
6. **Therapeutic intervention**: Type, dosage, duration
7. **Follow-up and outcomes**: Clinician and patient-assessed
8. **Discussion**: Strengths, limitations, relevant literature
9. **Patient perspective**: When available
10. **Informed consent**: Documented

---

## TRIPOD+AI (Prediction Models Using AI/ML)

TRIPOD+AI (2024) extends the original TRIPOD 2015 checklist for prediction models that use machine learning, deep learning, or other AI methods. If the prediction model involves any AI/ML component, use TRIPOD+AI instead of TRIPOD alone.

### Key Additional Requirements Beyond TRIPOD

- **Title**: Identify as AI/ML-based prediction model
- **Data sources**: Describe data provenance, collection context, and potential biases
- **Data preprocessing**: Feature engineering, handling of missing data, normalization
- **Model development**: Architecture, hyperparameter tuning, training procedure
- **Model performance**: Discrimination (AUROC), calibration, decision curve analysis
- **Fairness**: Performance across demographic subgroups (age, sex, ethnicity)
- **Explainability**: Methods used to interpret model predictions (SHAP, LIME, attention maps)
- **Reproducibility**: Code availability, software versions, random seeds
- **Deployment considerations**: Intended clinical context, human oversight requirements

### When to Use TRIPOD vs TRIPOD+AI

| Model Type | Guideline |
|------------|-----------|
| Logistic regression, Cox regression | TRIPOD |
| Random forest, XGBoost, neural network | TRIPOD+AI |
| Deep learning (CNN, transformer) | TRIPOD+AI |
| Traditional score + ML validation | TRIPOD+AI |

---

## SAGER Guidelines (Sex and Gender Reporting)

The SAGER (Sex And Gender Equity in Research) guidelines ensure appropriate reporting of sex and gender in research. Many journals now require compliance.

### Key Requirements

1. **Title/Abstract**: State whether sex/gender was considered
2. **Introduction**: Justify why sex/gender is relevant (or why not analyzed)
3. **Methods**:
   - Report how sex and/or gender were determined (self-report, genetic, hormonal)
   - Distinguish between sex (biological) and gender (social construct)
   - Include both sexes in study design unless single-sex study is justified
4. **Results**: Report data disaggregated by sex/gender where possible
5. **Discussion**: Address implications of sex/gender findings or lack thereof

### Journal-Specific Requirements

| Journal | Sex/Gender Policy |
|---------|-------------------|
| **JAMA** | Requires sex/gender reporting; specific guidelines for race/ethnicity terminology |
| **Lancet** | SAGER compliance expected; inclusive language guidelines |
| **Nature journals** | Reporting Summary includes sex/gender questions |
| **BMJ** | SAGER endorsed; sex-disaggregated data encouraged |
| **Cell Press** | Inclusion and diversity statement required |

### Terminology

- **Sex**: Biological attributes (chromosomes, hormones, anatomy) — use "male/female"
- **Gender**: Social/cultural roles — use "men/women/non-binary"
- Do NOT use "gender" when referring to biological sex of animals or cells

---

## CRediT (Contributor Roles Taxonomy)

CRediT is now required or recommended by most high-impact biomedical journals for declaring author contributions. It standardizes 14 contributor roles.

### The 14 CRediT Roles

| Role | Definition |
|------|-----------|
| **Conceptualization** | Ideas; formulation of research goals and aims |
| **Data curation** | Annotation, scrubbing, maintenance of research data |
| **Formal analysis** | Statistical, mathematical, computational analysis |
| **Funding acquisition** | Obtaining financial support |
| **Investigation** | Conducting research and experiments |
| **Methodology** | Development or design of methodology |
| **Project administration** | Management and coordination |
| **Resources** | Provision of study materials, reagents, patients, samples |
| **Software** | Programming, software development |
| **Supervision** | Oversight and leadership |
| **Validation** | Verification and reproducibility |
| **Visualization** | Preparation of figures and tables |
| **Writing – original draft** | Initial writing |
| **Writing – review & editing** | Critical review, commentary, revision |

### Format Example

```
Author Contributions: A.B.C. — Conceptualization, Methodology, Writing – original draft.
D.E.F. — Investigation, Formal analysis, Visualization. G.H.I. — Resources, Supervision,
Writing – review & editing, Funding acquisition.
```

### Journal Requirements

| Journal | CRediT Status |
|---------|--------------|
| **Nature / Nature Medicine** | Required |
| **Cell / Cell Press** | Required |
| **Lancet** | Required |
| **JAMA** | Required |
| **NEJM** | Author contribution statement required (not strictly CRediT format) |
| **BMJ** | Required |
| **Science** | Author contribution statement required |
| **PLOS journals** | Required |

---

## Journal-Specific Requirements

### Nature / Nature Medicine

- **Reporting Summary**: Mandatory standardised form
- **Life Sciences Reporting Summary**: Statistics, reagents, data availability
- **ARRIVE compliance** for animal studies
- **Data availability statement** required
- **Code availability statement** if applicable

### NEJM

- CONSORT for RCTs (mandatory)
- ICMJE disclosure forms
- Data sharing statement
- Trial registration verification
- Statistical review by journal statistician

### Lancet

- CONSORT/STROBE/PRISMA as applicable
- Research in Context panel (structured summary)
- Role of funding source declaration
- Data sharing commitment

### Cell / Cell Press

- STAR Methods section (Structured, Transparent, Accessible Reporting)
- Key Resources Table (antibodies, chemicals, organisms, software)
- Lead Contact and Materials Availability
- Method Details with full reproducibility

---

## Pre-Submission Reporting Checklist

- [ ] Identified correct reporting guideline for study type
- [ ] Downloaded and completed official checklist
- [ ] Indicated page numbers for each checklist item
- [ ] CONSORT/PRISMA flow diagram included (if applicable)
- [ ] Trial/protocol registered (if applicable)
- [ ] Ethics approval number stated
- [ ] Informed consent documented
- [ ] Data availability statement included
- [ ] Statistical analysis plan follows guideline
- [ ] Adverse events/harms reported (if applicable)

---

## Resources

- **EQUATOR Network**: https://www.equator-network.org/ (central resource for all guidelines)
- **CONSORT**: http://www.consort-statement.org/
- **STROBE**: https://www.strobe-statement.org/
- **PRISMA**: http://www.prisma-statement.org/
- **ARRIVE**: https://arriveguidelines.org/
- **STARD**: https://www.equator-network.org/reporting-guidelines/stard/
- **CARE**: https://www.care-statement.org/
- **TRIPOD+AI**: https://www.bmj.com/content/385/bmj-2023-078378
- **CRediT**: https://credit.niso.org/
- **SAGER**: https://ease.org.uk/communities/gender-policy-committee/the-sager-guidelines/
- **PROSPERO** (SR registration): https://www.crd.york.ac.uk/prospero/
- **ClinicalTrials.gov**: https://clinicaltrials.gov/
