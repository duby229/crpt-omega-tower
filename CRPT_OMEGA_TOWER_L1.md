# L1 — CRPT Substrate, Axioms, Regimes, and Modes

## L1.1 — The Substrate

*Purpose.* The CRPT Substrate. This section introduces the four-component substrate (𝒰_M, →_ρ, →_σ, 𝒯) that every CRPT model inhabits, together with the derived notions — normal forms, iterated reduction, bisimulation — that all subsequent theory presupposes. Everything in L2–Lω depends on this definition.*


The substrate is the axiom-free base. Every construct here is a definition.
No axioms are assumed in L1.1.

### Primitives

### Substrate
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L1.1.D1 | `Sub` | (𝒰, →_ρ, →_σ, 𝒯) | **Novel** |
**Synopsis:** The CRPT substrate is the minimal mathematical environment in which projection theory operates. It consists of four components: a universe 𝒰_M of elements, a reduction relation encoding the projection strategy, a structural relation encoding observational connectivity, and a topology 𝒯 for limiting behaviour. Every CRPT model lives inside a substrate; the axiom system (L1.2–L1.5) then selects which substrates qualify as genuine CRPT models.

**Source:** CRPT; from abstract reduction systems (Baader & Nipkow [1998] §2.1) + topological spaces (Munkres [2000]).


A *substrate* is an ordered quadruple (𝒰, →_ρ, →_σ, 𝒯)
where:
- 𝒰 is a class. Elements of 𝒰 are called *structures*.
- →_ρ ⊆ 𝒰 × 𝒰 is a binary relation called the *reduction relation*.
 We write x →_ρ y for (x, y) ∈ →_ρ.
- →_σ ⊆ 𝒰 × 𝒰 is a binary relation called the *structural relation*.
 We write x →_σ y for (x, y) ∈ →_σ.
- 𝒯 is a topology on 𝒰.
- **Inclusion constraint:** →_ρ ⊆ →_σ. Every reduction step is a structural step.

No further properties of 𝒰, →_ρ, →_σ, or 𝒯 are assumed at substrate-definition level.
The global topological requirements TopSep(𝒯) and continuity of ρ are imposed
as axioms in L5.2 (and used by PA-WN_top / CFix in the topological regime).
The inclusion constraint
is part of the definition of what it means to be a substrate, not an axiom.

### Why Two Relations

| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Remark** | L1.1.R1 | `Two-Rel` | | **Novel** |
**Synopsis:** Why the substrate carries two relations: →_ρ for projection and →_σ for structure.

**Source:** CRPT; from `Sub` (L1.1.D1).

The two-relation substrate serves two independent structural purposes:
1. **→_ρ for recursive projection:** All core CRPT axioms (PA-WN, PA-Conf, PA-Fix, PA-NWF, PA-CoInd, PA-Prod, PA-Bisim) constrain the projection operator ρ_M acting on →_ρ.
2. **→_σ for horizontal structure:** The structural relation →_σ is used in observation (L2.2), Gateway definition (L4.2), and regime connectivity analysis. The distinction is necessary because →_ρ is projection-sequential (determining what ρ_M reaches), while →_σ is structural-ambient (determining what observables see).

3. **Separation required for PA-Reach:** PA-Reach (L1.3) constrains recursive projection ρ_M in the persistent regime, guaranteeing orbit signature stabilization. This requires the two-relation design: if →_ρ and →_σ were a single relation →, then bisimulation-equivariance (C2: x ≈ y ⟹ ρ_M(x) ≈ ρ_M(y)) combined with PA-Conf would force every non-fixpoint x to have a unique →-successor, making non-deterministic →-branches impossible and trivializing PA-NWF. The separation keeps projection (→_ρ) semantically distinct from observation (→_σ), preventing observability constraints from interfering with the core projection axiom system.

### Derived Constructs

All of the following are definitions. No axioms are required.

### Normal Form
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L1.1.D2 | `NF` | NF(→_ρ) | **Imported** |
**Synopsis:** A normal form is an element that cannot be reduced further — it is already in its simplest form under the reduction relation. Normal forms are the resting states of the system; they become the canonical reference points for the equivalence classes defined in L2.

**Source:** Baader & Nipkow [1998] *Term Rewriting and All That* §2.1; Terese [2003] — normal form of an abstract reduction system.

x ∈ 𝒰 is a *normal form* if
```
NF(x) :⟺ ¬∃y ∈ 𝒰 : x →_ρ y
```
The set of normal forms is NF(→_ρ) := {x ∈ 𝒰 | NF(x)}.

### n-Step Reduction
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L1.1.D3 | `n-Step` | →_ρ^n | **Imported** |
**Synopsis:** The n-step reduction relation →_ρ^n relates x to y when y is reachable from x in exactly n steps of the reduction relation. This is the iterative counterpart to the projection operator: while the projection operator selects one canonical step, n-step reduction allows all reachable paths. It is used in the axiom statements to quantify orbit length.

**Source:** Baader & Nipkow [1998] *Term Rewriting and All That* §2.1 — n-step reduction relation.

Define →_ρⁿ ⊆ 𝒰 × 𝒰 by induction on n ∈ ℕ:
```
x →_ρ⁰ y :⟺ x = y
x →_ρⁿ⁺¹ y :⟺ ∃z ∈ 𝒰 : x →_ρ z ∧ z →_ρⁿ y
```
Here ℕ is the ambient (meta-level) natural numbers; it is not yet an object of 𝒰.

### Reflexive-Transitive Closure
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L1.1.D4 | `RT*` | →_ρ* | **Imported** |
**Synopsis:** The reflexive-transitive closure →_ρ* relates x to y when y is reachable from x in zero or more reduction steps. It is the standard ARS reachability relation and appears in the axiom PA-Reach and in the definitions of regimes.

**Source:** Baader & Nipkow [1998] *Term Rewriting and All That* §2.1; Huet [1980] — reflexive-transitive closure of a reduction relation.

```
x →_ρ* y :⟺ ∃n ∈ ℕ : x →_ρⁿ y
```
Reflexivity (x →_ρ* x) and transitivity (x →_ρ* y ∧ y →_ρ* z ⟹ x →_ρ* z) follow
immediately. Similarly define →_σ* using →_σ in place of →_ρ. By the inclusion
constraint, x →_ρ* y ⟹ x →_σ* y.

### Diverging Elements
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L1.1.D5 | `Div` | Div(→_ρ) | **Imported** |
**Synopsis:** Divergence is the property of having an infinite reduction sequence — an element from which the reduction relation can be applied indefinitely without reaching a normal form. Elements that diverge are candidates for the persistent regime; those that do not are in the convergent regime.

**Source:** Baader & Nipkow [1998] *Term Rewriting and All That* §2.1 — divergence (existence of an infinite reduction sequence).

x ∈ 𝒰 *diverges* (written x ∈ Div(→_ρ))
if there exists an infinite →_ρ-sequence from x:
```
x ∈ Div(→_ρ) :⟺ ∃σ : ℕ → 𝒰 : σ(0) = x ∧ ∀n ∈ ℕ : σ(n) →_ρ σ(n+1)
```
The set Div(→_ρ) := {x ∈ 𝒰 | x ∈ Div(→_ρ)}.

### Divergence Is Not Substrate-Determined

| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Remark** | L1.1.R2 | `Div-NotDet` | | **Novel** |
**Synopsis:** See the remark.

**Source:** CRPT; from `Div` (L1.1.D5).

Whether Div(→_ρ) is empty or non-empty is not determined by the
substrate. It depends on axioms added at L1.2–L1.5.

### Bisimulation
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L1.1.D6 | `Bisim` | | **Imported** |
**Synopsis:** Bisimilarity ≈ is the largest bisimulation — the union of all bisimulations. Two elements are bisimilar exactly when they cannot be distinguished by any finite or infinite sequence of reductions. This is the finest observational equivalence derivable from the substrate structure alone.

**Source:** Park [1981] *Concurrency and Automata on Infinite Sequences*, LNCS 104, pp. 167–183; Milner [1989] *Communication and Concurrency* — bisimulation.

A relation R ⊆ 𝒰 × 𝒰 is a *bisimulation on
(𝒰, →_ρ)* if for all (x, y) ∈ R:
- *Forward:* ∀x' : x →_ρ x' ⟹ ∃y' : y →_ρ y' ∧ (x', y') ∈ R
- *Backward:* ∀y' : y →_ρ y' ⟹ ∃x' : x →_ρ x' ∧ (x', y') ∈ R

### Bisimilarity
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L1.1.D7 | `Bisim~` | ≈ | **Imported** |
**Synopsis:** Bisimilarity is the largest bisimulation — the union of all bisimulations. Two elements are bisimilar exactly when they cannot be distinguished by any finite or infinite sequence of reductions.

**Source:** Park [1981] LNCS 104; Milner [1989] *Communication and Concurrency* — bisimilarity as the largest bisimulation (greatest fixed point).

The *bisimilarity relation* ≈ is the largest
bisimulation on (𝒰, →_ρ):
```
x ≈ y :⟺ ∃R (bisimulation) : (x, y) ∈ R
```

### Union of Bisimulations is a Bisimulation
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Lemma** | L1.1.L1 | `Bisim-Union` | | **Imported** |
**Synopsis:** The union of any family of bisimulations is itself a bisimulation. This is the standard lemma that makes bisimilarity (the largest bisimulation) well-defined: we can take the union of all bisimulations without leaving the class of bisimulations.

**Source:** Park [1981] LNCS 104; Milner [1989] *Communication and Concurrency* — union of bisimulations is a bisimulation.

If {Rᵢ}ᵢ∈I is any
family of bisimulations on (𝒰, →_ρ), then ∪ᵢ Rᵢ is also a bisimulation.

*Proof.* Let (x, y) ∈ ∪Rᵢ. Then (x, y) ∈ Rⱼ for some j. Since Rⱼ is a bisimulation:
Forward — if x →_ρ x', then ∃y' : y →_ρ y' ∧ (x', y') ∈ Rⱼ ⊆ ∪Rᵢ. ✓
Backward — symmetric. ✓ ∎

### ≈ is an Equivalence Relation
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Lemma** | L1.1.L2 | `≈-Eq` | | **Imported** |
**Synopsis:** Bisimilarity ≈ is an equivalence relation — reflexive, symmetric, and transitive — since the identity relation is a bisimulation and bisimulations are closed under inverse and composition.

**Source:** Milner [1989] *Communication and Concurrency* §2.2; Park [1981] LNCS 104.

≈ is reflexive, symmetric, and
transitive.

*Proof.*
- *Reflexivity:* {(x, x) | x ∈ 𝒰} is a bisimulation (trivially). Hence x ≈ x. ✓
- *Symmetry:* If R is a bisimulation, so is R⁻¹ (swap forward and backward). Hence
 x ≈ y ⟹ y ≈ x. ✓
- *Transitivity:* If R₁, R₂ are bisimulations, so is their composition R₁ ∘ R₂
 (standard argument: follow R₁ forward then R₂ forward). Hence x ≈ y ∧ y ≈ z ⟹
 x ≈ z. ✓ ∎

### Bisimilarity Is Not Equality

| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Remark** | L1.1.R3 | `Bisim-NotEq` | | **Novel** |
**Synopsis:** See the remark.

**Source:** CRPT; from `Bisim~` (L1.1.D7) + PA-Bisim (L1.3.Ax1).

The substrate does NOT assert that bisimilar elements are equal (x ≈ y
⟹ x = y). That is the content of axiom `PA-Bisim` (L1.3.Ax1), stated at the axiom level.
Here ≈ is defined as a congruence; its relationship to identity is axiom-governed.

### Discernibility: Bisimilarity

| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Remark** | L1.1.R4 | `Disc-Bisim` | | **Novel** |
**Synopsis:** Reading bisimilarity ≈ as the discernibility relation between elements.

**Source:** CRPT; from `Bisim~` (L1.1.D7).

Bisimilarity ≈ is the formal relation
of **mutual indiscernibility**: x ≈ y means no distinction between x and y survives all
forward and backward →_ρ-steps. This makes ≈ the canonical boundary between what
is **discernible** (x ≉ y: some reduction path distinguishes them) and what is
**indiscernible** (x ≈ y: no reduction path distinguishes them) within a substrate.
Every subsequent CRPT construct — horizons, the six-class partition, the observer
triple, the lift — can be understood as characterizing the architecture of
discernibility induced by ≈ and ρ_M.

---

## L1.2 — The Axiom System

*Purpose.* The Projection Axiom System. This section introduces seven of the nine PA-* projection axioms in two groups: three convergent-regime axioms (PA-WN, PA-Conf, PA-Fix) governing behaviour in ↓_M; and four persistent-regime axioms (PA-NWF, PA-CoInd, PA-Prod, PA-WN_top) governing behaviour in ∞_M. Of these, PA-WN equips the convergent regime with finitary mode and PA-WN_top equips part of the persistent regime with topological mode (`Mode` (L1.4.D1)). The two universal axioms (PA-Bisim, PA-Reach) follow in L1.3. All axioms use ρ_M, Fix(ρ_M), and the regimes ↓_M / ∞_M, which are formally defined in L2 — forward-referenced here.*

---

### Convergent-Regime Axioms

These axioms govern elements that reach fixpoints in finitely many →_ρ-steps.

