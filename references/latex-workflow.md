# LaTeX Manuscript Generation

## Workflow
1. **Draft in Markdown first** — easier to iterate on content
2. **Generate clean LaTeX** — not pandoc conversion (pandoc produces `{[}` artifacts, wrong `\graphicspath`, no proper `\cite{}`)
3. **Compile with tectonic** (lightweight, auto-downloads packages) or pdflatex/xelatex
4. **Upload to cloud** (rclone to gdrive) for collaborator access

## LaTeX Best Practices
- Use `\graphicspath{{../figures/publication/v4/}}` — relative path to figure directory
- Use `\cite{key}` with `\begin{thebibliography}` or `.bib` + `natbib` — NOT pandoc-style `{[}1{]}`
- Use `\emph{GENE}` for gene names (italic per CNS convention)
- Use `$n = 10$` for inline math, `$p = 0.003$` for statistics
- Use en-dash `--` for ranges (pages, years), em-dash `---` for breaks
- Use `\textit{et al.}` not `et al.`
- Place `[H]` on figures/tables for exact positioning during draft review
- **Do NOT duplicate figure legends** — put them in `\caption{}` only, not also in a separate section

## Author Conventions (Chinese academic context)
- **Last corresponding author** = highest seniority (PI / lab head)
- **First corresponding author** = primary intellectual contributor
- Co-first authors marked with `*`, corresponding with `†`

## Nature Reference Format
```
Author, A.B., Author, C.D. & Author, E.F. Title. J. Abbrev. vol, pages (year).
```
- Authors: surname, initials with periods
- >5 authors: list first 5, then `et al.`
- Journal name: italic, standard abbreviation with periods
- Volume: bold
- For final submission: use `.bib` + `naturemag.bst` for automatic formatting

## Required Statements
- Ethics approval numbers
- Data availability (accession numbers)
- Author contributions (CRediT format)
- Competing interests declaration
- Funding sources
