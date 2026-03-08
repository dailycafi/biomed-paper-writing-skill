---
name: biomed-paper-writing
description: Write publication-ready biomedical and pharmaceutical research papers for journals like Nature, Science, Cell, NEJM, Lancet, JAMA, Nature Medicine, and specialty journals. Use when drafting papers from research data, structuring IMRAD sections, verifying citations via PubMed, applying reporting guidelines (CONSORT, STROBE, PRISMA, ARRIVE), or preparing submissions. Make sure to use this skill whenever the user mentions writing a paper, drafting a manuscript, biomedical or clinical writing, research articles, IMRAD structure, journal names (Nature, Science, Cell, NEJM, Lancet, JAMA, BMJ, etc.), reporting guidelines (CONSORT, STROBE, PRISMA, ARRIVE, STARD, CARE, TRIPOD), responding to reviewer comments, cover letters, or converting lab results into manuscript form — even if they don't explicitly say "paper writing". Also trigger for drug development papers, grant manuscript sections, systematic reviews, meta-analyses, case reports, and any request involving PubMed citation verification.
version: 1.2.0
metadata:
  author: cafi
  license: MIT
tags: [Academic Writing, Biomedical, Pharmaceutical, IMRAD, PubMed, CONSORT, STROBE, PRISMA, ARRIVE, LaTeX, Citations, Nature, Science, Cell, NEJM, Lancet, JAMA]
---

# Biomedical Paper Writing

Expert-level guidance for writing publication-ready biomedical and pharmaceutical research papers. Combines Glasman-Deal's IMRAD section models, Gopen & Swan's reader expectation principles, PubMed citation verification, reporting guideline checklists, and journal-specific requirements.

## Core Philosophy

**Be proactive. Scientists are busy — deliver concrete drafts they can react to.**

Paper writing is collaborative, but Claude should lead with output, not questions. If the data and contribution are clear, produce a full draft. Reserve questions for genuine blockers (unclear study type, missing data, ethical concerns).

| Confidence Level | Action |
|-----------------|--------|
| **High** (clear data, obvious finding) | Write full draft, deliver, iterate on feedback |
| **Medium** (some ambiguity) | Write draft with flagged uncertainties, continue |
| **Low** (major unknowns) | Ask 1-2 targeted questions, then draft |

**Only block for input when**: target journal is unclear, study type is ambiguous, results seem incomplete, or ethical concerns exist (missing approvals, consent issues).

---

## Citation Safety

AI-generated citations have high error rates — studies report 20-40% fabrication depending on model and domain (Walczak & Cellary, JMIR 2024; Gravel et al., JAMIA 2023). In biomedical contexts, fabricated clinical evidence can have patient safety implications — a hallucinated RCT reference could influence treatment decisions.

**The rule is simple**: never generate BibTeX from memory. Every citation must be verified through PubMed or CrossRef before inclusion.

| Situation | Do This | Not This |
|-----------|---------|----------|
| Adding a citation | Search PubMed → verify PMID → fetch BibTeX | Write BibTeX from memory |
| Uncertain about a paper | Mark as `[CITATION NEEDED]` | Guess the reference |
| Can't find exact paper | Note "placeholder - verify" and tell scientist | Invent similar-sounding paper |

When citations can't be verified, use explicit placeholders and always inform the scientist how many remain unverified.

See [references/citation-workflow.md](references/citation-workflow.md) for PubMed/CrossRef API code and the full verification workflow.

---

## Paper Writing Workflow

### Step 0: Understand the Scientific Questions

Before writing, explore what exists:
- Data files, analysis notebooks, statistical output
- Existing drafts, lab notebooks, preliminary reports
- Figures, tables, supplementary materials
- Ethics approvals, trial registration documents

Then clarify the contribution:
> "Based on my understanding of the data, the main finding appears to be [X]. Is this the framing you want, or should we emphasize different aspects?"

### Step 1: Determine Paper Type and Route

Different paper types need different structures and guidelines. Route accordingly:

| Paper Type | Structure | Reporting Guideline | Reference |
|------------|-----------|-------------------|-----------|
| RCT | IMRAD | CONSORT | [reporting-guidelines.md](references/reporting-guidelines.md) |
| Observational study | IMRAD | STROBE | [reporting-guidelines.md](references/reporting-guidelines.md) |
| Systematic review / meta-analysis | Background, Methods, Results, Discussion | PRISMA | [reporting-guidelines.md](references/reporting-guidelines.md) |
| Animal research | IMRAD | ARRIVE | [reporting-guidelines.md](references/reporting-guidelines.md) |
| Diagnostic accuracy | IMRAD | STARD | [reporting-guidelines.md](references/reporting-guidelines.md) |
| Case report | Timeline-based narrative | CARE | [reporting-guidelines.md](references/reporting-guidelines.md) |
| Prediction model (traditional) | IMRAD | TRIPOD | [reporting-guidelines.md](references/reporting-guidelines.md) |
| Prediction model (AI/ML) | IMRAD | TRIPOD+AI | [reporting-guidelines.md](references/reporting-guidelines.md) |
| Review article | Thematic sections (no Methods/Results) | None (but follow PRISMA if systematic) | — |
| Letter / Correspondence | Brief, 1-2 pages, limited refs | None | — |

