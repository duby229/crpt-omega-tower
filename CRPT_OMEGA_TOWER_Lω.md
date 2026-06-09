# Lω — Meta-CRPT: The Theory Applied to Itself

*Purpose.* Apply the full CRPT apparatus — the HOA, the six-class partition, the
ω-tower — to the CRPT anchor itself as an object. This level constitutes the
self-application of the theory: the anchor content, organized by logical dependency,
forms a projection system to which CRPT's own machinery applies.

*Lω → ? transition.* Lω is the terminal level of the anchor. Its output — the
self-consistent self-classification — does not require a further level within CRPT.
Further application would produce a meta-meta-tower, which lies outside the anchor's
scope. The fixed point of this application is established by Lω.5.T1.

*Dependencies.* L0–L8 entirely.

---

## Lω.1 — CRPT as Its Own Projection System

*Purpose.* Self-Substrate and Self-Model Theorem. This section constructs the self-substrate 𝒰_CRPT — the collection of all ω-tower constructs as a CRPT substrate — and proves that it satisfies all CRPT axioms. CRPT is a model of itself. The dependency relation between constructs serves as the reduction relation.*


### Lω.1.D1 — Self-Substrate 𝒰_CRPT with Topology and Bisimilarity

| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | Lω.1.D1 | `U_CRPT` | 𝒰_CRPT | **Novel** |
**Synopsis:** The self-substrate 𝒰_CRPT is the collection of all labeled formal constructs of the CRPT-proper tower (levels L1 through L8) together with the meta-level Lω, viewed as mathematical objects to which CRPT's own machinery is applied. (L0, the Universal Projection Framework that CRPT instantiates, is the external meta-foundation — independent of CRPT — and is not a member of the self-substrate; correspondingly L1.1.D1 is defined from scratch and is the unique dependency root.) The reduction relation →_{ρ_CRPT} is the logical dependency relation: X →_{ρ_CRPT} Y means Y is a direct prerequisite of X. This turns the tower itself into a CRPT substrate.

**Source:** CRPT; from `Sub` (L1.1.D1) applied to the tower's own constructs.

The *self-substrate* of CRPT is the class:
```
𝒰_CRPT  :=  { all labelled constructs of the anchor: definitions, axioms,
              theorems, lemmas, corollaries, remarks at levels L1–L8 (and Lω) }
```
with relations and topology:
```
→_{ρ_CRPT}  :  X →_{ρ_CRPT} Y  iff  Y is logically required to define or prove X
               (the dependency relation on anchor constructs)

ρ_CRPT(X)  :=  the most primitive construct that X directly depends on
               (the immediate dependency projection)

→_{σ_CRPT}  :  the cross-reference relation (X →_{σ_CRPT} Y iff X cites Y
               without logical dependency — notational or motivational reference)

𝒯_CRPT     :  the discrete topology on 𝒰_CRPT (every subset is open; all elements isolated)
               Justification: 𝒰_CRPT is a finite set of labeled constructs, so all points
               satisfy the T₂ (Hausdorff) separation axiom trivially. The discrete topology
               ensures TopSep(𝒯_CRPT) holds and all continuity requirements are satisfied.

≈_CRPT     :  the bisimilarity relation on →_ρ-orbits defined by the coinductive greatest
               fixed point of the bisimulation functional on (𝒰_CRPT, →_ρ_CRPT).
               Remark: In the WF regime (∞_CRPT = ∅), every orbit is finite, so
               bisimilarity coincides with equality on fixpoints (L1.1.D1 has singleton fiber
               containing only itself since it depends on nothing).
```

### Lω.1.T1 — Self-Substrate is a CRPT Model

| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | Lω.1.T1 | `Self-Model` | | **Novel** |
**Synopsis:** The self-substrate theorem establishes that (𝒰_CRPT, →_{ρ_CRPT}, →_{σ_CRPT}, 𝒯_CRPT) is a valid CRPT model satisfying all the substrate conditions and axiom profiles. CRPT is not merely self-referential in name — it passes its own formal criteria for being a CRPT model. This is the foundational fact that makes Lω non-trivial.

**Source:** CRPT; from `U_CRPT` (Lω.1.D1) + `CRPT-Mod` (L1.5.D4).

*(M_CRPT, ρ_CRPT, C1, C2, PA-*) where M_CRPT := (𝒰_CRPT, →_{ρ_CRPT}, →_{σ_CRPT}, 𝒯_CRPT)
satisfies all CRPT substrate axioms and conditions for a genuine CRPT model.*

**Verification:**

**(1) Substrate axioms (L1.1.D1):** M_CRPT = (𝒰_CRPT, →_{ρ_CRPT}, →_{σ_CRPT}, 𝒯_CRPT) is a substrate:
  - 𝒰_CRPT is a non-empty class (all constructs). ✓
  - →_{ρ_CRPT} ⊆ 𝒰_CRPT × 𝒰_CRPT is the dependency relation. ✓
  - →_{σ_CRPT} ⊆ 𝒰_CRPT × 𝒰_CRPT is the cross-reference relation. ✓
  - 𝒯_CRPT is the discrete topology (every subset open). ✓
  - Inclusion: →_{ρ_CRPT} ⊆ →_{σ_CRPT} holds (dependency implies cross- reference). ✓*

**(2) Topology requirements (L2.3.D2, TopSep):** 𝒯_CRPT satisfies T₂ (Hausdorff) directly:
  - For any distinct X, Y ∈ 𝒰_CRPT, both singleton sets {X} and {Y} are open in the discrete
    topology and disjoint. ✓
  - Continuity of ρ_CRPT: For any open U ⊆ Fix(ρ_CRPT), ρ_CRPT^{-1}(U) = U (fixpoints map
    to themselves), which is open (finite union of singletons). ✓*

**(3) Projection operator conditions (L2.1.D1, C1–C2):**

  *C1 (Step-or-Fix):* ∀X ∈ 𝒰_CRPT : (X →_{ρ_CRPT} ρ_CRPT(X)) ∨ (ρ_CRPT(X) = X ∧ NF(X))
    - If X ∉ Fix(ρ_CRPT), then X has immediate dependencies; ρ_CRPT(X) is the most primitive one.
    - By definition of →_{ρ_CRPT}, ρ_CRPT(X) ≠ X, so X →_{ρ_CRPT} ρ_CRPT(X). ✓
    - If X ∈ Fix(ρ_CRPT), then X is L1.1.D1 (has no dependencies), so ρ_CRPT(X) = X = NF(X). ✓

  *C2 (Bisimulation Equivariance):* ∀X, Y ∈ 𝒰_CRPT : X ≈_CRPT Y ⟹ ρ_CRPT(X) ≈_CRPT ρ_CRPT(Y)
    - 𝒰_CRPT is finite (a finite set of labeled constructs). ✓
    - On finite→_ρ structures, bisimilarity ≈_CRPT is computable by partition refinement. ✓
    - ρ_CRPT is a deterministic function (single immediate dependency per construct). ✓
    - For any bisimulation R containing (X, Y): if X →_ρ Z for some Z, then Z is the unique
      →_ρ-successor of X (ρ_CRPT(X)). Similarly for Y → ρ_CRPT(Y). Since (X, Y) ∈ R
      (bisimulation), the forward and backward conditions give (ρ_CRPT(X), ρ_CRPT(Y)) ∈ R_next.
      By coinduction over all bisimulations, X ≈_CRPT Y ⟹ ρ_CRPT(X) ≈_CRPT ρ_CRPT(Y). ✓*