### PA-WN — Weak Normalisation
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Axiom** | L1.2.Ax1 | `PA-WN` | | **Imported** |
**Synopsis:** PA-WN (Weak Normalisation) asserts that every element has at least one terminating →_ρ-path reaching a normal form. This is the foundational finitary-mode axiom: it ensures the convergent regime ↓_M is non-trivial and that the projection strategy always has a reachable fixpoint to aim for.

**Source:** Baader & Nipkow [1998] *Term Rewriting and All That* §2.3; Newman [1942] — weak normalisation.

Every element has a terminating →_ρ-path:
```
∀x ∈ 𝒰 : ∃n ∈ ℕ, ∃y ∈ 𝒰 : x →_ρⁿ y ∧ NF(y)
```

*Standard Name:* WN(→_ρ) — weak normalisation of →_ρ (Baader & Nipkow [1998] §2.1, Def. 2.1.13; Terese [2003] §1.3).

*Logical Status:*
- **Pure WF (∞_M = ∅):** Globally satisfied over all of 𝒰. Every element has at least one terminating →_ρ-path.
- **Native Stratified (both regimes):** Declared `Scoped(↓_M)`: holds for all x ∈ ↓_M. Regime-sensitive usage is handled via scope semantics (`PA-Scope` (L1.5.D1)).
- **Pure NWF (↓_M = ∅):** Not globally satisfied.

*What it adds:* Without PA-WN, ↓_M could be empty. PA-WN ensures the convergent regime is non-trivial and makes CFix(ρ_M) well-defined on ↓_M.

*Remark (WN vs SN).* PA-WN asserts the *existence* of a terminating →_ρ-path — not that *all* →_ρ-paths terminate (strong normalisation). An element x ∈ ↓_M whose ρ_M-orbit terminates may still admit non-deterministic infinite →_ρ-branches; these do not affect x's regime membership or derivation height d_M(x), both defined via the ρ_M-orbit.

### PA-Conf — Confluence / Church-Rosser
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Axiom** | L1.2.Ax2 | `PA-Conf` | | **Imported** |
**Synopsis:** PA-Conf (Confluence / Church-Rosser Property) requires that all →_ρ-paths from the same element converge. Together with PA-WN, confluence ensures normal forms are unique — the canonical form computed by iterating ρ_M does not depend on which →_ρ-path is taken.

**Source:** Church & Rosser [1936]; Baader & Nipkow [1998] *Term Rewriting and All That* §2.7 — confluence (Church–Rosser property).

All →_ρ-paths from the same element converge:
```
∀x, y₁, y₂ ∈ 𝒰 : (x →_ρ* y₁) ∧ (x →_ρ* y₂) ⟹ ∃z ∈ 𝒰 : y₁ →_ρ* z ∧ y₂ →_ρ* z
```

*Standard name:* Church-Rosser property / confluence of →_ρ (Church & Rosser [1936]; Baader & Nipkow [1998] §2.1, Def. 2.1.11).

*Logical Status:*
- **All models:** Globally satisfied, or declared `Scoped(ρ_M-orbits)` when only orbit-level confluence is needed (see `SC-Orb` (L1.5.D5) and `Scope-Suf` (L1.5.T2)).

*What it adds:* Without PA-Conf, different →_ρ-paths from the same element may reach different normal forms. Together with PA-WN, guarantees unique canonical abstraction CFix(ρ_M) in ↓_M.

### PA-Fix — Projection Fixpoint Stratification
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Axiom** | L1.2.Ax3 | `PA-Fix` | | **Novel** |
**Synopsis:** PA-Fix requires that the fixpoints of the projection strategy ρ_M coincide exactly with the →_ρ-normal forms. This pins Fix(ρ_M) as the canonical terminal stratum of projection dynamics, preventing degenerate models where projection-fixpoints and reduction-normal-forms diverge.

**Source:** CRPT; from `Sub` (L1.1.D1) + `NF` (L1.1.D2).

Fixpoints of the projection strategy coincide with reduction normal forms:
```
∀x ∈ 𝒰 : (ρ_M(x) = x) ↔ NF(x)
```

*Logical Status:*
- **All models:** Global scope over 𝒰.

*What it adds:* A projection-level fixpoint boundary used by CFix and regime semantics. WF-Canon (L2) is theorem-level content over this boundary.

### PA Namespace Discipline
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Remark** | L1.2.R1 | `PA-NS` | | **Novel** |
**Synopsis:** The PA-* namespace is reserved exclusively for the nine projection axioms; WF-side orbit canonicalization (WF-Canon) is placed as a theorem and existential richness (LA-Rich) as a model-local axiom, so neither occupies a PA-* slot.

**Source:** CRPT; from the PA-* axiom system (L1.2–L1.3).

The PA-* namespace is reserved exclusively for Projection Axioms (nine total: PA-WN, PA-Conf, PA-Fix, PA-NWF, PA-CoInd, PA-Prod, PA-WN_top, PA-Bisim, PA-Reach). WF-side orbit canonicalization is placed as a theorem (WF-Canon, at L2), not an axiom. Existential richness is placed as a model-local axiom (LA-Rich(M)), not a PA axiom.

---

### Persistent-Regime Axioms

These axioms govern the persistent regime ∞_M where elements never reach fixpoints finitely. PA-WN_top, when present, additionally equips a sub-class of ∞_M with topological mode (`Mode` (L1.4.D1)).

### PA-NWF — Non-Well-Foundedness / Divergence Existence
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Axiom** | L1.2.Ax4 | `PA-NWF` | | **Imported** |
**Synopsis:** PA-NWF (Non-Well-Foundedness) asserts that the substrate admits elements whose ρ_M-orbit never reaches a fixpoint — the persistent regime ∞_M is non-empty. This is the foundational topological-mode axiom and the dual of PA-WN under the WF/NWF duality. In pure WF models it is false; in native stratified models it asserts ∞_M ≠ ∅.

**Source:** Aczel [1988] *Non-Well-Founded Sets* Ch. 1; Forti & Honsell [1983] — non-well-foundedness (divergence existence).

The substrate admits elements that never reach a fixpoint:
```
∃x ∈ 𝒰 : ∀n ∈ ℕ : ρ_M^n(x) ∉ Fix(ρ_M)
```

*Standard Name:* Non-well-foundedness (Aczel [1988]; Milner [1980]). PA-NWF asserts the deterministic strategy ρ_M has a non-terminating orbit, not merely that some →_ρ-path is infinite — those are distinct conditions.

*Logical Status:*
- **Pure WF (∞_M = ∅):** Not satisfied. Mutually exclusive with PA-WN (global) in pure models. In native stratified models, PA-WN is scoped to ↓_M and PA-NWF governs ∞_M; they coexist without contradiction (`Mode-Comp` (L1.4.T1)).
- **Native Stratified:** Satisfied. Asserts ∞_M ≠ ∅.
- **Pure NWF:** Satisfied.

*What it adds:* Without PA-NWF in native models, there would be no persistent regime. PA-NWF is the dual of PA-WN.

### PA-CoInd — Co-Induction / Park's Lemma / Greatest Fixed-Point Reasoning
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Axiom** | L1.2.Ax5 | `PA-CoInd` | | **Imported** |
**Synopsis:** PA-CoInd (Co-Induction) asserts that every predicate closed under the co-induction functional is contained in the greatest fixpoint — this is Park's Lemma. It is the standard coinductive proof principle for the persistent regime. In full second-order logic it is derivable from PA-NWF (proved at `Ax-Ind` (L1.6.T1)); it is retained as an explicit axiom for portability across schema and Henkin-mode proof systems.

**Source:** Park [1981] *Concurrency and Automata on Infinite Sequences*, LNCS 104; Knaster & Tarski [1955] — greatest-fixed-point coinduction principle.

Every predicate closed under the co-induction functional is contained in the greatest fixpoint:
```
∀Φ : 𝒫(𝒰)→𝒫(𝒰) (monotone), ∀P ⊆ 𝒰 : P ⊆ Φ(P) ⟹ P ⊆ νΦ
```

*Standard Name:* Park's Lemma (Park [1981]; Milner [1980] §4). Greatest fixed-point coinduction principle.

*Logical Status:*
- **All models:** Globally satisfied. Enables coinductive proofs over ∞_M.
- **Full SOL:** Derivable from PA-NWF (proved at `Ax-Ind` (L1.6.T1)). Not an independent basis axiom in full second-order semantics.
- **Schema/Henkin modes:** Retained as an explicit axiom for proof-system portability.

*What it adds:* Provides the coinductive proof principle. Without it, coinductive reasoning over ∞_M is not justified in weaker proof systems.

### PA-Prod — Productivity / Guardedness / Observable Content
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Axiom** | L1.2.Ax6 | `PA-Prod` | | **Novel** |
**Synopsis:** PA-Prod (Productivity) requires that persistent elements produce observable content at every step of their orbit: each projection step must yield a new element satisfying the Observable Contract conditions OC-1 and OC-2. This prevents 'silent' non-termination and ensures that the persistent regime has genuine observational content.

**Source:** CRPT; from guardedness/productivity (Coquand [1994]; Sangiorgi [2011] §1.3); the Observable Contract (OC-1, OC-2) is CRPT-original.

Every non-fixpoint element produces observable content at its ρ_M-successor:
```
∀x ∈ 𝒰 : (x ∉ Fix(ρ_M)) ⟹ Observable(ρ_M(x))
```

where Observable(y) is a model-specific predicate (defined at instantiation) satisfying:

**Observable Contract (OC).** Every instantiation must define Observable : 𝒰_M → {⊤, ⊥} such that:
```
(OC-1) ∀y ∈ 𝒰 : (y ∉ Fix(ρ_M)) ⟹ Observable(y)
 [non-fixpoints are always observable]
(OC-2) Observable is compatible with the PV component of the Observer Triple (L4.1):
 Observable(y) ⟹ w(x →_ρ y) ≠ 0_V for every x with ρ_M(x) = y
 [observable steps have non-zero trajectory weight]
```

*Remark (Observable Contract).* Condition (OC-1) means PA-Prod is non-trivial only
when ρ_M(x) ∈ Fix(ρ_M) — i.e., when x is exactly one step from a fixpoint. In
models where Observable is trivially true for all elements (Lambda Calculus, Streams,
ZFA), PA-Prod holds vacuously. In models where fixpoints lack observable content
(QG: β(g*) = 0), the instantiation must handle the fixpoint-endpoint case explicitly
(via the model's Observable contract, `OC-LA_M` (L1.5.R3)). Condition (OC-2) connects Observable to the
Observer Triple (L4.1): Observable is the minimal boolean predicate ensuring the
PV trajectory observable has no zero factors at non-fixpoint steps, so the behavioral
signature is well-defined and non-degenerate at every step of the ρ_M-orbit.

*Consequence (∀n on ∞_M).* By induction on the ρ_M-orbit: for x ∈ ∞_M,
ρ_M^n(x) ∉ Fix(ρ_M) for all n (`∞_M` (L2.2.D5)), so PA-Prod applies at every step:
```
∀x ∈ ∞_M : ∀n ∈ ℕ : Observable(ρ_M^n(x))
```
On ↓_M \ Fix(ρ_M), PA-Prod applies at each step until Fix(ρ_M) is reached:
∀n < d_M(x) : Observable(ρ_M^{n+1}(x)). After step d_M(x), the orbit is at
a fixpoint and no further ρ_M-steps produce new content.

*Remark.* For ↓_M \ Fix(ρ_M), the →_ρ relation terminates at normal forms
(Fix = NF, `Fix=NF` (L2.1.T2)), so there is no n-step →_ρ path for n > d_M(x).
The single-step formulation is therefore the canonical global statement and
preserves the axiom's logical content for downstream uses (`Obs-Const`
(L4.1.T1), `PV2` (L4.3.T2)).

*Standard Name:* Productivity / guardedness condition (Milner [1980] §2.3).

*Logical Status:*
- **All models:** Globally satisfied. Every non-fixpoint ρ_M-step produces observable content; diverging elements produce observables infinitely often (by induction).

*What it adds:* Excludes "silent divergence" where an element diverges without producing observables. Ensures ∞_M elements are actually productive. On ↓_M, ensures every intermediate ρ_M-step before reaching Fix(ρ_M) produces observable output.

### PA-WN_top — Topological Weak Normalisation / Asymptotic Convergence
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Axiom** | L1.2.Ax7 | `PA-WN_top` | | **Novel** |
**Synopsis:** PA-WN_top (Topological Weak Normalisation) requires that every persistent element has a unique topological limit point in 𝒯. This gives persistent orbits a 'destination' even when they never terminate, enabling the coinductive treatment of PA-CoInd. Without PA-WN_top, persistent orbits could wander without any asymptotic structure.

**Source:** CRPT; from PA-NWF (L1.2.Ax4) + topological convergence (Munkres [2000]); the topological-limit axiom is CRPT-original.


*Scope and Interpretation.* This axiom is what certifies **topological mode** (`Mode` (L1.4.D1)): where it holds, persistent elements of ∞_M that do not reach fixpoints finitely nonetheless converge to a limit in a topology 𝒯. It is an optional, independent axiom (`WNtop-Ind` (L1.4.T3)) — persistent elements for which it fails are canonicalized in asymptotic mode instead. The topology 𝒯 declared as part of the substrate (`Sub` (L1.1.D1)) for topological-mode use must satisfy the **T₂ (Hausdorff) separation axiom** (Definition L1.2.D1 below). This requirement is essential for uniqueness of topological limits: in a non-Hausdorff space a sequence can converge to multiple distinct limit points simultaneously, rendering CFix(ρ_M) on ∞_M multi-valued.

