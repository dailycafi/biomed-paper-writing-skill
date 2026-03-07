# Citation Management for Biomedical Papers

This reference provides a complete workflow for managing citations in biomedical research, using PubMed, CrossRef, and other biomedical databases.

---

## Contents

- [Why Citation Verification Matters](#why-citation-verification-matters)
- [Biomedical Citation APIs](#biomedical-citation-apis)
- [Verified Citation Workflow](#verified-citation-workflow)
- [Python Implementation](#python-implementation)
- [BibTeX and Citation Formats](#bibtex-and-citation-formats)
- [Reference Management](#reference-management)
- [Troubleshooting](#troubleshooting)

---

## Why Citation Verification Matters

### The Hallucination Problem

AI-generated citations have a **20-40% error rate** depending on model and domain (Walczak & Cellary, JMIR 2024; Gravel et al., JAMIA 2023). Common errors in biomedical contexts:
- Fabricated clinical trial results attributed to real authors
- Wrong journal names or publication years
- Non-existent papers with plausible PubMed-style metadata
- Incorrect DOIs or PMIDs
- Mixing up authors with similar names (common in large research groups)

### Consequences in Biomedical Publishing

- Desk rejection by editors
- Retraction if published with fabricated references
- Potential ethical violations if citing non-existent clinical evidence
- Loss of credibility with peer reviewers

### Solution

**Never generate citations from memory — always verify programmatically via PubMed, CrossRef, or DOI.**

---

## Biomedical Citation APIs

### Primary APIs

| API | Coverage | Rate Limits | Best For |
|-----|----------|-------------|----------|
| **PubMed/NCBI E-utilities** | 36M+ biomedical articles | 3 RPS (with API key: 10 RPS) | Biomedical literature, MeSH search |
| **CrossRef** | 140M+ DOIs | Polite pool with mailto | DOI lookup, BibTeX retrieval |
| **Semantic Scholar** | 214M papers | 1 RPS (free key) | Cross-disciplinary search, citation graphs |
| **Europe PMC** | 42M+ articles | 25 RPS | Open access biomedical, preprints |
| **OpenAlex** | 240M+ works | 100K/day, 10 RPS | Open alternative, bulk access |

### API Selection Guide

```
Need biomedical paper search?    → PubMed E-utilities
Have DOI, need BibTeX?           → CrossRef content negotiation
Have PMID, need metadata?        → PubMed E-fetch
Looking for preprint?            → bioRxiv/medRxiv or Europe PMC
Need clinical trial reference?   → ClinicalTrials.gov API
Need drug information?           → PubChem or DrugBank
```

### PubMed API (NCBI E-utilities)

Base URL: `https://eutils.ncbi.nlm.nih.gov/entrez/eutils/`

Key endpoints:
- `esearch.fcgi` — Search PubMed
- `efetch.fcgi` — Fetch full records
- `elink.fcgi` — Find related articles

**Get a free API key**: https://www.ncbi.nlm.nih.gov/account/settings/ (increases rate limit to 10 RPS)

---

## Verified Citation Workflow

### 6-Step Process

```
1. SEARCH → Query PubMed with specific keywords or author names
     ↓
2. VERIFY → Confirm paper exists (PMID + DOI cross-check)
     ↓
3. RETRIEVE → Get citation data via PMID or DOI
     ↓
4. VALIDATE → Confirm the claim you're citing actually appears in the paper
     ↓
5. FORMAT → Generate BibTeX/RIS in journal-required format
     ↓
6. ADD → Add verified entry to bibliography
```

### Step 1: Search PubMed

```python
import requests
import xml.etree.ElementTree as ET

def search_pubmed(query: str, max_results: int = 10, api_key: str = None) -> list:
    """Search PubMed and return PMIDs."""
    params = {
        "db": "pubmed",
        "term": query,
        "retmax": max_results,
        "retmode": "json",
        "sort": "relevance"
    }
    if api_key:
        params["api_key"] = api_key

    resp = requests.get(
        "https://eutils.ncbi.nlm.nih.gov/entrez/eutils/esearch.fcgi",
        params=params,
        timeout=10
    )
    resp.raise_for_status()
    data = resp.json()
    return data.get("esearchresult", {}).get("idlist", [])

# Example
pmids = search_pubmed("CRISPR-Cas9 gene therapy sickle cell disease")
print(f"Found PMIDs: {pmids}")
```

### Step 2: Fetch Paper Details

```python
def fetch_pubmed_details(pmids: list, api_key: str = None) -> list:
    """Fetch detailed metadata for PubMed IDs."""
    params = {
        "db": "pubmed",
        "id": ",".join(pmids),
        "retmode": "xml",
        "rettype": "abstract"
    }
    if api_key:
        params["api_key"] = api_key

    resp = requests.get(
        "https://eutils.ncbi.nlm.nih.gov/entrez/eutils/efetch.fcgi",
        params=params,
        timeout=15
    )
    resp.raise_for_status()

    root = ET.fromstring(resp.text)
    papers = []

    for article in root.findall(".//PubmedArticle"):
        medline = article.find(".//MedlineCitation")
        art = medline.find("Article")

        title = art.findtext("ArticleTitle", "")
        abstract = art.findtext(".//AbstractText", "")
        journal = art.findtext(".//Journal/Title", "")
        year = medline.findtext(".//PubDate/Year", "")
        pmid = medline.findtext("PMID", "")

        # Get DOI
        doi = ""
        for eid in article.findall(".//ArticleId"):
            if eid.get("IdType") == "doi":
                doi = eid.text

        # Get authors
        authors = []
        for author in art.findall(".//Author"):
            last = author.findtext("LastName", "")
            first = author.findtext("ForeName", "")
            if last:
                authors.append(f"{last}, {first}")

        papers.append({
            "pmid": pmid,
            "title": title,
            "authors": authors,
            "journal": journal,
            "year": year,
            "doi": doi,
            "abstract": abstract
        })

    return papers
```

### Step 3: Verify via CrossRef

```python
def verify_via_crossref(doi: str) -> bool:
    """Verify paper exists in CrossRef."""
    try:
        resp = requests.get(
            f"https://api.crossref.org/works/{doi}",
            timeout=10
        )
        return resp.status_code == 200
    except Exception:
        return False

def doi_to_bibtex(doi: str) -> str:
    """Get verified BibTeX from DOI via CrossRef."""
    response = requests.get(
        f"https://doi.org/{doi}",
        headers={"Accept": "application/x-bibtex"},
        allow_redirects=True,
        timeout=10
    )
    response.raise_for_status()
    return response.text
```

### Step 4: Validate Claims

```python
def validate_claim(pmid: str, claim_keywords: list, api_key: str = None) -> bool:
    """Check if a claim appears in the paper's abstract."""
    papers = fetch_pubmed_details([pmid], api_key)
    if not papers:
        return False

    abstract = papers[0].get("abstract", "").lower()
    return any(kw.lower() in abstract for kw in claim_keywords)
```

### Step 5: Handle Failures

If you cannot verify a citation at ANY step:

```latex
% Option 1: Explicit placeholder
\cite{PLACEHOLDER_smith2023_verify}  % TODO: Could not verify - scientist must confirm

% Option 2: Note in text
... as shown in prior work [CITATION NEEDED - could not verify Smith et al. 2023].
```

**Always inform the scientist.**

---

## Python Implementation

### Complete Biomedical Citation Manager

```python
"""
Biomedical Citation Manager - Verified citation workflow using PubMed and CrossRef.
"""

import requests
import xml.etree.ElementTree as ET
import time
from typing import Optional, List, Dict, Tuple
from dataclasses import dataclass, field

@dataclass
class BiomedPaper:
    title: str
    authors: List[str]
    year: str
    journal: str
    doi: Optional[str]
    pmid: Optional[str]
    abstract: Optional[str]
    volume: Optional[str] = None
    issue: Optional[str] = None
    pages: Optional[str] = None

class BiomedCitationManager:
    """Manage biomedical citations with PubMed verification."""

    def __init__(self, api_key: Optional[str] = None):
        self.api_key = api_key
        self.verified_papers: Dict[str, BiomedPaper] = {}

    def search(self, query: str, limit: int = 10) -> List[str]:
        """Search PubMed, return PMIDs."""
        params = {
            "db": "pubmed",
            "term": query,
            "retmax": limit,
            "retmode": "json",
            "sort": "relevance"
        }
        if self.api_key:
            params["api_key"] = self.api_key

        resp = requests.get(
            "https://eutils.ncbi.nlm.nih.gov/entrez/eutils/esearch.fcgi",
            params=params, timeout=10
        )
        resp.raise_for_status()
        return resp.json().get("esearchresult", {}).get("idlist", [])

    def fetch(self, pmids: List[str]) -> List[BiomedPaper]:
        """Fetch paper details from PubMed."""
        params = {
            "db": "pubmed",
            "id": ",".join(pmids),
            "retmode": "xml",
            "rettype": "abstract"
        }
        if self.api_key:
            params["api_key"] = self.api_key

        resp = requests.get(
            "https://eutils.ncbi.nlm.nih.gov/entrez/eutils/efetch.fcgi",
            params=params, timeout=15
        )
        resp.raise_for_status()
        root = ET.fromstring(resp.text)
        papers = []

        for article in root.findall(".//PubmedArticle"):
            medline = article.find(".//MedlineCitation")
            art = medline.find("Article")

            # Extract fields
            title = art.findtext("ArticleTitle", "")
            journal = art.findtext(".//Journal/Title", "")
            year = medline.findtext(".//PubDate/Year", "")
            pmid = medline.findtext("PMID", "")
            volume = art.findtext(".//JournalIssue/Volume", "")
            issue = art.findtext(".//JournalIssue/Issue", "")

            # Pages
            pages = art.findtext(".//Pagination/MedlinePgn", "")

            # DOI
            doi = ""
            for eid in article.findall(".//ArticleId"):
                if eid.get("IdType") == "doi":
                    doi = eid.text

            # Authors
            authors = []
            for author in art.findall(".//Author"):
                last = author.findtext("LastName", "")
                first = author.findtext("ForeName", "")
                if last:
                    authors.append(f"{last}, {first}")

            # Abstract
            abstract_parts = []
            for ab in art.findall(".//AbstractText"):
                label = ab.get("Label", "")
                text = ab.text or ""
                if label:
                    abstract_parts.append(f"{label}: {text}")
                else:
                    abstract_parts.append(text)
            abstract = " ".join(abstract_parts)

            papers.append(BiomedPaper(
                title=title, authors=authors, year=year,
                journal=journal, doi=doi, pmid=pmid,
                abstract=abstract, volume=volume,
                issue=issue, pages=pages
            ))

        return papers

    def verify(self, paper: BiomedPaper) -> Tuple[bool, List[str]]:
        """Verify paper exists in multiple sources."""
        sources = ["PubMed"]  # Already found via PubMed

        if paper.doi:
            try:
                resp = requests.get(
                    f"https://api.crossref.org/works/{paper.doi}",
                    timeout=10
                )
                if resp.status_code == 200:
                    sources.append("CrossRef")
            except Exception:
                pass

        return len(sources) >= 2, sources

    def get_bibtex(self, paper: BiomedPaper) -> str:
        """Get BibTeX for a verified paper."""
        if paper.doi:
            try:
                resp = requests.get(
                    f"https://doi.org/{paper.doi}",
                    headers={"Accept": "application/x-bibtex"},
                    timeout=10, allow_redirects=True
                )
                if resp.status_code == 200:
                    return resp.text
            except Exception:
                pass

        # Fallback: generate from metadata
        first_author = paper.authors[0].split(",")[0] if paper.authors else "unknown"
        key = f"{first_author.lower()}_{paper.year}"
        authors_str = " and ".join(paper.authors)

        return f"""@article{{{key},
  title = {{{paper.title}}},
  author = {{{authors_str}}},
  journal = {{{paper.journal}}},
  year = {{{paper.year}}},
  volume = {{{paper.volume or ''}}},
  number = {{{paper.issue or ''}}},
  pages = {{{paper.pages or ''}}},
  doi = {{{paper.doi or ''}}},
  pmid = {{{paper.pmid or ''}}}
}}"""

    def cite(self, query: str) -> Optional[str]:
        """Full workflow: search → verify → return BibTeX."""
        pmids = self.search(query, limit=5)
        if not pmids:
            return None

        papers = self.fetch(pmids[:1])
        if not papers:
            return None

        paper = papers[0]
        verified, sources = self.verify(paper)
        if not verified:
            print(f"Warning: Only verified in {sources}")

        bibtex = self.get_bibtex(paper)
        if bibtex:
            self.verified_papers[paper.pmid] = paper
        return bibtex


# Usage
if __name__ == "__main__":
    cm = BiomedCitationManager()
    bibtex = cm.cite("pembrolizumab melanoma checkpoint inhibitor")
    if bibtex:
        print(bibtex)
```

### Quick Functions

```python
def quick_cite_pubmed(query: str) -> str:
    """One-liner PubMed citation."""
    cm = BiomedCitationManager()
    return cm.cite(query)

def batch_cite(queries: List[str], output_file: str = "references.bib"):
    """Cite multiple papers and save to file."""
    cm = BiomedCitationManager()
    entries = []
    for query in queries:
        print(f"Processing: {query}")
        bibtex = cm.cite(query)
        if bibtex:
            entries.append(bibtex)
        time.sleep(0.5)  # Rate limiting

    with open(output_file, 'w') as f:
        f.write("\n\n".join(entries))
    print(f"Saved {len(entries)} citations to {output_file}")
```

---

## BibTeX and Citation Formats

### Biomedical Journal Article

```bibtex
@article{gandhi_2018,
  title = {Pembrolizumab plus Chemotherapy in Metastatic Non-Small-Cell Lung Cancer},
  author = {Gandhi, Leena and Rodr{\'\i}guez-Abreu, Delvys and Gadgeel, Shirish and others},
  journal = {New England Journal of Medicine},
  volume = {378},
  number = {22},
  pages = {2078--2092},
  year = {2018},
  doi = {10.1056/NEJMoa1801005},
  pmid = {29658856}
}
```

### Vancouver Style (Numbered)

Most biomedical journals use Vancouver (numbered) citation style:

```
Gandhi L, Rodríguez-Abreu D, Gadgeel S, et al. Pembrolizumab plus
chemotherapy in metastatic non-small-cell lung cancer. N Engl J Med.
2018;378(22):2078-2092. doi:10.1056/NEJMoa1801005
```

### Author-Year (Harvard) Style

Some journals (e.g., Cell Press) use author-year:

```
(Gandhi et al., 2018)
```

### LaTeX Setup for Vancouver Style

```latex
% Using natbib (common in biomedical)
\usepackage[numbers,sort&compress]{natbib}
\bibliographystyle{vancouver}

% Citations
\cite{gandhi_2018}        % [1]
\citep{gandhi_2018}       % [1]
```

---

## Reference Management

### Journal Abbreviation Standards

Use NLM (National Library of Medicine) abbreviations for journal names:
- New England Journal of Medicine → N Engl J Med
- The Lancet → Lancet
- Journal of the American Medical Association → JAMA
- Nature Medicine → Nat Med
- Cell → Cell (not abbreviated)

**NLM Catalog for abbreviations**: https://www.ncbi.nlm.nih.gov/nlmcatalog/journals

### Common Issues

| Issue | Solution |
|-------|----------|
| Journal name not abbreviated | Look up in NLM Catalog |
| Special characters in author names | Use LaTeX encoding: `{\'e}`, `{\"u}` |
| "et al." usage | Follow journal policy (usually >3 or >6 authors) |
| Epub ahead of print | Include DOI, note "Epub ahead of print" |
| Retracted papers | NEVER cite retracted papers; check Retraction Watch |

---

## Troubleshooting

### Common Issues

**Issue: PubMed returns no results**
- Try MeSH terms instead of free text
- Use [MeSH Browser](https://meshb.nlm.nih.gov/) to find correct terms
- Try author search: "Smith J[au]"

**Issue: DOI doesn't resolve**
- Check DOI format (should start with 10.)
- Try CrossRef metadata search by title
- Use PMID to fetch DOI from PubMed

**Issue: Paper is behind paywall**
- Use PubMed Central (PMC) for open access versions
- Check Europe PMC for author manuscripts
- Use Unpaywall API for legal open access copies

### Verification Checklist

Before adding a citation:

- [ ] Paper found in PubMed (has PMID)
- [ ] DOI verified via CrossRef
- [ ] BibTeX retrieved programmatically (not from memory)
- [ ] Author names and year verified
- [ ] Journal name correctly abbreviated
- [ ] Paper is NOT retracted (check Retraction Watch)
- [ ] Claim you're citing actually appears in the paper

---

## Additional Resources

**APIs:**
- PubMed E-utilities: https://www.ncbi.nlm.nih.gov/books/NBK25501/
- CrossRef: https://www.crossref.org/documentation/retrieve-metadata/rest-api/
- Europe PMC: https://europepmc.org/RestfulWebService
- ClinicalTrials.gov: https://clinicaltrials.gov/data-api/about-api

**Python Libraries:**
- `biopython` (Entrez): https://biopython.org/
- `habanero` (CrossRef): https://github.com/sckott/habanero
- `pubmed-parser`: https://github.com/titipata/pubmed_parser

**Verification Tools:**
- Retraction Watch Database: https://retractionwatch.com/retraction-watch-database-user-guide/
- iCite (NIH): https://icite.od.nih.gov/
