# QA checklist (run before finalizing or when auditing a draft)

## Completeness
- [ ] Every editor / AE / reviewer item has a reply — count `0)`,`1)`,`2)`… against the source.
- [ ] One recipient page per recipient (EiC, each AE, each Reviewer), in order.
- [ ] Each comment is quoted **verbatim** in `\textit{``…''}` (no paraphrase, typos preserved).
- [ ] Each reply follows acknowledge → action → location.
- [ ] Each recipient page ends with the `$\bullet$` "key points / other significant changes" list.

## Traceability
- [ ] Every claimed change has a manuscript locator — the parenthetical `(please see page N … in the revised version)` for a described change, or the connector `In the revised version, we have added … on page N.` right after a pasted blue block. No change without a page/section locator.
- [ ] Each text change is consistent across all three: blue in the marked (有标记) manuscript ⟺ blue block pasted below the reply ⟺ the page pointer — same passage, same location. No reply blue that isn't blue in the manuscript; no manuscript blue change left un-pasted/un-pointed.
- [ ] Revision-round wording correct ("revised" vs "second revised version").
- [ ] `\setcounter{remark|figure|table}{…}` matches the manuscript's numbering for every pasted block.
- [ ] Old→new reference numbers cross-referenced where the manuscript renumbered.

## No fabrication (the critical gate)
- [ ] No invented equations, figures, tables, numerical results, or thresholds.
- [ ] No invented citations (authors/venue/year/vol/pages) — pasted refs come from the author.
- [ ] No invented page/line numbers or Remark/Lemma/Theorem/Figure/Table numbers.
- [ ] Every gap is a visible `AUTHOR_INPUT_NEEDED` (or `[PAGE?]`) placeholder, also listed in the missing-info flags.
- [ ] Reference/citation style **matches the corresponding manuscript** (not a generic default).

## Tone
- [ ] Acknowledges before acting; gratitude present; no hostility/defensiveness.
- [ ] No refusal on time/money/convenience grounds.
- [ ] Disagreements give a scientific/scope reason and acknowledge the concern first.

## LaTeX compile sanity
- [ ] `\documentclass[...]{IEEEtran}` (class not switched); preamble matches house-style.md.
- [ ] Braces / `\begin{}`…`\end{}` / `\textcolor{blue}{…}` balanced; quotes open with `` `` `` and close with `''` or `"` (both render as a right double quote — the house letters use `` ``…" ``).
- [ ] `% & _ # $ ^ ~ \` escaped inside quoted comments.
- [ ] `\vfill\newpage` between recipient pages; document ends with `\end{document}`.
- [ ] Every figure/table is `[H]`-locked (or `\clearpage`/`\FloatBarrier`-fenced) so no float drifts into the next comment/recipient — confirm visually in the compiled PDF, not just that it compiles.
- [ ] If possible, compile: `pdflatex <file>.tex` (or `latex`+`dvips` for the `dvips` variant).
      A clean compile + correct page count (one page-group per recipient) is the strongest check.
      If compilation fails only on the obsolete `caption2`, comment it out (see house-style.md).

## Output package
- [ ] The `.tex` is returned in full and compiles.
- [ ] A short comment→action tracker is included.
- [ ] `AUTHOR_INPUT_NEEDED` flags are listed (or "None").
- [ ] 中文核对 included when the user worked in Chinese.
