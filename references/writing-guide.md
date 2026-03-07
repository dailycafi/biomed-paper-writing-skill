# Biomedical Paper Writing Philosophy & Best Practices

This reference compiles writing advice for biomedical research papers, synthesizing guidance from Glasman-Deal's *Science Research Writing*, Gopen & Swan's reader expectation principles, and best practices from leading biomedical journals.

---

## Contents

- [The IMRAD Structure](#the-imrad-structure)
- [Glasman-Deal's Section Models](#glasman-deals-section-models)
- [Time Allocation](#time-allocation)
- [Abstract Writing](#abstract-writing)
- [Sentence-Level Clarity](#sentence-level-clarity)
- [Tense Usage in Biomedical Writing](#tense-usage-in-biomedical-writing)
- [Signalling Language](#signalling-language)
- [Word Choice and Precision](#word-choice-and-precision)
- [Figure and Table Design](#figure-and-table-design)
- [Common Mistakes to Avoid](#common-mistakes-to-avoid)

---

## The IMRAD Structure

Biomedical papers follow the IMRAD convention: **Introduction, Methods, Results, and Discussion**. This structure mirrors a research hourglass:

```
    INTRODUCTION (broad → narrow)
         ↓
    METHODS (specific procedures)
         ↓
    RESULTS (specific findings)
         ↓
    DISCUSSION (narrow → broad)
```

The Introduction narrows from general context to specific aims. The Discussion widens from specific findings back to broader implications. This symmetry is fundamental — many elements in the Introduction are revisited in reverse order in the Discussion.

---

## Glasman-Deal's Section Models

### Introduction Model (4 Components)

From *Science Research Writing for Non-Native Speakers of English* (Glasman-Deal, 2009):

| Component | Function | Typical Tense |
|-----------|----------|---------------|
| **1. Establish importance** | Establish significance of research field; provide background facts; define key terminology; present problem area | Present Simple (facts), Present Perfect (recent trends) |
| **2. Literature review** | Previous and/or current research contributions | Past Simple (specific studies), Present Perfect (current relevance) |
| **3. Identify the gap** | Locate gap in research; describe the problem to address; present hypothesis | Present Perfect → signals current relevance |
| **4. Describe present work** | Describe the paper itself; state aims, methods overview, key findings | Present Simple (paper description), Past Simple (aims) |

**Key insight**: Start general, narrow progressively. Don't jump to your specific problem before providing sufficient background for the reader.

**Gap language** (Component 3) is typically signalled by connectors like *However*, *Although*, *Nevertheless*:
- "However, little attention has been paid to..."
- "Although X has been extensively studied, Y remains poorly understood"
- "Despite these advances, the mechanism of... is still unclear"

### Methods/Materials Model (4 Components)

| Component | Function |
|-----------|----------|
| **1. Overview** | General introduction to materials/methods; restate purpose; source of materials; essential background |
| **2. Specific details** | Precise details (quantities, concentrations, durations, conditions); justify choices; indicate care taken |
| **3. Relate to other studies** | Reference established protocols or modifications thereof |
| **4. Problems** | Note where problems occurred (if applicable) |

**Biomedical-specific requirements**:
- Ethical approvals (IRB/ethics committee, informed consent)
- Patient demographics and inclusion/exclusion criteria
- Drug dosages, formulations, routes of administration
- Cell lines: source, passage number, authentication
- Animal models: species, strain, housing conditions, IACUC approval
- Statistical methods and software used
- Clinical trial registration number

### Results Model (4 Components)

| Component | Function |
|-----------|----------|
| **1. Revisit** | Revisit research aim or existing research; expand on methodology; provide general overview of results |
| **2. Specific results** | Invite reader to view figures/tables; present key results in detail; compare with other studies or model predictions |
| **3. Problems** | Note problems with results; acknowledge unexpected findings |
| **4. Implications** | Indicate possible implications of results |

**Biomedical-specific tips**:
- Present results in logical order (not necessarily chronological)
- Separate Results from Discussion unless journal requires combined section
- Report exact p-values (e.g., P = 0.003, not P < 0.05)
- Include confidence intervals where appropriate
- Report effect sizes, not just statistical significance
- Use CONSORT flow diagrams for clinical trial participant flow

### Discussion/Conclusion Model (4 Components)

| Component | Function |
|-----------|----------|
| **1. Revisit** | Revisit previous sections; summarise key results |
| **2. Map** | Show how findings relate to existing research (agreement/disagreement) |
| **3. Achievement** | Highlight contributions; refine implications; clinical significance |
| **4. Limitations & Future** | Acknowledge limitations; suggest future work; note applications |

**Structure tip**: The Discussion mirrors the Introduction in reverse. If your Introduction moved from broad context → specific gap, your Discussion moves from specific findings → broader implications.

**Biomedical-specific tips**:
- Address clinical relevance and translational potential
- Discuss biological mechanisms underlying findings
- Compare with existing treatments or diagnostic approaches
- Address generalizability to different populations
- Note regulatory implications if applicable

### Abstract Model (5 Components)

| Component | Function |
|-----------|----------|
| **1. Background/Aim** | Background, aim, problem, what the paper does |
| **2. Methods** | Methodology/materials overview |
| **3. Results** | Key results, achievements, implications |
| **4. Applications** | Practical applications |
| **5. Limitations** | Limitations and future work (optional) |

**Two types**:
- **Structured Abstract** (most biomedical journals): Explicit subheadings (Background, Methods, Results, Conclusions). Components appear separately and in order.
- **Unstructured Abstract**: Selects 2-3 components, often combining them in single sentences. METHODOLOGY typically precedes RESULTS.

Most biomedical journals (NEJM, JAMA, Lancet, BMJ) require **structured abstracts** with explicit section headings.

---

## Time Allocation

Spend approximately **equal time** on each of:
1. The abstract
2. The introduction
3. The figures and tables
4. Everything else combined

**Why?** Editors and reviewers form judgments from the abstract and introduction. Many submissions are desk-rejected based on these sections alone. In biomedical publishing, the abstract is often the only part freely accessible (before full-text access), making it critical for readership.

---

## Abstract Writing

### Structured Abstract Formula (Biomedical)

Most biomedical journals require structured abstracts with these headings:

```
BACKGROUND: Why this study matters (1-2 sentences)
METHODS: What was done (2-3 sentences)
RESULTS: What was found, with key numbers (2-4 sentences)
CONCLUSIONS: What it means (1-2 sentences)
```

**Word limits** vary by journal:
- NEJM: 250 words (structured: Objective, Design, Results, Conclusions)
- Lancet: 300 words (structured: Background, Methods, Findings, Interpretation, Funding)
- JAMA: 350 words (structured: Importance, Objective, Design, Setting, Participants, etc.)
- BMJ: 400 words (structured)
- Nature: 200 words ("summary paragraph" — context, background, "Here we show", implications)
- Science: 250 words (single paragraph, ideally ~200)
- Nature Medicine: 150 words (unreferenced)
- Cell: 150 words (unstructured, called "Summary")

### What to Avoid in Abstracts

- Generic openings: "Cancer is a major health problem..." (delete — start specific)
- Results not supported by data in the paper
- Abbreviations not defined
- Citations (most journals prohibit them in abstracts)
- Conclusions that overreach the data

---

## Sentence-Level Clarity

### Gopen & Swan's 7 Principles of Reader Expectations

From "The Science of Scientific Writing" (1990):

| Principle | Rule | Biomedical Example |
|-----------|------|--------------------|
| **Subject-verb proximity** | Keep subject and verb close | Bad: "The protein, which was isolated from patient serum and purified using affinity chromatography, binds..." Better: "The protein binds... after isolation from patient serum and purification by affinity chromatography" |
| **Stress position** | Place emphasis at sentence ends | Bad: "Survival improved by 23% with the combination therapy" Better: "With the combination therapy, survival improved by **23%**" |
| **Topic position** | Put context first, new info after | Good: "Given these pharmacokinetic constraints, we designed a sustained-release formulation" |
| **Old before new** | Familiar info → unfamiliar info | Good: "Standard chemotherapy has significant toxicity. To reduce this toxicity, we developed a targeted delivery system" |
| **One unit, one function** | Each paragraph makes one point | Split multi-point paragraphs |
| **Action in verb** | Use verbs, not nominalizations | Bad: "We performed an investigation of..." Better: "We investigated..." |
| **Context before new** | Set stage before presenting data | Explain the assay before reporting its results |

### Micro-Level Tips (from Perez, adapted for biomedical)

- **Minimize pronouns**: Bad: "This shows..." Better: "This finding shows..." / "This result indicates..."
- **Verbs early**: Position the verb near the sentence start
- **Delete filler words**: "actually," "basically," "very," "quite," "essentially"
- **Active voice**: "We measured..." not "Measurements were taken..." (though passive is acceptable in Methods)
- **One idea per sentence**: If struggling to express an idea in one sentence, use two

---

## Tense Usage in Biomedical Writing

Tense choice carries meaning in science writing. Incorrect tense use can misrepresent findings.

### Present Simple
Used for **accepted facts and established knowledge**:
- "Aspirin inhibits cyclooxygenase enzymes"
- "The liver metabolises most oral drugs via first-pass metabolism"
- "Type 2 diabetes is characterised by insulin resistance"

### Present Perfect
Used for **research with current relevance** — signals that findings are still pertinent NOW:
- "Several studies **have shown** that statins reduce cardiovascular events"
- "Little attention **has been paid** to the role of the microbiome in drug metabolism"

### Past Simple
Used for **specific completed studies** — signals particular findings in a particular context:
- "Smith et al. **demonstrated** that the compound inhibited tumour growth in mice"
- "The patients **were randomized** to receive either drug A or placebo"

### Critical Tense Switch: Past Simple → Present Perfect

This switch signals a move from reporting specific past research to identifying a gap with current relevance:

> "Several groups **investigated** the effect of compound X on inflammation (refs). However, the mechanism by which X modulates the immune response **has not been fully elucidated**."

The Present Perfect ("has not been fully elucidated") signals that this gap exists NOW — creating the rationale for your study.

**Warning**: If you write "the mechanism **was not** fully elucidated" (Past Simple), it implies the problem may have been solved since then.

---

## Signalling Language

### Sentence Connection

Every sentence ending creates a dangerous gap for the reader. Close the gap using:

1. **Overlap**: Repeat a key term from the previous sentence
2. **Pro-forms**: "This mechanism...", "These findings...", "Such compounds..."
3. **Semicolons**: For closely related short sentences
4. **Signal connectors**: Words that indicate the relationship between sentences

### Key Connectors for Biomedical Writing

| Function | Connectors |
|----------|------------|
| **Cause** | due to, because, since, on account of, owing to, as a result of |
| **Result** | therefore, consequently, hence, as a result, which is why, thus |
| **Contrast** | however, whereas, but, on the other hand, while, by contrast, in contrast |
| **Unexpectedness** | although, even though, despite, in spite of, nevertheless, nonetheless |
| **Addition** | in addition, moreover, furthermore, also, apart from |
| **Example** | for example, for instance, such as, including |
| **Comparison** | similarly, likewise, in a similar manner, consistent with |

**Caution**:
- Don't start sentences with *so* (too informal)
- *Since* can mean "because" or "from that time" — avoid ambiguity
- *While* can mean "whereas" or "at the same time" — choose context carefully

---

## Word Choice and Precision

### Be Specific

| Vague | Specific |
|-------|----------|
| performance | sensitivity, specificity, AUC |
| improves | increases survival by X months, reduces toxicity by Y% |
| large | 500-patient cohort, 10 mM concentration |
| significant | statistically significant (P = 0.003) vs clinically significant |
| effective | reduces tumour volume by 45%, achieves complete response in 30% of patients |

### Consistent Terminology

Choose one term and stick with it throughout:
- "compound" vs "drug" vs "agent" vs "molecule"
- "patients" vs "subjects" vs "participants"
- "tumour" vs "tumor" (follow journal's convention)
- "efficacy" (controlled setting) vs "effectiveness" (real-world)

### Eliminate Hedging (Unless Genuinely Uncertain)

- Delete unnecessary "may," "might," "could possibly"
- Bad: "The results may potentially suggest that the drug could be effective"
- Good: "The results suggest that the drug is effective"
- But keep hedging when warranted: "This compound may have off-target effects that warrant further investigation"

### Vocabulary for Gap/Problem Description

Commonly used in biomedical Introductions to signal the research gap:

**Adjectives**: unclear, poorly understood, limited, insufficient, controversial, conflicting, inconclusive, under-investigated, unexplored, suboptimal

**Noun phrases**: a gap in our understanding, a lack of evidence, an unmet clinical need, a significant limitation, a major challenge, a critical barrier

**Verb phrases**: remains to be determined, has not been fully elucidated, warrants further investigation, requires clarification, has been largely overlooked

**Full phrases**:
- "Few studies have examined..."
- "The role of X in Y remains poorly understood"
- "There is currently no effective treatment for..."
- "Despite promising preclinical results, clinical translation has been limited"
- "An unmet need exists for..."

### Vocabulary for Describing Present Work

**Verbs**: investigate, examine, evaluate, assess, determine, characterize, elucidate, demonstrate, establish, develop, validate, optimize

**Framing phrases**:
- "In this study, we investigated..."
- "Here, we report..."
- "The aim of this study was to..."
- "We hypothesized that..."
- "To address this gap, we developed..."

---

## Figure and Table Design

### Biomedical Figure Standards

1. **Resolution**: 300 DPI minimum for photographs, 600 DPI for line art
2. **Format**: TIFF or EPS preferred; PDF acceptable; avoid JPEG for data figures
3. **Colour**: Use colourblind-safe palettes (Okabe-Ito recommended)
4. **Size**: Design for single-column (86 mm) or double-column (178 mm) width
5. **Annotations**: Include scale bars in microscopy images; label axes clearly

### Specific Biomedical Figure Types

| Figure Type | Key Requirements |
|-------------|-----------------|
| **Western blots** | Molecular weight markers, loading controls, quantification |
| **Microscopy** | Scale bars, magnification noted, representative images stated |
| **Flow cytometry** | Gating strategy shown, controls included |
| **Survival curves** | Kaplan-Meier with number at risk, log-rank P values |
| **Forest plots** | Effect sizes with CIs, heterogeneity statistics |
| **Dose-response curves** | EC50/IC50 values, Hill coefficients |
| **CONSORT diagrams** | Complete patient flow for clinical trials |

### Table Design

```latex
\usepackage{booktabs}
\begin{tabular}{lcc}
\toprule
Characteristic & Treatment (n=150) & Placebo (n=148) \\
\midrule
Age, years (mean ± SD) & 58.3 ± 12.1 & 57.8 ± 11.9 \\
Female sex, n (\%) & 72 (48) & 69 (47) \\
\textbf{Primary endpoint} & \textbf{23.5\%} & 34.2\% \\
\bottomrule
\end{tabular}
```

**Rules for biomedical tables**:
- Bold the primary outcome
- Include units for all measurements
- Report both absolute numbers and percentages
- Use consistent decimal precision
- Include P values or confidence intervals
- Baseline demographics table (Table 1) is standard for clinical studies

### Tools

```python
# SciencePlots: Publication-ready styles
import matplotlib.pyplot as plt
plt.style.use(['science', 'nature'])  # Nature-style figures

# Or for medical journals
plt.style.use(['science', 'ieee'])
```

---

## Common Mistakes to Avoid

### Structure Mistakes

| Mistake | Solution |
|---------|----------|
| Introduction jumps directly to your problem | Start with broad context, narrow progressively |
| Methods missing ethical approvals | Always include IRB/IACUC information |
| Results mixed with interpretation | Keep Results factual; save interpretation for Discussion |
| Discussion doesn't address limitations | Every journal expects a limitations paragraph |
| No CONSORT/STROBE/PRISMA compliance | Follow appropriate reporting guideline |

### Writing Mistakes

| Mistake | Solution |
|---------|----------|
| Tense inconsistency | Follow the rules: Present Simple for facts, Past Simple for your methods/results |
| "Significant" without clarification | Specify: statistically significant or clinically significant |
| Overclaiming | Match conclusions to evidence; "suggests" not "proves" |
| Paper-by-paper literature review | Organize methodologically: "One approach is X (refs)... Another strategy involves Y (refs)..." |

### Figure Mistakes

| Mistake | Solution |
|---------|----------|
| Missing scale bars | Always include in microscopy images |
| No error bars | Include with clear legend (SD vs SEM vs 95% CI) |
| Unlabelled axes | Include units for all axes |
| Red-green colour scheme | Use colourblind-safe palette |

### Citation Mistakes

| Mistake | Solution |
|---------|----------|
| AI-generated citations | Always verify via PubMed/CrossRef APIs |
| Missing key references | Reviewers may have authored relevant papers — cite generously |
| Outdated references only | Include recent (last 2-3 years) publications |
| Self-citation excess | Keep self-citations proportionate |

---

## Pre-Submission Checklist

### Narrative

- [ ] Can state the main finding in one sentence
- [ ] Introduction follows the 4-component model (importance → literature → gap → present work)
- [ ] Discussion mirrors Introduction structure in reverse
- [ ] Every experiment/analysis supports a specific claim

### Structure

- [ ] Abstract follows journal-required format (structured vs unstructured)
- [ ] Methods include all ethical approvals and registrations
- [ ] Results and Discussion appropriately separated (or combined per journal style)
- [ ] Limitations paragraph included in Discussion
- [ ] Reporting guideline followed (CONSORT/STROBE/PRISMA/ARRIVE etc.)

### Writing

- [ ] Consistent terminology throughout
- [ ] Tense usage follows conventions
- [ ] No generic opening sentences
- [ ] Hedging appropriate to evidence level
- [ ] All figures have self-contained legends

### Technical

- [ ] All citations verified via PubMed/CrossRef
- [ ] Statistical methods fully described
- [ ] P values exact (not just < 0.05)
- [ ] Error bars defined (SD, SEM, or CI)
- [ ] Sample sizes justified
- [ ] Data availability statement included