**(4) PA-* axioms (L1.2 and L2.2):**

  *PA-WN (convergent regime):* Every orbit from X reaches Fix(ρ_CRPT) = {L1.1.D1} in finite steps.
    - 𝒰_CRPT is finite. The dependency relation→_{ρ_CRPT} is well-founded (no cycles by
      level-number enforcement: Lk.* constructs depend only on Lj.* with j < k). ✓
    - Weak normalisation holds: all elements have terminating ρ_CRPT-orbits. ✓

  *PA-Conf (confluence):* All →_{ρ_CRPT}-paths from the same X converge.
    - ρ_CRPT is a deterministic function (each construct has a unique most primitive dependency). ✓
    - No branching: every element has at most one →_{ρ_CRPT}-successor (ρ_CRPT(X)). ✓
    - All paths coincide (diamond property trivially holds). ✓

  *PA-Fix:* ρ_CRPT(X) = X ⟺ NF(X).  By definition of →_{ρ_CRPT} and NF (normal form = no outgoing edges). ✓

  *PA-Bisim:* Bisimilar structures in finite →_ρ systems have identical orbits (w.f.). ✓

  *PA-CoInd (coinduction):* Park's Lemma applies to ℘(𝒰_CRPT) with monotone operators. ✓

  *PA-Prod (productivity):* On finite 𝒰_CRPT, all non-fixpoint elements produce observable content
    (empty in the WF regime; constraint is vacuous). ✓

  *PA-NWF:* ∞_{CRPT} = ∅ (no persistent elements). Every element reaches Fix(ρ_CRPT) finitely. ✓*

**(5) Regime partition:** ↓_{CRPT} = 𝒰_CRPT (all elements convergent); ∞_{CRPT} = ∅ (no persistent). Self-Model is a **pure WF** model (`Pure-WF` profile, L1.2). ✓

*Proof completion.* All claims are verified above. M_CRPT is a genuine CRPT model satisfying
the substrate definition (L1.1.D1), all projection operator conditions (C1–C2), the topological
requirements (TopSep on 𝒯_CRPT), and all axioms in the pure WF profile. ∎

---

## Lω.2 — Self-Horizon Classification

*Purpose.* Self-Horizon Classification. This section applies the six-class partition to the self-substrate, assigning each anchor construct to its class (A–E). The substrate definition L1.1.D1 is Class E (unique fixed point with siblings); all other constructs are classified by their dependency depth and sibling structure.*


### Lω.2.T1 — Self-Horizon Classification of the Anchor

| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | Lω.2.T1 | `Self-Horiz` | | **Novel** |
**Synopsis:** The Self-Horizon Classification assigns each anchor construct X ∈ 𝒰_CRPT to its six-class partition class under the self-substrate. The substrate definition L1.1.D1 is Class E (it is a fixed point of the dependency relation with multiple constructs depending on it). All other constructs are Class A (no siblings, not at the boundary) or Class D (no siblings, at the boundary layer — one dependency step from L1.1.D1).

**Source:** CRPT; from `U_CRPT` (Lω.1.D1) + `6-Part` (L3.2.T1).

*The HOA applied to 𝒰_CRPT via ρ_CRPT yields the following classification:*

```
Level       Rank m_CRPT(X)    Class    Interpretation
────────    ──────────────    ─────    ────────────────────────────────────
L0          ∞ / pre-0         —        Meta-framework: precedes CRPT's own HOA
L1.1.D1     0                 E        Unique fixpoint of ρ_CRPT; H_S = ⊤
                                        (many constructs depend on it); H_I = ⊥
                                        (those constructs are distinguishable)
L1 rest     1                 B        Depth-1 non-fixpoints; distinguishable by
                                        structural role (axiom vs. definition)
L2          2–3               B        Depth-2–3; distinguishable by function
L3          3–4               B        Depth-3–4; fiber/horizon machinery
L4          5                 B        Depth-5; classification output
L5          5–6               B        Depth-5–6; observer/perturbation tools
L6          7–8               B        Depth-7–8; formal model theory
L7          8–9               B        Depth-8–9; orbit theory
L8          8+                B        Depth 8+; categorical and tower
Lω          ∞ / self          —        Self-referential: applies HOA to 𝒰_CRPT
```

*Every level except L0 and Lω classifies as Class B: non-fixpoint, H_S = ⊤
(multiple constructs per level projecting to the same dependency points),
H_I = ⊥ (all constructs are distinguishable by their structural roles and
depth values). L1.1.D1 is Class E: the unique fixpoint with non-trivial fiber.*

*Proof.* Apply the HOA (`Bool-Pred` L3.2.D2; `6-Part` L3.2.T1) with
π := ρ_CRPT:

- **Fix(ρ_CRPT) = {L1.1.D1}:** The substrate definition is the unique construct
  with no outgoing dependencies (ρ_CRPT(L1.1.D1) = L1.1.D1). Therefore it is the
  unique fixpoint.

  *Fiber analysis:* NFC_{ρ_CRPT}(L1.1.D1) = {L1.1.D1} (a fixpoint's fiber under
  CFix(ρ_CRPT) contains only itself). The fiber is a singleton.

  *H_S determination:* H_S(L1.1.D1) = ⊤ iff |ρ_CRPT^{-1}(L1.1.D1) \ {L1.1.D1}| ≥ 1,
  i.e., iff there exists at least one non-fixpoint construct whose immediate
  dependency is L1.1.D1. Every depth-1 construct (L1 rest: axioms, substrate
  conditions) has ρ_CRPT(X) = L1.1.D1 directly. So the preimage
  ρ_CRPT^{-1}(L1.1.D1) contains all depth-1 elements — the structural axioms
  PA-WN, PA-Conf, PA-Fix, PA-Bisim, PA-CoInd, PA-Prod, PA-NWF and the axiom
  system definitions. Therefore H_S(L1.1.D1) = ⊤. ✓

  *H_I determination:* H_I(L1.1.D1) = ⊤ iff the kernel ker(ρ_CRPT, L1.1.D1) is
  sig_{ρ_CRPT}-uniform, i.e., iff all elements X with ρ_CRPT(X) = L1.1.D1 share
  the same orbit signature sig_{ρ_CRPT}(X). The depth-1 elements have different
  orbit signatures: PA-WN (Class B, H_S = ⊤ at the level of its own fiber) differs
  in sig from PA-NWF (Class B, NWF regime-enabling axiom) in H_S value since the
  fibers of those axioms have different ramification structures. Therefore the
  kernel is not sig_{ρ_CRPT}-uniform: H_I(L1.1.D1) = ⊥. ✓

  *Class determination:* x = L1.1.D1 ∈ Fix(ρ_CRPT), H_S = ⊤, H_I = ⊥. By
  `Bool-Pred` (L3.2.D2): this is **Class E**. ✓

