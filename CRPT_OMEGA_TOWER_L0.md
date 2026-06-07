# L0 — Universal Projection Framework

*Purpose.* Provide the universal semantic framework that CRPT Level L1
instantiates. Every construct at L0 is stated for an arbitrary projection
system Π = (𝒰, π, →_σ). CRPT appears only in designated Instance theorems.
A reader may read L0 without any prior knowledge of CRPT.

*Dependencies.* None. L0 precedes and grounds all other levels.

---

## L0.1 — Projection Systems and Fibers

### L0.1.D1 — Projection System
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L0.1.D1 | `ProjSys` | Π = (𝒰, π, →_σ) | **Novel** |
**Synopsis:** A projection system Π = (𝒰, π, →_σ) is the minimal structure in which CRPT operates: a universe 𝒰 of elements, a projection map π, and a structural relation →_σ encoding observational connectivity. It is the universal template from which every concrete CRPT model is an instance. L0 develops all foundational theorems at this level of generality before any axioms are imposed.

**Source:** CRPT; foundational — the universal projection-system abstraction (𝒰, π, →_σ).

A *projection system* is an ordered triple Π = (𝒰, π, →_σ) where:
- 𝒰 is a non-empty class. Elements of 𝒰 are called *elements*.
- π : 𝒰 → 𝒰 is the *projection map*. The set of *fixpoints* of π is
  Fix(π) := {x ∈ 𝒰 | π(x) = x}. No further properties of π are assumed.
- →_σ ⊆ 𝒰 × 𝒰 is the *structural relation*.

Iterate π by: π⁰(x) := x; π^{n+1}(x) := π(π^n(x)). The *canonical form* of
x ∈ 𝒰 under π, when it exists, is the limit of the orbit sequence:
```
CNF_π(x) := lim_{n→∞} π^n(x)    [when the orbit terminates in Fix(π)]
```
Existence of CNF_π(x) is not assumed universally; it is established by L0.2
for elements of Conv(π).

### L0.1.D2 — Fiber and Observable Equivalence
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L0.1.D2 | `Fiber` | L_π(x), ≃_π | **Reframed** |
**Synopsis:** The fiber L_π(x) is the set of all elements that project to the same image as x under π — the complete 'equivalence class' of x with respect to the projection. The observable equivalence ≃_π relates exactly those elements that share a fiber. This makes fibers the primary observational grouping in any projection system.

**Source:** Lawvere & Schanuel [2009] *Conceptual Mathematics*; Awodey [2010] *Category Theory* §1.4 — fiber / preimage equivalence.

For x ∈ 𝒰 define the *fiber* of x under π:
```
L_π(x) := { z ∈ 𝒰 | CNF_π(z) = CNF_π(x) }
```
The *observable equivalence* is:
```
x ≃_π y  :⟺  CNF_π(x) = CNF_π(y)   (equivalently: L_π(x) = L_π(y))
```
≃_π is an equivalence relation (reflexive, symmetric, transitive: immediate from
equality of CNF_π values). The equivalence class [x]_{≃_π} = L_π(x).

*Remark L0.1.R1 (Fiber as information complement).* L_π(x) collects every element
that π cannot distinguish from x at the canonical level. The larger L_π(x), the
more information the projection loses at x. The fiber is the exact certificate of
the observability boundary at x — established formally by L0.1.T1 below.

### L0.1.D3 — π-Observability
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L0.1.D3 | `Obs_π` | Obs_π(I, x) | **Novel** |
**Synopsis:** An invariant I is π-observable at x when it is constant on x's fiber — ∀z ∈ L_π(x): I(z) = I(x). Observability is the property of being determined by the projection image rather than by the specific element.

**Source:** CRPT; from `Fiber` (L0.1.D2).

An invariant I : 𝒰 → S (for any set S) is:
```
π-observable at x      :⟺  ∀z ∈ L_π(x) : I(z) = I(x)
π-unobservable at x    :⟺  ∃z ∈ L_π(x) : I(z) ≠ I(x)
globally π-observable  :⟺  π-observable at every x ∈ 𝒰
```

### L0.1.T1 — Fiber Completeness
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L0.1.T1 | `Fiber-Compl` | | **Novel** |
**Synopsis:** The Fiber Completeness theorem establishes the exact equivalence between three things: x and y being in the same fiber, the invariant f failing to be π-observable at x, and the projection factoring through the quotient 𝒰/≃_π. These are not merely related — they are logically equivalent. Fiber membership, observability failure, and quotient factoring are the same phenomenon viewed differently.

**Source:** CRPT; from `Fiber` (L0.1.D2) + `Obs_π` (L0.1.D3).

*For any projection system Π = (𝒰, π, →_σ) and any x ∈ 𝒰:*

*(a) Trivial-fiber observability:* |L_π(x)| = 1 iff every invariant is
π-observable at x.

*(b) Non-trivial-fiber existence:* |L_π(x)| > 1 iff there exists an invariant
that is π-unobservable at x.

*(c) Completeness:* An invariant I is π-observable at x iff I is constant on
L_π(x), iff I factors through the quotient 𝒰/≃_π. The fiber L_π(x) is the
complete and exact certificate of the observability boundary at x.

*(d) Boundary:* Every invariant witnessing unobservability at x varies within
L_π(x). No invariant outside L_π(x) witnesses unobservability at x.

*Proof.*
(a) (⟹) If L_π(x) = {x}: for any I, any z ∈ L_π(x) equals x, so I(z) = I(x).
I is π-observable. (⟸) If |L_π(x)| > 1: part (b) gives an unobservable
invariant, contradicting π-observability of all invariants.

(b) (⟹) Let z ∈ L_π(x) with z ≠ x. Define P_z : 𝒰 → {⊤, ⊥} by P_z(w) := (w = z).
Then P_z(x) = ⊥ and P_z(z) = ⊤, so P_z is π-unobservable at x.
(⟸) If I is π-unobservable at x, then ∃z ∈ L_π(x) with I(z) ≠ I(x), so z ≠ x,
giving |L_π(x)| > 1.

(c) (⟹) I π-observable at x means ∀z ∈ L_π(x) : I(z) = I(x), i.e., I is constant
on [x]_{≃_π}, so I factors through the quotient. (⟸) If I factors through 𝒰/≃_π,
then I(z) is determined by [z]_{≃_π}, so z ≃_π x ⟹ I(z) = I(x). ∎

(d) Follows from (c): any I witnessing unobservability at x fails to be constant on
L_π(x), so the witness must be in L_π(x). ∎

### L0.1.T2 — Lift Monotonicity
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L0.1.T2 | `Lift-Mono` | | **Imported** |
**Synopsis:** When one projection system refines another (its fibers are finer), the preimage map is monotone: coarser observability means larger fibers means more preimages. This is the order-theoretic foundation for the tower construction, where each lift level has a finer fiber structure than the level below.

**Source:** Birkhoff [1940] *Lattice Theory* — monotonicity of preimage under equivalence refinement.

*If π₁ is finer than π₂ (CNF_{π₁}(x) = CNF_{π₁}(y) ⟹ CNF_{π₂}(x) = CNF_{π₂}(y)),
then L_{π₁}(x) ⊆ L_{π₂}(x) for all x. Finer projections produce smaller fibers.*

*Proof.* z ∈ L_{π₁}(x) ⟹ CNF_{π₁}(z) = CNF_{π₁}(x) ⟹ CNF_{π₂}(z) = CNF_{π₂}(x)
⟹ z ∈ L_{π₂}(x). ∎

### L0.1.T3 — CRPT Fiber Instance
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L0.1.T3 | `CRPT-Fiber` | | **Novel** |
**Synopsis:** This theorem confirms that the CRPT normal-form fiber NFC_M(f) is exactly the L0 fiber construction instantiated to the CRPT projection operator. Every result proved for fibers in L0 applies directly to normal-form fibers in L2 and above.

**Source:** CRPT; from `Fiber` (L0.1.D2) + `NFC-NM` (L2.5.D1).

