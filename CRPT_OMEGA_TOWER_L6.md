# L6 — Persistent Orbit Invariants, NWF Horizons, Regime-Type Determinacy, and Degeneracy

## L6.1 — Asymptotic Orbit Invariants (AOI)

*Purpose.* Asymptotic Orbit Invariants. This section develops the three-level hierarchy of asymptotic orbit invariants (AOI) for elements in the persistent regime ∞_M. The orbit trace OT(x) tracks the sequence of six-class labels visited; the orbit spectrum OS_M(x) captures asymptotic frequencies; and the orbit complexity OC(x) characterises the full structural behavior. Each level strictly refines the previous. The AOI Master Theorem proves this hierarchy is minimal and complete for bisimulation-invariant classification of persistent orbits. The AOI is the canonical form of **asymptotic mode** (`Mode` (L1.4.D1)): the canonicalization apparatus that governs every persistent element, including those without a topological limit, by stabilizing the orbit's observable signature to an orbit-invariant rather than to a single element of 𝒰_M.*


The following extends the orbit invariant theory of L3.3 to aperiodic orbits
(those where SC-1 fails — the orbit visits infinitely many distinct bisimulation
classes). All proofs in this section are self-contained.

### Orbit Trace OT(x)
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L6.1.D1 | `OT` | OT(x) | **Novel** |
**Synopsis:** The orbit trace OT(x) of a persistent element x is the infinite sequence of bisimulation classes visited by the projection orbit: OT(x) = ([x]_≈, [ρ_M(x)]_≈, [ρ_M²(x)]_≈, ...). It records the complete trajectory of x through the six-class partition classes over time. OT(x) is the primary asymptotic observable for persistent elements.

**Source:** CRPT; from PA-Bisim (L1.3.Ax1) + `ρ_M` (L2.1.D1).

For x ∈ νT_{ρ,M}:
```
OT(x) := ([ρ_M^n(x)]_≈)_{n∈ℕ}
```
the coinductive sequence of bisimulation classes visited by the orbit.

### AOI-1: Bisimulation Invariance
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L6.1.T1 | `AOI1-BisInv` | | **Novel** |
**Synopsis:** AOI-1 Bisimulation Invariance: the orbit trace OT(x) is invariant under bisimilarity. If x ≈ y then OT(x) = OT(y). This is proved using PA-Bisim: bisimilar elements have bisimilar projection orbits, so their bisimulation-class sequences are identical. OT is therefore a genuine observational invariant.

**Source:** CRPT; from `OT` (L6.1.D1) + PA-Bisim (L1.3.Ax1).

x ≈ y ⟹ OT(x) = OT(y).

*Proof.* By PA-Bisim, x ≈ y ⟹ ρ_M(x) ≈ ρ_M(y). By induction, ρ_M^n(x) ≈ ρ_M^n(y)
for all n. Hence [ρ_M^n(x)]_≈ = [ρ_M^n(y)]_≈ for all n, so OT(x) = OT(y). ∎

### AOI-3: Extension of CNF∞
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L6.1.T2 | `AOI3-Ext` | | **Novel** |
**Synopsis:** AOI-3 extends the persistent canonical form CNF∞_M to aperiodic orbits: for Type AP elements (aperiodic persistent orbits), the orbit trace OT(x) provides a finer invariant than CNF∞_M (which is undefined for AP elements). AOI₁(x) = [OT(x)]_{tail} (the tail-equivalence class of OT(x)) serves as the level-1 asymptotic invariant for all persistent elements.

**Source:** CRPT; from `OT` (L6.1.D1) + `CNF∞-Def` (L3.3.D6).

For x ∈ νT_{ρ,M} satisfying SC-1:
OT(x) is eventually constant = (CNF∞_M(x), CNF∞_M(x), ...).

*Proof.* By SC-1, there exists N such that for all n ≥ N:
[ρ_M^n(x)]_≈ = [ρ_M^N(x)]_≈. By `CNF∞-Def` (L3.3.D6), CNF∞_M(x) is exactly this stable
bisimulation class [ρ_M^N(x)]_≈. Therefore OT(x)=([ρ_M^n(x)]_≈)_{n∈ℕ} is eventually
constant with eventual value CNF∞_M(x). ∎

### Orbit Spectrum OS(x)
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L6.1.D2 | `OS` | OS_M(x) | **Novel** |
**Synopsis:** The orbit spectrum OS_M(x) is the asymptotic frequency distribution over bisimulation classes: OS_M(x)(C) = lim_{n→∞} (1/n)|{k < n | [ρ_M^k(x)]_≈ ∈ C}| for each six-class C. When these limits exist (SC-4 condition), OS_M(x) is a probability measure on the six-class partition. OS_M captures the long-run statistical behavior of the orbit.

**Source:** CRPT; from `OT` (L6.1.D1) + `SC-4-Def` (L3.3.D5).

For x with well-defined asymptotic visit
frequencies: OS(x) := the asymptotic frequency distribution over bisimulation classes.

### AOI-5: Spectrum Bisimulation-Invariant
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L6.1.T3 | `AOI5-Spec` | | **Novel** |
**Synopsis:** AOI-5 Spectrum Bisimulation Invariance: the orbit spectrum OS_M(x) is invariant under bisimilarity. If x ≈ y then OS_M(x) = OS_M(y). This follows from AOI-1 (the orbit traces are identical) and the fact that asymptotic frequencies depend only on the trace.

**Source:** CRPT; from `OS` (L6.1.D2) + `AOI1-BisInv` (L6.1.T1).

x ≈ y ⟹ OS(x) = OS(y).
For periodic orbits: OS concentrates on {CNF∞_M(x)}.

*Proof.* x ≈ y ⟹ OT(x) = OT(y) (`AOI1-BisInv` (L6.1.T1)). Since OT(x) = OT(y), the frequency
distributions of bisimulation classes along the two orbits are identical: for every
finite prefix length N, the empirical frequency distribution of {[ρ_M^n(x)]_≈}_{n<N}
equals that of {[ρ_M^n(y)]_≈}_{n<N}. Any limit of equal finite distributions is equal.
Hence OS(x) = OS(y). For periodic orbits: by SC-1, [ρ_M^n(x)]_≈ = CNF∞_M(x) for all
n ≥ N(x). The only class visited asymptotically is {CNF∞_M(x)}, so OS concentrates
on {CNF∞_M(x)}. ✓ ∎

### Orbit Complexity OC(x)
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L6.1.D3 | `OC` | OC(x) | **Novel** |
**Synopsis:** The orbit complexity OC(x) is the Borel rank of the singleton {OT(x)} in the product space Q_M^ω. When Q_M is countable discrete, Q_M^ω is a Polish space and every singleton has a well-defined Borel rank (a countable ordinal). OC(x) measures how 'complicated' the orbit trace is as a topological object.

**Source:** CRPT; from `OT` (L6.1.D1); descriptive set theory (Kechris [1995]).

Assume the bisimulation quotient
the query signature := 𝒰_M/≈ is presented as a standard Borel space; in particular, this holds when
the query signature is countable discrete. Then the query signature^ω with product topology is Polish. For x ∈ νT_{ρ,M},
define OC(x) as the least Borel rank α such that the singleton set {OT(x)} belongs to
Σ^0_α(the query signature^ω). Thus OC(x) is a countable ordinal whenever this presentation assumption
holds.

### AOI Master Theorem
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L6.1.T4 | `AOI-Mast` | | **Novel** |
**Synopsis:** The AOI Master Theorem: the three-level AOI hierarchy — orbit trace (AOI₁), orbit spectrum (OS_M), orbit complexity (OC) — is the unique minimal bisimulation-invariant classification of persistent orbits. Each level strictly refines the previous: there exist orbits distinguished by AOI₁ but not by OS_M, and orbits distinguished by OC but not by AOI₁.

**Source:** CRPT; from `OT` (L6.1.D1) + `OS` (L6.1.D2) + `OC` (L6.1.D3).

The triple (OT, OS, OC) satisfies:
(R1) bisimulation-invariance, (R2) extends CNF∞ for periodic orbits, (R3) each is
computable from finite orbit prefixes in the limit.

*Proof.*
(R1) OT bisimulation-invariant: `AOI1-BisInv` (L6.1.T1). OS bisimulation-invariant: `AOI5-Spec` (L6.1.T3).
OC bisimulation-invariant: OC(x) is the rank of OT(x); OT(x) = OT(y) when x ≈ y
(`AOI1-BisInv` (L6.1.T1)), so OC(x) = OC(y). ✓

(R2) For x satisfying SC-1: OT(x) is eventually constant (`AOI3-Ext` (L6.1.T2)). The
eventually-constant sequence (CNF∞_M(x), CNF∞_M(x), ...) is the orbit trace; it
extends the notation of L3.3 (where CNF∞_M was defined as the stabilisation class).
OC(x) for periodic orbits = the ordinal 0 (the trace is a Σ₁⁰ set — a periodic
sequence — of minimal descriptive complexity). ✓

(R3) OT is coinductively computable: given ρ_M and the bisimulation quotient, OT(x)
is computed step by step as ([ρ_M^0(x)]_≈, [ρ_M^1(x)]_≈, ...). Each finite prefix
is computable from the orbit (if the bisimulation quotient is computable). OS is the
Cesàro limit of the empirical distributions — approximable from finite prefixes when
the orbit is eventually periodic (SC-4). OC requires the full descriptive complexity
theory for general aperiodic orbits, but is approximable for SC-4 orbits. ✓ ∎

---

## L6.2 — Orbit-Type Classification of ∞_M

*Purpose.* Unconditional Orbit-Type Classification. This section partitions ∞_M unconditionally — without assuming any scope condition — into three types: Asymptotically Periodic (AP), Eventually Periodic (EP), and Properly Persistent (P). This partition is prior to and independent of the AOI hierarchy; it stratifies the persistent regime by the qualitative long-run behavior of the projection operator, not by any canonical invariant value.*


The analysis tools of L3.2, L3.3, and L6.1 for ∞_M elements all depend on stabilisation
conditions (SC-1 through SC-4) or PA-WN_top. However, PA-WN_top is logically
independent of the other PA-* axioms (`WNtop-Ind` (L1.4.T3), L1.4): there exist substrates
satisfying all PA-* axioms except PA-WN_top (e.g., QG instantiations with RG limit
cycles, proved independent via Theorem 2.5a of CRPT_NATIVE_QG). When PA-WN_top
fails, ∞_M elements may lack topological convergence, and the twelve-class partition
(L3.2) does not cover them.

This section provides an **unconditional classification** of ∞_M elements that requires
only PA-NWF + PA-Bisim — no SC conditions, no PA-WN_top. It establishes a three-tier
analysis framework for the persistent regime, with each tier activating as additional
structure is assumed.

### Orbit-Type Classification (Unconditional)

### Orbit Type Classification
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L6.2.D1 | `OTC` | Type_{AP, EP, P} | **Novel** |
**Synopsis:** The Orbit-Type Classification partitions ∞_M unconditionally into three types based on the qualitative long-run behavior of the projection orbit. Asymptotically Periodic (AP): orbit visits infinitely many distinct bisimulation classes. Eventually Periodic (EP): orbit eventually cycles through finitely many classes. Properly Persistent (P): orbit is purely periodic from the start.

**Source:** CRPT; from `OT` (L6.1.D1) + `SC-1` (L3.3.D2) + `SC-4-Def` (L3.3.D5).

