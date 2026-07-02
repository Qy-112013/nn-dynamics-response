# Comment handling: split, preserve, classify, map

## 1. Split and ID every comment

Assign stable IDs and keep them in the tracker:

- Editor-in-Chief items → `E.0`, `E.1`, …
- Associate Editor items → `AE.0`, `AE.1`, … (use `AE1.x` / `AE2.x` if there are two AEs)
- Reviewer n items → `Rn.0` (overall), `Rn.1`, `Rn.2`, …

`*.0` is always the reviewer's/editor's overall summary or recommendation; later numbers are
the specific points. In the `.tex` these become `\item[0)]`, `\item[1)]`, …

If a reviewer bundled several asks into one paragraph, split them into sub-points you can
answer individually, but **quote the full paragraph verbatim once** under the item, then
address each sub-ask in the reply. If comment boundaries are genuinely ambiguous, flag it —
never invent a reviewer or comment that isn't there.

## 2. Preserve verbatim

Reproduce each comment **exactly** inside `\textit{``…"}` — original wording, symbols,
math, and any typos. Do not paraphrase, soften, or "clean up" a comment; the editor compares
your quote against their copy. Convert plain quotes to LaTeX — open with `` `` ``, close with
`''` or `"` (both render as a right double quote; the house letters use `` ``…" ``) — and
escape `% & _ # $`.

## 3. Classify (for planning the reply, not shown in the letter)

| Category | Typical action |
|---|---|
| Overall / recommendation | Thank; no manuscript change |
| Motivation / novelty / significance | Rewrite Introduction; paste new paragraph |
| Model / assumption justification | Add a Remark; justify scope |
| Math check / notation consistency | Verify, correct, paste corrected eqn; unify symbols |
| Method scope ("does it apply to all…") | Add a Remark on applicability |
| Missing analysis (sensitivity / robustness / scale) | Add experiment + figure/table |
| Figure quality / readability | Redraw; increase resolution/fonts; paste figure |
| Reference / literature | Add refs in the manuscript's style; justify each |
| Typo / grammar / English | Correct; "polished … highlighted in blue font" |
| Reviewer-suggested citations | Evaluate each; cite only justified ones (see tone-and-stance.md) |
| Out-of-scope / future work | Acknowledge; add to Conclusion future-work |

## 4. Map each item to one resolution

Every item resolves to exactly one of:

1. **Manuscript change** with a location pointer `(please see page N … for details)`.
2. **Pasted revised content** in `\textcolor{blue}{…}` (author-supplied only) + pointer.
3. **Justified scientific/scope reason** (a polite, evidence-based explanation; may add a Remark).
4. **`AUTHOR_INPUT_NEEDED`** placeholder when you lack the revised text/number/figure.

## 5. Never fabricate — use placeholders

You will frequently lack the actual revised text, a new equation, a figure, a page number, or
a Remark number. **Do not invent any of these.** Emit a visible placeholder and surface it in
the missing-info flags. In LaTeX write it **underscore-free and in red** (raw `_` breaks LaTeX
in text mode); keep the token `AUTHOR_INPUT_NEEDED` for the tracker/flags only:

```latex
\textcolor{red}{[AUTHOR INPUT NEEDED: revised Remark 3 text — activation-function justification]}
```
```latex
(please see page \textcolor{red}{[PAGE?]} of Section X in the revised version for details)
```

Specifically, never guess: equation content, numerical results/thresholds, figure/table
contents, citation details (authors, venue, year, vol/pages), page or line numbers, or
Remark/Lemma/Theorem/Figure/Table numbers. A wrong fabricated number is worse than a flagged
gap — the editor will check.

## 6. Tracker (return alongside the .tex)

```
| ID   | Concern (short)            | Category        | Resolution            | Location        | Missing input |
|------|----------------------------|-----------------|-----------------------|-----------------|---------------|
| R1.1 | Strengthen motivation      | Motivation      | Rewrote Introduction  | pp.1-2, Sec. I  | —             |
| R1.2 | Why linearize (4)->(5)     | Justification   | Added Remark 2        | p.3, Sec. II    | —             |
| R2.1 | Figure resolution          | Figure quality  | Redrew Figs. 4-7      | pp.8-10         | new EPS files |
```