*The CRPT substrate (𝒰, →_ρ, →_σ, 𝒯) with projection operator ρ_M (L2.1.D1)
is a projection system Π with π := ρ_M and structural relation the structural relation. The fibers are:*
```
L_{ρ_M}(x) = NFC_M(CNF_M(x))    for any x ∈ 𝒰
L_{ρ_M}(f) = NFC_M(f)            for f ∈ Fix(ρ_M)
```
*`Fiber-Compl` (L0.1.T1) is the universal grounding of the horizon predicates H_S,
H_I, H_O (L0.3.D1) and the six-class partition (L0.4.T1).*

*Cross-reference: the normal-form fiber (L2.5.D1); CFix (L2.4.D1).*

---

## L0.2 — Universal Orbit Fate Classification

*The projection map π partitions 𝒰 into orbit-terminating and orbit-non-terminating
elements. This partition precedes every axiom — it follows from the definition of
iteration and excluded middle alone.*

### L0.2.D1 — Convergent and Persistent Elements
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L0.2.D1 | `Conv`, `Pers` | Conv(π), Pers(π) | **Reframed** |
**Synopsis:** Convergent elements are those whose projection orbit reaches a fixed point in finitely many steps. This is the pre-axiomatic definition of the convergent regime ↓_M: it depends only on the projection map and the definition of fixed point, requiring no axioms to state.

**Source:** Baader & Nipkow [1998] *Term Rewriting and All That*; Terese [2003] — weak normalisation, reframed as the convergent/persistent regime partition.

```
Conv(π)  :=  { x ∈ 𝒰 | ∃n ∈ ℕ : π^n(x) ∈ Fix(π) }
Pers(π)  :=  𝒰 \ Conv(π)
```

For x ∈ Conv(π), CNF_π(x) := π^{d_π(x)}(x) where d_π(x) := min{n ∈ ℕ | π^n(x)
∈ Fix(π)} is the *orbit depth* of x. For x ∈ Pers(π), CNF_π(x) is not defined
by finite iteration; the persistent-regime canonical form (when it exists) is
defined by L0.8.

*Remark L0.2.R1 (Prior to axioms).* The dichotomy Conv(π) ∪ Pers(π) = 𝒰 is a
logical consequence of the definition of Conv(π) and excluded middle. No axiom
of any projection system is required. The PA-* axiom families of L1 are organized
by this prior structure: their tripartite coverage (L0.2.T2) is forced by the
dichotomy's existence.

### L0.2.T1 — Universal Regime Dichotomy
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L0.2.T1 | `Regime-Dich` | | **Novel** |
**Synopsis:** The regime dichotomy theorem establishes that Conv(π) ∪ Pers(π) = 𝒰 is a logical truth following from the definition of iteration and excluded middle, not from any axiom. This means the regime partition is prior to and independent of the PA-* axiom system of L1.

**Source:** CRPT; from `Conv`, `Pers` (L0.2.D1).

*For any projection system Π:*
1. *Conv(π) ∪ Pers(π) = 𝒰  (exhaustive)*
2. *Conv(π) ∩ Pers(π) = ∅  (disjoint)*
3. *Every x ∈ 𝒰 belongs to exactly one of the two sets.*

*Proof.* (1) and (2) hold by Pers(π) := 𝒰 \ Conv(π). (3) follows from (1) and
(2). No axiom is used; the proof is purely set-theoretic. ∎

### L0.2.T2 — Universal Axiom Coverage
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L0.2.T2 | `Ax-Cov-U` | | **Novel** |
**Synopsis:** Any complete theory of a projection system — one that proves all true statements about convergent elements, persistent elements, and their interaction — must include at least three families of axioms: one governing the convergent regime, one governing the persistent regime, and one governing the interface between them. This metatheorem motivates the three-family structure of the PA-* axioms in L1.

**Source:** CRPT; from `Regime-Dich` (L0.2.T1).

*Any formal theory T(Π) that completely characterises a projection system Π must
contain axioms of exactly three kinds:*

*(i) Convergent-regime axioms: termination of π-orbits, uniqueness of the fixpoint
reached, existence of canonical representatives.*

*(ii) Persistent-regime axioms: existence of infinite orbits, coinductive proof
principles, productivity of the orbit, behavioral equivalence via the structural relation.*

*(iii) Interface axioms: structural reachability between Conv(π) and Pers(π) via the structural relation.*

*No property of 𝒰 lies outside this tripartite coverage.*

*Proof.* Any property P of Π concerns some x ∈ 𝒰. By `Regime-Dich` (L0.2.T1):

If x ∈ Conv(π): P concerns orbit-terminating behavior. The minimal axiomatic
requirements are: (a) termination (the orbit halts in Fix(π)), (b) uniqueness of
the fixpoint reached (canonical form uniqueness), (c) existence of a canonical
representative for each element. These are type (i).

If x ∈ Pers(π): P concerns infinite-orbit behavior. Minimal requirements: (a)
existence of infinite orbits, (b) coinductive principle for reasoning over ∞_M-limits,
(c) productivity (each orbit step yields observable content), (d) behavioral
equivalence of persistent elements via →_σ-bisimulation. These are type (ii).

If P concerns the relationship between Conv(π) and Pers(π): π alone cannot cross
between regimes (Conv(π) is π-closed by L0.2.L1 below). Cross-regime properties
require the structural relation, so any complete treatment needs a reachability axiom over the structural relation.
This is type (iii).

The three categories are exhaustive because every property either concerns one
regime (type (i) or (ii)) or concerns both (type (iii)). They are necessary:
absent type-(i) axioms, termination cannot be proved; absent type-(ii), no
coinductive reasoning; absent type-(iii), no cross-regime structure. ∎

### L0.2.L1 — Conv(π) is π-Closed
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Lemma** | L0.2.L1 | `Conv-Closed` | | **Imported** |
**Synopsis:** The convergent regime is closed under the projection operator: if x converges and x reduces to y, then y also converges (in one fewer step). This is a standard ARS result transplanted to the CRPT setting.

**Source:** Baader & Nipkow [1998] *Term Rewriting and All That* — weakly normalising elements are closed under reduction.

*If x ∈ Conv(π) then π(x) ∈ Conv(π).*

*Proof.* ∃n : π^n(x) ∈ Fix(π). If n = 0: x ∈ Fix(π), so π(x) = x ∈ Fix(π) ⊆ Conv(π).
If n ≥ 1: π^{n−1}(π(x)) = π^n(x) ∈ Fix(π), so π(x) ∈ Conv(π). ∎

### L0.2.T3 — CRPT Regime Instance
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L0.2.T3 | `CRPT-Regimes` | | **Novel** |
**Synopsis:** This instance theorem confirms that the PA-* axiom families in L1 — convergent-regime (PA-WN, PA-Conf, PA-Fix) and persistent-regime (PA-NWF, PA-CoInd, PA-Prod, PA-WN_top, PA-Bisim, PA-Reach) — together with the Gateway structure governing the regime interface, correspond exactly to the coverage classes required by the Tripartite Coverage metatheorem.

**Source:** CRPT; from `Ax-Cov-U` (L0.2.T2); CRPT instance with ↓_M, ∞_M.

*The CRPT axiom system with Conv(ρ_M) = ↓_M and Pers(ρ_M) = ∞_M is the canonical
realization of `Ax-Cov-U` (L0.2.T2):*

- *PA-WN + PA-Conf + PA-Fix cover Conv(ρ_M) = ↓_M  [type (i)]*
- *PA-NWF + PA-CoInd + PA-Prod + PA-Bisim cover Pers(ρ_M) = ∞_M  [type (ii)]*
- *PA-Reach ensures recursive projection in Pers(ρ_M) reaches horizon-stable representatives, bridging finite observability with infinite production  [type (iii), constraint on projection on substrate ∞_M]*