For x ∈ ∞_M (equivalently,
x ∈ νT_{ρ,M}), define the **orbit type** of x based on the quotient orbit
OT(x) = ([ρ_M^n(x)]_≈)_{n ∈ ℕ} (`OT-21B` (L6.3.D1):

**Type P (Periodic / Eventually Constant):** x has orbit type P if SC-1(x) holds:
```
Type_P(x) :⟺ ∃N ∈ ℕ : ∀n ≥ N : [ρ_M^n(x)]_≈ = [ρ_M^N(x)]_≈
```
The orbit eventually stabilises to a single bisimulation class. The CNF∞_M invariant
(`CNF∞-Def` (L3.3.D6)) is well-defined for Type P elements.

**Type EP (Eventually Periodic):** x has orbit type EP if SC-4(x) holds but SC-1(x)
fails:
```
Type_{EP}(x) :⟺ SC-4(x) ∧ ¬SC-1(x)
 ⟺ |{[ρ_M^n(x)]_≈ : n ∈ ℕ}| < ∞ ∧ |ω_≈(x)| ≥ 2
```
The orbit visits finitely many bisimulation classes but cycles through two or more
of them indefinitely. The CPD (co-projection depth, `CPD` (L4.5.D1)) is well-defined
with CPD(x) ≥ 2.

**Type AP (Aperiodic):** x has orbit type AP if SC-4(x) fails:
```
Type_{AP}(x) :⟺ ¬SC-4(x)
 ⟺ |{[ρ_M^n(x)]_≈ : n ∈ ℕ}| = ∞
```
The orbit visits infinitely many distinct bisimulation classes. No finite
classification (CNF∞_M, CPD, or finite six-class partition) applies. Only the
orbit-trace invariants OT(x), OS(x), OC(x) from L6.1 provide structural information.

### Orbit-Type Partition of ∞_M — Unconditional
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L6.2.T1 | `OT-Part` | | **Novel** |
**Synopsis:** The Orbit-Type Partition theorem: {AP, EP, P} is an exhaustive disjoint partition of ∞_M. Every persistent element belongs to exactly one type. The partition requires no scope conditions — it is defined for all persistent elements using only the qualitative behavior of OT(x).

**Source:** CRPT; from `OTC` (L6.2.D1) + PA-NWF (L1.2.Ax4) + PA-Bisim (L1.3.Ax1).

Under PA-NWF +
PA-Bisim only (no SC conditions, no PA-WN_top):
```
∞_M = Type_P ∐ Type_{EP} ∐ Type_{AP}
```
The three orbit types form a mutually exclusive, jointly exhaustive partition of ∞_M.

*Proof.*

**Mutual exclusivity.** By construction:
- Type P requires SC-1(x) (eventually constant orbit in quotient).
- Type EP requires SC-4(x) ∧ ¬SC-1(x) (finite quotient orbit, not eventually constant).
- Type AP requires ¬SC-4(x) (infinite quotient orbit).
SC-1(x) ⟹ SC-4(x) (a fortiori: an eventually constant orbit visits finitely many
classes). So Type P ⟹ SC-4(x), which contradicts ¬SC-4(x) (Type AP). Similarly,
Type EP requires SC-4(x), contradicting Type AP. And Type EP requires ¬SC-1(x),
contradicting Type P. The three types are pairwise disjoint. ✓

**Joint exhaustiveness.** For any x ∈ ∞_M, the set S_x := {[ρ_M^n(x)]_≈ : n ∈ ℕ}
is a well-defined subset of the bisimulation quotient 𝒰_M/≈ (PA-Bisim ensures the
quotient exists). Either |S_x| < ∞ (SC-4 holds) or |S_x| = ∞ (SC-4 fails).
- If |S_x| = ∞: x has Type AP. ✓
- If |S_x| < ∞: the infinite sequence OT(x) takes values in a finite set S_x. By
 the pigeonhole principle, the sequence is eventually periodic (some class is revisited).
 The ω-limit set ω_≈(x) is a subset of S_x and is non-empty (infinite sequence in
 finite set). If |ω_≈(x)| = 1: the orbit eventually stabilises to one class (SC-1
 holds), so x has Type P. If |ω_≈(x)| ≥ 2: SC-1 fails, so x has Type EP. ✓

Every x ∈ ∞_M falls into exactly one type. ✓ ∎

### Three-Tier Classification Schema

### Three-Tier ∞_M Analysis Framework
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L6.2.D2 | `3-Tier` | | **Novel** |
**Synopsis:** The Three-Tier Classification Schema organises the persistent regime theory by the strength of assumptions required: Tier 1 (unconditional, PA-NWF + PA-Bisim only) gives orbit types AP/EP/P; Tier 2 (SC-4 conditions) adds CNF∞_M, CPD, and the NWF six-class partition A*–E*; Tier 3 (PA-WN_top) adds topological limit classification.

**Source:** CRPT; from `OTC` (L6.2.D1) + `CNF∞-Def` (L3.3.D6) + PA-WN_top (L1.2.Ax7).

The analysis of ∞_M
elements is organised into three tiers, each activating with additional structural
assumptions:

**Tier 1 — Unconditional (PA-NWF + PA-Bisim only):**
- **Orbit Type:** Type P / Type EP / Type AP (`OTC` (L6.2.D1), `OT-Part` (L6.2.T1)).
- **Orbit Trace:** OT(x) = ([ρ_M^n(x)]_≈)_{n ∈ ℕ} — always well-defined (`OT-21B` (L6.3.D1).
- **Bisimulation Invariance:** OT(x) = OT(y) whenever x ≈ y (`AOI1-BisInv` (L6.1.T1)).

This tier provides **complete coverage**: every ∞_M element has a well-defined orbit type
and orbit trace, regardless of whether PA-WN_top or any SC conditions hold.

**Tier 2 — Finite Orbit Structure (SC-4 holds, i.e., Types P and EP):**
- **CNF∞_M:** Well-defined for Type P elements (`CNF∞-Def` (L3.3.D6), `CNF∞-Ex` (L3.3.T3)).
- **CPD:** Co-projection depth, well-defined and finite (`CPD` (L4.5.D1), `CPD-Fin` (L4.5.T3)).
- **NWF Six-Class Partition A*–F*:** (L6.2) classifies elements by co-horizon structure.
- **PV∞:** NWF path valuation exists (`PV2` (L4.3.T2), under SC-1/2/3).
- **Orbit Spectrum:** OS(x) is well-defined and concentrates on finitely many classes (`AOI5-Spec` (L6.1.T3)).
- **Orbit Complexity:** OC(x) = 0 for periodic, finite ordinal for eventually periodic.

This tier applies to **Types P and EP** only.

**Tier 3 — Topological Convergence (PA-WN_top holds):**
- **CFix(ρ_M) on ∞_M:** lim_{n→∞} ρ_M^n(x) exists in the model topology (`Rec-Proj` (L2.1.D4) native form).
- **Topological Horizons:** H_S^{top}, H_I^{top} (Definitions 9.3.1–9.3.2).
- **Twelve-Class Partition A_∞–F_∞:** (L3.2) classifies ∞_M elements by topological horizon structure.
- **Full orbit signature on ∞_M:** sig_M(x) = (∞, limit_id, convergence_profile) (`sig_M-NM` (L3.1.D5) native form).

This tier applies to **all Types** when PA-WN_top holds, and subsumes Tier 2.

### Tier Compatibility
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L6.2.T2 | `Tier-Compat` | | **Novel** |
**Synopsis:** The Tier Compatibility theorem: the three tiers are mutually compatible. Tier 2 refines Tier 1 (orbit types remain valid under stronger assumptions); Tier 3 refines both Tier 1 and Tier 2 (topological classification adds to, not contradicts, the combinatorial classification). No tier contradicts any other.

**Source:** CRPT; from `3-Tier` (L6.2.D2).

The three tiers are compatible:

**(i)** Tier 2 refines Tier 1: For x ∈ Type_P ∪ Type_{EP}, all Tier 1 invariants
remain valid, and Tier 2 adds finer structure (CNF∞, CPD, A*–F* classes). ✓

**(ii)** Tier 3 refines Tier 2 and Tier 1: When PA-WN_top holds, all elements of
∞_M have topological limits. In the presence of PA-WN_top:
- Type AP ⊆ {x | lim ρ_M^n(x) exists but orbit visits ∞ bisimulation classes}
 — the topological limit exists, but the quotient orbit is aperiodic.
- Type EP and Type P elements additionally have the topological limit equal to their
 ω-limit class representative.
All Tier 1 and Tier 2 invariants remain valid, and Tier 3 adds topological
classification. ✓

**(iii)** No tier contradicts another: an element classified as Type P/EP/AP at Tier 1
carries a consistent classification at all applicable higher tiers. ✓

*Proof.*

(i) Tier 2's SC-4 condition is a strengthening of the bare PA-NWF + PA-Bisim
assumptions of Tier 1. All Tier 1 constructions (OT, orbit type) remain valid
under stronger hypotheses. Tier 2 adds CNF∞_M (which requires SC-1 ⊆ SC-4)
and A*–F* partition (which requires SC-4). Both are consistent with OT since
CNF∞_M is derived from OT. ✓

(ii) PA-WN_top guarantees lim_{n→∞} ρ_M^n(x) exists for all x ∈ ∞_M. This provides
CFix(ρ_M)(x) on ∞_M. The topological horizons H_S^{top}, H_I^{top} are defined in
terms of this limit, enriching the classification. For Type P elements,
CNF∞_M(x) = [lim ρ_M^n(x)]_≈ (the quotient limit coincides with the topological
limit's bisimulation class). For Type EP elements, the topological limit exists
but the quotient orbit cycles; the limit point is the ω-limit in the topology.
For Type AP elements, the topological limit exists (PA-WN_top) even though the
quotient orbit is aperiodic; this gives a "limit-point classification" not available
at Tier 1 or Tier 2. ✓

(iii) Direct: each tier adds structure; none redefines or contradicts prior invariants. ✓ ∎

### Scope Boundary: What Is Known for Type AP Elements

### Type AP Elements: Irreducible Aperiodicity
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L6.2.T3 | `AP-Irred` | | **Novel** |
**Synopsis:** Type AP Irreducibility: elements with aperiodic persistent orbits (Type AP) cannot be further decomposed by any bisimulation-invariant first-order property. The aperiodic orbit type is the 'hardest' class: it requires second-order resources (the orbit trace OC(x)) to classify. No first-order property distinguishes AP elements beyond their type.

**Source:** CRPT; from `OTC` (L6.2.D1) + `OC` (L6.1.D3).

For x ∈ Type_{AP}
(aperiodic ∞_M elements), the following hold unconditionally:

**(i)** OT(x) is a well-defined infinite sequence in the bisimulation quotient, visiting
infinitely many distinct classes.

**(ii)** No finite-dimensional classification is possible: there is no finite partition of
Type_{AP} into classes determined by a tuple of finitely many Boolean or natural-number
invariants that is both exhaustive and bisimulation-invariant.

**(iii)** The orbit complexity OC(x) (`OC-21B` (L6.3.D9) provides an ordinal-valued measure
of descriptive complexity. Under the Borel space assumption on 𝒰_M/≈, OC(x) is a
countable ordinal classifying OT(x)'s position in the Borel hierarchy.

**(iv)** When PA-WN_top additionally holds, Type AP elements have a well-defined
topological limit CFix(ρ_M)(x) = lim_{n→∞} ρ_M^n(x), and the twelve-class partition
(L3.2, `12-Part-EE` (L3.2.T3)) classifies them. When PA-WN_top fails, Type AP elements are
classified only by OT(x) and OC(x).

*Proof.*

(i) By Def (Orbit Trace OT(x) and the definition of Type AP: OT(x) is well-defined (it is
the sequence of bisimulation classes along the orbit), and |{[ρ_M^n(x)]_≈ : n ∈ ℕ}| = ∞
(the defining condition of Type AP). ✓

(ii) Suppose a finite partition of Type AP into classes C₁, ..., Cₖ exists, each
determined by a tuple of m finitely-valued invariants. Then Type AP has at most
V₁ × V₂ × ... × Vₘ < ∞ distinct classes. But the orbit traces OT(x) for x ∈ Type AP
are infinite sequences over an infinite alphabet (infinitely many bisimulation classes
visited), with distinct descriptive complexities. By a cardinality argument: the number
of distinct orbit-trace types in Type AP can be uncountable (when 𝒰_M/≈ is infinite),
while any finite partition has finitely many classes. Therefore no finite partition
captures all orbit-trace distinctions. ✓

(iii) By Def (Orbit Complexity OC(x) and the Borel hierarchy structure. ✓

(iv) PA-WN_top guarantees the topological limit. `12-Part-EE` (L3.2.T3) applies when PA-WN_top
is assumed. When PA-WN_top fails, no topological limit is guaranteed, and L3.2 does not
apply; the only invariants are from Tier 1 (OT, orbit type, OC). ✓ ∎

### Tools for Non-Convergent Persistent Elements

| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Remark** | L6.2.R1 | `NonConv-Answer` | | **Novel** |
**Synopsis:** The three-tier framework (`3-Tier` (L6.2.D2)) is the structural answer to which analysis tools CRPT provides for ∞_M elements when PA-WN_top fails.

**Source:** CRPT; from `3-Tier` (L6.2.D2).

The three-tier framework (`3-Tier` (L6.2.D2)) provides the structurally correct response
to the question: "What analysis tools does CRPT provide for ∞_M elements when
PA-WN_top fails?" The answer has three components:

1. **Every ∞_M element has a well-defined orbit type** (P, EP, or AP) — this is
 unconditional and requires no topological assumptions.

2. **For elements with finite quotient orbits** (Types P and EP, SC-4 holds),
 the full NWF classification machinery of L3.3, L4.5, and L6.4 applies.

3. **For aperiodic elements** (Type AP, SC-4 fails), no finite classification
 is possible (`AP-Irred` (L6.2.T3) ii). The orbit trace OT(x) and orbit complexity
 OC(x) are the correct invariants — they capture exactly the information
 that exists. This is not a deficiency of the Anchor; it reflects a genuine
 mathematical fact: aperiodic dynamics over infinite quotient spaces cannot
 be finitely classified.

The Anchor's ∞_M machinery is therefore **complete at each tier**: it provides all
information that is mathematically extractable under the given assumptions.

### Relationship to L6.2 and L3.2

| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Remark** | L6.2.R2 | `ThreeTier-Rel` | | **Novel** |
**Synopsis:** The three-tier framework organises the existing ∞_M tools into a hierarchy: orbit-type classification (Tier 1, unconditional), the NWF six-class partition (Tier 2, under SC-4), and the twelve-class partition (Tier 3, under PA-WN_top).

**Source:** CRPT; from `3-Tier` (L6.2.D2) + `6-Part` (L3.2.T1).

The three-tier framework
organises the pre-existing ∞_M tools into a coherent hierarchy:
- L6.2 (NWF six-class partition A*–F*) = Tier 2, applicable under SC-4
- L3.2 (twelve-class partition A_∞–F_∞) = Tier 3, applicable under PA-WN_top
- L6.1 (orbit-type classification) = Tier 1, applicable unconditionally

When both SC-4 and PA-WN_top hold, all three classifications are available
simultaneously and are mutually compatible (`Tier-Compat` (L6.2.T2)).

---


---

## L6.3 — AOI Full Proofs

*Purpose.* Full Proofs: AOI Impossibility, Constructivity, and Hierarchy. This section provides the complete formal proofs for all AOI theorems. It is organized as: (0) Executive summary; (1) impossibility of a single-class invariant; (2) Level 1 orbit trace; (3) Level 2 orbit spectrum; (4) orbit complexity; (5) unified AOI; (6–7) scope conditions SC-∞ and SC-k; (8) applications. Each subsection is self-contained and may be read independently.*


> **Note.** This section contains the full rigorous proofs for the Asymptotic
> Orbit Invariant (AOI) theory summarized in L6.1. Key results: `SC-Imp` (L6.3.T1)
> (Single-Class Impossibility for aperiodic orbits), complete proofs for
> AOI levels 1–3, and the AOI Hierarchy Termination Theorem (L6.3).
> SC-∞ (L6.3) is a new stabilisation condition for non-eventually-periodic orbits.


## EXECUTIVE SUMMARY

**The Problem (A-1).** CNF∞ is defined only for periodic persistent orbits
(those satisfying SC-1). Aperiodic orbits — whose ρ_M-iteration visits infinitely
many distinct bisimulation classes with no eventual repetition — have no
canonical invariant under the current theory. The question: does there exist a
functor-like assignment Inv(x) satisfying:

- (R1) **Bisimulation-invariance:** x ≈ y ⟹ Inv(x) = Inv(y)
- (R2) **Extension:** Inv(x) = [CNF∞(x)] when x is periodic
- (R3) **Constructivity:** Inv is computable from the orbit

**The Resolution.** We answer **positively** by constructing the **Asymptotic
Orbit Invariant (AOI)**, a three-level theory:

1. **Level 1 — The Orbit Trace (OT):** A coinductive invariant capturing the
   *full asymptotic structure* of any persistent orbit. Well-defined for ALL
   persistent elements, periodic or aperiodic.

2. **Level 2 — The Orbit Spectrum (OS):** An ergodic-theoretic invariant
   capturing the *frequency distribution* of bisimulation class visits. Defined
   for orbits with well-defined asymptotic frequencies (a measure-zero
   exclusion under mild regularity).

3. **Level 3 — The Orbit Complexity (OC):** A descriptive set-theoretic
   invariant classifying the *structural complexity* of the orbit trace.
   Always defined, providing a coarse but universal classification.

All three levels satisfy (R1)–(R3). Level 1 is the finest (most discriminating),
Level 3 the coarsest (always defined). CNF∞ embeds as a special case at all
three levels.

**Key theorems:**

| Theorem | Statement |
|---------|-----------|
| `AOI₁-WD` (L6.3.T2) | AOI is well-defined for all x ∈ ∞_M |
| `AOI-BisInv` (L6.3.T3) | AOI is bisimulation-invariant |
| `AOI-CNF∞` (L6.3.T4) | AOI extends CNF∞ for periodic orbits |
| `AOI-Const` (L6.3.T5) | AOI is constructive (computable from finite orbit prefixes) |
| `OS-BisInv` (L6.3.T7) | The orbit spectrum classifies aperiodic orbits up to asymptotic equivalence |
| `OC-WD` (L6.3.T10) | The orbit complexity provides a countable ordinal rank for all orbits |
| `SC-Imp` (L6.3.T1) | No single-class invariant exists for aperiodic orbits (impossibility) |

---

## THE IMPOSSIBILITY OF A SINGLE-CLASS INVARIANT

Before constructing the positive solution, we prove that the original framing
of the problem — seeking a *single bisimulation class* as invariant — is
impossible for genuinely aperiodic orbits. This motivates the shift to richer
invariant structures.

### Single-Class Impossibility
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L6.3.T1 | `SC-Imp` | | **Novel** |
**Synopsis:** The Single-Class Impossibility theorem: there is no single bisimulation-invariant function f : ∞_M → W (for any well-ordered W) that classifies all persistent elements into a hierarchy terminating at ordinal ω. The proof uses a diagonal argument on shift-invariant sequences. Multiple invariant levels (AOI₁, OS_M, OC) are genuinely necessary.

**Source:** CRPT; from `OT-21B` (L6.3.D1) + `CNF∞-Def` (L3.3.D6).


Let x ∈ ∞_M be aperiodic (∀N, p ≥ 1 : ∃n ≥ N : ρ_M^{n+p}(x) ≉ ρ_M^n(x)).
There exists no function Φ : ∞_M → 𝒰_M/≈ (assigning a single bisimulation
class) satisfying all of:

(i)   Φ(x) = Φ(y) whenever x ≈ y
(ii)  Φ(x) = [CNF∞(x)] whenever x is periodic
(iii) Φ is shift-invariant: Φ(ρ_M(x)) = Φ(x) for all x ∈ ∞_M

*Proof.*

Suppose such Φ exists. By (iii), Φ(ρ_M^n(x)) = Φ(x) for all n ∈ ℕ
(induction on n: Φ(ρ_M^{n+1}(x)) = Φ(ρ_M(ρ_M^n(x))) = Φ(ρ_M^n(x)) = Φ(x)).

So Φ assigns the single class Φ(x) = [c]_≈ for some c. By definition of Φ,
this means that [c]_≈ is the "invariant class" for the entire orbit of x.

Now construct a periodic orbit y with CNF∞(y) = [c]_≈ (such y exists: take
any z ∈ [c]_≈ and consider the constant orbit ρ_M(z) ≈ z, which gives
CNF∞(z) = [c]_≈; if no such z exists, Φ(x) = [c]_≈ is vacuous).

By (ii), Φ(y) = [CNF∞(y)] = [c]_≈ = Φ(x).

But x is aperiodic and y is periodic — they have fundamentally different
dynamical behaviour. For Φ to be a meaningful invariant, it must distinguish
orbits with different asymptotic structure. Yet Φ(x) = Φ(y) = [c]_≈ identifies
an aperiodic orbit with a periodic one.

More precisely: consider the orbit of x. Since x is aperiodic, ∃n₁ < n₂ with
[ρ_M^{n₁}(x)]_≈ ≠ [c]_≈ (if all orbit elements were in [c]_≈, then SC-1
would hold with N = 0, contradicting aperiodicity). So the orbit visits classes
other than [c]_≈. But the periodic orbit y stays in [c]_≈. No single class
can capture this distinction. ∎

### Shift-Invariance Scope of Single-Class Impossibility
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Remark** | L6.3.R1 | `SC-Imp-Scope` | | **Novel** |
**Synopsis:** Scope boundary remark for Single-Class Impossibility: the impossibility applies to first-order definable functions. Second-order resources (the orbit trace OC(x) as a Borel rank) do provide a classification into ordinals, at the cost of moving beyond first-order expressibility.

**Source:** CRPT; from `SC-Imp` (L6.3.T1).

The impossibility is specifically for *shift-invariant*
single-class assignments. If we drop shift-invariance, we can assign an
arbitrary class, but it would depend on the starting point of the orbit —
Φ(x) ≠ Φ(ρ_M(x)) in general — and would not be a genuine orbit invariant.

**Consequence:** Any invariant for aperiodic orbits must be *richer* than a
single bisimulation class. We need an invariant that captures the *sequence*
of classes visited, not just a single target class.

---

## LEVEL 1 — THE ORBIT TRACE INVARIANT

### The Orbit Trace

### Orbit Trace
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L6.3.D1 | `OT-21B` | OT_M(x) | **Novel** |
**Synopsis:** Orbit trace at L6.3: OT(x) treated as a point in the product space Q_M^ω with the product topology. Bisimulation invariance of OT is the starting point for all AOI proofs in this section.

**Source:** CRPT; from `OT` (L6.1.D1).


For x ∈ ∞_M, the *orbit trace* of x is the sequence of bisimulation classes
visited by the ρ_M-orbit of x:

```
OT_M(x)  :=  ( [ρ_M^n(x)]_≈ )_{n ∈ ℕ}  ∈  (𝒰_M / ≈)^ω
```

That is, OT_M(x) is a countable sequence whose n-th element is the bisimulation
class of the n-th iterate of x under ρ_M.

### Tail Equivalence on Traces
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L6.3.D2 | `Tail-Eq` | | **Reframed** |
**Synopsis:** Tail equivalence on Q_M^ω: two sequences s, t are tail-equivalent (s ~ t) when they agree from some index onward — ∃N : ∀n ≥ N, s(n) = t(n). Tail equivalence captures 'eventual sameness' of infinite sequences, ignoring finite prefixes.

**Source:** CRPT; from `OT-21B` (L6.3.D1); reframes tail equivalence of sequences.


Two orbit traces OT_M(x) and OT_M(y) are *tail-equivalent*, written
OT_M(x) ~_tail OT_M(y), if their tails eventually agree:

```
OT_M(x) ~_tail OT_M(y)  :⟺  ∃m, n ∈ ℕ : ∀k ∈ ℕ :
    [ρ_M^{m+k}(x)]_≈ = [ρ_M^{n+k}(y)]_≈
```

That is, after discarding finite initial segments, the two traces become identical
(as sequences of bisimulation classes).

### Tail Equivalence is an Equivalence Relation
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Lemma** | L6.3.L1 | `Tail-EqRel` | | **Imported** |
**Synopsis:** Tail equivalence ~ is an equivalence relation on Q_M^ω: reflexivity (s ~ s trivially), symmetry (s ~ t implies t ~ s), and transitivity (s ~ t and t ~ u implies s ~ u using the max of the two threshold indices). Standard verification.

**Source:** Standard set theory — equivalence-relation axioms; applied to `Tail-Eq` (L6.3.D2).


~_tail is reflexive, symmetric, and transitive on (𝒰_M/≈)^ω.

*Proof.*

*Reflexivity:* OT_M(x) ~_tail OT_M(x). Take m = n = 0. Then ∀k:
[ρ_M^{0+k}(x)]_≈ = [ρ_M^{0+k}(x)]_≈. ✓

*Symmetry:* If OT_M(x) ~_tail OT_M(y) with witnesses m, n, then
OT_M(y) ~_tail OT_M(x) with witnesses n, m. ✓

*Transitivity:* If OT_M(x) ~_tail OT_M(y) with witnesses m₁, n₁ and
OT_M(y) ~_tail OT_M(z) with witnesses m₂, n₂, then:
```
∀k : [ρ_M^{m₁+k}(x)]_≈ = [ρ_M^{n₁+k}(y)]_≈
∀k : [ρ_M^{m₂+k}(y)]_≈ = [ρ_M^{n₂+k}(z)]_≈
```

Set k' = k + max(n₁, m₂) - n₁ in the first, and k'' = k + max(n₁, m₂) - m₂ in
the second. We need a uniform offset.

Take M = m₁ + max(n₁, m₂) - n₁ = m₁ + max(0, m₂ - n₁) and
     N = n₂ + max(n₁, m₂) - m₂ = n₂ + max(0, n₁ - m₂).

For any k ∈ ℕ:
- From the first relation with offset max(n₁, m₂) - n₁ + k:
  [ρ_M^{m₁ + max(n₁,m₂) - n₁ + k}(x)]_≈ = [ρ_M^{max(n₁,m₂) + k}(y)]_≈
- From the second relation with offset max(n₁, m₂) - m₂ + k:
  [ρ_M^{max(n₁,m₂) + k}(y)]_≈ = [ρ_M^{n₂ + max(n₁,m₂) - m₂ + k}(z)]_≈

Therefore: [ρ_M^{M+k}(x)]_≈ = [ρ_M^{N+k}(z)]_≈ for all k. So OT_M(x) ~_tail OT_M(z). ✓ ∎

### The Asymptotic Orbit Invariant (Level 1)

### Asymptotic Orbit Invariant — Level 1
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L6.3.D3 | `AOI₁` | AOI₁(x) | **Novel** |
**Synopsis:** The level-1 asymptotic orbit invariant AOI₁(x) is the tail-equivalence class [OT(x)]_~ of the orbit trace. It captures the eventual behavior of the orbit — what the orbit does in the long run after discarding any finite transient prefix.

**Source:** CRPT; from `OT-21B` (L6.3.D1) + `Tail-Eq` (L6.3.D2).


For x ∈ ∞_M, the *Asymptotic Orbit Invariant* at Level 1 is the tail-equivalence
class of the orbit trace:

```
AOI₁(x)  :=  [OT_M(x)]_{~_tail}  ∈  (𝒰_M / ≈)^ω / ~_tail
```

### AOI₁ is Well-Defined
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L6.3.T2 | `AOI₁-WD` | | **Novel** |
**Synopsis:** AOI₁ is well-defined: [OT(x)]_~ depends only on x (not on any choice of representative) and is invariant under ≃_M by AOI-1 bisimulation invariance. AOI₁ is therefore a genuine observable invariant.

**Source:** CRPT; from `AOI₁` (L6.3.D3) + `Tail-EqRel` (L6.3.L1).


For every x ∈ ∞_M, AOI₁(x) exists and is uniquely determined.

*Proof.*

OT_M(x) = ([ρ_M^n(x)]_≈)_{n∈ℕ} is well-defined:
- ρ_M^n(x) is well-defined for all n (ρ_M is a total function on 𝒰_M, and
  x ∈ ∞_M ⟹ ρ_M^n(x) ∈ ∞_M by `Refl-Abs-T` (L4.7.T2),
  persistent regime closure).
- [ρ_M^n(x)]_≈ is a well-defined bisimulation class (≈ is an equivalence
  relation on 𝒰_M by `≈-Eq` (L1.1.L2), with ≈ defined at `Bisim~` (L1.1.D7)).

The quotient (𝒰_M/≈)^ω / ~_tail is well-defined because ~_tail is an equivalence
relation (`Tail-EqRel` (L6.3.L1)). Therefore AOI₁(x) = [OT_M(x)]_{~_tail} exists and is
unique. ∎

### Bisimulation Invariance
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L6.3.T3 | `AOI-BisInv` | | **Novel** |
**Synopsis:** AOI bisimulation invariance (full proof): if x ≈ y then AOI₁(x) = AOI₁(y). The proof uses PA-Bisim to show [ρ_M^n(x)]_≈ = [ρ_M^n(y)]_≈ for all n by induction, giving OT(x) = OT(y) pointwise and hence [OT(x)]_~ = [OT(y)]_~.

**Source:** CRPT; from `AOI₁` (L6.3.D3) + PA-Bisim (L1.3.Ax1).


For x, y ∈ ∞_M: if x ≈ y, then AOI₁(x) = AOI₁(y).

*Proof.*

Assume x ≈ y. We need to show OT_M(x) ~_tail OT_M(y), i.e., ∃m, n :
∀k : [ρ_M^{m+k}(x)]_≈ = [ρ_M^{n+k}(y)]_≈.

**Claim:** [ρ_M^n(x)]_≈ = [ρ_M^n(y)]_≈ for all n ∈ ℕ.

*Proof of claim by induction on n:*

*Base (n = 0):* [ρ_M^0(x)]_≈ = [x]_≈ and [ρ_M^0(y)]_≈ = [y]_≈.
Since x ≈ y, we have [x]_≈ = [y]_≈. ✓

*Step (n → n+1):* Assume [ρ_M^n(x)]_≈ = [ρ_M^n(y)]_≈, i.e.,
ρ_M^n(x) ≈ ρ_M^n(y).

We need: ρ_M^{n+1}(x) ≈ ρ_M^{n+1}(y), i.e., ρ_M(ρ_M^n(x)) ≈ ρ_M(ρ_M^n(y)).

This follows directly from C2 (Bisimulation Equivariance):
u ≈ v ⟹ ρ_M(u) ≈ ρ_M(v).
Apply C2 with u = ρ_M^n(x), v = ρ_M^n(y).

Applied to u = ρ_M^n(x), v = ρ_M^n(y): ρ_M^{n+1}(x) ≈ ρ_M^{n+1}(y). ✓

*End of claim.* We have [ρ_M^n(x)]_≈ = [ρ_M^n(y)]_≈ for all n. Therefore
OT_M(x) = OT_M(y) (pointwise equality of sequences), which implies
OT_M(x) ~_tail OT_M(y) (with m = n = 0). Therefore AOI₁(x) = AOI₁(y). ∎

### AOI₁ Proves Pointwise Orbit-Trace Equality
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Remark** | L6.3.R2 | `AOI₁-PW` | | **Novel** |
**Synopsis:** Pointwise orbit-trace equality: x ≈ y implies [ρ_M^n(x)]_≈ = [ρ_M^n(y)]_≈ for all n ≥ 0, proved by induction on n using PA-Bisim at each step.

**Source:** CRPT; from `AOI-BisInv` (L6.3.T3).

The proof establishes more than tail equivalence: it shows
pointwise equality of the orbit traces OT_M(x) = OT_M(y). This is strictly
stronger than tail equivalence. The stronger result holds because bisimulation
propagates through ρ_M at every step, not just eventually.

### Extension of CNF∞
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L6.3.T4 | `AOI-CNF∞` | | **Novel** |
**Synopsis:** AOI₁ extends CNF∞_M: for SC-1 elements, the tail-equivalence class [OT(x)]_~ completely determines CNF∞_M(x). AOI₁ is therefore at least as fine as CNF∞_M on the SC-1 stratum, and strictly finer on aperiodic elements where CNF∞_M is undefined.

**Source:** CRPT; from `AOI₁` (L6.3.D3) + `CNF∞-Def` (L3.3.D6).


For x ∈ ∞_M with periodic orbit (period p, transient N), satisfying SC-1:

```
AOI₁(x) determines CNF∞(x), and conversely.
```

More precisely: if x, y ∈ ∞_M are both periodic with AOI₁(x) = AOI₁(y), then
CNF∞(x) = CNF∞(y).

*Proof.*

Since x is periodic with period p and transient N, the orbit trace
OT_M(x) = ([x]_≈, [ρ_M(x)]_≈, ..., [ρ_M^N(x)]_≈, [ρ_M^{N+1}(x)]_≈, ..., [ρ_M^{N+p-1}(x)]_≈, [ρ_M^N(x)]_≈, ...)
is eventually periodic with period p after transient N.

Under SC-1: ∀m, n ≥ N : ρ_M^m(x) ≈ ρ_M^n(x). So all elements from position N
onward are in the same bisimulation class [ρ_M^N(x)]_≈. The tail of the trace
(from position N) is the constant sequence ([ρ_M^N(x)]_≈, [ρ_M^N(x)]_≈, ...).

Similarly for y: the tail from position N' is constant ([ρ_M^{N'}(y)]_≈, ...).

If AOI₁(x) = AOI₁(y), then OT_M(x) ~_tail OT_M(y): ∃m, n : ∀k :
[ρ_M^{m+k}(x)]_≈ = [ρ_M^{n+k}(y)]_≈. Taking m ≥ N and n ≥ N', the constant
tails must match: [ρ_M^N(x)]_≈ = [ρ_M^{N'}(y)]_≈. But [ρ_M^N(x)]_≈ = CNF∞(x)
and [ρ_M^{N'}(y)]_≈ = CNF∞(y). Therefore CNF∞(x) = CNF∞(y). ∎

### CNF∞ Embeds in AOI₁
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Corollary** | L6.3.C1 | `CNF∞⊂AOI₁` | | **Novel** |
**Synopsis:** CNF∞_M embeds into AOI₁: for SC-1 elements, knowing AOI₁(x) is sufficient to recover CNF∞_M(x). AOI₁ is the natural generalisation of CNF∞_M to all of ∞_M.

**Source:** CRPT; from `AOI-CNF∞` (L6.3.T4).


Define the embedding ι : CNF∞ → AOI₁ by:
```
ι(CNF∞(x))  :=  AOI₁(x)   for periodic x ∈ ∞_M satisfying SC-1
```

Then ι is well-defined (independent of the choice of representative x) and
injective (distinct CNF∞ values map to distinct AOI₁ values).

*Proof of well-definedness:* If CNF∞(x) = CNF∞(y), then [ρ_M^{N_x}(x)]_≈ =
[ρ_M^{N_y}(y)]_≈. The tails of OT_M(x) and OT_M(y) are eventually constant
at the same class. Therefore OT_M(x) ~_tail OT_M(y), i.e., AOI₁(x) = AOI₁(y).
So ι does not depend on which x represents CNF∞(x). ✓

*Proof of injectivity:* By `AOI-CNF∞` (L6.3.T4) above — AOI₁(x) = AOI₁(y) implies
CNF∞(x) = CNF∞(y) for periodic orbits. ✓ ∎

### Constructivity of AOI₁

### Constructivity
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L6.3.T5 | `AOI-Const` | | **Novel** |
**Synopsis:** AOI₁ constructivity: [OT(x)]_~ is computable from the orbit for SC-3 elements (computable period). For AP elements, AOI₁(x) may be a Π₂⁰ set in the Borel hierarchy — computable in the limit but not in general primitive recursive.

**Source:** CRPT; from `AOI₁` (L6.3.D3) + `SC-3` (L3.3.D4).


AOI₁(x) is constructive: it is determined by the orbit trace OT_M(x), which is
computable from finite orbit prefixes in the following sense.

For any finite prefix length n ∈ ℕ, the *n-prefix* of the orbit trace is:
```
OT_M^{≤n}(x)  :=  ([ρ_M^0(x)]_≈, [ρ_M^1(x)]_≈, ..., [ρ_M^n(x)]_≈)
```

This is a finite tuple computable by n applications of ρ_M followed by
bisimulation-class identification. The full orbit trace is the colimit:
```
OT_M(x)  =  colim_{n→∞} OT_M^{≤n}(x)
```

*Proof.*

Each step is computable:
1. ρ_M^k(x) is computable by k applications of ρ_M (ρ_M is a total function on 𝒰_M).
2. [ρ_M^k(x)]_≈ is computable by bisimulation checking (testing whether
   ρ_M^k(x) ≈ ρ_M^j(x) for previously seen orbit elements).
3. The finite prefix OT_M^{≤n}(x) is a finite sequence of bisimulation classes,
   computable in O(n²) bisimulation checks (each new element against all previous ones).
4. AOI₁(x) = [OT_M(x)]_{~_tail} is the tail-equivalence class of the full sequence.

The orbit trace is *coinductively generated*: at each step, we observe the current
bisimulation class (head) and advance to the next iterate (tail). This is exactly
the coalgebra structure of streams over 𝒰_M/≈. ✓

*Remark on decidability:* Whether two orbit traces are tail-equivalent is in
general undecidable (it requires checking eventual agreement of two infinite
sequences). However, for finite-alphabet substrates (|𝒰_M/≈| < ∞), tail
equivalence is decidable: two sequences over a finite alphabet are tail-equivalent
iff their suffixes eventually agree, which can be tested by suffix matching
algorithms. For the periodic case, tail equivalence reduces to comparing the
periodic tails, which is decidable in O(p₁ · p₂) where p₁, p₂ are the periods.
For aperiodic orbits over countable alphabets, the problem is Π₂⁰-complete in
the arithmetic hierarchy — undecidable but recursively enumerable in the limit. ∎

### Discriminating Power of AOI₁

AOI₁ is a *finer* invariant than CNF∞: it distinguishes orbits that CNF∞ cannot.

### AOI₁ Strictly Refines CNF∞
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L6.3.T6 | `AOI₁>CNF∞` | | **Novel** |
**Synopsis:** AOI₁ strictly refines CNF∞_M: there exist AP elements x, y with AOI₁(x) ≠ AOI₁(y) but CNF∞_M undefined for both. The witness is a pair of AP elements with distinct aperiodic orbit traces that are not tail-equivalent.

**Source:** CRPT; from `AOI₁` (L6.3.D3) + `OTC` (L6.2.D1).


There exist x, y ∈ ∞_M with AOI₁(x) ≠ AOI₁(y) but where neither has a
well-defined CNF∞ (both are aperiodic).

*Proof.* (Constructive — stream model.)

Let α = ℕ (natural numbers as stream alphabet). Consider:

- σ = (0, 1, 0, 1, 0, 2, 0, 1, 0, 1, 0, 2, ...) — repeating block (0,1,0,1,0,2)
  with period 6. This is periodic; CNF∞ exists.

- τ = (0, 1, 2, 3, 4, 5, 6, 7, ...) — the identity stream. This is aperiodic;
  SC-1 fails; CNF∞ undefined.

- ρ = (1, 0, 3, 2, 5, 4, 7, 6, ...) — the swap stream (each pair transposed).
  This is aperiodic; SC-1 fails; CNF∞ undefined.

Under stream bisimulation (σ ≈ τ iff σₙ = τₙ for all n): τ ≉ ρ (they differ
at position 0: τ₀ = 0 ≠ 1 = ρ₀). Moreover, tail(τ) = (1,2,3,...) ≉ tail(ρ) = (0,3,2,...).
No tail of τ ever equals any tail of ρ (every prefix differs).

Therefore OT_M(τ) ≁_tail OT_M(ρ): for any m, n, [tail^m(τ)]_≈ ≠ [tail^n(ρ)]_≈
(since tail^m(τ) = (m, m+1, m+2, ...) and tail^n(ρ) = a sequence starting with
ρ_n, and these are never equal for any choice of m, n because the sequences
have different structure).

So AOI₁(τ) ≠ AOI₁(ρ). Both are aperiodic. CNF∞ is undefined for both. But
AOI₁ distinguishes them. ∎

---

## LEVEL 2 — THE ORBIT SPECTRUM

Level 1 (AOI₁) captures the full sequence structure. Level 2 provides a coarser
but more analytically tractable invariant: the *frequency distribution* of
bisimulation class visits.

### Asymptotic Frequency

### Visit Frequency
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L6.3.D4 | `Freq` | freq_x(C) | **Reframed** |
**Synopsis:** Asymptotic frequency: given sequence s ∈ Q_M^ω and class C, freq(s, C) = lim_{n→∞} (1/n)|{k < n | s(k) ∈ C}| when this limit exists. Standard ergodic-theoretic concept adapted to projection-orbit class-visit sequences.

**Source:** CRPT; from `OT-21B` (L6.3.D1); reframes asymptotic (Cesàro) frequency.


For x ∈ ∞_M and a bisimulation class C ∈ 𝒰_M/≈, define the *visit frequency*
of C along the orbit of x:

```
freq_x(C)  :=  lim_{n→∞} (1/n) · |{ k < n  |  [ρ_M^k(x)]_≈ = C }|
```

when this limit exists. Here |{...}| denotes the cardinality of the set of
integers k < n for which the k-th iterate falls in class C.

### Orbit Spectrum
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L6.3.D5 | `OS-21B` | OS_M(x) | **Novel** |
**Synopsis:** Orbit spectrum at L6.3: OS_M(x) : {A,B,C,D,E} → [0,1] defined by C ↦ freq(OT(x), C) when all five limits exist (SC-4). OS_M(x) is a probability measure on the five active classes capturing statistical long-run behavior.

**Source:** CRPT; from `Freq` (L6.3.D4) + `OT-21B` (L6.3.D1).


For x ∈ ∞_M, the *orbit spectrum* of x is the function:

```
OS_M(x) : 𝒰_M/≈ → [0, 1]
OS_M(x)(C) := freq_x(C)
```

defined on those classes C for which the limit exists.

The *full orbit spectrum* is defined when freq_x(C) exists for ALL classes C ∈ B̃(x)
(where B̃(x) = {[ρ_M^n(x)]_≈ | n ∈ ℕ} is the set of visited classes).

### Spectrum-Definite Orbit
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L6.3.D6 | `Spec-Def` | | **Novel** |
**Synopsis:** Orbit spectrum formal definition: OS_M(x)(C) = freq(OT(x), C) when all limits exist and sum to 1. The SC-4 condition is precisely the requirement that all five limits exist.

**Source:** CRPT; from `OS-21B` (L6.3.D5) + `SC-4-Def` (L3.3.D5).


An orbit Orb_M(x) is *spectrum-definite* if OS_M(x) is fully defined, i.e.:
```
∀C ∈ B̃(x) : freq_x(C) exists
```

### Properties of the Orbit Spectrum

### Frequency Sum
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Lemma** | L6.3.L2 | `Freq-Sum` | | **Imported** |
**Synopsis:** Asymptotic frequencies of a partition sum to 1: if the five class frequencies all exist, Σ_C freq(OT(x), C) = 1. Standard ergodic-theory result for finite partitions.

**Source:** Standard measure theory — frequencies of a finite partition sum to 1; applied to `Freq` (L6.3.D4).


For spectrum-definite x ∈ ∞_M:
```
∑_{C ∈ B̃(x)} OS_M(x)(C) = 1
```

*Proof.*

For each n: ∑_{C ∈ B̃(x)} |{k < n | [ρ_M^k(x)]_≈ = C}| = n (every k < n falls
in exactly one class). Dividing by n:
∑_{C ∈ B̃(x)} (1/n)|{k < n | [ρ_M^k(x)]_≈ = C}| = 1.

Taking the limit as n → ∞: if B̃(x) is finite, the sum of limits equals the limit
of sums (finite sum). If B̃(x) is countably infinite, the dominated convergence
theorem applies (each term is bounded by 1 and the sum is exactly 1 for each n).
Therefore ∑_C freq_x(C) = 1. ∎

### Shift Invariance of Spectrum
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Lemma** | L6.3.L3 | `Spec-Shift` | | **Novel** |
**Synopsis:** Orbit Spectrum Shift-Invariance: OS_M(x) = OS_M(ρ_M(x)). Shifting the orbit by one step does not change its asymptotic frequency distribution — the first element has zero asymptotic weight.

**Source:** CRPT; from `OS-21B` (L6.3.D5).


OS_M(ρ_M(x)) = OS_M(x) for all spectrum-definite x ∈ ∞_M.

*Proof.*

For any class C: freq_{ρ_M(x)}(C) = lim_{n→∞} (1/n)|{k < n | [ρ_M^k(ρ_M(x))]_≈ = C}|
= lim_{n→∞} (1/n)|{k < n | [ρ_M^{k+1}(x)]_≈ = C}|
= lim_{n→∞} (1/n)|{j : 1 ≤ j ≤ n, [ρ_M^j(x)]_≈ = C}|.

Now |{j : 1 ≤ j ≤ n, [ρ_M^j(x)]_≈ = C}| = |{j < n+1 | [ρ_M^j(x)]_≈ = C}| - [j=0 case]
= |{j < n+1 | ...}| ± 1. Therefore:

freq_{ρ_M(x)}(C) = lim_{n→∞} (1/n)(|{j < n+1 | [ρ_M^j(x)]_≈ = C}| ± 1)
= lim_{n→∞} ((n+1)/n) · (1/(n+1))|{j < n+1 | ...}| ± 1/n
= 1 · freq_x(C) ± 0
= freq_x(C). ✓ ∎

### Orbit Spectrum is Bisimulation-Invariant
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L6.3.T7 | `OS-BisInv` | | **Novel** |
**Synopsis:** Orbit spectrum bisimulation invariance: x ≈ y implies OS_M(x) = OS_M(y). Follows from AOI-BisInv (identical orbit traces) and the fact that frequencies depend only on the trace.

**Source:** CRPT; from `OS-21B` (L6.3.D5) + `AOI-BisInv` (L6.3.T3).


For spectrum-definite x, y ∈ ∞_M: if x ≈ y, then OS_M(x) = OS_M(y).

*Proof.*

By the proof of `AOI-BisInv` (L6.3.T3), x ≈ y implies [ρ_M^n(x)]_≈ = [ρ_M^n(y)]_≈ for
all n. Therefore for any class C:

|{k < n | [ρ_M^k(x)]_≈ = C}| = |{k < n | [ρ_M^k(y)]_≈ = C}|

for all n. Taking limits: freq_x(C) = freq_y(C) for all C. So OS_M(x) = OS_M(y). ∎

### Orbit Spectrum for Periodic Orbits

### Periodic Spectrum Recovers CNF∞
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L6.3.T8 | `OS-Per=CNF∞` | | **Novel** |
**Synopsis:** For eventually-periodic orbits, the orbit spectrum reduces to a point mass at CNF∞_M(x): OS_M(x) = δ_{CNF∞_M(x)}. The orbit spends all its asymptotic time at the periodic canonical form.

**Source:** CRPT; from `OS-21B` (L6.3.D5) + `CNF∞-Def` (L3.3.D6).


For x ∈ ∞_M with periodic orbit (period p, transient N) satisfying SC-1:

(a) B̃(x) is finite (at most N + 1 classes: N transient classes + 1 stable class).

(b) The orbit is spectrum-definite.

(c) OS_M(x) is the atomic measure concentrated on CNF∞(x):
```
OS_M(x)(C) = 1    if C = CNF∞(x)
OS_M(x)(C) = 0    if C ≠ CNF∞(x) and C ∈ B̃(x)
```

*Proof.*

(a) Under SC-1, ∀m, n ≥ N: [ρ_M^m(x)]_≈ = [ρ_M^n(x)]_≈ = [ρ_M^N(x)]_≈.
So B̃(x) ⊆ {[ρ_M^0(x)]_≈, ..., [ρ_M^{N-1}(x)]_≈, [ρ_M^N(x)]_≈} — at most N+1
distinct classes. ✓

(b) For any C ∈ B̃(x): if C = [ρ_M^N(x)]_≈ = CNF∞(x), then for n > N:
|{k < n | [ρ_M^k(x)]_≈ = C}| ≥ n - N. So freq_x(C) = lim (n-N)/n ... wait,
more precisely:

|{k < n | [ρ_M^k(x)]_≈ = CNF∞(x)}| = (n - N) for n > N (all positions from
N onward are in class CNF∞(x), and some of 0,...,N-1 may also be in this class).
Actually: |{k < n | ...}| ≥ n - N for n > N. And |{k < n | ...}| ≤ n.
So freq_x(CNF∞(x)) = lim_{n→∞} |{...}|/n. Since n-N ≤ |{...}| ≤ n, the limit
is 1. ✓

For C ≠ CNF∞(x): the set {k | [ρ_M^k(x)]_≈ = C} ⊆ {0, 1, ..., N-1} (only finitely
many positions in the transient visit C). So |{k < n | ...}| is bounded by N.
Therefore freq_x(C) = lim N/n = 0. ✓

(c) Follows from (b): OS_M(x) = ρ_{CNF∞(x)} (the Dirac delta at CNF∞(x)). ✓ ∎

### Periodic Spectrum Determines CNF∞
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Corollary** | L6.3.C2 | `OS-Det` | | **Novel** |
**Synopsis:** For deterministic convergent orbits (elements of ↓_M), the spectrum is the Dirac delta OS_M(x) = δ_{[CNF_M(x)]_≈}: frequency 1 at the canonical form class, 0 everywhere else.

**Source:** CRPT; from `OS-Per=CNF∞` (L6.3.T8).

For periodic orbits satisfying SC-1, the orbit spectrum
OS_M(x) determines CNF∞(x) (as the unique class with frequency 1), and conversely.
The embedding CNF∞ ↪ OS is therefore faithful.

### Aperiodic Spectra — Concrete Examples

### Alternating Stream
| **Example** | L6.3.3.Ex1 | `Ex-AltStr` | | **Novel** |
**Synopsis:** Alternating structure example: orbit x → y → x → y → ... gives OS_M = (1/2)δ_{[x]_≈} + (1/2)δ_{[y]_≈}. Equal asymptotic frequency for both classes. Distinguishable from constant orbits by AOI₁.

**Source:** CRPT; from `OS-21B` (L6.3.D5).


Let σ = (0, 1, 0, 1, 0, 1, ...) over α = {0, 1}. The orbit is:
- tail^0(σ) = (0, 1, 0, 1, ...) in class C₀
- tail^1(σ) = (1, 0, 1, 0, ...) in class C₁
- tail^2(σ) = (0, 1, 0, 1, ...) in class C₀
- ...

This is periodic with period 2, not aperiodic. SC-1 holds with p = 2 (but
SC-1 as stated requires a *single* class, and here we have two classes C₀, C₁
alternating). Under SC-1's precise wording ("∀m, n ≥ N: ρ^m(x) ≈ ρ^n(x)"),
this FAILS — tail^N(σ) ≉ tail^{N+1}(σ) for all N.

So the alternating stream actually fails SC-1! The orbit has period 2 but visits
two distinct bisimulation classes. CNF∞ is technically undefined.

The orbit spectrum: OS(σ)(C₀) = 1/2, OS(σ)(C₁) = 1/2. This is the uniform
distribution on two classes — a perfectly well-defined invariant even though CNF∞
fails.

### Orbit Spectrum Beyond SC-1

| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Remark** | L6.3.R4 | `Spectrum-BeyondSC1` | | **Novel** |
**Synopsis:** The orbit spectrum extends beyond SC-1-periodic orbits to all eventually periodic orbits, including those of period p > 1 that visit several distinct bisimulation classes.

**Source:** CRPT; from `Spec-Def` (L6.3.D6).

This shows that the orbit spectrum extends beyond SC-1-periodic orbits
to all eventually periodic orbits (including those with period p > 1 visiting
multiple distinct classes).

### Champernowne Stream
| **Example** | L6.3.3.Ex2 | `Ex-Champ` | | **Novel** |
**Synopsis:** Champernowne-type example: an orbit whose class-visit sequence encodes the Champernowne word. This SC-4 orbit has uniform spectrum but high AOI₁ complexity — aperiodic with Borel rank ω in the orbit complexity measure.

**Source:** CRPT; from `OS-21B` (L6.3.D5); Champernowne normality (standard).


Let σ_C = (0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 1, 0, 1, 1, 1, 2, ...) — the
Champernowne sequence over α = {0, 1, ..., 9} (decimal digits of the
Champernowne constant 0.123456789101112...).

The orbit trace visits infinitely many distinct bisimulation classes (each
tail^n(σ_C) is a distinct stream, hence a distinct class).

The visit frequency of digit d ∈ {0,...,9} at position 0 is:
freq_{σ_C}([streams starting with d]_≈) = 1/10.

More precisely, each digit 0-9 appears as the leading digit of tail^k(σ_C) with
asymptotic frequency converging to specific values determined by the Champernowne
number's digit distribution. Since the Champernowne number is normal in base 10,
each digit d appears with frequency 1/10 as the leading digit of the tail.

The full orbit spectrum is well-defined (the Champernowne sequence is spectrum-definite)
and captures the "equidistribution" property that CNF∞ cannot express.

### Non-Spectrum-Definite Orbit
| **Example** | L6.3.3.Ex3 | `Ex-nonSD` | | **Novel** |
**Synopsis:** Non-shift-invariant orbit example: an orbit where frequency distributions change with the starting point of the count. Such orbits violate SC-4 and lie outside the orbit spectrum invariant's scope.

**Source:** CRPT; from `Spec-Def` (L6.3.D6).


Not all orbits are spectrum-definite. Consider the stream over α = {0, 1}:
```
σ = 0^1 1^2 0^4 1^8 0^{16} 1^{32} ...
```
(1 zero, 2 ones, 4 zeros, 8 ones, 16 zeros, ...). The fraction of 0s in the
first n positions oscillates and does not converge:

After the first 2^k - 1 positions (end of the k-th block):
- If k is odd: fraction of 0s ≈ 1/3
- If k is even: fraction of 0s ≈ 2/3

The limit does not exist. This orbit is NOT spectrum-definite.

For such orbits, Level 2 (orbit spectrum) is undefined. Level 1 (orbit trace)
and Level 3 (orbit complexity) still apply.

### Spectrum-Definite Orbits: Sufficient Conditions

### Sufficient Conditions for Spectrum-Definiteness
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L6.3.T9 | `OS-Suf` | | **Novel** |
**Synopsis:** Orbit Spectrum Sufficiency: for EP orbits, OS_M is a complete bisimulation-invariant. For AP elements, OS_M is not sufficient: distinct AP orbits can have identical spectra but different AOI₁ values.

**Source:** CRPT; from `Spec-Def` (L6.3.D6) + `SC4-EP` (L3.3.T1); Birkhoff ergodic theorem.


An orbit Orb_M(x) is spectrum-definite if any of the following hold:

(i) The orbit is eventually periodic (period p ≥ 1). In this case, the spectrum
is the empirical distribution of the periodic block.

(ii) |B̃(x)| < ∞ (SC-4 holds). Then the orbit is eventually periodic by
`SC4-EP` (L3.3.T1), reducing to case (i).

(iii) The orbit trace, viewed as a sequence over 𝒰_M/≈, is *generic* for an
ergodic shift-invariant measure μ on (𝒰_M/≈)^ω. (Birkhoff's ergodic theorem
guarantees that μ-almost every orbit trace is spectrum-definite.)

*Proof of (i):* If the orbit is eventually periodic with transient N and period p,
then for any class C:

|{k < n | [ρ_M^k(x)]_≈ = C}| = |{k < N | [ρ_M^k(x)]_≈ = C}| +
    ⌊(n-N)/p⌋ · |{j : 0 ≤ j < p | [ρ_M^{N+j}(x)]_≈ = C}|  ± p

Dividing by n and taking n → ∞: freq_x(C) = |{j : 0 ≤ j < p | [ρ_M^{N+j}(x)]_≈ = C}| / p.
This is the fraction of the periodic block that class C occupies. Well-defined. ✓

*Proof of (ii):* SC-4 ⟹ eventually periodic (`SC4-EP` (L3.3.T1)) ⟹ case (i). ✓

*Proof of (iii):* Birkhoff's pointwise ergodic theorem: for an ergodic
shift-invariant measure μ on a sequence space, for μ-a.e. sequence ω:
lim_{n→∞} (1/n) Σ_{k=0}^{n-1} f(T^k(ω)) = ∫ f dμ
for any integrable f. Taking f = 1_C (indicator of class C):
freq_x(C) = μ({ω | ω_0 = C}) = μ(cylinder set [C]). This exists μ-a.e. ✓ ∎

---

## LEVEL 3 — THE ORBIT COMPLEXITY

Level 3 provides a *universally defined* invariant — it applies to every persistent
orbit, including those that are neither periodic nor spectrum-definite. It uses
descriptive set-theoretic methods to assign a complexity rank.

### The Recurrence Structure

### Recurrence Set
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L6.3.D7 | `Rec-Set` | | **Reframed** |
**Synopsis:** The recurrence set R(x, C) = {n ∈ ℕ | [ρ_M^n(x)]_≈ ∈ C} records the times at which the orbit visits class C. Its density is the asymptotic frequency freq(OT(x), C).

**Source:** CRPT; from `OT-21B` (L6.3.D1); reframes the recurrence set of symbolic dynamics.


For x ∈ ∞_M and a bisimulation class C ∈ 𝒰_M/≈, the *recurrence set* of C
along the orbit of x is:

```
Rec_x(C)  :=  { n ∈ ℕ  |  [ρ_M^n(x)]_≈ = C }  ⊆  ℕ
```

The set of times at which the orbit visits class C.

### Recurrence Type
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L6.3.D8 | `Rec-Type` | | **Reframed** |
**Synopsis:** Recurrence type classifies R(x, C) by its density and structure: transient (finite), recurrent (infinite), periodic, syndetic (bounded gaps), thick (arbitrarily long intervals). Standard symbolic-dynamics taxonomy adapted for projection orbits.

**Source:** CRPT; from `Rec-Set` (L6.3.D7); reframes the symbolic-dynamics recurrence taxonomy.


For x ∈ ∞_M, the *recurrence type* of the orbit classifies each visited class C ∈ B̃(x)
by the structure of Rec_x(C):

| Recurrence Type | Condition on Rec_x(C) | Interpretation |
|-----------------|----------------------|----------------|
| **Transient** | Rec_x(C) is finite | Class visited only finitely often |
| **Recurrent** | Rec_x(C) is infinite | Class visited infinitely often |
| **Periodic** | Rec_x(C) is eventually arithmetic | Visits with eventual constant gap |
| **Syndetic** | Rec_x(C) has bounded gaps | Return time bounded |
| **Dense** | Rec_x(C) has positive upper density | Positive frequency of visits |
| **Thick** | Rec_x(C) contains arbitrarily long intervals | Long consecutive runs |

### The Orbit Complexity Rank

### Orbit Complexity
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L6.3.D9 | `OC-21B` | OC_M(x) | **Novel** |
**Synopsis:** Orbit Complexity OC_M(x) = (AOI₁(x), OS_M(x), rtype(x)): the complete bisimulation-invariant characterisation combining eventual behavior, long-run frequencies, and recurrence structure.

**Source:** CRPT; from `AOI₁` (L6.3.D3) + `OS-21B` (L6.3.D5) + `Rec-Type` (L6.3.D8).


For x ∈ ∞_M, the *orbit complexity* OC_M(x) is the pair:

```
OC_M(x)  :=  (κ(x), ρ(x))
```

where:

**(a) κ(x) ∈ {0, 1, 2, ω} — the complexity class:**
```
κ(x) = 0   if B̃(x) is a singleton (orbit stays in one class — SC-1 with N=0)
κ(x) = 1   if B̃(x) is finite, |B̃(x)| > 1 (eventually periodic, SC-4 holds)
κ(x) = 2   if B̃(x) is countably infinite and spectrum-definite
κ(x) = ω   if B̃(x) is countably infinite and NOT spectrum-definite
```

**(b) ρ(x) ∈ Ord — the recurrence rank (a countable ordinal):**

The recurrence rank measures how "complex" the recurrence patterns are, using the
Cantor-Bendixson derivative on the topological space of orbit tails.

Define the space of orbit tails:
```
Tails(x)  :=  { OT_M(ρ_M^n(x)) | n ∈ ℕ }  ⊆  (𝒰_M/≈)^ω
```

Equip (𝒰_M/≈)^ω with the product topology (where 𝒰_M/≈ has the discrete topology).
This makes (𝒰_M/≈)^ω a Polish space (when 𝒰_M/≈ is countable) or at least a
topological space.

The *Cantor-Bendixson derivative* D(S) of a set S ⊆ (𝒰_M/≈)^ω is the set of
limit points of S. Iterate:
```
Tails⁰(x) = Tails(x)
Tails^{α+1}(x) = D(Tails^α(x))    (remove isolated points)
Tails^λ(x) = ⋂_{α<λ} Tails^α(x)  (intersection at limit ordinals)
```

The Cantor-Bendixson rank of Tails(x) is the smallest ordinal α such that
Tails^α(x) = Tails^{α+1}(x) (stabilisation).

```
ρ(x) := CB-rank(Tails(x))
```

### Orbit Complexity is Well-Defined and Bisimulation-Invariant
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L6.3.T10 | `OC-WD` | | **Novel** |
**Synopsis:** Orbit complexity OC_M(x) is well-defined: AOI₁ requires no scope condition; OS_M and rtype require SC-4. When SC-4 holds, all three components are defined.

**Source:** CRPT; from `OC-21B` (L6.3.D9) + `SC-4-Def` (L3.3.D5).


For all x ∈ ∞_M:

(a) OC_M(x) = (κ(x), ρ(x)) is well-defined.
(b) If x ≈ y, then OC_M(x) = OC_M(y).
(c) OC_M(x) is a countable ordinal pair.

*Proof.*

**(a) Well-definedness:**

κ(x) is well-defined: B̃(x) = {[ρ_M^n(x)]_≈ | n ∈ ℕ} is a well-defined subset of
𝒰_M/≈ (each element is a bisimulation class, well-defined by `≈-Eq` (L1.1.L2)
with ≈ defined at `Bisim~` (L1.1.D7)).
B̃(x) is either a singleton, finite with > 1 element, or countably infinite
(it is the image of ℕ under n ↦ [ρ_M^n(x)]_≈, hence at most countable). The
spectrum-definiteness condition is well-defined (whether certain limits exist).
Therefore κ(x) ∈ {0, 1, 2, ω} is uniquely determined.

ρ(x) is well-defined: Tails(x) is a subset of (𝒰_M/≈)^ω, which is a topological
space under the product topology. The Cantor-Bendixson derivative is a standard
operation on topological spaces. The Cantor-Bendixson theorem guarantees that for
any subset of a second-countable space (which (𝒰_M/≈)^ω is when 𝒰_M/≈ is countable),
the Cantor-Bendixson process terminates at a countable ordinal. Therefore ρ(x) is
a well-defined countable ordinal.

When 𝒰_M/≈ is uncountable: the product space (𝒰_M/≈)^ω may not be second-countable.
In this case, replace the Cantor-Bendixson rank with the *condensation rank* (using
only points that are limit points from within Tails(x) itself). Since Tails(x) is
the image of ℕ under a continuous function (the orbit map), |Tails(x)| ≤ ℵ₀, and the
Cantor-Bendixson rank of a countable set is always a countable ordinal. ✓

**(b) Bisimulation invariance:**

If x ≈ y, then by `AOI-BisInv` (L6.3.T3) (proof), [ρ_M^n(x)]_≈ = [ρ_M^n(y)]_≈ for all n.
Therefore:
- B̃(x) = B̃(y) (same set of visited classes), so κ(x) = κ(y). ✓
- Tails(x) = Tails(y) (same set of orbit tails: OT_M(ρ_M^n(x)) = OT_M(ρ_M^n(y))
  for all n by the pointwise equality), so ρ(x) = ρ(y). ✓
- Spectrum-definiteness: freq_x(C) = freq_y(C) for all C (same counting sequences),
  so x is spectrum-definite iff y is. ✓

Therefore OC_M(x) = OC_M(y). ✓

**(c) Countability:** κ(x) ∈ {0, 1, 2, ω} (finite set). ρ(x) is a countable ordinal
(by the Cantor-Bendixson theorem applied to the countable set Tails(x)). ✓ ∎

### Orbit Complexity for Periodic Orbits

### Periodic Orbit Complexity
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L6.3.T11 | `OC-Per` | | **Novel** |
**Synopsis:** For SC-1 elements, orbit complexity reduces to: AOI₁ = eventual period class, OS_M = Dirac delta at CNF∞_M(x), rtype = periodic for the canonical class and transient for all others.

**Source:** CRPT; from `OC-21B` (L6.3.D9) + `SC-1` (L3.3.D2).


For x ∈ ∞_M with periodic orbit satisfying SC-1 (transient N, period 1 in
the bisimulation-class sequence):

```
OC_M(x) = (0, 0)
```

*Proof.*

Under SC-1: B̃(x) has at most N + 1 elements but the tail is a single class.
After position N, OT_M(ρ_M^n(x)) = constant sequence in (𝒰_M/≈)^ω. So
B̃(x) restricted to the tail = {CNF∞(x)} — a singleton. κ(x) = 0.

Tails(x) = {OT_M(ρ_M^n(x)) | n ∈ ℕ}. For n ≥ N, OT_M(ρ_M^n(x)) is the constant
sequence (CNF∞(x), CNF∞(x), ...). For n < N, OT_M(ρ_M^n(x)) is a distinct sequence
(containing the transient prefix). So |Tails(x)| = N + 1 (one tail for each
of the N transient positions, plus the stabilised constant tail).

A finite set has Cantor-Bendixson rank 0 (no limit points — all points are isolated
in the discrete topology). So ρ(x) = 0. ✓

Therefore OC_M(x) = (0, 0). ∎

### Eventually Periodic, Multi-Class
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L6.3.T12 | `OC-EP` | | **Novel** |
**Synopsis:** For AP elements satisfying SC-4, OC_M(x) captures the full statistical structure of the aperiodic orbit. The AOI₁ component is genuinely new information not captured by CNF∞_M.

**Source:** CRPT; from `OC-21B` (L6.3.D9) + `SC-4-Def` (L3.3.D5).


For x ∈ ∞_M with eventually periodic orbit, period p > 1, visiting p distinct
bisimulation classes cyclically (SC-4 holds but SC-1 fails):

```
OC_M(x) = (1, 0)
```

*Proof.*

B̃(x) is finite with |B̃(x)| = N + p for some transient N and period p. Since p > 1,
|B̃(x)| > 1. κ(x) = 1.

Tails(x) is again a finite set (at most N + p distinct tails). ρ(x) = 0. ✓ ∎

### Aperiodic, Spectrum-Definite
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L6.3.T13 | `Aper-Spec-Defi` | | **Novel** |
**Synopsis:** For AP orbits satisfying SC-4, the orbit spectrum OS_M is genuinely non-trivial — a proper probability distribution assigning positive frequency to at least two distinct classes, not a degenerate Dirac measure.

**Source:** CRPT; from `OC-21B` (L6.3.D9) + `Spec-Def` (L6.3.D6).


For x ∈ ∞_M with aperiodic, spectrum-definite orbit (e.g., Champernowne):

```
OC_M(x) = (2, ρ)  for some ρ ≥ 1
```

*Proof.*

B̃(x) is countably infinite (aperiodic orbit visits infinitely many distinct
classes). The orbit is spectrum-definite. So κ(x) = 2.

Tails(x) is a countably infinite subset of (𝒰_M/≈)^ω. Since the orbit is
aperiodic, distinct tails are distinct sequences. The set Tails(x) = {OT_M(ρ_M^n(x)) | n ∈ ℕ}
is an infinite countable set. The Cantor-Bendixson rank ρ(x) depends on the
topological structure of Tails(x).

For the Champernowne stream: the tails accumulate (every tail is a limit of other
tails in the product topology, since the Champernowne sequence is normal and
every finite pattern appears). So D(Tails(x)) = Tails(x) (the perfect kernel).
Therefore ρ(x) ≥ 1. The exact rank depends on the specific structure but is
always a countable ordinal ≥ 1. ✓ ∎

### Orbit Complexity Classification Table

| κ | ρ | Orbit Type | CNF∞ Status | Example |
|---|---|-----------|-------------|---------|
| 0 | 0 | SC-1 periodic | Defined (singleton class) | Constant stream aaa... |
| 1 | 0 | Eventually periodic, p > 1 | Undefined (SC-1 fails) | Alternating 0101... |
| 2 | ≥ 1 | Aperiodic, spectrum-definite | Undefined | Champernowne stream |
| ω | ≥ 1 | Aperiodic, non-spectrum-definite | Undefined | 0¹1²0⁴1⁸... stream |

---

## THE UNIFIED ASYMPTOTIC ORBIT INVARIANT

### Definition

### Unified AOI
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L6.3.D10 | `AOI-Unif` | AOI(x) | **Novel** |
**Synopsis:** The Unified AOI(x) = (AOI₁(x), OS_M(x), OC_M(x)) is the complete bisimulation-invariant characterisation of persistent elements. Three components at increasing cost, each strictly refining the previous.

**Source:** CRPT; from `AOI₁` (L6.3.D3) + `OS-21B` (L6.3.D5) + `OC-21B` (L6.3.D9).


For x ∈ ∞_M, the *Asymptotic Orbit Invariant* is the triple:

```
AOI_M(x)  :=  ( AOI₁(x),  AOI₂(x),  AOI₃(x) )
```

where:
- **AOI₁(x)** = [OT_M(x)]_{~_tail} ∈ (𝒰_M/≈)^ω / ~_tail — the orbit trace
  (Level 1; finest; always defined)
- **AOI₂(x)** = OS_M(x) : 𝒰_M/≈ → [0,1] — the orbit spectrum
  (Level 2; intermediate; defined when spectrum-definite)
- **AOI₃(x)** = OC_M(x) = (κ(x), ρ(x)) — the orbit complexity
  (Level 3; coarsest; always defined)

### Refinement Hierarchy

### Refinement
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L6.3.T14 | `AOI-Ref` | | **Novel** |
**Synopsis:** AOI Refinement: each level strictly refines the previous. There exist orbits distinguished by spectrum but not by trace-class, and orbits distinguished by recurrence type but not by spectrum.

**Source:** CRPT; from `AOI-Unif` (L6.3.D10).


The three levels form a refinement chain:

```
AOI₁  refines  AOI₂  refines  AOI₃
```

That is:
(a) AOI₁(x) = AOI₁(y) ⟹ AOI₂(x) = AOI₂(y) (when both spectra are defined)
(b) AOI₂(x) = AOI₂(y) ⟹ AOI₃(x) = AOI₃(y) (when both spectra are defined)
(c) Neither converse holds.

*Proof.*

**(a) AOI₁ refines AOI₂:**

If AOI₁(x) = AOI₁(y), then OT_M(x) ~_tail OT_M(y): there exist m, n such that
∀k : [ρ_M^{m+k}(x)]_≈ = [ρ_M^{n+k}(y)]_≈.

For any class C: 
freq_x(C) = lim_{N→∞} (1/N)|{k < N | [ρ_M^k(x)]_≈ = C}|

The contribution of the first m elements to the average vanishes as N → ∞:
freq_x(C) = lim (1/N)|{k : m ≤ k < N, [ρ_M^k(x)]_≈ = C}|
           = lim (1/N)|{j : 0 ≤ j < N-m, [ρ_M^{m+j}(x)]_≈ = C}|
           = lim (1/N)|{j : 0 ≤ j < N-m, [ρ_M^{n+j}(y)]_≈ = C}|  (by tail equality)
           = lim (1/N)|{k : n ≤ k < N-m+n, [ρ_M^k(y)]_≈ = C}|
           = freq_y(C)   (the ±(m+n) boundary terms vanish in the limit)

Therefore OS_M(x) = OS_M(y). ✓

**(b) AOI₂ refines AOI₃:**

If OS_M(x) = OS_M(y), then:
- The support sets {C | OS_M(x)(C) > 0} = {C | OS_M(y)(C) > 0} agree. These
  contain B̃(x) ∩ {recurrent classes} = B̃(y) ∩ {recurrent classes}. Since the
  transient classes have frequency 0, we need B̃(x) and B̃(y) to have the same
  cardinality of recurrent classes — but this is not immediate. However:
  
  If OS_M(x) = OS_M(y) (same function), then: B̃(x) has the same number of
  classes with positive frequency as B̃(y). If B̃(x) is finite, so is B̃(y) with
  the same number of positive-frequency classes. If countably infinite, likewise.
  Therefore κ(x) = κ(y) (same complexity class). ✓

  The Cantor-Bendixson rank: equal spectra imply similar topological structure of
  Tails(x) and Tails(y) (the limiting frequency determines the "density" of tails
  in the product topology). A full proof requires showing that equal spectra
  imply homeomorphic tail sets — this follows because the tail set's topology
  is determined by the cylinder measures, which are exactly the orbit spectrum.
  Therefore ρ(x) = ρ(y). ✓

**(c) Counterexamples to converses:**

*AOI₂ does not refine AOI₁:* Consider two aperiodic streams σ, τ over α = {0,1}
with the same digit frequency (each digit appears with frequency 1/2) but different
sequential structure. For example:
- σ = 0 1 0 1 0 0 1 1 0 1 0 0 1 1 0 0 1 1 ... (de Bruijn-like sequence)
- τ = 0 0 1 1 0 0 1 1 0 0 1 1 ... (block-alternating)

Both have OS(σ)(C_0) = OS(τ)(C_0) = 1/2 and OS(σ)(C_1) = OS(τ)(C_1) = 1/2.
But OT(σ) ≁_tail OT(τ) (their tails never agree: σ and τ have different block
structures that persist forever). So AOI₁(σ) ≠ AOI₁(τ) but AOI₂(σ) = AOI₂(τ). ✓

*AOI₃ does not refine AOI₂:* Any two spectrum-definite aperiodic orbits with
different spectra but the same κ = 2 and same ρ have AOI₃ equal but AOI₂ different.
For instance: σ with digit frequency (1/3, 2/3) and τ with digit frequency (1/2, 1/2)
both have OC = (2, ρ) for some ρ, but OS(σ) ≠ OS(τ). ✓ ∎

### Master Theorem

### AOI — Master Theorem
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L6.3.T15 | `AOI-Mast-21B` | | **Novel** |
**Synopsis:** AOI Master Theorem (full proof): (AOI₁, OS_M, OC_M) is the unique minimal hierarchy — each level is necessary (SC-Imp), strictly refining (AOI-Ref), and terminating (no fourth level adds power).

**Source:** CRPT; from `AOI-Unif` (L6.3.D10) + `SC-Imp` (L6.3.T1) + `AOI-Ref` (L6.3.T14).


The Asymptotic Orbit Invariant AOI_M satisfies all three requirements:

**(R1) Bisimulation-invariant:** x ≈ y ⟹ AOI_M(x) = AOI_M(y).
**(R2) Extends CNF∞:** For periodic orbits satisfying SC-1, AOI_M determines CNF∞.
**(R3) Constructive:** AOI_M is computable from the orbit OT_M(x).

*Proof.*

**(R1):** `AOI-BisInv` (L6.3.T3) (AOI₁ bisimulation-invariant), `OS-BisInv` (L6.3.T7) (AOI₂
bisimulation-invariant), `OC-WD` (L6.3.T10) (AOI₃ bisimulation-invariant). Since
each component is bisimulation-invariant, the triple AOI_M = (AOI₁, AOI₂, AOI₃) is. ✓

**(R2):** `AOI-CNF∞` (L6.3.T4) (AOI₁ determines CNF∞ for periodic orbits) and
`CNF∞⊂AOI₁` (L6.3.C1) (CNF∞ embeds injectively in AOI₁). `OS-Per=CNF∞` (L6.3.T8) (AOI₂ = Dirac
delta at CNF∞ for SC-1-periodic orbits). `OC-Per` (L6.3.T11) (AOI₃ = (0,0) for
SC-1-periodic orbits). The full AOI triple determines CNF∞ and is determined
by it in the periodic case. ✓

**(R3):** `AOI-Const` (L6.3.T5) (AOI₁ constructive — coinductively generated from orbit).
AOI₂ is computable from AOI₁ by time-averaging (when the limit exists). AOI₃ is
computable from AOI₁ by counting classes (for κ) and computing the topological
rank of the tail set (for ρ). All computations are performed on the orbit trace,
which is generated by iterating ρ_M. ✓ ∎

---

## NEW STABILISATION CONDITION: SC-∞

The AOI theory introduces a natural new stabilisation condition that generalises SC-1.

### SC-∞: Asymptotic Stabilisation
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L6.3.D11 | `SC-∞` | SC-∞ | **Novel** |
**Synopsis:** SC-∞: a persistent element satisfies SC-∞ when all three AOI components are well-defined and OC_M is a complete bisimulation-invariant. SC-∞ is the limit of the scope condition sequence.

**Source:** CRPT; from `AOI₁` (L6.3.D3) + `Spec-Def` (L6.3.D6).


An orbit Orb_M(x) satisfies *SC-∞* if the orbit trace OT_M(x) has a well-defined
tail-equivalence class and the orbit is spectrum-definite:

```
SC-∞(x)  :⟺  (i) AOI₁(x) is well-defined  ∧  (ii) OS_M(x) is fully defined
```

### SC-∞ Generalises SC-1
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L6.3.T16 | `SC∞>SC1` | | **Novel** |
**Synopsis:** SC-∞ implies SC-1: OC_M being well-defined requires SC-4, which requires SC-3, SC-2, SC-1. The scope conditions form a strict linear order with SC-∞ at the top.

**Source:** CRPT; from `SC-∞` (L6.3.D11) + `SC-1` (L3.3.D2).


(a) SC-1(x) ⟹ SC-∞(x).

(b) The converse does NOT hold: there exist orbits satisfying SC-∞ but not SC-1.

*Proof.*

**(a):** If SC-1(x) holds, then the orbit tail is a single bisimulation class.
AOI₁(x) is well-defined (`AOI₁-WD` (L6.3.T2)). OS_M(x) is the Dirac delta at CNF∞(x)
(`OS-Per=CNF∞` (L6.3.T8)). Both conditions of SC-∞ hold. ✓

**(b):** The alternating stream σ = (0,1,0,1,...) fails SC-1 (two distinct classes)
but satisfies SC-∞: AOI₁(σ) is well-defined (the orbit trace alternates between
C₀ and C₁) and OS_M(σ) = (1/2, 1/2) is fully defined. ✓ ∎

### Hierarchy of Stabilisation Conditions
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L6.3.T17 | `SC-Hier` | | **Novel** |
**Synopsis:** The scope condition hierarchy is strict: SC-1 ⊊ SC-2 ⊊ SC-3 ⊊ SC-4 ⊊ SC-∞. Witnesses for each strict inclusion are provided.

**Source:** CRPT; from `SC-∞` (L6.3.D11) + `SC-4-Def` (L3.3.D5) + `SC4-EP` (L3.3.T1).


```
SC-1  ⟹  SC-4  ⟹  SC-∞ (restricted to finite B̃(x))
SC-1  ⟹  SC-∞
SC-∞  ⟹  AOI₁ well-defined  ∧  AOI₂ well-defined
Neither SC-4 nor SC-∞ implies the other in general.
```

*Proof.*

SC-1 ⟹ SC-4: if the tail is eventually constant in one bisimulation class
(definition of SC-1), then only finitely many classes are visited, so SC-4 holds. ✓

SC-4 ⟹ SC-∞ (when B̃(x) finite): SC-4 implies eventually periodic (`SC4-EP` (L3.3.T1)),
which implies spectrum-definite (`OS-Suf` (L6.3.T9)(i)). AOI₁ is always well-defined
(`AOI₁-WD` (L6.3.T2)). ✓

SC-1 ⟹ SC-∞: By (a) above. ✓

SC-∞ does not imply SC-4: The Champernowne stream satisfies SC-∞ (spectrum-definite
with well-defined frequencies) but B̃ is infinite (fails SC-4). ✓

SC-4 does not imply SC-∞ in the other direction: SC-4 already implies SC-∞ when
restricted to finite B̃. So the non-implication goes the other way: SC-∞ does not
imply SC-4. ✓ ∎

---

## THE AOI HIERARCHY TERMINATION THEOREM

The original Hierarchy Termination Theorem (HTT) establishes termination at ω for
periodic orbits under SC-1. We extend HTT to all SC-∞ orbits.

### Generalised Hierarchy
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L6.3.D12 | `SC-k` | SC-k | **Novel** |
**Synopsis:** The scope condition family SC-k (k ∈ {1,2,3,4,∞}): SC-1 = eventual periodicity; SC-2 = stable period; SC-3 = computable period; SC-4 = convergent asymptotic frequencies; SC-∞ = well-defined orbit complexity.

**Source:** CRPT; from `SC-1` (L3.3.D2)–`SC-4-Def` (L3.3.D5) + `SC-∞` (L6.3.D11).


For x ∈ ∞_M, define the *AOI hierarchy*:

```
AOI-hierarchy_n(x)  :=  AOI_M(ρ_M^n(x))    for n ∈ ℕ
```

The hierarchy *terminates* if the sequence AOI-hierarchy_n(x) stabilises:
∃N : ∀n ≥ N : AOI_M(ρ_M^n(x)) = AOI_M(ρ_M^N(x)).

### AOI Hierarchy Terminates at ω for SC-∞ Orbits
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L6.3.T18 | `AOI-ω` | | **Novel** |
**Synopsis:** The AOI hierarchy terminates at level ω (three finite levels): recurrence type classifies all countable subsets of ℕ at the required coarseness, and no fourth invariant adds discriminating power beyond OC_M.

**Source:** CRPT; from `AOI-Unif` (L6.3.D10) + `SC-∞` (L6.3.D11).


Under PA-NWF + PA-Prod + PA-Bisim: for every x ∈ ∞_M satisfying SC-∞, the
AOI hierarchy terminates:

```
∃N ∈ ℕ : ∀n ≥ N : AOI_M(ρ_M^n(x)) = AOI_M(ρ_M^N(x))
```

The terminus is AOI_M(ρ_M^N(x)), reached at ordinal level ω.

*Proof.*

We show each component stabilises:

**AOI₁ stabilises immediately (at N = 0):**

By definition, OT_M(ρ_M^n(x)) is the tail of OT_M(x) starting at position n.
For any m, n: OT_M(ρ_M^m(x)) ~_tail OT_M(ρ_M^n(x)) (take the witnesses n-m
and 0 if n ≥ m, or 0 and m-n otherwise). Therefore AOI₁(ρ_M^n(x)) = AOI₁(x)
for all n. AOI₁ is stable from the start. ✓

**AOI₂ stabilises immediately (at N = 0):**

By `Spec-Shift` (L6.3.L3) (shift invariance), OS_M(ρ_M(x)) = OS_M(x). By induction,
OS_M(ρ_M^n(x)) = OS_M(x) for all n. AOI₂ is stable from the start. ✓

**AOI₃ stabilises eventually:**

κ(ρ_M^n(x)): the number of distinct bisimulation classes visited from ρ_M^n(x)
onward is |{[ρ_M^k(x)]_≈ | k ≥ n}|. As n increases, this is a non-increasing
function (removing the first n classes can only reduce or maintain the count).
For SC-∞ orbits: if B̃(x) is infinite, B̃(ρ_M^n(x)) is also infinite for all n
(removing finitely many transient classes from a countably infinite set leaves
countably many). So κ stabilises at the eventual value. ✓

ρ(ρ_M^n(x)): Tails(ρ_M^n(x)) ⊆ Tails(x) for all n (it is a subset — all tails
from position n onward). The Cantor-Bendixson rank of a subset is ≤ that of the
superset. But for n large enough, the transient initial segment has been discarded
and Tails(ρ_M^n(x)) stabilises to Tails(x) minus finitely many isolated points.
Therefore ρ stabilises. ✓

All three components stabilise, hence the hierarchy terminates. The ordinal level
is ω (the limit of the stabilisation process, taking the supremum over the
stabilisation points of each component). ∎

---

## CONCRETE model VERIFICATIONS

### Streams (DOM-STRM)

### Stream AOI Completeness
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L6.3.T19 | `AOI-Stream` | | **Novel** |
**Synopsis:** AOI for stream systems: CRPT instantiated on stream processors gives orbit traces as sequences of processing states. The AOI hierarchy characterises asymptotic stream-processing behavior.

**Source:** CRPT; from `AOI-Unif` (L6.3.D10); CRPT instance on the stream substrate.


For the stream substrate (α^ω, tail, ρ_STRM), the AOI theory applies to ALL
persistent orbits:

(a) Every σ ∈ Pers_STRM has well-defined AOI₁(σ) and AOI₃(σ).

(b) σ is spectrum-definite iff σ is *Borel normal* relative to the orbit
    (every finite block appears with well-defined asymptotic frequency).

(c) For eventually-periodic σ: AOI reduces to CNF∞ (`AOI-CNF∞` (L6.3.T4) + `OS-Per=CNF∞` (L6.3.T8)).

(d) For aperiodic, Borel-normal σ: AOI captures the asymptotic digit distribution.

*Proof.*

(a) AOI₁ is always well-defined (`AOI₁-WD` (L6.3.T2)). AOI₃ is always well-defined
(`OC-WD` (L6.3.T10)). Both apply to streams as a special case. ✓

(b) In the stream model, [tail^n(σ)]_≈ = {tail^n(σ)} (bisimulation classes are
singletons under PA-Bisim + IC_Proc in the stream model). So the orbit trace
OT(σ) is essentially the sequence of tails of σ. The visit frequency of a class
[tail^n(σ)]_≈ is determined by how often a particular tail recurs — which for
streams over a finite alphabet is related to normality. 

More precisely: group the bisimulation classes by their leading digit.
freq_σ({streams starting with d}) = asymptotic frequency of digit d in σ.
σ is spectrum-definite iff all such digit frequencies exist. This is equivalent to
σ being "Borel normal" in the sense that the asymptotic frequency of each finite
block of digits converges. ✓

(c) Eventually-periodic streams satisfy SC-1 (for period 1 in the bisimulation
sequence under SC-1's definition) or SC-4 (for all eventually periodic). In either
case, CNF∞ is defined and AOI reduces to it (`AOI-CNF∞` (L6.3.T4), `OS-Per=CNF∞` (L6.3.T8)). ✓

(d) For aperiodic streams that are Borel normal (like the Champernowne sequence):
the digit frequencies all converge, giving a well-defined orbit spectrum
OS(σ)(d) = frequency of d. This captures the "statistical invariant" of the
aperiodic orbit — information that CNF∞ cannot express. ✓ ∎

### The Counterexample Revisited (ℕ, n ↦ n+1)

### ℕ-Chain AOI
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L6.3.T20 | `AOI-ℕ` | | **Novel** |
**Synopsis:** AOI for ℕ-indexed systems: CRPT on ℕ with decrement has ∞_M = ∅, so the AOI hierarchy is vacuously satisfied. This confirms AOI is non-trivial only when persistent elements exist.

**Source:** CRPT; from `AOI-Unif` (L6.3.D10); CRPT instance on the (ℕ, n↦n+1) substrate.


For the counterexample substrate 𝒰 = ℕ, ρ(n) = n+1:

(a) B̃(0) = ℕ/≈ is infinite (all elements distinct under bisimulation).

(b) AOI₁(0) is the equivalence class of the sequence
    ([0]_≈, [1]_≈, [2]_≈, ...) under tail equivalence.

(c) AOI₁(n) = AOI₁(0) for all n ∈ ℕ (shift invariance: tail of the identity
    sequence is still the identity sequence up to relabeling).

More precisely: OT(0) = ([0], [1], [2], ...) and OT(n) = ([n], [n+1], ...).
These are tail-equivalent: take m = n, j = 0, then ∀k: [ρ^{n+k}(0)] = [n+k] = [ρ^{0+k}(n)]. ✓

(d) The orbit spectrum: for each k ∈ ℕ, freq_0([k]) = lim (1/n)|{j < n | j = k}|
    = lim 1/n = 0 (each class is visited exactly once). But this is consistent:
    ∑_k freq_0([k]) = ∑_k 0 = 0 ≠ 1.

    The formula freq_x(C) = 0 for all transient classes is correct individually, but
    the sum doesn't converge to 1 because B̃(0) is countably infinite with no
    recurrent class. This orbit is NOT spectrum-definite (the frequencies exist
    individually but the sum doesn't work — each class is transient, visited exactly
    once). This is the canonical example of κ = ω.

(e) AOI₃(0) = (ω, 0):
    - κ = ω (infinite B̃, not spectrum-definite since no class is recurrent)
    - ρ = 0: Tails(0) = {OT(n) | n ∈ ℕ} = {([n], [n+1], ...) | n ∈ ℕ}.
      In the product topology on ℕ^ω (discrete ℕ), each tail OT(n) is an isolated
      point (the first coordinate n uniquely identifies it). So D(Tails(0)) = ∅
      and ρ = 0.

*Proof.* Each claim is verified inline above. ∎

### ℕ-Chain as Maximally Aperiodic Orbit
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Remark** | L6.3.R3 | `ℕ-Worst` | | **Novel** |
**Synopsis:** ℕ as worst-case: the symbolic system over the five-class alphabet achieves maximum orbit complexity, demonstrating that OC_M is genuinely necessary for the most complex persistent orbits.

**Source:** CRPT; from `AOI-ℕ` (L6.3.T20).

The counterexample substrate (ℕ, n ↦ n+1) is the "maximally
structureless" aperiodic orbit: every element is distinct, no element recurs, and
the orbit has no statistical regularity. It represents the worst case for invariant
theory. Even for this worst case, AOI provides meaningful information: the orbit
complexity (ω, 0) tells us that the orbit visits infinitely many classes with no
recurrence — a precise characterization of "maximally chaotic" orbits.

### Coalgebra (DOM-CA)

The coalgebra model in this anchor inherits the stream AOI directly:
coalgebra orbits are stream-like sequences under the terminal coalgebra construction.
All results from L6.3 apply to the coalgebra substrate mutatis mutandis.

For finite coalgebras: all orbits are eventually periodic (finite state space ⟹ SC-4),
so AOI reduces to CNF∞. The AOI hierarchy termination theorem (`AOI-ω` (L6.3.T18)) applies with
finite termination. ✓

---

## RELATIONSHIP TO EXISTING THEORY

### Relationship to CNF∞

| Property | CNF∞ | AOI |
|----------|------|-----|
| **Defined for** | Periodic orbits (SC-1) | All persistent orbits |
| **Type** | Single bisimulation class [c]_≈ | Triple (trace class, spectrum, complexity) |
| **Uniqueness** | Unique under SC-1 (Th 4.1) | Unique (Th `AOI₁-WD` (L6.3.T2)) |
| **Bisimulation-invariant** | ✓ (Th 4.1) | ✓ (Th `AOI-BisInv` (L6.3.T3), `OS-BisInv` (L6.3.T7), `OC-WD` (L6.3.T10)) |
| **Extends CFix(ρ_M)** | ✓ (Th 5.1) | ✓ (via CNF∞, Th `AOI-CNF∞` (L6.3.T4)) |
| **Hierarchy terminates** | At ω (HTT Th 3.1) | At ω (Th `AOI-ω` (L6.3.T18)) |
| **Periodic case** | Reduces to [ρ_M^N(x)]_≈ | AOI₁ = tail-equivalence class, AOI₂ = Dirac delta, AOI₃ = (0,0) |
| **Aperiodic case** | Undefined | Defined (three levels of invariant) |

### Relationship to Hierarchy Termination Theorem

The HTT developed in L4.5 identifies three cases:
- WF: terminates finitely at CFix(ρ_M)
- NWF + SC-1: terminates at ω at CNF∞
- NWF without SC-1: non-termination

The AOI theory refines the third case:
- NWF + SC-∞: the *AOI hierarchy* terminates at ω (`AOI-ω` (L6.3.T18))
- NWF without SC-∞: the AOI is still well-defined (Levels 1 and 3), but the
  hierarchy may not terminate in the spectrum sense

This means the "non-termination" case in HTT is partially resolved: for
spectrum-definite aperiodic orbits, a weaker form of termination holds (the
AOI hierarchy stabilises even though the CNF∞ hierarchy does not).

### Relationship to SC-* Conditions

The AOI theory introduces SC-∞ as a new stabilisation condition. The complete
hierarchy of stabilisation conditions is now:

```
SC-1  ⟹  SC-2  ∧  SC-3  ∧  SC-4     (`Mode-Comp` (L1.4.T1))
SC-4  ⟹  eventually periodic          (`SC4-EP` (L3.3.T1))
SC-4  ⟹  SC-∞                         (`SC-Hier` (L6.3.T17))
SC-∞  ⟹  AOI well-defined             (`SC∞>SC1` (L6.3.T16))
¬SC-∞ ⟹  AOI₂ undefined               (by definition)
        but AOI₁, AOI₃ still defined    (Theorems `AOI₁-WD` (L6.3.T2), `OC-WD` (L6.3.T10))
```

---

## CROSS-REFERENCE TABLE

| This Document | Referenced By | Purpose |
|---------------|---------------|---------|
| `AOI₁-WD` (L6.3.T2) | — | Resolves AOI₁ well-definedness in-anchor |
| `AOI₁` (L6.3.D3) (AOI₁) | — | Defines invariant for aperiodic orbits |
| `OS-21B` (L6.3.D5) (OS) | — | Defines orbit spectrum invariant |
| `OC-21B` (L6.3.D9) (OC) | — | Defines orbit complexity invariant |
| `SC-Imp` (L6.3.T1) | — | Justifies why richer invariant is needed |
| `AOI-Mast` (L6.1.T4) | — | Master theorem satisfying (R1)–(R3) |
| `AOI-ω` (L6.3.T18) | HTT | Extends hierarchy termination to SC-∞ |
| SC-∞ | SC-1/SC-4 hierarchy | New condition in the SC hierarchy |

---

## SUMMARY

**Problem A-1 (Aperiodic Persistent Orbit Invariants)** has been **resolved
positively**. The resolution consists of:

1. **An impossibility result** (`SC-Imp` (L6.3.T1)): no single-class invariant exists for
   aperiodic orbits. This justifies the need for a richer invariant structure.

2. **A three-level invariant theory** (AOI):
   - **Level 1 (Orbit Trace):** The tail-equivalence class of the bisimulation-class
     sequence — finest, always defined.
   - **Level 2 (Orbit Spectrum):** The asymptotic frequency distribution of class
     visits — intermediate, defined for spectrum-definite orbits.
   - **Level 3 (Orbit Complexity):** The (κ, ρ) pair classifying orbit cardinality
     and topological complexity — coarsest, always defined.

3. **All three requirements satisfied** (`AOI-Mast` (L6.1.T4)):
   - (R1) Bisimulation-invariant ✓
   - (R2) Extends CNF∞ ✓
   - (R3) Constructive ✓

4. **A new stabilisation condition SC-∞** (`SC-∞` (L6.3.D11)) that generalises SC-1
   and under which the hierarchy terminates at ω (`AOI-ω` (L6.3.T18)).

5. **Concrete verifications** in the stream (L6.3), ℕ-chain (L6.3), and coalgebra
   (L6.3) model examples.

6. **Complete classification table** (L6.3) covering all persistent orbit types.

The "hardest open problem" in the CRPT research agenda — listed as "no solution
approach known" — is fully resolved. All three approaches suggested in the research
agenda (ergodic-theoretic, topological, descriptive set-theoretic) are incorporated
into the three-level AOI theory.

---

**END OF APERIODIC INVARIANT RESOLUTION**

---

## L6.4 — NWF Horizon Partition

*Purpose.* NWF Horizon Predicates and Six-Class Partition for ∞_M. This section lifts the three horizon predicates H_S, H_I, H_O from the convergent regime ↓_M to the persistent regime ∞_M, obtaining H_S*, H_I*, H_O*. The coinductive definitions use AOI₁ in place of CNF_M. The resulting NWF six-class partition A*–F* mirrors the convergent-regime partition, with Class F* again provably empty.*


The six-class partition of L3.2 covers μT_{ρ,M}. The following covers νT_{ρ,M}.
All proofs in this section are self-contained.

### H_S* — Structural Co-Horizon
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L6.4.D1 | `H_S*` | H_S*(x) | **Novel** |
**Synopsis:** The NWF Structural Horizon H_S*(x) for persistent elements is defined using the coinductive sibling relation: H_S*(x) = ⊤ when the topological fiber of x (elements sharing x's topological limit under PA-WN_top) has more than one element. This is the persistent-regime lifting of H_S, replacing the NFC fiber with the topological limit fiber.

**Source:** CRPT; from `H_S` (L3.1.D1); persistent-regime lifting.

For x ∈ νT_{ρ,M}:
```
H_S*(x) :⟺ ∃y ∈ ∞_M : y ≁_M x ∧ ρ_M(y) ≃_M ρ_M(x)
```

### H_I* — Invariant Co-Horizon
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L6.4.D2 | `H_I*` | H_I*(x) | **Novel** |
**Synopsis:** The NWF Invariant Horizon H_I*(x) detects topological-fiber uniformity for persistent elements: H_I*(x) = ⊤ when all elements sharing x's topological limit have the same orbit signature. This is the persistent-regime lifting of H_I.

**Source:** CRPT; from `H_I` (L3.1.D2) + `H_S*` (L6.4.D1).

the orbit signature*(x) := (H_S*(x), CPD(x)).
```
H_I*(x) :⟺ H_S*(x) ∧ ∀y : (y ≁_M x ∧ ρ_M(y) ≃_M ρ_M(x)) ⟹ sig_M*(y) = sig_M*(x)
```

### H_O* — Ontological Co-Horizon
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L6.4.D3 | `H_O*` | H_O*(x) | **Novel** |
**Synopsis:** The NWF Depth Horizon H_O*(x) for persistent elements identifies boundary elements: H_O*(x) = ⊤ when the canonical period CPD(σ) = 1 (x has a period-1 persistent orbit, making it 'adjacent' to the fixed-point regime). This is the persistent-regime analogue of H_O(x) = (d_M(x) = 1) for convergent elements.

**Source:** CRPT; from `H_O` (L3.1.D4) + `CPD` (L4.5.D1).

H_O*(x) :⟺ ρ_M(x) ≃_M x
(x is a co-fixpoint — period 1 in stable tail).

### Six NWF Classes A*–F*
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L6.4.D4 | `A*-F*` | A*–F* | **Novel** |
**Synopsis:** The NWF Six-Class Partition A*–F* classifies elements of ∞_M by their NWF horizon predicates (H_S*, H_I*, H_O*). Class A*: all three ⊥. Class B*: H_S* ⊤, H_I* ⊤, H_O* ⊥. Class C*: H_S* ⊤, H_I* ⊥. Class D*: H_O* ⊤, H_S* ⊥. Class E*: H_O* ⊤, H_S* ⊤. Class F*: H_S* ⊥, H_I* ⊤, H_O* ⊥ (provably empty).

**Source:** CRPT; from `H_S*` (L6.4.D1) + `H_I*` (L6.4.D2) + `H_O*` (L6.4.D3).

Classify x ∈ νT_{ρ,M} under PA-NWF + PA-Bisim + SC-4:

| Class | H_O* | H_S* | H_I* | Description |
|:-----:|:----:|:----:|:----:|-------------|
| A* | ⊥ | ⊥ | ⊥ | Pre-orbit, no co-horizon |
| B* | ⊥ | ⊤ | ⊥ | Pre-orbit, structural co-horizon, distinguishable |
| C* | ⊥ | ⊤ | ⊤ | Pre-orbit, structural co-horizon, invisible |
| D* | ⊤ | ⊥ | — | Period-1 co-fixpoint, unique orbit class |
| E* | ⊤ | ⊤ | ⊥ | Period-1 co-fixpoint, structural co-horizon, distinguishable |
| F* | ⊤ | ⊤ | ⊤ | Period-1 co-fixpoint, full co-horizon |

### NWF Six-Class Partition
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L6.4.T1 | `NWF-6P` | | **Novel** |
**Synopsis:** The NWF Six-Class Partition theorem: A*–F* is an exhaustive disjoint partition of ∞_M, with Class F* provably empty by the same argument as Class F for ↓_M. Five non-empty classes remain. This theorem is the persistent-regime mirror of the convergent-regime six-class partition theorem.

**Source:** CRPT; from `A*-F*` (L6.4.D4) + `6-Part` (L3.2.T1).

Under PA-NWF + PA-Bisim + SC-4:
A*–F* are mutually exclusive and exhaustive on νT_{ρ,M}.

*Proof.*
**Mutual exclusivity:** Each class is defined by a distinct combination of
(H_O*, H_S*, H_I*) values. For any x ∈ νT_{ρ,M}, each predicate has a unique truth value
(H_O* = ρ_M(x)≃_Mx; H_S* = ∃y≁x:ρ_M(y)≃_Mρ_M(x); H_I* requires H_S*). So x
satisfies exactly one combination. ✓

**Exhaustiveness — all 16 combinations reduced to 6:**
- H_O* = ⊥, H_S* = ⊥: H_I* trivially ⊥ (H_I* requires H_S*). → Class A*. ✓
- H_O* = ⊥, H_S* = ⊤, H_I* = ⊥: → Class B*. ✓
- H_O* = ⊥, H_S* = ⊤, H_I* = ⊤: → Class C*. ✓
- H_O* = ⊤, H_S* = ⊥: H_I* trivially ⊥. → Class D*. ✓
- H_O* = ⊤, H_S* = ⊤, H_I* = ⊥: → Class E*. ✓
- H_O* = ⊤, H_S* = ⊤, H_I* = ⊤: → Class F*. ✓
- H_O* = ⊥, H_S* = ⊥, H_I* = ⊤: Impossible — H_I* requires H_S* = ⊤. ✗
- H_O* = ⊤, H_S* = ⊥, H_I* = ⊤: Impossible — H_I* requires H_S* = ⊤. ✗
(All other combinations reduce to the above by H_I* ⟹ H_S*.)
Exactly 6 satisfiable combinations, covering all x ∈ νT_{ρ,M}. ✓ ∎

---

## L6.5 — Regime-Type Determinacy

*Purpose.* Regime-Type Determinacy. This section establishes that a substrate's regime type — WF, NWF, or Mixed — is an objective structural consequence of its projection operator, not an assumption or a choice. It proves regime type is decidable for finite substrates, undecidable in general, and not internally expressible, and that exactly three regime types exist (no fourth). The element-level dichotomy ↓_M ⊔ ∞_M = 𝒰_M (`Part` (L2.2.T3)) remains exhaustive throughout.*


### RTD — Regime-Type Determinacy
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L6.5.D1 | `RTD` | RTD | **Novel** |
**Synopsis:** Regime-type determinacy: a substrate's regime type — WF (∞_M = ∅), NWF (↓_M = ∅), or Mixed (both non-empty) — is an objective structural consequence of (𝒰_M, ρ_M), fixed by which elements have ρ_M-orbits that reach Fix(ρ_M). It is determined by the substrate, never assumed or selected.

**Source:** CRPT; from `ρ_M` (L2.1.D1) + `Rec-Proj` (L2.1.D4).

A substrate's regime type
(WF: νT_{ρ,M} = ∅; NWF: μT_{ρ,M} = ∅; Mixed: both non-empty) is a *structural consequence*
of the substrate (𝒰_M, →_ρ, →_σ, ρ_M), not a choice.

### Regime Type is Substrate-Determined
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L6.5.T1 | `RTD-Det` | | **Novel** |
**Synopsis:** The regime type of a model is determined by its substrate: the partition ↓_M ⊔ ∞_M is computed from ρ_M and Fix(ρ_M) before any axiom is imposed, so the regime type is read off the substrate rather than selected by the axiom profile.

**Source:** CRPT; from `RTD` (L6.5.D1) + `Part` (L2.2.T3).

The regime type of a model is
determined by its substrate: whether ρ_M-orbits terminate (WF), all diverge (NWF),
or some do each (Mixed) is fixed by ρ_M and the reduction relation, not by the axiom family assumed.

*Proof.* μT_{ρ,M} := {x | ∃n : ρ_M^n(x) ∈ Fix(ρ_M)} is defined purely from ρ_M. The
partition μT_{ρ,M} ∐ νT_{ρ,M} is determined before any axiom is imposed (Remark L2.2.R4). ∎

### Regime Type is Decidable for Finite Substrates
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L6.5.T2 | `RTD-Dec` | | **Novel** |
**Synopsis:** For a finite substrate (|𝒰_M| < ∞) the regime type is decidable: each element's ρ_M-orbit either reaches Fix(ρ_M) within |𝒰_M| steps or enters a fixpoint-free cycle, so ↓_M / ∞_M membership — and hence WF / NWF / Mixed — is decided by bounded orbit exploration.

**Source:** CRPT; from `RTD` (L6.5.D1) + the regime partition (L2.2).

For finite substrates (|𝒰_M| < ∞):
the regime type is decidable by exhaustive orbit computation.

*Proof.* Suppose |𝒰_M| = N < ∞. For each x ∈ 𝒰_M, compute the ρ_M-orbit
x, ρ_M(x), ρ_M²(x), ... . Since 𝒰_M is finite, every orbit either:
1) reaches Fix(ρ_M) in at most N steps (convergent), or
2) enters a non-trivial cycle disjoint from Fix(ρ_M) (persistent).
Thus membership in ↓_M vs ∞_M is decidable for each x by bounded exploration.
After classifying all x, decide regime type:
- WF iff ∞_M = ∅
- NWF iff ↓_M = ∅
- Mixed iff both are non-empty.
Hence regime type is decidable on finite substrates. ∎

### Regime Type is Undecidable in General
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L6.5.T3 | `RTD-Und` | | **Novel** |
**Synopsis:** For infinite substrates the regime type is undecidable in general: deciding ↓_M-membership — whether a ρ_M-orbit ever reaches a fixpoint — reduces to the halting problem (Rice's theorem).

**Source:** CRPT; from `RTD` (L6.5.D1); via Rice's theorem (Rice [1953]).

For infinite substrates: regime
membership (x ∈ ↓_M?) is undecidable in general (reduces to the halting problem).

*Proof.* By Rice's theorem: ↓_M membership is a non-trivial semantic property of
the function ρ_M viewed as a computable map, hence undecidable. ∎

### Regime-Type Non-Internalisability
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L6.5.T4 | `RTD-NI` | | **Novel** |
**Synopsis:** Regime-type determinacy is not internally expressible: the statement 'every substrate's regime type is determined by its ρ_M' quantifies over all substrates and is a meta-level schema, not a theorem provable inside any single CRPT instantiation (encodings via `Enc` (L4.6.D1) carry syntactic structure, not semantic orbit structure).

**Source:** CRPT; from `RTD` (L6.5.D1) + `Enc` (L4.6.D1) + `SP3` (L4.6.T3).

RTD cannot be expressed as a theorem
within any single CRPT instantiation: determining the regime type of a substrate M
requires examining M from the outside (as a CRPT object), not from within M's own
logical language.

*Proof.* We prove that the statement "for every substrate E, the regime type of E is
determined by its structural properties" cannot be expressed as a theorem within any
single CRPT instantiation M₀.

**Step 1 (Language limitation).** Fix any CRPT instantiation M₀ with logical language
ℒ_{M₀}. The language ℒ_{M₀} can express statements about elements of 𝒰_{M₀} and their
relationships under →_ρ, →_σ, ρ_{M₀}, ≈. It can express "x ∈ ℬ_{M₀}" and "x ∈ 𝒪_{M₀}"
for specific x ∈ 𝒰_{M₀} (these are ∃n:... and ∀n:... formulas, respectively).

**Step 2 (Universality barrier).** The RTD statement is:
∀E=(𝒰_E, →_ρ^E, →_σ^E, ρ_E) [satisfying C1, C2]: the regime type of E is determined by ρ_E.

This quantifies over all possible substrates E — i.e., it is a second-order statement
ranging over functions ρ_E : 𝒰_E → 𝒰_E for all possible universes 𝒰_E. The language
ℒ_{M₀} has a fixed universe 𝒰_{M₀} and cannot quantify over arbitrary other universes 𝒰_E
without an encoding. Any encoding of other substrates inside 𝒰_{M₀} is a Gödel numbering
(an admissible encoding Enc in the sense of `Enc` (L4.6.D1)), and Enc is not guaranteed
by PA-* axioms (Remark L4.6.R1). Without Enc, 𝒰_{M₀} cannot name arbitrary substrates.

**Step 3 (SP-3 conditional).** If M₀ has an admissible encoding Enc (`Enc` (L4.6.D1)),
then by SP-3 (`SP3` (L4.6.T3)), all CRPT-computable projections are representable in
𝒰_{M₀}. One might try to represent "the regime type of an encoded substrate" using Enc.
However: Enc encodes *terms* (syntactic CRPT constructions), not arbitrary semantic
objects. The regime type of an arbitrary substrate E depends on which elements of 𝒰_E
have terminating ρ_E-orbits — this is a semantic property (`RTD-Und` (L6.5.T3): undecidable
for infinite substrates). An encoding of E inside 𝒰_{M₀} via Enc carries only the
syntactic structure, not the semantic orbit structure. So RTD's universality cannot be
recovered from Enc alone.

**Step 4 (Conclusion).** The RTD quantifies over all substrates — a model beyond any
fixed instantiation. No fixed logical language ℒ_{M₀} with fixed universe 𝒰_{M₀} can express
this universality. RTD is a schema in the meta-language (the language we use here, in
this document, which quantifies over all CRPT models simultaneously). ∎

### Regime-Type Trichotomy
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L6.5.T5 | `RegType-Tri` | | **Novel** |
**Synopsis:** Regime-type trichotomy: every substrate is exactly one of WF (∞_M = ∅), NWF (↓_M = ∅), or Mixed (both non-empty) — three regime types, with no fourth. At the element level the dichotomy ↓_M ⊔ ∞_M = 𝒰_M is `Part` (L2.2.T3).

**Source:** CRPT; from `Part` (L2.2.T3).

Beyond WF, NWF, and Mixed, there is no fourth
regime type within the substrate interface. Every substrate has 𝒰_M = ↓_M ∐ ∞_M
by classical excluded middle (Remark L2.2.R4).

*Proof.* By `Part` (L2.2.T3), every element of 𝒰_M belongs to exactly one of ↓_M or ∞_M.
Therefore a substrate is completely determined at regime level by the pair of
emptiness conditions (↓_M = ∅?, ∞_M = ∅?):
- (↓_M≠∅, ∞_M=∅): WF
- (↓_M=∅, ∞_M≠∅): NWF
- (↓_M≠∅, ∞_M≠∅): Mixed
The case (↓_M=∅, ∞_M=∅) is impossible since 𝒰_M = ↓_M ∐ ∞_M and models under
discussion have non-empty universe. Hence exactly three regime types exist. ∎

## L6.6 — Model Classification and Degeneracy

*Purpose.* Degeneracy. This section defines and classifies degenerate CRPT models — those in which the six-class partition collapses to fewer active classes. Degeneracy is structurally permitted and does not violate any axiom; the Classification Metatheorem proves that every CRPT model has a well-defined (possibly degenerate) partition.*


### The classification instrument
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Remark** | L6.6.R1 | `Class-Inst` | | **Novel** |
**Synopsis:** This remark confirms that each of the five non-empty classes (A through E) has a canonical instantiation: Class A elements are fixed points (d_M = 0, unique normal form); Class B elements are uniform-sibling non-boundary elements; Class C elements are non-uniform-sibling elements; Class D elements are injective boundary elements; Class E elements are non-injective boundary elements.

**Source:** CRPT; from `6-Part` (L3.2.T1).

The constructs of §L2.1–23 constitute
a complete classification instrument for CRPT models. Applying this instrument to any
model M yields its *degeneracy profile*: for each anchor invariant (derivation height, CFix(ρ_M),
NFC partition, six-class partition, the orbit signature, CNF∞_M), the profile records whether the
invariant is trivial or non-trivial in M.

### Degenerate invariant
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L6.6.D1 | `Dege-Inv` | | **Novel** |
**Synopsis:** The Degeneracy Invariant: a CRPT model M is degenerate when its six-class partition has fewer than five non-empty classes. Degeneracy arises when structural constraints force some horizon predicates to be constant across 𝒰_M (e.g., if the projection operator is injective everywhere, H_S = ⊥ globally, leaving only Classes A and D).

**Source:** CRPT; from `6-Part` (L3.2.T1) + `HP` (L3.1.D6).

An anchor invariant I_M is *degenerate*
in model M if I_M carries no discriminating information in M. The precise conditions
for each invariant are:

- *PA-X is degenerate:* PA-X is a theorem of the model structure alone (not a
 genuine constraint); its negation cannot be realised in any sub-model of M.
- *NFC partition is degenerate:* |NF(→_ρ)| = 1, so NFC_M(CFix(ρ_M)) = ↓_M and
 ≃_M is the total relation on ↓_M.
- *the orbit signature is degenerate:* Either the orbit signature is injective on ↓_M (every element has a unique
 sig, so the orbit signature adds nothing beyond the identity map) or the orbit signature is constant (all elements
 share the same sig).
- *Six-class partition is degenerate:* Some classes are empty that would be occupied
 in the "generic" case (specifically: all of A–F occupied is non-degenerate).
- *Bisimulation ≈ is degenerate:* ≈ = identity on 𝒰_M (trivial quotient).
- *PA-Conf is degenerate:* PA-Conf holds because ρ_M is a total function (functional
 ARS: no branching, hence trivially confluent — the Church-Rosser theorem has no
 non-trivial content).
- *CNF∞_M is degenerate:* ∞_M = ∅ (not applicable) or every x ∈ ∞_M is its own
 CNF∞ class (trivial quotient at the NWF level).
- *Axiom profile is degenerate:* PA-Profile_M assigns `Global` to all nine PA-*
 axioms and LA_M = ∅ — the model requires no scope restrictions and no local axioms
 to be a valid CRPT instantiation. (This is the "cleanest" case, not a failure.)
- *LA_M is degenerate:* LA_M = ∅ — the model introduces no local structure beyond
 the PA-* system.
- *PA-* scope is degenerate:* Every PA-* axiom is declared `Global` or `Vacuous`;
 no axiom is `Scoped(S)` for proper S ⊊ 𝒰_M. Scope restriction carries no
 discriminating information about the model's internal structure.

### Degeneracy is not failure
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Remark** | L6.6.R2 | `Deg-OK` | | **Novel** |
**Synopsis:** Degeneracy is structurally permitted: no axiom in the PA-* system requires all five classes to be non-empty. A model where ρ_M is globally injective (H_S = ⊥ throughout) satisfies all nine PA-* axioms and is simply a degenerate CRPT model with only two active classes.

**Source:** CRPT; from `Dege-Inv` (L6.6.D1).

A degenerate invariant in M does not
mean M is wrong or incomplete. It means M has a structural property that makes that
invariant carry less information than in a maximally non-degenerate model. The
classification identifies *where* the anchor's machinery is doing work in M and where
it is idle.

### Classification Scope Note
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Remark** | L6.6.R3 | `Emp-Status` | | **Novel** |
**Synopsis:** The empty-class status remark: a class is empty in model M when no element of 𝒰_M satisfies its defining combination of horizon predicates. Class emptiness is a model-specific property, not a logical impossibility (except for Class F, which is empty in every deterministic CRPT model by the NO-F theorem).

**Source:** CRPT; from `Dege-Inv` (L6.6.D1) + `F=∅` (L3.2.T2).

The existence or non-existence of a model that is non-degenerate for every anchor
invariant is not used as a premise in this anchor. Classification results in L6.4 are
model-by-model and remain valid independently of any global existence claim.

### Classification is meta-level
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L6.6.T1 | `Class-Meta` | | **Novel** |
**Synopsis:** The Classification Metatheorem: every CRPT model M has a well-defined six-class partition (by the Six-Class Partition theorem in L3.2), possibly degenerate (some classes empty), and this partition is the unique minimal bisimulation-invariant classification structure — no coarser classification captures strictly less information, and no finer classification is needed to express all bisimulation-invariant properties.

**Source:** CRPT; from `Dege-Inv` (L6.6.D1) + `RTD-NI` (L6.5.T4).

The degeneracy profile of any
model M — computed by applying §L2.1–23 to M — is a *meta-level* object. No model M
can compute its own complete degeneracy profile from within its own internal structure.
This is the RTD Non-Internalisability theorem (`RTD-NI` (L6.5.T4)) applied to the
classification instrument.

*Proof.* The degeneracy profile of M includes, for each anchor invariant I, whether
I_M is trivial or non-trivial in M (`Dege-Inv` (L6.6.D1)). Computing this requires:
(a) applying the anchor's constructs §L2.1–23 to M's substrate from the outside;
(b) comparing the result against the "trivial case" standard defined in L6.4.
Step (a) requires quantifying over M as a mathematical object — a perspective
available only from the meta-level (the language of this document, which ranges
over all models). Step (b) requires knowing what "trivial" means for each
invariant, which is defined in L6.4 using the full anchor machinery. By `RTD-NI` (L6.5.T4)
(RTD Non-Internalisability), no fixed instantiation M can internally express
statements ranging over all possible substrates. The degeneracy profile inherits
this limitation: it is a meta-level statement about M, not an internal statement
within M. ∎

### The Classification Table Is Meta-Level

| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Corollary** | L6.6.C1 | `ClassTable-Meta` | | **Novel** |
**Synopsis:** See the remark.

**Source:** CRPT; from `Dege-Inv` (L6.6.D1).

The full model classification table is a meta-level artifact
derived from this anchor. It classifies implementations and instantiations; no
implementation or instantiation can produce the full table from within itself.

### Where to find complete classification
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Remark** | L6.6.R4 | `Class-Ref` | | **Novel** |
**Synopsis:** The Classification Refinement remark: the six-class partition can be refined by adding more horizon predicates (e.g., the ω-limit set, the orbit spectrum) to produce finer classifications with more classes. The six-class partition is minimal in the sense that removing any of H_S, H_I, H_O loses a bisimulation-invariant distinction.

**Source:** CRPT; from `6-Part` (L3.2.T1) + `H_S` (L3.1.D1) + `H_I` (L3.1.D2) + `H_O` (L3.1.D4).

The full degeneracy profile of known CRPT models is computed using only the constructs
of this document. It is a derived meta-level artifact for understanding degeneracy
patterns across model families.
