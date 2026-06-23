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

### Detailed clarifications

#### 1. What counts as “solving” the problem?

A complete solution is not required. Valid contributions include:

- **Rigorous proofs** for natural subclasses of priors (e.g. fixed bond lengths
  and angles, free dihedrals, hard-sphere exclusion).
- **Counterexamples** to the naive threshold $m_{\mathrm{eff}} \ge d_C$,
  especially constructions with $m_{\mathrm{eff}} = d_C - 1$ that still admit
  flip ambiguities or spurious local minima.
- **Sharp characterizations** of local identifiability, global identifiability,
  or landscape convexity as *separate* results.
- **Computational certificates**: for a specified finite family of priors and a
  discretized resolution operator, numerically determine the threshold at which
  injectivity / convexity is lost, with reproducible code and data.

#### 2. $m_{\mathrm{eff}}$ must be made explicit

The symbol $m_{\mathrm{eff}}$ is intentionally left as an *effective
information dimension*. A valid solution must choose and state one of the
following interpretations (or an equivalent one):

- **Singular-value cutoff:** the number of singular values of the discretized
  operator $R$ above a specified noise floor.
- **Nyquist count:** $m_{\mathrm{eff}} = \lceil R_{\max} / \Delta r\rceil$
  with $\Delta r = \pi / Q_{\max}$, possibly reduced by broadening $\sigma$.
- **Finite-sample rank:** the rank of the linear map from a discretized distance
  grid to the observed PDF samples.

You may assume $m_{\mathrm{eff}}$ is finite. The exact value may depend on the
kernel and on $R_{\max}$; state your choice.

#### 3. Treat P1, P2, P3 separately

The equivalence

> P1 (injectivity) $\Leftrightarrow$ P2 (full-rank Fisher)
> $\Leftrightarrow$ P3 ($\varepsilon$-convexity)

is a **conjecture**, not an assumed theorem.

- **P2 is local.** It can often be attacked with differential geometry /
  transversality arguments.
- **P1 is global.** It is the hardest and may fail even when
  $m_{\mathrm{eff}} \ge d_C$.
- **P3 is about optimization landscape.** It requires specifying the Riemannian
  metric on $C$ and the norm on $Y$.

Do not assume the three properties are equivalent. Proving or disproving any
one implication is already progress.

#### 4. Genericity

“For generic $X \in C$” means: the set of exceptions has measure zero with
respect to a natural measure on the prior manifold $C$ (e.g. Lebesgue measure in
internal-coordinate parameter space). You may restrict to smooth points of $C$.

#### 5. The chirality / reflection ambiguity is irreducible

Pair-distance data, whether exact or band-limited, cannot distinguish a chiral
structure from its mirror image. Therefore:

- Identifiability holds at best modulo a $\mathbb{Z}_2$ reflection.
- A fiber of size 2 for chiral configurations is **not** a failure of the
  problem.
- Do not quotient reflections away implicitly; state clearly when your result is
  “up to reflection.”

#### 6. Permutation of identical atoms

Atoms with the same scattering length $b_i$ can be permuted without changing
$F(X)$. The problem is formally posed on structures modulo rigid motions, but
for identically labeled atoms you may additionally quotient by permutations of
those labels. A valid solution should state which symmetry group is being used.

#### 7. What is a “chemistry-consistent prior”?

At minimum, a prior $C$ is a closed subset of
$\mathcal{X} = (\mathbb{R}^3)^N / E(3)$ that can be realized in internal coordinates with:

- a bond graph,
- fixed or interval-constrained bond lengths and bond angles,
- a finite set of free dihedral angles whose cardinality defines $d_C$,
- inequality constraints (steric lower bounds, coordination bounds, etc.).

You may restrict to smooth manifolds $C$ (away from constraint boundaries). You
do not need to model all of chemistry; a well-defined subclass is enough.

#### 8. “Minimal prior” means maximal $d_C$

For given resolution parameters $(Q_{\max}, \sigma)$, the “least informative”
prior is the one with the largest number of free dihedrals $d_C$ for which the
desired property (P1/P2/P3) still holds. Thus the trade-off curve
$d_C^{\,*}(Q_{\max})$ is well-defined once a property and a family of priors are
fixed.

#### 9. The information-theoretic part (item c) is optional

To address the deficit

$$
I_{\mathrm{deficit}} = h(X \mid C) - I\bigl(F(X); X \mid C\bigr),
$$

you must supply:

- a probabilistic noise model,
- a reference measure on $C$,
- a definition of $h$ and $I$ compatible with the band-limited observation.

If you do not wish to address this part, that is acceptable; partial solutions
are welcome.

#### 10. Norms and spaces

Unless stated otherwise, assume:

- $Y = L^2([0, R_{\max}])$ or a finite-dimensional sample space,
- the loss is the least-squares residual
  $\mathcal{L}_y(X) = \|F(X) - y\|_Y^2$.

If you use a different norm or regularizer, state it explicitly.

#### 11. Numerical / experimental contributions

If you solve the problem computationally for a specific family:

- Provide the code and the exact discretization of $R$.
- Report how $m_{\mathrm{eff}}$ was estimated.
- Show the failure cases (e.g. pairs of non-congruent structures with the same
  PDF, or landscapes with spurious minima).
- Use reproducible random seeds and make the structure files / PDF data
  available.

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