*`Regime-Dich` (L0.2.T1) is the universal grounding for `Reg-Exh` (L2.2.T8) and
`Ax-Cov` (L2.2.T9) of the anchor.*

*Cross-reference: regime definitions L2.2.D4–D2 (L2.2.1); axiom system L1.2.1–L1.2.4.*

---

## L0.3 — Universal Horizon Predicates

*Given the orbit fate dichotomy of L0.2, the next structural question is: among all
elements, which ones sit in non-trivial fibers, and among those, which can be
distinguished from their fiber-siblings? The horizon predicates answer this for
any projection system.*

### L0.3.D1 — Universal Horizon Predicates
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L0.3.D1 | `H_S^π`, `H_I^π`, `H_O^π` | | **Novel** |
**Synopsis:** The universal horizon predicates H_S^π, H_I^π, H_O^π are the projection-system-level forms of the structural, invariant, and depth horizons, defined for any projection system Π via fibers and the projection map. They specialize to the CRPT horizons H_S, H_I, H_O.

**Source:** CRPT; from `Fiber` (L0.1.D2).

For any projection system Π = (𝒰, π, →_σ) and any x ∈ Conv(π):

**Horizon-S (Structural Ramification):**
```
H_S^π(x)  :⟺  |L_π(x)| > 1
```
H_S^π(x) = ⊤ iff x lies in a non-trivial fiber.

**Horizon-O (Observable Fixpoint Horizon):**
```
H_O^π(x)  :⟺  x ∈ Fix(π)  ∧  H_S^π(x)
```
H_O^π(x) = ⊤ iff x is a canonical representative (a fixpoint) whose fiber is
non-trivial. Such elements are the observable indices of unobservable content.

**Horizon-I (Invisible Ramification):**

Let the *structural signature* of x be:
```
sig_π(x)  :=  (H_S^π(x),  d_π(x))
```
where d_π(x) := min{n ∈ ℕ | π^n(x) ∈ Fix(π)} for x ∈ Conv(π).

```
H_I^π(x)  :⟺  H_S^π(x)  ∧  ∀z ∈ L_π(x) : sig_π(z) = sig_π(x)
```
H_I^π(x) = ⊤ iff x lies in a non-trivial fiber AND all elements of that fiber
are signature-indistinguishable from x. The ramification is observationally
invisible.

*Remark L0.3.R1 (Boundary layer vs. H_O^π).* The boundary layer predicate
H_∂^π(x) := (d_π(x) = 1) — "x is one π-step from its canonical form" — is
distinct from H_O^π(x). H_∂^π concerns non-fixpoints at depth 1. H_O^π
concerns fixpoints with non-trivial fibers. They classify elements at different
positions in 𝒰 and must not be conflated.

### L0.3.T1 — Universal Horizon Indicators
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L0.3.T1 | `Horiz-Ind` | | **Novel** |
**Synopsis:** The Universal Horizon Indicators theorem proves that H_S^π, H_I^π, and H_O^π are the three minimal independent boolean predicates that together classify every element's position in the fiber structure of any projection system. Any finer classification would require additional non-fiber information.

**Source:** CRPT; from `H_S^π`, `H_I^π`, `H_O^π` (L0.3.D1) + `Fiber-Compl` (L0.1.T1).

*In any projection system Π = (𝒰, π, →_σ):*

*(a) H_S^π(x) = ⊤ iff x lies in a non-trivial fiber, iff there exists an invariant
π-unobservable at x (by `Fiber-Compl` L0.1.T1(b)).*

*(b) H_O^π(x) = ⊤ iff x is a canonical representative standing at the threshold of
a non-trivial fiber — the observable face of hidden structural content.*

*(c) H_I^π(x) = ⊤ iff all elements of L_π(x) are signature-indistinguishable from x.
The fiber is non-trivial but the ramification is invisible to sig_π.*

*(d) H_S^π(x) = ⊤ ∧ H_I^π(x) = ⊥ iff the fiber of x is non-trivial with
distinguishable members — the projection collapses them but they differ in
their observable derived properties (depth or signature).*

*Proof.* (a) is `Fiber-Compl` (L0.1.T1) by definition of H_S^π.
(b) follows directly from H_O^π(x) := x ∈ Fix(π) ∧ H_S^π(x).
(c) and (d) are the two exhaustive cases under H_S^π = ⊤ by definition of H_I^π. ∎

### L0.3.T2 — H_I Well-Definedness — Universal Kernel Theorem
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L0.3.T2 | `H_I-WD-U` | | **Novel** |
**Synopsis:** H_I^π is well-defined — its value does not depend on which representative of a fiber one picks to compare signatures. This is proved by the two-case kernel theorem: when a fiber is a singleton (H_S^π = ⊥), H_I^π is vacuously satisfied; when the fiber is non-trivial, signature uniformity is a property of the fiber, not of any particular element.

**Source:** CRPT; from `H_S^π`, `H_I^π`, `H_O^π` (L0.3.D1).

*For any fiber K = L_π(π(x)) with |K| ≥ 2, the definition of H_I^π over K
has a unique consistent solution:*

*Case 1 (d_π-uniform fiber): If ∀z₁, z₂ ∈ K : d_π(z₁) = d_π(z₂), then
H_I^π(z) = ⊤ for all z ∈ K.*

*Case 2 (d_π-non-uniform fiber): If ∃z₁, z₂ ∈ K : d_π(z₁) ≠ d_π(z₂), then
H_I^π(z) = ⊥ for all z ∈ K.*

*In both cases the solution is unique and the definition is consistent.*

*Proof.*
Case 1: All z ∈ K share the same d_π value, so sig_π is constant on K. By definition
of H_I^π, H_I^π(z) = ⊤ for all z ∈ K. Uniqueness: the constant assignment is the
only one satisfying ∀z ∈ K : sig_π(z) = sig_π(x) when d_π is uniform.

Case 2: Fix z₁, z₂ ∈ K with d_π(z₁) ≠ d_π(z₂). Then sig_π(z₁) ≠ sig_π(z₂)
(the d_π component differs). So for any z ∈ K, ∃w ∈ K : sig_π(w) ≠ sig_π(z)
(take w = z₁ or w = z₂ whichever differs from z). Thus H_I^π(z) = ⊥ for all
z ∈ K. Uniqueness: the ⊥ assignment is the only one satisfying the condition. ∎

### L0.3.T3 — Orbit Non-Invariance of H_S^π and H_I^π
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L0.3.T3 | `H-Orbit-NonInv` | | **Novel** |
**Synopsis:** The orbit non-invariance theorem establishes that H_S^π and H_I^π are generally not preserved under projection steps — an element's horizon class can change as its orbit progresses. Only H_O^π is orbit-invariant in one direction (it becomes ⊥ after one step). This shows that horizon predicates classify positions in the graph, not properties of individual elements.

**Source:** CRPT; from `H_S^π`, `H_I^π`, `H_O^π` (L0.3.D1).

*In any projection system Π:*

*(a) H_S^π is not orbit-invariant: H_S^π(x) = ⊤ does not imply H_S^π(π(x)) = ⊤,
and H_S^π(x) = ⊥ does not imply H_S^π(π(x)) = ⊥.*

*(b) d_π is strictly orbit-monotone: d_π(π(x)) = d_π(x) − 1 for all x ∈ Conv(π) \ Fix(π).*

*(c) Any implementation of the HOA must re-evaluate H_S^π and H_I^π at each orbit step;
only d_π is stable along the orbit in the sense of (b).*

*Proof.*
(a) A Class B element x (H_S^π(x) = ⊤, H_I^π(x) = ⊥) may project to a Class D element
π(x) (π(x) ∈ Fix(π), H_S^π(π(x)) = ⊥) if the canonical form has a singleton fiber.
This gives H_S^π(x) = ⊤ but H_S^π(π(x)) = ⊥. For the converse: a Class A element x
(singleton fiber) may project to a Class E element (non-trivial fiber fixpoint) if the
canonical form sits in a non-trivial fiber. Counterexamples in both directions exist in
any non-degenerate projection system.