- **All other x ∈ 𝒰_CRPT:** x ∉ Fix(ρ_CRPT) (no other construct has no
  dependencies). Every non-substrate construct has at least one dependency, and
  ρ_CRPT(x) ≠ x.

  *H_S:* For any non-fixpoint x at level Lk (k ≥ 1), the fiber
  NFC_{ρ_CRPT}(CFix(ρ_CRPT)(x)) contains all constructs that share the same
  canonical dependency root. Since every level Lk has multiple constructs mapping
  to the same dependency points (e.g., multiple theorems at L2 all depend on the
  projection operator L2.1.D1), the fiber is non-singleton: H_S(x) = ⊤. ✓

  *H_I:* Constructs at the same level are distinguishable by their structural role
  (definition vs. theorem vs. axiom) and by d_{ρ_CRPT} values (constructs at the
  same depth that depend on different sub-dependencies have different sig_{ρ_CRPT}
  values). The kernel ker(ρ_CRPT, ρ_CRPT(x)) is not sig_{ρ_CRPT}-uniform in
  general: H_I(x) = ⊥. ✓

  *Class:* x ∉ Fix(ρ_CRPT), H_S = ⊤, H_I = ⊥. By `Bool-Pred` (L3.2.D2):
  **Class B**. ✓ ∎

---

## Lω.3 — Rank Ordering m_CRPT

*Purpose.* Rank Ordering of Anchor Constructs. This section defines m_CRPT(X) — the rank of a construct X in the self-substrate — as its tower-level index (1 for L1, 2 for L2, …, 8 for L8, ω for Lω; L0 is the external meta-foundation and is not ranked). This rank extends the derivation height derivation height to the self-substrate and confirms that the self-substrate is well-founded.*


### Lω.3.D1 — Rank Function m_CRPT

| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | Lω.3.D1 | `m_CRPT` | m_CRPT(X) | **Novel** |
**Synopsis:** The rank function m_CRPT(X) = k when X is a construct in level Lk (m_CRPT(X) ∈ {0, 1, ..., 8, ω}). This is the derivation height of X in the self-substrate: it counts how many dependency steps are needed to reach L1.1.D1 from X. Level indices directly encode derivation heights in the self-application.

**Source:** CRPT; from `d_M` (derivation height, L2.3.D2) + `U_CRPT` (Lω.1.D1).

```
m_CRPT(X)  :=  d_{ρ_CRPT}(X)  =  min{ n ∈ ℕ | ρ_CRPT^n(X) = L1.1.D1 }
```
The *CRPT rank* of construct X is its dependency depth from the substrate
definition. The level structure L0–L8, Lω is the zonally grouped expression
of m_CRPT: each level Lk groups all constructs X with m_CRPT(X) in the
corresponding range of the rank order.

---

## Lω.4 — Tower of Towers

*Purpose.* Tower of Towers. This section proves that applying the Lift construction to the self-substrate produces a tower whose levels are themselves towers — a tower of towers. This is the maximal self-referential structure CRPT generates before closing at the fixed point of Lω.5.*


### Lω.4.T1 — Tower of Towers Structure

| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | Lω.4.T1 | `Tower-of-Towers` | | **Novel** |
**Synopsis:** The Tower of Towers theorem: applying the Lift construction to the self-substrate 𝒰_CRPT produces a tower Lift(Self_CRPT), Lift²(Self_CRPT), ... whose levels are themselves isomorphic to towers of CRPT models. The self-application produces the most complex object the CRPT tower construction can generate — a tower whose elements are themselves towers.

**Source:** CRPT; from `Tower` (L8.4.D1) + `U_CRPT` (Lω.1.D1).

*The ω-tower Tower(M) (`Tower` L8.4.D1) applied to the self-substrate
M := Self_CRPT (𝒰_CRPT with ρ_CRPT) produces a tower-of-towers structure:*
```
Tower(Self_CRPT)  =  (Self_CRPT, Lift(Self_CRPT), Lift²(Self_CRPT), …)
```
*At each level n, the atoms of Lift^n(Self_CRPT) are the fiber-equivalence classes
of Lift^{n−1}(Self_CRPT) — i.e., the equivalence classes of anchor constructs
under the n-fold iterated ρ_CRPT-quotient.*

*The tower is well-founded in the upward direction (each lift is a legitimate CRPT
model by `Lift-Compat` (L8.3.T4)). The base level Self_CRPT is itself a
WF model (∞_{Self_CRPT} = ∅) so all levels of Tower(Self_CRPT) are WF CRPT models.*

*Proof.* `Lift-Compat` (L8.3.T4) applies at each level. WF-ness propagates:
if Mₙ is WF (∞_{Mₙ} = ∅) then Lift(Mₙ) has no persistent elements (all words in
FMA(Q_{Mₙ}) reach an atomic fixpoint q ∈ Q_{Mₙ} in |w|−1 steps). ∎

---

## Lω.5 — Fixed Point of the Meta-Tower

*Purpose.* Self-Consistency Fixed Point. This section proves the culminating theorem: the level structure of the ω-tower is the unique fixed point of the meta-HOA operation. Applying CRPT's classification machinery to 𝒰_CRPT recovers the ω-tower structure exactly. The theory closes without regress.*


### Lω.5.T1 — Self-Consistency Fixed Point

| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | Lω.5.T1 | `Self-FP` | | **Novel** |
**Synopsis:** The Self-Consistency Fixed Point theorem: the level structure of the ω-tower is the unique fixed point of the meta-HOA operation. CRPT applied to its own constructs recovers exactly those constructs in exactly their existing arrangement.

**Source:** CRPT; closes `CRPT-Self-Cons` (L0.10.T2); from `Self-Model` (Lω.1.T1) + `m_CRPT` (Lω.3.D1).