### Step 2: Draft the Paper

Write sections in this order (the order scientists typically refine them):

```
Paper Writing Progress:
- [ ] Define the one-sentence finding (confirm with scientist)
- [ ] Title and Running Title
- [ ] Abstract (structured or unstructured per journal)
- [ ] Introduction (4-component model)
- [ ] Methods/Materials (with ethical approvals)
- [ ] Results (with figures/tables)
- [ ] Discussion (mirror of Introduction)
- [ ] Reporting guideline checklist
- [ ] Verify all citations via PubMed
- [ ] Final review and submission prep
```

### Step 3: Verify Citations and Submit

Follow the workflow in [references/citation-workflow.md](references/citation-workflow.md):
1. Search PubMed for each citation
2. Verify PMID exists and cross-check DOI via CrossRef
3. Retrieve BibTeX programmatically
4. Mark unverifiable citations as `[CITATION NEEDED]`

---

## IMRAD Section Guidance

Each section follows Glasman-Deal's **4-component model** — a framework for what to DO in each section. Full details with vocabulary, signalling language, and examples are in [references/writing-guide.md](references/writing-guide.md).

### Introduction

| Component | Function | Tense |
|-----------|----------|-------|
| **1. Establish importance** | Significance of field; background; define terms | Present Simple, Present Perfect |
| **2. Literature review** | Previous research (organized thematically, not paper-by-paper) | Past Simple, Present Perfect |
| **3. Identify the gap** | Gap in knowledge; problem to address | Present Perfect |
| **4. Present work** | Describe this paper; state aims | Present Simple, Past Simple |

Start broad, narrow progressively. Jumping straight to your problem without context loses the reader — they need to understand why the field matters before understanding why the gap matters.

**Gap language** signals the transition to your contribution. The tense switch from Past Simple to Present Perfect is the key signal: "Groups **investigated** X. However, Y **has not been** fully elucidated." The Present Perfect tells the reader this gap exists *now*.

### Methods

Include all applicable elements:
- **Ethics**: IRB/IACUC approval number, informed consent, trial registration
- **Study design**: Type, setting, dates
- **Participants**: Eligibility criteria, demographics, sample size justification
- **Interventions**: Drug doses, formulations, routes (enough for replication)
- **Materials**: Cell lines (source, authentication, passage), reagents, antibodies
- **Outcomes**: Primary and secondary, how measured
- **Statistics**: Tests, software, significance threshold, missing data handling

Reviewers check Methods first to decide if findings are trustworthy. Missing ethical approvals or unclear statistical methods are common reasons for desk rejection.

### Results

- Present in logical order (not necessarily chronological)
- Report exact p-values (P = 0.003, not P < 0.05) — exact values let readers judge significance themselves
- Include confidence intervals and effect sizes — p-values alone don't convey clinical relevance
- Reference each figure/table explicitly in text
- Separate results from interpretation — mixing them obscures what you actually found

### Discussion

| Component | Function |
|-----------|----------|
| **1. Revisit** | Summarise key findings (1-2 paragraphs) |
| **2. Map** | How findings relate to existing research (agree/disagree) |
| **3. Achievement** | Clinical significance, mechanistic insights, translational potential |
| **4. Limitations & Future** | Limitations (always include), future directions |

The Discussion mirrors the Introduction in reverse: specific findings → broader implications. This symmetry is deliberate — elements introduced in the Introduction are revisited in reverse order.

Limitations matter because reviewers are instructed not to penalize honesty. Omitting limitations signals either naivety or evasion, both of which undermine credibility.

### Abstract

Most biomedical journals require **structured abstracts** (BACKGROUND, METHODS, RESULTS, CONCLUSIONS). Word limits: NEJM 250, Lancet 300, JAMA 350, Nature Medicine 150 (unstructured), Cell 150 (unstructured "Summary").

Avoid generic openings — editors and reviewers read hundreds of abstracts that start with "X is a leading cause of..." Start with what's specific to your study.

---

## Writing Quality

### Gopen & Swan's Principles (abbreviated)

| Principle | Why It Matters |
|-----------|---------------|
| **Subject-verb proximity** | Long interruptions between subject and verb force readers to hold context in working memory |
| **Stress position** | Readers naturally emphasize what comes last in a sentence — put your key point there |
| **Old before new** | Starting with familiar info anchors the reader before introducing new concepts |
| **Action in verb** | "We analyzed" beats "We performed an analysis" — nominalizations hide the action |

### Tense Usage

| Tense | Signals | Example |
|-------|---------|---------|
| **Present Simple** | Accepted fact | "Aspirin inhibits cyclooxygenase" |
| **Present Perfect** | Current relevance, gap still open | "Several studies **have shown**..." |
| **Past Simple** | Specific completed study | "Smith et al. **demonstrated**..." |

