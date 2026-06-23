# Convexification of Atomic-Structure Solution from the Pair Distribution Function

An open problem: **what minimal information about an atomic structure, beyond
its pair distribution function (PDF), makes the PDF → structure inverse
problem identifiable and convex?** The PDF gives a distribution of
interatomic distances without assigning each distance to an atom pair — an
instance of the *unassigned distance geometry problem* — and is further
band-limited by instrumental resolution. The residual non-uniqueness is what
structural and chemical priors are asked to remove.

Drafted for submission to the [CUHK-Shenzhen AI Math Open Problems](https://rybindmitry.github.io/problems/index.html) bank.

## The question, in one line

Given a band-limited, scattering-weighted distance measurement $F(X)=R\,\rho_X$
of a configuration $X$ and a structural prior $C$ of free dimension $d_C$,
characterize when the inversion is identifiable, locally identifiable, and
$\varepsilon$-convex — conjecturally at the sharp threshold
$m_{\mathrm{eff}} \ge d_C$ between the instrument's information capacity
$m_{\mathrm{eff}}$ and the prior's free dimension (modulo the irreducible
chirality / reflection ambiguity).

The full statement, known facts, and three sub-questions — (a) the threshold,
(b) the minimal prior, (c) the information-theoretic form — are in the LaTeX
sources below.

## Files

| file | description |
|---|---|
| `pdf_convexification_problem_math.tex` / `.pdf` | concise math-only submission draft (2 pp) |
| `pdf_convexification_problem.tex` / `.pdf` | full statement with known facts and references |
| `archive/` | internal notes / earlier drafts (gitignored) |

## Build

```bash
pdflatex pdf_convexification_problem_math.tex   # run twice for citation numbers
# or: latexmk -pdf pdf_convexification_problem_math.tex
```

Both `.tex` files are self-contained. For the problem-bank form, paste the
fragment from `\title{...}` through `\end{thebibliography}` (drop the preamble
and `\begin{document}` / `\end{document}`).

## References

1. S. Huang, I. Dokmanić, *Reconstructing Point Sets from Distance
   Distributions*, IEEE Trans. Signal Process. **69** (2021), 1811–1827.
   [arXiv:1804.02465](https://arxiv.org/abs/1804.02465).
2. K. Jaganathan, B. Hassibi, *Reconstruction of Integers from Pairwise
   Distances*, [arXiv:1212.2386](https://arxiv.org/abs/1212.2386) (2012).
3. S. J. L. Billinge, P. M. Duxbury, D. S. Gonçalves, C. Lavor, A. Mucherino,
   *Recent results on assigned and unassigned distance geometry with
   applications to protein molecules and nanostructures*, Ann. Oper. Res.
   **271**(1) (2018), 161–203.
   [doi:10.1007/s10479-018-2989-6](https://doi.org/10.1007/s10479-018-2989-6).
4. S. J. L. Billinge, M. G. Kanatzidis, *Beyond crystallography: the study of
   disorder, nanocrystallinity and crystallographically challenged materials
   with pair distribution functions*, Chem. Commun. (2004), 749–760.
   [doi:10.1039/b311073n](https://doi.org/10.1039/b311073n).

## Links

- Submission target: [CUHK-SZ AI Math Open Problems — Submit a problem](https://rybindmitry.github.io/problems/submit.html)
- License: problem text under [CC-BY-4.0](https://creativecommons.org/licenses/by/4.0/).