*The CRPT anchor, organized by the level structure L0–L8, Lω, is the unique
fixed point of the operation: "apply CRPT's HOA to CRPT's own content and
reorganize by the resulting rank ordering." Specifically:*

*1. The rank ordering m_CRPT(X) produced by `Self-Horiz` (Lω.2.T1) induces exactly
the level structure L0–L8, Lω of the anchor.*

*2. Applying CRPT's HOA to the level-structured anchor produces the same rank
ordering m_CRPT: no further restructuring is required.*

*3. The unique fixpoint of the meta-projection is L1.1.D1 (the substrate definition),
which is Class E of the anchor's own HOA.*

*Proof.*

**(1)** m_CRPT(X) = k iff X is at level Lk: this is the definition of the level
structure as the rank-grouped presentation of 𝒰_CRPT. The grouping is exact: every
construct in Lk has m_CRPT(X) in the Lk-range by construction, and every construct
with that rank is in Lk by the dependency enforcement (Lk.* constructs depend only
on Lj.* with j < k, as verified in `Self-Model` Lω.1.T1 clause (4), PA-WN step). ✓

**(2)** The HOA applied to the level-structured anchor gives the same classification
as `Self-Horiz` (Lω.2.T1): Class B for all non-substrate constructs, Class E for
L1.1.D1. The level-grouping is purely presentational — it does not alter the
dependency relation ρ_CRPT, the fixpoint set Fix(ρ_CRPT), or the fiber structure.
Therefore re-applying the HOA to the grouped presentation gives an identical output
to applying it to the raw 𝒰_CRPT. ✓

**(3) Uniqueness of the fixed point.**

*Existence:* L1.1.D1 is Class E (proved in Lω.2.T1) and is stable: under any
re-application of the HOA to 𝒰_CRPT, L1.1.D1 is still the unique element with
ρ_CRPT(L1.1.D1) = L1.1.D1 (it has no dependencies — this is structural, not
contingent on organization). Fix(ρ_CRPT) = {L1.1.D1} is therefore invariant across
all re-applications. The Class E designation is consequently stable. ✓

*Uniqueness:* Suppose some other construct Y ≠ L1.1.D1 were Class E. Then Y would
need to be:
  (a) In Fix(ρ_CRPT) — i.e., ρ_CRPT(Y) = Y, meaning Y has no logical dependencies.
  (b) With H_S(Y) = ⊤ — i.e., the preimage ρ_CRPT^{-1}(Y) \ {Y} is non-empty.

But condition (a) requires that Y depends on nothing in 𝒰_CRPT. The only content
that depends on nothing is the substrate definition itself (L1.1.D1): all axioms
depend on the substrate, all theorems depend on definitions and axioms, and so on.
No other construct satisfies (a). Therefore no Y ≠ L1.1.D1 can be Class E, and
the Class E fixed point is unique. ✓

*Stability under re-application:* Let HOA_n denote the n-th re-application of the
HOA to (𝒰_CRPT, ρ_CRPT). Since Fix(ρ_CRPT) = {L1.1.D1} is invariant (it depends
only on ρ_CRPT, not on the HOA output), HOA_n produces Class E at L1.1.D1 and
Class B elsewhere for all n ∈ ℕ. The sequence HOA_n is eventually constant from
n = 1 (it is constant from the first application). The fixed point of the operation
"apply HOA and reorganize" is the level structure itself, with L1.1.D1 as its
unique Class E element. ✓

By `6-Part` (L3.2.T1) instantiated at π := ρ_CRPT, the Class E assignment
of L1.1.D1 is the correct output. The fixed point is unique and stable. ∎

### Self-Consistency, Not Generativity

| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Remark** | Lω.5.R2 | `SelfCons-NotGen` | | **Novel** |
**Synopsis:** Lω is a self-consistency certificate, not a generative decomposition: the forward dependency projection ρ_CRPT collapses every construct to the single root L1.1.D1, so the self-application reveals no structure finer than the rank strata. Any finer internal organization lives in the co-dependency (in-degree / ramification) direction, orthogonal to ρ_CRPT.

**Source:** CRPT; from `Self-FP` (Lω.5.T1) + `Lω-FixedPt-Unique` (Lω.7.T2) + `Self-Horiz` (Lω.2.T1).

`Self-FP` (Lω.5.T1) certifies that the tower is its own fixed point under self-application — a **self-consistency** result. It is not a generative decomposition: the forward dependency projection ρ_CRPT collapses every construct to the single root L1.1.D1 (`Lω-FixedPt-Unique` (Lω.7.T2)), so the self-application reveals no internal structure finer than the rank strata, and the resulting classification is flat (one Class E sink, all else Class B, `Self-Horiz` (Lω.2.T1)). Any finer internal organization of the theory would live in the *co-dependency* (in-degree / ramification) direction, which is orthogonal to the forward projection ρ_CRPT and outside the scope of this self-application.

### The Anchor Is Self-Consistent

| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Remark** | Lω.5.R1 | `Anchor-SelfConsist` | | **Novel** |
**Synopsis:** Self-FP establishes that the anchor is self-consistent.

**Source:** CRPT; from `Self-FP` (Lω.5.T1).

`Self-FP` (Lω.5.T1) is the
formal statement of the anchor's self-consistency: the theory correctly classifies
its own content, the classification is stable under reapplication, and the structure
that results is exactly the one presented here. CRPT is an instance of its own
universal framework (L0), organized by its own rank ordering (Lω.3), and classified
by its own HOA (Lω.2). The loop closes without regress because the self-substrate
is purely WF: ∞_{Self_CRPT} = ∅ and the classification terminates at the substrate
fixpoint L1.1.D1.

---

## Lω.6 — The Anchor as the Fractal It Describes

*Purpose.* Apply the CRPT-fractal theorem (L8.9.T2) to the CRPT self-substrate
(Lω.1.D1). This is the formal closure of the fractal interpretation: the anchor
does not merely describe CRPT-fractal projection systems; under its own
self-substrate projection, the anchor is one.

### Lω.6.T1 — Anchor Fractality Theorem

*Purpose.* Anchor Fractality. This section proves that the ω-tower, as a self-applied CRPT model, is fractal in the sense of L8.9: its tail is self-similar to the whole. The fractality claim is internal to CRPT — provable within the theory — and introduces no new objects beyond the tower already constructed.*

### Anchor-Fractal Closure

| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | Lω.6.T1 | `Anchor-Fractal` | Frac(Self_CRPT) | **Novel** |
**Synopsis:** The anchor fractality theorem shows that the ω-tower, viewed as a CRPT model under the self-application, exhibits the same fractal structure as every CRPT tower (L8.9.T2): its query signature Q_{CRPT} and local structure replicate at every level. The self-application does not produce a qualitatively different object — it produces exactly the same kind of fractal tower that CRPT builds for any base model, confirming the theory's internal coherence.

**Source:** CRPT; from `Self-Model` (Lω.1.T1) + `Twr-Fractal` (L8.9.T2).

*The CRPT anchor, regarded as the self-substrate Self_CRPT defined in Lω.1.D1,
is a CRPT-fractal projection system in the sense of `CRPT-Fractal` (L8.9.D2):*
```
Frac(Self_CRPT)
```

*Equivalently: the theory whose mathematical object is recursive projection under
Lift is itself a recursive projection system whose generated tower is fractal by
the same theorem.*

*Proof.* By `Self-Model` (Lω.1.T1), Self_CRPT ∈ Mod_CRPT. Therefore the hypotheses
of `Twr-Fractal` (L8.9.T2) hold with M := Self_CRPT. Applying L8.9.T2 gives:

(F1) ∀n ∈ ℕ, Lift^n(Self_CRPT) ∈ Mod_CRPT.

(F2) ∀k ∈ ℕ, Tower(Lift^k(Self_CRPT)) ≅ Tail_k(Tower(Self_CRPT)).

(F3) ∀n ∈ ℕ, Q_{Lift^n(Self_CRPT)} ≅ Q_{Self_CRPT}.

(F4) At every adjacent pair Lift^n(Self_CRPT) → Lift^{n+1}(Self_CRPT),
horizontal self-substrate fiber structure becomes vertical composition structure,
and vertical dependency-orbit structure becomes horizontal structure at the next
scale.

These four clauses are exactly `CRPT-Fractal` (L8.9.D2) instantiated at
Self_CRPT. Hence Frac(Self_CRPT). ∎

### Lω.6.C1 — The Fractal Claim is Internal to CRPT

| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Corollary** | Lω.6.C1 | `Fractal-Internal` | | **Novel** |
**Synopsis:** The fractality of the ω-tower is internal to CRPT: the proof that the anchor is a CRPT-fractal projection system (L8.9.T2) applies to Self_CRPT without any external axioms. The self-application does not require any new mathematical resources not already present in the tower.

**Source:** CRPT; from `Anchor-Fractal` (Lω.6.T1).

*The statement "the CRPT anchor is a fractal" is not an added metaphor or external
geometric analogy. It is the theorem Frac(Self_CRPT), proved from the anchor's own
projection, Lift, quotient-invariance, horizontal-vertical duality, and self-model
theorems.*

*Proof.* `Anchor-Fractal` (Lω.6.T1) proves Frac(Self_CRPT). The predicate Frac
is defined internally in `CRPT-Fractal` (L8.9.D2) using only Tower, Lift, the query signature,
and HV-Dual, all of which are anchor constructs. Therefore the fractal claim is
internal to CRPT. ∎

### Lω.6.C2 — No Internal ω-State is Introduced

| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Corollary** | Lω.6.C2 | `No-Internal-ω-State` | | **Novel** |
**Synopsis:** No internal ω-state is introduced by the self-application: 𝒰_CRPT is a finite set, every dependency chain terminates at L1.1.D1 in finitely many steps, and Lω.7.T1 confirms ∞_{CRPT} = ∅. The 'ω' in 'ω-tower' is a tower-level index, not a persistent orbit.

**Source:** CRPT; from `Anchor-Fractal` (Lω.6.T1) + `Tower` (L8.4.D1).

*The fractal theorem introduces no element Lω ∈ 𝒰_{Self_CRPT} and no state
M_ω inside Tower(Self_CRPT). The ω-indexing is an external indexing of all finite
Lift iterates.*

*Proof.* By `Tower` (L8.4.D1), Tower(M) is the sequence (M₀, M₁, M₂, …) indexed
by n ∈ ℕ with M_{n+1} := Lift(M_n). No clause of L8.2.D1 defines an object M_ω.
By `the self-substrate universe` (Lω.1.D1), 𝒰_CRPT contains labelled constructs of the finite anchor
levels L1–L8 (plus Lω) used as the self-substrate; it does not contain a tower-limit state.
`Anchor-Fractal` (Lω.6.T1) applies `Twr-Fractal` only to finite iterates
Lift^n(Self_CRPT). Therefore the fractal theorem is an external ω-indexed
statement about all finite scales, not the introduction of an internal ω-state. ∎

### Final Framing

| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Remark** | Lω.6.R1 | `Final-Framing` | | **Novel** |
**Synopsis:** The final framing of the self-application result.

**Source:** CRPT; from `Anchor-Fractal` (Lω.6.T1).

The proved framing is:

```
CRPT is a fractal of projection systems.
The ω-tower is its linear spine.
Lift is the scale operator.
Fibers at one scale become atoms at the next.
Quotients are invariant across scales.
Horizontal and vertical structure exchange roles at every adjacent scale.
The anchor itself, as Self_CRPT, satisfies this same fractal theorem.
```

This is exactly what the proof chain establishes: L8 proves fractality for all
CRPT towers; Lω proves that the anchor is one of those towers under self-application.

## Canonical Notation and References

## Notation Index


---