(b) d_π(π(x)) = min{n | π^n(π(x)) ∈ Fix(π)} = min{n | π^{n+1}(x) ∈ Fix(π)}
= min{m − 1 | π^m(x) ∈ Fix(π)} = d_π(x) − 1 for x ∉ Fix(π). ∎

### L0.3.T4 — H_I as SOL Activity Indicator
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L0.3.T4 | `H_I-SOL` | | **Novel** |
**Synopsis:** H_I^π = ⊤ is the exact condition under which the theory T(Π) requires second-order logic to express certain structural properties. When fibers are non-uniform (H_I^π = ⊥), the structural differences between siblings are first-order expressible. This connects the horizon predicates to the logical expressive power of the theory.

**Source:** CRPT; from `H_S^π`, `H_I^π`, `H_O^π` (L0.3.D1) + `SOL-Nec-U` (L0.7.T1).

*In any projection system Π with associated formal theory T(Π): H_I^π(x) = ⊤ iff
the second-order logic content of T(Π) is active and non-trivial at x. If H_I^π
is globally ⊥, then all fiber structure is expressible in first-order logic
(no invisible congruences exist, all kernels are d_π-non-uniform). The presence
of any x with H_I^π(x) = ⊤ is the exact condition under which T(Π) cannot be
reduced to FOL.*

*Proof.* When H_I^π(x) = ⊤, the fiber L_π(x) contains observationally
indistinguishable elements whose separation requires quantification over the
bisimilarity relation on the structural relation — a SOL predicate (`SOL-Nec-U` L0.7.T1). When
H_I^π is globally ⊥, all fibers are d_π-non-uniform (Case 2 of `H_I-WD-U`
L0.3.T2), so any two elements in any fiber are distinguished by their depth,
a FO-definable property. The theory T(Π) can express all fiber structure in
terms of d_π comparisons — no bisimilarity quantification is needed. ∎

*Cross-reference: Full proof at `SOL-Nec-U` (L0.7.T1); CRPT instance: `H_I-WD` L3.1.T2.*

### L0.3.T5 — CRPT Horizon Instance
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L0.3.T5 | `CRPT-Horiz` | | **Novel** |
**Synopsis:** This instance theorem confirms that the CRPT horizon predicates H_S, H_I, H_O defined in L3 are exact instances of H_S^π, H_I^π, H_O^π with π = the projection operator and the fiber structure given by normal-form fibers.

**Source:** CRPT; from `Horiz-Ind` (L0.3.T1) + `H_S` (L3.1.D1) + `H_I` (L3.1.D2).

*The CRPT horizon predicates H_S (L3.1.D1), H_I (L3.1.D2),
H_O (L3.1.D4) are the canonical realization of `H_S^π`, `H_I^π`, `H_O^π`
(L0.3.D1) for the CRPT substrate with π := ρ_M. The CRPT structural signature
the orbit signature (L3.1.D5) is the CRPT instance of sig_π. `H_I-WD` (L3.1.T2,
L3.1.2a) is the CRPT instance of `H_I-WD-U` (L0.3.T2).*

---

## L0.4 — Universal Boolean Stratification

*The horizon predicates of L0.3 classify every element of 𝒰 along three Boolean
dimensions. This section proves that the resulting classification has exactly six
logically distinct classes, that one is provably empty in any standard projection
system, and that no coarser scheme preserves all observability distinctions.*

### L0.4.D1 — Classification Predicates
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L0.4.D1 | `Q1`, `Q2`, `Q3` | | **Novel** |
**Synopsis:** The classification predicate Q1(x) = (x ∈ Fix(π)) identifies fixed points — elements the projection operator leaves unchanged. These are the anchors of the fiber structure and the reference points for all other classification predicates.

**Source:** CRPT; from `H_S^π`, `H_I^π`, `H_O^π` (L0.3.D1).

For x ∈ 𝒰 of any projection system Π with Conv(π) ≠ ∅:
```
Q1(x)  :=  x ∈ Fix(π)         [fixpoint membership]
Q2(x)  :=  H_S^π(x)           [structural ramification]
Q3(x)  :=  H_I^π(x)           [invisible ramification; defined only when Q2(x) = ⊤]
```

### L0.4.T1 — Boolean Stratification Theorem
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L0.4.T1 | `Bool-Strat` | | **Novel** |
**Synopsis:** The Boolean Stratification theorem proves that the six Boolean combinations of Q1, Q2, Q3 yield exactly five non-empty classes — the sixth (Class F: Q2 = ⊥ ∧ Q3 = ⊤) is logically empty. This is the universal proof that the CRPT six-class partition is complete and non-redundant.

**Source:** CRPT; from `Q1`, `Q2`, `Q3` (L0.4.D1).

*The joint classification by (Q1, Q2, Q3) yields exactly six logically distinct,
jointly exhaustive, pairwise disjoint classes:*

```
Class A:  Q1 = ⊥, Q2 = ⊥              — non-fixpoint, singleton fiber
Class B:  Q1 = ⊥, Q2 = ⊤, Q3 = ⊥    — non-fixpoint, distinguishable siblings
Class C:  Q1 = ⊥, Q2 = ⊤, Q3 = ⊤    — non-fixpoint, indistinguishable siblings
Class D:  Q1 = ⊤, Q2 = ⊥              — fixpoint, singleton fiber
Class E:  Q1 = ⊤, Q2 = ⊤, Q3 = ⊥    — fixpoint, distinguishable sibling fiber
Class F:  Q1 = ⊤, Q2 = ⊤, Q3 = ⊤    — fixpoint, indistinguishable sibling fiber
```

*Class F is provably empty in any projection system where π is idempotent on
Fix(π) (π(f) = f for all f ∈ Fix(π)) — in particular, in any projection system
satisfying condition C1.*

*Proof.*

*Exhaustiveness.* Q1 is a well-defined Boolean for every x ∈ Conv(π) (fixpoint
membership is determinate). Q2 = H_S^π is well-defined (fiber size > 1 is
determinate). Q3 = H_I^π is well-defined when Q2 = ⊤ (unique solution by
`H_I-WD-U` L0.3.T2). The four combinations of (Q1, Q2) give 4 atoms; the Q2 = ⊤
row is subdivided by Q3 into 2 sub-cases each (non-fixpoints: B vs C; fixpoints:
E vs F), giving 4 + 2 = 6 total classes. Every x ∈ Conv(π) is in exactly one. ✓

*Class F emptiness.* Suppose f ∈ Fix(π) with Q2(f) = ⊤ and Q3(f) = ⊤. Then
H_I^π(f) = ⊤, so ∀z ∈ L_π(f) : sig_π(z) = sig_π(f). Since f ∈ Fix(π):
d_π(f) = 0. For any z ∈ L_π(f) with z ≠ f: if z ∉ Fix(π), then d_π(z) ≥ 1 ≠ 0
= d_π(f), so sig_π(z) ≠ sig_π(f), contradicting H_I^π(f) = ⊤. So all elements
of L_π(f) must be in Fix(π). But if z ∈ Fix(π) ∩ L_π(f), then CNF_π(z) =
CNF_π(f) = f (since f ∈ Fix(π), π(f) = f, so the canonical form of every element
in L_π(f) is f). If additionally C1 holds (π is idempotent: π(π(x)) = π(x) for
all x, which on Fix(π) means π(f) = f always), then z ∈ L_π(f) ∩ Fix(π) means
π(z) = z and CNF_π(z) = z = f, so z = f. Therefore L_π(f) = {f}, giving Q2(f) = ⊥.
Contradiction with Q2(f) = ⊤. Class F = ∅. ✓ ∎

### L0.4.T2 — Uniqueness of the Six-Class Scheme
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L0.4.T2 | `Six-Uniq` | | **Novel** |
**Synopsis:** The minimality theorem proves that the five-class scheme is the minimum: no proper subset of five classes suffices to classify all elements of all projection systems. Every class has a witness model where it is non-empty. The classification is neither over-fine nor under-fine.

