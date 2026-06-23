# Convexification of Atomic-Structure Solution from the Pair Distribution Function

An open mathematical problem on **what minimal chemical information, jointly
with instrument resolution, makes the PDF → atomic-structure inverse problem
identifiable and convex** — i.e., what extra information about the structure
does the pair distribution function (PDF) alone lack?

Drafted for submission to the **[CUHK-Shenzhen AI Math Open Problems](https://rybindmitry.github.io/problems/index.html)** bank.

---

## Motivation

Determining atomic coordinates from the PDF is the central inverse problem of
total-scattering crystallography. Empirically it is *non-convex*: practical
solvers need good initial guesses, restraints, and multi-start global
optimization. The non-convexity has two separable sources:

1. **Trivial symmetries** — permutations of identical atoms, rigid motions,
   and chirality — which one may quotient out by convention.
2. **Residual geometric non-uniqueness** — several non-congruent structures
   share the same pair-distance data, and band-limited instrumental resolution
   erases further information.

Chemical knowledge (bond lengths, angles, coordination, steric exclusion) is
known in practice to "convexify" the problem by pruning spurious minima. This
problem asks *how much* chemical information, *jointly with the instrument
resolution*, suffices to make the residual problem identifiable and convex —
equivalently, the *minimal* extra information the PDF alone lacks.

Mathematically, the PDF inversion is an instance of the **unassigned Distance
Geometry Problem (uDGP)**: the data are a multiset (distribution) of
interatomic distances without the assignment of each distance to a specific
atom pair.

## The problem (in brief)

Let $X=(x_1,\dots,x_N)\in(\mathbb{R}^3)^N$ be an element-labeled structure,
quotiented by rigid motions $E(3)$ (reflections **not** quotiented, so
chirality remains as an irreducible $\mathbb{Z}_2$ residue). The forward map is

$$F(X) = R_{Q_{\max},\sigma}\,\rho_X, \qquad \rho_X=\sum_{i<j} w_{ij}\,\delta_{\|x_i-x_j\|},$$

where $R_{Q_{\max},\sigma}$ is the **resolution operator** (reciprocal-space
window on $[0,Q_{\max}]$ giving $\Delta r\approx\pi/Q_{\max}$, plus thermal/
instrumental broadening of width $\sigma$). Its **instrument information
capacity**

$$m_{\mathrm{eff}}(Q_{\max},\sigma)=\dim\operatorname{span}\{R\,\delta_t:t\in[0,R_{\max}]\}\approx\lceil R_{\max}/\Delta r\rceil$$

is finite, with $m_{\mathrm{eff}}\to\infty$ as $Q_{\max}\to\infty$ (exact-distance
limit) and $m_{\mathrm{eff}}\to 0$ as $Q_{\max}\to 0$.

A **chemistry-consistent prior** $C$ is a closed subset, realizable as an
internal-coordinate manifold (bond graph with fixed lengths/angles, $d_C$ free
dihedrals, steric/coordination/hybridization inequalities), satisfying
chemistry-consistency axioms.

For the loss $\mathcal{L}_y(X)=\|F(X)-y\|^2|_C$ the problem relates three
properties:

- **(P1) Identifiability** — $F|_C$ injective modulo chirality.
- **(P2) Local identifiability** — Fisher operator $I_X=(DF_X)^*(DF_X)$ full rank on $T_XC$.
- **(P3) ε-convexity** — $\mathcal{L}_y|_C$ geodesically ε-convex with a unique stationary point (no spurious local minima).

> **Open problem.** Characterize the priors $C$ (as a function of resolution)
> for which **(P1) ⇔ (P2) ⇔ (P3)** hold generically, and find the **minimal**
> such prior. Conjectured sharp threshold: $m_{\mathrm{eff}} \ge d_C$ (modulo
> chirality), with three sub-questions on (a) the threshold, (b) the minimal
> prior / trade-off curve $d_C^{*}(Q_{\max})$, and (c) the information-theoretic
> form $I_{\mathrm{deficit}}=h(X|C)-I(F(X);X|C)\to 0$.

The crux is generic-global-rigidity theory transferred from *exact, unweighted,
complete* distance data to *band-limited, scattering-weighted, soft* data on a
*chemistry-constrained manifold*.

See [`pdf_convexification_problem.tex`](pdf_convexification_problem.tex) /
[`.pdf`](pdf_convexification_problem.pdf) for the full statement, known facts,
and references.

## References

1. S. Huang, I. Dokmanić, *Reconstructing Point Sets from Distance
   Distributions*, IEEE Trans. Signal Process. **69** (2021), 1811–1827.
   [arXiv:1804.02465](https://arxiv.org/abs/1804.02465).
2. K. Jaganathan, B. Hassibi, *Reconstruction of Integers from Pairwise
   Distances*, [arXiv:1212.2386](https://arxiv.org/abs/1212.2386) (2012).
3. S. J. L. Billinge, P. M. Duxbury, D. S. Gonçalves, C. Lavor, A. Mucherino,
   *Recent results on assigned and unassigned distance geometry with
   applications to protein molecules and nanostructures*, Ann. Oper. Res.
   **271**(1) (2018), 161–203. [doi:10.1007/s10479-018-2989-6](https://doi.org/10.1007/s10479-018-2989-6).
4. S. J. L. Billinge, M. G. Kanatzidis, *Beyond crystallography: the study of
   disorder, nanocrystallinity and crystallographically challenged materials
   with pair distribution functions*, Chem. Commun. (2004), 749–760.
   [doi:10.1039/b311073n](https://doi.org/10.1039/b311073n).

## Repository contents

```
pdf_convexification_problem.tex   # full LaTeX statement (compilable standalone)
pdf_convexification_problem.pdf   # rendered output
README.md
.gitignore
archive/                          # internal notes / earlier drafts (gitignored)
```

## Build

Requires a LaTeX distribution (e.g. TeX Live / MacTeX). The `.tex` is
self-contained:

```bash
pdflatex pdf_convexification_problem.tex      # run twice for citation numbers
# or, in one shot:
latexmk -pdf pdf_convexification_problem.tex
```

> **Note for the problem-bank submission form:** the bank renders a *fragment*
> and supplies its own `\documentclass`, preamble, and `\newtheorem`. For
> submission, paste everything from `\title{...}` through
> `\end{thebibliography}` (drop the `\documentclass` / `\usepackage` /
> `\newtheorem` / `\begin{document}` / `\maketitle` / `\end{document}` lines).
> The standalone preamble here is for local preview only.

## Submission target

[CUHK-Shenzhen AI Math Open Problems — Submit a problem](https://rybindmitry.github.io/problems/submit.html).

## License

Problem text (`.tex` / `.pdf` / `README.md`): released under
[CC-BY-4.0](https://creativecommons.org/licenses/by/4.0/).