| Symbol | Name | Section |
|--------|------|---------|
| (𝒰, →_ρ, →_σ, 𝒯) | Substrate | L1.1 |
| NF(x), NF(→_ρ) | Normal form | L1.1 |
| →_ρⁿ, →_ρ* | n-step, reflexive-transitive closure | L1.1 |
| Div(→_ρ) | Diverging elements | L1.1 |
| ≈ | Bisimilarity | L1.1 |
| Abs_M | Level-0 abstraction map (= CFix(ρ_M)) | L2.4 |
| H(x) | Horizon profile (H_S, H_I, H_O, Reg) | L3.3 |
| x^{(k)} | Tower image of x at level k | L8.6 |
| Tower-discernible | Distinction survives some tower level | L8.6 |
| Tower-indiscernible | Distinction survives no tower level | L8.6 |
| PA-WN | Weak Normalisation (Baader & Nipkow L1.2) | L1.2 |
| PA-Conf | Confluence / Church-Rosser (Church & Rosser 1936) | L1.2 |
| WF-Canon | Well-Founded Canonicalization Totality | L1.2 |
| LA-Rich(M) | Model-local existential richness schema (optional) | L1.4 |
| PA-NWF | Non-Well-Founded Divergence (Aczel 1988) | L1.2 |
| PA-CoInd | Co-Induction / Park's Lemma (Park 1981) | L1.2 |
| PA-Prod | Productivity / Guardedness (Milner 1980) | §2.3 |
| PA-Bisim | Bisimulation Congruence (Milner 1980, Park 1981) | §2.4 |
| PA-Reach | Regime Reachability (novel) | L1.3 |
| ρ_M | Projection operator (ARS standard name: reduction strategy, Baader & Nipkow L1.2 Def. 2.1.19) | §3.1 |
| Fix(ρ_M) | Fixpoint set | L2.1 |
| ↓_M | Convergent regime = {x ∈ 𝒰_M \| ∃n : ρ_M^n(x) ∈ Fix(ρ_M)} = μT_conv | L2.2 |
| ∞_M | Persistent regime = {x ∈ 𝒰_M \| ∀n : ρ_M^n(x) ∉ Fix(ρ_M)}; note ∞_M ⊆ Div(→_ρ) but inclusion may be strict | L2.2 |
| d_M(x) | Derivation height / strategy length (CRPT local: abstraction depth) | L2.3 |
| CFix(ρ_M)(x) | Canonical normal-form map | L2.4 |
| NFC_M(f) | Normal-form fiber (CRPT notation: NFC_M(f)) | L2.5 |
| ≃_M | Church-Rosser orbit-equivalence (↔*_ρ) | L2.5 |
| H_S(x) | Structural Horizon = ramification locus of ρ_M | L3.1 |
| H_I(x) | Invariant Horizon = ⊤ iff H_S(x) = ⊤ and ker(ρ_M, ρ_M(x)) is sig_M-uniform (novel — no standard counterpart) | L3.1 |
| H_O(x) | Obstruction Horizon = ⊤ iff d_M(x) = 1 (boundary layer ∂↓_M); avoid in formal statements for H_I — distinct predicates | L3.1 |
| sig_M(x) | Orbit signature = (H_S, H_I, d_M) (novel) | L3.2 |
| Classes A–F | Six-class horizon partition (novel) | L3.2 |
| SC-1 through SC-4 | Stabilisation conditions (orbit definitions, not axioms) | L3.3 |
| CNF∞_M(x) | Canonical Orbit Invariant = ω-limit class | L3.3 |
| Q_M | Abstraction quotient ↓_M/≃_M | L8.2, L8.2 |
| FMA(A) | Free monoidal algebra over set A | L8.1 |
| Lift(M) | Free lift of model M | L8.2 |
| ι_M | Canonical inclusion Q_M ↪ 𝒰_{Lift(M)} | L8.2 |
| Tower(M₀) | Tower generated by M₀ | L8.4 |
| Q_M^* | NWF abstraction quotient | L8.5 |
| Lift^*(M) | NWF-extended free lift | L8.5 |
| 𝒞^Tower_{M₀} | Tower ω-category | L8.7 |
| α_M | Galois abstraction function (= CFix(ρ_M)) | L7.1 |
| γ_M | Galois concretisation (identity on Fix) | L7.1 |
| π_M | Collapse map (= α_M = CFix(ρ_M) on ↓_M) | L7.1 |
| PV | Path valuation = path semiring weight (Eilenberg 1974) | L4.1 |
| H | Horizon classifier | L4.1 |
| D | Regime discriminator (Persistence Observable) | L4.1 |
| 𝒪 = (PV, H, D) | Observer Triple / Orbit Characterisation Triple | L4.1 |
| V = (V,+,·,0,1) | Value semiring | L4.3 |
| w : →_ρ → V | Step weighting function | L4.3 |
| ℋ_finite(x) | Finite reduction histories from x | L4.3 |
| PV(h) | Projection valuation of history h | L4.3 |
| PV_c(x) | Confluent orbit valuation under PA-Conf | L4.3 Cor 13.1 |
| PV∞(h) | Limit path valuation (NWF) | L4.3 |
| DU-1, DU-2, DU-3 | Fixpoint/Induction/PV duality theorems | L4.4 |
| DU-4, DU-5 | Meta-Observations on axiom family symmetry | L4.4 |
| H(x) | Inversion horizon = d_M(x) | L4.5 |
| CIH(x) | Co-inversion horizon = N(x) + CPD(x) | L4.5 |
| CPD(x) | Co-projection depth = minimal period | L4.5 |
| SP-1, SP-2, SP-3 | Self-projection theorems | L4.6 |
| Enc | Admissible encoding (SP-3 condition) | L4.6 |
| CPEP | Coherent Perturbation Existence Property | L4.7 |
| M₁ ∘ M₂, M₁ ∩ M₂, M₁ × M₂ | Model composition, intersection, product | L4.8/L5.1 |
| M₁ ∪ M₂, M₁/~ | Model union, quotient | L4.8/L5.1 |
| 𝟙, 𝟘 | Identity and zero models | L4.8/L5.1 |
| Φ : M₁ → M₂ | Model homomorphism | L5.2 |
| Mod_CRPT | Category of CRPT models; [CK90 L2.1] | L5.2 |
| Φ_ZC, Φ_CH, Φ_ZH | Regime-restricted isomorphisms ZFC↔Cat↔HoTT | L5.2 |
| ⊑ | Model refinement order | L5.3 |
| ⪯ | Model expressiveness preorder | L5.3 |
| OT(x) | Orbit Trace = ([ ρ_M^n(x) ]_≈)_{n∈ℕ} | L6.1 |
| OS(x) | Orbit Spectrum (asymptotic visit frequencies) | L6.1 |
| OC(x) | Orbit Complexity (ordinal rank of OT) | L6.1 |
| H_S*(x), H_I*(x) | NWF co-horizon predicates | L6.2 |
| sig_M*(x) | NWF orbit signature = (H_S*, CPD) | L6.2 |
| Classes A*–F* | NWF six-class partition of ∞_M | L6.2 |
| RTD | Regime-Type Determinacy | L6.5 |
| Type_P, Type_{EP}, Type_{AP} | Orbit-type classification (Periodic / Eventually Periodic / Aperiodic) | L6.1 |
| Tier 1, 2, 3 | Three-tier ∞_M analysis framework | L6.1 |
| Discernible / Indiscernible | Structurally distinguishable (x ≉ y) / collapsed by bisimulation (x ≈ y) | L1.1, Remark L1.1.R4 |

---

---

## Lω.7 — Supplementary Lemmas

*Purpose.* Acyclicity, Finiteness, and Well-Foundedness of the Self-Substrate. This section provides the formal proofs that the dependency relation →_{ρ_CRPT} is acyclic (DAG structure), the self-substrate is finite (|𝒰_CRPT| < ω), and ∞_CRPT = ∅. It also proves the uniqueness of Fix(ρ_CRPT) = {L1.1.D1}.*

---

### Acyclicity of →_{ρ_CRPT}