```
PA-WN_top:
∀x ∈ ∞_M : ∃!L ∈ 𝒰_M, ∃𝒯-neighborhood basis {U_k}_{k ∈ ℕ} of L :
 ∀k ∈ ℕ ∃N_k ∈ ℕ : ∀n ≥ N_k : ρ_M^n(x) ∈ U_k
```

The ∃! (unique existence) is justified as follows: existence follows from the convergence
condition stated; uniqueness is a consequence of the Hausdorff property of 𝒯 (see
`TopSep-Uniq` (L1.2.T1) below).

*Equivalently:* Every element x ∈ ∞_M has a **unique** limit point L ∈ 𝒰_M in topology 𝒯:
```
lim_{n→∞} ρ_M^n(x) = L (unique, in the Hausdorff topology 𝒯)
```

where 𝒯 is fixed by the substrate Sub = (𝒰, →_ρ, →_σ, 𝒯) and must satisfy TopSep (L1.2.D1).

*Standard Interpretation:* This is **full sequence convergence** (not merely the Bolzano-Weierstrass cluster-point property): the entire orbit sequence ρ_M^n(x) converges to L, not just a subsequence.

### Hausdorff Separation Condition
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L1.2.D1 | `TopSep` | TopSep(𝒯) | **Imported** |
**Synopsis:** Topological separation (the Hausdorff / T₂ condition) requires that distinct limit points are separated by disjoint open sets. Under this condition, sequences have at most one limit. This is the minimal separation condition ensuring that topological limits in the substrate are unique — a prerequisite for PA-WN_top.

**Source:** Hausdorff [1914] *Grundzüge der Mengenlehre*; Munkres [2000] *Topology* §17 — T₂ (Hausdorff) separation axiom.

A topology 𝒯 on 𝒰_M satisfies **TopSep** (the Hausdorff / T₂ condition) if:
```
TopSep(𝒯) :⟺ ∀L₁, L₂ ∈ 𝒰_M : L₁ ≠ L₂ ⟹
 ∃U₁, U₂ ∈ 𝒯 : L₁ ∈ U₁ ∧ L₂ ∈ U₂ ∧ U₁ ∩ U₂ = ∅
```
Any two distinct points can be separated by disjoint open neighborhoods.

*Standard name.* The T₂ separation axiom (Hausdorff [1914]; Munkres [2000] L8.8).
All metric spaces satisfy TopSep. Standard instantiation topologies (ℝ, ℝⁿ,
Banach spaces, metric spaces) are Hausdorff. When PA-WN_top is declared `Vacuous`
(pure WF case with ∞_M = ∅), TopSep imposes no constraint.

### Uniqueness of Topological Limits under TopSep
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L1.2.T1 | `TopSep-Uniq` | | **Imported** |
**Synopsis:** Under the Hausdorff condition TopSep(𝒯), topological limits are unique, so the persistent-regime canonical form CFix(ρ_M)(x) = lim_{n→∞} ρ_M^n(x) is well-defined and single-valued on ∞_M.

**Source:** Munkres [2000] *Topology* Lemma 17.9 — uniqueness of limits in Hausdorff spaces.

If TopSep(𝒯) holds and (ρ_M^n(x))_{n∈ℕ} is a sequence in (𝒰_M, 𝒯) converging to L₁ and also converging to L₂, then L₁ = L₂.

*Proof.* Suppose L₁ ≠ L₂. By TopSep(𝒯), ∃ disjoint open U₁ ∋ L₁, U₂ ∋ L₂.
Since ρ_M^n(x) → L₁: ∃N₁ : ∀n ≥ N₁ : ρ_M^n(x) ∈ U₁.
Since ρ_M^n(x) → L₂: ∃N₂ : ∀n ≥ N₂ : ρ_M^n(x) ∈ U₂.
For n ≥ max(N₁, N₂): ρ_M^n(x) ∈ U₁ ∩ U₂ = ∅. Contradiction. Hence L₁ = L₂. ∎

### Topological Limit via Metric/Order
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L1.2.D2 | `Top-Lim` | | **Imported** |
**Synopsis:** The topological limit structure defines what it means for a sequence of elements to converge to a limit point in the topology 𝒯 of the substrate. This includes limit via neighborhood bases, metric convergence when 𝒯 is metrizable, and order-theoretic monotone limits. The substrate's topology must admit a well-defined limit notion for PA-WN_top to have content.

**Source:** Hausdorff [1914] *Grundzüge der Mengenlehre*; Munkres [2000] *Topology* — topological limit via neighbourhood bases.

For concrete instantiations:
- **Metric spaces:** d(ρ_M^n(x), L) → 0 as n → ∞
- **Topological spaces:** For every neighborhood U of L, ∃N : ∀n ≥ N, ρ_M^n(x) ∈ U
- **Lattices/posets:** ρ_M^n(x) ↓ L (monotone decreasing to L) or ρ_M^n(x) ↑ L (monotone increasing)

*Logical Status:*
- **Pure WF (∞_M = ∅):** Vacuously true. No elements in ∞_M, so the ∀x ∈ ∞_M is satisfied trivially.
- **Native Stratified:** Substantively true on ∞_M. Required to be explicitly satisfied for topological models (R, metric spaces, etc.).
- **Pure NWF:** May be true or false depending on whether the model admits a topology with the required convergence property.

*Philosophical Meaning:* PA-WN_top is the **topological dual of PA-WN** in finitary regime:
- **PA-WN says:** "Finitary iteration converges to fixpoints in ℕ steps"
- **PA-WN_top says:** "Topological iteration converges to limits in topology 𝒯"

Both express convergence, but in different modes.

*What it adds:* Without PA-WN_top, persistent elements in ∞_M might oscillate indefinitely without converging. With it, all persistent elements have well-defined limit points (in the topology), enabling canonical abstraction CFix(ρ_M)(x) = lim_{n→∞} ρ_M^n(x) to be defined on all ∞_M.

---

## L1.3 — Universal Axioms

### PA-Bisim — Bisimulation Congruence
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Axiom** | L1.3.Ax1 | `PA-Bisim` | | **Reframed** |
**Synopsis:** PA-Bisim requires that the projection operator respects bisimilarity: bisimilar elements project to bisimilar elements, and their projection orbits remain bisimilar throughout. This binds bisimulation theory to the canonical form computation: bisimilar elements must produce the same canonical form.

**Source:** Park [1981] LNCS 104; Milner [1989] *Communication and Concurrency* — bisimulation congruence, reframed so bisimilarity implies canonical-form equivalence.

Bisimilarity implies ρ-equivalence:
```
∀x, y ∈ 𝒰 : x ≈ y ⟹ x ≃_M y
```

where ≃_M is the abstraction equivalence relation (`NFC-NM` (L2.5.D1)).

*Standard Name:* Bisimulation congruence (Milner [1980], Park [1981]).

*Logical Status:*
- **All models:** Global scope over all 𝒰. Required universally.

*What it adds:* Connects bisimilarity to ρ-equivalence. Without it, bisimilar elements need not be orbit-equivalent.

### PA-Reach — Recursive Projection Horizon Stabilization
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Axiom** | L1.3.Ax2 | `PA-Reach` | | **Novel** |
**Synopsis:** PA-Reach (Recursive Projection Horizon Stabilization) requires that for every persistent element x, the orbit signature sig_M(ρ_M^n(x)) eventually stabilizes as n increases. This is the most structurally original CRPT axiom: it guarantees that the observer triple can extract finite, canonical observable information from infinite orbits.

**Source:** CRPT; from `sig_M-NM` (L3.1.D5) + PA-NWF (L1.2.Ax4).

For every persistent element, recursive projection reaches and stabilizes at a horizon-characterized region:
```
∀x ∈ ∞_M : ∃n ∈ ℕ : ∀j ≥ 0 : sig_M(ρ_M^(n+j)(x)) = sig_M(ρ_M^n(x))
```

**Interpretation:** Recursive projection ρ_M, when applied to any persistent (non-terminating) element, eventually enters a stratum where the orbit signature sig_M becomes constant and remains constant under further projection. On ∞_M the orbit signature is the topological form sig_M(x) = (∞, limit_id, convergence_profile) (`sig_M-NM` (L3.1.D5)); its stabilization is what enables the observer to extract a canonical representative from the infinite productive object.

### Canonical Persistent Representative

| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L1.3.D1 | `CPer` | CPer_M(x) | **Novel** |
**Synopsis:** The canonical persistent representative CPer_M(x) := ρ_M^{n(x)}(x) is the point on x's orbit where the orbit signature first stabilizes (n(x) is the reachability depth). PA-Reach guarantees n(x) exists, making CPer_M(x) the canonical finite descriptor of the infinite element x.

**Source:** CRPT; from PA-Reach (L1.3.Ax2) + `sig_M-NM` (L3.1.D5).


For x ∈ ∞_M, the **canonical persistent representative** is:
```
CPer_M(x) := ρ_M^{n(x)}(x)
```
where n(x) is the smallest natural number such that sig_M(ρ_M^(n(x)+j)(x)) = sig_M(ρ_M^{n(x)}(x)) for all j ≥ 0. PA-Reach asserts that this n(x) exists for every x ∈ ∞_M, making CPer_M(x) well-defined.

**Why PA-Reach is a Recursive Projection Axiom (not connectivity):**

PA-Reach is fundamentally about what the recursive projection operator ρ_M can extract and where it stabilizes:
- It constrains ρ_M (not →_σ or any other relation)
- It operates on the persistent regime ∞_M where ρ_M does not terminate
- It guarantees that even in non-terminating regimes, the horizon structure is recursively reachable
- This is the observer extraction principle: the object is infinite, but the observable signature is finitary and recursively determined

*Logical Status:*
- **Pure WF (∞_M = ∅):** Not assumed (vacuous: no persistent elements to constrain).
- **Native Stratified (∞_M ≠ ∅):** Substantively true. Guarantees that recursive projection can extract the horizon structure that characterizes persistent orbits.
- **Pure NWF (↓_M = ∅):** Not assumed separately but may be stated for internal consistency (*all* non-terminating elements must have reachable horizon structure).

*Standard Name:* Novel to CRPT. In ARS theory, weak normalization and productivity (PA-WN + PA-NWF + PA-Prod) constrain reduction behavior but do not guarantee horizon stabilization. PA-Reach adds this guarantee, closing the reachability gap between infinite production and finite observability.

*Rigorous Scope Note:* PA-Reach constrains sig_M — the orbit signature defined at L3.1 — which itself depends on horizons H_S, H_I, H_O defined in L3.1. Forward references are resolved by the logical ordering of the Anchor: horizon definitions (L3.1) logically precede this axiom in structure, even though L1.2–L1.5 introduces all axioms in compressed notation. The formal definitions of sig_M and H_S, H_I, H_O are at L3.1–8.2; the complete formal statement of PA-Reach in terms of these constructs is at L1.3 (present section). Both locations state the axiom consistently.

### PA-Reach — Structural Role and Impact on Theorems
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Remark** | L1.3.R1 | `PA-Reach-Role` | | **Novel** |
**Synopsis:** This analysis clarifies what PA-Reach actually does: it is not a connectivity axiom (it does not require elements to be reachable from others) but a recursive projection axiom (it constrains the long-run behavior of the projection operator on persistent orbits). This distinction matters for understanding which theorems require PA-Reach and which do not.

**Source:** CRPT; from PA-Reach (L1.3.Ax2).

**Structural consequences:**
1. **Observer Extraction Principle:** PA-Reach enables the observer triple (L4.1) to extract finite observables because recursive projection reaches and stabilizes the orbit signature—the canonical finite descriptor of infinite objects.
2. **Regime Connectivity (derived, not primitive):** The fact that convergent elements can reach persistent regimes follows as a consequence of the regime partition definition (L2.2) combined with PA-Reach: the persistent regime is defined as ∞_M = {x | ∞_M - orbit}, and PA-Reach guarantees this regime has well-characterized recursive projection structure.
3. **Gateway (*derived consequence*):** The Gateway definition (L4.2.D1) is compatible with PA-Reach: elements with →_σ-paths to ∞_M are precisely those whose fusion operator finds a persistent element (which PA-Reach ensures exists and is recursively characterized).
4. **Tower Construction:** PA-Reach enters critical proofs in L8 — the Lift/Tower construction (L8.2–L8.4) and horizon inheritance (`Hor-Lift` (L8.2.T2)). The tower's ability to collapse horizon-characterized fibers into atoms depends on PA-Reach: it guarantees that the horizons being collapsed are recursively determined, not ad-hoc equivalences.

*Theorems using PA-Reach:* `Reg-Conn` (L4.2.T1 — regime connectedness as projection property), `Hor-Lift` (L8.2.T2 — horizon inheritance under Lift, proved using PA-Reach on ρ_M), `Inf-Dual` (L2.2.T7 — infinity duality as a consequence of projection reachability).

### PA-Reach Closes the Reachability Gap: Observer Extraction Principle
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L1.3.T1 | `PA-Reach-ObsExt` | | **Novel** |
**Synopsis:** The Observer Extraction Principle: PA-Reach closes the reachability gap between finite observers and infinite orbits. Without PA-Reach, an observer examining a persistent element could never extract a canonical, finite observable summary. With PA-Reach, the observer can always wait until the signature stabilizes and read off CPer_M(x).

