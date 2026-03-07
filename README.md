# Biomedical Paper Writing Skill for Claude Code

A [Claude Code skill](https://docs.anthropic.com/en/docs/claude-code/skills) that helps you write publication-ready biomedical and pharmaceutical research papers. It provides expert-level guidance on paper structure, citation verification, reporting guidelines, and journal-specific requirements.

## What It Does

When you ask Claude Code to help write a biomedical paper, this skill activates and provides:

- **IMRAD section guidance** based on Glasman-Deal's 4-component models — concrete frameworks for what goes in each section of a paper (Introduction, Methods, Results, Discussion)
- **PubMed citation verification** — every citation is searched and verified through PubMed E-utilities API and CrossRef, preventing the ~40% error rate of AI-generated references
- **Reporting guideline checklists** — CONSORT (RCTs), STROBE (observational), PRISMA (systematic reviews), ARRIVE (animal studies), STARD, CARE, TRIPOD
- **Journal-specific formatting** — word limits, abstract formats, and submission requirements for Nature, Science, Cell, NEJM, Lancet, JAMA, and more
- **Writing quality principles** — Gopen & Swan's reader expectation framework, tense usage rules, signalling language, and vocabulary lists

## Quick Start

### Install

```bash
# Clone to your Claude Code skills directory
git clone https://github.com/dailycafi/biomed-paper-writing-skill.git \
  ~/.claude/skills/biomed-paper-writing
```

Or manually copy the folder to `~/.claude/skills/biomed-paper-writing`.

### Use

Just talk to Claude Code as you normally would. The skill triggers automatically when you mention anything related to paper writing, manuscripts, journals, or citations. Examples:

```
"Help me draft the Methods section for my RCT on empagliflozin in HFpEF"

"I have Western blot and flow cytometry data showing our compound inhibits NLRP3.
 IC50 ~50nM. Need to write this up for JCI."

"Search PubMed for recent papers on mRNA vaccine stability and format as BibTeX"

"Reviewer 2 says our Introduction doesn't adequately review GLP-1 agonists in NASH"

"帮我把实验结果写成一篇投Nature Medicine的论文"
```

## What's Inside

```
biomed-paper-writing/
├── SKILL.md                              # Main skill file (auto-loaded when triggered)
├── references/
│   ├── writing-guide.md                  # Glasman-Deal models, Gopen & Swan principles,
│   │                                     # tense rules, vocabulary, figure standards
│   ├── citation-workflow.md              # PubMed/CrossRef API code, BibTeX retrieval,
│   │                                     # verification checklist
│   ├── reporting-guidelines.md           # CONSORT, STROBE, PRISMA, ARRIVE, STARD,
│   │                                     # CARE, TRIPOD checklists
│   └── sources.md                        # Original references, journal author guidelines
└── evals/
    └── evals.json                        # Test prompts for skill evaluation
```

## Key Features

### Citation Safety

AI models hallucinate ~40% of academic citations. In biomedicine, a fabricated RCT reference could influence treatment decisions. This skill enforces a strict verification workflow:

1. Search PubMed via E-utilities API
2. Cross-verify DOI through CrossRef
3. Retrieve BibTeX programmatically (not from memory)
4. Mark anything unverifiable as `[CITATION NEEDED]`

### Paper Type Routing

The skill automatically routes to the appropriate reporting guideline:

| Paper Type | Guideline |
|------------|-----------|
| Randomized controlled trial | CONSORT |
| Observational study | STROBE |
| Systematic review / meta-analysis | PRISMA |
| Animal research | ARRIVE |
| Diagnostic accuracy | STARD |
| Case report | CARE |
| Prediction model | TRIPOD |

### Journal Requirements

Built-in formatting specs for high-impact journals:

| Journal | Word Limit | Abstract |
|---------|-----------|----------|
| NEJM | 2500-3000 | 250 words, structured |
| Lancet | 3000-3500 | 300 words, structured |
| Nature | ~3000 + Methods | 150 words, unstructured |
| Cell | ~7000 + STAR Methods | 150 words ("Summary") |
| Science | ~2500 + SOM | 125 words, unstructured |

## Benchmark Results

Tested with 3 evaluation scenarios (Introduction drafting, Methods writing, citation verification), comparing with-skill vs without-skill performance:

| Metric | With Skill | Without Skill | Delta |
|--------|-----------|---------------|-------|
| Pass rate | 95% | 81% | **+14%** |
| Citation safety | 100% | 71% | **+29%** |
| Methods quality | 100% | 100% | 0% |

The biggest differentiator is **citation safety**: with the skill, all citations are verified through PubMed/CrossRef APIs. Without it, Claude generates references from memory — including fabricated ones.

## Attribution and Inspiration

This skill is adapted from the **ML Paper Writing skill** by [Orchestra Research](https://github.com/Orchestra-Research/AI-Research-SKILLs/tree/main/20-ml-paper-writing) (MIT License), which targets AI/ML conferences (NeurIPS, ICML, ICLR, etc.). The biomedical adaptation preserves the core architecture — proactive drafting philosophy, citation verification workflow, progressive disclosure structure — while replacing the content for biomedical journals and clinical research:

- ML conference checklists → biomedical reporting guidelines (CONSORT, STROBE, PRISMA, ARRIVE)
- Semantic Scholar / arXiv verification → PubMed E-utilities / CrossRef verification
- LaTeX conference templates → journal-specific requirements (NEJM, Lancet, Nature, Cell)
- ML writing advice (Karpathy, Lipton, etc.) → Glasman-Deal's *Science Research Writing* (2009) + Gopen & Swan's reader expectation principles

The skill was built and evaluated using the [Skill Creator](https://github.com/anthropics/skills/tree/main/skills/skill-creator) from Anthropic's official skills repository.

## References

- Glasman-Deal, H. (2009). *Science Research Writing for Non-Native Speakers of English*. Imperial College Press.
- Gopen, G. D., & Swan, J. A. (1990). The Science of Scientific Writing. *American Scientist*, 78(6), 550-558.
- Orchestra Research. (2025). [AI Research SKILLs — ML Paper Writing](https://github.com/Orchestra-Research/AI-Research-SKILLs/tree/main/20-ml-paper-writing). MIT License.
- Anthropic. (2025). [Skills — Skill Creator](https://github.com/anthropics/skills/tree/main/skills/skill-creator). Apache 2.0 License.

## License

MIT
