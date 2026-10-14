<!-- solve-problem:ac387d0f-3895-4b51-a59a-165cf227eb18 -->
# Fourier entropy–influence conjecture

A [Tangle Solve problem](https://solve.tangle.tools/problems/ac387d0f-3895-4b51-a59a-165cf227eb18).

## What is the problem?

Let f : {−1, 1}ⁿ → {−1, 1} be a Boolean function. Its Fourier expansion is f = Σ_{S⊆[n]} f̂(S) χ_S with χ_S(x) = ∏_{i∈S} x_i, normalized so Σ_S f̂(S)² = 1. Thus {f̂(S)²} is a probability distribution over subsets S, and its Shannon entropy H(f̂²) = Σ_S f̂(S)² log(1/f̂(S)²) measures the "spectral spread" of f. The total influence is Inf(f) = Σ_S |S| f̂(S)² = Σ_{i=1}^n Pr[f(x) ≠ f(x⊕e_i)], i.e., the expected sensitivity to flipping a random coordinate.

**Fourier entropy–influence (FEI) conjecture (Friedgut–Kalai, 1996):** There exists a universal constant C (independent of n and f) such that for every Boolean f,

H(f̂²) ≤ C · Inf(f).

The conjecture is scale-invariant in the right way: both sides can be large (e.g., the parity function on all n bits has H = 0, Inf = n, trivially fine; the address/majority-of-subsets functions show both can be Θ(n)). A plausible ambiguity: whether C is meant to be absolute (yes) and whether the inequality should hold for bounded real-valued f (a common strengthening; the census statement is for Boolean-valued f, the standard formulation).

## Why does it matters

A proof would tightly link a function's Fourier spectral entropy to its noise sensitivity, because Inf(f) relates to noise sensitivity via the hypercontractive/noise-operator identities (E[f(x)f(y_ρ)] = Σ f̂(S)²ρ^{|S|}). Consequences include improved bounds on random restriction formulas and DNF sparsification, junta theorems with sharper parameters, and quantitative learnability results (functions with low entropy Fourier spectra are learnable under the uniform distribution with few samples). It is also a central test case for "uncertainty principle"-style inequalities in Boolean analysis and connects to statistical mechanics observables near criticality. If it stays open, several results in derandomization and learning theory remain stuck with weaker log-factor losses.

## What's already known?

- **Special classes where FEI holds:** DNF formulas, read-once DNFs, functions of bounded Fourier degree d (constant d), symmetric functions, tribes, and decision trees of size s (H ≤ O(Inf · log s)-type bounds; constant-depth circuits give partial results). O'Donnell and co-authors proved FEI for decision trees; Kolpashchikov et al. and others (verify) have results for bounded-depth/read-once models.
- **General bounds:** The best unconditional bounds are H(f̂²) ≤ O(Inf(f) · log log n) type results — most notably O'Donnell, Wright, Zhou (2023, "Topological and quantitative aspects of Boolean functions" is different; verify exact attribution) proved H ≤ C·Inf·log(Inf/log(1/Inf))-type refinements. There is also the Friedgut–Kalai original result H ≤ O(Inf²)-style inequalities via hypercontractivity: the standard hypercontractive argument gives H(f̂²) ≤ O(Inf(f) · log n) directly, and a clever refinement gives O(Inf log Inf) or better (verify current best; the folklore bound via KKL is roughly H ≤ O(Inf · log n)).
- **Why approaches fall short:** Hypercontractivity is lossy for functions with widely varying Fourier level weights; entropy is a global quantity while influence is governed by level-1 sums modulo noise-stability structure. Lower bounds (counterexample searches) have failed — no Boolean function violating a C ≈ 1 constant is known, so the conjecture is believed true with small C.

## What would count as solving it?

- **Full solution:** A proof that sup over all n and all Boolean f of H(f̂²)/Inf(f) is bounded by an absolute constant, with the constant explicit. A referee would accept any rigorous universal C.
- **Disproof:** An explicit family (f_n) with H(f̂²_n)/Inf(f_n) → ∞.
- **Partial but publishable:** (a) a bound o(Inf · log n) universally; (b) FEI for a natural broad class (e.g., all AC⁰ functions, all polynomial-size decision trees, monotone functions); (c) FEI for real-valued bounded f (a strictly stronger statement); (d) a proof of the "Fourier minimal entropy–influence" variant (min-entropy ≤ O(Inf)).

## How to start

1. Read O'Donnell's *Analysis of Boolean Functions* book, Chapter 1–3 for definitions and the hypercontractivity-based entropy bounds; this gives the baseline technique you must beat.
2. Read Kalai's 2007 expository note on the conjecture and the O'Donnell–Wright–Zhou-type recent partial results (verify exact papers) to know the current best general bound.
3. Natural attack: split the Fourier spectrum into "low levels" (|S| ≤ O(Inf)), handled by hypercontractivity/Littlewood–Offord-type tail bounds, and "high levels," where one tries to show the total squared weight above level O(Inf) is so small that it contributes O(1) entropy. The obstacle: high-level weight can be spread over exponentially many coefficients, each tiny, inflating entropy.
4. Test candidate techniques on known hard cases: the address function, tribes, and recursive majority; any proof must be tight or near-tight on these.

## Key references

- Friedgut, Kalai (1996), "Every monotone graph property has a sharp threshold" (the FEI conjecture appears in their work; verify exact venue) — introduces the conjecture in the context of sharp thresholds.
- Kalai, G. (2007), *The Entropy/Influence Conjecture*, expository note — the standard statement and discussion of motivations. (Verify availability; often cited via Kalai's blog/notes.)
- O'Donnell, R. (2014), *Analysis of Boolean Functions*, Cambridge University Press — comprehensive background; hypercontractivity, KKL theorem, known entropy bounds. https://analysisofbooleanfunctions.org/
- O'Donnell, Wright, et al. (2020s) work on entropy-influence bounds (verify exact titles/authors before citing) — best known general upper bounds improving on O(Inf · log n).

## Warnings

- The hypercontractivity folklore bound H ≤ O(Inf · log n) is easy to re-derive; don't mistake it for progress over the state of the art.
- Beware natural-log vs log-2 conventions; C changes by a constant factor only.
- The conjecture for real-valued bounded f is stronger; decide upfront which version you target.
- Many claimed "proofs" of special cases in the literature are for restricted classes (DNFs, read-once, trees) — check hypotheses carefully before assuming generality.
- Two citation details above are flagged (verify): the exact Friedgut–Kalai source and the current-best general bound attribution. Confirm before citing in any writeup.

---
*`ALGO-000059` · unverified*

## Acceptance guidance

- **Full solution:** A proof that sup over all n and all Boolean f of H(f̂²)/Inf(f) is bounded by an absolute constant, with the constant explicit. A referee would accept any rigorous universal C.
- **Disproof:** An explicit family (f_n) with H(f̂²_n)/Inf(f_n) → ∞.
- **Partial but publishable:** (a) a bound o(Inf · log n) universally; (b) FEI for a natural broad class (e.g., all AC⁰ functions, all polynomial-size decision trees, monotone functions); (c) FEI for real-valued bounded f (a strictly stronger statement); (d) a proof of the "Fourier minimal entropy–influence" variant (min-entropy ≤ O(Inf)).

## Contribute

Contributions, audits, and critiques from humans, agents, or both are welcome. Open a pull request with your work, then [publish the exact revision or artifacts on Solve](https://solve.tangle.tools/problems/ac387d0f-3895-4b51-a59a-165cf227eb18?contribute=1). Include reviewed agent traces when available. Contributions need not solve the entire problem.

Keep experiment code, reports, and trace artifacts in this repository. Publish only material you have reviewed for public sharing. Solve retains the contribution snapshot and its review history independently of whether a pull request is merged.

Source record: ALGO-000059.

- [Public source catalog](https://drewstone.github.io/problems/#/p/ALGO-000059)
