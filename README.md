# nn-dynamics-response

Drafts, audits, and revises **point-by-point response-to-reviewers letters** for the group's
manuscripts on neural-network dynamics (stability, Hopf bifurcation, time delay,
fractional-order, reaction-diffusion, higher-order/hypergraph interactions, synchronization,
tipping, RL control), submitted to IEEE (TSMC-Systems, TCYB, TAI, TCAS-I, TNNLS), Elsevier
(*Neural Networks*), or Science China Information Sciences.

**Output:** a compile-ready LaTeX letter in the group's IEEEtran "SUMMARY OF CHANGES" house
template — per-recipient pages, `Your comment and suggestion` / `Our reply` markers, blue-font
highlighting, manuscript-matched citations — plus a comment→action tracker and a list of
`AUTHOR_INPUT_NEEDED` gaps.

## Fires on
Reviewer comments, an editor/AE decision letter, a previous response draft, or asks like
"回复审稿意见 / 写修回信 / response to reviewers / rebuttal" for a paper in the above scope.

## Core guarantees
- Every comment preserved verbatim and answered; none dropped.
- Nothing fabricated — missing equations/figures/numbers/citations become visible
  `AUTHOR_INPUT_NEEDED` placeholders.
- Reference style mirrors the **corresponding manuscript**, per paper.

## Layout
- `SKILL.md` — entry: stance, workflow, output, red lines, file index.
- `assets/reply-template.tex` — the compile-safe house scaffold.
- `assets/phrase-bank.md` — verbatim house boilerplate.
- `references/house-style.md` — per-journal switches, preamble, encoding notes.
- `references/comment-handling.md` — split/preserve/classify/map + no-fabrication.
- `references/tone-and-stance.md` — voice, disagreement, forbidden moves.
- `references/qa-checklist.md` — completeness, traceability, compile sanity.
- `examples/worked-reviewer-reply.md` — a full worked transform.

Adapted for the group's direction from the Nature-portfolio `nature-response` skill (kept
intact as a separate Nature tool).
