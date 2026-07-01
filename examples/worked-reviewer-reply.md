# Worked example: comments → house-style reply

A realistic slice showing the full transform — a synthetic example, not from any specific
manuscript. Shows: verbatim quoting, the acknowledge→action→locate arc, a pasted Remark
with manuscript-matched citations, an `AUTHOR_INPUT_NEEDED` placeholder, and the closing list.

## Input given to the skill

- Journal: IEEE TSMC-Systems (`SMCA-XX-XX-XXXXR1`) → IEEE numeric citations, Roman sections.
- Reviewer 1, overall: *"the manuscript is well written and organized, so I recommend it to publish in this journal after solving the following problems."*
- R1.1: *"Please explain why the authors linearize model (4) into (5)."*
- R1.2: *"Coates' flow diagram … Is it suitable for solving all complex network characteristic equations? Some remarks are suggested to be added."*
- Author note: added **Remark 2** (p.3, Sec. II) on the linearization; added **Remark 6** (p.4, Sec. II) on Coates' scope. Did **not** supply the Remark 6 text yet.

## Output (.tex fragment)

```latex
\soheader
\recipient{Reply to Reviewer 1}

\vspace{2ex} The authors wish to express their appreciation to the reviewers for insightful comments and useful suggestions. Without the reviewers' help, the paper cannot reach the present much improved level.

\vspace{2ex}
\begin{enumerate}[1)]
\item[0)] \textbf{Your comment and suggestion}: \ \textit{``\ldots the manuscript is well written and organized, so I recommend it to publish in this journal after solving the following problems."}

\vspace{2ex}
\textbf{Our reply}: \ Thanks the reviewer very much for the encouraging comments and for the positive recommendation.

\vspace{2ex}
\item[1)] \textbf{Your comment and suggestion}: \ \textit{``Please explain why the authors linearize model (4) into (5)."}

\vspace{2ex} \textbf{Our reply}: \ Thanks the reviewer for pointing out this problem. According to your comment, we have added Remark 2 to explain the reason for the linearization of system (4) (please see page 3 in Section II in the revised version).

\vspace{2ex}
\setcounter{remark}{1}
\begin{remark}
In order to determine the stability boundary, the linear part governs the Hopf bifurcation threshold [17]. Since this work targets the threshold point rather than the bifurcation direction, the influence of the nonlinear terms is disregarded, and system (4) is reduced to system (5).
\end{remark}

\vspace{2ex}
\item[2)] \textbf{Your comment and suggestion}: \ \textit{``Coates' flow diagram is very effective \ldots Is it suitable for solving all complex network characteristic equations? Some remarks are suggested to be added."}

\vspace{2ex} \textbf{Our reply}: \ Thanks the reviewer for pointing the problem and for the good suggestion. According to your comment, we have added Remark 6 to illustrate the scope of application of Coates' flow diagram method (please see page 4 in Section II in the revised version).

\vspace{2ex}
\setcounter{remark}{5}
\begin{remark}
\textcolor{red}{[AUTHOR INPUT NEEDED: text of Remark 6 on the scope of Coates' flow diagram method]}
\end{remark}

\vspace{2ex} \textbf{Other significant changes in the paper:}
\vspace{2ex}
\begin{enumerate}[$\bullet$]
\item According to Reviewer 2's comments, we have increased the resolution and font size for the sub-figures of Figs. 4--7 (please see pages 8--10 in Section IV in the revised version for details).
\end{enumerate}
\end{enumerate}
```

Notes:
- R1.1's revised text was supplied → pasted; numbering aligned with `\setcounter{remark}{1}` so it prints as **Remark 2**.
- R1.2's text was **not** supplied → `AUTHOR_INPUT_NEEDED`, surfaced in the missing-info flags. Never invent a Remark.
- Citations use IEEE numeric `[17]` because the manuscript is IEEE.

## Same R1.1, if the paper were Elsevier *Neural Networks* (author-year)

Only the pasted citation format changes — the structure and phrasing are identical:

```latex
\textcolor{blue}{In order to determine the stability boundary, the linear part governs the Hopf bifurcation threshold (Surname et al., 2025). Since only the threshold point is sought here, the nonlinear terms are disregarded and system (4) is reduced to system (5).}
```

## Tracker + flags returned with it

```
| ID   | Concern               | Category       | Resolution          | Location     | Missing input        |
|------|-----------------------|----------------|---------------------|--------------|----------------------|
| R1.0 | Positive overall      | Overall        | Thanks              | —            | —                    |
| R1.1 | Why linearize (4)->(5)| Justification  | Added Remark 2      | p.3, Sec. II | —                    |
| R1.2 | Coates' scope         | Method scope   | Added Remark 6      | p.4, Sec. II | Remark 6 text        |

AUTHOR_INPUT_NEEDED: Remark 6 text (R1.2).
```
