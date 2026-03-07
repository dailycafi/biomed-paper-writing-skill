# Source Bibliography

All authoritative sources used to build this skill, organized by topic.

---

## Writing Philosophy & Guides

### Primary Sources

| Source | Author | Key Contribution |
|--------|--------|------------------|
| **Science Research Writing for Non-Native Speakers of English** | Hilary Glasman-Deal (Imperial College) | IMRAD section models (4-component framework), tense usage, signalling language, vocabulary lists |
| **The Science of Scientific Writing** | Gopen & Swan (1990) | 7 principles of reader expectations (topic/stress positions, old-before-new) |
| **Heuristics for Scientific Writing** | Zachary Lipton (CMU) | Word choice, hedging elimination, vocabulary signalling |
| **Easy Paper Writing Tips** | Ethan Perez (Anthropic) | Micro-level clarity: pronoun management, verb placement, filler word removal |
| **Advice for Authors** | Jacob Steinhardt (UC Berkeley) | Precision over brevity, consistent terminology |

### Biomedical-Specific Writing Guides

| Source | URL | Key Contribution |
|--------|-----|------------------|
| **How to Write a Medical Research Paper** | Byrne DW. Published guides | Structure, statistical reporting |
| **ICMJE Recommendations** | [ICMJE](http://www.icmje.org/recommendations/) | Authorship criteria, conflicts of interest, ethical obligations |
| **Writing for Impact** | Various editorial board guides | Journal-specific expectations |

---

## Reporting Guidelines

| Guideline | URL | Study Type |
|-----------|-----|------------|
| **CONSORT** | [consort-statement.org](http://www.consort-statement.org/) | Randomized controlled trials |
| **STROBE** | [strobe-statement.org](https://www.strobe-statement.org/) | Observational studies |
| **PRISMA** | [prisma-statement.org](http://www.prisma-statement.org/) | Systematic reviews & meta-analyses |
| **ARRIVE** | [arriveguidelines.org](https://arriveguidelines.org/) | Animal research |
| **STARD** | [EQUATOR](https://www.equator-network.org/reporting-guidelines/stard/) | Diagnostic accuracy |
| **CARE** | [care-statement.org](https://www.care-statement.org/) | Case reports |
| **TRIPOD** | [EQUATOR](https://www.equator-network.org/reporting-guidelines/tripod-statement/) | Prediction models |
| **TRIPOD+AI** | [BMJ 2024](https://www.bmj.com/content/385/bmj-2023-078378) | AI/ML prediction models |
| **CRediT** | [credit.niso.org](https://credit.niso.org/) | Author contribution roles (14 roles) |
| **SAGER** | [EASE](https://ease.org.uk/communities/gender-policy-committee/the-sager-guidelines/) | Sex and gender equity in research |
| **CHEERS** | [EQUATOR](https://www.equator-network.org/reporting-guidelines/cheers/) | Economic evaluations |
| **EQUATOR Network** | [equator-network.org](https://www.equator-network.org/) | Central resource for all guidelines |

---

## Journal Author Guidelines

### High-Impact General Medical Journals

| Journal | Author Guidelines | IF (2024) |
|---------|------------------|-----------|
| **NEJM** | [nejm.org/author-center](https://www.nejm.org/author-center/new-manuscripts) | ~176 |
| **Lancet** | [thelancet.com/information-for-authors](https://www.thelancet.com/pb/assets/raw/Lancet/authors/tl-info-for-authors.pdf) | ~169 |
| **JAMA** | [jamanetwork.com/journals/jama/pages/instructions-for-authors](https://jamanetwork.com/journals/jama/pages/instructions-for-authors) | ~120 |
| **BMJ** | [bmj.com/about-bmj/resources-authors](https://www.bmj.com/about-bmj/resources-authors) | ~105 |

### High-Impact Life Science Journals

| Journal | Author Guidelines | IF (2024) |
|---------|------------------|-----------|
| **Nature** | [nature.com/nature/for-authors](https://www.nature.com/nature/for-authors) | ~64 |
| **Science** | [science.org/content/page/instructions-preparing-initial-manuscript](https://www.science.org/content/page/instructions-preparing-initial-manuscript) | ~56 |
| **Cell** | [cell.com/cell/authors](https://www.cell.com/cell/authors) | ~64 |
| **Nature Medicine** | [nature.com/nm/for-authors](https://www.nature.com/nm/for-authors) | ~82 |
| **Nature Biotechnology** | [nature.com/nbt/for-authors](https://www.nature.com/nbt/for-authors) | ~46 |

### Speciality Journals

| Journal | Focus | Author Guidelines |
|---------|-------|------------------|
| **J Clinical Investigation** | Translational | [jci.org](https://www.jci.org/kiosk/publish) |
| **J Med Chemistry** | Drug design | [ACS](https://pubs.acs.org/page/jmcmar/submission/authors.html) |
| **Cancer Cell** | Oncology | [Cell Press](https://www.cell.com/cancer-cell/authors) |
| **Immunity** | Immunology | [Cell Press](https://www.cell.com/immunity/authors) |
| **Neuron** | Neuroscience | [Cell Press](https://www.cell.com/neuron/authors) |
| **Blood** | Hematology | [bloodjournal.org](https://ashpublications.org/blood/pages/author-guide) |
| **Circulation** | Cardiology | [AHA](https://www.ahajournals.org/circ/author-instructions) |

---

## Citation APIs & Tools

### APIs

| API | Documentation | Best For |
|-----|---------------|----------|
| **PubMed E-utilities** | [NCBI](https://www.ncbi.nlm.nih.gov/books/NBK25501/) | Biomedical paper search |
| **CrossRef** | [Docs](https://www.crossref.org/documentation/retrieve-metadata/rest-api/) | DOI lookup, BibTeX |
| **Europe PMC** | [Docs](https://europepmc.org/RestfulWebService) | Open access biomedical |
| **Semantic Scholar** | [Docs](https://api.semanticscholar.org/api-docs/) | Cross-disciplinary, citation graphs |
| **ClinicalTrials.gov** | [API](https://clinicaltrials.gov/data-api/about-api) | Trial registration data |
| **OpenAlex** | [Docs](https://docs.openalex.org/) | Open metadata |

### Python Libraries

| Library | Install | Purpose |
|---------|---------|---------|
| `biopython` | `pip install biopython` | PubMed/NCBI Entrez access |
| `habanero` | `pip install habanero` | CrossRef client |
| `pubmed-parser` | `pip install pubmed-parser` | PubMed XML parsing |
| `semanticscholar` | `pip install semanticscholar` | Semantic Scholar wrapper |

### Reference Managers

| Tool | Best For |
|------|----------|
| **Zotero** | Free, open source, browser extension |
| **Mendeley** | Elsevier integration |
| **EndNote** | Institutional subscriptions |
| **Paperpile** | Google Docs integration |

---

## Visualization

### Figure Creation

| Tool | URL | Purpose |
|------|-----|---------|
| **SciencePlots** | [GitHub](https://github.com/garrettj403/SciencePlots) | Publication-ready matplotlib (Nature/Science styles) |
| **GraphPad Prism** | [graphpad.com](https://www.graphpad.com/) | Statistical graphics standard in biomedical |
| **BioRender** | [biorender.com](https://www.biorender.com/) | Biological diagrams and schematics |
| **Okabe-Ito Palette** | [Reference](https://jfly.uni-koeln.de/color/) | Colourblind-safe colours |

### Statistical Software

| Tool | Purpose |
|------|---------|
| **R** | Statistical analysis, ggplot2 for publication figures |
| **Python (scipy/statsmodels)** | Statistical analysis |
| **GraphPad Prism** | Standard in many biomedical labs |
| **SAS** | Clinical trials, regulatory submissions |
| **SPSS** | Clinical and epidemiological research |

---

## Quick Reference by Topic

### For IMRAD Structure & Section Models
→ Start with: Glasman-Deal, writing-guide.md

### For Sentence-Level Clarity
→ Start with: Gopen & Swan, Ethan Perez, Zachary Lipton

### For Reporting Guidelines
→ Start with: EQUATOR Network, reporting-guidelines.md

### For Citation Management
→ Start with: PubMed E-utilities, citation-workflow.md

### For Journal-Specific Requirements
→ Start with: ICMJE Recommendations, journal author guidelines