**Source:** CRPT; from PA-Reach (L1.3.Ax2) + `CPer` (L1.3.D1) + `Rec-Proj` (L2.1.D4).

PA-Reach guarantees that recursive projection ρ_M extracts a finite, observer-accessible slice from infinite productive objects:

**(i) Horizon Stabilization:** For x ∈ ∞_M, there exists a finite n such that sig_M(ρ_M^n(x)) is the "asymptotic orbit signature" of x's orbit — it is constant on the entire future trajectory under ρ_M (independent of orbit signature of x itself if aperiodic).

**(ii) Observer Extraction:** The observer can extract the stabilized orbit signature sig_M(CPer_M(x)) as the canonical observable from the infinite element x without measuring infinitely far. This is the canonical, recursively reachable observable that the reachability gap demanded.

**(iii) Stability Under Further Productivity:** Even as x continues to generate further infinite structure through ρ_M and →_σ transitions, the extracted observable sig_M(CPer_M(x)) does not change. The extraction is stable under continued production (by definition of CPer_M and PA-Reach).

**(iv) Accessibility Without Traversal:** The observer needs to compute n (the reachability depth) but can do so by testing sig_M-uniformity: apply ρ_M repeatedly until sig_M is constant. This is computable in principle without full knowledge of the infinite object.

*Proof.*

We verify each component:

**(i)** By PA-Reach: ∀x ∈ ∞_M : ∃n : ∀j ≥ 0 : sig_M(ρ_M^{n+j}(x)) = sig_M(ρ_M^n(x)). This defines the orbit signature as constant from step n onward. ✓

**(ii)** For x ∈ ∞_M, define CPer_M(x) := ρ_M^{n(x)}(x) where n(x) is as in (i). The stabilized orbit signature sig_M(CPer_M(x)) is well-defined: by (i) it is invariant under further ρ_M-iteration, and by `Rec-Proj` (L2.1.D4) it depends only on x, not on the chosen orbit representative. It is recursively reachable (computable by iterating ρ_M until sig_M stabilizes). This is the canonical observable. ✓

