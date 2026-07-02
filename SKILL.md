---
name: nn-dynamics-response
description: >-
  Use when drafting, auditing, or revising a point-by-point response-to-reviewers or
  rebuttal letter for a manuscript on neural-network dynamics — stability, Hopf
  bifurcation, time delay, fractional-order, reaction-diffusion, higher-order /
  hypergraph interactions (HOI), synchronization, tipping, or RL control — submitted to
  IEEE (TSMC-Systems, TCYB, TAI, TCAS-I, TNNLS), Elsevier (Neural Networks), or Science
  China Information Sciences. Triggers: reviewer comments, editor/AE decision letter,
  response draft, SUMMARY OF CHANGES, rebuttal, response to reviewers, 审稿意见回复,
  逐点回复, 修回信, 大修回复, 小修回复, 如何回复审稿人.
version: 0.1.1
status: Beta
---

# Neural-Network-Dynamics Reviewer Response (house style)

Convert editor/AE decision letters and reviewer comments into a **compile-ready LaTeX
response letter** in the group's house template — the IEEEtran "SUMMARY OF CHANGES" letter.

The letter is an editor-facing verification document: every editor and reviewer concern is
preserved **verbatim**, answered, and mapped to a concrete manuscript change, a justified
scientific reason, or an explicit `AUTHOR_INPUT_NEEDED` placeholder.

## When not to use

Nature-portfolio journals (Nature, Nature Communications, Communications Physics, …) → use
`nature-response` instead. A journal not listed in the description but within the group's
scope → still use this skill: keep the house shell, mirror that manuscript's reference
style, and note the inference in the tracker.

## Default stance

- Preserve every editor/AE/reviewer comment **verbatim** before responding; never reword a comment.
- Answer **every** numbered item; never silently drop one.
- Map each reply to a manuscript location, pasted revised text, a justified disagreement, or `AUTHOR_INPUT_NEEDED`.
- **Never fabricate** equations, figures, tables, numerical results, citations, page/line numbers, Remark/Lemma/Theorem numbers, or claimed changes. Paste revised content in blue ONLY when the author supplied it; otherwise emit a clearly-marked placeholder.
- **Match the corresponding manuscript's citation/reference style** — not a fixed format. The reply's references mirror *that specific paper's* bibliography (IEEE numeric `[n]`, Elsevier author-year, Science China numeric, …). When the manuscript or its `.bbl`/`.bib` is available, copy its exact style; otherwise infer from the journal. See [references/house-style.md](references/house-style.md).
- Warm, deferential tone. Acknowledge first, then act. When disagreeing, give a scientific/scope reason — never cost, time, or convenience. See [references/tone-and-stance.md](references/tone-and-stance.md).

## Inputs it accepts

Editor/AE decision letter · reviewer comments · previous response draft · manuscript change
notes / tracked changes · the corresponding manuscript (for reference style + numbering) ·
page–line map · figure/table/equation list · author notes in 中文 or English · journal name +
manuscript ID + revision round.

If comment boundaries are ambiguous, flag it — do not invent reviewer structure.

## Workflow

1. Identify mode (`draft` / `audit` / `revise`), decision type (minor / major / accept-with-changes), and revision round (R1 → "the revised version"; R2 → "the second revised version").
2. Detect the target journal → set **citation style mirrored from the manuscript** (IEEE numeric / Elsevier author-year / Science China numeric), section numbering (Roman `II` vs Arabic `2`), author-list format (`First Last` vs Science China `SURNAME Given`), recipients (EiC, one or two AEs, N reviewers). See [references/house-style.md](references/house-style.md).
3. Split editor (`E.x`), AE (`AE.x`), reviewer (`Rn.m`) comments — each preserved verbatim, numbered `0)` for the overall comment then `1)`, `2)`, … See [references/comment-handling.md](references/comment-handling.md).
4. Classify each item, plan the action, note missing input → tracker.
5. Scaffold the per-recipient pages from [assets/reply-template.tex](assets/reply-template.tex).
6. Draft each reply with house phrasing from [assets/phrase-bank.md](assets/phrase-bank.md): acknowledge → action → `(please see page N … in the revised version for details)`.
7. Paste author-supplied revised content inline in `\textcolor{blue}{...}`, `\setcounter{remark|figure|table}{}` aligned to the manuscript's numbering, and **close every pasted block with a page/section locator**. The pasted blue block must be the same passage highlighted blue in the marked (有标记) manuscript — the three-way rule and connector sentences are in [references/house-style.md](references/house-style.md). Missing text/page → the red placeholders in [references/comment-handling.md](references/comment-handling.md); never guess, and never a raw `_` in text mode.
8. Close each reviewer with the `$\bullet$` "Some key points of the revision" / "Other significant changes in the paper" list.
9. Run [references/qa-checklist.md](references/qa-checklist.md): completeness, traceability, no fabrication, LaTeX compile sanity.
10. Return the `.tex` (primary) + a short comment→action tracker + `AUTHOR_INPUT_NEEDED` flags (+ 中文核对 if the user worked in Chinese).

## Output

- **Primary:** the complete `.tex` reply letter (compiles with `pdflatex`/`latex`).
- A brief comment→action tracker.
- A list of `AUTHOR_INPUT_NEEDED` flags (or "None").
- Optional 中文核对 when the user wrote in Chinese.

## Red lines

- Don't drop or reword any comment.
- Don't invent equations, figures, tables, results, citations, line numbers, or Remark/Lemma/Theorem numbers, or claim a change the author didn't supply. Use `AUTHOR_INPUT_NEEDED` instead.
- Don't impose a uniform reference style across papers — each reply follows its **own manuscript's** format.
- Don't use hostile/accusatory language; don't cite time, money, or convenience to refuse a requested experiment.
- Don't hide limitations.
- Don't let a reply's figure/table float into the next comment — lock it with `[H]` (from `float`); `\newpage` alone won't flush a float.
- Don't switch the document class or template — the group's letters are always the IEEEtran SUMMARY OF CHANGES shell, even for Elsevier / Science China submissions.

## Files

| File | Open when |
|---|---|
| [assets/reply-template.tex](assets/reply-template.tex) | Scaffolding the `.tex`: preamble, per-recipient page, comment/reply unit, blue-paste + `\setcounter` patterns |
| [assets/phrase-bank.md](assets/phrase-bank.md) | You need the exact house boilerplate (openings, thanks, agree/disagree, location pointers, closing bullets) |
| [references/house-style.md](references/house-style.md) | Journal switches: citation style, section numbering, author-list format, revision-round wording, recipients, environment/encoding notes |
| [references/comment-handling.md](references/comment-handling.md) | Splitting / ID-ing / classifying comments, preserving verbatim, tracker fields, `AUTHOR_INPUT_NEEDED` |
| [references/tone-and-stance.md](references/tone-and-stance.md) | Recommended language, forbidden phrasing, how to disagree, acceptance-round wording |
| [references/qa-checklist.md](references/qa-checklist.md) | Before finalizing or auditing a draft: completeness, traceability, no-fabrication, LaTeX sanity |
| [examples/worked-reviewer-reply.md](examples/worked-reviewer-reply.md) | A full worked comment→reply derived from the group's real letters (IEEE-numeric and author-year variants) |
