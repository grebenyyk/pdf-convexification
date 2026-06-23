# Convexification of Atomic-Structure Solution from the Pair Distribution Function

An open problem: **what minimal information about an atomic structure, beyond
its pair distribution function (PDF), makes the PDF → structure inverse
problem identifiable and convex?** The PDF gives a distribution of
interatomic distances without assigning each distance to an atom pair — an
instance of the *unassigned distance geometry problem* — and is further
band-limited by instrumental resolution. The residual non-uniqueness is what
structural and chemical priors are asked to remove.

## The question

Given a band-limited, scattering-weighted distance measurement $F(X)=R\,\rho_X$
of a configuration $X$ and a structural prior $C$ of free dimension $d_C$,
characterize when the inversion is identifiable, locally identifiable, and
$\varepsilon$-convex — conjecturally at the sharp threshold
$m_{\mathrm{eff}} \ge d_C$ between the instrument's information capacity
$m_{\mathrm{eff}}$ and the prior's free dimension (modulo the irreducible
chirality / reflection ambiguity).

The threshold $m_{\mathrm{eff}} \ge d_C$ should be understood as a conjectural information-capacity lower bound/phase transition, not as an assumed theorem. Part of the problem is to determine what additional genericity, sampling/noise, finite-rank, and prior-regularity assumptions are needed for local identifiability, global injectivity, or convexity; counterexamples to the naive threshold are also considered valid progress.

## Clarifications for solvers

The submitted problem statement is frozen; this repository records clarifications
and acceptable interpretations.

- The threshold $m_{\mathrm{eff}} \ge d_C$ is conjectural. A counterexample
  to this naive threshold is a valid contribution.
- $m_{\mathrm{eff}}$ should be interpreted as an effective information
  dimension, requiring a finite sampling model, noise floor, resolution
  threshold, or singular-value cutoff.
- Identifiability, local identifiability, and convexity should be treated as
  distinct targets. Proving implications between them, or showing that an
  implication fails, is part of the problem.
- The information-theoretic formulation requires an explicit probabilistic/noise
  model and reference measure on the prior manifold.
- Partial solutions are absolutely welcome.

## Files

| file | description |
|---|---|
| `pdf_convexification_problem_math.tex` / `.pdf` | concise math-only submission draft |
| `pdf_convexification_problem.tex` / `.pdf` | full statement with chemical details |

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
   [doi:10.1039/B309577K](https://doi.org/10.1039/B309577K).
   

## Links

- Submission: [CUHK-SZ AI Math Open Problems — Problem 17](https://rybindmitry.github.io/problems/17.html)
- License: problem text under [CC-BY-4.0](https://creativecommons.org/licenses/by/4.0/).