### Lω.7.L1 — CRPT-Acyclic: The Self-Reduction is Acyclic

| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Lemma** | Lω.7.L1 | `CRPT-Acyclic` | | **Novel** |
**Synopsis:** The dependency relation →_{ρ_CRPT} on 𝒰_CRPT is acyclic: no construct depends on itself directly or indirectly. The proof uses the tower-level stratification: if X ∈ Lk and X →_{ρ_CRPT} Y, then Y ∈ Lj with j < k. A strictly decreasing sequence of natural numbers cannot cycle.

**Source:** CRPT; follows from DAG structure of dependency relation (Lω.1.D1).

*The reduction relation →_{ρ_CRPT} on 𝒰_CRPT is acyclic:*
```
¬∃X ∈ 𝒰_CRPT :  X →_{ρ_CRPT}⁺ X      [no positive-length cycles]
```

**Proof.**

(1) By Lω.1.D1, X →_{ρ_CRPT} Y iff Y is a direct logical dependency of X (Y is required to define or prove X). In the anchor, every construct at level Lk depends only on constructs at levels Lj with j < k:
```
L0 depends on: nothing  (universal framework)
L1–L2 depend on: L0 only
L3–L4 depend on: L1–L2
L5–L7 depend on: L1–L4
L8 depends on: L1–L7
Lω depends on: L0–L8
```

(2) This stratification defines a strict partial order: if X ∈ Lk and Y ∈ Lj with X →_{ρ_CRPT} Y, then j < k (Y is at a strictly lower level than X). In particular, the dependency relation respects the level ordering: level index strictly decreases along every →_{ρ_CRPT} edge.

(3) Suppose a cycle exists: X₀ →_{ρ_CRPT} X₁ →_{ρ_CRPT} ... →_{ρ_CRPT} Xₙ = X₀. Each arrow reduces level index: level(X₀) > level(X₁) > ... > level(Xₙ) = level(X₀). This is a strictly decreasing sequence in ℕ that returns to its starting value — a contradiction.

Therefore →_{ρ_CRPT} is acyclic. ✓  ∎

### Acyclicity Implies Termination

| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Remark** | Lω.7.R4 | `Acyc-Term` | | **Novel** |
**Synopsis:** Acyclicity together with finiteness of 𝒰_CRPT implies every construct reaches Fix(ρ_CRPT) in finitely many steps — a finite acyclic graph has no infinite descending chains.

**Source:** CRPT; from `CRPT-Acyclic` (Lω.7.L1) + `Self-CRPT-Finite` (Lω.7.R1).

Combined with finiteness of 𝒰_CRPT (see Lω.7.R1 below), acyclicity implies that every element of 𝒰_CRPT reaches Fix(ρ_CRPT) in finitely many steps (no infinite descending chains in a finite acyclic graph).

---

### Finiteness of Self_CRPT

### Self-CRPT-Finite: The Self-Application Universe is Finite

| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Remark** | Lω.7.R1 | `Self-CRPT-Finite` | | **Novel** |
**Synopsis:** The self-substrate universe 𝒰_CRPT is finite: it consists of all labeled constructs in L1–L8 and Lω, and each level Lk contains finitely many labeled items (definitions, theorems, lemmas, corollaries, remarks). The union over finitely many levels of finite sets is finite. This finiteness, combined with acyclicity, gives ∞_{CRPT} = ∅ without requiring any sophisticated argument.


The self-substrate 𝒰_CRPT consists of all labeled constructs of the anchor at levels L1–L8 plus Lω. The total number of labeled constructs is finite:
```
|𝒰_CRPT|  <  ω
```
This is immediate: each level Lk contains finitely many definitions, theorems, lemmas, corollaries, and remarks (each with a unique label of the form §k.n.Xm). The union over the finitely many levels L1–L8, Lω is therefore finite.

**Consequences:**

**(a) Bisimulation triviality:** In a finite pure-WF model, bisimilarity coincides with equality on fixpoints. Since ∞_{CRPT} = ∅ (proved in Lω.1.T1 clause 5), every orbit is finite and bisimilarity is determined entirely by the fixpoint reached. Therefore:
```
X ≈_CRPT Y  ⟺  CFix(ρ_CRPT)(X) = CFix(ρ_CRPT)(Y)
```
Two anchor constructs are bisimilar iff they reduce to the same primitive dependency root. In particular, L1.1.D1 ≈_CRPT L1.1.D1 and no non-substrate element is bisimilar to L1.1.D1 (since L1.1.D1 is the unique element of Fix(ρ_CRPT), all other elements reduce to it in finitely many steps and are bisimilar to each other iff they share the same immediate ancestor chain).

**(b) Well-foundedness:** A finite acyclic directed graph under any relation is well-founded (no infinite descending chain). Together with `CRPT-Acyclic` (Lω.7.L1), this confirms PA-WN on 𝒰_CRPT without requiring the abstract PA-WN axiom: the finite-acyclic structure is a direct proof.

---

### Pure Well-Foundedness of the Self-Application

### Lω.7.T1 — CRPT-WF: The Self-Application is Pure Well-Founded

| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | Lω.7.T1 | `CRPT-WF` | | **Novel** |
**Synopsis:** When CRPT is applied to itself, the self-substrate 𝒰_CRPT is pure well-founded: ∞_{CRPT} = ∅. Every construct in the tower (every definition, theorem, lemma) eventually depends on L1.1.D1 (the substrate definition) in finitely many dependency steps, and L1.1.D1 depends on nothing. The theory has no circular dependencies — it is acyclic and terminates.

**Source:** CRPT; makes explicit the regime result asserted in `Self-Model` (Lω.1.T1) clause (5).


*When CRPT is instantiated on itself:*
```
∞_{CRPT}  =  ∅
```
*Every anchor construct converges to Fix(ρ_CRPT) = {L1.1.D1} in finitely many ρ_CRPT-steps.*

**Proof.**

(1) By `Self-CRPT-Finite` (Lω.7.R1): 𝒰_CRPT is finite.

(2) By `CRPT-Acyclic` (Lω.7.L1): →_{ρ_CRPT} is acyclic.

(3) In any finite, acyclic directed graph, every node has a path of bounded length to a sink (a node with no outgoing edges). Proof by induction on graph size: base case (single node) is a sink; inductive step: any node either is a sink or has an outgoing edge to a strictly smaller sub-graph (by acyclicity), so by induction hypothesis that sub-graph has paths to sinks.

(4) The sinks of →_{ρ_CRPT} are exactly Fix(ρ_CRPT) = {L1.1.D1} (L1.1.D1 has no outgoing edges since it depends on nothing). Every other element X ∈ 𝒰_CRPT has at least one outgoing →_{ρ_CRPT} edge and by (3) eventually reaches L1.1.D1.