**(iii)** If x' ∈ →_σ^*(x) (x' is reachable from x via structural steps), then sig_M(x') is determined by the structural/horizon characterization of x', which may differ from sig_M(x). However, CPer_M(x) is defined *specifically* as the point where sig_M stabilizes, so sig_M(CPer_M(x)) is invariant under further ρ_M-steps by definition (item i). ✓

**(iv)** An algorithm to find n(x): initialize a witness set W ← {sig_M(x)}. For k = 1, 2, 3, ...: compute ρ_M(·) stepwise (apply ρ_M once), sample sig_M at the new iterate y_k, add sig_M(y_k) to W. If W becomes stationary (sig_M(y_k) was already seen in a prior step), then stabilization has occurred, and n(x) is the first index where stationarity is detected. This algorithm terminates by PA-Reach (guarantees n exists) but does not require knowing the full infinite structure—only the finitary orbit signature. ✓

*Consequence.* PA-Reach guarantees that every persistent orbit yields a canonical, stable, and recursively reachable orbit signature sig_M(CPer_M(x)). ∎

### PA-Reach Independence: Witness Model
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Remark** | L1.3.R2 | `PA-Reach-Indep` | | **Novel** |
**Synopsis:** PA-Reach is independent of the remaining eight PA-* axioms: there exists a model M_Reach satisfying all other axioms but not PA-Reach. This witness model has a persistent element whose orbit signature oscillates indefinitely, never stabilizing.

**Source:** CRPT; from PA-Reach (L1.3.Ax2); independence via the M_Reach countermodel.

To verify PA-Reach is independent (not derived from other axioms), a witness model M_Reach is constructed. This is a native stratified model where:
- PA-WN, PA-Conf, PA-Fix hold (core finitary axioms)
- PA-NWF, PA-Prod, PA-Bisim hold (core NWF axioms)
- PA-Reach fails: there exists x ∈ ∞_M where sig_M never stabilizes under ρ_M

**Construction:** Let 𝒰_M = {a, b, c, s₀, s₁, s₂, ...} ∪ {f_n | n ∈ ℕ} (countable set). Define →_ρ by:
```
a →_ρ c
b →_ρ c
c →_ρ c (fixpoint; represents ↓_M)
s_n →_ρ s_{n+1} for all n ≥ 0 (infinite chain; ∞_M)
f_n →_ρ f_{n+1} for all n ≥ 0 (generating infinite alternatives)
```

Define ρ_M as:
```
ρ_M(a) := c, ρ_M(b) := c, ρ_M(c) := c
ρ_M(s_n) := s_{n+1} for all n
ρ_M(f_n) := f_{n+1} for all n
```

Define horizon predicates to alternate:
```
H_S(s_n) := ⊤ if n is even, ⊥ if n is odd (violates stabilization)
H_I, H_O defined consistently on both regimes
```

**Verification:**
- PA-WN, PA-Conf, PA-Fix: satisfied on ↓_M = {a, b, c} (finitary). ✓
- PA-NWF: ∞_M = {s_n | n} ∪ {f_n | n} both have infinite ρ_M-chains. ✓
- PA-Prod, PA-Bisim: bisimulation and guardedness conditions satisfied on this structure. ✓
- PA-Reach **fails**: For x := s₀ ∈ ∞_M, sig_M(ρ_M^{2k}(x)) ≠ sig_M(ρ_M^{2k+1}(x)) for all k, so the orbit signature never stabilizes. ✗

Thus M_Reach ⊨ {PA-WN, PA-Conf, PA-Fix, PA-NWF, PA-Prod, PA-Bisim} but M_Reach ⊭ PA-Reach, confirming independence.

---

## L1.4 — Regimes and Canonicalization Modes

### Regimes and Canonicalization Modes
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L1.4.D1 | `Mode` | | **Novel** |
**Synopsis:** CRPT distinguishes two orthogonal classifications. A **regime** classifies an *element* by the fate of its ρ_M-orbit — convergent ↓_M if the orbit reaches a fixpoint, persistent ∞_M otherwise; regimes partition 𝒰_M and need no topology. A **canonicalization mode** classifies the *apparatus* by which an orbit is assigned a canonical form — finitary (termination at a fixpoint), topological (convergence to a 𝒯-limit), or asymptotic (stabilization of the orbit signature to an orbit-invariant). Modes are not a partition of 𝒰_M; they record how canonicalization is certified.

**Source:** CRPT; from `Rec-Proj` (L2.1.D4) + the regime partition (L2.2) + PA-WN (L1.2.Ax1) + PA-WN_top (L1.2.Ax7) + PA-Reach (L1.3.Ax2).

CRPT separates two distinct axes.

**Regime axis (element orbit-fate; two values).** For x ∈ 𝒰_M:
- x ∈ ↓_M (**convergent regime**) iff ∃n ∈ ℕ : ρ_M^n(x) ∈ Fix(ρ_M);
- x ∈ ∞_M (**persistent regime**) otherwise.

This is the well-founded / non-well-founded dichotomy at the level of element dynamics. It is intrinsic to (𝒰_M, ρ_M), requires no topology, and is exhaustive and exclusive (`Part` (L2.2.T3)) — there is **no third regime**.

**Mode axis (canonicalization apparatus; three values).** A *mode* is how the ρ_M-orbit of x is assigned a canonical form:
- **Finitary mode** — the orbit terminates: CFix(ρ_M)(x) = ρ_M^{d_M(x)}(x) is a reached fixpoint (an element of 𝒰_M). Available exactly on ↓_M; certified by PA-WN.
- **Topological mode** — the orbit converges in 𝒯: CFix(ρ_M)(x) = lim_{n→∞} ρ_M^n(x) is a topological limit (an element of 𝒰_M). Available on the part of ∞_M where PA-WN_top holds; certified by PA-WN_top with a Hausdorff topology (`TopSep-Uniq` (L1.2.T1)).
- **Asymptotic mode** — the orbit's observable signature stabilizes: the canonical form is an *orbit-invariant* (the asymptotic orbit invariant `AOI-Unif` (L6.3.D10)), not in general an element of 𝒰_M. Available on all of ∞_M; certified by PA-Reach + PA-Bisim.

**Relationship between the axes.**
- On ↓_M only finitary mode applies, and it is *coextensive* with the convergent regime — "finitary convergence" is by definition "reaching a fixpoint in finitely many steps." Asymptotic mode degenerates here to the reached fixpoint — which is why regime and mode coincide on the convergent regime.
- On ∞_M the coincidence fails. Finitary mode never applies. **Asymptotic mode always applies; topological mode applies only where PA-WN_top holds.** Since PA-WN_top is independent of the other axioms (`WNtop-Ind` (L1.4.T3)), the persistent regime is strictly larger than the topological mode:
```
∞_M  =  (topological-mode part: PA-WN_top holds)  ⊎  (asymptotic-only part: no 𝒯-limit)
```
The three-tier analysis of L6 (`3-Tier` (L6.2.D2)) is exactly this mode-stratification of ∞_M.

Consequently **regime ≠ mode**: there are two regimes but three modes, and "topological mode" must never be used as a synonym for the persistent regime.

### Regime Coexistence and Mode Coverage
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L1.4.T1 | `Mode-Comp` | | **Novel** |
**Synopsis:** Regime coexistence: the WF and NWF axiom profiles are jointly consistent because they govern the disjoint regimes ↓_M and ∞_M, licensing the partition 𝒰_M = ↓_M ⊔ ∞_M and the regime-stratified proof methods. Mode coverage: the convergent regime is canonicalized in finitary mode; the persistent regime is canonicalized in asymptotic mode throughout and additionally in topological mode wherever PA-WN_top holds.

**Source:** CRPT; from PA-WN (L1.2.Ax1) + PA-NWF (L1.2.Ax4) + PA-WN_top (L1.2.Ax7).


In a model M with regime partition 𝒰 = ↓_M ∐ ∞_M:

**(i) Mode Coverage:** Every element is canonicalized by an applicable mode (`Mode` (L1.4.D1)):
```
∀x ∈ 𝒰 : (x ∈ ↓_M ∧ finitary mode applies)
        ∨ (x ∈ ∞_M ∧ asymptotic mode applies, and topological mode applies iff PA-WN_top holds at x)
```

**(ii) Regime Disjointness:** No element lies in both regimes:
```
↓_M ∩ ∞_M = ∅
```

**(iii) Complementary Axiom Profiles:**
- On ↓_M: PA-WN is true (finitary convergence to a fixpoint); PA-WN_top is vacuous (the fixpoint is its own limit).
- On ∞_M: PA-WN is false (no finitary termination); the asymptotic apparatus (PA-Reach + PA-Bisim) always applies, and PA-WN_top — an *independent*, optional axiom (`WNtop-Ind` (L1.4.T3)) — certifies topological mode on exactly the sub-class of ∞_M whose orbits have a 𝒯-limit.

*Proof.*
- (i) By `Reg-Strat` (L2.2.D3), 𝒰 = ↓_M ∪ ∞_M. For x ∈ ↓_M: the ρ_M-orbit reaches Fix(ρ_M) by definition of ↓_M; PA-WN ensures the existence of at least one terminating →_ρ-path (`PA-WN-Tot` (L2.2.T4)), so finitary mode canonicalizes x. For x ∈ ∞_M: the ρ_M-orbit never reaches Fix(ρ_M) by definition of ∞_M; PA-NWF asserts such elements exist; PA-Reach + PA-Bisim make the asymptotic orbit invariant well-defined, so asymptotic mode always canonicalizes x; where PA-WN_top additionally holds, the orbit also has a 𝒯-limit and topological mode applies. ✓

- (ii) Immediate from disjointness by definition: ↓_M = {x | ∃n : ρ_M^n(x) ∈ Fix(ρ_M)}, ∞_M = {x | ∀n : ρ_M^n(x) ∉ Fix(ρ_M)}. ✓

- (iii) For x ∈ ↓_M: PA-WN_top is vacuously true (if x ∈ ↓_M and reaches a fixpoint finitely, it trivially has a limit—the fixpoint itself). For x ∈ ∞_M: PA-WN restricted to ∞_M would assert "∃n : ρ_M^n(x) ∈ Fix(ρ_M)," which is the logical negation of the defining condition of ∞_M (namely "∀n : ρ_M^n(x) ∉ Fix(ρ_M)"); thus PA-WN is false on ∞_M (mutual logical non-satisfaction, not a contradiction in the technical sense). The asymptotic apparatus (PA-Reach + PA-Bisim) governs ∞_M unconditionally; PA-WN_top, where declared, is substantively non-vacuous and certifies topological mode on the convergent sub-class of ∞_M. ✓ ∎

### Native Structure Consistency and Completeness
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L1.4.T2 | `Nat-CC` | | **Novel** |
**Synopsis:** Native Structure Consistency: the nine PA-* axioms are mutually consistent, witnessed by the model ℕ ∪ (0,1] with the decrement operator (convergent on ℕ, topologically persistent on (0,1]). Native Completeness: the axiom system is regime-stratified-complete — it proves all true first-order statements about the regime structure.

**Source:** CRPT; from the nine PA-* axioms (L1.2–L1.3); consistency witnessed by the ℕ ∪ (0,1] model.

The projection-axiom system:
```
{PA-WN, PA-NWF + PA-WN_top on ∞_M, PA-Conf, PA-CoInd, PA-Prod, PA-Bisim, PA-Reach, PA-Fix}
```

possesses the following properties:

**(i) Consistency:** The axiom system is non-contradictory. There exist models satisfying all nine PA axioms.

**(ii) Completeness (Regime-Stratified):** For every element x ∈ 𝒰, a unique canonical abstraction CFix(ρ_M)(x) exists:
```
x ∈ ↓_M ⟹ CFix(ρ_M)(x) ∈ Fix(ρ_M) ∧ x →_ρ* CFix(ρ_M)(x) (finitary case)
 x ∈ ∞_M ⟹ CFix(ρ_M)(x) = lim_{n→∞} ρ_M^n(x) (topological case; existence by PA-WN_top, uniqueness by `TopSep-Uniq` (L1.2.T1) which requires TopSep(𝒯) — the Hausdorff separation condition now formally required by PA-WN_top)
```

**(iii) WF-Specialization:** When ∞_M = ∅ (pure WF model), the native system reduces exactly to the pure-WF CRPT profile with 8 of the 9 axioms (PA-WN_top is vacuous when ∞_M = ∅). All established theorems and proofs remain unchanged.

*Proof.*
- (i) **Consistency:** We exhibit a concrete model satisfying all nine PA axioms. Let 𝒰 = ℕ ∪ (0, 1] with ↓_M = ℕ and ∞_M = (0, 1]. Define ρ_M(n) = max(n−1, 0) for n ∈ ℕ, and ρ_M(x) = x/2 for x ∈ (0, 1]. Define →_ρ = {(n, n−1) | n ≥ 1} ∪ {(x, x/2) | x ∈ (0, 1]}. Define →_σ = →_ρ ∪ {(n, x) | n ≥ 1, x ∈ (0, 1]} (gateway paths from non-fixpoint convergent elements to the persistent regime). Let 𝒯 be the topology on 𝒰 generated by: {n} is open for each n ∈ ℕ (discrete on ℕ), and the Euclidean subspace topology on [0, 1] restricted to {0} ∪ (0, 1], with 0 ∈ ℕ identified with the limit point 0 ∈ [0, 1]. In this topology, ρ_M^n(x) = x/2^n → 0 ∈ 𝒰 for all x ∈ (0, 1], and every natural number is an isolated point. Verification:
 - **PA-WN:** For each n ∈ ℕ, there exists a finite →_ρ-path n →_ρ* 0 with NF(0). ✓
 - **PA-NWF:** (0, 1] ≠ ∅ and x/2^n > 0 for all n, so no element of ∞_M reaches Fix. ✓
 - **PA-WN_top:** For x ∈ (0, 1]: lim_{n→∞} ρ_M^n(x) = lim x/2^n = 0, and 0 ∈ 𝒰 (since 0 ∈ ℕ ⊂ 𝒰) with the 𝒯-neighborhood basis of 0 given by [0, ε) ∩ 𝒰 for ε > 0. For each such neighborhood, ∃N : ∀n ≥ N, x/2^n < ε. ✓
 - **PA-Conf:** ρ_M is a function (deterministic), so →_ρ is trivially confluent. ✓
 - **PA-Prod:** For x ∉ Fix: ρ_M(x) ≠ x, so each non-fixpoint step produces new content. Define Observable(x) := (x ∉ Fix(ρ_M)). Then ∀x ∉ Fix : Observable(ρ_M(x)) holds since ρ_M(x) ∉ Fix for x ∈ (0, 1] (as x/2 > 0) and ρ_M(n) = n−1 ≠ 0 = Fix for n ≥ 2. ✓
 - **WF-Canon (theorem layer):** For x ∈ ℕ, the orbit ρ_M^k(x) = max(x−k, 0) reaches Fix(ρ_M), proving WF-Canon-1 in the exhibited model; and every fixpoint is inhabited by CFix-image, proving WF-Canon-2. ✓
 - **LA-Rich(M) (model-profile layer):** If existential richness over ≈-invariant formulas is required for this model class, it is declared in LA_M rather than PA-*. ✓
 - **PA-CoInd:** Define T^{NWF}(S) = {x ∈ 𝒰 | x ∉ Fix(ρ_M) ∧ ρ_M(x) ∈ S}. Then (0, 1] is a fixed point of T^{NWF}: for x ∈ (0, 1], x ∉ Fix(ρ_M) (since x/2^n > 0 for all n) and ρ_M(x) = x/2 ∈ (0, 1]. Moreover (0, 1] is the greatest such fixed point: if S ⊇ (0, 1] and S ⊆ T^{NWF}(S), then S ∩ ℕ = ∅ (since every n ∈ ℕ eventually reaches Fix), so S = (0, 1]. Thus ∞_M = (0, 1] = νT^{NWF}. ✓
 - **PA-Bisim:** ρ_M deterministic, so bisimilarity = orbit equivalence = ≃_M. ✓
 - **PA-Reach:** For x ∈ ∞_M = (0,1], define sig_M(x) to be constant on (0,1], e.g. sig_M(y) := (H_S = ⊤, H_I = ⊤, H_O = ⊥) for all y ∈ (0,1]. Then for any x ∈ (0,1], taking n = 0: ∀j ≥ 0, sig_M(ρ_M^j(x)) = sig_M(x/2^j) = (⊤, ⊤, ⊥) = constant. PA-Reach is satisfied. ✓

 All nine PA axioms are simultaneously satisfied in M. ✓

- (ii) **Completeness:** Define CFix(ρ_M) as follows:
 ```
 CFix(ρ_M)(x) := {
 ρ_M^{d_M(x)}(x) if x ∈ ↓_M
 lim_{n→∞} ρ_M^n(x) if x ∈ ∞_M (exists by PA-WN_top; uniqueness follows from `TopSep-Uniq` (L1.2.T1), i.e. the explicit TopSep(𝒯) condition)
 }
 ```
 This is well-defined and total on all 𝒰. For x ∈ ↓_M: d_M(x) is finite by definition, so CFix(ρ_M)(x) is a fixpoint. For x ∈ ∞_M: the limit exists by PA-WN_top and uniqueness follows by `TopSep-Uniq` (L1.2.T1), i.e. the explicit TopSep(𝒯) separation assumption. ✓

- (iii) **WF-Specialization:** If ∞_M = ∅, all elements are in ↓_M. PA-WN_top is vacuous. PA-NWF is false, which simply reflects ∞_M = ∅ (no contradiction). The PA family reduces to projection axioms on the WF substrate, and WF-Canon remains theorem-level. This preserves PA-namespace discipline while keeping the pure-WF results unchanged. ✓ ∎

### Independence of PA-WN_top
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L1.4.T3 | `WNtop-Ind` | | **Novel** |
**Synopsis:** PA-WN_top is independent of the remaining axioms, witnessed by the model M_ind = (ℤ, decrement, identity, discrete topology). In M_ind, every element is weakly normalizing (integer decrement terminates at 0 by a separate argument), but no element has a topological limit in the discrete topology.

**Source:** CRPT; from PA-WN_top (L1.2.Ax7) + PA-NWF (L1.2.Ax4); independence via the M_ind countermodel.

In the native axiom system, the following hold:

**(i) Mutual Exclusivity in Pure Models:**
- **Pure WF (∞_M = ∅):** PA-WN globally true; PA-NWF false; PA-WN_top vacuously true.
- **Pure NWF (↓_M = ∅):** PA-WN false; PA-NWF true; PA-WN_top true (non-vacuous).

**(ii) Complementary Independence in Native Stratified Models (Both regimes):** For native models with ↓_M ≠ ∅ and ∞_M ≠ ∅:
- PA-WN (on ↓_M) and PA-NWF (on ∞_M) are **conditionally independent**: both are true but govern disjoint parts of 𝒰.
- PA-NWF and PA-WN_top are **interdependent**: PA-NWF guarantees ∞_M ≠ ∅; PA-WN_top requires non-empty ∞_M.
- PA-WN (finitary mode) and PA-WN_top (topological mode) are **mode-independent**: they express convergence in different modes and are compatible.

*Proof.*

**(i)** By definitions of ↓_M and ∞_M, and by mutual exclusivity of PA-WN and PA-NWF on pure models. ✓

**(ii)** In native models:
 - PA-WN restricted to ↓_M is true by definition of ↓_M. PA-NWF on ∞_M is true by definition of ∞_M. They govern disjoint regimes, hence conditionally independent.
 - PA-NWF asserts ∞_M ≠ ∅. PA-WN_top requires ∀x ∈ ∞_M : ∃ limit. If ∞_M = ∅, PA-WN_top is vacuous and PA-NWF is false. Thus they are codependent. ✓
 - PA-WN and PA-WN_top are mode-independent: see the independence witness M_ind below. ✓

**(iii) PA-WN_top Independence Witness.** We exhibit a model satisfying the other projection axioms while failing PA-WN_top, thereby proving PA-WN_top is not entailed by the remaining PA-family.

**Model M_ind.** Let 𝒰 = ℤ with ↓_M = ℕ and ∞_M = ℤ_{<0} = {z ∈ ℤ | z < 0}. Define:
```
ρ_M(n) = max(n − 1, 0) for n ∈ ℕ
ρ_M(z) = z − 1 for z < 0
→_ρ = graph of ρ_M (deterministic)
→_σ = →_ρ ∪ {(n, z) | n ≥ 1, z < 0}
𝒯 = discrete topology on ℤ
```

**Verification:**
- **PA-WN (on ↓_M):** For n ∈ ℕ, ρ^n_M(n) = 0 ∈ Fix(ρ_M). ✓
- **PA-Conf:** ρ_M is a total function, so →_ρ is deterministic, hence trivially confluent. ✓
- **WF-Canon (theorem layer):** WF-Canon-1 holds on ↓_M since every n ∈ ℕ reaches 0 ∈ Fix(ρ_M) under finite iteration. WF-Canon-2 holds since every fixpoint f ∈ Fix(ρ_M) is inhabited by CFix-image (here Fix(ρ_M) = {0}, witnessed by x = 0). ✓
- **LA-Rich(M_ind):** not declared (LA_M = ∅) in this witness model; no PA-axiom depends on it. ✓
- **PA-NWF:** ∞_M = ℤ_{<0} ≠ ∅. For z < 0: ρ^n_M(z) = z − n < 0, hence ρ^n_M(z) ∉ Fix(ρ_M) = {0} for all n. ✓
- **PA-CoInd:** ℤ_{<0} = νT^{NWF} (greatest set S with ρ_M(S) ⊆ S and S ∩ Fix(ρ_M) = ∅). Any superset would include some n ∈ ℕ with ρ^n_M(n) = 0 ∈ Fix(ρ_M). ✓
- **PA-Prod:** For x ≠ 0: ρ_M(x) ≠ x (predecessor on ℕ≥1 and subtraction on ℤ_{<0}). ✓
- **PA-Bisim:** ρ_M deterministic → bisimilarity reduces to orbit equivalence ≃_M. ✓
- **PA-Reach:** For z ∈ ∞_M = ℤ_{<0}, define sig_M(z) to be constant on ℤ_{<0}, e.g. sig_M(w) := (⊥, ⊤, ⊥) for all w ∈ ℤ_{<0}. Then for any z < 0, taking n = 0: ∀j ≥ 0, sig_M(ρ_M^j(z)) = sig_M(z − j) = (⊥, ⊤, ⊥) = constant. PA-Reach is satisfied. ✓
- **PA-WN_top:** **FAILS.** For z ∈ ∞_M: ρ^n_M(z) = z − n. In the discrete topology, convergence requires eventual constancy; but z − n is strictly decreasing, hence not eventually constant. No L ∈ 𝒰 has ρ^n_M(z) ∈ U for eventually all n and any singleton neighborhood {L}. ✗

Thus M_ind satisfies the remaining PA-family while failing PA-WN_top, establishing PA-WN_top independence relative to that family. ∎

---

### Native Duality Remarks

### Regime / Mode Terminology Discipline
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Remark** | L1.4.R1 | `Nat-Reg` | | **Novel** |
**Synopsis:** Terminology discipline for the two axes: "regime" and "WF/NWF" name the element orbit-fate dichotomy (↓_M / ∞_M); "finitary / topological / asymptotic mode" name the canonicalization apparatus. The axes coincide on ↓_M but diverge on ∞_M, so the vocabularies must not be used interchangeably.

**Source:** CRPT; from `Mode` (L1.4.D1) + `Mode-Comp` (L1.4.T1).


The regime axis and the mode axis (`Mode` (L1.4.D1)) are distinct and are kept terminologically separate throughout the tower.
1. **Regime / WF / NWF** name one dichotomy at the level of element dynamics: a well-founded (WF) orbit reaches a fixpoint and lies in the convergent regime ↓_M; a non-well-founded (NWF) orbit never does and lies in the persistent regime ∞_M. "Regime", "↓_M / ∞_M", and "WF / NWF" are synonyms for this axis.
2. **Finitary / topological / asymptotic** name canonicalization modes, never regimes. They classify how a canonical form is certified, not which elements exist.
3. The convergent regime is canonicalized entirely in finitary mode (coextensively). The persistent regime is canonicalized in asymptotic mode throughout, and additionally in topological mode where PA-WN_top holds.
4. Proof method follows the regime: induction on derivation height for ↓_M, coinduction (PA-CoInd; `AOI-BisInv` (L6.3.T3)) for ∞_M — the regime-stratified strategy `Reg-Strat` (L2.2.D3).

### The Infinity Duality Explained
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Remark** | L1.4.R2 | `Inf-Dual-Expl` | | **Novel** |
**Synopsis:** The Infinity Duality is a third, distinct duality — horizontal infinity (σ-branching within a fiber) versus vertical infinity (ρ-orbit non-termination). It is orthogonal to both the regime axis and the mode axis: it concerns directions of infinite structure that exchange roles across tower levels, not element orbit-fate and not canonicalization apparatus.

**Source:** CRPT; from `Inf-Dual` (L2.2.T7).


`Inf-Dual` (L2.2.T7) concerns a duality of *directions* of infinite structure, independent of the regime and mode axes:

```
Horizontal infinity:  σ-branching within a normal-form fiber (H_S / H_I structure)
Vertical infinity:    ρ-orbit non-termination (persistent dynamics)
```

The two exchange roles across tower levels (`Inf-Dual` (L2.2.T7), `σ-Not3rd` (L8.6.T4)): horizontal within-fiber structure at level Mₙ becomes vertical composition depth at Mₙ₊₁, and conversely. This *directional* duality is neither the regime dichotomy (↓_M / ∞_M) nor the finitary/topological/asymptotic mode distinction (`Mode` (L1.4.D1)); identifying it with either is a category error.

### Topological Structure as Substrate Data
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Remark** | L1.4.R3 | `Top-Inst` | | **Novel** |
**Synopsis:** The topology 𝒯 is a free parameter of the CRPT substrate. This remark gives three canonical instantiations: the discrete topology (PA-WN_top vacuous), the metric topology on a complete metric space (PA-WN_top = completeness condition), and the order topology on a complete lattice (PA-WN_top = directed-completeness). All three are valid CRPT substrates.

**Source:** CRPT; from `Sub` (L1.1.D1) + PA-WN_top (L1.2.Ax7).


Topology is a structural component of the substrate Sub = (𝒰, →_ρ, →_σ, 𝒯).
Concrete instantiations supply the specific 𝒯. Examples:
- **REAL_ANALYSIS:** 𝒯 = standard topology on ℝ
- **METRIC_SPACES:** 𝒯 = metric topology d(x, y)
- **FUNCTIONAL_ANALYSIS:** 𝒯 = norm or weak topology on Banach spaces
- **STREAMS:** 𝒯 = pointwise or uniform convergence

The abstract anchor remains topology-polymorphic over concrete choices of 𝒯,
subject to the global conditions TopSep(𝒯) and continuity of ρ required by
the topological branch of CFix.

---

## L1.5 — Model Axiom Profiles

**Motivation.** The nine PA-* axioms of L1.2–L1.5 define what it means to *engage* with a CRPT
substrate. But not every model satisfies every axiom globally, and some models require
axioms beyond the PA-* family to characterise their internal structure fully. This section
formalises both: the *scope* with which each PA-* axiom applies to a model, and the
mechanism by which models may introduce *local axioms* not derivable from the PA-* system.

This section formalizes regime-scoping conventions (e.g. "PA-WN restricted to ↓_M") with
a first-class formal object — the **model axiom profile** — that is part of the
definition of a CRPT model. It also resolves, cleanly and without stochastic
reinterpretation, the compliance status of models (such as CCS and π-calculus) where PA-Conf
fails globally but holds on ρ_M-orbits.

---

### PA-* Scope Declarations

### PA-* Scope Declaration
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L1.5.D1 | `PA-Scope` | | **Novel** |
**Synopsis:** The four-valued scope system classifies each PA-* axiom's applicability to a given model: Global (applies to all elements), Scoped(S) (applies precisely to the subset S), Vacuous (hypothesis is never satisfied, so the axiom holds trivially), and Fails (the conclusion fails for some element). This makes the axiom profiles precise rather than binary.

**Source:** CRPT; from the PA-* axiom system (L1.2–L1.3).

For each PA-* axiom PA-X, a
model M declares a *scope* — a definable subset S ⊆ 𝒰_M — over which PA-X holds.
The four canonical scope values are:

| Scope | Meaning |
|-------|---------|
| `Global` | PA-X holds for all x ∈ 𝒰_M |
| `Scoped(S)` | PA-X holds for all x ∈ S, for some explicitly defined S ⊆ 𝒰_M |
| `Vacuous` | PA-X holds because its antecedent condition is never triggered in M |
| `Fails` | PA-X is false in M — explicitly declared inapplicable |

### Scope is not status
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Remark** | L1.5.R1 | `Scope-Status` | | **Novel** |
**Synopsis:** The crucial distinction: Scoped(S) is not a weakening of Global — it is a precise, falsifiable statement about which elements satisfy the axiom's conclusion. An axiom is Scoped(S) only when S ≠ 𝒰_M and the axiom holds for all elements of S. This prevents scope from being used as an escape from falsification.

**Source:** CRPT; from `PA-Scope` (L1.5.D1).

A `Scoped(S)` declaration is not a failure.
It is a precise mathematical statement: PA-X is a theorem on S and is not claimed
elsewhere. In particular, `Scoped(ρ_M-orbits)` for PA-Conf means that the deterministic
strategy ρ_M produces a unique canonical form — which is exactly the content required
for CFix(ρ_M) to be well-defined — even when →_ρ overall is non-confluent. All downstream
theorems in §L2.1–24 that depend on PA-Conf depend only on its orbit-level content;
`Scoped(ρ_M-orbits)` is sufficient for every such theorem.

### Scope Convention Formalised
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Remark** | L1.5.R2 | `Conv-Form` | | **Novel** |
**Synopsis:** The scope convention notation (G), (S), (V), (F) annotates each axiom's scope declaration inline with the formal statement, making scope explicit at the point of use rather than in a separate table.

**Source:** CRPT; from `PA-Scope` (L1.5.D1).

The convention
"PA-WN restricted to ↓_M" is expressed as PA-WN declared `Scoped(↓_M)`.
PA-NWF declared `Vacuous` expresses the pure-WF case. `Fails` is an explicit
inapplicability declaration — the distinction between `Vacuous` and `Fails` is mathematically
significant: a `Vacuous` axiom contributes no constraint and introduces no tension;
a `Fails` axiom is actively false.

---

### Model-Local Axioms

### Model-Local Axiom Schema LA_M
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L1.5.D2 | `LA_M` | LA_M | **Novel** |
**Synopsis:** The model-local axiom schema LA_M collects all axioms specific to a particular CRPT model M — facts that hold in M but are not consequences of the nine PA-* axioms alone. LA_M is the extension point for domain-specific axiomatizations built on the CRPT foundation.

**Source:** CRPT; from `Sub` (L1.1.D1) + the PA-* axiom system (L1.2–L1.3).

A model M may declare a
finite set LA_M of sentences over the extended signature

```
Σ_M := (𝒰_M, →_ρ, →_σ, ρ_M, [model-specific primitives])
```

that are not derivable from the PA-* system alone. These are *model-local axioms*.
They capture genuinely model-specific structure: non-deterministic choice operators,
context-dependence, observable-specific predicates, or any other structural commitments
that have no abstract anchor counterpart.

*Notation.* LA_M = {LA_M^1, LA_M^2, ...} where each LA_M^i is a sentence of L(Σ_M).
When LA_M = ∅, the model introduces no local axioms (the standard case for pure WF
and pure NWF foundational models).

### Observable Contract as proto-LA_M
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Remark** | L1.5.R3 | `OC-LA_M` | | **Novel** |
**Synopsis:** The Observable Contract (OC-1, OC-2) from PA-Prod is the prototype for model-local axioms: it is a condition specific to a model's orbit structure that the nine PA-* axioms do not determine. This remark formally recognises it as an instance of the LA_M schema.

**Source:** CRPT; from `LA_M` (L1.5.D2) + PA-Prod (L1.2.Ax6).

The Observable Contract (OC-1,
OC-2) of `PA-Prod` (L1.2.Ax6) is the existing instance of this pattern: a model-specific
predicate Observable : 𝒰_M → {⊤, ⊥} subject to two local conditions. `LA_M` (L1.5.D2) generalises this to an arbitrary finite set of such commitments.

### IC_M as proto-LA_M
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Remark** | L1.5.R4 | `IC_M-LA_M` | | **Novel** |
**Synopsis:** Model-specific identity conditions IC_M — axioms about which elements are equal — are another instance of LA_M. Different domain models (set theory, type theory, process algebra) have different identity axioms; IC_M collects them as model-local extensions.

**Source:** CRPT; from `LA_M` (L1.5.D2).

The model-specific identity condition IC_M
(e.g., IC_ZFC = set extensionality, IC_HoTT = univalence) is likewise a local axiom
in the sense of `LA_M` (L1.5.D2). Models that already document IC_M have implicitly
provided their LA_M ⊇ {IC_M}.

---

### Model Axiom Profiles

### Model Axiom Profile
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L1.5.D3 | `PA-Profile` | PA-Profile_M | **Novel** |
**Synopsis:** The axiom profile Profile(M) = (PA-Profile_M, LA_M) is the complete specification of the axioms that model M satisfies. Treating profiles as mathematical objects (not just as informal descriptions) enables the formal study of profile-preserving maps (homomorphisms) and profile-indexed model classes.

**Source:** CRPT; from `PA-Scope` (L1.5.D1) + `LA_M` (L1.5.D2).

The *axiom profile* of model M is
the pair

```
Profile(M) := (PA-Profile_M, LA_M)
```

where:
- **PA-Profile_M** is a function assigning each of the nine PA-* axioms a scope
 declaration from {Global, Scoped(S), Vacuous, Fails}.
- **LA_M** is the (possibly empty) set of model-local axioms over Σ_M.

### CRPT Model
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L1.5.D4 | `CRPT-Mod` | | **Novel** |
**Synopsis:** A CRPT model is a substrate together with an axiom profile satisfying: (1) non-triviality (𝒰_M is non-empty), (2) profile consistency (the profile is satisfiable), and (3) the witness condition (a specific element witnessing the profile exists). This is the official definition of 'model' that the category Mod_CRPT is built from.

**Source:** CRPT; from `Sub` (L1.1.D1) + `PA-Profile` (L1.5.D3).

A *CRPT model* M is
a substrate (𝒰_M, →_ρ, →_σ, ρ_M) satisfying L1.1 conditions,
equipped with an axiom profile Profile(M) = (PA-Profile_M, LA_M) such that:

1. **Non-triviality:** At least one PA-* axiom is declared `Global` or `Scoped(S)` for
 non-empty S.
2. **Consistency:** LA_M ∪ {PA-X restricted to its declared scope | PA-X not Fails} is
 jointly satisfiable — i.e., there exists a model of the substrate satisfying all
 non-failed PA-* scoped commitments and all model-local axioms simultaneously.
3. **Witness:** The consistency is witnessed by an explicit model (the model itself,
 or a sub-model satisfying the declared scope).

*Remark.* Condition 2 is strictly stronger than requiring only that some axiom holds: it requires the full declared profile to be jointly satisfiable. Condition 3 makes the consistency check constructive.

---

### Consistency of Profiles

### Profile Consistency is Constructively Checkable
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L1.5.T1 | `Prof-CC` | decide(PA-Profile_M) | **Novel** |
**Synopsis:** Profile consistency is constructively checkable: given a candidate model, one can verify each PA-* axiom against the model's structure in a finite computation (for finite models) or by providing an explicit witness (for infinite models). This makes CRPT model verification a concrete activity.

**Source:** CRPT; from `PA-Profile` (L1.5.D3) + `CRPT-Mod` (L1.5.D4).

For any model M with finite LA_M and a decidable PA-* profile, consistency of
Profile(M) is verifiable by exhibiting the model itself (or an appropriate
sub-structure) as the required model.

*Proof.* Take M itself (or the sub-structure witnessing the declared scopes) as the required witness. Each
PA-X declared `Global` or `Scoped(S)` is verified in M by the model's existing
theorems. Each LA_M^i is verified in M by the model-specific proof provided at
instantiation. Since M satisfies all non-failed conditions, Profile(M) is consistent.
Decidability follows from the finite size of both PA-Profile_M (nine entries) and
LA_M (finite by assumption). ∎

### Scoped Confluence along ρ_M-orbits
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L1.5.D5 | `SC-Orb` | SC-Orb(M) | **Novel** |
**Synopsis:** Scoped confluence along projection orbits is the first-order axiom schema that replaces the full PA-Conf axiom when only orbit-level confluence is needed. Many theorems that appear to require global confluence actually only need confluence along the specific orbits involved, which this scoped version provides.

**Source:** CRPT; from PA-Conf (L1.2.Ax2) + `ρ_M` (L2.1.D1).

We write `Scoped(ρ_M-orbits)` for the following first-order schema:

```
Scoped(ρ_M-orbits) : ⇔ ∀x ∈ 𝒰_M. ∀n,m ∈ ℕ, (ρ_M^n(x) ∈ NF(→_ρ) ∧ ρ_M^m(x) ∈ NF(→_ρ)) ⇒ ρ_M^n(x) = ρ_M^m(x).
```

In words: for every element x, the ρ_M-orbit meets the set of normal forms in
at most one element. Equivalently, the ρ_M-orbit cannot reach two distinct normal
forms. This is a strictly weaker statement than global confluence of →_ρ.

### Scope Sufficiency for CFix(ρ_M)
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L1.5.T2 | `Scope-Suf` | | **Novel** |
**Synopsis:** Scoped projection-orbit confluence is provably sufficient for all theorems in L2–L8 that cite PA-Conf: the canonical form uniqueness, regime partition, and tower construction all hold under this weaker condition. This means CRPT's results are available even in models where global confluence fails.

**Source:** CRPT; from `SC-Orb` (L1.5.D5) + PA-Conf (L1.2.Ax2).

Suppose the following hold for a model M:

- `PA-WN` holds on ↓_M (every x ∈ ↓_M reaches some normal form along a ρ_M-iteration), and
- `Scoped(ρ_M-orbits)` holds as defined above.

Then for every x ∈ ↓_M the element CFix(ρ_M)(x) defined by iterating ρ_M to depth d_M(x)
is well-defined and unique. Moreover, any theorem in §L2.2–10 whose only use of
PA-Conf is to deduce uniqueness of the normal form along a ρ_M-orbit remains
valid under the `Scoped(ρ_M-orbits)` declaration.

*Proof.* Let x ∈ ↓_M. By `PA-WN` (restricted to ↓_M) there exists n ∈ ℕ such that
ρ_M^n(x) ∈ NF(→_ρ); let n₀ := d_M(x) be the minimal such n. By the definition of
CFix(ρ_M) we take CFix(ρ_M)(x) := ρ_M^{n₀}(x). To prove well-definedness, suppose there is
another m ∈ ℕ with ρ_M^m(x) ∈ NF(→_ρ). Then `Scoped(ρ_M-orbits)` implies
ρ_M^{n₀}(x) = ρ_M^m(x); hence the normal form reached along the ρ_M-orbit is unique.

For any proof in §L2.2–10 that appeals to PA-Conf solely to obtain this orbit-level
uniqueness, the same argument carries through directly under the `Scoped(ρ_M-orbits)`
assumption. If a particular result in those sections uses global confluence beyond
orbit-uniqueness, that additional global-confluence hypothesis is required for that
result. ∎

### CCS, Ï-Calculus, Petri Nets Are Compliant

| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Corollary** | L1.5.C1 | `Proc-Compliant` | | **Novel** |
**Synopsis:** See the remark.

**Source:** CRPT; from `LA_M` (L1.5.D2).

Any model
where →_ρ is non-confluent but ρ_M is a total deterministic function satisfying C1–C3
(L2.1) is CRPT-compatible with PA-Conf declared `Scoped(ρ_M-orbits)`. No stochastic
reinterpretation is required.

### LA_M Independence
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L1.5.T3 | `LA-Ind` | | **Novel** |
**Synopsis:** Model-local axioms are independent of the nine PA-* axioms: there exist models where every PA-* axiom holds but the model-local axiom fails, and vice versa. This independence means that LA_M genuinely extends the CRPT foundation rather than being redundant with it.

**Source:** CRPT; from `LA_M` (L1.5.D2) + the PA-* axiom system (L1.2–L1.3).

Model-local axioms in LA_M neither
strengthen nor weaken any PA-* axiom unless they explicitly reference PA-* constructs
(ρ_M, CFix(ρ_M), d_M, etc.). An LA_M containing only model-primitive sentences is
independent of the PA-* system.

*Proof.* By `LA_M` (L1.5.D2), LA_M^i ∈ L(Σ_M). If LA_M^i does not reference any
PA-* construct symbol, it is a sentence purely about model primitives. Since the
PA-* axioms are axioms of the abstract signature (𝒰, →_ρ, →_σ, ρ_M) with no
model-primitive symbols, no PA-* axiom is derivable from or refutable by LA_M^i.
Independence follows. ∎

---

### Profile Notation

Throughout §L2.1–32, instantiation documents, and the meta documents, the following
compact notation is used for axiom profiles:

```
Profile(M) = {
 PA-WN: <scope>,
 PA-Conf: <scope>,
 PA-Fix: <scope>,
 PA-WN_top: <scope>,
 PA-NWF: <scope>,
 PA-CoInd: <scope>,
 PA-Prod: <scope>,
 PA-Bisim: <scope>,
 PA-Reach: <scope>,
 WF-Canon: <theorem-status>,
 LA-Rich: <declared|not-declared>,
 LA_M: { <axiom-name>: <sentence>, ... } -- or ∅
}
```

The `LA_M` entry uses human-readable axiom names followed by their formal statements.
Models with LA_M = ∅ may omit the LA_M line.

---


---

## L1.6 — Axiom Minimality and Independence

**Status of each axiom:**

| Axiom | Status | Independence |
|-------|--------|-------------|
| PA-WN | Axiom | Independent by duality with PA-NWF |
| PA-NWF | Axiom | Independent by duality with PA-WN |
| PA-Conf | Axiom | Independent — Countermodel M_Conf (new) |
| PA-Fix | Axiom | Independent — Countermodel M_Fix (new) |
| PA-CoInd | Axiom (portable); theorem in full SOL | Derived from PA-NWF under full SOL (proved in `Ax-Ind` (L1.6.T1)) |
| PA-Prod | Axiom | Independent — Countermodel M_Prod (new) |
| PA-WN_top | Axiom (conditional scope) | Independent — Countermodel M_ind (`WNtop-Ind` (L1.4.T3)) |
| PA-Bisim | Axiom | Independent — Countermodel M_Bisim (new) |
| PA-Reach | Axiom | Independent — Countermodel M_Reach (new) |
| WF-Canon | THEOREM (not an axiom) | N/A — derived from PA-WN + PA-Conf + definitions |

**Note on axiom count:** The strict independence basis here has 8 PA axioms
{PA-WN, PA-NWF, PA-Conf, PA-Fix, PA-Prod, PA-WN_top, PA-Bisim, PA-Reach} — each is
independent of the conjunction of the other seven (countermodels below, plus
M_ind for PA-WN_top at `WNtop-Ind` (L1.4.T3)). PA-WN_top **is** part of the minimal
basis: its vacuity on pure-WF models (∞_M = ∅) is a *scope* property, not
redundancy — it is not derivable from the other axioms (witness M_ind), so any
minimal basis must contain it. This is the same conditional-scope situation as
PA-NWF, PA-Prod, and PA-Reach (all vacuous when ∞_M = ∅), which are likewise
counted. PA-CoInd is the **only** PA axiom outside the strict basis: in full
second-order semantics it is derivable from PA-NWF (proved in `Ax-Ind` (L1.6.T1)),
and is retained as an explicit axiom solely for schema/Henkin portability.
Hence the nine PA-* axioms decompose as **eight independent basis axioms + PA-CoInd
(portability/derivable)**. WF-Canon and WF-Ext are theorem-level and are not counted
as PA axioms.

**Naming note (PA namespace discipline):** The theorem label is **WF-Ext**
(WF extensionality / indiscernibility),
with proof content represented by `CNF=CR` (L2.5.T2) and `GC3` (L7.1.C3).

### New Countermodels

Each countermodel satisfies all PA-* axioms except the targeted one, proving that
the targeted axiom is not derivable from the others.

---

**Countermodel M_Conf (PA-Conf independence)**

*Target:* Show PA-Conf is not derivable from {PA-WN, PA-Fix, PA-NWF, PA-CoInd,
PA-Prod, PA-Bisim, PA-Reach}.

*Construction:* Let 𝒰 = {a, b, c, d} with:
- →_ρ: a →_ρ b, a →_ρ c, b →_ρ d, c →_ρ d
- →_σ = →_ρ
- ρ_M: ρ_M(a) = b (choosing left branch), ρ_M(b) = d, ρ_M(c) = d, ρ_M(d) = d

*Verification:*
- **PA-WN:** Every element reaches d (a normal form) in ≤ 2 steps. ✓
- **PA-Conf fails:** a →_ρ* b →_ρ* d and a →_ρ* c →_ρ* d — this is actually
  confluent (both paths reach d). We need non-confluence.

*Construction:* Let 𝒰 = {a, b₁, b₂} with:
- →_ρ: a →_ρ b₁, a →_ρ b₂
- b₁, b₂ are distinct normal forms (NF(b₁), NF(b₂))
- →_σ = →_ρ
- ρ_M: ρ_M(a) = b₁ (arbitrary deterministic choice), ρ_M(b₁) = b₁, ρ_M(b₂) = b₂

*Verification:*
- **PA-WN:** a reaches b₁ in 1 step; b₁, b₂ are fixpoints. ✓
- **PA-Conf fails:** a →_ρ* b₁ and a →_ρ* b₂, but b₁ and b₂ are distinct normal
  forms with no common reduct. ✗ (PA-Conf violated)
- **LA-Rich(M_Conf):** not declared (LA_M = ∅); this model is used only for PA-axiom
  independence and does not require model-local richness assumptions.
- **PA-Fix:** Fixpoint structure is explicit (b₁, b₂ are fixpoints). ✓
- **WF-Ext:** Theorem — automatically satisfied. ✓
- **PA-NWF:** Does not apply (no infinite paths; ∞_M = ∅). Vacuously consistent. ✓
- **PA-CoInd, PA-Prod, PA-Bisim:** Vacuous (∞_M = ∅; no persistent elements). ✓
- **PA-Reach:** Vacuous (∞_M = ∅). ✓

*Conclusion:* M_Conf ⊨ {PA-WN, PA-Fix, PA-NWF(vac), PA-CoInd(vac), PA-Prod(vac),
PA-Bisim(vac), PA-Reach(vac)} but M_Conf ⊭ PA-Conf. Therefore PA-Conf is not
derivable from the remaining axioms. ∎

---

**Countermodel M_Fix (PA-Fix independence)**

*Target:* Show PA-Fix is not derivable from {PA-WN, PA-Conf, PA-NWF,
PA-CoInd, PA-Prod, PA-Bisim, PA-Reach}.

*Construction:* Let 𝒰 = {a, b} with:
- →_ρ: a →_ρ b (and no outgoing edge from b)
- →_σ = →_ρ
- ρ_M: ρ_M(a) = a, ρ_M(b) = b

*Verification:*
- **PA-Fix fails:** ρ_M(a) = a, but a is not a normal form because a →_ρ b. So
  (ρ_M(a)=a) ↔ NF(a) is false. ✗
- **PA-WN:** a reaches the normal form b in one →_ρ-step; b is already normal. ✓
- **PA-Conf:** →_ρ is deterministic (at most one successor at each element), hence confluent. ✓
- **PA-CoInd, PA-NWF:** No persistent chain is required in this WF witness; these clauses are vacuously consistent in the witness profile. ✓
- **PA-Prod:** Non-fixpoint antecedent is false everywhere (Fix(ρ_M) = {a, b}), so implication is vacuous. ✓
- **PA-Bisim:** No bisimilar-distinct pair violates ρ-equivalence in this two-state deterministic witness. ✓
- **PA-Reach:** Vacuous (∞_M = ∅, so the universal quantification over ∞_M is empty). ✓

*Conclusion:* M_Fix satisfies all remaining PA axioms but violates PA-Fix, so
PA-Fix is independent. ∎

---

**Namespace placement note.**

Witness-richness requirements are represented by LA-Rich(M) in model profiles,
not in PA-*.

---

**PA-CoInd status (full SOL vs schema/Henkin modes)**

In full (standard) second-order semantics, PA-CoInd is derivable from PA-NWF.
Write the PA-CoInd antecedent for a predicate P ⊆ 𝒰 as:

```
Ante(P):= ∀x (P(x) ⟹ x ∉ Fix(ρ_M) ∧ ∀y (x →_ρ y ⟹ P(y))).
```

Assume Ante(P) and x₀ with P(x₀). We show x₀ ∈ ∞_M.

By Ante(P), x₀ ∉ Fix(ρ_M). Also, since x₀ →_ρ ρ_M(x₀), we get P(ρ_M(x₀)).
Applying Ante(P) again gives ρ_M(x₀) ∉ Fix(ρ_M). Iterating yields:

```
∀n ∈ ℕ : P(ρ_M^n(x₀)) ∧ ρ_M^n(x₀) ∉ Fix(ρ_M).
```

Therefore no iterate of x₀ reaches Fix(ρ_M), i.e. x₀ ∈ ∞_M by definition of
the persistent regime. Since x₀ was arbitrary in P, we have P ⊆ ∞_M, which is
exactly PA-CoInd. Thus:

```
PA-NWF ⟹ PA-CoInd   (full SOL, standard metatheory).
```

Hence PA-CoInd is not part of the strict independence basis in full SOL.

In schema/Henkin modes, PA-CoInd may be retained as an explicit axiom schema for
portability across proof frameworks. This document's strict independence theorem
below is stated only for the full-SOL basis.

---

**Countermodel M_Prod (PA-Prod independence)**

*Target:* Show PA-Prod is not derivable from {PA-WN, PA-Conf, PA-Fix, PA-NWF,
PA-CoInd, PA-Bisim, PA-Reach}.

*Construction:* Under the single-step formulation (L1.2),
PA-Prod states: ∀x ∈ 𝒰 : (x ∉ Fix(ρ_M)) ⟹ Observable(ρ_M(x)).
The Observable Contract (OC-1) forces Observable(y) = ⊤ for all y ∉ Fix(ρ_M).
Therefore PA-Prod can only fail when ρ_M(x) ∈ Fix(ρ_M) and Observable(ρ_M(x)) = ⊥ —
i.e., at a convergent element one step from an unobservable fixpoint.

We need a model where PA-NWF holds (infinite paths exist), PA-CoInd holds, PA-Bisim
holds, PA-Reach holds, but PA-Prod fails at some convergent-to-fixpoint boundary.

Let 𝒰 = {a, b, c, d} with:
- →_ρ: a →_ρ b, b →_ρ a (alternating cycle), c →_ρ d, d →_ρ d (fixpoint)
- →_σ = →_ρ ∪ {(c, a)}  (structural gateway from c to persistent regime)
- ρ_M: ρ_M(a) = b, ρ_M(b) = a, ρ_M(c) = d, ρ_M(d) = d
- Fix(ρ_M) = {d}
- Observable: Observable(a) = Observable(b) = Observable(c) = ⊤, Observable(d) = ⊥
- OC-1 check: a,b,c ∉ Fix ⟹ Observable = ⊤. ✓  d ∈ Fix ⟹ no constraint. ✓

*Verification:*
- **PA-NWF:** Both a and b have infinite paths (a → b → a → b → …). ✓
- **PA-CoInd:** Let P ⊆ Φ(P). If P(a), then a ∉ Fix ✓ and b ∈ P. Similarly P(b) ⟹ P(a).
  If P(c), then c ∉ Fix ✓ and d ∈ P. If P(d), then d ∈ Fix, so the coinduction
  condition ρ_M(d) ≠ d fails. So P cannot contain d. Therefore P ⊆ {a, b}, and both
  are on infinite paths. P ⊆ InfinitePaths. ✓
- **PA-Bisim:** The maximal bisimulation on {a,b}: R = {(a,a), (b,b), (a,b), (b,a)} gives
  a ≈ b. Under PA-Bisim, a ≃_M b. This holds: ρ_M(a) = b ≃_M a = ρ_M(b). ✓
  On {c,d}: no non-trivial bisimulation (c → d → d loops, unique behavior). ✓
- **PA-WN:** c ∈ ↓_M: ρ_M(c) = d ∈ Fix, so d_M(c) = 1. ✓
- **PA-Conf:** ρ_M is deterministic (total function). ✓
- **PA-Fix:** Fixpoint stratum is explicit and stable under ρ_M in this finite model. ✓
- **PA-Reach:** For ∞_M = {a, b}, the orbit of a cycles a → b → a → ..., and orbit of b cycles b → a → b → .... Horizon stabilization requires: define sig_M(a) := sig_M(b) (equal orbit signature). Then for both a and b, the orbit signature is constant from n=0: sig_M(a) = sig_M(b) for all iterates. PA-Reach is satisfied with this choice. ✓
- **PA-Prod FAILS:** c ∉ Fix(ρ_M), but Observable(ρ_M(c)) = Observable(d) = ⊥. ✗

*Conclusion:* M_Prod ⊨ {PA-NWF, PA-CoInd, PA-Bisim, PA-Reach, PA-WN,
PA-Conf, PA-Fix} but M_Prod ⊭ PA-Prod. Therefore PA-Prod is not
derivable from the remaining axioms. ∎

---

**Countermodel M_Bisim (PA-Bisim independence)**

*Target:* Show PA-Bisim is not derivable from {PA-WN, PA-Conf, PA-Fix,
PA-NWF, PA-CoInd, PA-Prod, PA-Reach}.

*Construction:* Let 𝒰 = {a, b, f, g} with:
- →_ρ: a →_ρ f, b →_ρ g; f and g are normal forms
- →_σ = →_ρ
- ρ_M: ρ_M(a)=f, ρ_M(b)=g, ρ_M(f)=f, ρ_M(g)=g

Define abstraction-equivalence by canonical projection target:
```
x ≃_M y  :⇔  CFix(ρ_M)(x) = CFix(ρ_M)(y)
```
Hence a ≄_M b because CFix(ρ_M)(a)=f and CFix(ρ_M)(b)=g with f ≠ g.

Now define relation
```
R = {(a,b), (f,g), (a,a), (b,b), (f,f), (g,g)}.
```
R is a bisimulation: (a,b) is matched through successors (f,g); (f,g) are both
terminal and match vacuously. Therefore a ≈ b but a ≄_M b.

*Verification:*
- **PA-Bisim fails:** a ≈ b but not a ≃_M b. ✗
- **PA-WN, PA-Conf:** immediate from finite deterministic reduction to normal forms. ✓
- **PA-Fix:** f,g are exactly the normal forms and exactly the ρ_M-fixpoints. ✓
- **PA-Prod:** choose Observable(x)=⊤ for all x; PA-Prod holds trivially. ✓
- **PA-NWF, PA-CoInd:** vacuously consistent in this WF witness profile. ✓
- **PA-Reach:** vacuous here (no persistent/diverging regime in the witness profile). ✓

*Conclusion:* M_Bisim satisfies all remaining PA axioms but violates PA-Bisim,
so PA-Bisim is independent. ∎

---

**Countermodel M_Reach (PA-Reach independence)**

*Target:* Show PA-Reach is not derivable from {PA-WN, PA-Conf, PA-Fix,
PA-NWF, PA-CoInd, PA-Prod, PA-Bisim}.

*Construction:* Let 𝒰 = {f} ∪ {s_n | n ∈ ℕ} with:
- →_ρ: no successor for f (f is a normal form); s_n →_ρ s_{n+1} for all n ∈ ℕ
- →_σ = →_ρ ∪ {(f, s_0)} (structural gateway from fixpoint to persistent regime)
- ρ_M: ρ_M(f) = f; ρ_M(s_n) = s_{n+1} for all n ∈ ℕ
- Fix(ρ_M) = {f}; ↓_M = {f}; ∞_M = {s_n | n ∈ ℕ}
- 𝒯: discrete topology on {f}; cofinite topology on ∞_M with shared limit point s_∞
  (all s_n-orbits converge to the same limit, so CFix(ρ_M)(s_n) = s_∞ for all n)
- Observable: ⊤ for all elements
- Horizon signature: for s_n ∈ ∞_M, define
  sig_M(s_n) := (H_S(s_n), ⊤, ⊥) where H_S(s_n) := ⊤ if n even, ⊥ if n odd

*Verification:*
- **PA-Reach FAILS:** For x := s_0 ∈ ∞_M, the iterate ρ_M^n(s_0) = s_n. For any
  n ∈ ℕ, sig_M(s_n) alternates: (⊤, ⊤, ⊥) when n is even, (⊥, ⊤, ⊥) when n is odd.
  Thus ∀n : ∃j = 1 : sig_M(s_{n+1}) ≠ sig_M(s_n) — orbit signature never stabilizes. ✗
- **PA-WN (Scoped(↓_M)):** f ∈ ↓_M with d_M(f) = 0; ρ_M^0(f) = f ∈ Fix(ρ_M). ✓
- **PA-NWF:** s_0 ∈ ∞_M: ρ_M^n(s_0) = s_n ∉ Fix(ρ_M) for all n ∈ ℕ. ✓
- **PA-Conf:** ρ_M is a total function, so →_ρ is deterministic and trivially confluent. ✓
- **PA-Fix:** Fix(ρ_M) = {f} = NF(→_ρ). For f: ρ_M(f) = f ↔ NF(f). For each s_n:
  ρ_M(s_n) = s_{n+1} ≠ s_n ↔ s_n ∉ NF(→_ρ). ✓
- **PA-Prod:** For s_n ∉ Fix: Observable(ρ_M(s_n)) = Observable(s_{n+1}) = ⊤. ✓
- **PA-CoInd:** The set {s_n | n ∈ ℕ} is the greatest fixed point of the NWF coinduction
  operator T^{NWF}(S) = {x ∉ Fix(ρ_M) | ρ_M(x) ∈ S}. By Knaster–Tarski, every
  pre-fixed point P ⊆ T^{NWF}(P) satisfies P ⊆ ∞_M = ν T^{NWF}. ✓
- **PA-Bisim:** R = {(s_n, s_m) | n, m ∈ ℕ} ∪ {(f, f)} is a bisimulation: each s_n
  matches s_m via s_{n+1} ↔ s_{m+1} ∈ R. Since CFix(ρ_M)(s_n) = s_∞ for all n, we have
  s_n ≃_M s_m for all n, m. Hence s_n ≈ s_m ⟹ s_n ≃_M s_m — bisimulation equivariance
  holds. ✓

*Conclusion:* M_Reach satisfies all remaining PA axioms but violates PA-Reach,
so PA-Reach is independent. ∎

---

### Full Independence Matrix

We now have countermodels separating each non-trivial axiom from the rest:

| Axiom | Countermodel | Key feature |
|-------|-------------|-------------|
| PA-WN | Any NWF-only model (e.g., ℕ with n↦n+1) | No termination |
| PA-NWF | Any WF-only model (e.g., {0,1,2} with n↦0) | No infinite paths |
| PA-Conf | M_Conf: {a, b₁, b₂}, a branches to two NFs | Two normal forms reachable from a |
| PA-Fix | M_Fix: {a,b}, ρ_M(a)=a but a →_ρ b | Fixpoint not equal to normal form |
| PA-Prod | M_Prod: {a,b,c,d} with c →_ρ d and Observable(d)=⊥ | One-step productivity failure at convergent boundary |
| PA-WN_top | M_ind: (ℤ, decrement, discrete topology) (`WNtop-Ind` (L1.4.T3)) | Persistent orbit has no 𝒯-limit in the discrete topology |
| PA-Bisim | M_Bisim: {a,b,f,g}, a≈b but CFix(a)≠CFix(b) | Bisimulation ≠ ρ-equivalence |
| PA-Reach | M_Reach: {f} ∪ {s_n} with H_S(s_n) alternating by parity | Horizon signature never stabilizes |

### Axiom Independence
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L1.6.T1 | `Ax-Ind` | | **Novel** |
**Synopsis:** The full independence matrix for the eight-axiom basis: each of the eight basis axioms is independent of the conjunction of the remaining seven. Six countermodels witness this independence — M_Conf, M_Fix, M_Prod, M_Bisim, M_Reach here, and M_ind for PA-WN_top at `WNtop-Ind` (L1.4.T3) — while PA-WN and PA-NWF are separated by the trivial WF-only / NWF-only duality models. PA-CoInd is the one PA axiom outside the basis: it is derivable from PA-NWF in full second-order logic (Park [1981]).

**Source:** CRPT; from the eight-axiom basis (L1.2–L1.3); independence via the countermodel matrix.

*In full second-order semantics, the 8-axiom basis
{PA-WN, PA-NWF, PA-Conf, PA-Fix, PA-Prod, PA-WN_top, PA-Bisim, PA-Reach}
is mutually independent: no basis axiom is derivable from the conjunction of the
other 7. Moreover, PA-CoInd is derivable from PA-NWF and is therefore not part of
the basis.*

*Proof.*

Independence: for each basis axiom A in the 8-axiom set above, the corresponding
countermodel listed in the matrix (or M_ind for PA-WN_top, `WNtop-Ind` (L1.4.T3))
satisfies the other seven basis axioms and fails A.
By soundness, A is not derivable from the other seven.

Derivability of PA-CoInd from PA-NWF: proved in the subsection immediately above by
iterating the successor-closure condition in the PA-CoInd antecedent and showing all
ρ_M-iterates remain outside Fix(ρ_M), which is exactly membership in ∞_M.

Therefore the full-SOL minimal basis is exactly the 8-axiom set above. ∎

### No Splitting
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Remark** | L1.6.R1 | `No-Split` | | **Novel** |
**Synopsis:** No profitable splitting exists for any of the basis axioms: none can be divided into two strictly weaker independent axioms that together imply it. This confirms the basis is minimal — removing or weakening any axiom would change the expressive power of the system.

**Source:** CRPT; from `Ax-Ind` (L1.6.T1).

None of the 8 basis axioms can be profitably split into independent sub-axioms:

- PA-WN, PA-NWF, PA-Prod, PA-Bisim, PA-Reach are first-order sentences — they
  cannot be split without changing their logical content.
- PA-WN_top is a single unique-limit assertion (∀x ∈ ∞_M ∃!L : ρ_M^n(x) → L);
  its existence and uniqueness clauses are not independent — uniqueness is forced
  by TopSep(𝒯) (`TopSep-Uniq` (L1.2.T1)) rather than by a separable axiom — so no
  profitable split exists.
- PA-Conf is a single universal-existential sentence (∀x∀y₁∀y₂ ∃z) — splitting
  it into "local confluence" and "global confluence" is possible but the split is
  redundant in CRPT's orbit-theoretic framework, where confluence is checked on
  ρ_M-orbits rather than all →_ρ-paths. Newman's Lemma (local confluence + SN ⟹
  global confluence) would apply only under strong normalisation, which CRPT does not
  require; but orbit-level local confluence is already sufficient for CFix uniqueness.
- WF-Canon is theorem-level and should not be split into pseudo-axioms; its clauses
  are jointly tied to PA-WN + PA-Conf and CFix definitions.
- LA-Rich(M) is model-local schema content in LA_M, outside PA-axiom minimality.

PA-CoInd is handled separately from basis minimality in full SOL because it is
derivable from PA-NWF there; in schema/Henkin modes it may be retained as an
explicit portability axiom.

No split produces two independent sub-axioms that jointly recover the original.

*Conclusion.* The full-SOL basis is minimal: 8 independent axioms, no redundancy,
no profitable splitting.

---

---
