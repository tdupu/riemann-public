# Notes on the Riemann Hypothesis

AI-generated notes, printed by Taylor Dupuy. They are temporary reading aids for
Levent Alpöge's Lean proof of the Riemann Hypothesis and GRH for Dirichlet L-functions. They are not an independent verification of the mathematics.
Updated 27 November 2026.

## Proof versions and verification

- **Original archive (20 November):** [Alpöge's announcement](https://alpo.ge/remark.pdf)
  and the [preserved original Lean source](https://github.com/leanprover-community/riemann-hypothesis/tree/original).
  Our existing book below reads this version.
- **Shorter rewrite (25 November):** [Luke Sernau, Anthropic colleagues, and Claude](https://github.com/lsernau/grh-lean)
  released two editions of the same five theorems at commit
  [`72fead10`](https://github.com/lsernau/grh-lean/tree/72fead102f663d5c7a407964a13dc0cf9d977207).
  The [readable edition](https://github.com/lsernau/grh-lean/tree/main/grh) has
  299,902 code lines (477,124 total lines); the
  [compact edition](https://github.com/lsernau/grh-lean/tree/main/grh-compact)
  has 76,149 code lines (112,827 total lines). The [community-maintained
  repository](https://github.com/leanprover-community/riemann-hypothesis)
  now uses the readable edition on its main branch.
- **Machine checks:** [Andrew Sutherland's verification record for both shorter
  editions](https://math.mit.edu/~drew/shortgrh/) reports successful builds,
  kernel and independent-checker replays, axiom audits, and paranoid comparator
  checks. His [original-archive record](https://math.mit.edu/~drew/grh/) is
  separate. The rewrite's authors say that no mathematician has yet read the
  new proof through and that no accompanying paper has been published.

The line counts above distinguish code lines from all lines, including comments
and blanks, as in Sutherland's pinned-source count.

## Our manuscripts

- [Notes on Alpöge's Proof of the Riemann Hypothesis](riemann-book.pdf)
  (21 November 2026). An AI-generated book explaining the original archive;
  it predates the shorter rewrite and does not verify the proof.
- [The Compact Lean Argument for Dirichlet GRH](grh-compact.pdf)
  (working draft, 27 November 2026). An AI-generated reading guide to the
  compact rewrite. It proves the elementary comparison from stated inputs;
  its deep construction and height arguments still need human mathematical
  review. [LaTeX source](latex/grh-compact/grh-compact.tex) ·
  [Bibliography](latex/grh-compact/grh-compact.bib).
- [The Approach to the Riemann Hypothesis via Hilbert–Pólya Operators and
  Deninger Cohomology Theories](hilbert-polya-deninger.pdf). Notes on a
  different, conditional route; this is not a proof of RH.

## Other reading and discussion

- [Bartosz Naskręcki's note on the condensed proof](https://nasqret.github.io/riemann-rev/summary/grh-condensed-summary.pdf)
  explains the rewrite and its checks; his [reading project](https://nasqret.github.io/riemann-rev/)
  includes a working mathematical write-up.
- [Jimmie Adriazola's reconstruction](https://github.com/jimjamzola/RH-Alpoge-Reconstruction)
  follows the readable rewrite in its current working manuscript. Its author
  explicitly describes the written reconstruction as conditional.
- [Abhishek Saha's updated one-page poster](https://x.com/ObhishekSaha/status/2125942899921563755)
  gives a high-level picture. The [G.R.H. Polymath Zulip](https://rh-polymath.zulipchat.com/)
  hosts ongoing discussion.

## Contents

| Path | What it is |
| --- | --- |
| `riemann-book.pdf` | The book on the original archive, built from `latex/riemann-book.tex` |
| `grh-compact.pdf` | Working draft on the compact rewrite, built from `latex/grh-compact/grh-compact.tex` |
| `hilbert-polya-deninger.pdf` | The Hilbert–Pólya and Deninger notes, built from `latex/notes.tex` |
| `latex/` | LaTeX sources, bibliographies, and figure and data files read by the builds |
| `lean/` | Lean 4 + Mathlib project formalizing claims of `latex/notes.tex` (not Alpöge's proof) |
| `blueprint/` | Hand-written leanblueprint describing the original Alpöge archive in mathematical language |
| `ai/` | AI provenance record (`ai-usage.md`) and token/cost record (`tokens.md`) |
| `AI-POLICY.md` | AI-use policy followed by the records |

This repository is a published copy, regenerated from a private working
repository. References inside its sources to `ai/<date>-…/` packages,
`scratch/`, or `refs/` point to files not included here.

## Building

```bash
cd latex && latexmk -pdf -outdir=build riemann-book.tex
cd latex && latexmk -pdf -outdir=build notes.tex
cd latex/grh-compact && latexmk -pdf -outdir=../build grh-compact.tex
cd lean && lake exe cache get && lake build
```