(5) Therefore: ∀X ∈ 𝒰_CRPT, ∃n ∈ ℕ : ρ_CRPT^n(X) = L1.1.D1 ∈ Fix(ρ_CRPT). This means X ∈ ↓_CRPT.

(6) Since every element is in ↓_CRPT: ↓_CRPT = 𝒰_CRPT, so ∞_CRPT = 𝒰_CRPT \ ↓_CRPT = ∅. ✓  ∎

### Regime-Partition Extraction

| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Remark** | Lω.7.R2 | `RegPart-Extract` | | **Novel** |
**Synopsis:** See the remark.

**Source:** CRPT; from `CRPT-WF` (Lω.7.T1).

This theorem is a formal extraction of the claim in Lω.1.T1(5) ("Regime partition: ↓_{CRPT} = 𝒰_CRPT … ∞_CRPT = ∅") with an explicit proof that uses only finiteness and acyclicity — neither requiring the full CRPT axiom apparatus nor circular self-reference.

---

### Uniqueness Supplement for the Fixed Point

### Lω.7.T2 — Lω-FixedPt-Unique: L1.1.D1 is the Unique Projective Fixed Point

| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | Lω.7.T2 | `Lω-FixedPt-Unique` | | **Novel** |
**Synopsis:** L1.1.D1 is the unique projective fixed point: Fix(ρ_CRPT) = {L1.1.D1}. Every other construct depends on at least one prior construct.

**Source:** CRPT; complements `Self-FP` (Lω.5.T1) with an explicit uniqueness argument in terms of Fix(ρ_CRPT).

*In the self-application M_CRPT:*

*(a) Fix(ρ_CRPT) = {L1.1.D1} — the substrate definition is the unique element fixed by ρ_CRPT.*

*(b) No other construct Y ≠ L1.1.D1 satisfies ρ_CRPT(Y) = Y.*

*(c) L1.1.D1 is Class E (fixpoint, H_S = ⊤) — the unique sink of the dependency DAG.*

**Proof.**

**(a)** ρ_CRPT(X) = X iff X has no outgoing edges in →_{ρ_CRPT} (X has no logical dependencies — it depends on nothing). In the anchor, the only construct that depends on nothing is the substrate definition L1.1.D1: it introduces the substrate (𝒰, →_ρ, →_σ, 𝒯) from scratch, without assuming any prior definition. Every other construct in the anchor depends on at least one prior definition or axiom. Therefore Fix(ρ_CRPT) = {L1.1.D1}. ✓

**(b)** This is the contrapositive of (a): any Y ≠ L1.1.D1 has at least one dependency, so ρ_CRPT(Y) ≠ Y. ✓

**(c)** L1.1.D1 ∈ Fix(ρ_CRPT) = {L1.1.D1} so it is a fixpoint (depth 0). For Class E classification: H_S(L1.1.D1) = ⊤ requires |ρ_CRPT^{-1}(ρ_CRPT(L1.1.D1)) \ {L1.1.D1}| ≥ 1, i.e., there exist constructs other than L1.1.D1 that also reduce to L1.1.D1 (since all elements eventually reduce to L1.1.D1 in one or more steps, and ρ_CRPT selects the immediate predecessor, many constructs have ρ_CRPT(X) eventually equaling L1.1.D1). This is established in `Self-Horiz` (Lω.2.T1): L1.1.D1 is classified as Class E there. ✓  ∎

### Scope of the Uniqueness Claim

| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Remark** | Lω.7.R3 | `FixUniq-Scope` | | **Novel** |
**Synopsis:** The uniqueness claim is specifically for projective fixed points.

**Source:** CRPT; from `Lω-FixedPt-Unique` (Lω.7.T2) + `Self-FP` (Lω.5.T1).

The uniqueness claimed here is specifically for projective fixed points (elements fixed by ρ_CRPT itself). The stronger self-consistency fixed point of `Self-FP` (Lω.5.T1) — uniqueness of the level structure as a fixed point of the meta-HOA operation — is proved there and is a separate (stronger) claim. `Lω-FixedPt-Unique` provides the simpler building block that Fix(ρ_CRPT) is a singleton.

---

## References

[1] F. Baader and T. Nipkow. *Term Rewriting and All That*. Cambridge University Press, 1998.

[2] A. Church and J. B. Rosser. "Some Properties of Conversion." *Transactions of the American Mathematical Society* 39(3):472–482, 1936.

[3] R. De Nicola and M. Hennessy. "Testing Equivalences for Processes." *Theoretical Computer Science* 34(1-2):83–133, 1984.

[4] S. Eilenberg. *Automata, Languages, and Machines*, Vol. A. Academic Press, 1974.

[5] R. Hartshorne. *Algebraic Geometry*. Graduate Texts in Mathematics 52. Springer, 1977.

[6] L. Henkin. "The Completeness of the First-Order Functional Calculus." *Journal of Symbolic Logic* 14(3):159–166, 1949.

[7] A. Katok and B. Hasselblatt. *Introduction to the Modern Theory of Dynamical Systems*. Cambridge University Press, 1995.

[8] R. Milner. *A Calculus of Communicating Systems*. Lecture Notes in Computer Science 92. Springer, 1980.

[9] M. Park. "Concurrency and Automata on Infinite Sequences." In *Theoretical Computer Science*, Lecture Notes in Computer Science 104, pp. 167–183. Springer, 1981.

[10] Terese. *Term Rewriting Systems*. Cambridge Tracts in Theoretical Computer Science 55. Cambridge University Press, 2003.

[11] P. Aczel. *Non-Well-Founded Sets*. CSLI Lecture Notes 14. Stanford, 1988.

[12] J. J. M. M. Rutten. "Universal Coalgebra: A Theory of Systems." *Theoretical Computer Science* 249(1):3–80, 2000.

[13] B. Jacobs. *Introduction to Coalgebra: Towards Mathematics of States and Observation*. Cambridge University Press, 2017.

[14] M. Droste, W. Kuich, and H. Vogler (eds.). *Handbook of Weighted Automata*. Springer, 2009.

[15] J. W. de Bakker and E. P. de Vink. *Control Flow Semantics*. MIT Press, 1996.

[16] K. Weihrauch. *Computable Analysis*. Springer, 2000.

[17] A. Kechris. *Classical Descriptive Set Theory*. Springer, 1995.


---

*End of CRPT Abstract Anchor — ω-Tower.*
*Levels L0 through Lω. Every construct appears once in its dependency-correct canonical level.*
*The structure is the theory's own self-classification and fractal theorem, realized.*