The Past Simple → Present Perfect switch is how you signal a research gap to the reader. Getting this wrong can imply a gap has already been filled.

### Word Choice

- **Be specific**: "sensitivity" not "performance"; "reduces mortality by 15%" not "improves outcomes"
- **Eliminate hedging** (unless genuinely uncertain): "suggests" not "may potentially suggest"
- **Consistent terminology**: pick one term per concept ("compound" vs "drug" vs "agent" — choose one)
- **"Significant"**: always specify — statistically (with P value) or clinically (with relevance explained)

Full vocabulary lists and connector language: [references/writing-guide.md](references/writing-guide.md)

---

## Journal Requirements

### High-Impact General Medical

| Journal | Word Limit | Abstract | Key Requirement |
|---------|-----------|----------|-----------------|
| **NEJM** | ~2700 | 250 words, structured | ICMJE disclosure, data sharing |
| **Lancet** | 3000 (RCT up to 4500) | 300 words, structured (Background/Methods/Findings/Interpretation/Funding) | Research in Context panel |
| **JAMA** | 3000 | 350 words, structured | ICMJE, 3 Key Points required |
| **BMJ** | ~4400 (aim for 2000) | 400 words, structured | ICMJE, patient involvement |

### High-Impact Life Science

| Journal | Word Limit | Abstract | Key Requirement |
|---------|-----------|----------|-----------------|
| **Nature** | 2500 (6pp) / 4300 (8pp) + Methods | 200 words, "summary paragraph" (structured: context → background → "Here we show" → implications) | Online Methods (≤3000 words), Reporting Summary, ≤50 refs |
| **Science** | ~3000 + SOM | 250 words (ideally ~200), single paragraph | Supplementary Online Material, one-sentence summary (≤135 chars) |
| **Cell** | ~7000 + STAR Methods | 150 words ("Summary") | STAR Methods, Key Resources Table, Graphical Abstract (1200×1200px) |
| **Nature Medicine** | 4000 + Methods | 150 words, unreferenced | Reporting Summary, data availability, ≤60 refs |

### Universal Requirements

- **ICMJE compliance**: Authorship criteria, conflict of interest disclosure
- **CRediT**: Author contribution roles (14 standardized roles) — required by Nature, Cell, Lancet, JAMA, BMJ, PLOS. See [reporting-guidelines.md](references/reporting-guidelines.md)
- **Ethics**: IRB/IACUC approval, informed consent, trial registration
- **SAGER guidelines**: Sex and gender reporting — distinguish sex (biological, male/female) from gender (social, men/women). Many journals now require compliance. See [reporting-guidelines.md](references/reporting-guidelines.md)
- **Data availability**: Statement on data sharing (increasingly mandatory)
- **References**: Vancouver style (numbered) for most medical journals; author-year for some life science

---

## Figures and Tables

- **Resolution**: 300 DPI (photos), 600 DPI (line art)
- **Colour**: Colourblind-safe palettes (Okabe-Ito) — ~8% of male readers are colourblind
- **Scale bars**: Required for all microscopy images
- **Legends**: Self-contained — reader should understand without reading main text
- **Table 1**: Baseline demographics (standard for clinical studies) with units, n (%), mean ± SD
- **P values**: Report exact values and define error bars (SD vs SEM vs 95% CI)

Common figure types and their requirements: [references/writing-guide.md](references/writing-guide.md)

---

## Common Pitfalls

| Pitfall | Why It's a Problem | Fix |
|---------|-------------------|-----|
| Introduction jumps to problem | Reader lacks context to understand why gap matters | Follow 4-component model: importance → literature → gap → present work |
| Methods missing ethics | Automatic desk rejection at most journals | Always state IRB/IACUC approval number and consent process |
| Results mixed with interpretation | Obscures actual findings, makes replication harder | Keep Results factual; save interpretation for Discussion |
| No limitations paragraph | Signals naivety or evasion to reviewers | Be honest — reviewers respect transparency |
| "Significant" without qualifier | Ambiguous — could mean statistically or clinically | Always specify: "statistically significant (P = 0.003)" or "clinically significant (NNT = 12)" |
| Overclaiming | Reviewers will downgrade if conclusions exceed evidence | "suggests" not "proves"; observational data shows "association" not "causation" |

---

## Reference Files

| Document | When to Read |
|----------|-------------|
| [writing-guide.md](references/writing-guide.md) | Drafting any section — contains Glasman-Deal models, Gopen & Swan principles, tense rules, vocabulary lists, figure standards |
| [citation-workflow.md](references/citation-workflow.md) | Adding or verifying citations — contains PubMed/CrossRef API code, BibTeX formats, verification checklist |
| [reporting-guidelines.md](references/reporting-guidelines.md) | Any study requiring reporting compliance — contains CONSORT, STROBE, PRISMA, ARRIVE, STARD, CARE, TRIPOD/TRIPOD+AI checklists, plus CRediT author roles and SAGER sex/gender guidelines |
| [sources.md](references/sources.md) | Looking up original sources — complete bibliography and journal author guideline links |
