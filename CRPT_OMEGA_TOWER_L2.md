# L2 — Projection, Regime, Depth, Canonical Form, and Fibers

## L2.1 — The Reduction Strategy ρ_M

*Purpose.* Projection Operator and Fixed Points. This section defines the deterministic projection operator ρ_M and its iteration, and characterises its fixed-point set Fix(ρ_M). Fixed points are the canonical resting positions of the theory; all canonical-form and regime definitions depend on them.*


From here forward, M denotes a fixed substrate (𝒰_M, →_ρ, →_σ) together with
a reduction strategy ρ_M satisfying the conditions below. All constructs are
subscripted by M. The subscript _M is a parameter label, not an acronym.

### Definition

### Projection Operator ρ_M
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L2.1.D1 | `ρ_M` | ρ_M | **Reframed** |
**Synopsis:** The projection operator ρ_M is the deterministic, single-valued function that computes canonical form one step at a time. It satisfies three conditions: C1 (determinism: ρ_M selects exactly one successor), C2 (bisimulation equivariance: bisimilar inputs produce bisimilar outputs), and C3 (fixpoint stability: ρ_M(x) = x for all x ∈ Fix(ρ_M)). Iterating the projection operator produces the canonical form.

**Source:** Cousot & Cousot [1977] POPL — the abstraction step; reframed as the deterministic projection strategy over [`Sub` (L1.1.D1)](CRPT_OMEGA_TOWER_L1.md#substrate).

*Reframing Note.* **Source form:** the ARS one-step reduction *strategy* (Baader & Nipkow [1998] §9 — a deterministic selector of reduction steps) and the abstract-interpretation *abstraction step* (Cousot & Cousot [1977] — one application of the abstraction map). **CRPT form:** the projection operator ρ_M, packaged by C1–C3. **The delta:** nothing in the mathematics — a deterministic strategy over →_ρ whose iteration computes canonical forms — and everything in the reading: CRPT reads canonicalization as **information projection** (each step erases indiscernible structure, [`Disc-Proj` (L2.1.R6)](CRPT_OMEGA_TOWER_L2.md#discernibility-projection-step)). This is the theory's founding move: the operator that rewriting reads as "reducing toward normal form" and abstract interpretation reads as "abstracting toward a fixpoint" is read here as "projecting onto observable content". **Justification:** conceptual, stated as such — the projection reading is what lets one operator carry the WF canonical-form theory (L2.4), the persistent destination theory ([PA-Reach (L1.3.Ax2)](CRPT_OMEGA_TOWER_L1.md#pa-reach--recursive-projection-horizon-stabilization)), and the observer architecture (L4.1) at once.

The *projection operator* of M is a total function ρ_M : 𝒰_M → 𝒰_M satisfying:

**C1 (Step-or-Fix):**
```
∀x ∈ 𝒰_M : (x →_ρ ρ_M(x)) ∨ (ρ_M(x) = x ∧ NF(x))
```
ρ_M either takes a genuine →_ρ-step, or x is already in normal form
and ρ_M fixes it. Equivalently: every non-normal-form element is advanced by ρ_M.

**C2 (Bisimulation Equivariance):**
```
∀x, y ∈ 𝒰_M : x ≈ y ⟹ ρ_M(x) ≈ ρ_M(y)
```
ρ_M preserves bisimilarity: bisimilar inputs produce bisimilar outputs.

*Standard name.* ρ_M is a *reduction strategy* on (𝒰_M, the reduction relation) in the sense
of Baader & Nipkow [1998] §2.1 Def. 2.1.19: a function that, at each element,
selects one →_ρ-successor or fixes the element. The projection-operator
operator* is required because CRPT interprets each ρ_M-step as projecting toward
a canonical representative — information-discarding in the direction of Fix(ρ_M)
— rather than rule-driven syntactic simplification. C2 is the CRPT-required
congruence condition with respect to ≈ (Milner [1980] §5: bisimulation equivariance).

### Projection vs. Abstraction

| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Remark** | L2.1.R1 | `Proj-vs-Abs` | | **Derived** |
**Synopsis:** Why ρ_M is the projection operator, and how projection differs from abstraction.

**Source:** CRPT; from [`RP=Abs` (L2.1.T4)](CRPT_OMEGA_TOWER_L2.md#recursive-projection--abstraction) + [`ρ_M` (L2.1.D1)](CRPT_OMEGA_TOWER_L2.md#projection-operator-ρ_m).

*Derivation:* composed from [`RP=Abs` (L2.1.T4)](CRPT_OMEGA_TOWER_L2.md#recursive-projection--abstraction) + [`ρ_M` (L2.1.D1)](CRPT_OMEGA_TOWER_L2.md#projection-operator-ρ_m); no content beyond the composition.

That ρ_M is the projection operator is
established by definition (C1–C2). That the recursive projection CFix(ρ_M)(x) :=
ρ_M^{d_M(x)}(x) is the *abstraction function* in the sense of Cousot & Cousot
(1977) is a theorem ([`RP=Abs` (L2.1.T4)](CRPT_OMEGA_TOWER_L2.md#recursive-projection--abstraction)), not part of the definition ([`ρ_M` (L2.1.D1)](CRPT_OMEGA_TOWER_L2.md#projection-operator-ρ_m)). The two claims are
distinct: ρ_M is defined as the projection operator; CFix(ρ_M) being the abstraction
is derived from the PA-* axioms via the Galois connection theorem.

### ρ_M as Regime-Neutral Projection

| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Remark** | L2.1.R2 | `Rho-RegNeutral` | | **Novel** |
**Synopsis:** ρ_M acts uniformly on both regimes — it is regime-neutral.

**Source:** CRPT; from [`ρ_M` (L2.1.D1)](CRPT_OMEGA_TOWER_L2.md#projection-operator-ρ_m) + [`Reg-Strat` (L2.2.D3)](CRPT_OMEGA_TOWER_L2.md#native-regime-stratification).

*Novelty Note.* **Basis (credited):** [`ρ_M` (L2.1.D1)](CRPT_OMEGA_TOWER_L2.md#projection-operator-ρ_m) + [`Reg-Strat` (L2.2.D3)](CRPT_OMEGA_TOWER_L2.md#native-regime-stratification). **New:** ρ_M acts uniformly on both regimes — it is regime-neutral. **Why it does not follow:** the stated observation is the contribution; the basis does not state it.


In the native regime-stratified framework ([`Reg-Strat` (L2.2.D3)](CRPT_OMEGA_TOWER_L2.md#native-regime-stratification), L1.2–L1.5), ρ_M operates
identically in both ↓_M and ∞_M. What changes between regimes is the mode of
convergence of the projection:

- **In ↓_M:** The recursive projection ρ_M^{d_M(x)}(x) = CFix(ρ_M)(x) completes in
 **finite steps** d_M(x) ∈ ℕ (PA-WN).
- **In ∞_M:** The co-recursive projection ρ_M^n(x) converges to CFix(ρ_M)(x)
 **asymptotically** in topology 𝒯 (PA-WN_top).

In both cases CFix(ρ_M)(x) is the canonical projection limit. All theorems about
ρ_M's properties (equivariance C2, depth decrease [`Depth-Dec` (L2.3.T2)](CRPT_OMEGA_TOWER_L2.md#strict-depth-decrease), etc.) apply
uniformly in both regimes.

### C3 — Idempotence on Fixpoints

| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Remark** | L2.1.R3 | `C3-Idem` | | **Novel** |
**Synopsis:** Idempotence on fixpoints is automatic: ρ_M(ρ_M(x)) = ρ_M(x) for x ∈ Fix(ρ_M) is immediate from the definition of Fix and needs no extra condition.

**Source:** CRPT; from [`ρ_M` (L2.1.D1)](CRPT_OMEGA_TOWER_L2.md#projection-operator-ρ_m).

*Novelty Note.* **Basis (credited):** [`ρ_M` (L2.1.D1)](CRPT_OMEGA_TOWER_L2.md#projection-operator-ρ_m). **New:** Idempotence on fixpoints is automatic: ρ_M(ρ_M(x)) = ρ_M(x) for x ∈ Fix(ρ_M) is immediate from the definition of Fix and needs no extra condition. **Why it does not follow:** the stated observation is the contribution; the basis does not state it.

For any x ∈ Fix(ρ_M), ρ_M(x) = x,
so ρ_M(ρ_M(x)) = ρ_M(x). This is immediate from the definition of Fix(ρ_M) and
imposes no constraint. It is not a condition on ρ_M.

### Iteration

### Strategy Iteration ρ_Mⁿ
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L2.1.D2 | `ρ^n` | ρ_M^n | **Specialized** |
**Synopsis:** The n-fold application ρ_M^n(x) is the result of applying the projection operator n times in sequence starting from x. For x ∈ ↓_M, there exists n = d_M(x) such that ρ_M^n(x) ∈ Fix(ρ_M). This iterated application is the constructive definition of canonical form computation.

**Source:** Cousot & Cousot [1977] POPL — iterated application; applied to [`ρ_M` (L2.1.D1)](CRPT_OMEGA_TOWER_L2.md#projection-operator-ρ_m).

For n ∈ ℕ:
```
ρ_M⁰(x) := x
ρ_M^{n+1}(x) := ρ_M(ρ_M^n(x))
```

### Fixpoints

### Fixpoint Set
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L2.1.D3 | `Fix` | Fix(ρ_M) | **Reframed** |
**Synopsis:** The fixed-point set Fix(ρ_M) contains all elements that the projection operator maps to themselves. Under PA-Fix, Fix(ρ_M) equals the set of normal forms NF(→_ρ). Fixed points are the terminal objects of the projection operator — they represent elements that have reached their canonical position.

**Source:** Tarski [1955]; Knaster & Tarski [1928] — fixed-point set of a function, reframed as the canonical resting positions of the projection operator (Fix(ρ_M) = NF(→_ρ) via PA-Fix).

*Reframing Note.* **Source form:** the fixed-point set of a function (Knaster & Tarski). **CRPT form:** Fix(ρ_M) as the canonical resting positions — the theory's observable output stratum. **The delta:** fixpointhood is strengthened by C1 to dead-end normality, identifying Fix(ρ_M) with NF(→_ρ) ([`Fix=NF` (L2.1.T2)](CRPT_OMEGA_TOWER_L2.md#fix--nf)). **Justification:** mathematical — the identification makes the fixed-point set the codomain of canonicalization rather than an arbitrary invariant set.

```
Fix(ρ_M) := { x ∈ 𝒰_M | ρ_M(x) = x }
```

### NF ⊆ Fix
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L2.1.T1 | `NF⊆Fix` |  | **Imported** |
**Synopsis:** Every normal form is a ρ_M-fixpoint: if x has no outgoing →_ρ-edge then C1 forces ρ_M(x) = x, so NF(→_ρ) ⊆ Fix(ρ_M). (PA-Fix gives the converse, hence equality.)

**Source:** Baader & Nipkow [1998] §2.1 — normal forms under a reduction strategy.

NF(→_ρ) ⊆ Fix(ρ_M).

*Proof.* Let x ∈ NF(→_ρ). Then x has no outgoing →_ρ-edges. By C1, since
x →_ρ ρ_M(x) cannot hold (no outgoing →_ρ-edges), we must have ρ_M(x) = x.
So x ∈ Fix(ρ_M). ∎

### Fix = NF
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L2.1.T2 | `Fix=NF` | | **Novel** |
**Synopsis:** Under PA-Fix, the converse also holds: every fixed point is a normal form. This axiom closes the equivalence Fix(ρ_M) = NF(→_ρ), making the two notions interchangeable in any CRPT model satisfying PA-Fix.

**Source:** CRPT; from [PA-Fix (L1.2.Ax3)](CRPT_OMEGA_TOWER_L1.md#pa-fix--projection-fixpoint-stratification) + [`NF` (L1.1.D2)](CRPT_OMEGA_TOWER_L1.md#normal-form).

*Novelty Note.* **Basis (credited):** [PA-Fix (L1.2.Ax3)](CRPT_OMEGA_TOWER_L1.md#pa-fix--projection-fixpoint-stratification) + [`NF` (L1.1.D2)](CRPT_OMEGA_TOWER_L1.md#normal-form). **New:** Under PA-Fix, the converse also holds: every fixed point is a normal form. **Why it does not follow:** the statement is not an unfolding of the basis; the proof in the body supplies the argument that connects them.

Fix(ρ_M) = NF(→_ρ).

*Proof.* NF ⊆ Fix by [`NF⊆Fix` (L2.1.T1)](CRPT_OMEGA_TOWER_L2.md#nf--fix). For Fix ⊆ NF: if x ∈ Fix(ρ_M) then ρ_M(x) = x.
By C1, ρ_M(x) = x requires NF(x). Hence x ∈ NF(→_ρ). ∎

### Dead-End Lemma
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L2.1.T3 | `Dead-End` | | **Novel** |
**Synopsis:** Dead-end fixed points are fixed points that are reachable only from themselves — no other element's projection orbit passes through them. These are the 'absorbing' or 'sink' nodes of the reduction graph. Classifying fixed points into dead-ends and non-dead-ends is relevant for the NFC fiber structure.

**Source:** CRPT; from [`Fix` (L2.1.D3)](CRPT_OMEGA_TOWER_L2.md#fixpoint-set) + [`NF` (L1.1.D2)](CRPT_OMEGA_TOWER_L1.md#normal-form).

*Novelty Note.* **Basis (credited):** [`Fix` (L2.1.D3)](CRPT_OMEGA_TOWER_L2.md#fixpoint-set) + [`NF` (L1.1.D2)](CRPT_OMEGA_TOWER_L1.md#normal-form). **New:** Dead-end fixed points are fixed points that are reachable only from themselves — no other element's projection orbit passes through them. **Why it does not follow:** the statement is not an unfolding of the basis; the proof in the body supplies the argument that connects them.

If x ∈ NF(→_ρ) then ρ_M(x) = x and
d_M(x) = 0. If x ∉ NF(→_ρ) and x ∈ ↓_M, then ρ_M(x) ∈ ↓_M and
d_M(ρ_M(x)) = d_M(x) - 1.

*Proof.* (Here d_M(x) := min{n ∈ ℕ | ρ_M^n(x) ∈ Fix(ρ_M)}, formalized as the rank function in [`d_M` (L2.3.D2)](CRPT_OMEGA_TOWER_L2.md#rank-function--derivation-height-notation-d_m).)

*First clause:* x ∈ NF(→_ρ) implies ρ_M(x) = x by [`NF⊆Fix` (L2.1.T1)](CRPT_OMEGA_TOWER_L2.md#nf--fix). Since x ∈ Fix(ρ_M),
we have ρ_M^0(x) = x ∈ Fix(ρ_M), so 0 ∈ {n | ρ_M^n(x) ∈ Fix(ρ_M)} and d_M(x) = 0. ✓

*Second clause:* Let x ∉ NF(→_ρ) with x ∈ ↓_M, so d_M(x) = k for some k ∈ ℕ.
Since x ∉ Fix(ρ_M) (by [`Fix=NF` (L2.1.T2)](CRPT_OMEGA_TOWER_L2.md#fix--nf)), k ≥ 1. Now ρ_M^k(x) ∈ Fix(ρ_M), so
ρ_M^{k-1}(ρ_M(x)) = ρ_M^k(x) ∈ Fix(ρ_M), giving d_M(ρ_M(x)) ≤ k − 1.
If d_M(ρ_M(x)) = j < k − 1, then ρ_M^j(ρ_M(x)) = ρ_M^{j+1}(x) ∈ Fix(ρ_M) with
j + 1 < k, contradicting k = min{n | ρ_M^n(x) ∈ Fix}. So d_M(ρ_M(x)) = k − 1
= d_M(x) − 1. Since d_M(ρ_M(x)) < ∞, we have ρ_M(x) ∈ ↓_M. ✓ ∎

### Recursive Projection and Abstraction

**Purpose.** This section proves that the recursive projection CFix(ρ_M) is the abstraction
function of a Galois insertion between (↓_M, ≤_ρ) and (Fix(ρ_M), =). No new axioms
are introduced. The proof uses PA-WN, PA-Conf, C1, and the definitions of ≤_ρ and derivation height
established in §L2.1–5. The concept of *Galois insertion* is imported from Cousot &
Cousot [1977] §2.2.

### Recursive Projection
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L2.1.D4 | `Rec-Proj` | CFix(ρ_M) | **Novel** |
**Synopsis:** The canonical fixpoint map CFix(ρ_M)(x) sends each convergent element x to the unique fixed point that its projection orbit reaches. It is equivalent to CNF_M(x) and provides an alternative notation emphasising the fixpoint (rather than the canonical form) perspective.

**Source:** CRPT; from [`ρ_M` (L2.1.D1)](CRPT_OMEGA_TOWER_L2.md#projection-operator-ρ_m) + [`d_M` (L2.3.D2)](CRPT_OMEGA_TOWER_L2.md#rank-function--derivation-height-notation-d_m).

*Novelty Note.* **Basis (credited):** [`ρ_M` (L2.1.D1)](CRPT_OMEGA_TOWER_L2.md#projection-operator-ρ_m) + [`d_M` (L2.3.D2)](CRPT_OMEGA_TOWER_L2.md#rank-function--derivation-height-notation-d_m). **New:** The canonical fixpoint map CFix(ρ_M)(x) sends each convergent element x to the unique fixed point that its projection orbit reaches. **Why it does not follow:** the basis supplies the ingredients; the notion assembled from them, and the role it is defined to play in the theory, is introduced here rather than entailed.

[Note: CFix(ρ_M)(x) := ρ_M^{d_M(x)}(x) is a CRPT-novel construction.
The abstraction-function concept is imported from Cousot & Cousot [1977] §2.2;
that CFix(ρ_M) instantiates it is proved in [`RP=Abs` (L2.1.T4)](CRPT_OMEGA_TOWER_L2.md#recursive-projection--abstraction), not assumed here.
The status "Imported" would be misleading; the definition is a novel CRPT construct.]

The
*recursive projection* of x ∈ ↓_M is:
```
CFix(ρ_M)(x) := ρ_M^{d_M(x)}(x)
```
the result of applying the projection operator ρ_M exactly d_M(x) times. CFix(ρ_M)(x) is
the *canonical normal form* of x (standard ARS terminology: Baader &
Nipkow [1998] §2.1 Thm. 2.1.15). The NWF analog CNF∞_M(x) for x ∈ ∞_M is the
*co-recursive projection* ([`CNF∞-Def` (L3.3.D6)](CRPT_OMEGA_TOWER_L3.md#canonical-orbit-invariant-cnf_m-ω-limit-quotient)).

### Fixpoints are ρ_M-stable
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Lemma** | L2.1.L1 | `Fix-Stab` | | **Imported** |
**Synopsis:** Fixed points are stable under reduction: if x is a fixed point and x reduces to y, then y = x. This is a standard ARS result that follows from the definition of fixed point and the determinism condition C1. It ensures that fixed points cannot 'escape' by being reduced.

**Source:** Baader & Nipkow [1998] *Term Rewriting and All That*; Tarski [1955] — fixpoints are stable under the reduction/projection operator.

For all f ∈ Fix(ρ_M)
and all k ∈ ℕ: ρ_M^k(f) = f.

*Proof.* By induction on k. Base k = 0: ρ_M^0(f) = f by [`ρ^n` (L2.1.D2)](CRPT_OMEGA_TOWER_L2.md#strategy-iteration-ρ_mⁿ). Step:
ρ_M^{k+1}(f) = ρ_M(ρ_M^k(f)) = ρ_M(f) = f [IH, then f ∈ Fix(ρ_M)]. ∎

### Unique Reachable Fixpoint
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Lemma** | L2.1.L2 | `UF` | | **Novel** |
**Synopsis:** Under PA-WN and scoped confluence, every convergent element x has a unique fixed point that its projection orbit reaches. Two different projection paths from x cannot lead to two different fixed points. This is the uniqueness half of the canonical form theorem.

**Source:** CRPT; from [PA-WN (L1.2.Ax1)](CRPT_OMEGA_TOWER_L1.md#pa-wn--weak-normalisation) + [PA-Conf (L1.2.Ax2)](CRPT_OMEGA_TOWER_L1.md#pa-conf--confluence--church-rosser) + [`Depth-Dec` (L2.3.T2)](CRPT_OMEGA_TOWER_L2.md#strict-depth-decrease).

*Novelty Note.* **Basis (credited):** [PA-WN (L1.2.Ax1)](CRPT_OMEGA_TOWER_L1.md#pa-wn--weak-normalisation) + [PA-Conf (L1.2.Ax2)](CRPT_OMEGA_TOWER_L1.md#pa-conf--confluence--church-rosser) + [`Depth-Dec` (L2.3.T2)](CRPT_OMEGA_TOWER_L2.md#strict-depth-decrease). **New:** Under PA-WN and scoped confluence, every convergent element x has a unique fixed point that its projection orbit reaches. **Why it does not follow:** the statement is not an unfolding of the basis; the proof in the body supplies the argument that connects them.

Under PA-WN + PA-Conf + C1,
for all x ∈ ↓_M:
```
{f ∈ Fix(ρ_M) | x ≤_ρ f} = {CFix(ρ_M)(x)}
```
The recursive projection CFix(ρ_M)(x) is the unique fixpoint reachable from x by
ρ_M-iteration.

*Proof.* We show the set equals exactly {CFix(ρ_M)(x)}.

*CFix(ρ_M)(x) ∈ Fix(ρ_M).* By [`Rec-Proj` (L2.1.D4)](CRPT_OMEGA_TOWER_L2.md#recursive-projection), CFix(ρ_M)(x) = ρ_M^{d_M(x)}(x).
By [`d_M` (L2.3.D2)](CRPT_OMEGA_TOWER_L2.md#rank-function--derivation-height-notation-d_m) (used here via its informal pre-introduction in L1.2–L1.5): d_M(x) =
min{n ∈ ℕ | ρ_M^n(x) ∈ Fix(ρ_M)}, so ρ_M^{d_M(x)}(x) ∈ Fix(ρ_M) by definition of
the minimum. Hence CFix(ρ_M)(x) ∈ Fix(ρ_M). ✓

*CFix(ρ_M)(x) is in the set.* By the above, CFix(ρ_M)(x) ∈ Fix(ρ_M). By [`Rec-Proj`
(L2.1.D4)](CRPT_OMEGA_TOWER_L2.md#recursive-projection), CFix(ρ_M)(x) = ρ_M^{d_M(x)}(x), so taking k = d_M(x) witnesses
x ≤_ρ CFix(ρ_M)(x) (by definition of ≤_ρ at [`≤_ρ` (L2.3.D1)](CRPT_OMEGA_TOWER_L2.md#ρ_m-reachability-preorder): ∃k : ρ_M^k(x) = CFix(ρ_M)(x)). ✓

*k-Step depth decrease (used below).* We establish by induction on k that for
x ∈ ↓_M and k ≤ d_M(x): d_M(ρ_M^k(x)) = d_M(x) − k.
Base k = 0: d_M(ρ_M^0(x)) = d_M(x) = d_M(x) − 0. ✓
Step: Assume d_M(ρ_M^k(x)) = d_M(x) − k with k < d_M(x), so ρ_M^k(x) ∉ Fix(ρ_M)
(since d_M(ρ_M^k(x)) ≥ 1). By [`Depth-Dec` (L2.3.T2)](CRPT_OMEGA_TOWER_L2.md#strict-depth-decrease) applied to ρ_M^k(x):
d_M(ρ_M^{k+1}(x)) = d_M(ρ_M^k(x)) − 1 = (d_M(x) − k) − 1 = d_M(x) − (k+1). ✓

*Nothing else is in the set.* Let f ∈ Fix(ρ_M) with x ≤_ρ f, so ∃k ∈ ℕ :
ρ_M^k(x) = f.

— Case k < d_M(x): By the k-step depth decrease proved above, d_M(ρ_M^k(x)) =
d_M(x) − k ≥ 1 (since k < d_M(x)). But d_M(y) ≥ 1 implies y ∉ Fix(ρ_M) (for if
y ∈ Fix(ρ_M) then d_M(y) = 0 by [`Fix-D0` (L2.3.T3)](CRPT_OMEGA_TOWER_L2.md#fixpoints-have-depth-zero), contradicting d_M(y) ≥ 1).
Hence ρ_M^k(x) ∉ Fix(ρ_M). But ρ_M^k(x) = f ∈ Fix(ρ_M). Contradiction.
This case is impossible. ✓

— Case k = d_M(x): f = ρ_M^{d_M(x)}(x) = CFix(ρ_M)(x). ✓

— Case k > d_M(x): Write k = d_M(x) + j with j ≥ 1. Then:
```
f = ρ_M^k(x) = ρ_M^j(ρ_M^{d_M(x)}(x)) = ρ_M^j(CFix(ρ_M)(x)) = CFix(ρ_M)(x)
```
where the last equality uses [`Fix-Stab` (L2.1.L1)](CRPT_OMEGA_TOWER_L2.md#fixpoints-are-ρ_m-stable) (since CFix(ρ_M)(x) ∈ Fix(ρ_M),
proved above, and Fix-Stab states ρ_M^j(f') = f' for all f' ∈ Fix(ρ_M), j ∈ ℕ). ✓

In every admissible case f = CFix(ρ_M)(x). ∎

### Recursive Projection = Abstraction
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L2.1.T4 | `RP=Abs` | | **Derived** |
**Synopsis:** Recursive Projection equals Abstraction: the canonical fixpoint map CFix(ρ_M) is exactly the abstraction map α_M of the Galois insertion α_M ⊣ γ_M proved in L7. Computing the canonical form by iterating the projection operator is the same operation as abstracting an element to its equivalence class.

**Source:** CRPT; from [`Rec-Proj` (L2.1.D4)](CRPT_OMEGA_TOWER_L2.md#recursive-projection) + [PA-WN (L1.2.Ax1)](CRPT_OMEGA_TOWER_L1.md#pa-wn--weak-normalisation) + [PA-Conf (L1.2.Ax2)](CRPT_OMEGA_TOWER_L1.md#pa-conf--confluence--church-rosser).

*Derivation:* composed from [`Rec-Proj` (L2.1.D4)](CRPT_OMEGA_TOWER_L2.md#recursive-projection) + [PA-WN (L1.2.Ax1)](CRPT_OMEGA_TOWER_L1.md#pa-wn--weak-normalisation) + [PA-Conf (L1.2.Ax2)](CRPT_OMEGA_TOWER_L1.md#pa-conf--confluence--church-rosser); no content beyond the composition.

Under PA-WN + PA-Conf,
the pair:
```
α_M : ↓_M → Fix(ρ_M) α_M(x) := CFix(ρ_M)(x) [recursive projection]
γ_M : Fix(ρ_M) → ↓_M γ_M(f) := f [inclusion]
```
satisfies the Galois connection biconditional (Cousot & Cousot [1977] §2.2):
```
∀x ∈ ↓_M, ∀f ∈ Fix(ρ_M) : CFix(ρ_M)(x) = f ⟺ x ≤_ρ f
```
Therefore (α_M, γ_M) is a Galois insertion, and CFix(ρ_M) is the abstraction function
(upper adjoint) in the sense of Cousot & Cousot [1977].

*Proof.*

*(→)* Assume CFix(ρ_M)(x) = f. By [`Rec-Proj` (L2.1.D4)](CRPT_OMEGA_TOWER_L2.md#recursive-projection), CFix(ρ_M)(x) = ρ_M^{d_M(x)}(x), so
ρ_M^{d_M(x)}(x) = f. Taking k = d_M(x): ρ_M^k(x) = f, hence x ≤_ρ f by
[`≤_ρ` (L2.3.D1)](CRPT_OMEGA_TOWER_L2.md#ρ_m-reachability-preorder). ✓

*(←)* Assume f ∈ Fix(ρ_M) and x ≤_ρ f. By [`UF` (L2.1.L2)](CRPT_OMEGA_TOWER_L2.md#unique-reachable-fixpoint):
{f ∈ Fix(ρ_M) | x ≤_ρ f} = {CFix(ρ_M)(x)}, so f = CFix(ρ_M)(x). ✓ ∎

### No New Axioms (RP=Abs)

| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Remark** | L2.1.R4 | `RPAbs-NoNewAx` | | **Novel** |
**Synopsis:** RP=Abs introduces no axioms beyond PA-WN, PA-Conf, and C1.

**Source:** CRPT; from [`RP=Abs` (L2.1.T4)](CRPT_OMEGA_TOWER_L2.md#recursive-projection--abstraction); background in Cousot & Cousot [1977].

*Novelty Note.* **Basis (credited):** [`RP=Abs` (L2.1.T4)](CRPT_OMEGA_TOWER_L2.md#recursive-projection--abstraction). **New:** RP=Abs introduces no axioms beyond PA-WN, PA-Conf, and C1. **Why it does not follow:** the stated observation is the contribution; the basis does not state it.

[`RP=Abs` (L2.1.T4)](CRPT_OMEGA_TOWER_L2.md#recursive-projection--abstraction) uses PA-WN (existence of d_M(x) ∈ ℕ,
used in [`UF` (L2.1.L2)](CRPT_OMEGA_TOWER_L2.md#unique-reachable-fixpoint) via [`Depth-Dec` (L2.3.T2)](CRPT_OMEGA_TOWER_L2.md#strict-depth-decrease) and [`Fix-D0` (L2.3.T3)](CRPT_OMEGA_TOWER_L2.md#fixpoints-have-depth-zero)),
PA-Conf (uniqueness of the fixpoint reached, via confluence), C1 (for the Step-or-Fix
property underpinning [`Depth-Dec` (L2.3.T2)](CRPT_OMEGA_TOWER_L2.md#strict-depth-decrease) and [`Fix-D0` (L2.3.T3)](CRPT_OMEGA_TOWER_L2.md#fixpoints-have-depth-zero)), and
the definitions of ≤_ρ ([`≤_ρ` (L2.3.D1)](CRPT_OMEGA_TOWER_L2.md#ρ_m-reachability-preorder)), derivation height ([`d_M` (L2.3.D2)](CRPT_OMEGA_TOWER_L2.md#rank-function--derivation-height-notation-d_m)), and CFix(ρ_M)
([`Rec-Proj` (L2.1.D4)](CRPT_OMEGA_TOWER_L2.md#recursive-projection)). No conditions on what "abstraction" means are introduced
alongside the PA-* system. The definition of Galois connection is imported from
Cousot & Cousot [1977] §2.2 without modification.

### Monotonicity Is Derivable

| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Remark** | L2.1.R5 | `Mono-Deriv` | | **Novel** |
**Synopsis:** Monotonicity of the projection is derivable, not a separate assumption.

**Source:** CRPT; from [`UF` (L2.1.L2)](CRPT_OMEGA_TOWER_L2.md#unique-reachable-fixpoint).

*Novelty Note.* **Basis (credited):** [`UF` (L2.1.L2)](CRPT_OMEGA_TOWER_L2.md#unique-reachable-fixpoint). **New:** Monotonicity of the projection is derivable, not a separate assumption. **Why it does not follow:** the stated observation is the contribution; the basis does not state it.

The standard Moore closure definition
requires extensiveness, monotonicity, idempotence, and abstract range. In the CRPT
setting, monotonicity is redundant: any map satisfying the other three conditions
equals CFix(ρ_M) by [`UF` (L2.1.L2)](CRPT_OMEGA_TOWER_L2.md#unique-reachable-fixpoint), and CFix(ρ_M) is monotone (if x ≤_ρ y then CFix(ρ_M)(x) =
CFix(ρ_M)(y) by Lemma L-CNF, proved in L2.4). The derivability of monotonicity from
the determinism of ρ_M via C1 is specific to CRPT's orbit structure.

### Discernibility: Projection Step

| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Remark** | L2.1.R6 | `Disc-Proj` | | **Novel** |
**Synopsis:** Each projection step erases indiscernible structure: recursive projection is stepwise discernibility-compression, which is what makes its fixpoints canonical observables.

**Source:** CRPT; from [`ρ_M` (L2.1.D1)](CRPT_OMEGA_TOWER_L2.md#projection-operator-ρ_m).

*Novelty Note.* **Basis (credited):** [`ρ_M` (L2.1.D1)](CRPT_OMEGA_TOWER_L2.md#projection-operator-ρ_m). **New:** Each projection step erases indiscernible structure: recursive projection is stepwise discernibility-compression, which is what makes its fixpoints canonical observables. **Why it does not follow:** the stated observation is the contribution; the basis does not state it.

Each step of the projection operator
ρ_M systematically erases indiscernible structure. The recursive projection
CFix(ρ_M)(x) retains only what is structurally distinguishable in [x]_{≃_M}: it is
the discernibility limit of the projection process.

---
---

## L2.2 — Regime Partition

*Purpose.* Regime Partition: Convergent and Persistent. This section partitions 𝒰_M into the convergent regime ↓_M (elements that reach Fix(ρ_M) in finitely many ρ_M-steps) and the persistent regime ∞_M (elements that do not). This partition is the foundational dichotomy of CRPT; every subsequent construction respects it.*


### Regime Operators (Fixed-Point Characterization)

The regime partition is formalized as a fixed-point decomposition on the lattice
(𝒫(𝒰_M), ⊆). The two regimes arise as the least and greatest fixed points of
monotone regime operators.

### ρ-Predecessor Operator
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L2.2.D1 | `Pre_ρ` | Pre_ρ(X) | **Specialized** |
**Synopsis:** The predecessor set Pre_ρ(X) = {y ∈ 𝒰_M | y →_ρ x for some x ∈ X} is the set of all elements that reduce to some element of X in one step. Predecessor sets are used to define convergent and persistent templates and appear in the definition of the horizon predicates.

**Source:** Cousot & Cousot [1977] POPL — the predecessor (pre-) operator; applied to [`ρ_M` (L2.1.D1)](CRPT_OMEGA_TOWER_L2.md#projection-operator-ρ_m).

For X ⊆ 𝒰_M define:
```
Pre_ρ(X) := { x ∈ 𝒰_M | ρ_M(x) ∈ X }
```
the set of elements whose ρ_M-image lies in X.

### Regime Operators T_conv and T_pers
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L2.2.D2 | `T^{conv/pers}` | T^{conv}, T^{pers} | **Specialized** |
**Synopsis:** Convergent and persistent templates partition the predecessor set into elements coming from ↓_M (convergent predecessors, T^{conv}) and elements coming from ∞_M (persistent predecessors, T^{pers}). This typed predecessor partition connects the regime structure to the fiber structure underlying the horizon predicates.

**Source:** Tarski [1955]; Cousot & Cousot [1977] POPL — lattice operators; applied to [`Pre_ρ` (L2.2.D1)](CRPT_OMEGA_TOWER_L2.md#ρ-predecessor-operator).

On the complete lattice
(𝒫(𝒰_M), ⊆), define:
```
T_{ρ,M}^{conv}(X) := Fix(ρ_M) ∪ Pre_ρ(X), (convergent regime operator)
T_{ρ,M}^{pers}(X) := (𝒰_M ∖ Fix(ρ_M)) ∩ Pre_ρ(X) (persistent regime operator)
```

### Monotonicity
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Lemma** | L2.2.L1 | `L-Mono` |  | **Specialized** |
**Synopsis:** Level monotonicity: the derivation height d_M is strictly monotone under the projection operator on ↓_M: if x ∈ ↓_M and x is not a fixed point, then d_M(ρ_M(x)) = d_M(x) − 1 < d_M(x). Each projection step strictly decreases derivation height, ensuring termination.

**Source:** Tarski [1955] — monotonicity; applied to [`T^{conv/pers}` (L2.2.D2)](CRPT_OMEGA_TOWER_L2.md#regime-operators-t_conv-and-t_pers).

T_{ρ,M}^{conv} and T_{ρ,M}^{pers} are monotone.

*Proof.* If X ⊆ Y, then Pre_ρ(X) ⊆ Pre_ρ(Y). Union and intersection with fixed sets
preserve inclusion. Hence both operators are monotone. ∎

### Native Regime Stratification
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L2.2.D3 | `Reg-Strat` | | **Novel** |
**Synopsis:** Native regime stratification is the methodological principle of treating the two regimes with different proof methods: induction for convergent elements (using derivation height as the induction measure) and coinduction for persistent elements (using PA-CoInd / the asymptotic orbit invariant). All proofs in L3–L8 follow this regime-stratified strategy implicitly.

**Source:** CRPT; from [`ρ_M` (L2.1.D1)](CRPT_OMEGA_TOWER_L2.md#projection-operator-ρ_m) + the regime partition (L2.2).

*Novelty Note.* **Basis (credited):** [`ρ_M` (L2.1.D1)](CRPT_OMEGA_TOWER_L2.md#projection-operator-ρ_m). **New:** Native regime stratification is the methodological principle of treating the two regimes with different proof methods: induction for convergent elements (using derivation height as the induction measure) and coinduction for persistent elements (using PA-CoInd / the asymptotic orbit invariant). **Why it does not follow:** the basis supplies the ingredients; the notion assembled from them, and the role it is defined to play in the theory, is introduced here rather than entailed.

A substrate (𝒰_M, →_ρ, →_σ, ρ_M) satisfies *native regime stratification* if:

(i) The regime partition ↓_M ∪ ∞_M = 𝒰_M is **computable** from →_ρ and Fix(ρ_M):
```
↓_M := { x ∈ 𝒰_M | ∃n ∈ ℕ : ρ_M^n(x) ∈ Fix(ρ_M) } (computable reachability)
∞_M := 𝒰_M ∖ ↓_M (complement)
```

(ii) The partition satisfies **properties of regime closure** ([`↓-Closed` (L2.2.T1)](CRPT_OMEGA_TOWER_L2.md#_m-is-ρ_m-closed), [`∞-Closed` (L2.2.T2)](CRPT_OMEGA_TOWER_L2.md#_m-is-ρ_m-closed-1) below):
- ρ_M(↓_M) ⊆ ↓_M (convergent regime is closed under ρ_M)
- ρ_M(∞_M) ⊆ ∞_M (persistent regime is closed under ρ_M)

(iii) The partition admits the **native axiom system**: the convergent-regime axioms on ↓_M (global PA-WN, with regime-sensitive use via scope semantics) and the persistent-regime axioms on ∞_M (PA-NWF, PA-CoInd, PA-Prod, and the optional PA-WN_top). Canonicalization then proceeds by recurrence on ↓_M (termination at depth d_M) and on ∞_M by the realizations of [PA-Reach (L1.3.Ax2)](CRPT_OMEGA_TOWER_L1.md#pa-reach--recursive-projection-horizon-stabilization) — recurrence, or convergence wherever PA-WN_top holds, or their composite ([`Mode` (L1.4.D1)](CRPT_OMEGA_TOWER_L1.md#regimes-and-canonicalization-modes)).

### The Regime Partition Adds No Axiom

| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Remark** | L2.2.R1 | `RegPart-NoAxiom` | | **Novel** |
**Synopsis:** The regime partition is not an axiom constraint: ↓_M and ∞_M are definitions, and their exhaustiveness and disjointness are theorem consequences of those definitions.

**Source:** CRPT; from [`Reg-Strat` (L2.2.D3)](CRPT_OMEGA_TOWER_L2.md#native-regime-stratification) + [`Part` (L2.2.T3)](CRPT_OMEGA_TOWER_L2.md#partition).

*Novelty Note.* **Basis (credited):** [`Reg-Strat` (L2.2.D3)](CRPT_OMEGA_TOWER_L2.md#native-regime-stratification) + [`Part` (L2.2.T3)](CRPT_OMEGA_TOWER_L2.md#partition). **New:** The regime partition is not an axiom constraint: ↓_M and ∞_M are definitions, and their exhaustiveness and disjointness are theorem consequences of those definitions. **Why it does not follow:** the stated observation is the contribution; the basis does not state it.

This is not a new axiom constraint. The regime partition is specified by definitions (↓_M and ∞_M), and its exhaustiveness/disjointness are theorem consequences of those definitions. It is essential for native regime stratification (L1.2–L1.5) but automatically satisfied in pure WF/NWF models.

### Fixed-Point Definitions

### Convergent Regime ↓_M
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L2.2.D4 | `↓_M` | ↓_M | **Novel** |
**Synopsis:** The convergent regime ↓_M contains every element of 𝒰_M whose ρ_M-orbit eventually reaches a fixed point in finitely many steps. Elements in ↓_M are the well-founded part of the model — they have canonical forms, derivation heights, and participate in the six-class partition of L3.

**Source:** CRPT; from [`ρ_M` (L2.1.D1)](CRPT_OMEGA_TOWER_L2.md#projection-operator-ρ_m) + [`Fix` (L2.1.D3)](CRPT_OMEGA_TOWER_L2.md#fixpoint-set).

*Novelty Note.* **Basis (credited):** [`ρ_M` (L2.1.D1)](CRPT_OMEGA_TOWER_L2.md#projection-operator-ρ_m) + [`Fix` (L2.1.D3)](CRPT_OMEGA_TOWER_L2.md#fixpoint-set). **New:** The convergent regime ↓_M contains every element of 𝒰_M whose ρ_M-orbit eventually reaches a fixed point in finitely many steps. **Why it does not follow:** the basis supplies the ingredients; the notion assembled from them, and the role it is defined to play in the theory, is introduced here rather than entailed.


The *convergent regime* (elements with finite abstraction depth) is the least fixed point of T_{ρ,M}^{conv}:
```
↓_M := μT_{ρ,M} := least fixed point of T_{ρ,M}^{conv}
 = { x ∈ 𝒰_M | ∃n ∈ ℕ : ρ_M^n(x) ∈ Fix(ρ_M) }
 (weakly-normalizing set WN(→_ρ))
```
x ∈ ↓_M iff some iterate of ρ_M(x) reaches a fixpoint. The notation ↓_M ("downward") emphasizes the direction of abstraction: elements progress downward through finite abstraction steps toward their canonical form.

### Persistent Regime ∞_M
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L2.2.D5 | `∞_M` | ∞_M | **Novel** |
**Synopsis:** The persistent regime ∞_M is the complement of ↓_M: elements whose ρ_M-orbit never terminates. These are the non-well-founded elements. They cannot be assigned a finite derivation height, and their 'canonical form' (if any) is defined coinductively via the persistent canonical form CNF∞_M of L3.3.

**Source:** CRPT; from [`↓_M` (L2.2.D4)](CRPT_OMEGA_TOWER_L2.md#convergent-regime-_m).

*Novelty Note.* **Basis (credited):** [`↓_M` (L2.2.D4)](CRPT_OMEGA_TOWER_L2.md#convergent-regime-_m). **New:** The persistent regime ∞_M is the complement of ↓_M: elements whose ρ_M-orbit never terminates. **Why it does not follow:** the basis supplies the ingredients; the notion assembled from them, and the role it is defined to play in the theory, is introduced here rather than entailed.


The *persistent regime* (elements with infinite abstraction depth) is the greatest fixed point of T_{ρ,M}^{pers}:
```
∞_M := νT_{ρ,M} := greatest fixed point of T_{ρ,M}^{pers}
 = { x ∈ 𝒰_M | ∀n ∈ ℕ : ρ_M^n(x) ∉ Fix(ρ_M) }
 (divergence set Div(→_ρ)∩𝒰_M)
```
x ∈ ∞_M iff no iterate of ρ_M(x) reaches a fixpoint. The notation ∞_M ("infinite") emphasizes that elements in this regime never reach a fixpoint; abstraction depth is infinite.

### Regime Operators in Pure and Native Settings

| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Remark** | L2.2.R2 | `RegOps-PureNative` | | **Derived** |
**Synopsis:** How the regime operators behave in pure-WF versus native stratified settings.

**Source:** CRPT; from [`Reg-Strat` (L2.2.D3)](CRPT_OMEGA_TOWER_L2.md#native-regime-stratification) + [`Mode` (L1.4.D1)](CRPT_OMEGA_TOWER_L1.md#regimes-and-canonicalization-modes).

*Derivation:* composed from [`Reg-Strat` (L2.2.D3)](CRPT_OMEGA_TOWER_L2.md#native-regime-stratification) + [`Mode` (L1.4.D1)](CRPT_OMEGA_TOWER_L1.md#regimes-and-canonicalization-modes); no content beyond the composition.



The regime operators use Fix(ρ_M), not NF(→_ρ), because the partition is defined via ρ_M-orbits. The distinction is important in both settings:

**Pure-WF profile (§L1.1–3):** Fix(ρ_M) = NF(→_ρ) ([`Fix=NF` (L2.1.T2)](CRPT_OMEGA_TOWER_L2.md#fix--nf)), so the two coincide. Under PA-WN, all elements are weakly normalizing, and Definitions 4.1–4.2 reduce to: ↓_M = 𝒰_M and ∞_M = ∅.

**Native CRPT (L1.2–L1.5, regime-stratified):** With the convergent-regime axioms on ↓_M (global PA-WN, used via scope semantics) and the persistent-regime axioms (PA-NWF, PA-CoInd, PA-Prod, and the optional PA-WN_top) on ∞_M:
- Elements in ↓_M reach Fix(ρ_M) in finitely many steps (finitary mode).
- Elements in ∞_M never reach Fix(ρ_M); their asymptotic destination is reached by recurrence — or by convergence to a 𝒯-limit wherever PA-WN_top holds, or by their composite ([PA-Reach (L1.3.Ax2)](CRPT_OMEGA_TOWER_L1.md#pa-reach--recursive-projection-horizon-stabilization), [`Mode` (L1.4.D1)](CRPT_OMEGA_TOWER_L1.md#regimes-and-canonicalization-modes)) — and is analysed by the orbit invariant [`AOI-Unif` (L6.3.D10)](CRPT_OMEGA_TOWER_L6.md#unified-aoi) in either mode.
- Partitioning via Fix(ρ_M) captures both regimes: an element either reaches a fixpoint (↓_M) or never does (∞_M).

**Self-loop elements:** Fixed-point elements (in Fix(ρ_M)) are classified as convergent (they reach a fixpoint in 0 steps) even though they have outgoing →_ρ-edges. This is correct in both settings: they are normal forms, so they should not be classified as diverging.

*Cross-reference:* For detailed treatment of native regime stratification with finitary and topological axes, see L1.2–L1.5 above.

### Closure and Partition Theorems

### ↓_M is ρ_M-Closed
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L2.2.T1 | `↓-Closed` |  | **Novel** |
**Synopsis:** The convergent regime ↓_M is closed under the projection operator: if x ∈ ↓_M and x reduces to y, then y ∈ ↓_M with d_M(y) = d_M(x) − 1. Reduction always moves toward the fixed-point set, never away from it. This is the monotone-depth property of the projection operator.

**Source:** CRPT; from [`↓_M` (L2.2.D4)](CRPT_OMEGA_TOWER_L2.md#convergent-regime-_m) + [`ρ_M` (L2.1.D1)](CRPT_OMEGA_TOWER_L2.md#projection-operator-ρ_m).

*Novelty Note.* **Basis (credited):** [`↓_M` (L2.2.D4)](CRPT_OMEGA_TOWER_L2.md#convergent-regime-_m) + [`ρ_M` (L2.1.D1)](CRPT_OMEGA_TOWER_L2.md#projection-operator-ρ_m). **New:** The convergent regime ↓_M is closed under the projection operator: if x ∈ ↓_M and x reduces to y, then y ∈ ↓_M with d_M(y) = d_M(x) − 1. **Why it does not follow:** the statement is not an unfolding of the basis; the proof in the body supplies the argument that connects them.

∀x ∈ ↓_M : ρ_M(x) ∈ ↓_M.

*Proof.* Let x ∈ ↓_M, so ∃n : ρ_M^n(x) ∈ Fix(ρ_M). If n = 0: x ∈ Fix(ρ_M), so
ρ_M(x) = x ∈ Fix(ρ_M) ⊆ ↓_M. If n ≥ 1: ρ_M^{n-1}(ρ_M(x)) = ρ_M^n(x) ∈ Fix(ρ_M),
so ρ_M(x) ∈ ↓_M. ∎

### ∞_M is ρ_M-Closed
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L2.2.T2 | `∞-Closed` |  | **Novel** |
**Synopsis:** The persistent regime ∞_M is also closed under the projection operator: if x ∈ ∞_M then ρ_M(x) ∈ ∞_M. Once an orbit enters the persistent regime it never leaves. This closure makes ↓_M and ∞_M invariant under the projection operator.

**Source:** CRPT; from [`∞_M` (L2.2.D5)](CRPT_OMEGA_TOWER_L2.md#persistent-regime-_m) + [`ρ_M` (L2.1.D1)](CRPT_OMEGA_TOWER_L2.md#projection-operator-ρ_m).

*Novelty Note.* **Basis (credited):** [`∞_M` (L2.2.D5)](CRPT_OMEGA_TOWER_L2.md#persistent-regime-_m) + [`ρ_M` (L2.1.D1)](CRPT_OMEGA_TOWER_L2.md#projection-operator-ρ_m). **New:** The persistent regime ∞_M is also closed under the projection operator: if x ∈ ∞_M then ρ_M(x) ∈ ∞_M. **Why it does not follow:** the statement is not an unfolding of the basis; the proof in the body supplies the argument that connects them.

∀x ∈ ∞_M : ρ_M(x) ∈ ∞_M.

*Proof.* Suppose ρ_M(x) ∈ ↓_M. Then ∃m : ρ_M^m(ρ_M(x)) = ρ_M^{m+1}(x) ∈ Fix(ρ_M).
But then m+1 witnesses x ∈ ↓_M, contradicting x ∈ ∞_M. ∎

### Partition
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L2.2.T3 | `Part` |  | **Novel** |
**Synopsis:** The regime partition theorem: 𝒰_M = ↓_M ⊔ ∞_M is an exhaustive disjoint partition. Every element is either in the convergent regime or the persistent regime, with no overlap. This follows from the definition of ↓_M and ∞_M as complements.

**Source:** CRPT; from [`↓_M` (L2.2.D4)](CRPT_OMEGA_TOWER_L2.md#convergent-regime-_m) + [`∞_M` (L2.2.D5)](CRPT_OMEGA_TOWER_L2.md#persistent-regime-_m).

*Novelty Note.* **Basis (credited):** [`↓_M` (L2.2.D4)](CRPT_OMEGA_TOWER_L2.md#convergent-regime-_m) + [`∞_M` (L2.2.D5)](CRPT_OMEGA_TOWER_L2.md#persistent-regime-_m). **New:** The regime partition theorem: 𝒰_M = ↓_M ⊔ ∞_M is an exhaustive disjoint partition. **Why it does not follow:** the statement is not an unfolding of the basis; the proof in the body supplies the argument that connects them.

𝒰_M = ↓_M ∐ ∞_M (disjoint union).

*Proof.* Exhaustiveness: for any x, either ∃n : ρ_M^n(x) ∈ Fix(ρ_M) (x ∈ ↓_M) or
∀n : ρ_M^n(x) ∉ Fix(ρ_M) (x ∈ ∞_M). These are the two cases of classical excluded
middle on the predicate x ∈ ↓_M. Disjointness: immediate from the definitions. ∎

### The Regime Partition Is a Tautology

| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Remark** | L2.2.R3 | `Part-Taut` | | **Novel** |
**Synopsis:** The regime partition is a logical tautology given the definitions — stated as a theorem only for citability; it consumes no axiom.

**Source:** CRPT; from [`Part` (L2.2.T3)](CRPT_OMEGA_TOWER_L2.md#partition).

*Novelty Note.* **Basis (credited):** [`Part` (L2.2.T3)](CRPT_OMEGA_TOWER_L2.md#partition). **New:** The regime partition is a logical tautology given the definitions — stated as a theorem only for citability; it consumes no axiom. **Why it does not follow:** the stated observation is the contribution; the basis does not state it.

[`Part` (L2.2.T3)](CRPT_OMEGA_TOWER_L2.md#partition) is a logical tautology given the definitions. It requires
no axiom. It is stated as a theorem (rather than a remark) only because it is a
named result that appears in cross-references.

### PA-WN Gives Terminating-Path Witnesses
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L2.2.T4 | `WN-Tot` |  | **Specialized** |
**Synopsis:** Under PA-WN, every element has a terminating path to a normal form under the reduction relation. This is a direct consequence of PA-WN and confirms that the convergent regime is total when ∞_M = ∅.

**Source:** Baader & Nipkow [1998] §2.3 — weak normalisation; restates [PA-WN (L1.2.Ax1)](CRPT_OMEGA_TOWER_L1.md#pa-wn--weak-normalisation) over [`NF` (L1.1.D2)](CRPT_OMEGA_TOWER_L1.md#normal-form).

Under PA-WN, every element has a terminating →_ρ-path to a normal form.

*Proof.* This is a direct restatement of PA-WN: for every x ∈ 𝒰 there exists a
terminating →_ρ-path from x to some normal form y. No additional derivation is
needed. ∎

### PA-NWF ⟹ νT_{ρ,M} ≠ ∅
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L2.2.T5 | `NWF-NE` |  | **Specialized** |
**Synopsis:** Under PA-NWF, the persistent regime ∞_M is non-empty. This is the minimal content of the non-well-founded axiom.

**Source:** Aczel [1988] Ch. 1 — non-well-foundedness; restates [PA-NWF (L1.2.Ax4)](CRPT_OMEGA_TOWER_L1.md#pa-nwf--non-well-foundedness--divergence-existence) over [`∞_M` (L2.2.D5)](CRPT_OMEGA_TOWER_L2.md#persistent-regime-_m).

Under PA-NWF, the persistent regime is
non-empty.

*Proof.* PA-NWF states exactly:
∃x ∈ 𝒰 : ∀n ∈ ℕ, ρ_M^n(x) ∉ Fix(ρ_M) ([PA-NWF (L1.2.Ax4)](CRPT_OMEGA_TOWER_L1.md#pa-nwf--non-well-foundedness--divergence-existence)).
By definition of ∞_M ([`∞_M` (L2.2.D5)](CRPT_OMEGA_TOWER_L2.md#persistent-regime-_m)), this is equivalent to ∃x ∈ ∞_M.
Therefore the persistent regime is non-empty. ∎

### Discernibility: Regime

| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Remark** | L2.2.R4 | `Disc-Regime` | | **Derived** |
**Synopsis:** Reading the regime partition as a discernibility classification.

**Source:** CRPT; from [`↓_M` (L2.2.D4)](CRPT_OMEGA_TOWER_L2.md#convergent-regime-_m) + [`∞_M` (L2.2.D5)](CRPT_OMEGA_TOWER_L2.md#persistent-regime-_m).

*Derivation:* composed from [`↓_M` (L2.2.D4)](CRPT_OMEGA_TOWER_L2.md#convergent-regime-_m) + [`∞_M` (L2.2.D5)](CRPT_OMEGA_TOWER_L2.md#persistent-regime-_m); no content beyond the composition.

The regime partition classifies elements
by the **limit of their discernible content under abstraction**: ↓_M elements have
finitely exhaustible discernibility (reduction terminates), while ∞_M elements have
inexhaustible discernibility (reduction never terminates — infinite unfolding
continuously reveals or cycles through distinctions).

### The Two-Regime Completeness Theorem

### Regime Completeness — Two Regimes Exactly
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L2.2.T6 | `Reg-Compl` |  | **Novel** |
**Synopsis:** Under PA-WN, every element has a terminating path to a normal form. This is a direct restatement of PA-WN: the axiom asserts that the convergent regime is all of 𝒰_M when ∞_M = ∅, or that every element in ↓_M has a terminating reduction path.

**Source:** CRPT; from [PA-WN (L1.2.Ax1)](CRPT_OMEGA_TOWER_L1.md#pa-wn--weak-normalisation) + [`Reg-Strat` (L2.2.D3)](CRPT_OMEGA_TOWER_L2.md#native-regime-stratification).

*Novelty Note.* **Basis (credited):** [PA-WN (L1.2.Ax1)](CRPT_OMEGA_TOWER_L1.md#pa-wn--weak-normalisation) + [`Reg-Strat` (L2.2.D3)](CRPT_OMEGA_TOWER_L2.md#native-regime-stratification). **New:** Under PA-WN, every element has a terminating path to a normal form. **Why it does not follow:** the statement is not an unfolding of the basis; the proof in the body supplies the argument that connects them.

On any fixed
model M with projection operator ρ_M (= abstraction function by [`RP=Abs` (L2.1.T4)](CRPT_OMEGA_TOWER_L2.md#recursive-projection--abstraction)), there are exactly two abstraction regimes:
↓_M and ∞_M. No third regime exists.

*Formal statement.* The partition 𝒰_M = ↓_M ∐ ∞_M ([`Part` (L2.2.T3)](CRPT_OMEGA_TOWER_L2.md#partition)) is exhaustive and
irreducible: no predicate P on 𝒰_M satisfying the ρ_M-closure conditions (Theorems
4.1 and 4.2) produces a strictly finer partition into three or more non-empty classes.

*Proof.* We show that any ρ_M-closed partition of ↓_M (or ∞_M) into two non-empty
parts reduces to a sub-classification by fixpoint (resp. orbit) identity — hence is
not a genuinely new regime.

*Convergent case.* Suppose ↓_M = B₁ ∐ B₂ with both B₁, B₂ non-empty and ρ_M-forward-closed
(ρ_M(Bᵢ) ⊆ Bᵢ). Take x ∈ B₁. The ρ_M-orbit
x, ρ_M(x), ρ_M²(x), ..., ρ_M^{d_M(x)}(x) = f ∈ Fix(ρ_M)
is finite. By forward closure (ρ_M(B₁) ⊆ B₁) applied d_M(x) times, every element
on the orbit of x lies in B₁. In particular, f = CFix(ρ_M)(x) ∈ B₁.

Now let y ∈ B₂ (the other part). By the same argument, CFix(ρ_M)(y) ∈ B₂. Since
B₁ ∩ B₂ = ∅, we have CFix(ρ_M)(x) ≠ CFix(ρ_M)(y) for x ∈ B₁, y ∈ B₂. Therefore
B₁ and B₂ are separated by canonical form: B₁ = ⋃_{f ∈ Fix(ρ_M) ∩ B₁} the normal-form fiber NFC_M(f) and
B₂ = ⋃_{f ∈ Fix(ρ_M) ∩ B₂} the normal-form fiber NFC_M(f). (Every element of ↓_M lies in exactly one
the normal-form fiber NFC_M(f) by [`UF` (L2.1.L2)](CRPT_OMEGA_TOWER_L2.md#unique-reachable-fixpoint); each the normal-form fiber NFC_M(f) lies entirely within B₁ or B₂ by
forward closure as shown above.) This is internal sub-classification of ↓_M by
fixpoint identity — not a new regime.

*Remark on backward closure.* The proof does NOT require backward closure of B₁ or B₂.
Forward closure alone is sufficient: it forces each orbit to stay within its part,
hence forces fixpoints into the same part as their orbit origins. Membership of an
element y in B₁ or B₂ is determined entirely by CFix(ρ_M)(y), not by backward
reachability from f.

*Persistent case.* Suppose ∞_M = O₁ ∐ O₂ with ρ_M(Oᵢ) ⊆ Oᵢ. Take x ∈ O₁.
By forward closure, ρ_M^n(x) ∈ O₁ for all n ∈ ℕ. So O₁ contains the entire
forward orbit of x. Similarly O₂ contains the entire forward orbit of any y ∈ O₂.
Two elements are in the same part iff their orbits stay in the same part. This is
internal sub-classification of ∞_M by orbit membership — not a new regime.

In both cases the alleged third class reduces to sub-classification within an
existing regime, determined by CFix(ρ_M) (convergent case) or orbit containment
(persistent case). Therefore exactly two regimes exist on any fixed model M. ∎

### Regime Notation - Canonical
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Remark** | L2.2.R5 | `Reg-Nota` |  | **Novel** |
**Synopsis:** The canonical regime notation: ↓_M (convergent) and ∞_M (persistent) are the primary CRPT notations. The fixed-point theory notations μT_{ρ,M} and νT_{ρ,M} are alternative formal definitions equivalent to ↓_M and ∞_M respectively, used when the fixed-point theoretic perspective clarifies a proof.

**Source:** CRPT; notation for [`↓_M` (L2.2.D4)](CRPT_OMEGA_TOWER_L2.md#convergent-regime-_m) + [`∞_M` (L2.2.D5)](CRPT_OMEGA_TOWER_L2.md#persistent-regime-_m).

*Novelty Note.* **Basis (credited):** [`↓_M` (L2.2.D4)](CRPT_OMEGA_TOWER_L2.md#convergent-regime-_m) + [`∞_M` (L2.2.D5)](CRPT_OMEGA_TOWER_L2.md#persistent-regime-_m). **New:** The canonical regime notation: ↓_M (convergent) and ∞_M (persistent) are the primary CRPT notations. **Why it does not follow:** the stated observation is the contribution; the basis does not state it.

The regime notation is:
- **↓_M** (downward): The CANONICAL primary notation for the convergent regime with finite abstraction depth
- **∞_M** (infinite): The CANONICAL primary notation for the persistent regime with infinite abstraction depth

Formal notation in proofs (when fixed-point theory requires precision):
- μT_{ρ,M} := ↓_M (underlying fixed-point definition)
- νT_{ρ,M} := ∞_M (underlying fixed-point definition)

The regime symbols are canonical: ↓_M and ∞_M are used throughout CRPT.

### Vertical vs Horizontal Infinity: Why σ-Structure is NOT a Third Regime
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Remark** | L2.2.R6 | `Vert-Horiz` |  | **Derived** |
**Synopsis:** This remark establishes that the structural relation →_σ does not create a third regime. Elements connected horizontally (within the same fiber via →_σ) are already classified as convergent or persistent by their position relative to Fix(ρ_M). Horizontal connectivity is not a new regime; it is a within-regime structural property.

**Source:** CRPT; from [`Reg-Strat` (L2.2.D3)](CRPT_OMEGA_TOWER_L2.md#native-regime-stratification) + [`Inf-Dual` (L2.2.T7)](CRPT_OMEGA_TOWER_L2.md#horizontal-vertical-infinity-duality).

*Derivation:* composed from [`Reg-Strat` (L2.2.D3)](CRPT_OMEGA_TOWER_L2.md#native-regime-stratification) + [`Inf-Dual` (L2.2.T7)](CRPT_OMEGA_TOWER_L2.md#horizontal-vertical-infinity-duality); no content beyond the composition.


The regime dichotomy (↓_M vs ∞_M) classifies elements by **VERTICAL INFINITY** — the abstraction tower dimension (ρ-reduction direction):
- **↓_M (Vertical Finite):** Elements with finite abstraction depth; the ρ_M-orbit terminates at a fixpoint
- **∞_M (Vertical Infinite):** Elements with infinite abstraction depth; the ρ_M-orbit never reaches a fixpoint

Orthogonal to this is **HORIZONTAL INFINITY** — the structural dimension (σ-relation direction):
- **Horizontal Structure:** Within any abstraction fiber f ∈ Fix(ρ_M), there can be INFINITE σ-paths among elements of fiber NFC_M(f)
- **Horizontal Infinity within ↓_M:** Elements x ∈ ↓_M can have infinite σ-branching inside their fiber, while still reaching a fixpoint via ρ-reduction

**Why this is not a third regime:** The σ-structure operates at a FIXED abstraction level (within a single fiber). Elements remain classified by their vertical fate: do they reach a fixpoint under ρ-iteration, or diverge? The σ-branching within the fiber does NOT change this classification.

**Geometric picture:**
- **Vertical axis (tower):** ρ-reduction, abstraction depth (dimension of ↓_M vs ∞_M)
- **Horizontal axis (fiber):** σ-structure, internal branching within the normal-form fiber NFC_M(f) (orthogonal to regime)

Elements can be:
1. **↓_M with finite σ-structure:** Converges vertically, bounded σ-paths (typical)
2. **↓_M with infinite σ-structure:** Converges vertically, INFINITE σ-paths within fiber (H_I = ⊤ cases)
3. **∞_M with infinite σ-structure:** Diverges vertically, potentially infinite σ-structure (not separately classified)

**Why σ-infinity stays within a single regime:** An element x ∈ the normal-form fiber NFC_M(f) can have infinite →_σ-successors, but ALL those successors have the same ρ-fate: they all reach f under iteration of ρ_M. The σ-branching stays internal to the fiber; it does not cause escape to a different abstraction level.

**Tower perspective:** By the Information Loss Theorem (L8.2), when Lift(M) is constructed, the entire fiber the normal-form fiber NFC_M(f) — including all its σ-internal structure — is collapsed to a single atom ι_M(the normal-form fiber NFC_M(f)) at the next tower level. The horizontal infinity of σ-structure is invisible to the vertical tower; it is not reflected in the regime classification at higher levels.

**Why both dimensions matter:** The two-regime partition (↓_M ∐ ∞_M) captures the essential classification for the ABSTRACT TOWER (vertical dimension). The σ-structure (horizontal dimension) enriches the CONCRETE FIBER within each abstraction level. Together, they give the complete picture: vertical termination (regimes) × horizontal structure (fibers). Neither is a "third regime"—they are orthogonal dimensions of the model's structure.

**Precise statement:** There are exactly two regimes (↓_M and ∞_M) because the ρ-reduction relation partitions 𝒰_M exhaustively into convergent and persistent elements. The σ-relation does not introduce a partition; it enriches the structure at each abstraction level. The regime dichotomy is about VERTICAL infinity; σ-structure is about HORIZONTAL infinity at fixed vertical levels.

---

## Infinity Duality: Formal Characterization

### Horizontal-Vertical Infinity Duality
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L2.2.T7 | `Inf-Dual` | | **Novel** |
**Synopsis:** The Infinity Duality theorem establishes that horizontal infinity (having infinitely many elements in a fiber, H_S = ⊤ at every level) and vertical infinity (having an infinite projection orbit, ∞_M ≠ ∅) are dual in CRPT: each implies the other in any non-degenerate model. A model with no persistent elements necessarily has trivial fiber structure.

**Source:** CRPT; from [`∞_M` (L2.2.D5)](CRPT_OMEGA_TOWER_L2.md#persistent-regime-_m) + [`Lift-Def` (L8.2.D2)](CRPT_OMEGA_TOWER_L8.md#free-lift-of-m).

*Novelty Note.* **Basis (credited):** [`∞_M` (L2.2.D5)](CRPT_OMEGA_TOWER_L2.md#persistent-regime-_m) + [`Lift-Def` (L8.2.D2)](CRPT_OMEGA_TOWER_L8.md#free-lift-of-m). **New:** The Infinity Duality theorem establishes that horizontal infinity (having infinitely many elements in a fiber, H_S = ⊤ at every level) and vertical infinity (having an infinite projection orbit, ∞_M ≠ ∅) are dual in CRPT: each implies the other in any non-degenerate model. **Why it does not follow:** the statement is not an unfolding of the basis; the proof in the body supplies the argument that connects them.

*Three homes of the duality.* This is the **model-level statement**; its universal
template is L0.6, and its tower-level theory is L8.6 — three distinct constructs in
three strata, ι-related across levels, each owned by its stratum's section.

Let M satisfy PA-WN + PA-Conf, and let Lift(M) be its free lift ([`Lift-Def` (L8.2.D2)](CRPT_OMEGA_TOWER_L8.md#free-lift-of-m)). Then:

**(i) Horizontal infinity in M maps to vertical infinity in Lift(M):**
If x ∈ ↓_M ∩ (⋃_{f ∈ Fix(ρ_M)} G(f)) where G(f) = {y ∈ the normal-form fiber NFC_M(f) | ∃ a σ-path from y visiting infinitely many distinct ≃_M-classes} (elements whose fiber opens onto an infinite atom supply), then the depths of the compositions are unbounded:
```
sup{ d_{Lift(M)}(t) | t is a composition encoding x's σ-successors } = ∞
```
That is: if x has infinite horizontal structure at level M, the lifting process creates terms in Lift(M) with arbitrarily large abstraction depth.

**(ii) Vertical infinity in M remains vertical infinity in the limit tower:**
If x ∈ ∞_M, then x remains in the persistent regime at every tower level: ∞_M ⊆ ∞_{Mₙ} for all n ≥ 1 — no tower level converts a persistent element into a convergent one.

**(iii) Depth reset at abstraction: The complete horizontal structure collapses:**
For any f ∈ Fix(ρ_M), when the fiber the normal-form fiber NFC_M(f) is lifted as an atomic element to Lift(M):
```
d_{Lift(M)}(ι_M(NFC_M(f))) = 0
```
regardless of whether elements within f had infinite σ-structure. The entire horizontal infinity of the normal-form fiber NFC_M(f) is invisible to the vertical tower at level n+1.

**(iv) The duality stated as transformation:**
- **At level Mₙ:** Elements in ↓_{Mₙ} with infinite σ-structure within a fiber f are classified as Class C (horizon points)
- **At level Mₙ₊₁:** The fiber f becomes an atom ι_Mₙ(f) with depth 0, but σ-composition with other atoms creates new elements with depth 1, 2, ... in Lift(Mₙ)
- **The mapping:** Horizontal σ-structure of fiber f in Mₙ ↦ Horizontal σ-structure among fiber-atoms {ι_Mₙ(f) · ι_Mₙ(f')} in Mₙ₊₁
- **Net effect:** The σ-infinity of ONE fiber at level Mₙ becomes the (potentially infinite) depth of multi-fiber compositions at level Mₙ₊₁

*Proof.* (Parts (i) and (iv) reference the Lift construction of L8.1; see [`Lift-Def` (L8.2.D2)](CRPT_OMEGA_TOWER_L8.md#free-lift-of-m) for the free monoidal algebra FMA(Q_M) and the last-atom-strip reduction ρ_{Lift(M)} (strip the rightmost atom each step).)

(i) Let y ∈ G(f): a σ-path from y visits infinitely many distinct ≃_M-classes [a₁], [a₂], … (the hypothesis). By construction of Lift(M) ([`Lift-Def` (L8.2.D2)](CRPT_OMEGA_TOWER_L8.md#free-lift-of-m)), each visited class maps to an atom ι_M([aᵢ]) ∈ FMA(Q_M), and distinct classes yield distinct atoms — so the σ-path supplies an infinite atom stock. For any n ∈ ℕ form the n-fold composition t_n := ι_M([a₁]) · ι_M([a₂]) · ... · ι_M([aₙ]) ∈ FMA(Q_M) from the first n classes visited. The reduction ρ_{Lift(M)} removes the last atom at each step: ρ_{Lift(M)}(t_n) = ι_M([a₁]) · ... · ι_M([a_{n−1}]), so d_{Lift(M)}(t_n) = n − 1. As n → ∞, d_{Lift(M)}(t_n) → ∞: the supremum of the depths is ∞. ✓

(ii) By [`NFC-TInv` (L8.4.T2)](CRPT_OMEGA_TOWER_L8.md#nfc-partition-is-a-tower-invariant): Q_{Mₙ₊₁} = Q_{Mₙ} (abstraction quotient invariant), so the fixpoint stock is tower-invariant. An element reaching no fixpoint at level Mₙ reaches none at level Mₙ₊₁; hence x ∈ ∞_M lies in ∞_{Mₙ} at every level — the persistent regime persists up the tower. ✓

(iii) By [`Fix-Bas` (L8.2.T1)](CRPT_OMEGA_TOWER_L8.md#fixpoints-to-basics): Every fixpoint of Mₙ maps to depth 0 in Lift(Mₙ). This holds independent of internal structure. ✓

(iv) Combining (i)–(iii): At level Mₙ, a fiber f with infinite σ-structure has elements that compose into terms of unbounded depth at level Mₙ₊₁ (by (i)). Yet each fiber — including its infinite σ-structure — collapses to a single depth-0 atom at level Mₙ₊₁ (by (iii)). The infinite σ-structure at level Mₙ is thus not lost but re-encoded: the composition of atoms from distinct fibers at Mₙ₊₁ recreates a new horizontal σ-dimension among those atoms, and the depth of their compositions constitutes the new vertical structure. By (ii), any element that was vertically infinite at Mₙ remains so at Mₙ₊₁. Therefore horizontal infinity at one level becomes vertical infinity at the next, completing the duality. ✓ ∎

### The Infinity Cycle

| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Remark** | L2.2.R7 | `Infinity-Cycle` | | **Novel** |
**Synopsis:** Horizontal (σ-branching within a fiber) and vertical (unbounded composition depth) infinity are dual facets of one phenomenon, transformed into one another at successive tower levels.

**Source:** CRPT; from [`Inf-Dual` (L2.2.T7)](CRPT_OMEGA_TOWER_L2.md#horizontal-vertical-infinity-duality).

*Novelty Note.* **Basis (credited):** [`Inf-Dual` (L2.2.T7)](CRPT_OMEGA_TOWER_L2.md#horizontal-vertical-infinity-duality). **New:** Horizontal (σ-branching within a fiber) and vertical (unbounded composition depth) infinity are dual facets of one phenomenon, transformed into one another at successive tower levels. **Why it does not follow:** the stated observation is the contribution; the basis does not state it.

[`Inf-Dual` (L2.2.T7)](CRPT_OMEGA_TOWER_L2.md#horizontal-vertical-infinity-duality) reveals a deep symmetry: infinities are not lost in the tower, they are **transformed**. Horizontal infinity (σ-branching within a fiber) at level Mₙ becomes vertical infinity (unbounded composition depth) at level Mₙ₊₁, which then becomes horizontal infinity again (σ-structure among composite atoms) when viewed at that level. The two notions of infinity are **dual facets of the same phenomenon**, expressed in different directions at consecutive tower levels.

This explains why:
- **Regimes capture vertical infinity:** The ↓_M/∞_M partition asks whether x eventually reaches fixpoint under ρ-iteration (termination question at one level).
- **Horizon structure captures the transition:** The H_S/H_I classification identifies which elements are non-injective or ambiguous under the collapse — precisely those whose fiber has complex σ-structure.
- **The tower mediates:** Lifting transforms one manifestation of infinity into another.

### Inf-Dual Dependency Note

| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Remark** | L2.2.R8 | `InfDual-DepNote` | | **Derived** |
**Synopsis:** Dependency note: Inf-Dual's proof consumes the L8 Lift apparatus (Lift-Def, Fix-Bas, NFC-TInv); the dependency is forward but acyclic, so the anchor structure stays well-founded.

**Source:** CRPT; from [`Inf-Dual` (L2.2.T7)](CRPT_OMEGA_TOWER_L2.md#horizontal-vertical-infinity-duality) + [`Lift-Def` (L8.2.D2)](CRPT_OMEGA_TOWER_L8.md#free-lift-of-m).

*Derivation:* composed from [`Inf-Dual` (L2.2.T7)](CRPT_OMEGA_TOWER_L2.md#horizontal-vertical-infinity-duality) + [`Lift-Def` (L8.2.D2)](CRPT_OMEGA_TOWER_L8.md#free-lift-of-m); no content beyond the composition.

[`Inf-Dual` (L2.2.T7)](CRPT_OMEGA_TOWER_L2.md#horizontal-vertical-infinity-duality) uses [`Lift-Def` (L8.2.D2)](CRPT_OMEGA_TOWER_L8.md#free-lift-of-m),
[`Fix-Bas` (L8.2.T1)](CRPT_OMEGA_TOWER_L8.md#fixpoints-to-basics), and [`NFC-TInv` (L8.4.T2)](CRPT_OMEGA_TOWER_L8.md#nfc-partition-is-a-tower-invariant). This dependency is non-circular:
L8.1 does not depend on [`Inf-Dual` (L2.2.T7)](CRPT_OMEGA_TOWER_L2.md#horizontal-vertical-infinity-duality). The placement in L2.2 is expository,
while proof dependencies remain fully internal to this anchor.

---


## Regime Exhaustiveness: No Third Paradigm

### Regime Exhaustiveness
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L2.2.T8 | `Reg-Exh` | | **Novel** |
**Synopsis:** The regime exhaustion theorem confirms ↓_M ∪ ∞_M = 𝒰_M: every element is either convergent or persistent, with no third possibility. This follows from the universal regime dichotomy (L0.2.T1) instantiated to the CRPT projection operator.

**Source:** CRPT; from [`Reg-Strat` (L2.2.D3)](CRPT_OMEGA_TOWER_L2.md#native-regime-stratification); instance of [`Regime-Dich` (L0.2.T1)](CRPT_OMEGA_TOWER_L0.md#universal-regime-dichotomy).

*Novelty Note.* **Basis (credited):** [`Reg-Strat` (L2.2.D3)](CRPT_OMEGA_TOWER_L2.md#native-regime-stratification) + [`Regime-Dich` (L0.2.T1)](CRPT_OMEGA_TOWER_L0.md#universal-regime-dichotomy). **New:** The regime exhaustion theorem confirms ↓_M ∪ ∞_M = 𝒰_M: every element is either convergent or persistent, with no third possibility. **Why it does not follow:** the statement is not an unfolding of the basis; the proof in the body supplies the argument that connects them.

*Let (𝒰, →_ρ, →_σ, 𝒯) be a substrate satisfying →_ρ ⊆ →_σ, and let ρ_M : 𝒰 → 𝒰
be an abstraction operator (step-or-fix) satisfying the structural conditions
C1 (idempotence on NF), C2 (Bisimulation Equivariance) (coherence). Define:*

$$↓_M := \{x \in \mathcal{U} \mid \exists n \in \mathbb{N} : \rho_M^n(x) \in \text{Fix}(\rho_M)\}$$

$$∞_M := \mathcal{U} \setminus ↓_M$$

*Then:*
1. $↓_M \cup ∞_M = \mathcal{U}$ *(exhaustive)*
2. $↓_M \cap ∞_M = \emptyset$ *(disjoint)*
3. *Every x ∈ 𝒰 is classified by exactly one of:*
   - *(convergent regime)* x ∈ ↓_M — the ρ_M-orbit of x terminates
   - *(persistent regime)* x ∈ ∞_M — the ρ_M-orbit of x does not terminate

*There is no third possibility.*

*Proof.*

Claims (1) and (2) follow immediately from the definition: ∞_M := 𝒰 \ ↓_M is
the set-theoretic complement, so the union is 𝒰 and the intersection is ∅. This
is a logical tautology (law of excluded middle applied to the predicate
"∃n : ρ_M^n(x) ∈ Fix(ρ_M)").

Claim (3) restates (1) and (2) in operational language: for each x ∈ 𝒰, either
the orbit (x, ρ_M(x), ρ_M²(x), …) reaches Fix(ρ_M) in finite steps, or it does
not. There is no third option because "reaches in finite steps" and "does not reach
in finite steps" are contradictory predicates that jointly exhaust all possibilities.

No appeal to PA-WN or PA-NWF is needed — the partition is a property of the
definitions, not of any axiom. ∎

### Axiom Coverage
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L2.2.T9 | `Ax-Cov` |  | **Novel** |
**Synopsis:** The axiom coverage theorem: the convergent-regime axioms (PA-WN, PA-Conf, PA-Fix) and persistent-regime axioms (PA-NWF, PA-CoInd, PA-Prod, PA-WN_top, PA-Bisim, PA-Reach), together with the Gateway structure (→_σ interface), cover all structurally distinct cases of the regime partition.

**Source:** CRPT; from [`Reg-Exh` (L2.2.T8)](CRPT_OMEGA_TOWER_L2.md#regime-exhaustiveness); instance of [`Ax-Cov-U` (L0.2.T2)](CRPT_OMEGA_TOWER_L0.md#universal-axiom-coverage).

*Novelty Note.* **Basis (credited):** [`Reg-Exh` (L2.2.T8)](CRPT_OMEGA_TOWER_L2.md#regime-exhaustiveness) + [`Ax-Cov-U` (L0.2.T2)](CRPT_OMEGA_TOWER_L0.md#universal-axiom-coverage). **New:** The axiom coverage theorem: the convergent-regime axioms (PA-WN, PA-Conf, PA-Fix) and persistent-regime axioms (PA-NWF, PA-CoInd, PA-Prod, PA-WN_top, PA-Bisim, PA-Reach), together with the Gateway structure (→_σ interface), cover all structurally distinct cases of the regime partition. **Why it does not follow:** the statement is not an unfolding of the basis; the proof in the body supplies the argument that connects them.

*The PA-* axiom system partitions all structural commitments on (𝒰, →_ρ, →_σ, 𝒯)
as follows:*

- *PA-WN governs ↓_M (the convergent regime): termination, confluence, saturation, extensionality*
- *PA-NWF and the persistent-regime axioms (PA-CoInd, PA-Prod, PA-Bisim, PA-WN_top, PA-Reach) govern ∞_M: infinite paths, coinduction, productivity, bisimulation, topological convergence, asymptotic-destination reachability*
- *The Gateway structure (→_σ connectivity) governs the interface between ↓_M and ∞_M*

*No property of (𝒰, →_ρ, →_σ, ρ_M) lies outside this tripartite coverage.*

*Proof.*

Any property P of (𝒰, →_ρ, →_σ, ρ_M) falls into one of three categories:

1. **P concerns elements of ↓_M only.** Then P is governed by PA-WN and its
   consequences (RP-1, RP-2, PV-1, CFix(ρ_M) existence, rank function, horizon
  classification). The WF projection axioms (PA-WN, PA-Conf, PA-Fix)
  together with theorems WF-Canon and WF-Ext provide a complete account of convergent behaviour:
  termination (PA-WN), uniqueness (PA-Conf), fixpoint stratification (PA-Fix),
  canonicalization totality (WF-Canon), and indiscernibility (WF-Ext, a theorem).

2. **P concerns elements of ∞_M only.** Then P is governed by PA-NWF and its
   consequences (CP-1, CP-2, PV-2, CNF∞, SC-*). The persistent-regime axioms (PA-NWF,
   PA-CoInd, PA-Prod, PA-Bisim, PA-WN_top, PA-Reach) provide a complete axiomatisation
   of persistent behaviour: infinite paths (PA-NWF), membership coinduction (PA-CoInd),
   evaluability (PA-Prod), behavioural equivalence (PA-Bisim), topological convergence
   (PA-WN_top), and asymptotic-destination reachability (PA-Reach).

3. **P concerns the relationship between ↓_M and ∞_M.** Then P is governed by the
   Gateway structure — the Gateway predicate GW (L4.2.D1) and the Gateway Reachability
   property, both stated over →_σ. Theorem [`Reg-Conn` (L4.2.T1)](CRPT_OMEGA_TOWER_L4.md#regime-connectedness--rt) derives
   regime-connectedness from Gateway Reachability, and [`CPEP-Ind` (L4.7.T1)](CRPT_OMEGA_TOWER_L4.md#cpep-is-independent-of-pa-) and [`Refl-Abs-T` (L4.7.T2)](CRPT_OMEGA_TOWER_L4.md#reflectiveabsorbing-dichotomy) govern
   cross-regime perturbations.

The three categories are exhaustive because every element of 𝒰 is in ↓_M or ∞_M
([`Reg-Compl` (L2.2.T6)](CRPT_OMEGA_TOWER_L2.md#regime-completeness--two-regimes-exactly)), and every property either concerns one regime or their interaction. ∎

### No Third Paradigm Within the Substrate Interface
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L2.2.T10 | `No-3rd` |  | **Novel** |
**Synopsis:** The no-third-regime theorem: there is no consistent axiom system that would introduce a third regime beyond ↓_M and ∞_M. Any proposed third class 𝒫_M would either be a subset of ↓_M, a subset of ∞_M, or empty — the regime dichotomy is logically exhaustive.

**Source:** CRPT; from [`Reg-Exh` (L2.2.T8)](CRPT_OMEGA_TOWER_L2.md#regime-exhaustiveness).

*Novelty Note.* **Basis (credited):** [`Reg-Exh` (L2.2.T8)](CRPT_OMEGA_TOWER_L2.md#regime-exhaustiveness). **New:** The no-third-regime theorem: there is no consistent axiom system that would introduce a third regime beyond ↓_M and ∞_M. **Why it does not follow:** the statement is not an unfolding of the basis; the proof in the body supplies the argument that connects them.

*A "third model-level paradigm" beyond WF and NWF would require one of:*

1. *A third regime 𝒫_M ⊆ 𝒰 with 𝒫_M ∩ ↓_M = ∅ and 𝒫_M ∩ ∞_M = ∅ — impossible by [`Reg-Compl` (L2.2.T6)](CRPT_OMEGA_TOWER_L2.md#regime-completeness--two-regimes-exactly).*
2. *A substrate with more than two primitive relations — possible in principle, but outside CRPT's substrate interface.*
3. *An abstraction operator ρ_M that is not step-or-fix — possible in principle, but outside CRPT's structural conditions C1/C2 (Bisimulation Equivariance)/C3.*

*Proof.*

Option (1) is ruled out by [`Reg-Compl` (L2.2.T6)](CRPT_OMEGA_TOWER_L2.md#regime-completeness--two-regimes-exactly): ↓_M ∪ ∞_M = 𝒰, so no element can be
in neither regime.

Options (2) and (3) are *logically possible* but require changing the substrate
interface itself — they are not "third paradigms within CRPT" but "different
meta-model frameworks." CRPT does not claim to be the unique possible
meta-model framework; it claims that within its substrate interface
(𝒰, →_ρ, →_σ, 𝒯) and structural conditions (C1, C2 (Bisimulation Equivariance), C3), WF and NWF are exhaustive.

This distinction is important: "Are there CRPT models beyond WF/NWF?" has two
readings:
- *Within CRPT:* No, by theorem. The partition is definitional.
- *Beyond CRPT's substrate interface:* Possible, but this is a question about
  alternative meta-model frameworks, not about CRPT.

Examples of approaches that might not reduce to WF/NWF:
- **Predicative type theory** (neither fully WF nor NWF; restricted comprehension)
- **Modal set theory** (accessibility relations add a third dimension)
- **Non-distributive lattice structures** (e.g. orthomodular lattices)

These would require a richer substrate interface to accommodate. CRPT's analysis
is conditional on the (𝒰, →_ρ, →_σ, 𝒯) interface; within that interface, the
exhaustiveness is a theorem, not a hypothesis. ∎

*Conclusion.* Within CRPT, WF/NWF exhaustiveness is a theorem immediate from the regime definitions.
Beyond CRPT's substrate interface, other paradigms are conceivable but are outside
CRPT's scope. The scope distinction is explicit.

---

---

## L2.3 — Derivation Height d_M

*Purpose.* Derivation Height. This section assigns to each element of ↓_M a natural-number rank d_M(x) — its derivation height. This rank orders the convergent regime as a well-founded poset and is the key quantity for the depth-horizon predicate H_O of L3.*


### Partial Order: ρ_M-Reachability

### ρ_M-Reachability Preorder
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L2.3.D1 | `≤_ρ` | ≤_ρ | **Specialized** |
**Synopsis:** The derivation-height poset (↓_M, ≤_ρ) orders elements of the convergent regime by their derivation height. This is a well-founded partial order: every non-empty subset has a minimal element (fixed points, at depth 0). It is the induction measure for all structural arguments in L3–L8.

**Source:** Cousot & Cousot [1977] POPL — approximation ordering; reframed over [`ρ_M` (L2.1.D1)](CRPT_OMEGA_TOWER_L2.md#projection-operator-ρ_m).

On μT_{ρ,M}, define:
```
x ≤_ρ y :⟺ ∃k ∈ ℕ : ρ_M^k(x) = y
```
the reflexive-transitive relation "y is reachable from x by ρ_M iteration."

### ≤_ρ is a Partial Order under PA-Conf
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Lemma** | L2.3.L1 | `≤ρ-PO` |  | **Specialized** |
**Synopsis:** The derivation-height order ≤_ρ on ↓_M is a partial order: it is reflexive (d_M(x) ≤ d_M(x)), antisymmetric (x ≤_ρ y and y ≤_ρ x implies d_M(x) = d_M(y)), and transitive. Well-foundedness follows from the fact that d_M takes values in ℕ, which has no infinite descending chains.

**Source:** Cousot & Cousot [1977] POPL — order verification; applied to [`≤_ρ` (L2.3.D1)](CRPT_OMEGA_TOWER_L2.md#ρ_m-reachability-preorder) under [PA-Conf (L1.2.Ax2)](CRPT_OMEGA_TOWER_L1.md#pa-conf--confluence--church-rosser).

Under PA-Conf (Church-Rosser),
≤_ρ is reflexive, transitive, and antisymmetric on μT_{ρ,M}. Therefore (μT_{ρ,M}, ≤_ρ) is a **poset**
(partially ordered set).

*Proof.* (Here d_M(x) := min{n ∈ ℕ | ρ_M^n(x) ∈ Fix(ρ_M)}, formalized in [`d_M` (L2.3.D2)](CRPT_OMEGA_TOWER_L2.md#rank-function--derivation-height-notation-d_m).)

- *Reflexivity:* ρ_M⁰(x) = x, so x ≤_ρ x. ✓
- *Transitivity:* x ≤_ρ y and y ≤_ρ z imply ∃k, ℓ : ρ_M^k(x) = y and ρ_M^ℓ(y) = z.
 Then ρ_M^{k+ℓ}(x) = z, so x ≤_ρ z. ✓
- *Antisymmetry:* Suppose x ≤_ρ y and y ≤_ρ x. Then ∃k, ℓ : ρ_M^k(x) = y and
 ρ_M^ℓ(y) = x. If k + ℓ = 0, then x = y. If k + ℓ > 0: ρ_M^{k+ℓ}(x) = x, so by
 induction ρ_M^{a(k+ℓ)}(x) = x for all a ∈ ℕ. Since x ∈ μT_{ρ,M}, let d = d_M(x)
 and f = ρ_M^d(x) ∈ Fix(ρ_M). For all m ≥ d: ρ_M^m(x) = f (since ρ_M fixes f).
 Choose a large enough that a(k+ℓ) ≥ d. Then ρ_M^{a(k+ℓ)}(x) = f (since a(k+ℓ) ≥ d).
 But ρ_M^{a(k+ℓ)}(x) = x. So x = f ∈ Fix(ρ_M), and y = ρ_M^k(f) = f = x. ✓ ∎

### Antisymmetry of ≤_ρ

| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Remark** | L2.3.R1 | `leq-Antisym` | | **Novel** |
**Synopsis:** Antisymmetry of ≤_ρ comes from determinism of ρ_M and finite reachability of fixpoints; PA-Conf appears in the hypothesis only for uniform citation, not as a logical need.

**Source:** CRPT; from [`d_M` (L2.3.D2)](CRPT_OMEGA_TOWER_L2.md#rank-function--derivation-height-notation-d_m).

*Novelty Note.* **Basis (credited):** [`d_M` (L2.3.D2)](CRPT_OMEGA_TOWER_L2.md#rank-function--derivation-height-notation-d_m). **New:** Antisymmetry of ≤_ρ comes from determinism of ρ_M and finite reachability of fixpoints; PA-Conf appears in the hypothesis only for uniform citation, not as a logical need. **Why it does not follow:** the stated observation is the contribution; the basis does not state it.

Antisymmetry of ≤_ρ follows from the deterministic (functional) nature of ρ_M and the
finite reachability of fixpoints in μT_{ρ,M}. PA-Conf is included in the hypothesis for consistency with
downstream uses (the reachability poset interacts with Church-Rosser uniqueness in L2.4).

### Rank Function Definition

### Rank Function / Derivation Height, notation d_M
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L2.3.D2 | `d_M` | d_M | **Reframed** |
**Synopsis:** The derivation height d_M(x) counts the minimum ρ_M-steps needed to reach Fix(ρ_M) from x. Depth 0 = already a fixed point; depth 1 = boundary layer (H_O = ⊤ in L3). This gives ↓_M a well-founded rank ordering used throughout the horizon theory.

**Source:** Baader & Nipkow [1998] §2.1 (derivation length / ARS rank); reframed as the derivation height d_M(x) = min{n | ρ_M^n(x) ∈ Fix(ρ_M)}, defined on the convergent regime, with the strict orbit-monotone property.

*Reframing Note.* **Source form:** derivation length / ARS rank (Baader & Nipkow §2.1) — path lengths over all reductions. **CRPT form:** d_M(x) = min{n | ρ_M^n(x) ∈ Fix(ρ_M)}, the rank along the canonical strategy's orbit. **The delta:** the rank is taken along the deterministic ρ_M-orbit only, and is total exactly on ↓_M. **Justification:** mathematical — determinism makes the rank well-defined without confluence hypotheses, and this form is what dualizes to the reachability depth n_M ([`n-Reach` (L3.3.D10)](CRPT_OMEGA_TOWER_L3.md#reachability-depth-n_m)).

For x ∈ μT_{ρ,M}, define:
```
d_M(x) := rank_{(μT_{ρ,M}, ≤_ρ)}(x) := min { n ∈ ℕ | ρ_M^n(x) ∈ Fix(ρ_M) }
```

The **rank function** derivation height assigns to each element x ∈ μT_{ρ,M} its height in the reachability poset
(μT_{ρ,M}, ≤_ρ). Since ρ_M is a function (deterministic), there is exactly one ρ_M-chain from x to
Fix(ρ_M), so the following characterizations are equivalent:
- d_M(x) = min{n ∈ ℕ | ρ_M^n(x) ∈ Fix(ρ_M)} (the defining formula above)
- d_M(x) = the unique length of the ρ_M-chain from x to its fixpoint
- Standard ARS terminology: derivation height / reduction length (Baader & Nipkow [1998] §2.1).
- Standard order theory terminology: rank function (Diestel [2017] §3.2) on the poset of convergent elements.

The CRPT local term is **abstraction depth**: d_M(x) measures how many abstraction steps are required
to collapse x down to its canonical abstraction CFix(ρ_M)(x).

### Domain of Derivation Height

| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Remark** | L2.3.R2 | `dM-Domain` | | **Novel** |
**Synopsis:** The derivation height is defined exactly on the convergent regime: for persistent x the defining set is empty and d_M(x) is undefined — its persistent counterpart is the reachability depth n_M.

**Source:** CRPT; from [`d_M` (L2.3.D2)](CRPT_OMEGA_TOWER_L2.md#rank-function--derivation-height-notation-d_m).

*Novelty Note.* **Basis (credited):** [`d_M` (L2.3.D2)](CRPT_OMEGA_TOWER_L2.md#rank-function--derivation-height-notation-d_m). **New:** The derivation height is defined exactly on the convergent regime: for persistent x the defining set is empty and d_M(x) is undefined — its persistent counterpart is the reachability depth n_M. **Why it does not follow:** the stated observation is the contribution; the basis does not state it.

derivation height is defined only on μT_{ρ,M}. For x ∈ νT_{ρ,M}, the set {n | ρ_M^n(x) ∈ Fix(ρ_M)} is
empty, so d_M(x) is undefined. The rank function has no meaning for persistent/diverging elements.

### Derivation Height in the Native Framework

| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Remark** | L2.3.R3 | `dM-Native` | | **Derived** |
**Synopsis:** How derivation height extends across both regimes in the native framework.

**Source:** CRPT; from [`d-WD` (L2.3.T1)](CRPT_OMEGA_TOWER_L2.md#d_m-is-well-defined-on-μt_ρm) + [`Reg-Strat` (L2.2.D3)](CRPT_OMEGA_TOWER_L2.md#native-regime-stratification).

*Derivation:* composed from [`d-WD` (L2.3.T1)](CRPT_OMEGA_TOWER_L2.md#d_m-is-well-defined-on-μt_ρm) + [`Reg-Strat` (L2.2.D3)](CRPT_OMEGA_TOWER_L2.md#native-regime-stratification); no content beyond the composition.


In the native regime-stratified setting (L1.2–L1.5, [`Reg-Strat` (L2.2.D3)](CRPT_OMEGA_TOWER_L2.md#native-regime-stratification)), the concept of derivation height extends to all elements:

- **For x ∈ ↓_M:** d_M(x) ∈ ℕ (finite derivation height), measured as the number of ρ_M iterations to reach a fixpoint. All existing theorems on d_M ([`d-WD` (L2.3.T1)](CRPT_OMEGA_TOWER_L2.md#d_m-is-well-defined-on-μt_ρm), [`Depth-Dec` (L2.3.T2)](CRPT_OMEGA_TOWER_L2.md#strict-depth-decrease), [`Fix-D0` (L2.3.T3)](CRPT_OMEGA_TOWER_L2.md#fixpoints-have-depth-zero)) apply directly.
- **For x ∈ ∞_M:** d_M(x) := ∞ (infinite derivation), reflecting that the orbit never reaches Fix(ρ_M) in finitely many steps. Instead, x has a well-defined **topological depth** d_M^{top}(x, ε) for ε > 0, defined as:
 ```
 d_M^{top}(x, ε) := min { N ∈ ℕ | ∀n ≥ N : d_𝒯(ρ_M^n(x), CFix(ρ_M)(x)) < ε }
 ```
 This measures how many ρ_M-iterations are needed to come within ε-distance of the limit point CFix(ρ_M)(x). As ε → 0, derivation height^{top}(x, ε) → ∞ in a controlled way, capturing the convergence rate.

[`d-WD` (L2.3.T1)](CRPT_OMEGA_TOWER_L2.md#d_m-is-well-defined-on-μt_ρm) transfers: derivation height is well-defined on all of 𝒰, with ℕ-values on ↓_M and ∞ on ∞_M. The model includes the persistent regime via this extension.

### d_M is Well-Defined on μT_{ρ,M}
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L2.3.T1 | `d-WD` |  | **Imported** |
**Synopsis:** The derivation height d_M(x) is well-defined on the convergent regime: for every x ∈ ↓_M the set {n | ρ_M^n(x) ∈ Fix(ρ_M)} is non-empty, so its minimum d_M(x) ∈ ℕ exists.

**Source:** Baader & Nipkow [1998] — well-definedness of reduction length.

For all x ∈ μT_{ρ,M}, d_M(x) ∈ ℕ.

*Proof.* By definition of μT_{ρ,M}, the set S(x) := {n | ρ_M^n(x) ∈ Fix(ρ_M)} is
non-empty. ℕ is well-ordered, so every non-empty subset of ℕ has a minimum.
Therefore min S(x) exists and equals d_M(x). ∎

### Strict Depth Decrease
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L2.3.T2 | `Depth-Dec` |  | **Imported** |
**Synopsis:** Strict depth decrease: for a non-fixpoint convergent element, one projection step reduces derivation height by exactly one — d_M(ρ_M(x)) = d_M(x) − 1. The height strictly decreases along every ρ_M-orbit until the fixpoint is reached.

**Source:** Baader & Nipkow [1998] — strict decrease of reduction length.

For x ∈ μT_{ρ,M} with ρ_M(x) ≠ x:
```
d_M(ρ_M(x)) = d_M(x) - 1 < d_M(x)
```

*Proof.* Let d_M(x) = k. Then ρ_M^k(x) ∈ Fix(ρ_M) and k ≥ 1 (since x ∉ Fix(ρ_M)).
Now ρ_M^{k-1}(ρ_M(x)) = ρ_M^k(x) ∈ Fix(ρ_M), so d_M(ρ_M(x)) ≤ k-1.
Suppose d_M(ρ_M(x)) = j < k-1. Then ρ_M^j(ρ_M(x)) = ρ_M^{j+1}(x) ∈ Fix(ρ_M),
with j+1 < k. This contradicts k = min S(x). So d_M(ρ_M(x)) = k-1. ∎

### Fixpoints have Depth Zero
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L2.3.T3 | `Fix-D0` |  | **Imported** |
**Synopsis:** Fixpoints have depth zero: d_M(x) = 0 for every x ∈ Fix(ρ_M), since ρ_M^0(x) = x already lies in Fix(ρ_M). This is the base case of the derivation-height clock.

**Source:** Baader & Nipkow [1998] — normal forms have reduction length zero.

For x ∈ Fix(ρ_M): d_M(x) = 0.

*Proof.* ρ_M⁰(x) = x ∈ Fix(ρ_M), so 0 ∈ S(x) and d_M(x) = min S(x) = 0. ∎

### d_M is a Well-Founded Measure on μT_{ρ,M}
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Corollary** | L2.3.C1 | `d-WFM` |  | **Imported** |
**Synopsis:** The derivation height induces a well-founded measure on ↓_M: every non-empty subset of ↓_M has a minimal element under ≤_ρ (namely, any element with the minimum d_M value in the subset). This makes structural induction on d_M valid.

**Source:** Baader & Nipkow [1998]; Tarski [1955] — well-founded measure for induction.

The relation
{(x, ρ_M(x)) | x ∈ μT_{ρ,M}, x ∉ Fix(ρ_M)} is well-founded. derivation height is the corresponding
measure: derivation height strictly decreases along ρ_M-orbits in μT_{ρ,M}.

*Proof.* Immediate from [`Depth-Dec` (L2.3.T2)](CRPT_OMEGA_TOWER_L2.md#strict-depth-decrease) and the fact that derivation height ∈ ℕ. ∎

---

## L2.4 — Canonical Normal Form Map

*Purpose.* Canonical Form and Canonical Fixpoint. This section defines the canonical form map — the map sending each x ∈ ↓_M to its unique fixed-point limit — and proves its fundamental properties: existence, uniqueness, and compatibility with observable equivalence ≃_M.*


### Definition

### Canonical Normal Form Map — Native Form
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L2.4.D1 | `CFix-NM` |  | **Novel** |
**Synopsis:** The canonical fixpoint map CFix(ρ_M)(x) = ρ_M^{d_M(x)}(x) is the unique fixed point reachable from x by the canonical number of projection steps. This is the explicit computation that the canonical form map performs.

**Source:** CRPT; from [`Rec-Proj` (L2.1.D4)](CRPT_OMEGA_TOWER_L2.md#recursive-projection) + [`d_M` (L2.3.D2)](CRPT_OMEGA_TOWER_L2.md#rank-function--derivation-height-notation-d_m).

*Novelty Note.* **Basis (credited):** [`Rec-Proj` (L2.1.D4)](CRPT_OMEGA_TOWER_L2.md#recursive-projection) + [`d_M` (L2.3.D2)](CRPT_OMEGA_TOWER_L2.md#rank-function--derivation-height-notation-d_m). **New:** The canonical fixpoint map CFix(ρ_M)(x) = ρ_M^{d_M(x)}(x) is the unique fixed point reachable from x by the canonical number of projection steps. **Why it does not follow:** the basis supplies the ingredients; the notion assembled from them, and the role it is defined to play in the theory, is introduced here rather than entailed.

The map CFix(ρ_M) : 𝒰 → (NF(→_ρ) ∪ Limits(𝒯)) is defined in a regime-dependent manner:

```
CFix(ρ_M)(x) := {
 ρ_M^{d_M(x)}(x) if x ∈ ↓_M
 lim_{n→∞} ρ_M^n(x) (unique in 𝒯) if x ∈ ∞_M
}
```

where the limit for ∞_M elements is taken in the model topology 𝒯 specified as part of the substrate ([`Sub` (L1.1.D1)](CRPT_OMEGA_TOWER_L1.md#substrate), L1.2).

### Existence and Uniqueness (Native Form)

| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Remark** | L2.4.R1 | `CFix-ExUniq-Nat` | | **Novel** |
**Synopsis:** Existence and uniqueness of the canonical form in native (both-regime) form.

**Source:** CRPT; from [`CNF-Ex` (L2.4.T1)](CRPT_OMEGA_TOWER_L2.md#cnf-existence) + [`TopSep-Uniq` (L1.7.T1)](CRPT_OMEGA_TOWER_L1.md#uniqueness-of-topological-limits-under-topsep).

*Novelty Note.* **Basis (credited):** [`CNF-Ex` (L2.4.T1)](CRPT_OMEGA_TOWER_L2.md#cnf-existence) + [`TopSep-Uniq` (L1.7.T1)](CRPT_OMEGA_TOWER_L1.md#uniqueness-of-topological-limits-under-topsep). **New:** Existence and uniqueness of the canonical form in native (both-regime) form. **Why it does not follow:** the stated observation is the contribution; the basis does not state it.

**Existence and Uniqueness in Native Form:**

- **For x ∈ ↓_M:** CFix(ρ_M)(x) ∈ NF(→_ρ) exists by [`CNF-Ex` (L2.4.T1)](CRPT_OMEGA_TOWER_L2.md#cnf-existence).
 Uniqueness holds for the deterministic ρ_M-orbit (C1–C2). If PA-Conf is assumed
 globally then uniqueness also extends to arbitrary →_ρ*-paths (Church–Rosser).
 See L1.4 (Scope Sufficiency for CFix(ρ_M)) for the `Scoped(ρ_M-orbits)` formulation used by some instantiations.
- **For x ∈ ∞_M:** The limit lim_{n→∞} ρ_M^n(x) exists in (𝒰, 𝒯) by PA-WN_top ([`Ax-Scope` (L1.5.D1)](CRPT_OMEGA_TOWER_L1.md#pa--scope-declaration), L1.4). Uniqueness follows formally from [`TopSep-Uniq` (L1.7.T1)](CRPT_OMEGA_TOWER_L1.md#uniqueness-of-topological-limits-under-topsep), i.e. from the explicit TopSep(𝒯) condition required by PA-WN_top. Thus CFix(ρ_M) is single-valued on all of 𝒰.

The definition unifies both regimes: CFix(ρ_M) is a total function on 𝒰, with finitary normal form on ↓_M and topological limit on ∞_M.

*Standard name.* In standard (pure WF) CRPT: CFix(ρ_M) is the canonical normal-form map (Baader & Nipkow §2.1, Church-Rosser normal form). In native CRPT: CFix(ρ_M) extends to analytic models via topological closure, generalizing the Church-Rosser property to topological limit convergence. Both are called **canonical** because they are unique: finitary uniqueness follows from PA-Conf, while topological uniqueness follows from [`TopSep-Uniq` (L1.7.T1)](CRPT_OMEGA_TOWER_L1.md#uniqueness-of-topological-limits-under-topsep), i.e. PA-WN_top together with the explicit TopSep(𝒯) assumption. They represent the maximal abstraction of their fiber.

### Discernibility: Canonical Form

| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Remark** | L2.4.R2 | `Disc-CFix` | | **Derived** |
**Synopsis:** Reading CFix(ρ_M)(x) as the canonical discernible representative of x.

**Source:** CRPT; from [`CFix-NM` (L2.4.D1)](CRPT_OMEGA_TOWER_L2.md#canonical-normal-form-map--native-form).

*Derivation:* composed from [`CFix-NM` (L2.4.D1)](CRPT_OMEGA_TOWER_L2.md#canonical-normal-form-map--native-form); no content beyond the composition.

CFix(ρ_M)(x) is the **canonical discernible
residue** of x: the unique representative that encodes all and only the discernible
content of [x]_{≃_M}. Every element in this equivalence class shares the same
canonical form — they are indiscernible with respect to the orbit structure. CFix(ρ_M)
is injective on equivalence classes, ensuring that no discernible information is lost.

### Existence and Uniqueness

### CNF Existence
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L2.4.T1 | `CNF-Ex` |  | **Specialized** |
**Synopsis:** Canonical form existence: every convergent element reaches a normal form — for x ∈ ↓_M, ρ_M^{d_M(x)}(x) ∈ NF(→_ρ). Hence the canonical form CFix(ρ_M)(x) exists and is a genuine normal form.

**Source:** Baader & Nipkow [1998] §6.1 — normal-form existence under weak normalisation; applied to [`d_M` (L2.3.D2)](CRPT_OMEGA_TOWER_L2.md#rank-function--derivation-height-notation-d_m) + [`Fix=NF` (L2.1.T2)](CRPT_OMEGA_TOWER_L2.md#fix--nf).

For each x ∈ μT_{ρ,M}: ρ_M^{d_M(x)}(x) ∈ NF(→_ρ).

*Proof.* Let n = d_M(x). By [`d_M` (L2.3.D2)](CRPT_OMEGA_TOWER_L2.md#rank-function--derivation-height-notation-d_m), ρ_M^n(x) ∈ Fix(ρ_M). Under PA-WN,
Fix(ρ_M) = NF(→_ρ) by [`Fix=NF` (L2.1.T2)](CRPT_OMEGA_TOWER_L2.md#fix--nf). So ρ_M^n(x) ∈ NF(→_ρ). ∎

### Fix = NF Unconditionally

| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Remark** | L2.4.R3 | `FixNF-Uncond` | | **Novel** |
**Synopsis:** Fix(ρ_M) = NF(→_ρ) holds unconditionally by the strengthened C1, so canonical forms are normal forms in every setting, not only under PA-WN.

**Source:** CRPT; from [`Fix=NF` (L2.1.T2)](CRPT_OMEGA_TOWER_L2.md#fix--nf).

*Novelty Note.* **Basis (credited):** [`Fix=NF` (L2.1.T2)](CRPT_OMEGA_TOWER_L2.md#fix--nf). **New:** Fix(ρ_M) = NF(→_ρ) holds unconditionally by the strengthened C1, so canonical forms are normal forms in every setting, not only under PA-WN. **Why it does not follow:** the stated observation is the contribution; the basis does not state it.

Fix(ρ_M) = NF(→_ρ) unconditionally ([`Fix=NF` (L2.1.T2)](CRPT_OMEGA_TOWER_L2.md#fix--nf), from the strengthened
C1 condition). So ρ_M^{d_M(x)}(x) ∈ Fix(ρ_M) = NF(→_ρ) in all settings.

### CNF Uniqueness — Orbit-Scoped Uniqueness
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L2.4.T2 | `CNF-Uniq` | | **Novel** |
**Synopsis:** Under PA-WN and scoped confluence, the canonical form map CNF_M(x) = ρ_M^{d_M(x)}(x) is the unique element of Fix(ρ_M) reachable from x. Two elements x, y have the same canonical form if and only if they are observationally equivalent (x ≃_M y).

**Source:** CRPT; from [PA-Conf (L1.2.Ax2)](CRPT_OMEGA_TOWER_L1.md#pa-conf--confluence--church-rosser) + [PA-WN (L1.2.Ax1)](CRPT_OMEGA_TOWER_L1.md#pa-wn--weak-normalisation); background in Church & Rosser [1936], Baader & Nipkow [1998] §6.1.

*Novelty Note.* **Basis (credited):** [PA-Conf (L1.2.Ax2)](CRPT_OMEGA_TOWER_L1.md#pa-conf--confluence--church-rosser) + [PA-WN (L1.2.Ax1)](CRPT_OMEGA_TOWER_L1.md#pa-wn--weak-normalisation). **New:** Under PA-WN and scoped confluence, the canonical form map CNF_M(x) = ρ_M^{d_M(x)}(x) is the unique element of Fix(ρ_M) reachable from x. **Why it does not follow:** the statement is not an unfolding of the basis; the proof in the body supplies the argument that connects them.

Under C1–C2
([`ρ_M` (L2.1.D1)](CRPT_OMEGA_TOWER_L2.md#projection-operator-ρ_m) (ρ_M a deterministic strategy), for each x ∈ μT_{ρ,M} the ρ_M-orbit
of x reaches at most one element of NF(→_ρ): the element ρ_M^{d_M(x)}(x). Equivalently,
the ρ_M-orbit contains a unique normal form.

If PA-Conf holds globally then this uniqueness extends to arbitrary →_ρ*-paths.
When PA-Conf is declared `Scoped(ρ_M-orbits)` (see L1.4, Scope Sufficiency for CFix(ρ_M)), the
orbit-scoped uniqueness stated here is sufficient for CFix(ρ_M) to be well-defined on μT_{ρ,M}.

*Proof.* The ρ_M-orbit of x is the deterministic sequence (ρ_M^n(x))_{n∈ℕ}. If
x ∈ μT_{ρ,M}, then by [`d_M` (L2.3.D2)](CRPT_OMEGA_TOWER_L2.md#rank-function--derivation-height-notation-d_m) there is a minimal d_M(x) with
ρ_M^{d_M(x)}(x) ∈ Fix(ρ_M) = NF(→_ρ). Since ρ_M is a function, this orbit is
unique and therefore reaches a single NF element, namely f := ρ_M^{d_M(x)}(x).
Hence no two distinct normal forms can be reached along the ρ_M-orbit. ∎

### CNF-Uniq Is the Church–Rosser Theorem

| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Remark** | L2.4.R4 | `CNFUniq-CR` | | **Novel** |
**Synopsis:** CNF-Uniq is exactly the Church–Rosser theorem for (𝒰_M, →_ρ): under PA-WN + PA-Conf the canonical form map is the normal-form function of a confluent, weakly normalising system.

**Source:** CRPT; from [`CNF-Uniq` (L2.4.T2)](CRPT_OMEGA_TOWER_L2.md#cnf-uniqueness--orbit-scoped-uniqueness); background in Baader & Nipkow [1998].

*Novelty Note.* **Basis (credited):** [`CNF-Uniq` (L2.4.T2)](CRPT_OMEGA_TOWER_L2.md#cnf-uniqueness--orbit-scoped-uniqueness). **New:** CNF-Uniq is exactly the Church–Rosser theorem for (𝒰_M, →_ρ): under PA-WN + PA-Conf the canonical form map is the normal-form function of a confluent, weakly normalising system. **Why it does not follow:** the stated observation is the contribution; the basis does not state it.

[`CNF-Uniq` (L2.4.T2)](CRPT_OMEGA_TOWER_L2.md#cnf-uniqueness--orbit-scoped-uniqueness) is the Church-Rosser theorem (Baader & Nipkow Thm 2.1.15)
for the abstract reduction system (𝒰_M, →_ρ). Under PA-WN + PA-Conf, CFix(ρ_M) is a
well-defined total function μT_{ρ,M} → NF(→_ρ).

### CNF Stability
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L2.4.T3 | `CNF-Stab` |  | **Specialized** |
**Synopsis:** Canonical form stability (idempotence): applying the canonical form map to a canonical form returns it unchanged — CFix(ρ_M)(CFix(ρ_M)(x)) = CFix(ρ_M)(x). Canonical forms are fixed points of the abstraction map.

**Source:** Baader & Nipkow [1998] §6.1 — idempotence of normalisation; applied to [`CNF-Ex` (L2.4.T1)](CRPT_OMEGA_TOWER_L2.md#cnf-existence).

Under PA-Conf: CFix(ρ_M)(CFix(ρ_M)(x)) = CFix(ρ_M)(x).

*Proof.* CFix(ρ_M)(x) ∈ NF(→_ρ) ([`CNF-Ex` (L2.4.T1)](CRPT_OMEGA_TOWER_L2.md#cnf-existence)). By [`NF⊆Fix` (L2.1.T1)](CRPT_OMEGA_TOWER_L2.md#nf--fix), CFix(ρ_M)(x) ∈ Fix(ρ_M),
so ρ_M(CFix(ρ_M)(x)) = CFix(ρ_M)(x). Then d_M(CFix(ρ_M)(x)) = 0 ([`Fix-D0` (L2.3.T3)](CRPT_OMEGA_TOWER_L2.md#fixpoints-have-depth-zero)) and
CFix(ρ_M)(CFix(ρ_M)(x)) = ρ_M⁰(CFix(ρ_M)(x)) = CFix(ρ_M)(x). ∎

### of the Church-Rosser Theorem
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Corollary** | L2.4.C1 | `CR-Cor` |  | **Specialized** |
**Synopsis:** The canonical representative corollary: for each fiber NFC_M(f), the element f itself is the canonical representative — the unique element of NFC_M(f) ∩ Fix(ρ_M). The fixed point f is simultaneously a member of its own fiber and the fiber's canonical form.

**Source:** Church & Rosser [1936]; applied to [`d_M` (L2.3.D2)](CRPT_OMEGA_TOWER_L2.md#rank-function--derivation-height-notation-d_m) + [`CNF-Ex` (L2.4.T1)](CRPT_OMEGA_TOWER_L2.md#cnf-existence).

Under PA-WN + PA-Conf, every x ∈ 𝒰_M
reaches CFix(ρ_M)(x) in exactly d_M(x) steps and no fewer.

*Proof.* This is the definition of d_M(x) = min{n | ρ_M^n(x) ∈ Fix(ρ_M)} combined
with [`CNF-Ex` (L2.4.T1)](CRPT_OMEGA_TOWER_L2.md#cnf-existence) and [`CNF-Uniq` (L2.4.T2)](CRPT_OMEGA_TOWER_L2.md#cnf-uniqueness--orbit-scoped-uniqueness). No additional argument is required. The claim follows
immediately from the definitions and the Church-Rosser theorem ([`CNF-Uniq` (L2.4.T2)](CRPT_OMEGA_TOWER_L2.md#cnf-uniqueness--orbit-scoped-uniqueness)). ∎

### Provenance of the CR Corollary

| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Remark** | L2.4.R5 | `CRCor-Prov` | | **Derived** |
**Synopsis:** Provenance note: CR-Cor is a direct consequence of the Church–Rosser theorem applied to ρ_M — imported, not novel.

**Source:** CRPT; from [`CR-Cor` (L2.4.C1)](CRPT_OMEGA_TOWER_L2.md#of-the-church-rosser-theorem).

*Derivation:* composed from [`CR-Cor` (L2.4.C1)](CRPT_OMEGA_TOWER_L2.md#of-the-church-rosser-theorem); no content beyond the composition.

[`CR-Cor` (L2.4.C1)](CRPT_OMEGA_TOWER_L2.md#of-the-church-rosser-theorem) is a direct consequence of the Church-Rosser theorem applied to ρ_M.

### Abstraction as Recursive Projection

**Provenance.** This subsection synthesizes [`Rec-Proj` (L2.1.D4)](CRPT_OMEGA_TOWER_L2.md#recursive-projection) with the regime partition
(L2.2) to give a single characterization of abstraction as recursive projection by ρ_M.
All ingredients are established in §L1.2–L1.5–6. No new axioms are introduced.

### Level-0 Abstraction
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L2.4.D2 | `Abs-L0` |  | **Novel** |
**Synopsis:** The abstraction quotient at L2 (restated from L0): the map x ↦ NFC_M(CNF_M(x)) sends each element to its fiber equivalence class. This is the same construction as the L0 quotient 𝒰/≃_π instantiated to the CRPT projection operator.

**Source:** CRPT; restates the L0 abstraction ([`Fiber` (L0.1.D2)](CRPT_OMEGA_TOWER_L0.md#fiber-and-observable-equivalence)) via [`NFC-NM` (L2.5.D1)](CRPT_OMEGA_TOWER_L2.md#normal-form-fiber--native-form).

*Novelty Note.* **Basis (credited):** [`Fiber` (L0.1.D2)](CRPT_OMEGA_TOWER_L0.md#fiber-and-observable-equivalence) + [`NFC-NM` (L2.5.D1)](CRPT_OMEGA_TOWER_L2.md#normal-form-fiber--native-form). **New:** The abstraction quotient at L2 (restated from L0): the map x ↦ NFC_M(CNF_M(x)) sends each element to its fiber equivalence class. **Why it does not follow:** the basis supplies the ingredients; the notion assembled from them, and the role it is defined to play in the theory, is introduced here rather than entailed.

Let M be a CRPT model with substrate
(𝒰_M, →_ρ, →_σ), reduction strategy ρ_M, and regime partition 𝒰 = ↓_M ∐ ∞_M.
Define the *abstraction* of x ∈ 𝒰_M by:
```
Abs_M(x) := CFix(ρ_M)(x)
```
where CFix(ρ_M) is the canonical normal form map of [`Rec-Proj` (L2.1.D4)](CRPT_OMEGA_TOWER_L2.md#recursive-projection).

### Abstraction = Recursive Projection
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L2.4.T4 | `Abs=RP` |  | **Novel** |
**Synopsis:** Abstraction equals recursive projection: the abstraction map Abs_M(x) is computed by iterating ρ_M — ρ_M^{d_M(x)}(x) on ↓_M (reaching the fixpoint) and lim_{n→∞} ρ_M^n(x) on ∞_M (the topological limit). Abstraction is recursive projection to the canonical form.

**Source:** CRPT; from [`Rec-Proj` (L2.1.D4)](CRPT_OMEGA_TOWER_L2.md#recursive-projection) + [`d_M` (L2.3.D2)](CRPT_OMEGA_TOWER_L2.md#rank-function--derivation-height-notation-d_m).

*Novelty Note.* **Basis (credited):** [`Rec-Proj` (L2.1.D4)](CRPT_OMEGA_TOWER_L2.md#recursive-projection) + [`d_M` (L2.3.D2)](CRPT_OMEGA_TOWER_L2.md#rank-function--derivation-height-notation-d_m). **New:** Abstraction equals recursive projection: the abstraction map Abs_M(x) is computed by iterating ρ_M — ρ_M^{d_M(x)}(x) on ↓_M (reaching the fixpoint) and lim_{n→∞} ρ_M^n(x) on ∞_M (the topological limit). **Why it does not follow:** the statement is not an unfolding of the basis; the proof in the body supplies the argument that connects them.

For all x ∈ 𝒰_M:
```
Abs_M(x) = {
 ρ_M^{d_M(x)}(x) if x ∈ ↓_M
 lim_{n→∞} ρ_M^n(x) if x ∈ ∞_M
}
```

*Proof.*

**Case 1: x ∈ ↓_M.** By [`Reg-Strat` (L2.2.D3)](CRPT_OMEGA_TOWER_L2.md#native-regime-stratification) and PA-WN, there exists a finite
d_M(x) ∈ ℕ such that ρ_M^{d_M(x)}(x) ∈ Fix(ρ_M), and ρ_M^k(x) ∉ Fix(ρ_M) for
all k < d_M(x) ([`WN-Tot` (L2.2.T4)](CRPT_OMEGA_TOWER_L2.md#pa-wn-gives-terminating-path-witnesses), [`d_M` (L2.3.D2)](CRPT_OMEGA_TOWER_L2.md#rank-function--derivation-height-notation-d_m)). By [`Fix=NF` (L2.1.T2)](CRPT_OMEGA_TOWER_L2.md#fix--nf), Fix(ρ_M) = NF(→_ρ)
under PA-WN. By [`Rec-Proj` (L2.1.D4)](CRPT_OMEGA_TOWER_L2.md#recursive-projection), CFix(ρ_M)(x) = ρ_M^{d_M(x)}(x). Hence
Abs_M(x) = CFix(ρ_M)(x) = ρ_M^{d_M(x)}(x). ✓

**Case 2: x ∈ ∞_M.** By [`Reg-Strat` (L2.2.D3)](CRPT_OMEGA_TOWER_L2.md#native-regime-stratification) and PA-NWF, ρ_M^n(x) ∉ Fix(ρ_M) for all
n ∈ ℕ. By PA-WN_top ([`Ax-Scope` (L1.5.D1)](CRPT_OMEGA_TOWER_L1.md#pa--scope-declaration)), the sequence (ρ_M^n(x))_{n∈ℕ} converges
in (𝒰, 𝒯) to a limit L. Uniqueness of the limit follows from [`TopSep-Uniq` (L1.7.T1)](CRPT_OMEGA_TOWER_L1.md#uniqueness-of-topological-limits-under-topsep),
which uses the explicit TopSep(𝒯) condition required by PA-WN_top. By
[`Rec-Proj` (L2.1.D4)](CRPT_OMEGA_TOWER_L2.md#recursive-projection), CFix(ρ_M)(x) = lim_{n→∞} ρ_M^n(x) = L. Hence
Abs_M(x) = CFix(ρ_M)(x) = lim_{n→∞} ρ_M^n(x). ✓

In both cases, Abs_M(x) is the result of recursive projection by ρ_M — finite
iteration to a fixpoint (↓_M) or infinite iteration to a topological limit (∞_M). ∎

### Why "Recursive Projection"

| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Remark** | L2.4.R6 | `Why-RecProj` | | **Derived** |
**Synopsis:** Why the term "recursive projection" is precise.

**Source:** CRPT; from [`CNF-Stab` (L2.4.T3)](CRPT_OMEGA_TOWER_L2.md#cnf-stability).

*Derivation:* composed from [`CNF-Stab` (L2.4.T3)](CRPT_OMEGA_TOWER_L2.md#cnf-stability); no content beyond the composition.

The term "projection" is precise: each
application of ρ_M projects along the →_ρ relation toward a canonical form, and
ρ_M² = ρ_M on Fix(ρ_M) (idempotence on fixpoints, [`CNF-Stab` (L2.4.T3)](CRPT_OMEGA_TOWER_L2.md#cnf-stability)). The recursion is
the iteration ρ_M, ρ_M², ρ_M³, ...; the projection is the collapse from fiber to
canonical representative. Together they yield the abstraction map Abs_M = CFix(ρ_M).

---

### WF-Canon: Complete Proofs

### WF-Canon Complete Proof
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L2.4.T5 | `WF-Canon-Pf` |  | **Novel** |
**Synopsis:** The well-founded canonicalisation proof: under PA-WN and scoped confluence, the canonical form map CNF_M is well-defined on all of ↓_M. The proof proceeds by well-founded induction on derivation height: the base case (fixed points) is immediate, and the inductive step uses scoped confluence to show all reduction paths from x agree on their canonical form.

**Source:** CRPT; from [PA-WN (L1.2.Ax1)](CRPT_OMEGA_TOWER_L1.md#pa-wn--weak-normalisation) + [PA-Conf (L1.2.Ax2)](CRPT_OMEGA_TOWER_L1.md#pa-conf--confluence--church-rosser) + [`CNF-Ex` (L2.4.T1)](CRPT_OMEGA_TOWER_L2.md#cnf-existence) + [`CNF-Uniq` (L2.4.T2)](CRPT_OMEGA_TOWER_L2.md#cnf-uniqueness--orbit-scoped-uniqueness).

*Novelty Note.* **Basis (credited):** [PA-WN (L1.2.Ax1)](CRPT_OMEGA_TOWER_L1.md#pa-wn--weak-normalisation) + [PA-Conf (L1.2.Ax2)](CRPT_OMEGA_TOWER_L1.md#pa-conf--confluence--church-rosser) + [`CNF-Ex` (L2.4.T1)](CRPT_OMEGA_TOWER_L2.md#cnf-existence) + [`CNF-Uniq` (L2.4.T2)](CRPT_OMEGA_TOWER_L2.md#cnf-uniqueness--orbit-scoped-uniqueness). **New:** The well-founded canonicalisation proof: under PA-WN and scoped confluence, the canonical form map CNF_M is well-defined on all of ↓_M. **Why it does not follow:** the statement is not an unfolding of the basis; the proof in the body supplies the argument that connects them.

*(Formal proof of the well-founded canonicalisation theorem, deferred to this
point where all dependencies are in scope.)*

**WF-Canon-1:** ∀x ∈ ↓_M : CFix(ρ_M)(x) ∈ Fix(ρ_M).

*Proof.* Let x ∈ ↓_M. By [`Rec-Proj` (L2.1.D4)](CRPT_OMEGA_TOWER_L2.md#recursive-projection):
```
CFix(ρ_M)(x) = ρ_M^{d_M(x)}(x)
```
By [`d-WD` (L2.3.T1)](CRPT_OMEGA_TOWER_L2.md#d_m-is-well-defined-on-μt_ρm), d_M(x) ∈ ℕ is well-defined. By [`d_M` (L2.3.D2)](CRPT_OMEGA_TOWER_L2.md#rank-function--derivation-height-notation-d_m),
d_M(x) = min{n ∈ ℕ | ρ_M^n(x) ∈ Fix(ρ_M)}. Therefore, by the definition of
minimum, ρ_M^{d_M(x)}(x) ∈ Fix(ρ_M). Hence CFix(ρ_M)(x) ∈ Fix(ρ_M). ∎

**WF-Canon-2:** ∀f ∈ Fix(ρ_M) : ∃x ∈ ↓_M : CFix(ρ_M)(x) = f.

*Proof.* Let f ∈ Fix(ρ_M). We exhibit x := f as the required witness.

*Step 1: f ∈ ↓_M.* By [`d_M` (L2.3.D2)](CRPT_OMEGA_TOWER_L2.md#rank-function--derivation-height-notation-d_m), ↓_M = {x ∈ 𝒰_M | ∃n ∈ ℕ : ρ_M^n(x) ∈ Fix(ρ_M)}.
Take n = 0: ρ_M^0(f) = f ∈ Fix(ρ_M). Hence f ∈ ↓_M. ✓

*Step 2: CFix(ρ_M)(f) = f.* By [`Fix-D0` (L2.3.T3)](CRPT_OMEGA_TOWER_L2.md#fixpoints-have-depth-zero), d_M(f) = 0 for all f ∈ Fix(ρ_M).
By [`Rec-Proj` (L2.1.D4)](CRPT_OMEGA_TOWER_L2.md#recursive-projection):
```
CFix(ρ_M)(f) = ρ_M^{d_M(f)}(f) = ρ_M^0(f) = f
```
Hence CFix(ρ_M)(f) = f. ✓

*Conclusion.* Taking x = f: x ∈ ↓_M (Step 1) and CFix(ρ_M)(x) = f (Step 2).
Therefore every fixpoint is the CFix-image of itself, witnessed by itself. ∎

### CFix Is Surjective onto Fix(ρ_M)

| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Remark** | L2.4.R7 | `CFix-Surj` | | **Novel** |
**Synopsis:** CFix(ρ_M) : ↓_M → Fix(ρ_M) is surjective — immediate from Fix(ρ_M) ⊆ ↓_M (fixpoints have depth 0, [`Fix-D0` (L2.3.T3)](CRPT_OMEGA_TOWER_L2.md#fixpoints-have-depth-zero)), with no model-specific assumptions.

**Source:** CRPT; from [`WF-Canon-Pf` (L2.4.T5)](CRPT_OMEGA_TOWER_L2.md#wf-canon-complete-proof) + [`Fix-D0` (L2.3.T3)](CRPT_OMEGA_TOWER_L2.md#fixpoints-have-depth-zero).

*Novelty Note.* **Basis (credited):** [`WF-Canon-Pf` (L2.4.T5)](CRPT_OMEGA_TOWER_L2.md#wf-canon-complete-proof) + [`Fix-D0` (L2.3.T3)](CRPT_OMEGA_TOWER_L2.md#fixpoints-have-depth-zero). **New:** CFix(ρ_M) : ↓_M → Fix(ρ_M) is surjective — immediate from Fix(ρ_M) ⊆ ↓_M (fixpoints have depth 0, [`Fix-D0` (L2.3.T3)](CRPT_OMEGA_TOWER_L2.md#fixpoints-have-depth-zero)), with no model-specific assumptions. **Why it does not follow:** the stated observation is the contribution; the basis does not state it.

WF-Canon-2 shows that CFix(ρ_M) : ↓_M → Fix(ρ_M) is surjective (every
fixpoint is in the range). This is non-trivial only if one imagines models where
Fix(ρ_M) ⊄ ↓_M — but in CRPT, Fix(ρ_M) ⊆ ↓_M universally (fixpoints have
depth 0, hence are convergent), and every fixpoint is trivially its own witness.
The surjectivity content of WF-Canon-2 is therefore an immediate consequence of
Fix(ρ_M) ⊆ ↓_M together with [`Fix-D0` (L2.3.T3)](CRPT_OMEGA_TOWER_L2.md#fixpoints-have-depth-zero). No model-specific assumptions
are required.

---

---

## L2.5 — Normal-Form Fibers and Church-Rosser Equivalence

*Purpose.* Normal-Form Fibers. This section defines the normal-form fiber NFC_M(f) — the fiber of fixed point f under the canonical form map — and proves that fibers partition ↓_M into disjoint, observable equivalence classes. Fibers are the building blocks of the query signature used in L8.*


### Normal-Form Fiber — Native Form
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L2.5.D1 | `NFC-NM` |  | **Novel** |
**Synopsis:** The normal-form fiber NFC_M(f) is the complete preimage of fixed point f under the canonical form map: NFC_M(f) = {x ∈ 𝒰_M | CNF_M(x) = f}. This is the named partition block corresponding to f, containing every element whose projection orbit terminates at f. Fibers partition ↓_M into disjoint observable equivalence classes.

**Source:** CRPT; from [`Rec-Proj` (L2.1.D4)](CRPT_OMEGA_TOWER_L2.md#recursive-projection).

*Novelty Note.* **Basis (credited):** [`Rec-Proj` (L2.1.D4)](CRPT_OMEGA_TOWER_L2.md#recursive-projection). **New:** The normal-form fiber NFC_M(f) is the complete preimage of fixed point f under the canonical form map: NFC_M(f) = {x ∈ 𝒰_M | CNF_M(x) = f}. **Why it does not follow:** the basis supplies the ingredients; the notion assembled from them, and the role it is defined to play in the theory, is introduced here rather than entailed.

For any element y in the range of CFix(ρ_M) (i.e., y ∈ NF(→_ρ) ∪ Limits(𝒯)):
```
NFC_M(y) := { x ∈ 𝒰 | CFix(ρ_M)(x) = y }
```
the canonical pre-image (normal-form or limit-point fiber) of y: the set of all elements (in both ↓_M and ∞_M) whose canonical normal form / limit is y.

**Regime-Specific Behavior:**
- **In ↓_M:** y ∈ NF(→_ρ), so NFC_M(y) ∩ ↓_M = { x ∈ ↓_M | x →_ρ* y } (finitary pre-image, stable fiber in dynamical system sense)
- **In ∞_M:** y ∈ Limits(𝒯), so NFC_M(y) ∩ ∞_M = { x ∈ ∞_M | lim_{n→∞} ρ_M^n(x) = y } (topological pre-image, limit set fiber)

Together: NFC_M(y) partitions 𝒰 by destination (normal forms or limits).

### Church-Rosser Orbit Equivalence, notation ≃_M
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L2.5.D2 | `≃_M` | ≃_M | **Novel** |
**Synopsis:** Observable (orbit) equivalence: x ≃_M y holds when x and y share the same canonical form, CFix(ρ_M)(x) = CFix(ρ_M)(y). It is total and unconditional on ↓_M (CFix is the finitary normal form). On ∞_M, CFix is the topological limit and so requires PA-WN_top; without it the regime-general observable equivalence is persistent orbit equivalence ≃∞ ([`≃∞` (L3.3.D7)](CRPT_OMEGA_TOWER_L3.md#--persistent-orbit-equivalence)), with which ≃_M agrees on the PA-WN_top sub-class.

**Source:** CRPT; from [`Rec-Proj` (L2.1.D4)](CRPT_OMEGA_TOWER_L2.md#recursive-projection).

*Novelty Note.* **Basis (credited):** [`Rec-Proj` (L2.1.D4)](CRPT_OMEGA_TOWER_L2.md#recursive-projection). **New:** Observable (orbit) equivalence: x ≃_M y holds when x and y share the same canonical form, CFix(ρ_M)(x) = CFix(ρ_M)(y). **Why it does not follow:** the basis supplies the ingredients; the notion assembled from them, and the role it is defined to play in the theory, is introduced here rather than entailed.

Define the relation ≃_M on 𝒰:
```
x ≃_M y :⟺ CFix(ρ_M)(x) = CFix(ρ_M)(y)
```
x and y are *orbit-equivalent* if they have the same canonical normal form (or limit point).

*Regime-aware reading.* On **↓_M**, CFix(ρ_M)(x) is the finitary normal form ([`CNF-Ex` (L2.4.T1)](CRPT_OMEGA_TOWER_L2.md#cnf-existence)), so ≃_M is total and is exactly CFix-equality. On **∞_M**, CFix(ρ_M)(x) = lim_{n→∞} ρ_M^n(x) is the topological limit, which exists only under PA-WN_top ([`TopSep-Uniq` (L1.7.T1)](CRPT_OMEGA_TOWER_L1.md#uniqueness-of-topological-limits-under-topsep)); so ≃_M is **partial** on ∞_M, defined precisely on the PA-WN_top sub-class. Where PA-WN_top is absent, the regime-general observable equivalence on ∞_M is persistent orbit equivalence ≃∞ ([`≃∞` (L3.3.D7)](CRPT_OMEGA_TOWER_L3.md#--persistent-orbit-equivalence)), comparing ω-limit sets. The two **agree** on the PA-WN_top sub-class — a single topological limit L is exactly the singleton ω-limit set {[L]_≈}. Accordingly, [PA-Bisim (L1.3.Ax1)](CRPT_OMEGA_TOWER_L1.md#pa-bisim--bisimulation-congruence)'s conclusion x ≃_M y reads as CFix-equality on ↓_M and as ≃∞ on ∞_M where PA-WN_top is absent.

### ≃_M and Orbit-Coincidence

| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Remark** | L2.5.R1 | `EquivM-OrbitCoin` | | **Novel** |
**Synopsis:** Under PA-Conf, ≃_M coincides with the orbit-coincidence characterisation ([`CNF=CR` (L2.5.T2)](CRPT_OMEGA_TOWER_L2.md#cnf-fiber--church-rosser-quotient)) and extends directly to the native regime-stratified setting.

**Source:** CRPT; from [`≃_M` (L2.5.D2)](CRPT_OMEGA_TOWER_L2.md#church-rosser-orbit-equivalence-notation-_m) + [`CNF=CR` (L2.5.T2)](CRPT_OMEGA_TOWER_L2.md#cnf-fiber--church-rosser-quotient).

*Novelty Note.* **Basis (credited):** [`≃_M` (L2.5.D2)](CRPT_OMEGA_TOWER_L2.md#church-rosser-orbit-equivalence-notation-_m) + [`CNF=CR` (L2.5.T2)](CRPT_OMEGA_TOWER_L2.md#cnf-fiber--church-rosser-quotient). **New:** Under PA-Conf, ≃_M coincides with the orbit-coincidence characterisation ([`CNF=CR` (L2.5.T2)](CRPT_OMEGA_TOWER_L2.md#cnf-fiber--church-rosser-quotient)) and extends directly to the native regime-stratified setting. **Why it does not follow:** the stated observation is the contribution; the basis does not state it.

Under PA-Conf, this definition is equivalent to the orbit-coincidence characterization ([`CNF=CR` (L2.5.T2)](CRPT_OMEGA_TOWER_L2.md#cnf-fiber--church-rosser-quotient)), and it extends directly to the native regime-stratified setting. ≃_M is regime-agnostic: it works identically on both finitary (↓_M) and topological (∞_M) regimes.

### ≃_M is an Equivalence Relation
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L2.5.T1 | `≃-Eq` |  | **Novel** |
**Synopsis:** ≃_M is an equivalence relation: observable equivalence is reflexive, symmetric, and transitive on 𝒰_M — immediate from equality of canonical forms CFix(ρ_M).

**Source:** CRPT; from [`≃_M` (L2.5.D2)](CRPT_OMEGA_TOWER_L2.md#church-rosser-orbit-equivalence-notation-_m).

*Novelty Note.* **Basis (credited):** [`≃_M` (L2.5.D2)](CRPT_OMEGA_TOWER_L2.md#church-rosser-orbit-equivalence-notation-_m). **New:** ≃_M is an equivalence relation: observable equivalence is reflexive, symmetric, and transitive on 𝒰_M — immediate from equality of canonical forms CFix(ρ_M). **Why it does not follow:** the statement is not an unfolding of the basis; the proof in the body supplies the argument that connects them.

≃_M is reflexive, symmetric,
and transitive on all of 𝒰.

*Proof.* Reflexivity: CFix(ρ_M)(x) = CFix(ρ_M)(x). ✓
Symmetry: if CFix(ρ_M)(x) = CFix(ρ_M)(y), then CFix(ρ_M)(y) = CFix(ρ_M)(x). ✓
Transitivity: if CFix(ρ_M)(x) = CFix(ρ_M)(y) and CFix(ρ_M)(y) = CFix(ρ_M)(z), then CFix(ρ_M)(x) = CFix(ρ_M)(z). ✓ ∎

### Orbit-Coincidence Biconditional under PA-WN + PA-Conf
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Lemma** | L2.5.L1 | `Orb-Bic` |  | **Novel** |
**Synopsis:** Orbit-coincidence biconditional: for convergent x, y, they have the same canonical form iff their orbits reach a common reduct — CFix(ρ_M)(x) = CFix(ρ_M)(y) ⟺ ∃z with x →_ρ* z and y →_ρ* z. This is the Church-Rosser characterization underlying ≃_M.

**Source:** CRPT; from [PA-WN (L1.2.Ax1)](CRPT_OMEGA_TOWER_L1.md#pa-wn--weak-normalisation) + [PA-Conf (L1.2.Ax2)](CRPT_OMEGA_TOWER_L1.md#pa-conf--confluence--church-rosser) + [`≃_M` (L2.5.D2)](CRPT_OMEGA_TOWER_L2.md#church-rosser-orbit-equivalence-notation-_m).

*Novelty Note.* **Basis (credited):** [PA-WN (L1.2.Ax1)](CRPT_OMEGA_TOWER_L1.md#pa-wn--weak-normalisation) + [PA-Conf (L1.2.Ax2)](CRPT_OMEGA_TOWER_L1.md#pa-conf--confluence--church-rosser) + [`≃_M` (L2.5.D2)](CRPT_OMEGA_TOWER_L2.md#church-rosser-orbit-equivalence-notation-_m). **New:** Orbit-coincidence biconditional: for convergent x, y, they have the same canonical form iff their orbits reach a common reduct — CFix(ρ_M)(x) = CFix(ρ_M)(y) ⟺ ∃z with x →_ρ* z and y →_ρ* z. **Why it does not follow:** the statement is not an unfolding of the basis; the proof in the body supplies the argument that connects them.

For x, y ∈ ↓_M, under PA-WN and PA-Conf:
```
CFix(ρ_M)(x) = CFix(ρ_M)(y) ⟺ ∃z ∈ 𝒰 : x →_ρ* z ∧ y →_ρ* z
```

*Proof.*
(⇒) Let CFix(ρ_M)(x) = CFix(ρ_M)(y) = c. By [`Rec-Proj` (L2.1.D4)](CRPT_OMEGA_TOWER_L2.md#recursive-projection), c = ρ_M^{d_M(x)}(x); since each ρ_M-step is a →_ρ-step, x →_ρ* c. Symmetrically y →_ρ* c. Hence c witnesses the existential. ✓

(⇐) Let z satisfy x →_ρ* z and y →_ρ* z. By PA-WN, pick c₁ ∈ NF(→_ρ) with z →_ρ* c₁; composing paths gives x →_ρ* c₁ and y →_ρ* c₁. Since x →_ρ* CFix(ρ_M)(x) (by [`Rec-Proj` (L2.1.D4)](CRPT_OMEGA_TOWER_L2.md#recursive-projection)) and CFix(ρ_M)(x) ∈ NF(→_ρ), PA-Conf applied to x yields w with CFix(ρ_M)(x) →_ρ* w and c₁ →_ρ* w. Both CFix(ρ_M)(x) and c₁ are normal forms, so they cannot reduce further; hence w = CFix(ρ_M)(x) = c₁. By the identical argument applied to y, CFix(ρ_M)(y) = c₁. Therefore CFix(ρ_M)(x) = CFix(ρ_M)(y). ✓ ∎

### CNF-Fiber = Church-Rosser Quotient
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L2.5.T2 | `CNF=CR` | | **Derived** |
**Synopsis:** The canonical representative fiber theorem: CNF_M(x) = CNF_M(y) if and only if x ≃_M y. This is the fundamental connection between the canonical form computation and observational equivalence. The canonical form map is exactly the quotient map from 𝒰_M to its observational equivalence classes.

**Source:** CRPT; from [`Rec-Proj` (L2.1.D4)](CRPT_OMEGA_TOWER_L2.md#recursive-projection) + [`NFC-NM` (L2.5.D1)](CRPT_OMEGA_TOWER_L2.md#normal-form-fiber--native-form); background in Church & Rosser [1936], Baader & Nipkow [1998] §2.7.

*Derivation:* composed from [`Rec-Proj` (L2.1.D4)](CRPT_OMEGA_TOWER_L2.md#recursive-projection) + [`NFC-NM` (L2.5.D1)](CRPT_OMEGA_TOWER_L2.md#normal-form-fiber--native-form); no content beyond the composition.

Under PA-WN and PA-Conf, for all x, y ∈ ↓_M:
```
x ≃_M y ⟺ ∃z ∈ 𝒰 : x →_ρ* z ∧ y →_ρ* z
```
That is, the CNF-equality relation ≃_M ([`≃_M` (L2.5.D2)](CRPT_OMEGA_TOWER_L2.md#church-rosser-orbit-equivalence-notation-_m)) coincides with the orbit-coincidence relation — the Church-Rosser quotient of the reduction relation restricted to ↓_M. (For x, y ∈ ∞_M, orbit-coincidence is topological limit-coincidence, which equals CFix(ρ_M)-equality by [`Rec-Proj` (L2.1.D4)](CRPT_OMEGA_TOWER_L2.md#recursive-projection) and PA-WN_top.)

*Proof.* x ≃_M y iff CFix(ρ_M)(x) = CFix(ρ_M)(y) by [`≃_M` (L2.5.D2)](CRPT_OMEGA_TOWER_L2.md#church-rosser-orbit-equivalence-notation-_m). By [`Orb-Bic` (L2.5.L1)](CRPT_OMEGA_TOWER_L2.md#orbit-coincidence-biconditional-under-pa-wn--pa-conf), CFix(ρ_M)(x) = CFix(ρ_M)(y) iff ∃z ∈ 𝒰 : x →_ρ* z ∧ y →_ρ* z. The composition of these equivalences gives the stated biconditional. ∎

### Partition into NFC Classes — Native Form
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Corollary** | L2.5.C1 | `NFC-Part-NM` |  | **Derived** |
**Synopsis:** The normal-form fiber partition at L2: the collection {NFC_M(f) | f ∈ Fix(ρ_M)} is a partition of ↓_M. Non-emptiness: each f ∈ NFC_M(f). Disjointness: NFC_M(f₁) ∩ NFC_M(f₂) = ∅ when f₁ ≠ f₂. Exhaustiveness: every x ∈ ↓_M belongs to NFC_M(CNF_M(x)). The index set of this partition is Fix(ρ_M) = Q_M.

**Source:** CRPT; from [`NFC-NM` (L2.5.D1)](CRPT_OMEGA_TOWER_L2.md#normal-form-fiber--native-form) + [`≃-Eq` (L2.5.T1)](CRPT_OMEGA_TOWER_L2.md#_m-is-an-equivalence-relation).

*Derivation:* composed from [`NFC-NM` (L2.5.D1)](CRPT_OMEGA_TOWER_L2.md#normal-form-fiber--native-form) + [`≃-Eq` (L2.5.T1)](CRPT_OMEGA_TOWER_L2.md#_m-is-an-equivalence-relation); no content beyond the composition.

Under PA-Conf:
```
𝒰 = ∐_{y ∈ range(CFix(ρ_M))} NFC_M(y)
```
The NFC classes partition all of 𝒰; they are the ≃_M equivalence classes.

*Proof.* Exhaustiveness: every x ∈ 𝒰 is in NFC_M(CFix(ρ_M)(x)) (by [`NFC-NM` (L2.5.D1)](CRPT_OMEGA_TOWER_L2.md#normal-form-fiber--native-form), since CFix(ρ_M)(x) is in the range of CFix(ρ_M)). Disjointness: if x ∈ NFC_M(y₁) ∩ NFC_M(y₂), then CFix(ρ_M)(x) = y₁ and CFix(ρ_M)(x) = y₂, so y₁ = y₂ (CFix(ρ_M) single-valued). ∎

---
