# House style: structure + per-journal switches

The group's reply letters are a single, stable template. What changes between papers is
driven by the **corresponding manuscript** (mainly its reference style and section
numbering), not by preference. Detect these per submission.

## Invariant skeleton (every letter)

- `\documentclass[letter,onecolumn,11pt]{IEEEtran}` — used for **all** journals, including
  Elsevier *Neural Networks* and Science China Information Sciences. Never switch class.
- One **"SUMMARY OF CHANGES"** page per recipient, separated by `\vfill\newpage`; the
  centered title + `Manuscript ID` / `Paper Title` / `Author(s)` block repeats on every page.
- Recipient order: **Editor-in-Chief → Associate Editor(s) → Reviewer 1 … N**. One or two AEs.
- Underlined large header: `\underline{\Large \textbf{Reply to ...}}`.
- `\begin{enumerate}[1)]` with `\item[0)]` for the overall comment, then `1)`, `2)`, …
- Comment marker `\textbf{Your comment and suggestion}: \ \textit{``…''}`; reply marker
  `\textbf{Our reply}: \ …`.
- Highlight new manuscript text with `\textcolor{blue}{…}`; describe it as **"blue font"**.
- Paste added content inline; align numbering with `\setcounter{remark|figure|table}{n-1}`.
- Each recipient page ends with a `$\bullet$` "Some key points of the revision" / "Other
  significant changes in the paper" list.

## Two manuscript versions + blue-font consistency

A revision ships **two** manuscript files, and the reply letter must stay consistent with both:

- **Clean version (无标记):** the revised manuscript with no highlighting — the production copy.
- **Marked version (有标记):** the same manuscript with every reviewer-driven **addition or
  modified paragraph** wrapped in `\textcolor{blue}{…}` (blue font). Deletions are simply
  removed — nothing is marked for a deletion (no red, no strikethrough).

**The blue passage is the single source of truth, mirrored in three places.** For each comment
that changes or adds text, the *same* passage must appear, identical, in all three:

1. blue-highlighted in the **marked manuscript** at the cited location;
2. pasted in `\textcolor{blue}{…}` in the **reply**, directly **below** the "Our reply"
   explanation of that comment;
3. pointed to by `(please see page N of Section X in the revised version for details)` —
   "the revised version" is the **marked** copy, so the editor can find the blue change.

So the atom for a text change is: acknowledge → action sentence → pasted blue block → connector
"In the revised version, we have added the above statement in Section X on page N." Never paste
a blue block in the reply that isn't blue in the marked manuscript, and never leave a blue
manuscript change un-pasted (or at least un-pointed) in the reply.

## Figures & tables: lock them in place

A reply's figure/table must stay inside the comment it answers — it must never float into the
next comment. Place it with `[H]` (from `\usepackage{float}`, already in the template preamble),
not `[htbp]`, so it is pinned directly under the reply text and the next `\item` follows cleanly.
Remember: `\newpage` does **not** flush a pending float — only `[H]`, `\clearpage`, or
`\FloatBarrier` (package `placeins`) stop a float from migrating. The `\vfill\newpage` break
between recipient pages is safe only because `[H]` floats never pend; if you ever keep a floating
`[htbp]` figure, end that comment with `\clearpage` instead.

## Per-journal switches

| Journal (ID prefix) | Citation style in reply | Section nums | Author list | Notes |
|---|---|---|---|---|
| IEEE TSMC-Systems (`SMCA-`) | numeric `[n]`, added refs as `\item [{[n]}] …` | Roman (Section I, II) | `First Last, …` | |
| IEEE Cybernetics (`CYB-`) | numeric `[n]` | Roman | `First Last, …` | |
| IEEE Trans. AI (`TAI-`) | numeric `[n]` | Roman | `First Last, …` | RL papers add `algorithm`/`algpseudocode` |
| IEEE TCAS-I (`TCAS-I-`) | numeric `[n]` | Roman | `First Last, …` | tables common; `\setcounter{table}` |
| Elsevier *Neural Networks* (`NEUNET-`) | **author-year**, refs as `Surname, X. (Year). Title. \textit{Journal}, \textit{vol}, pp.` | Arabic (Section 2) | `First Last, …` | pasted refs go inside `\textcolor{blue}{…}` |
| Science China Info Sci (`SCIS-`) | numeric `[n]` | Arabic (Section 2) | **surname-first caps**: `SURNAME Given, SURNAME Given` | ships a separate `Cover_Letter.tex` (article class) |

**Reference style is mirrored from the manuscript, not chosen.** Best practice: open the
corresponding manuscript (or its `.bbl`) and copy its exact entry format and delimiters. When
references are renumbered across revisions, cross-reference old→new:
"references [10], [20] and [21] (references [13], [23] and [24] in the revised version)".

## Revision-round wording

- First revision (`…R1`): "the revised version".
- Second revision (`…R2`): "the second revised version".
- Acceptance-round replies use the acceptance opener (see phrase-bank.md) and minimal pasting.

## Exact original preamble (for 100% fidelity)

The group's IEEE letters use this superset (some files add `caption2`, `thm`, `algorithm`,
`booktabs`/`array`/`bm`). `assets/reply-template.tex` ships a compile-safe version with the
obsolete `caption2` commented out. For byte-faithful output, the originals include:

```latex
\usepackage{amsfonts}\usepackage{graphicx}\usepackage{amsmath,amssymb}\usepackage{latexsym}
\usepackage{psfrag}\usepackage{epsfig}\usepackage{graphicx,subfigure}\usepackage{graphicx,color}
\usepackage{cite}\usepackage{enumerate}\usepackage{flushend}\usepackage{multirow}
\usepackage{makecell}\usepackage{caption2}\usepackage{amsmath}
\setlength{\textwidth}{17cm}
\newtheorem{example}{Example}\newtheorem{remark}{Remark}\newtheorem{lemma}{Lemma}
```

## Environment / encoding

The group works on a Chinese Windows / GBK setup; source files often contain GBK-encoded
Chinese comments that appear as mojibake when read as UTF-8 (e.g. `% 自定义三线命令`). When
editing an existing letter, **do not "fix" or delete these comments blindly** — they are
intact in the author's editor. Emit new files in clean UTF-8 (or plain ASCII) and never paste
mojibake into output.

## Corresponding author / affiliation (per paper)

Treat the author list, corresponding author, affiliation, and contact email as **per-paper
input** — read them from the manuscript's front matter, or ask. Never assume or hard-code a
name; the `Author(s)` block and signature change with every submission.