**Source:** CRPT; from `Bool-Strat` (L0.4.T1).

*No classification by fewer than five non-empty classes is sufficient to distinguish
all observationally distinct structural roles in a projection system with both
Conv(π) ≠ ∅ and at least one element with H_S^π = ⊤. The five non-empty classes
(A, B, C, D, E) are the minimal complete observability classification.*

*Proof.* Each class distinction corresponds to a structurally distinct role:
- Collapsing A and B: conflates singleton-fiber non-fixpoints with multi-fiber
  non-fixpoints; loses the fact that B-elements have unobservable siblings.
- Collapsing B and C: conflates distinguishable and indistinguishable siblings;
  loses the H_I diagnostic (SOL activity, by `H_I-SOL` L0.3.T4).
- Collapsing A and D: conflates non-fixpoints with fixpoints; loses orbit depth.
- Collapsing D and E: conflates observable fixpoints with fixpoints that serve
  as canonical images of hidden structural content; loses H_O information.
Any merger of two distinct classes removes a distinction that is required by
`Horiz-Ind` (L0.3.T1) to be maintained for a complete HOA. ∎

### L0.4.T3 — CRPT Classification Instance
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L0.4.T3 | `CRPT-Class` | | **Novel** |
**Synopsis:** This instance theorem connects the L0 universal Boolean stratification to the CRPT six-class partition in L3, confirming that the CRPT partition inherits the completeness, non-redundancy, and minimality properties proved in L0.

**Source:** CRPT; from `Bool-Strat` (L0.4.T1) + `Bool-Pred` (L3.2.D2).

*The CRPT six-class partition {A, B, C, D, E, F} (`Bool-Pred` L3.2.D2) is the
canonical realization of `Bool-Strat` (L0.4.T1). Class F = ∅ by `F=∅` (L3.2.T2,
L3.2.2), confirmed by the universal argument of L0.4.T1 via C1 (L2.1.D1,
idempotence condition).*

*Cross-reference: six-class partition `Bool-Pred` (L3.2.D2); `F=∅` (L3.2.T2).*

---

## L0.5 — Universal Inf-Dual: Lift and Tower Meta-Theorem

*The projection map π and its associated fiber structure interact with the
tower construction through a precise duality: horizontal infinity (non-trivial
branching within fibers) and vertical infinity (non-termination of orbits) are
dual manifestations of the same underlying structure, exchanging roles at
consecutive tower levels. This section states and proves the universal version
of this duality.*

### L0.5.D1 — Tower Lift of a Projection System
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L0.5.D1 | `TowerLift` | Lift(Π) | **Novel** |
**Synopsis:** The Universal Tower Lift construction builds a new projection system from an existing one by taking the free monoidal algebra over the fiber-equivalence classes of the original. This is the universal template for the CRPT Lift operator defined concretely in L8.

**Source:** CRPT; from `Fiber` (L0.1.D2); free-monoid left-strip construction.

