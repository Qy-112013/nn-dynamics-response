# House phrase bank (verbatim from the group's letters)

Use these as the default wording. Keep them; vary only the bracketed slots. All are
quoted as they actually appear across SMCA, TCYB, TAI, TCAS-I, Neural Networks, and
Science China reply letters.

## Per-recipient opening sentences

**To the Editor-in-Chief** (first paragraph of page 1):
> The authors appreciate the Editor-in-Chief's, the Associate Editor's and the reviewers' insightful comments and constructive suggestions. In light of the comments and suggestions of the Associate Editor and the reviewers, we have tried our best to make a very careful revision of the paper. The revisions suggested by the reviewers are highlighted in \textcolor{blue}{blue font} in the revised paper.

(For a clearly positive decision swap "insightful" → "positive".)

**To an Associate Editor:**
> The authors appreciate the Associate Editor's and the reviewers' insightful comments and constructive suggestions. In light of the comments and suggestions of the Associate Editor and the reviewers, we have tried our best to make a very careful revision of the paper. The \textcolor{blue}{blue font} are revisions suggested by the reviewers.

**To a Reviewer:**
> The authors wish to express their appreciation to the reviewers for insightful comments and useful suggestions. Without the reviewers' help, the paper cannot reach the present much improved level.

(When a reviewer grouped comments, append: "We will compile the comments and provide consolidated responses.")

## Editor / AE reply openers (item 0)

- EiC: "Thanks the Editor-in-Chief for the time and efforts in handling the paper and for providing the opportunity to revise the manuscript. We appreciate you very much for your constructive suggestions and comments on our manuscript entitled ``\papertitle"  (ID: \msid). In light of the comments of the Associate Editor and the reviewers, we have tried our best to revise our manuscript."
- EiC (closing hope, Elsevier): "We hope that the revised manuscript now meets the standards of \textit{Neural Networks}, and we look forward to hearing from you at your earliest convenience."
- AE: "Thanks the Associate Editor for your summary and pointing out these problems. In light of the comments of the reviewers, we have tried our best to make a very careful revision of the paper."
- AE (constructive): "Thanks the Associate Editor for the constructive guidance. In response, we have carefully and thoroughly revised the manuscript to address all comments raised by the reviewers."

## Reviewer reply openers (by situation)

| Situation | Opener |
|---|---|
| Overall positive / recommendation | "Thanks the reviewer very much for the encouraging comments and for the positive recommendation." |
| Summary comment | "Thanks the reviewer for your summary. We really appreciate your efforts in reviewing our manuscript. We have revised the manuscript accordingly, and our point-by-point responses are presented as below." |
| Points out a problem | "Thanks the reviewer for pointing out this problem. According to your comment, we have [action]." |
| Constructive suggestion | "Thanks the reviewer for your constructive suggestion. In response, we have [action] (please see page N … in the revised version for details)." |
| Points out a mistake | "We are extremely grateful to reviewer for pointing out this mistake, and have [action]." |
| Careful observation / typo | "Thanks the reviewer for this careful observation. We apologize for the typographical oversights. In response, we have [action]." |
| Insightful question | "Thanks the reviewer for this insightful question. [explanation]" |
| Valuable suggestion | "Thanks the reviewer for your valuable suggestion. In response, we have [action]." |
| Acceptance round (reviewer accepts) | "We sincerely thank the reviewer for the positive assessment and are pleased that the paper is deemed acceptable for publication." |
| Grateful, prior revision accepted | "We are deeply grateful to the reviewer for your positive assessment on our previous revision. Without your constructive suggestions, this paper would not reach its current standard." |

## Concession / agreement

> We completely agree that [the more general / realistic scenario] is a more generalized and physically realistic condition … 

> Thanks the reviewer for pointing out this oversight. In response, we have [removed / corrected] …

## Polite disagreement & reviewer-suggested citations

> Concerning the references suggested by Reviewer N, we have critically evaluated each one against the content and scope of our paper. Only those references that are directly relevant to our work and genuinely contribute to improving the quality and presentation of the manuscript have been incorporated, with clear and explicit justifications provided for each citation. References that are not closely related to the proposed work have not been cited.

> We have carefully studied the recommended papers in the context of our current study's focus … To strengthen our introduction, we have gladly incorporated the [first] suggested study …

Disagree by giving a **scientific or scope** reason, never time/money/convenience. Acknowledge first.

## Location pointers (every change carries one)

Every change must tell the reviewer **where** it landed in the manuscript. Two house forms —
use the **parenthetical** for a *described* change, and the **connector sentence** immediately
after a *pasted* blue block:

**Parenthetical** (at the end of the action sentence):
- `(please see page N of Section X in the revised version for details).`
- `(please see pages N--M of Section X in the revised version for details).`
- `(please see the third and fourth paragraphs on pages 1--2 in Section I in the revised version for details).`
- `(please see the blue font in the revised version for details).`

**Connector sentence** (right after a pasted blue block, so the paste is anchored to a page):
- `In the revised version, we have added the above statement in Section X on page N.`
- `In the revised version, we have added/revised the above [Remark/equation] in Section X on page N.`

Second revision: replace "the revised version" → "the second revised version" in both forms.

## Closing bullet block (end of each recipient page)

Header (pick one): `\textbf{Some key points of the revision are:}` or `\textbf{Other significant changes in the paper:}`

```latex
\vspace{2ex}
\begin{enumerate}[$\bullet$]
\item According to Reviewer 1's comments, we have [change] (please see page N of Section X in the revised version for details).
\vspace{2ex}
\item According to Reviewers 1 and 3's comments, we have [change] (please see pages N--M of Section X in the revised version for details).
\end{enumerate}
```

## Comment / reply unit (the atom)

```latex
\item[k)] \textbf{Your comment and suggestion}: \ \textit{``VERBATIM COMMENT"}

\vspace{2ex} \textbf{Our reply}: \ [acknowledge] [action] (please see page N … for details).
```