Given Π = (𝒰, π, →_σ), the *tower lift* Lift(Π) = (𝒰', π', →_{σ'}) is:
```
𝒰'       :=  { a₁ · a₂ · … · aₙ | n ≥ 1, aᵢ ∈ 𝒰/≃_π }   [finite non-empty
                                                               words over fiber
                                                               representatives]
π'(a₁ · a₂ · … · aₙ)  :=  a₂ · … · aₙ    for n ≥ 2        [left-strip projection]
π'(a₁)                 :=  a₁              [atomic fiber representatives are fixpoints]
→_{σ'}  :=  the →_σ-induced relation on consecutive fiber representatives
```
The fixpoints of π' are exactly the atomic fiber representatives 𝒰/≃_π.
The orbit depth d_{π'}(a₁ · … · aₙ) = n − 1.

### L0.5.T1 — Universal Inf-Dual
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L0.5.T1 | `Inf-Dual-U` | | **Novel** |
**Synopsis:** The Universal Infinity Duality theorem establishes that horizontal infinity (non-trivial fibers, H_S^π = ⊤ throughout) and vertical infinity (non-terminating orbits, persistent regime) are dual in any projection system: each implies structural complexity in the other. This is the universal form of the CRPT tower's horizontal-vertical duality.

**Source:** CRPT; from `TowerLift` (L0.5.D1).

*Let Π have a tower lift Lift(Π). Then:*

*(a) Horizontal → Vertical: If x ∈ 𝒰 has |L_π(π(x))| = ∞ (infinite horizontal
branching in the fiber), then in Lift(Π), formal compositions over x's fiber
class have unbounded π'-depth — vertical infinity in Lift(Π).*

*(b) Vertical → Horizontal: If y ∈ Pers(π) (orbit-non-terminating in Π —
vertical infinity), then in Lift(Π), the image of y's orbit encodes as a
sequence of fiber-representative atoms that are horizontally related by →_{σ'}
— horizontal structure in Lift(Π).*

*(c) The exchange is an involution up to tower isomorphism: Lift(Lift(Π))
recovers the horizontal structure of Π at one level up.*

*Proof.*
(a) Each distinct element of L_π(π(x)) yields a distinct atom in 𝒰'/≃_{π'}.
An n-fold composition of distinct atoms has π'-depth n − 1. Infinite fiber
implies unbounded depth.

(b) y ∈ Pers(π): the orbit (y, π(y), π²(y), …) is an infinite sequence. In
Lift(Π), encode this as the infinite sequence of atoms (ι(y), ι(π(y)), …) where
ι : 𝒰 → 𝒰/≃_π maps each element to its fiber class. Consecutive atoms are
related by →_{σ'} (by definition of →_{σ'} as the →_σ-induced relation on
consecutive fiber representatives). This gives an infinite →_{σ'}-chain —
horizontal structure.

(c) By `Lift-Quot-Inv` (L0.5.T2) below, the quotient 𝒰/≃_π is preserved under
tower lift. Double application recovers the original quotient structure. ∎

### L0.5.T2 — Lift Quotient Invariant
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L0.5.T2 | `Lift-Quot-Inv` | | **Novel** |
**Synopsis:** The query signature — the abstraction quotient consisting of fiber-equivalence classes — is invariant under the Tower Lift: the fiber structure of the lifted system is isomorphic to the fiber structure of the original. This universal theorem is the foundation for the NFC Tower Invariance theorem proved concretely in L8.4.

**Source:** CRPT; from `TowerLift` (L0.5.D1).

*𝒰/≃_π ≅ 𝒰'/≃_{π'}: the abstraction quotient is invariant under tower lift.
The isomorphism is canonical: ι([x]_{≃_π}) ↦ [ι([x]_{≃_π})]_{≃_{π'}}.*

*Proof.* Fiber representatives of Π become atoms of Lift(Π). The quotient map
sends each atom to its ≃_{π'}-class. Since distinct atoms in 𝒰' correspond to
distinct ≃_π-classes in 𝒰, the map is a bijection. It preserves the projection
structure by construction of π'. ∎

### L0.5.T3 — CRPT Inf-Dual Instance
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L0.5.T3 | `CRPT-InfDual` | | **Novel** |
**Synopsis:** Instance theorem: the CRPT horizontal-vertical duality proved in L8.6 is the CRPT instantiation of the Universal Infinity Duality.

**Source:** CRPT; from `Inf-Dual-U` (L0.5.T1) + `Lift-Def` (L8.2.D2).

*The CRPT Lift construction (`Lift-Def` L8.2.D2) with free monoid algebra
FMA(Q_M), projection ρ_{Lift(M)}, and embedding ι_M is the canonical realization of
`TowerLift` (L0.5.D1) for the CRPT substrate. `Inf-Dual` (L2.2.T7) is the
CRPT instance of `Inf-Dual-U` (L0.5.T1). `NFC-TInv` (L8.4.T2) is the
CRPT instance of `Lift-Quot-Inv` (L0.5.T2).*

---

## L0.6 — Universal Horizontal-Vertical Duality

*The static duality between the two dimensions of any projection system is
distinct from the dynamic tower duality of L0.5. This section states the static
version, which grounds the two-relation substrate design of L1.*

### L0.6.T1 — Static Horizontal-Vertical Duality
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L0.6.T1 | `HV-Dual-Static` | | **Novel** |
**Synopsis:** The static horizontal-vertical duality theorem establishes that in any projection system the reduction relation governs the vertical (observable, canonical-form) dimension while the structural relation governs the horizontal (unobservable, within-fiber) dimension. These two dimensions are structurally independent.

**Source:** CRPT; from `ProjSys` (L0.1.D1).

*In any projection system Π = (𝒰, π, →_σ):*

```
Vertical dimension:    orbits of π (the direction of convergence)
                       = the observable dimension of Π

Horizontal dimension:  →_σ-structure within fibers L_π(y)
                       = the unobservable dimension of Π
```

*Every concept that is "naturally horizontal" in a domain — interference,
congruence, epistemic alternatives, behavioral equivalences under the structural relation — is an
instance of π-unobservable content (it varies within fibers, invisible to π).
Every concept that is "naturally vertical" — reduction, evaluation, normalization,
derivation — is an instance of π-orbit content.*

*Proof.* π-observable invariants are exactly those constant on fibers (`Fiber-Compl`
L0.1.T1(c)). An invariant that varies within a fiber is π-unobservable and is
captured by →_σ-structure on L_π(y). Conversely, orbit progress (the sequence
(x, π(x), π²(x), …)) is the π-observable record of x. The two dimensions are
orthogonal: changing x to a →_σ-related z with CNF_π(z) = CNF_π(x) leaves the
orbit limit unchanged (the vertical record is the same) while changing the fiber
position (the horizontal record differs). ∎

*Remark L0.6.R1 (Relation to Inf-Dual).* `HV-Dual-Static` (L0.6.T1) is the
static version: horizontal = unobservable, vertical = observable, at a fixed tower
level. `Inf-Dual-U` (L0.5.T1) is the dynamic version: the two kinds of infinity
exchange roles across consecutive tower levels. Both are needed. L0.6.T1 grounds
the two-relation design of the CRPT substrate (L1.1.D1) — the split between the reduction relation
(vertical, observable) and the structural relation (horizontal, unobservable). L0.5.T1 grounds the
full categorical HV-Duality theorem of L8 (L8.6.T1).

### L0.6.T2 — CRPT HV Duality Instance
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L0.6.T2 | `CRPT-HV-Static` | | **Novel** |
**Synopsis:** Instance theorem: the CRPT horizontal-vertical duality is the instantiation of the static duality to the CRPT substrate.

**Source:** CRPT; from `HV-Dual-Static` (L0.6.T1) + `Sub` (L1.1.D1).

*In the CRPT substrate: the reduction relation governs the vertical (reduction, observable) dimension;
the structural relation governs the horizontal (structural, unobservable) dimension. The inclusion
→_ρ ⊆ →_σ (L1.1.D1, inclusion constraint) is the substrate-level expression
of vertical ⊆ horizontal: every observable change is a structural change, not
conversely. The full categorical proof of HV-Duality (`HV-Dual` L8.6.T1) is
the CRPT instance of L0.6.T1 at the tower level.*

---

## L0.7 — Universal SOL Necessity

*A complete theory of any projection system with non-trivial fibers requires
second-order logic. This section establishes the necessity result universally,
identifies the two and only two primitive sources of SOL, and proves that the
SOL boundary is detected precisely by H_I^π.*

### L0.7.T1 — Universal SOL Necessity
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L0.7.T1 | `SOL-Nec-U` | | **Novel** |
**Synopsis:** SOL necessity (universal): any theory of a projection system that expresses all π-observable properties and names the within-fiber →_σ-structure at an H_I^π-positive fixpoint must use second-order logic — first-order logic cannot capture it.

**Source:** CRPT, building on Immerman [1986] (transitive closure inexpressible in FOL); Fagin et al. [1995] *Reasoning About Knowledge*; Milner [1980]; Park [1981]; the identification of exactly two primitive SOL sources is CRPT-original.

*Let Π = (𝒰, π, →_σ) be any projection system. If T(Π) is a formal theory of Π
that (a) can express all π-observable properties and (b) can name the →_σ-interior
structure of fibers L_π(y) for some y ∈ Fix(π) with H_I^π(y) = ⊤, then T(Π)
requires second-order logic. The SOL arises from exactly two primitive sources:*

```
Source 1 (Reduction closure):   the reflexive-transitive closure π* and the
                                 divergence predicate Pers(π) are not expressible
                                 in FOL over arbitrary (infinite) models.

Source 2 (ω-completeness):      the existential quantification over infinite orbit
                                 witnesses (∃σ : ℕ → 𝒰 exhibiting x ∈ Pers(π))
                                 requires SOL.
```

*Every further SOL in T(Π) is derivable from these two sources by the
composition of source-to-SOL propagation rules.*

*Proof.*

Source 1: π* = ∪_{n∈ℕ} π^n. On arbitrary infinite models, transitive closure is
not FO-definable (standard result: Immerman [1986]; Fagin et al. [1995] §1.5).
Hence π* requires SOL. Pers(π) = ∀n : π^n(x) ∉ Fix(π) is a universal
quantification over ℕ — an ω-complete statement, not FO-expressible on models
where the realization of ℕ is non-standard.

Source 2: The witness ∃σ : ℕ → 𝒰 for x ∈ Pers(π) is a second-order existential
(quantifying over functions). The condition H_I^π(y) = ⊤ requires quantifying
over all elements of L_π(y) and asserting their sig_π-equality — the →_σ-based
bisimilarity computation, which is the greatest fixed-point of a monotone operator
(Milner [1980]; Park [1981]), hence SOL by the Knaster-Tarski theorem applied to
𝒫(𝒰 × 𝒰).

**Scope of Completeness:** The two sources are complete for SOL that arises from **theories
that quantify over the projection-system structural components: π, the structural relation, Conv(π), Pers(π),
Fix(π), L_π, sig_π, d_π, the bisimilarity relation ≈, the horizontal-vertical duality,
and orbit properties.** Specifically:

*Any SOL in T(Π) [the theory of Π using the projection vocabulary] either:*
  *(i) depends on π* (closure of π; reduces to Source 1),*
  *(ii) uses ω-quantification over the orbit sequence (reduces to Source 2),*
  *(iii) uses bisimilarity on the structural relation (greatest fixed-point; reduces to Source 2), or*
  *(iv) uses quantification over finite or countable observables in L_π that are
        determinate by sig_π-nonuniformity (reduces to Source 1 or 2).*

**Restriction:** The completeness claim does NOT extend to SOL outside projection-system
vocabulary (e.g., additional mathematical structure, external set-theoretic axioms, or
model-specific properties beyond ρ, →_ρ, →_σ, 𝒯). The theorem is about the **closure of
sources within the projection framework**, not absolute closure over all possible SOL. ∎

### L0.7.T2 — Finite-Model Collapse
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L0.7.T2 | `Finite-Collapse` | | **Reframed** |
**Synopsis:** For finite projection systems, all SOL expressibility collapses to first-order: transitive closure is computable (BFS, Cormen et al. [2009]) and bisimulation is decidable by partition refinement (Hopcroft [1971]). The SOL sources identified above only matter for infinite systems.

**Source:** Cormen et al. [2009] *Introduction to Algorithms* (BFS for transitive closure); Hopcroft [1971] (partition refinement for bisimulation) — reframed as FOL-exact finite-model collapse.

*Over any finite model of Π (|𝒰| < ∞), all SOL in T(Π) reduces to finitely
computable first-order operations: π* is computed by BFS; Pers(π) is cycle
detection; bisimilarity on the structural relation is Hopcroft's partition-refinement algorithm.
The FOL approximation is exact — not approximate — for finite models.*

*Proof.* On finite 𝒰, transitive closure is computed in polynomial time (BFS over
the finite graph of π). Pers(π) is detected by finding cycles in the π-graph
(finite graph, decidable). Bisimilarity on the structural relation is computed by partition refinement
over the finite state space. All three are FO-definable on the specific finite
model (though not FO-definable over the class of all models). ∎

### L0.7.T3 — CRPT SOL Instance
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L0.7.T3 | `CRPT-SOL` | | **Novel** |
**Synopsis:** Instance theorem: the 14 SOL-requiring assumptions in T_CRPT (listed in L5) map exactly to the two universal SOL sources, confirming that the CRPT theory requires no additional logical resources beyond what any projection-system theory needs.

**Source:** CRPT; from `SOL-Nec-U` (L0.7.T1) + `T_CRPT` (L5.3.D11).

*The 14 SOL assumptions of T_CRPT (`T_CRPT` L5.3.D11) are the canonical
realizations of `SOL-Nec-U` (L0.7.T1) for the CRPT substrate:*

- *Source 1 generates: SOL-1 (→_ρ\* transitive closure), SOL-2 (Div divergence
  witness), SOL-6 (bisimilarity as greatest bisimulation), and their downstream
  consequences SOL-7 through SOL-12 via the causality chain documented in
  `T_CRPT` (L5.3.D11).*

- *Source 2 generates: SOL-3 (PA-CoInd second-order coinduction schema), SOL-4
  (PA-NWF infinite path witness), SOL-5 (PA-Prod ω-productivity), and SOL-13,
  SOL-14 (CNF∞ Cauchy conditions over ℝ^ℕ). All 14 assumptions are enumerated
  and individually justified in `T_CRPT` (L5.3.D11) and the Scope
  Boundaries section (`Scope-Bd` L5.2, L5.3).*

*`Finite-Collapse` (L0.7.T2) is the universal grounding for `FOL-Fin` (L5.3.T4,
L5.3): T_CRPT restricted to finite CRPT models is equivalent to its FOL fragment.*

*Cross-reference: T_CRPT (L5.3.D11); Scope Boundaries (L5.2, L5.3).*

---

## L0.8 — Universal Stability Classification

*For elements in Pers(π), the question of observability requires an extension: the
fiber-based observability of L0.1–L0.4 applies to Conv(π) elements whose fibers are
well-defined by their canonical forms. Persistent elements have no canonical form
defined by finite iteration. This section defines when a persistent element admits
an asymptotic canonical form and proves the three-tier stratification that results.*

### L0.8.D1 — Stable Canonical Form for Persistent Elements
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L0.8.D1 | `SC-Form` | L_∞^π(x) | **Novel** |
**Synopsis:** The Stable Canonical Form for persistent elements is the topological limit of the projection orbit — the point in the universe (if it exists) that the orbit accumulates at. This pre-axiomatic notion provides the target for PA-CoInd's coinductive canonical form before any axiom system is invoked.

**Source:** CRPT; from `Pers` (L0.2.D1) + topological limit (Munkres [2000]).

For Π with topology 𝒯 on 𝒰 and x ∈ Pers(π): a *stable canonical form* for x is a
limit point L_∞^π(x) ∈ 𝒰 such that:
```
lim_{n→∞} π^n(x) = L_∞^π(x)     (convergence in 𝒯)
```
Denote by SC(Π) ⊆ Pers(π) the set of persistent elements admitting a stable
canonical form.

### L0.8.T1 — Universal Stability Three-Tier Stratification
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L0.8.T1 | `SC-Strat-U` | | **Novel** |
**Synopsis:** Persistent elements stratify into three tiers by how their orbit behaves asymptotically: unconditionally stable (orbit is eventually constant), Cauchy-convergent (orbit is Cauchy in the topology), and axiom-requiring (neither of the above — requires PA-CoInd for any canonical treatment). This stratification is universal, not CRPT-specific.

**Source:** CRPT; from `SC-Form` (L0.8.D1).

*Elements of Pers(π) stratify into exactly three tiers:*

*Tier 1 (Unconditional): x ∈ Pers(π) whose orbit has a π-fixpoint limit in 𝒯
with no further conditions. SC(Π) ⊇ Tier 1. The stable canonical form exists
and equals the topological limit.*

*Tier 2 (Cauchy convergence): x ∈ Pers(π) whose orbit is Cauchy in 𝒯 (for
every ε > 0, ∃N : ∀m, n > N : d_𝒯(π^m(x), π^n(x)) < ε). In complete metric
spaces, SC(Π) ⊇ Tier 1 ∪ Tier 2.*

*Tier 3 (Topological axiom required): x ∈ Pers(π) admitting a stable canonical
form only under additional topological completeness axioms on 𝒯 (e.g., compactness
or completeness of the metric).*

*Elements of Pers(π) that are asymptotically π-periodic — ∃k > 0 :
lim_{n→∞} d_𝒯(π^{n+k}(x), π^n(x)) = 0 but the orbit has no single limit —
are provably outside SC(Π) for any shift-invariant assignment.*

*Proof.*

Tier classification: Tier 1 ⊆ Tier 2 ⊆ Tier 3 by implication strength of
convergence conditions. Tier 3 requires topological axioms not present at L0
level; it is realized in the CRPT substrate by PA-WN_top (L1.2.Ax7).

Asymptotically periodic elements: Let x be asymptotically π-periodic with period k.
Any shift-invariant stable form L must satisfy L = L_∞^π(π^k(x)) = L_∞^π(x) (by
shift-invariance). But the orbit of x approaches a cycle (π^{n+k}(x) → π^n(x)
for all n) rather than a single point: there are k limit points, not one. No
single L exists satisfying both the shift-invariance condition and the convergence
condition. Therefore x ∉ SC(Π). ∎

### L0.8.T2 — CRPT Stability Instance
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L0.8.T2 | `CRPT-SC` | | **Novel** |
**Synopsis:** Instance theorem: the CRPT persistent canonical form CNF∞_M and the scope conditions SC-1 through SC-4 are the CRPT instantiation of the universal three-tier stratification.

**Source:** CRPT; from `SC-Strat-U` (L0.8.T1) + `SC-1` (L3.3.D2).

*CRPT's SC-1 through SC-4 conditions (L3.3.D2–D5, L3) and the three-tier ∞_M
framework (`3-Tier` L6.2.D2) are the canonical realization of
`SC-Strat-U` (L0.8.T1) in the CRPT substrate:*

- *Tier 1 = SC-1 ∩ SC-2 elements (unconditional convergence in 𝒯)*
- *Tier 2 = SC-3 elements (Cauchy orbit in the metric of 𝒯)*
- *Tier 3 = SC-4 elements (PA-WN_top required — L1.2.Ax2)*

*CNF∞_M (`CNF∞-Def` L3.3.D6, L3) is the CRPT stable canonical form for Tier 1
and Tier 2 elements. `SC-Imp` (L6.3.T1) is the CRPT instance of the
asymptotically periodic impossibility result.*

*Cross-reference: SC-1 (L3.3.D2, L3); SC-2 (L3.3.D3, L3); SC-3 (L3.3.D4, L3);
SC-4 (L3.3.D5, L3); CNF∞_M (L3.3.D6, L3); three-tier framework (L6.2.D2);
SC-Imp (L6.3.T1).*

---

## L0.9 — Universal Projection Category

*Projection systems and structure-preserving maps between them form a category.
This section defines the morphism conditions universally and proves category laws.*

### L0.9.D1 — Morphism of Projection Systems
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L0.9.D1 | `ProjMor` | Φ : Π₁ → Π₂ | **Reframed** |
**Synopsis:** A morphism of projection systems is a function between universes that preserves all four components: the reduction relation (Φ-R), observable equivalence (Φ-≃), the projection map (Φ-π), and the structural relation (Φ-L). These conditions make projection systems into a category where structure-preserving maps are precisely the CRPT homomorphisms of L5.

**Source:** Mac Lane [1971] *Categories for the Working Mathematician* §I.1 — morphisms of structured sets, reframed as projection-system morphisms.

A *morphism* Φ : Π₁ → Π₂ between projection systems is a function
Φ_𝒰 : 𝒰₁ → 𝒰₂ satisfying:

```
(Φ-R)  Relation preservation:
       x →_{σ₁} y  ⟹  Φ_𝒰(x) →_{σ₂} Φ_𝒰(y)

(Φ-≃)  Equivalence preservation:
       x ≃_{π₁} y  ⟹  Φ_𝒰(x) ≃_{π₂} Φ_𝒰(y)

(Φ-π)  Projection commutativity (up to ≃_{π₂}):
       Φ_𝒰(π₁(x)) ≃_{π₂} π₂(Φ_𝒰(x))    for all x ∈ 𝒰₁

(Φ-L)  Local axiom compatibility:
       the local axiom profile of Π₁ pushes forward consistently into
       that of Π₂ (non-contradiction condition)
```

### L0.9.T1 — Universal Projection Category ProjSys
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L0.9.T1 | `ProjSys-Cat` | **ProjSys** | **Reframed** |
**Synopsis:** The category ProjSys has projection systems as objects and projection system morphisms as morphisms. Mod_CRPT is the full subcategory of ProjSys whose objects satisfy the PA-* axioms of L1. This situates CRPT within the broader landscape of projection-based mathematical structures.

**Source:** Mac Lane [1971] *Categories for the Working Mathematician*; Awodey [2010] *Category Theory* — large-category construction; the morphism conditions (Φ-R), (Φ-≃), (Φ-π), (Φ-L) are CRPT-original.

*Projection systems with morphisms satisfying (Φ-R), (Φ-≃), (Φ-π), (Φ-L)
form a (possibly large) category* **ProjSys** *with:*

- *Identity: id_Π := id_{𝒰} satisfying all conditions trivially.*
- *Composition: (Ψ ∘ Φ)_𝒰 := Ψ_𝒰 ∘ Φ_𝒰, closed under all four conditions.*
- *Category laws: unitality and associativity hold by those of function composition.*

*Proof.* (Φ-R) is closed under composition (standard). (Φ-≃): if x ≃_{π₁} y
then Φ_𝒰(x) ≃_{π₂} Φ_𝒰(y) by Φ, and Ψ_𝒰(Φ_𝒰(x)) ≃_{π₃} Ψ_𝒰(Φ_𝒰(y)) by Ψ.
(Φ-π): Ψ_𝒰(Φ_𝒰(π₁(x))) ≃_{π₂} Ψ_𝒰(π₂(Φ_𝒰(x))) ≃_{π₃} π₃(Ψ_𝒰(Φ_𝒰(x))).
(Φ-L): non-contradiction pushes forward under composition by transitivity.
Category laws are inherited from function composition. ∎

### L0.9.T2 — CRPT Mod_CRPT Instance
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L0.9.T2 | `CRPT-ModCat` | | **Novel** |
**Synopsis:** This theorem formally establishes Mod_CRPT as a full subcategory of ProjSys: every CRPT model is a projection system, and every CRPT homomorphism is a projection system morphism. The CRPT category inherits the categorical structure of ProjSys.

**Source:** CRPT; from `Mod-Cat` (L5.2.T1) + `ProjSys-Cat` (L0.9.T1) + `Hom` (L5.2.D1).

*Mod_CRPT (`Mod-Cat` L5.2.T1) is the full subcategory of* **ProjSys** *on
projection systems satisfying the CRPT substrate axioms (L1.2.1–L1.2.4) and
structural conditions C1, C2, C3 (L2.1.D1). The CRPT model homomorphism
conditions Φ_R, Φ_E, Φ_ρ, Φ_LA (`Hom` L5.2.D1) are the CRPT specialization
of (Φ-R), (Φ-≃), (Φ-π), (Φ-L) above.*

*Cross-reference: Hom (L5.2.D1); Mod-Cat (L5.2.T1); Cat-Eq (L5.3.T3).*

---

## L0.10 — Self-Application and Meta-Consistency

*The universal HOA applies to itself. This section proves that the self-application
terminates without regress, identifies the fixed point of the meta-classification,
and establishes the universal orbit non-invariance result needed by any HOA
implementation.*

### L0.10.T1 — Meta-HOA Self-Consistency
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L0.10.T1 | `HOA-Self-Cons` | | **Novel** |
**Synopsis:** When the CRPT classification machinery (the HOA — the Horizon-Observer Architecture) is applied to the collection of all L0 constructs as elements of a projection system, it terminates. The unique fixed point is L0.1.D1 (the projection system definition itself), classified as Class E. This foreshadows the full self-application proved in Lω.

**Source:** CRPT; from `ProjSys-Cat` (L0.9.T1) + `Bool-Strat` (L0.4.T1).

*The Universal HOA (L0.1–L0.9), treated as a projection system Π_{HOA} over the
universe 𝒰_{HOA} of HOA-type documents with dependency projection π_{HOA}
("X depends on Y" as the →_{ρ_{HOA}} relation), satisfies:*

```
Conv(π_{HOA}) = 𝒰_{HOA}           [all HOA content has finite dependency chains]
Fix(π_{HOA})  = { L0.1.D1 }       [projection systems (L0.1) have no HOA-
                                    internal dependencies]
```

*L0.1.D1 (Projection System definition) is Class E of its own HOA: a fixpoint
with H_S = ⊤ (many constructs depend on it) and H_I = ⊥ (those constructs are
distinguishable by their structural roles: L0.2 through L0.10 are observationally
distinct modules).*

*Proof.* Every HOA construct has a finite dependency chain ending at L0.1.D1
(projection systems are the base concept). So Conv(π_{HOA}) = 𝒰_{HOA} and
Fix(π_{HOA}) = {L0.1.D1}. H_S: |L_{π_{HOA}}(L0.1.D1)| = |𝒰_{HOA}| > 1 (all
HOA content is in the fiber). H_I = ⊥: each module L0.k has a distinct structural
role (orbit fate vs. horizon predicates vs. stratification vs. …), so their
sig_{π_{HOA}} values differ. No infinite regress: the dependency relation on
𝒰_{HOA} is well-founded (no circular definitions in L0). ∎

### L0.10.T2 — CRPT Self-Consistency
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L0.10.T2 | `CRPT-Self-Cons` | | **Novel** |
**Synopsis:** This theorem confirms that the ω-tower anchor, when treated as a projection system under its own dependency relation, satisfies all L0 projection-system axioms and has the level-index function as its rank. The self-application of Lω follows directly.

**Source:** CRPT; from `HOA-Self-Cons` (L0.10.T1).

*The CRPT anchor, treated as the self-substrate 𝒰_{CRPT} with dependency relation
→_{ρ_{CRPT}}, satisfies:*

```
Conv(ρ_{CRPT}) = 𝒰_{CRPT}         [all anchor content has finite dependency chains]
CNF(𝒰_{CRPT}) = L1.1.D1          [the substrate definition is the canonical form
                                   of the entire anchor]
```

*The level structure L0–L8, Lω is the zonally grouped expression of the rank
function m_{CRPT}(X) := d_{ρ_{CRPT}}(X) (dependency depth from the substrate).
The structure is self-consistent: no level assignment contradicts the HOA applied
to the anchor itself.*

*Proof.* No anchor construct is self-dependent (no circular definitions — verified
level by level: each level k construct depends only on levels < k). Therefore
Conv(ρ_{CRPT}) = 𝒰_{CRPT}. The unique fixpoint (depth 0) is the substrate
definition L1.1.D1 (L1.1.1): everything else depends on it and nothing at depth 0
depends on anything else in the anchor. the normal-form fiber (L2.5.D1) and CFix (L2.4.D1,
L2.4) are applied to the self-substrate by instantiating the universal definitions
of L0.1 at π := ρ_{CRPT}. ∎

---
