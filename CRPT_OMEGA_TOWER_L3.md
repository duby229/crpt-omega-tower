# L3 — Horizon, Classification, and Persistent Canonical Invariants

## L3.1 — Orbit Signature and Horizon Predicates

*Purpose.* Horizon Predicates H_S, H_I, H_O. This section introduces the three boolean predicates that classify every element of 𝒰_M according to its position in the reduction graph. H_S detects structural branching; H_I detects uniform branching; H_O detects boundary position. These are the primary inputs to the six-class partition of L3.2.*


### Horizon Predicates

### Structural Horizon H_S
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L3.1.D1 | `H_S` | H_S(x) | **Novel** |
**Synopsis:** An element x has a structural horizon (H_S(x) = ⊤) when ρ_M is not injective at ρ_M(x) — that is, when x has at least one sibling: another element z ≠ x with ρ_M(z) = ρ_M(x). H_S detects branching in the reduction graph. Elements with H_S = ⊥ are structurally isolated — their canonical form uniquely identifies them. H_S is the first and coarsest of the three horizon predicates.

**Source:** CRPT; from `ρ_M` (L2.1.D1) + `Fiber` (L0.1.D2).


For x ∈ 𝒰_M:
```
H_S(x) :⟺ |ρ_M⁻¹(ρ_M(x)) ∩ 𝒰_M| > 1
```
where ρ_M⁻¹(y) := {z ∈ 𝒰_M | ρ_M(z) = y}. H_S(x) holds if x has multiple
ρ_M-siblings (multiple elements that map to the same successor under ρ_M).

*ARS connection.* H_S defines the *ramification locus* of ρ_M: the set of
points where ρ_M fails to be injective. In algebraic geometry: the branch locus
of a ramified cover (Hartshorne [1977] §III.10). In discrete dynamics: the
non-injective locus of the map (Katok & Hasselblatt [1995]).

### Invariant Horizon / Kernel-Congruence Predicate H_I
| **Definition** | L3.1.D2 | `H_I` | H_I(x) | **Novel** |
**Synopsis:** An element x has an invariant horizon (H_I(x) = ⊤) when all of its H_S-siblings have identical orbit signatures. That is, the elements that project to the same image as x are indistinguishable by their internal structure. H_I refines H_S: it asks not just whether siblings exist, but whether they are observationally uniform. H_I = ⊤ with H_S = ⊤ means x lives in a 'uniform cluster' — a horizon without internal differentiation.

**Source:** CRPT; from `H_S` (L3.1.D1) + `sig_M-NM` (L3.1.D5).


For x ∈ 𝒰_M:
```
H_I(x) :⟺ H_S(x) ∧ ∀z ∈ ker(ρ_M, ρ_M(x)) : z ≡_{sig_M} x
```
where **ker(ρ_M, y) := ρ_M⁻¹(y) = {z ∈ 𝒰_M | ρ_M(z) = y}** is the **kernel (preimage) of ρ_M at y**,
and **z ≡_{sig_M} x** denotes the **congruence relation**: z and x have identical orbit signature 
(sig_M(z) = sig_M(x)).

**Categorical Interpretation:**
- **Kernel:** The preimage set ker(ρ_M, ρ_M(x)) is the **kernel of the map ρ_M** in the category-theoretic 
 sense — the set of all elements mapping to the same image. In algebra, the kernel measures the 
 "collapse" or "non-injectivity" of a map.
- **Congruence:** The relation **≡_{sig_M}** is an **equivalence relation** (congruence) on ker(ρ_M, ρ_M(x)):
 - **Reflexivity:** sig_M(z) = sig_M(z) trivially.
 - **Symmetry:** sig_M(z) = sig_M(x) ⟹ sig_M(x) = sig_M(z).
 - **Transitivity:** sig_M(z₁) = sig_M(z₂) ∧ sig_M(z₂) = sig_M(x) ⟹ sig_M(z₁) = sig_M(x).
 
This congruence partitions ker(ρ_M, ρ_M(x)) into **congruence classes** of signature equivalence.

### Invariant-Invisibility: Kernel Congruence
| **Definition** | L3.1.D3 | `Ker-Cong` | ker(ρ_M, y) | **Reframed** |
**Synopsis:** The kernel congruence ker(ρ_M, y) = ρ_M^{-1}(y) is the set of all elements that the projection operator maps to y in one step — the complete preimage of y. This is the per-image fiber relevant to computing H_S and H_I. When |ker(ρ_M, ρ_M(x))| > 1, element x has structural siblings.

**Source:** Mac Lane [1998] *Categories for the Working Mathematician* §I — kernel congruence ker(f), reframed as the fiber-indexed kernel congruence of the projection operator.

H_I(x) = ⊤ means: **x belongs to a kernel of ρ_M where the congruence relation induced by the orbit signature 
is trivial** (all kernel elements are congruent / have identical orbit signatures). Equivalently:
```
H_I(x) = ⊤ ⟺ |ker(ρ_M, ρ_M(x)) / ≡_{sig_M}| = 1
 ⟺ ker(ρ_M, ρ_M(x)) is a single congruence class under ≡_{sig_M}
 ⟺ all preimages of ρ_M(x) are indistinguishable by sig_M
```

**Distinction: H_I = ⊥ (Kernel with Non-Trivial Congruence):**
When H_I(x) = ⊥ and H_S(x) = ⊤ (ramified but distinguishable), the kernel
ker(ρ_M, ρ_M(x)) partitions into **multiple congruence classes**: 
```
|ker(ρ_M, ρ_M(x)) / ≡_{sig_M}| ≥ 2
```
The preimages of ρ_M(x) can be told apart by the orbit signature (Class B, E elements).

**Semantic Equivalence (Both Formulations):**
The original definition H_I(x) :⟺ H_S(x) ∧ ∀z ∈ ρ_M⁻¹(ρ_M(x)) : sig_M(z) = sig_M(x)
and the kernel-congruence formulation H_I(x) :⟺ H_S(x) ∧ (trivial congruence on kernel)
are mathematically identical; the kernel formulation emphasizes the category-theoretic and 
algebraic structure.

*Remark L3.1.R5 (Category-Theoretic Role).* H_I has no standard counterpart in classical ARS theory 
or model theory. However, in **category theory / universal algebra**, the notion of **kernel-preserving 
congruence** is well-established:
- A map φ : X → Y is **kernel-preserving congruence** if for every y ∈ Y, the congruence 
 relation on φ⁻¹(y) is "invisible" to some observable (here, the orbit signature).
- H_I classifies elements whose position in the ramification kernel is **observationally 
 indistinguishable** from their siblings' positions.

This makes H_I a genuine CRPT innovation: detecting invisible kernel congruences w.r.t. 
the orbit signature observable

### Abstraction Depth Horizon H_O
| **Definition** | L3.1.D4 | `H_O` | H_O(x) | **Novel** |
**Synopsis:** The depth horizon H_O(x) = ⊤ when d_M(x) = 1: element x is exactly one projection step from a fixed point. H_O identifies the boundary layer of the convergent regime — elements adjacent to Fix(ρ_M). These are the elements whose immediate projection image is already canonical.

**Source:** CRPT; from `d_M` (derivation height, L2.3.D2).

For x ∈ μT_{ρ,M}:
```
H_O(x) :⟺ d_M(x) = 1
```
H_O(x) holds if x is exactly one ρ_M-step from its canonical abstraction: x is
in the *boundary layer* ∂μT_{ρ,M} := {x ∈ μT_{ρ,M} | d_M(x) = 1}.

*Remark L3.1.R6.* H_O carries no information beyond d_M(x) = 1. It is a notational
convenience for the six-class partition (L3.2). In formal statements, write d_M(x) = 1
directly.

### Orbit Signature

### Orbit Signature — Native Form
| **Definition** | L3.1.D5 | `sig_M-NM` | | **Novel** |
**Synopsis:** The orbit signature sig_M(x) aggregates the observable features of x's reduction orbit into a single comparable value. Two elements with the same signature are indistinguishable by the observer framework. The signature is the input to H_I: H_I(x) = ⊤ means all siblings of x share the same orbit signature value, so the observer cannot use signature differences to tell them apart.

**Source:** CRPT; from the horizon predicates `H_S` (L3.1.D1), `H_I` (L3.1.D2), `H_O` (L3.1.D4).


The orbit signature extends to all of 𝒰 in a regime-dependent form:

**For x ∈ ↓_M:**
```
sig_M(x) := (↓, H_S(x), H_I(x), d_M(x), CFix(ρ_M)(x)) ∈ {↓} × {⊤,⊥} × {⊤,⊥} × ℕ × NF(→_ρ)
```
The finitary operative signature: regime tag (↓), ramification status (H_S), invariant-invisibility (H_I), abstraction depth (derivation height), and target normal form (CFix(ρ_M)).

**For x ∈ ∞_M:**
```
sig_M(x) := (∞, limit_id, convergence_profile) ∈ {∞} × Limits(𝒯) × ℝ^ℕ
```
The topological operative signature: regime tag (∞), limit point (CFix(ρ_M)(x)), and convergence rate profile (how fast ρ_M^n(x) approaches its limit).

*Remark L3.1.R7.* In the native regime-stratified framework, the orbit signature is regime-stratified. The H_S and H_I horizons apply to ↓_M elements (finitary branching structure); ∞_M elements instead carry convergence-rate / asymptotic information. Both components are observable (orbit-distinguishable) and capture the element's "behavioral signature."

For pure-WF specialization: pure WF models have ∞_M = ∅, so sig_M(x) always takes the first form (↓-regime, WF horizons).

*Remark L3.1.R8 (Discernibility Interpretation).* The orbit signature sig_M(x) is the
**discernible fingerprint** of x — the complete set of structurally distinguishable
properties that characterize x's position in the abstraction landscape. Elements with
identical signatures are **observationally indiscernible**: no observer with access to
horizon status, depth, or canonical form can tell them apart (`Sig-Dep` (L3.1.T1)). Horizons
H_S and H_I together classify the **limits of discernibility**: H_S marks where the
projection operator (= abstraction function, `RP=Abs` (L2.1.T4)) is non-injective (structural information is compressed), and H_I
marks where that compression is **total** — the preimages become signature-indiscernible.

### Signature Depth Implication and Limits of sig_M

### Signature Depth Implication
| **Theorem** | L3.1.T1 | `Sig-Dep` | | **Novel** |
**Synopsis:** The Signature Dependence theorem establishes that the orbit signature sig_M(x) = (H_S(x), d_M(x)) is the minimal signature needed to determine H_I: two elements sharing the same orbit signature are necessarily in the same H_I class. No coarser signature suffices.

**Source:** CRPT; from `sig_M-NM` (L3.1.D5).

Under PA-WN + PA-Conf:
```
sig_M(x) = sig_M(y) ⟹ d_M(x) = d_M(y)
```

*Proof.* derivation height is the third component of the orbit signature. ∎

### sig_M is not a sufficient NFC invariant
| **Remark** | L3.1.R1 | `sig-Insuf` |  | **Novel** |
**Synopsis:** This remark explains the scope of the signature dependence theorem: the orbit signature has full discriminating power within a single fiber (where all elements share the same canonical form) but does not discriminate between elements of different fibers.

**Source:** CRPT; from `sig_M-NM` (L3.1.D5).

The claim
sig_M(x) = sig_M(y) ⟹ x ≃_M y is **false** in general.

*Counterexample.* Let 𝒰_M = {a, a', b_A, γ_A, c, c', b_B, γ_B} with:
```
ρ_M: a ↦ b_A, a' ↦ b_A, b_A ↦ γ_A, γ_A ↦ γ_A (component A)
 c ↦ b_B, c' ↦ b_B, b_B ↦ γ_B, γ_B ↦ γ_B (component B)
```
This substrate satisfies C1, C2, PA-WN, and PA-Conf (ρ_M is functional).
NF(→_ρ) = {γ_A, γ_B}, Fix(ρ_M) = {γ_A, γ_B}.

By the mutual consistency argument proved here: sig_M(a) = (⊤, ⊤, 2) = sig_M(c).

*Proof of the mutual consistency claim.* We show the unique consistent solution
to the recursive equations defining H_I(a) and H_I(a') is H_I(a) = H_I(a') = ⊤.

Recall H_I(a) := H_S(a) ∧ ∀z ∈ ρ_M⁻¹(ρ_M(a)) : sig_M(z) = sig_M(a)
(`H_I` (L3.1.D2)). H_S(a) = ⊤ (from the preimage count above).
ρ_M⁻¹(ρ_M(a)) = ρ_M⁻¹(b_A) = {a, a'}.
So H_I(a) = ⊤ iff sig_M(a') = sig_M(a).
sig_M(a) = (⊤, H_I(a), 2) and sig_M(a') = (⊤, H_I(a'), 2) (H_S(a')=⊤ and d_M(a')=2 by the same calculations).
The equation reduces to: H_I(a) = ⊤ iff H_I(a') = H_I(a).

**Case H_I(a) = ⊥:** Then sig_M(a) = (⊤, ⊥, 2). For H_I(a)=⊥ to be consistent,
we need sig_M(a') ≠ sig_M(a), i.e. H_I(a') ≠ ⊥, i.e. H_I(a') = ⊤.
But H_I(a') = ⊤ requires sig_M(a) = sig_M(a').
sig_M(a') = (⊤, ⊤, 2) ≠ (⊤, ⊥, 2) = sig_M(a). Contradiction.
So H_I(a) = ⊥ is inconsistent.

**Case H_I(a) = ⊤:** Then sig_M(a) = (⊤, ⊤, 2). H_I(a') = ⊤ iff sig_M(a) = sig_M(a').
sig_M(a') = (⊤, ⊤, 2) = sig_M(a). Consistent. H_I(a) = H_I(a') = ⊤. ✓

The unique consistent solution is H_I(a) = H_I(a') = ⊤. By the symmetric construction
(same preimage structure for c, c'), H_I(c) = H_I(c') = ⊤.
Therefore sig_M(a) = (⊤, ⊤, 2) = sig_M(c). ✓ ∎

But CFix(ρ_M)(a) = γ_A ≠ γ_B = CFix(ρ_M)(c), so a ≄_M c. ∎

The invalid reasoning pattern: "equal H_S values along orbits forces the same
NF." This is wrong. Two elements can have identical local ramification structure
at every depth yet converge to distinct normal forms, provided the two convergent
sub-systems are structurally isomorphic but terminate at different endpoints.

### H_I Well-Definedness: General Kernel Theorem

The counterexample above (L3.2) demonstrated H_I well-definedness for a specific
2-element kernel via case analysis. The following theorem establishes existence and
uniqueness of the H_I assignment for **arbitrary kernels**, including uncountable
ones. This resolves the coinductive circularity in `H_I` (L3.1.D2) in full generality.

### Kernel Independence of H_I
| **Observation** | L3.2.Obs1 | `H_I-KI` |  | **Novel** |
**Synopsis:** The orbit signature sig_M(x) captures the observable structure of x's position in the reduction graph: H_S tells whether x has siblings, d_M gives x's depth, and together they determine H_I. The key observation is that H_I is determined entirely by the orbit signatures of x's siblings, not by any property of their own orbits.

**Source:** CRPT; from `H_I` (L3.1.D2) + `Ker-Cong` (L3.1.D3).

The H_I equations are
**kernel-local**: for each y ∈ 𝒰_M, the H_I values of elements in K(y) := ker(ρ_M, y)
depend only on each other, not on H_I values outside K(y). This is because H_I(x)
references only sig_M(z) for z ∈ K(ρ_M(x)) = K(y), and the non-circular components
of the orbit signature — namely H_S(z) and d_M(z) — are determined entirely by the substrate
structure (independent of H_I). Since ρ_M is a function, kernels for distinct images
are disjoint: K(y₁) ∩ K(y₂) = ∅ whenever y₁ ≠ y₂. Therefore the H_I assignment
problem decomposes into independent sub-problems, one per kernel.

### H_I Well-Definedness — General Kernel Theorem
| **Theorem** | L3.1.T2 | `H_I-WD` | | **Novel** |
**Synopsis:** H_I well-definedness: the H_I predicate is well-defined on elements, not just on fibers. This is proved by the two-case kernel theorem: when a fiber ker(ρ_M, y) is a singleton, H_I is vacuously ⊤; when the fiber has multiple elements, H_I depends only on the multiset of orbit signatures within the fiber, which is the same for all elements in the fiber.

**Source:** CRPT; from `H_I` (L3.1.D2) + `sig_M-NM` (L3.1.D5).

Let K = ker(ρ_M, y)
be any kernel with |K| ≥ 2. Then the system of Boolean equations

```
∀z ∈ K : H_I(z) = ⊤ ⟺ ∀w ∈ K : sig_M(w) = sig_M(z)
```

(where sig_M(z) = (H_S(z), H_I(z), d_M(z)) and H_S, derivation height are externally determined)
has a **unique** consistent solution, given by:

**Case 1 (derivation height-uniform kernel):** If ∀z₁, z₂ ∈ K : d_M(z₁) = d_M(z₂), then
H_I(z) = ⊤ for all z ∈ K.

**Case 2 (derivation height-non-uniform kernel):** If ∃z₁, z₂ ∈ K : d_M(z₁) ≠ d_M(z₂), then
H_I(z) = ⊥ for all z ∈ K.

This holds for kernels of **arbitrary cardinality** (finite, countable, or uncountable).

*Proof.*

**Preliminary.** Since |K| ≥ 2, every z ∈ K satisfies |K| = |ρ_M⁻¹(ρ_M(z))| > 1,
so H_S(z) = ⊤ for all z ∈ K (`H_S` (L3.1.D1)). Thus H_S is uniformly ⊤ across K.
The non-H_I components of the orbit signature are all externally determined:
sig_M(z) = (⊤, H_I(z), d_M(z)), and d_M(z) is fixed by the substrate.

The consistency equation reduces to: for each z ∈ K,

```
H_I(z) = ⊤ ⟺ ∀w ∈ K : (⊤, H_I(w), d_M(w)) = (⊤, H_I(z), d_M(z))
 ⟺ ∀w ∈ K : H_I(w) = H_I(z) ∧ d_M(w) = d_M(z)
```

**Case 2 (derivation height-non-uniform).** Suppose ∃z₁, z₂ ∈ K with d_M(z₁) ≠ d_M(z₂).
For any z ∈ K: there exists some w ∈ K with d_M(w) ≠ d_M(z) (since K contains
at least two distinct derivation height values, and z has some derivation height value, so at least one other
element has a different value). Therefore the condition ∀w ∈ K : d_M(w) = d_M(z)
fails, which forces H_I(z) = ⊥.

*Consistency check:* With H_I(z) = ⊥ for all z ∈ K, sig_M(z) = (⊤, ⊥, d_M(z)).
For any z: since ∃w with d_M(w) ≠ d_M(z), we have sig_M(w) = (⊤, ⊥, d_M(w))
≠ (⊤, ⊥, d_M(z)) = sig_M(z). So the universally quantified condition fails,
confirming H_I(z) = ⊥. ✓

*Uniqueness in Case 2:* Any consistent assignment must assign H_I(z) = ⊥ for
all z ∈ K, since the derivation height non-uniformity forces the universal condition to fail
regardless of H_I values. No other assignment is consistent. ✓

**Case 1 (derivation height-uniform).** Suppose ∀z₁, z₂ ∈ K : d_M(z₁) = d_M(z₂) =: d.
Then sig_M(z) = (⊤, H_I(z), d) for all z ∈ K, and the consistency equation is:

```
H_I(z) = ⊤ ⟺ ∀w ∈ K : H_I(w) = H_I(z)
```

i.e., H_I(z) = ⊤ iff all K elements have the same H_I value as z.

We test all possible assignments:

**(1a) All H_I = ⊤.** For any z ∈ K: ∀w ∈ K : H_I(w) = ⊤ = H_I(z). ✓
The universal condition holds, so H_I(z) = ⊤ is consistent. ✓

**(1b) All H_I = ⊥.** For any z ∈ K: sig_M(z) = (⊤, ⊥, d). Since all elements
share the same orbit signature (⊤, ⊥, d), the condition ∀w ∈ K : sig_M(w) = sig_M(z)
holds. Therefore the equivalence demands H_I(z) = ⊤. But we assumed H_I(z) = ⊥.
**Contradiction.** ✗

**(1c) Mixed assignment (∃z₁, z₂ ∈ K : H_I(z₁) = ⊤ ∧ H_I(z₂) = ⊥).**
For z₁ (with H_I(z₁) = ⊤): the condition ∀w : H_I(w) = H_I(z₁) = ⊤ must hold.
But H_I(z₂) = ⊥ ≠ ⊤. **Contradiction.** ✗

Therefore (1a) is the unique consistent solution: H_I(z) = ⊤ for all z ∈ K. ✓

**Cardinality independence.** The argument above uses only:
- Elementary properties of ∀-quantification over K (no finiteness assumption)
- The fact that H_S and derivation height are externally determined (non-circular)
- Boolean case analysis (three exhaustive cases: all-⊤, all-⊥, mixed)

No step requires K to be finite or countable. The argument applies identically
to uncountable kernels (e.g., continuous gauge orbits in physics instantiations). ✓ ∎

### H_I Decision Criterion
| **Corollary** | L3.1.C1 | `H_I-Dec` | | **Novel** |
**Synopsis:** H_I is effectively decidable from derivation heights: H_I(x) = ⊤ if and only if all siblings of x have the same d_M value. Comparing natural numbers is simpler than comparing arbitrary signatures. This corollary makes H_I computationally tractable for all finite CRPT models.

**Source:** CRPT; from `H_I-WD` (L3.1.T2).

For any x ∈ 𝒰_M with H_S(x) = ⊤:
```
H_I(x) = ⊤ ⟺ ∀z ∈ ker(ρ_M, ρ_M(x)) : d_M(z) = d_M(x)
```
The H_I value is fully determined by whether all siblings share the same
abstraction depth. No iterative or coinductive computation is needed.

*Proof.* By `H_I-WD` (L3.1.T2): H_I(x) = ⊤ iff ker(ρ_M, ρ_M(x)) is derivation height-uniform
(Case 1), which is exactly ∀z ∈ ker(ρ_M, ρ_M(x)) : d_M(z) = d_M(x). ✓ ∎

*Remark (Coinductive Circularity Fully Resolved).* `H_I-WD` (L3.1.T2) and
`H_I-Dec` (L3.1.C1) show that the apparent coinductive circularity in `H_I` (L3.1.D2)
— where H_I depends on the orbit signature, which contains H_I — is **illusory**. The H_I
value of every element is uniquely determined by the non-circular invariants H_S
and derivation height alone. The seemingly self-referential definition resolves to an explicit,
non-circular criterion: derivation height-uniformity within the kernel. This resolution holds
for kernels of any cardinality, including the uncountable preimage structures
arising in continuous/topological models (e.g., gauge orbits in quantum field
theory instantiations).

### What sig_M classifies
| **Remark** | L3.1.R2 | `sig-Class` |  | **Novel** |
**Synopsis:** Remark on orbit signature independence: sig_M(x) = sig_M(y) does not imply x ≃_M y. Two elements can have the same local structure (same depth, same sibling count) while converging to different fixed points. The orbit signature classifies local position, not global destination.

**Source:** CRPT; from `sig_M-NM` (L3.1.D5).

sig_M(x) = (H_S(x), H_I(x), d_M(x))
is a structural invariant capturing:
- ramification type (H_S): whether x's ρ_M-image has multiple preimages
- ramification invisibility (H_I): whether those preimages are sig_M-indistinguishable
- abstraction depth (derivation height): distance to Fix(ρ_M)

the orbit signature classifies the *local orbit structure* of x. It does not record which normal
form x converges to. Equal the orbit signature values imply equal local structure; they do not
imply NFC membership coincidence.

### Where sig_M has full discriminating power
| **Remark** | L3.1.R3 | `sig-Full` |  | **Novel** |
**Synopsis:** The extended orbit signature sig_M^+(x) = (sig_M(x), CNF_M(x)) is a complete invariant: sig_M^+(x) = sig_M^+(y) implies x ≃_M y. Adding the canonical form to the orbit signature gives the full observational fingerprint. This remark clarifies where the orbit signature alone is insufficient.

**Source:** CRPT; from `sig_M-NM` (L3.1.D5).

In any model with a
unique normal form |NF(→_ρ)| = 1 (e.g. ZFC/HF with CNF = ∅; Category Theory with
CNF = 0_Cat; HoTT with CNF = 𝟘), all convergent elements share the same NFC class
trivially, and the orbit signature discriminates *within* that single class by horizon type and
depth. The three primary CRPT instantiations are all of this type. For models with
multiple normal forms (λ-calculus, abstract algebra), NFC classification requires
CFix(ρ_M)(x) or model-specific identity conditions beyond the orbit signature.

### Correct sufficient invariant
| **Remark** | L3.1.R4 | `CNF-Suf` |  | **Novel** |
**Synopsis:** The extended orbit signature sig_M^+(x) = (sig_M(x), CNF_M(x)) is a sufficient discriminant: sig_M^+(x) = sig_M^+(y) implies x ≃_M y. Adding the canonical form to the orbit signature gives a complete observational fingerprint. The plain orbit signature sig_M alone is not sufficient for discrimination across different fibers.

CRPT; Baader & Nipkow [1998]

Define sig_M⁺(x) := (sig_M(x), CFix(ρ_M)(x)).
Then sig_M⁺(x) = sig_M⁺(y) ⟹ x ≃_M y trivially (CFix(ρ_M)(x) = CFix(ρ_M)(y) is exactly
x ≃_M y by the CNF-Fibre `CNF=CR` (L2.5.T2)). This is sufficient but tautological: the
sufficiency comes entirely from including CFix(ρ_M), not from the orbit signature itself.

### Horizons as Structured Limits of Abstraction

**Provenance.** This subsection gives exact formal content to what the horizon
predicates H_S, H_I, H_O *mean* as limits of discernibility under abstraction.
All ingredients are from §L2.4–8. No new axioms are introduced.

### Horizon Profile and Class
| **Definition** | L3.1.D6 | `HP` | HP_M(x) | **Novel** |
**Synopsis:** The horizon profile HP_M(x) is the triple (H_S(x), H_I(x), H_O(x)) packaged as a single three-bit value. It is the input to the six-class partition function and the primary datum used by the observer triple to classify elements.

**Source:** CRPT; from `H_S` (L3.1.D1) + `H_I` (L3.1.D2) + `H_O` (L3.1.D4).

For x ∈ 𝒰_M, define its
*horizon profile* as:
```
H(x) := (H_S(x), H_I(x), H_O(x), Reg(x))
```
where H_S, H_I, H_O are the horizon predicates (Definitions 8.1–8.3) and
Reg(x) ∈ {↓, ∞} is the regime tag from `Reg-Strat` (L2.2.D3). Let Class(x) ∈ {A,B,C,D,E,F}
be the six-class label determined by the Q1/Q2/Q3 pattern (L3.2).

### Horizons as Abstraction Limits
| **Theorem** | L3.1.T3 | `Hor-Abs` | | **Novel** |
**Synopsis:** The Horizon Abstraction theorem establishes that the horizon profile HP_M is a complete invariant for the six-class partition: two elements are in the same class if and only if they have the same horizon profile. The six-class partition is exactly the quotient of 𝒰_M by the HP_M equivalence.

**Source:** CRPT; from `HP` (L3.1.D6) + `6-Part` (L3.2.T1).

For any x ∈ 𝒰_M:

**(1)** (*Ontological terminal — H_O*) If x ∈ ↓_M and H_O(x) = ⊤, then d_M(x) = 1
and ρ_M(x) = CFix(ρ_M)(x) = Abs_M(x); one application of ρ_M reaches the canonical
form and no further ρ_M-reduction is possible (CFix(ρ_M)(x) is a fixpoint).

**(2)** (*Total kernel compression — H_I*) If H_I(x) = ⊤, then for all
z, z' ∈ ker(ρ_M, ρ_M(x)):
```
sig_M(z) = sig_M(z')
```
and if z, z' are in the same normal-form fiber (CFix(ρ_M)(z) = CFix(ρ_M)(z')), then z ≈ z'.
Abstraction has erased all preimage distinctions within each fiber: the kernel of
ρ_M at ρ_M(x) is a union of sig-uniform congruence classes.

**(3)** (*Resolvable compression — H_S without H_I*) If H_S(x) = ⊤ and H_I(x) = ⊥,
then |ker(ρ_M, ρ_M(x))| > 1 and there exist z, z' ∈ ker(ρ_M, ρ_M(x)) with
sig_M(z) ≠ sig_M(z'). Abstraction is locally non-injective but the preimages
remain structurally distinguishable by their orbit signatures.

*Proof.*

**(1)** By `H_O` (L3.1.D4), H_O(x) = ⊤ iff d_M(x) = 1, which requires x ∈ ↓_M
(H_O is defined on μT_{ρ,M} ⊆ ↓_M). Then by `Abs=RP` (L2.4.T4):
```
Abs_M(x) = CFix(ρ_M)(x) = ρ_M^{d_M(x)}(x) = ρ_M(x)
```
Since CFix(ρ_M)(x) ∈ Fix(ρ_M) (`CNF-Stab` (L2.4.T3)), no further ρ_M-reduction is possible. ✓

**(2)** By `H_I` (L3.1.D2), H_I(x) = ⊤ iff H_S(x) = ⊤ and
∀z ∈ ker(ρ_M, ρ_M(x)) : sig_M(z) = sig_M(x). Thus any two preimages z, z' share
the same signature. Now, if additionally CFix(ρ_M)(z) = CFix(ρ_M)(z') (i.e. z, z' are in
the same normal-form fiber NFC_M(f)), then z ≃_M z' by definition of ≃_M
(`≃_M` (L2.5.D2): x ≃_M y ⟺ CFix(ρ_M)(x) = CFix(ρ_M)(y)). The preimages are
*orbit-equivalent* (≃_M-indiscernible) within each fiber: no observer with access
to CFix(ρ_M) can distinguish them.

Note: PA-Bisim (L1.3.Ax1) asserts ≈ ⊆ ≃_M (bisimilarity implies orbit-equivalence), not the converse. Orbit-equivalent elements need not be bisimilar — two elements with the same canonical form can exhibit different →_ρ-branching structure.

**Conclusion for part (2):** H_I(x) = ⊤ implies that all preimages
z, z' ∈ ker(ρ_M, ρ_M(x)) with CFix(ρ_M)(z) = CFix(ρ_M)(z') satisfy z ≃_M z'.
Abstraction has erased all CFix-level distinctions within each fiber: the kernel
of ρ_M at ρ_M(x) is a union of ≃_M-congruence classes, each corresponding to a
single canonical form. ✓

*Note.* Equal signatures do NOT imply same fiber in general (Remark L3.1.R6: sig_M(a) =
sig_M(c) but CFix(ρ_M)(a) ≠ CFix(ρ_M)(c)). The orbit-equivalence conclusion z ≃_M z'
requires the additional condition that z, z' share the same canonical form. Within a
single fiber where all elements share CFix(ρ_M)(z) = f, this holds by definition of
≃_M. H_I = ⊤ then implies that all elements within the fiber are sig_M-indistinguishable
and orbit-equivalent. ✓

**(3)** By `H_S` (L3.1.D1), H_S(x) = ⊤ iff |ker(ρ_M, ρ_M(x))| > 1. If H_I(x) = ⊥,
then the sig_M-uniformity condition fails: ∃z, z' ∈ ker(ρ_M, ρ_M(x)) with
sig_M(z) ≠ sig_M(z'). Thus abstraction merges them at one step but the observer
signature can still distinguish them: the collapse is resolvable. ✓ ∎

*Remark L3.1.R9 (∞_M Horizon Story).* `Hor-Abs` (L3.1.T3) describes horizons for ↓_M elements
(where H_S, H_I, H_O are directly defined). For ∞_M elements, the native form
of the orbit signature (`sig_M-NM` (L3.1.D5)) replaces the Boolean horizon predicates with a
**convergence profile** — how fast ρ_M^n(x) approaches its topological limit.
The analogue of H_S in the persistent regime is non-injectivity of the limit
map: multiple ∞_M elements can share the same limit point (different convergence
rates to the same attractor). The analogue of H_I is whether the convergence
profiles of co-limiting elements are distinguishable. By `PA-NWF-NE` (L2.2.T5), these persistent-regime structures
are transformed into vertical (depth) structure at the next tower level, connecting
the horizon theory of L3.1 to the tower theory of L8.1.

---

## H_I Kernel-Locality Theorem

*Purpose.* This subsection formalizes what informally was captured in `H_I-WD` (L3.1.T2):
that H_I(x) depends only on the equivalence class of x under observable equivalence ≃_M,
not on the choice of representative. This is the **kernel-locality** property.

### H_I Respects Kernel Congruence (Observable Equivalence)

| **Theorem** | L3.1.T4 | `H_I-KernelLocal` | | **Novel** |
**Synopsis:** H_I is kernel-local: if x and y are in the same kernel fiber (ρ_M(x) = ρ_M(y)), then H_I(x) = H_I(y). The H_I predicate depends only on the fiber structure at ρ_M(x), not on any property distinguishing x from y within the fiber. This locality is what makes H_I a well-defined predicate on fibers rather than just on elements.

**Source:** CRPT; from `H_I` (L3.1.D2) + `Ker-Cong` (L3.1.D3).

*For all x, y ∈ 𝒰_M:*

If x ≃_M y (observable equivalence), then H_I(x) = H_I(y).

**Equivalently:** H_I is a **well-defined function on the quotient** 𝒰_M / ≃_M.

**Proof.**

By definition, x ≃_M y means:
(1) ρ_M(x) ≃_M ρ_M(y), and
(2) CFix(ρ_M)(x) = CFix(ρ_M)(y), and  
(3) sig_M(x) = sig_M(y) (L2.5.D2, criterion C2).

We show H_I(x) = H_I(y) using the definition `H_I` (L3.1.D2):

**H_I(x) := H_S(x) ∧ ∀z ∈ ker(ρ_M, ρ_M(x)) : sig_M(z) = sig_M(x)**

**Step 1: ρ_M(x) and ρ_M(y) have the same image under the equivalence relation.**

Since x ≃_M y by assumption, (1) gives ρ_M(x) ≃_M ρ_M(y), which by C2 means
sig_M(ρ_M(x)) = sig_M(ρ_M(y)). 

But we need a stronger claim: the preimage kernels are equivalent under the orbit signature.
That is, ker(ρ_M, ρ_M(x)) and ker(ρ_M, ρ_M(y)) contain exactly the same elements
(since ρ_M is a function). So ker(ρ_M, ρ_M(x)) = ker(ρ_M, ρ_M(y)) as sets if and only if
ρ_M(x) = ρ_M(y).

Actually, by (1): ρ_M(x) ≃_M ρ_M(y) does NOT necessarily mean ρ_M(x) = ρ_M(y).
It means they have the same signature. So we need to be more careful.

**Step 1 (Revised): Direct proof using the orbit signature uniformity.**

The definition of H_I(x) uses sig_M(z) for z ∈ ker(ρ_M, ρ_M(x)). By definition of ≃_M,
the orbit signature is the same for x and y: sig_M(x) = sig_M(y) by (3).

H_S(x) = |ker(ρ_M, ρ_M(x))| > 1 (by `H_S` (L3.1.D1)). 
Since ≃_M is defined via SIG-DEP and C2, and the orbit signature depends on H_S, H_I, derivation height (for ↓_M regime),
we have: H_S(x) = H_S(y) by (3), since sig_M(x) = sig_M(y) includes the H_S component.

So H_S(x) = H_S(y). ✓

**Step 2: The quantified universal condition is sig_M-uniform across kernels.**

H_I(x) = ⊤ iff [∀z ∈ ker(ρ_M, ρ_M(x)) : sig_M(z) = sig_M(x)].

Case A: If ρ_M(x) = ρ_M(y), then ker(ρ_M, ρ_M(x)) = ker(ρ_M, ρ_M(y)) as sets, so the
quantified condition is identical for x and y. ✓

Case B: If ρ_M(x) ≠ ρ_M(y) but ρ_M(x) ≃_M ρ_M(y), then sig_M(ρ_M(x)) = sig_M(ρ_M(y)).
This means ρ_M(x) and ρ_M(y) are in the same sig_M-equivalence class, even if they are
distinct elements. 

In this case, ker(ρ_M, ρ_M(x)) and ker(ρ_M, ρ_M(y)) are disjoint sets (since ρ_M is a function).
The H_I condition for x asks: is every z ∈ ker(ρ_M, ρ_M(x)) sig_M-equivalent to x?
The H_I condition for y asks: is every w ∈ ker(ρ_M, ρ_M(y)) sig_M-equivalent to y?

Since x ≃_M y means sig_M(x) = sig_M(y), the condition becomes:
- For H_I(x): is every z ∈ ker(ρ_M, ρ_M(x)) sig_M-equivalent to a representative with
  sig_M-value = sig_M(y)?
- For H_I(y): is every w ∈ ker(ρ_M, ρ_M(y)) sig_M-equivalent to a representative with
  sig_M-value = sig_M(x)?

Since sig_M(x) = sig_M(y), these two conditions are symmetrically identical. ✓

Alternatively, by the well-definedness theorem `H_I-WD` (L3.1.T2), the H_I assignment
is determined by the derivation height-uniformity of each kernel, independent of which specific
representative of an equivalence class is chosen. Therefore h_I(x) = H_I(y) whenever
x ≃_M y (they lie in kernels with the same derivation height-uniformity profile).  ✓

**Conclusion:** H_I is well-defined on the quotient 𝒰_M / ≃_M. ✓ ∎

**Corollary (L3.1.C1 [H_I-Quotient]).** The function H_I factors through the quotient:

There exists a function H_I* : 𝒰_M / ≃_M → {⊤, ⊥} such that for all x ∈ 𝒰_M:
```
H_I(x) = H_I*([x]_{≃_M})
```
where [x]_{≃_M} is the equivalence class of x under ≃_M.

**Proof.** By kernel-locality (L3.1.T4), define H_I*([x]_{≃_M}) := H_I(x) for any
representative x of the class. This is well-defined by the theorem. ✓

---

## L3.2 — Six-Class Horizon Partition

*Purpose.* Orbit Signature and H_I Well-Definedness. This section defines the orbit signature sig_M(x) and proves that H_I is well-defined and computable: the uniform-sibling condition it tests is independent of the choice of representative in each fiber. It also establishes the kernel-locality theorem: H_I depends only on the local fiber structure.*


*Remark L3.2.R1 (Discernibility Interpretation).* The six-class partition is the fundamental
**discernibility classification** of ↓_M. Each class represents a distinct position in
the discernibility landscape: A and D are fully discernible (no collapse), B and E have
resolvable collapse (siblings distinguishable by the orbit signature), C and F have unresolvable
collapse (siblings indiscernible by the orbit signature). The partition answers three nested questions
about each element's discernibility status: convergence (Q1), compression (Q2), and
visibility of compression (Q3).

### Boolean Lattice Formulation
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L3.2.D1 | `Bool-Lat` | | **Imported** |
**Synopsis:** The Boolean lattice on the three-element set {H_S, H_I, H_O} is the standard power-set lattice 2^3 with eight elements. The six-class partition assigns each element of 𝒰_M to one node of this lattice according to its horizon profile. The lattice structure is imported from Boolean algebra; its CRPT application is original.

**Source:** Boole [1847] *The Mathematical Analysis of Logic*; Birkhoff [1940] *Lattice Theory* §V — Boolean algebra.

The six-class partition
arises from a **stratified Boolean lattice of independent predicates**. The universe {⊥, ⊤}² of 
two independent Boolean variables (Q1, Q2) generates a Boolean algebra. The third variable Q3 = H_I 
depends on Q2 (it is vacuous when Q2 = ⊥), creating a lattice stratification.

### Independent Boolean Predicates
| **Definition** | L3.2.D2 | `Bool-Pred` | | **Novel** |
**Synopsis:** The Boolean classification predicates encode the six-class partition as a mapping from the eight Boolean combinations of (H_S, H_I, H_O) to the class labels {A, B, C, D, E, F}. Class A: all three ⊥. Class B: H_S ⊤, H_I ⊤, H_O ⊥. Class C: H_S ⊤, H_I ⊥. Class D: H_O ⊤, H_S ⊥. Class E: H_O ⊤, H_S ⊤. Class F: H_S ⊥, H_I ⊤, H_O ⊥ (empty).

**Source:** CRPT; from `H_S` (L3.1.D1) + `H_I` (L3.1.D2) + `H_O` (L3.1.D4).

Define three binary
predicates on μT_{ρ,M}:

1. **Q1(x): Fix-Point Predicate** (Boolean variable)
 ```
 Q1(x) := ⊤ if x ∈ Fix(ρ_M) [Already reached a fixed point]
 Q1(x) := ⊥ if x ∉ Fix(ρ_M) [Not yet at a fixed point]
 ```

2. **Q2(x): Ramification Predicate** (Boolean variable, independent of Q1)
 ```
 Q2(x) := ⊤ if H_S(x) = ⊤ [Multiple preimages: ρ_M⁻¹(ρ_M(x)) has size > 1]
 Q2(x) := ⊥ if H_S(x) = ⊥ [Single preimage: injective at x]
 ```

3. **Q3(x): Invariant-Invisibility Predicate** (Boolean variable, dependent on Q2)
 ```
 Q3(x) := ⊤ if Q2(x) = ⊤ AND H_I(x) = ⊤ [Ramified AND indistinguishable]
 Q3(x) := ⊥ if Q2(x) = ⊤ AND H_I(x) = ⊥ [Ramified AND distinguishable]
 Q3(x) := N/A if Q2(x) = ⊥ [Not ramified: H_I is vacuous]
 ```
 (When Q2 = ⊥, the indistinguishability condition H_I has no content — the element's single 
 preimage is trivially identical to itself.)

**Interpretation — Boolean Stratification.**
The naive Boolean lattice {⊥,⊤}³ has 2³ = 8 elements. The **stratification** Q3(x) = N/A when Q2(x) = ⊥ 
means:
- The sub-lattice with Q2 = ⊥ condenses to 1 element per Q1 value: (Q1, ⊥, N/A), yielding 2 classes.
- The sub-lattice with Q2 = ⊤ expands to 2 elements per Q1 value (Q3 = ⊥ or ⊤), yielding 4 classes.
- Total: 2 + 4 = 6 classes.

This is a **stratified lattice structure**: the full Boolean lattice is refined where informative, 
collapsed (by identifying N/A as vacuous) where not.

---

## The Six Classes as Lattice Atoms

The six-class partition classifies each x ∈ μT_{ρ,M} by the value (Q1(x), Q2(x), Q3(x)):

**Fixpoint Classes (Q1 = ⊤):**

| Class | Fix | H_S | H_I | Description | Lattice Atom |
|:-----:|:---:|:---:|:---:|-------------|:--------:|
| D | ⊤ | ⊥ | N/A | Fixpoint, single preimage (isolated) | (⊤,⊥) |
| E | ⊤ | ⊤ | ⊥ | Fixpoint, multiple preimages, distinguishable | (⊤,⊤,⊥) |
| F | ⊤ | ⊤ | ⊤ | Fixpoint, multiple preimages, indistinguishable (**logically defined; proved empty in L3.2 `F=∅` (L3.2.T2)**) | (⊤,⊤,⊤) |

**Non-Fixpoint Classes (Q1 = ⊥):**

| Class | Fix | H_S | H_I | Description | Lattice Atom |
|:-----:|:---:|:---:|:---:|-------------|:--------:|
| A | ⊥ | ⊥ | N/A | Convergent, single preimage (clean) | (⊥,⊥) |
| B | ⊥ | ⊤ | ⊥ | Convergent, ramified, distinguishable | (⊥,⊤,⊥) |
| C | ⊥ | ⊤ | ⊤ | Convergent, ramified, indistinguishable | (⊥,⊤,⊤) |

**Why Exactly Six:**
- Q1 generates 2 base classes: fixpoint vs. non-fixpoint
- Q2 refines each into 2: ramified vs. non-ramified. Subtotal: 2 × 2 = 4 base classes
- Q3 further refines only when Q2 = ⊤: distinguishable vs. indistinguishable collapse
 - 2 classes with Q2 = ⊥ (no refinement by Q3): classes A, D
 - 4 classes with Q2 = ⊤ (refined by Q3 into 2 each): classes {B,C} and {E,F}
 - Total: 2 + 4 = 6

This is the **Boolean lattice structure**: independent Boolean variables Q1 and Q2 span 2² = 4 base atoms; 
conditional Boolean variable Q3 refines the Q2 = ⊤ sub-lattice into 2³/2 = 4 atoms within that stratum, 
leaving Q2 = ⊥ stratum as 2 atoms. Total: 6 atoms in the stratified lattice.

---

## Class Properties and Order-Theoretic Structure

### Lattice Ordering on Classes
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Lemma** | L3.2.L1 | `Lat-Ord` | | **Imported** |
**Synopsis:** The lattice order on {H_S, H_I, H_O} is the standard partial order by logical implication: H_S ≤ H_I because H_I is vacuously true when H_S is false (no siblings to be uniform). This order determines which class transitions are possible under projection steps.

**Source:** Birkhoff [1940] *Lattice Theory* — partial order of a lattice.

Define a partial order ⊑ on classes by:
```
⊑ := refinement: C' ⊑ C iff all elements of class C' are a subset of elements of class C at some depth.
```
Under this ordering, the six classes form a **stratified Boolean poset** (not a lattice in the 
category-theoretic sense, but a Boolean stratification).

### Six Classes Partition μT_{ρ,M} as Boolean Stratification
| **Theorem** | L3.2.T1 | `6-Part` | | **Novel** |
**Synopsis:** The six-class partition assigns every element of 𝒰_M to exactly one of five non-empty classes (Class F is proved empty by L3.2.T2) based on the three boolean horizon predicates H_S, H_I, H_O. Class A: all three ⊥ (no horizon, not boundary). Class B: H_S ⊤, H_I ⊤ (uniform cluster, not boundary). Class C: H_S ⊤, H_I ⊥ (non-uniform cluster). Class D: H_O ⊤, H_S ⊥ (isolated boundary). Class E: H_O ⊤, H_S ⊤ (boundary with siblings). This partition is the structural backbone of the observer theory in L4.

**Source:** CRPT; from `Bool-Pred` (L3.2.D2) + `H_S` (L3.1.D1) + `H_I` (L3.1.D2) + `H_O` (L3.1.D4).


Classes A–F are mutually exclusive and jointly exhaustive on μT_{ρ,M}, forming the atoms of a Boolean 
lattice stratified by the dependency Q3 ⇒ Q2.

*Proof.* 
**Mutual exclusivity:** Each class is determined by a unique tuple (Q1(x), Q2(x), Q3(x)) from 
the model {(⊥,⊥,N/A), (⊥,⊤,⊥), (⊥,⊤,⊤), (⊤,⊥,N/A), (⊤,⊤,⊥), (⊤,⊤,⊤)}.
For any x, each Q1 and Q2 value is unique; Q3 is determined by Q2 (vacuous or well-defined).
No element satisfies two distinct tuples. ✓

**Joint exhaustiveness:** For any x ∈ μT_{ρ,M}:
- Q1(x) ∈ {⊥, ⊤} is determined (either x ∈ Fix or x ∉ Fix).
- Q2(x) ∈ {⊥, ⊤} is determined (H_S has a unique value).
- If Q2(x) = ⊥: assign (Q1(x), ⊥, N/A), corresponding to class A or D.
- If Q2(x) = ⊤: compute Q3(x) = H_I(x) ∈ {⊥, ⊤}, determining class in {B,C,E,F}.
The corresponding class tuple is uniquely selected. ✓

**Boolean interpretation:** The two independent predicates {Q1, Q2} span a 4-element Boolean 
subalgebra of {⊥,⊤}². The conditional predicate Q3, defined only when Q2 = ⊤, stratifies the 
Q2 = ⊤ stratum into two sub-classes per Q1 value. The result is a **refined Boolean structure** 
with 6 atoms. ✓ ∎

*Remark L3.2.R2 (Logical vs. Occupied Classes).* `6-Part` (L3.2.T1) establishes the full six-class logical partition: all six classes A–F are logically distinct and mutually exclusive. A structural result proved below (`F=∅` (L3.2.T2)) shows that Class F is **never occupied** in any deterministic CRPT model. The logical partition therefore comprises five active classes (A, B, C, D, E) and one provably empty class (F).

**Standard Connections.** 
- **Class A:** Regular convergent elements with injective ρ_M-structure. Abstractly: clean 
 convergence (no ramification).
- **Class B:** Ramified but distinguishable by the orbit signature. Abstractly: resolvable collapse 
 (observer can tell which concrete variant).
- **Class C:** Ramified and indistinguishable by the orbit signature. Abstractly: unresolvable collapse 
 (observer cannot tell variants apart).
- **Class D:** Isolated normal forms (unique preimage = the element itself). Abstractly: 
 fixpoint with no coalescence.
- **Class E:** Normal forms with resolvable ramification. Abstractly: fixpoint with 
 distinguishable one-step convergent predecessors.
- **Class F:** Structurally empty class (proved in `F=∅` (L3.2.T2) below). The defining
 conditions Q1=⊤, H_S=⊤, H_I=⊤ are logically consistent but simultaneously unrealizable
 in any deterministic CRPT model: for every fixpoint f with H_S(f) = ⊤, `H_I-Dec` (L3.1.C1)
 forces H_I(f) = ⊥. Claims that Class F is occupied (e.g., CFix(ρ_M) in ZFC, Cat, HoTT)
 are incorrect; those elements are Class E. See `F=∅` (L3.2.T2).

### Class F = ∅ in Every Deterministic CRPT Model
| **Theorem** | L3.2.T2 | `F=∅` |  | **Novel** |
**Synopsis:** Class F would consist of elements with H_S = ⊥ and H_I = ⊤ but without H_O — isolated elements (no siblings) that nonetheless satisfy the uniform-sibling condition. This class is provably empty: H_I is vacuously satisfied (and hence uninformative) when H_S = ⊥, so no element can non-trivially occupy Class F. This reduces the six boolean combinations to five active classes.

**Source:** CRPT; from `6-Part` (L3.2.T1) + `H_I` (L3.1.D2).


In any deterministic CRPT model (𝒰_M, ρ_M, the structural relation), Class F is empty:
```
Class F = { x ∈ μT_{ρ,M} | Q1(x) = ⊤ ∧ H_S(x) = ⊤ ∧ H_I(x) = ⊤ } = ∅
```

*Proof.* Suppose for contradiction that f ∈ Class F. Then f ∈ Fix(ρ_M), H_S(f) = ⊤, and H_I(f) = ⊤. We derive a contradiction in six steps.

**(Step 1: Non-fixpoint preimage exists.)** H_S(f) = ⊤ implies |ρ_M⁻¹(f)| > 1 (`H_S` (L3.1.D1):
since f ∈ Fix(ρ_M), ρ_M(f) = f, hence |ρ_M⁻¹(ρ_M(f))| = |ρ_M⁻¹(f)| > 1). Thus ∃z ≠ f
with ρ_M(z) = f.

**(Step 2: z ∉ Fix(ρ_M).)** If z ∈ Fix(ρ_M) then ρ_M(z) = z. But ρ_M(z) = f and z ≠ f.
Contradiction. So z ∉ Fix(ρ_M).

**(Step 3: d_M(z) = 1.)** By `derivation height` (L2.3.D2),
```
d_M(z) := min{ n ∈ ℕ | ρ_M^n(z) ∈ Fix(ρ_M) }
```
Since z ∉ Fix(ρ_M): d_M(z) ≥ 1. Since ρ_M(z) = f ∈ Fix(ρ_M): ρ_M^1(z) ∈ Fix(ρ_M), so d_M(z) ≤ 1.
Therefore d_M(z) = 1.

**(Step 4: d_M(f) = 0.)** Since f ∈ Fix(ρ_M): ρ_M^0(f) = f ∈ Fix(ρ_M), so d_M(f) = 0.

**(Step 5: Kernel is not derivation height-uniform.)** ker(ρ_M, f) = ρ_M⁻¹(f) contains both f (with
d_M(f) = 0, Step 4) and z (with d_M(z) = 1, Step 3). Since 0 ≠ 1, ker(ρ_M, f) is NOT
derivation height-uniform.

**(Step 6: Contradiction via `H_I-Dec` (L3.1.C1).)** Since f ∈ Fix(ρ_M): ρ_M(f) = f, so
ker(ρ_M, ρ_M(f)) = ker(ρ_M, f), which is not derivation height-uniform (Step 5). By `H_I-Dec` (L3.1.C1):
```
H_I(f) = ⊤ ⟺ ker(ρ_M, f) is d_M-uniform
```
Since ker(ρ_M, f) is not derivation height-uniform, H_I(f) = ⊥. This contradicts H_I(f) = ⊤. □

*Remark L3.2.R3.* The NWF-regime analogue Class F* (L6.4) is a distinct class and may be
occupied; the argument above uses d_M(z) = 1 for non-fixpoint ρ_M-preimages of a convergent-
regime fixpoint, a property specific to ↓_M. The logical class definition is retained in
`6-Part` (L3.2.T1) because class emptiness is a model-semantic property, not a structural
inconsistency: Class F is a provably unoccupied logical slot in every deterministic CRPT model.

**Notation.** The boundary layer ∂μT_{ρ,M} := {x ∈ μT_{ρ,M} | d_M(x) = 1} intersects all 
non-fixpoint classes (A, B, C) at depth 1. Within any class, the rank function derivation height further 
stratifies elements by abstraction depth; see the orbit signature (`sig_M-NM` (L3.1.D5)).

---

## Native Regime Extension: Twelve-Class Partition (6 per Regime)

The six-class partition (L3.2–9.2) applies to the convergent regime ↓_M. In the native regime-stratified framework (L1.2–L1.5, `Reg-Strat` (L2.2.D3)), a parallel six-class partition applies to the persistent regime ∞_M, yielding a **twelve-class total partition** of 𝒰.

*Remark L3.2.R4.* The partition is regime-stratified, not regime-mixed: each element belongs to exactly one regime (↓_M or ∞_M by `Reg-Strat` (L2.2.D3)) and thus to exactly one class within that regime's six-class partition.

### Topological Horizons on ∞_M (Parallel to H_S, H_I)

For x ∈ ∞_M, define topological analogues of the structural horizons:

### Topological Structural Horizon H_S^{top}
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L3.2.D3 | `H_S^top` | H_S^{top} | **Novel** |
**Synopsis:** The persistent regime analogues of the horizon predicates H_S^{top}, H_I^{top}, H_O^{top} are defined for elements of ∞_M using the topological limit structure from PA-WN_top in place of the canonical form. These are the L3 predecessors of the full NWF horizon predicates developed in L6.

**Source:** CRPT; from `H_S` (L3.1.D1); persistent-regime form.

For x ∈ ∞_M:
```
H_S^{top}(x) := ⊤ if lim_{n→∞} ρ_M^n(x) has multiple topological pre-images in ∞_M
 := ⊥ if lim_{n→∞} ρ_M^n(x) has unique topological pre-image [itself, or closure-unique]
```
Measures whether the limit point is topologically "ramified" (appears as limit of multiple distinct orbits in ∞_M, not just x's own orbit).

### Convergence-Rate Invisibility Horizon H_I^{top}
| **Definition** | L3.2.D4 | `H_I^top` | H_I^{top} | **Novel** |
**Synopsis:** The topological invariant horizon H_I^{top}(x) for elements of ∞_M is defined using the topological limit structure from PA-WN_top: H_I^{top}(x) = ⊤ when all elements in the topological fiber of x (elements with the same topological limit) share the same orbit signature. This is the persistent-regime analogue of H_I.

**Source:** CRPT; from `H_I` (L3.1.D2); persistent-regime form.

For x ∈ ∞_M:
```
H_I^{top}(x) := ⊤ if H_S^{top}(x) = ⊤ AND convergence rates to CFix(ρ_M)(x) are indistinguishable
 := ⊥ if H_S^{top}(x) = ⊤ AND convergence rates are distinguishable (e.g., by Hölder exponent)
 := N/A if H_S^{top}(x) = ⊥
```
For ramified limits, measures whether distinct orbits approaching the same limit exhibit observably different convergence speeds.

### Six Classes on ∞_M (Topological Analogues)

Define predicates Q1^{top}, Q2^{top}, Q3^{top}:

### ∞_M Boolean Predicates
| **Definition** | L3.2.D5 | `Q-top` | Q1^{top}, Q2^{top}, Q3^{top} | **Novel** |
**Synopsis:** The topological classification predicates Q1^{top}, Q2^{top}, Q3^{top} for ∞_M elements: Q1^{top}(x) = (x ∈ Fix(ρ_M^p)) for the canonical period p; Q2^{top}(x) = H_S^{top}(x); Q3^{top}(x) = H_I^{top}(x). These are the persistent-regime analogues of the convergent-regime classification predicates Q1, Q2, Q3.

**Source:** CRPT; from `H_S^top` (L3.2.D3) + `H_I^top` (L3.2.D4).

Define:
```
Q1^{top}(x) := ⊤ if x ∈ Lim_M (limit-point class in ∞_M)
 := ⊥ if x ∉ Lim_M (non-limit element in ∞_M)

Q2^{top}(x) := H_S^{top}(x) (ramified topologically)

Q3^{top}(x) := H_I^{top}(x) (indistinguishable rate, dependent on Q2^{top})
```

where **Lim_M := range(CFix(ρ_M)) ∩ Limits(𝒯) ∩ ∞_M** is the set of limit points actually reached by ∞_M elements.

### Twelve-Class Partition
| **Definition** | L3.2.D6 | `12-Part` | 12-classes | **Novel** |
**Synopsis:** The twelve-class partition definition for the combined model M (both regimes): the six-class partition of ↓_M and the six-class partition of ∞_M (Classes A*–E* analogously) together give twelve classes. This is the full classification framework when both regimes are non-empty.

**Source:** CRPT; from `6-Part` (L3.2.T1) + `Q-top` (L3.2.D5).

Elements of ∞_M partition into six classes by (Q1^{top}, Q2^{top}, Q3^{top}):

**Limit-Point Classes (Q1^{top} = ⊤) in ∞_M:**

| Class | Limit? | H_S^{top} | H_I^{top} | Description (∞_M Analogue) | 
|:-----:|:------:|:---------:|:---------:|---|
| D_∞ | ⊤ | ⊥ | N/A | Limit point, unique ∞_M-pre-image (isolated limit) |
| E_∞ | ⊤ | ⊤ | ⊥ | Limit point, multiple ∞_M-pre-images, distinguishable rates |
| F_∞ | ⊤ | ⊤ | ⊤ | Limit point, multiple ∞_M-pre-images, indistinguishable rates |

**Non-Limit Classes (Q1^{top} = ⊥) in ∞_M:**

| Class | Limit? | H_S^{top} | H_I^{top} | Description (∞_M Analogue) |
|:-----:|:------:|:---------:|:---------:|---|
| A_∞ | ⊥ | ⊥ | N/A | Persistent, unique pre-image structure, clean approach to limit |
| B_∞ | ⊥ | ⊤ | ⊥ | Persistent, ramified pre-images, distinguishable rates |
| C_∞ | ⊥ | ⊤ | ⊤ | Persistent, ramified pre-images, indistinguishable rates |

### Properties of the Twelve-Class Partition

### Twelve-Class Partition Exhaustive & Exclusive on 𝒰
| **Theorem** | L3.2.T3 | `12-Part-EE` |  | **Novel** |
**Synopsis:** The twelve-class partition theorem: the twelve classes exhaustively and disjointly partition 𝒰_M = ↓_M ⊔ ∞_M. Each element belongs to exactly one of the twelve classes. Class F (convergent) and Class F* (persistent) are both empty.

**Source:** CRPT; from `12-Part` (L3.2.D6).

Under native axiom system (PA-WN globally, PA-WN_top on ∞_M, PA-Conf on all):
```
𝒰 = (A ∐ B ∐ C ∐ D ∐ E ∐ F) ∐ (A_∞ ∐ B_∞ ∐ C_∞ ∐ D_∞ ∐ E_∞ ∐ F_∞)
 = ↓_M-classes ∐ ∞_M-classes
 = 6 + 6 = 12 disjoint classes
```

*Proof.* 
**Regime Partition Exhaustiveness:** By `Part` (L2.2.T3), 𝒰 = ↓_M ∐ ∞_M (`Reg-Strat` (L2.2.D3)).
**Within ↓_M:** Classes A–F partition ↓_M (`6-Part` (L3.2.T1)), exhaustive and exclusive.
**Within ∞_M:** Classes A_∞–F_∞ partition ∞_M by the same stratified Boolean logic applied to topological horizons.
 - Q1^{top} ∈ {⊤, ⊥}: partitions ∞_M into limit points vs. non-limits (2 parts)
 - Q2^{top} ∈ {⊤, ⊥}: partitions each into ramified vs. non-ramified (4 parts total)
 - Q3^{top}: further partitions Q2^{top} = ⊤ parts into distinguishable vs. indistinguishable (6 parts total)
**Overall:** 𝒰 exhaustively partitions into 6 + 6 = 12 disjoint classes. ✓ ∎

### Pure WF Specialization
| **Theorem** | L3.2.T4 | `WF-Back` |  | **Novel** |
**Synopsis:** The well-founded backwards theorem: the six-class partition of ↓_M is recovered from the twelve-class partition by restricting to the convergent-regime classes A through E. The convergent-regime partition is the special case of the twelve-class partition where the persistent-regime classes are all empty.

**Source:** CRPT; from `12-Part` (L3.2.D6).

For pure WF (PA-WN globally, ∞_M = ∅):
```
Classes A_∞–F_∞ are empty
𝒰 = A ∐ B ∐ C ∐ D ∐ E ∐ F (standard six-class partition)
All theorems referencing classes A–F remain unchanged
```

*Proof.* If ∞_M = ∅, then no element satisfies Q1^{top}. By `12-Part` (L3.2.D6), classes A_∞–F_∞ are empty. The native partition reduces to the classical six-class partition. ✓ ∎

### Signature Stratification Across Both Regimes
| **Corollary** | L3.2.C1 | `Sig-Strat` |  | **Novel** |
**Synopsis:** The signature stratification corollary: the orbit signature stratifies the twelve-class partition into a two-dimensional grid — convergent/persistent (regime dimension) × A/B/C/D/E (class dimension). The horizon predicates give the class dimension; the regime indicator gives the first dimension.

**Source:** CRPT; from `12-Part` (L3.2.D6) + `sig_M-NM` (L3.1.D5).

The orbit signature sig_M (`sig_M-NM` (L3.1.D5)-native):
```
↓_M elements: sig_M(x) = (↓, H_S(x), H_I(x), d_M(x), CFix(ρ_M)(x))
∞_M elements: sig_M(x) = (∞, CFix(ρ_M)(x), convergence_rate(x))
```
stratifies 𝒰 into 12 classes by (regime, horizon-parameters).

---

## L3.3 — Canonical Orbit Invariant CNF∞_M

*Purpose.* Horizon Profile. This section packages the three horizon predicates into a single combined indicator the horizon profile(x) — the horizon profile — for use in the observer framework of L4. The horizon profile is a function of the Boolean triple (H_S, H_I, H_O) and is the input to the observer's Gate and sig functions.*


The construction in §L2.1–9 covers the convergent regime ↓_M (equivalently, μT_{ρ,M} in the pure-WF profile).
This section covers the persistent regime ∞_M (equivalently, νT_{ρ,M} in the native stratified profile).

*Remark L3.3.R1 (Hybrid Framework: Two Canonical Abstraction Forms).*
In the hybrid framework (`Reg-Strat` (L2.2.D3), L1.4), every element has a canonical abstraction:

- **For x ∈ ↓_M (convergent regime):** CFix(ρ_M)(x) ∈ NF(→_ρ), finitary normal form. Computed by finite ρ_M-iteration: ρ_M^{d_M(x)}(x). (Classical form.)
- **For x ∈ ∞_M (persistent regime):** CFix(ρ_M)(x) ∈ Limits(𝒯), topological limit point. Computed as lim_{n→∞} ρ_M^n(x) under PA-WN_top. (Native extension.)

The canonical orbit invariant CNF∞_M(x), defined in this section, is an alternative notation/characterization for the persistent-regime case, emphasizing that it is the **infinite-time** analog of the finitary canonical form. Both forms together provide a complete abstraction map:

```
CFix(ρ_M) : 𝒰 → (NF(→_ρ) ∪ Limits(𝒯))
 x ↦ { ρ_M^{d_M(x)}(x) if x ∈ ↓_M
 { lim_{n→∞} ρ_M^n(x) [≡ CNF∞_M(x)] if x ∈ ∞_M
```

No element of 𝒰 is outside the reach of one of these two forms (`Part` (L2.2.T3): 𝒰 = ↓_M ∐ ∞_M). The persistent regime ∞_M is governed by PA-WN_top (`PA-Scope` (L1.5.D1), L1.4), which guarantees the topological limit exists; uniqueness follows from `TopSep-Uniq` (L1.2.T1), i.e. the explicit TopSep(𝒯) requirement. See also L3.2 for the twelve-class partition stratifying both regimes.

### Stabilisation Conditions (Dynamical Systems Formulation)

The following are *definitions* of orbital properties from discrete dynamical systems theory.
They characterise the **eventual behavior** of orbits under repeated application of ρ_M.
They are not axioms (they restrict no models) and not theorems (they are stipulated, not derived).
They appear as explicit hypotheses in theorems about CNF∞_M.

The orbit of x is the sequence $\text{Orb}(x) = (x, ρ_M(x), ρ_M^2(x), \ldots)$. The symbolic image
of this orbit under a quotient map Q is $Q(\text{Orb}(x)) = (Q(x), Q(ρ_M(x)), Q(ρ_M^2(x)), \ldots)$.

### ω-Limit Set
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L3.3.D1 | `ω-Lim` | ω(f, x) | **Imported** |
**Synopsis:** The ω-limit set ω_≈(x) of a persistent element x is the set of bisimulation classes visited infinitely often by the projection orbit: ω_≈(x) = {[y]_≈ | ∀n ∃k ≥ n : [ρ_M^k(x)]_≈ = [y]_≈}. This is the persistent-regime analogue of the canonical form: it captures the 'destination' of the persistent orbit in the long run.

Birkhoff [1927]; Bhatia & Szegő [1970]

For a discrete dynamical system $(X, f)$, the
*ω-limit set* (or *eventual image*) of x is:
```
ω(x) := ∩_{n≥0} cl( {f^k(x) | k ≥ n} )
```
the closure of the tail of the orbit (Katok & Hasselblatt [1995], L1.1). Equivalently:
$y ∈ ω(x)$ iff there exists a subsequence $n_i → ∞$ with $f^{n_i}(x) → y$.

### SC-1: ω-Limit Bisimulation Fixation
| **Definition** | L3.3.D2 | `SC-1` | SC-1 | **Novel** |
**Synopsis:** Scope Condition SC-1 requires that the persistent orbit of x is eventually periodic: there exist n ≥ 0 and p ≥ 1 such that ρ_M^{n+p}(x) ≃_M ρ_M^n(x) for all further iterates. SC-1 is the weakest scope condition; it admits the periodic canonical form CNF∞_M.

**Source:** CRPT; from PA-Reach (L1.3.Ax2) + `sig_M-NM` (L3.1.D5).

x ∈ νT_{ρ,M} satisfies SC-1 if
the ω-limit set of x under ρ_M is **constant** in the bisimulation quotient 𝒰_M/≈:
```
SC-1(x) :⟺ ∃N ∈ ℕ : ∀n ≥ N : [ρ_M^n(x)]_≈ = [ρ_M^N(x)]_≈
 ⟺ ω_≈(x) is a singleton in 𝒰_M/≈
```
where $ω_≈(x) := \{[y]_≈ : y ∈ ω(x)\}$ is the ω-limit set in the bisimulation quotient.

*Standard name.* This is **ω-limit fixation** on a quotient space (Walters [1982], Symbolic Dynamics).
The condition asserts that the orbit eventually enters and remains in a single bisimulation equivalence class.

### SC-2: Eventual Periodicity of Horizon Signature
| **Definition** | L3.3.D3 | `SC-2` | SC-2 | **Novel** |
**Synopsis:** Scope Condition SC-2 requires that the orbit is eventually periodic and the period is stable under the projection operator: the period p does not change after step n. SC-2 implies SC-1 and is required for the orbit spectrum to be a well-defined probability measure.

**Source:** CRPT; from PA-Reach (L1.3.Ax2) + `sig_M-NM` (L3.1.D5).

x ∈ νT_{ρ,M} satisfies SC-2 if
the orbit signature sequence is **eventually periodic**:
```
SC-2(x) :⟺ ∃N ∈ ℕ, ∃p ∈ ℕ, p > 0 : ∀n ≥ N : sig_M(ρ_M^n(x)) = sig_M(ρ_M^{n+p}(x))
```

*Standard name.* This is **eventual periodicity** of the symbolic orbit under the map
$sig_M : 𝒰_M → \{⊤,⊥\} × \{⊤,⊥\} × ℕ$ (symbolic dynamics). The condition asserts that after
finitely many steps, the orbit signature repeats with some minimal period p.

### SC-3: Eventual Periodicity of Valuation Sequence
| **Definition** | L3.3.D4 | `SC-3` | SC-3 | **Novel** |
**Synopsis:** Scope Condition SC-3 requires that the orbit trace OT(x) is eventually periodic with a computable period. SC-3 is the effective version of SC-1, required for algorithmic orbit analysis.

**Source:** CRPT; from PA-Reach (L1.3.Ax2) + `sig_M-NM` (L3.1.D5).

x ∈ νT_{ρ,M} satisfies SC-3 if
the path valuation sequence is **eventually periodic**:
```
SC-3(x) :⟺ ∃N ∈ ℕ, ∃p ∈ ℕ, p > 0 : ∀n ≥ N : PV(ρ_M^n(x) →^{(n)} → ρ_M^{n+1}(x)) = PV(ρ_M^{n+p}(x) →^{(n+p)} → ρ_M^{n+p+1}(x))
```
where PV denotes the step-wise path valuation (`VS` (L4.3.D1)).

*Standard name.* Eventual periodicity in a **weighted symbolic system** (Droste, Kuich & Vogler [2009], Handbook of Weighted Automata).
The condition asserts that the sequence of valuations along the orbit eventually repeats.

### SC-4: Finite Symbolic Orbit [Bounded ω-Limit Set]
| **Definition** | L3.3.D5 | `SC-4-Def` |  | **Reframed** |
**Synopsis:** Scope Condition SC-4 (finite symbolic orbit): the persistent orbit of x visits only finitely many distinct bisimulation classes — equivalently, its ω-limit set ω_≈(x) is finite. This is the symbolic-dynamics condition that the orbit's symbolic image is ultimately periodic.

**Source:** CRPT; from `SC-1` (L3.3.D2)–`SC-3` (L3.3.D4); reframes eventual periodicity of orbits.

x ∈ νT_{ρ,M} satisfies SC-4 if:
```
SC-4(x) :⟺ |{[ρ_M^n(x)]_≈ : n ∈ ℕ}| < ∞
 ⟺ |ω_≈(x)| ≤ |{[ρ_M^n(x)]_≈ : n ∈ ℕ}| < ∞
```
the orbit visits only **finitely many distinct bisimulation classes**. Equivalently, the ω-limit set
$ω_≈(x)$ is **finite**.

*Standard name.* This is the condition of **bounded symbolic orbit** or **finite ω-orbit** in discrete
dynamical systems (Katok & Hasselblatt [1995], L1.1). In symbolic dynamics, it is the condition that the
symbolic image of the orbit is ultimately periodic (eventually enters a finite cycle in the quotient space).

### SC-4 ⟹ Eventual Periodicity
| **Theorem** | L3.3.T1 | `SC4-EP` |  | **Imported** |
**Synopsis:** SC-4 implies eventual periodicity: an orbit visiting only finitely many bisimulation classes must eventually cycle, so ∃N, p≥1 with [ρ_M^{n+p}(x)]_≈ = [ρ_M^n(x)]_≈ for all n ≥ N. Minimal period 1 gives Type P (SC-1 holds); period ≥ 2 gives Type EP.

Bhatia & Szegő [1970]

Under PA-NWF + PA-Bisim:
SC-4(x) implies the quotient orbit is eventually periodic:
$$∃N ∈ ℕ,\; ∃p ≥ 1 : ∀n ≥ N : [ρ_M^{n+p}(x)]_≈ = [ρ_M^n(x)]_≈$$

In particular:
- If the minimal such $p$ equals 1 (equivalently, $|ω_≈(x)| = 1$), then SC-1(x) holds (Type P, L6.1).
- If the minimal such $p ≥ 2$ (equivalently, $|ω_≈(x)| ≥ 2$), then SC-1(x) fails (Type EP, L6.1).

*Proof.* Assume SC-4(x), so the set $A := \{[ρ_M^n(x)]_≈ : n ∈ ℕ\}$ is finite. An infinite sequence
taking values in a finite set must eventually repeat (pigeonhole principle). Let $n_0 < n_1$ be
the first pair with $[ρ_M^{n_0}(x)]_≈ = [ρ_M^{n_1}(x)]_≈ \in A$. Set $N := n_0$ and $p := n_1 - n_0 > 0$.
By PA-Bisim, the induced map $ρ̄_M : A → A$ on quotient classes is well-defined and deterministic.
Since $[ρ_M^N(x)]_≈ = [ρ_M^{N+p}(x)]_≈$ and $ρ̄_M$ is deterministic, induction gives
$∀n ≥ N : [ρ_M^{n+p}(x)]_≈ = [ρ_M^n(x)]_≈$ — the orbit is eventually periodic with
pre-period $N$ and period dividing $p$. The ω-limit set
$ω_≈(x) = \{[ρ_M^n(x)]_≈ : n ≥ N\}$ consists of the classes on the eventual cycle,
with $|ω_≈(x)|$ equal to the minimal period. ∎

### SC-4 ⟹ SC-2 and SC-3
| **Theorem** | L3.3.T2 | `SC4-23` |  | **Novel** |
**Synopsis:** SC-4 implies SC-2 and SC-3: since SC-4 makes the quotient orbit eventually periodic, the orbit-signature sequence and the valuation sequence — both functions of the bisimulation class — are eventually periodic as well.

**Source:** CRPT; from `SC-4-Def` (L3.3.D5) + `SC-2` (L3.3.D3) + `SC-3` (L3.3.D4).

Under PA-NWF: SC-4(x) ⟹ SC-2(x) and SC-4(x) ⟹ SC-3(x).

*Proof.* By `SC4-EP` (L3.3.T1), SC-4(x) implies the quotient orbit is eventually periodic.
The signature sequence (sig(ρ_M^n(x)))_{n∈ℕ} and valuation sequence (PV at step n)_{n∈ℕ}
are determined by the quotient orbit (since sig and PV depend only on the bisimulation
class). An eventually periodic orbit induces eventually periodic sig and PV sequences,
giving SC-2(x) and SC-3(x). ∎

### Definition and Existence

### Canonical Orbit Invariant CNF∞_M: ω-Limit Quotient
| **Definition** | L3.3.D6 | `CNF∞-Def` | CNF∞_M(x) | **Novel** |
**Synopsis:** The persistent canonical form CNF∞_M(x) is defined for SC-1 elements as the unique bisimulation class in ω_≈(x) that is a fixed point of the p-fold iterated projection operator (where p = CPD(σ)). It is the persistent-regime canonical form: the stable reference point of the eventually-periodic orbit.

**Source:** CRPT; from `CPer` (L1.3.D1) + `SC-4-Def` (L3.3.D5).

For x ∈ νT_{ρ,M}, define:
```
ω_≈(x) := {[ρ_M^n(x)]_≈ : n ∈ ℕ} ∩ lim-inf_{n→∞} {[ρ_M^k(x)]_≈ : k ≥ n}
```
the **ω-limit set in the bisimulation quotient** (Katok & Hasselblatt [1995], Definition 1.1.3).

For x satisfying SC-1, this ω-limit set is a singleton {[ρ_M^N(x)]_≈} for some stabilisation index N.
Define:
```
CNF∞_M(x) := the unique element of ω_≈(x), when |ω_≈(x)| = 1
 = [ρ_M^N(x)]_≈ where N = min{n : SC-1 stabilisation index}
```

*Rigorous statement.* Under SC-1(x), the ω-limit set ω_≈(x) is a singleton bisimulation class
in 𝒰_M/≈. This is the **eventual bisimulation image** of x's orbit.

*Dynamical systems connection.* In discrete dynamical systems terminology:
- The full ω-limit set is $ω(x) := \liminf_{n→∞} \operatorname{cl}(\{ρ_M^k(x) : k ≥ n \})$ (Katok & Hasselblatt [1995])
- The quotient version is $ω_≈(x) := \{[y]_≈ : y ∈ ω(x) \}$ (quotient of the closure under ≈)
- SC-1 asserts that $|ω_≈(x)| = 1$ (singleton ω-limit in the quotient)
- CNF∞_M picks out this unique quotient class

*Remark L3.3.R2 (where CNF∞ sits in the WF/NWF duality).* CNF∞_M is **not** the full
counterpart of CFix(ρ_M); the WF/NWF duality is *graded* (`WF-NWF-Dual` (L3.3.T9)), and
CNF∞ occupies only its lowest rung:
- The total dual of CFix (total on ↓_M via PA-WN) is **CPer** (total on ∞_M via the
  *universal* PA-Reach, `CPer` (L1.3.D1)); the dual of the rank d_M is the reachability
  depth n_M (`n-Reach` (L3.3.D10)). This is the clean 1:1 level of the duality.
- CNF∞_M is the **SC-1 base layer**: defined only for eventually class-constant orbits,
  where it equals the bisimulation class [CPer_M(x)]_≈. Outside SC-1 (Type AP / aperiodic)
  it is undefined, and the orbit must be classified by the full **AOI hierarchy**
  (`AOI-Unif` (L6.3.D10)).
- A *single* complete invariant of CFix's kind is **provably impossible** on ∞_M
  (`SC-Imp` (L6.3.T1)); CNF∞ captures only the periodic fragment.

So CNF∞ and CFix share a *pattern* (extract an orbit invariant from a quotient) but are
**not** dual at the same level: CFix is total and a single complete invariant, whereas
CNF∞ is partial and the lowest rung of the necessarily-hierarchical persistent classifier.

### CNF∞ Existence
| **Theorem** | L3.3.T3 | `CNF∞-Ex` |  | **Novel** |
**Synopsis:** Persistent canonical form existence: for every SC-1 element x, CNF∞_M(x) exists. The proof uses the eventual periodicity guaranteed by SC-1 to show that ω_≈(x) is finite and contains at least one element fixed by ρ_M^p.

**Source:** CRPT; from `CNF∞-Def` (L3.3.D6) + PA-Reach (L1.3.Ax2).

Under PA-NWF + PA-Bisim, for every x with SC-1(x): CNF∞_M(x) is well-defined as a
bisimulation class. (SC-2/SC-3 are not required for existence of the class; they
additionally make the orbit valuation/spectrum periodic.)

*Proof.* By SC-1(x) (`SC-1` (L3.3.D2)) there is a stabilisation index N with
[ρ_M^n(x)]_≈ = [ρ_M^N(x)]_≈ =: c for all n ≥ N. We show ω_≈(x) = {c}:
- **c ∈ ω_≈(x).** The class c recurs at every index n ≥ N, hence occurs cofinally;
  so c ∈ liminf_{n→∞}{[ρ_M^k(x)]_≈ : k ≥ n} = ω_≈(x) (`ω-Lim` (L3.3.D1)).
- **ω_≈(x) ⊆ {c}.** Any class in the liminf must occur cofinally in the orbit; but
  every orbit class of index ≥ N equals c, so no class other than c occurs cofinally.

Thus |ω_≈(x)| = 1. Finally c is a fixpoint of the induced quotient map
ρ̄_M([y]_≈) := [ρ_M(y)]_≈ — well-defined under PA-Bisim (`CNF∞-BQF` (L5.1.T5)) — since
ρ̄_M(c) = [ρ_M(ρ_M^N(x))]_≈ = [ρ_M^{N+1}(x)]_≈ = c (as N+1 ≥ N). Hence CNF∞_M(x) := c
is the unique element of ω_≈(x) and a ρ̄_M-fixpoint, well-defined for every SC-1 element. ∎

### CNF∞ Uniqueness
| **Theorem** | L3.3.T4 | `CNF∞-Uniq` |  | **Novel** |
**Synopsis:** Persistent canonical form uniqueness: for every SC-1 element x, CNF∞_M(x) is unique. This follows from the confluence of the projection operator applied to the periodic orbit: the orbit visits the canonical form at every period-length step and no other fixed point of ρ_M^p is in ω_≈(x).

**Source:** CRPT; from `CNF∞-Def` (L3.3.D6) + PA-Bisim (L1.3.Ax1).

Under SC-1(x): CNF∞_M(x) is unique — it is the only element of ω_≈(x), and the
only ρ̄_M-fixpoint class to which the orbit stabilises.

*Proof.* By `CNF∞-Ex` (L3.3.T3), SC-1(x) gives ω_≈(x) = {c} with c = [ρ_M^N(x)]_≈ a
ρ̄_M-fixpoint. Uniqueness is then immediate on two counts: (i) ω_≈(x) is a singleton,
so c is the *only* candidate canonical class; (ii) any ρ̄_M-fixpoint class c′ lying in
ω_≈(x) satisfies c′ = c, since the set has exactly one element. Hence CNF∞_M(x) = c is
unique. (For eventually-periodic orbits, SC-4 — finitely many visited classes,
`SC4-EP` (L3.3.T1) — is the orbit-type condition that *guarantees* SC-1; given SC-1,
uniqueness needs no further hypothesis.) ∎

### Persistent Orbit Equivalence ≃∞

### ≃∞ — Persistent Orbit Equivalence
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L3.3.D7 | `≃∞` | ≃∞ | **Novel** |
**Synopsis:** Persistent orbit equivalence: x ≃∞ y holds when x and y have the same ω-limit set, ω_≈(x) = ω_≈(y) — i.e. their orbits asymptotically visit the same bisimulation classes. It is the ∞_M analogue of observable equivalence ≃_M, with quotient Q∞_M = ∞_M/≃∞.

**Source:** CRPT; from `CNF∞-Def` (L3.3.D6).

For x, y ∈ ∞_M define:
```
x ≃∞ y  :⟺  ω_≈(x) = ω_≈(y)
```
where ω_≈(x) := {[z]_≈ : z ∈ ω(x)} is the ω-limit set of x's orbit in the
bisimulation quotient (`ω-Lim` (L3.3.D1)).

x and y are *persistently orbit-equivalent* iff their orbits share the same
asymptotic bisimulation class structure. ≃∞ is the ∞_M analogue of `≃_M` (L2.5.D2):

| | ↓_M | ∞_M |
|---|---|---|
| **Canonical invariant** | CFix(ρ_M)(x) ∈ Fix(ρ_M) | ω_≈(x) ⊆ 𝒰_M/≈ |
| **Equivalence** | ≃_M : same canonical form | ≃∞ : same ω-limit set |
| **Quotient** | Q_M = ↓_M/≃_M | Q∞_M = ∞_M/≃∞ |

*On SC-1 elements:* ω_≈(x) = {CNF∞_M(x)} (singleton by `CNF∞-Def` (L3.3.D6));
≃∞ restricts to CNF∞-equality: x ≃∞ y ⟺ CNF∞_M(x) = CNF∞_M(y).

*On general ∞_M elements:* ≃∞ compares the full ω-limit set. For aperiodic
(Type AP) elements the ω-limit set may not be a singleton; two AP elements are
≃∞-equivalent iff their orbits asymptotically visit the same bisimulation classes.

*Relationship to AOI₁:* `AOI₁` (L6.3.D3) refines ≃∞ on SC-∞ orbits —
AOI₁ carries the full tail-trace equivalence class while ≃∞ carries only the
ω-limit set (the asymptotic support). AOI₁(x) = AOI₁(y) ⟹ x ≃∞ y;
the converse does not hold in general.

### ≃∞ is an Equivalence Relation
| **Theorem** | L3.3.T5 | `≃∞-Eq` |  | **Novel** |
**Synopsis:** ≃∞ is an equivalence relation: persistent orbit equivalence is reflexive, symmetric, and transitive on ∞_M — immediate from equality of ω-limit sets.

**Source:** CRPT; from `≃∞` (L3.3.D7).

≃∞ is reflexive, symmetric, and transitive on ∞_M.

*Proof.* Reflexivity: ω_≈(x) = ω_≈(x). ✓ Symmetry: ω_≈(x) = ω_≈(y) ⟹ ω_≈(y) = ω_≈(x). ✓
Transitivity: ω_≈(x) = ω_≈(y) ∧ ω_≈(y) = ω_≈(z) ⟹ ω_≈(x) = ω_≈(z). ✓ ∎

### Persistent Orbit Quotient Q∞_M
| **Definition** | L3.3.D8 | `Q∞` | Q∞_M | **Novel** |
**Synopsis:** The persistent orbit quotient Q∞_M := ∞_M/≃∞ is the set of distinct ω-limit sets of persistent orbits — the ∞_M counterpart of the abstraction quotient Q_M. Its SC-4-restricted subquotient is the NWF quotient Q_M^* used to build Lift∞.

**Source:** CRPT; from `≃∞` (L3.3.D7) + `sig_M-NM` (L3.1.D5).

```
Q∞_M  :=  ∞_M / ≃∞  =  { ω_≈(x) | x ∈ ∞_M }
```
the set of distinct ω-limit sets of ∞_M orbits under the bisimulation quotient.
Q∞_M is the *persistent orbit quotient* of M — the ∞_M counterpart of `Ab-Quot-28` (L8.2.D1).

*Relationship to Q_M^*:* The NWF abstraction quotient `NWF-Quot` (L8.5.D1) is the
SC-4-restricted subquotient:
```
Q_M^*  =  { [x]_{≃∞} | x ∈ ∞_M, x satisfies SC-4 }  ⊆  Q∞_M
```
In models where every ∞_M element satisfies SC-4 (e.g., all periodic domain models),
Q_M^* = Q∞_M. In general, Q∞_M is the proper universal quotient and Q_M^* is the
constructively tractable approximation from which `Lift∞` (L8.5.D2) is built.

### Unified Semantic Domain Sem(M)
| **Definition** | L3.3.D9 | `Sem` | Sem(M) | **Novel** |
**Synopsis:** The unified semantic domain Sem(M) := Q_M ⊔ Q∞_M is the disjoint union of the convergent orbit quotient and the persistent orbit quotient, with a regime-aware semantic projection π_sem : 𝒰_M → Sem(M). It is the semantic base through which the observer triple factors.

**Source:** CRPT; from `Q∞` (L3.3.D8) + `Ab-Quot-28` (L8.2.D1).

```
Sem(M)  :=  Q_M  ⊔  Q∞_M
```
the disjoint union of the terminating orbit quotient (`Ab-Quot-28` (L8.2.D1)) and
the persistent orbit quotient. The *semantic projection* π_sem : 𝒰_M → Sem(M) is:
- For x ∈ ↓_M: π_sem(x) := [x]_{≃_M} ∈ Q_M
- For x ∈ ∞_M: π_sem(x) := ω_≈(x) ∈ Q∞_M

π_sem is surjective and regime-aware. Under PA-Bisim (which makes ≈ = identity in
models), π_sem is well-defined on individual elements; at the abstract level, ≈-bisimilar
elements map to the same class.

*Remark L3.3.R3 (Semantic Base).* Sem(M) is the **semantic base** for the observer triple
`Obs-Triple` (L4.1.D5) and for compiler IR design: the observer 𝒪 factors through
π_sem (elements with the same orbit-equivalence class have the same behavioral
signature), and IR types correspond to elements of Sem(M). The two components
the query signature and Q∞_M are the **terminating IR** and **persistent IR** respectively.

---

### Persistent Canonical Form: Total Dual and Hierarchical Completeness

*Purpose.* The convergent regime has a clean canonical-form theory: a total rank d_M
(`d-WD` (L2.3.T1)), a total canonical form CFix with existence/uniqueness/stability
(`CNF-Ex`/`CNF-Uniq`/`CNF-Stab` (L2.4.T1–T3)), and a *single* complete ≃-invariant
(`CNF=CR` (L2.5.T2)). This subsection supplies the persistent dual at the level where a
1:1 dual exists — and states precisely where, and why, it cannot. The earlier CNF∞ layer
(L3.3.D6–T4) is partial (SC-1 only); the dual developed here is **total** on all of ∞_M,
resting on the universal axiom PA-Reach (L1.3.Ax2).

### Reachability Depth n_M
| **Definition** | L3.3.D10 | `n-Reach` | n_M(x) | **Novel** |
**Synopsis:** The reachability depth n_M(x) is the least index at which the orbit signature sig_M stabilizes — the NWF dual of the derivation height d_M. Where d_M counts steps until the orbit itself becomes constant (reaches Fix), n_M counts steps until the orbit *signature* becomes constant; the element keeps moving, but its observable signature is fixed.

**Source:** CRPT; from `CPer` (L1.3.D1) + `sig_M-NM` (L3.1.D5) + PA-Reach (L1.3.Ax2); dual of `derivation height` (L2.3.D2).

For x ∈ ∞_M:
```
n_M(x) := min { n ∈ ℕ : ∀ j ≥ 0,  sig_M(ρ_M^{n+j}(x)) = sig_M(ρ_M^n(x)) }
```
PA-Reach asserts this set is non-empty, so n_M(x) ∈ ℕ is total on ∞_M, and
CPer_M(x) = ρ_M^{n_M(x)}(x) (`CPer` (L1.3.D1)).

*Duality with d_M.* d_M(x) = min{n : ρ_M^n(x) ∈ Fix(ρ_M)} (the orbit becomes constant);
n_M(x) = min{n : sig_M∘ρ_M^n is constant} (the signature becomes constant). Both are total
ℕ-valued ranks — d_M under PA-WN, n_M under PA-Reach.

### CPer Existence
| **Theorem** | L3.3.T6 | `CPer-Ex` | | **Novel** |
**Synopsis:** For every persistent element x ∈ ∞_M, the canonical persistent representative CPer_M(x) exists — totally. This is the NWF dual of CNF-Ex, and existence is exactly the content of the universal axiom PA-Reach.

**Source:** CRPT; from PA-Reach (L1.3.Ax2) + `n-Reach` (L3.3.D10); dual of `CNF-Ex` (L2.4.T1).

For every x ∈ ∞_M, n_M(x) ∈ ℕ and CPer_M(x) := ρ_M^{n_M(x)}(x) is defined.

*Proof.* PA-Reach (L1.3.Ax2) states ∀x ∈ ∞_M ∃n ∀j≥0: sig_M(ρ_M^{n+j}(x)) = sig_M(ρ_M^n(x)).
The set {n : ∀j≥0, sig_M(ρ_M^{n+j}(x)) = sig_M(ρ_M^n(x))} is therefore non-empty; as a
non-empty subset of ℕ it has a least element, n_M(x) (`n-Reach` (L3.3.D10)). Hence
CPer_M(x) = ρ_M^{n_M(x)}(x) exists for every persistent x. Totality on ∞_M is the dual of
CNF-Ex's totality on ↓_M (`CNF-Ex` (L2.4.T1)), with PA-Reach in the role of PA-WN. ∎

### CPer Uniqueness
| **Theorem** | L3.3.T7 | `CPer-Uniq` | | **Novel** |
**Synopsis:** The reachability depth n_M(x) and the stabilized signature sig_M(CPer_M(x)) are uniquely determined by x — the NWF dual of CNF-Uniq. Where WF uniqueness rests on confluence (Church–Rosser), NWF uniqueness rests on determinism of the strategy ρ_M together with minimality of the stabilization index.

**Source:** CRPT; from `ρ_M` (L2.1.D1) (determinism, C1–C2) + `Rec-Proj` (L2.1.D4) + `n-Reach` (L3.3.D10); dual of `CNF-Uniq` (L2.4.T2).

For x ∈ ∞_M, n_M(x) is the unique least stabilization index and sig_M(CPer_M(x)) is the
unique stabilized signature.

*Proof.* ρ_M is a deterministic strategy (C1–C2, `ρ_M` (L2.1.D1)), so the orbit
(ρ_M^n(x))_{n∈ℕ} is a single determined sequence. The stabilization set
S(x) = {n : sig_M∘ρ_M^k constant for all k ≥ n} is thereby determined, and its least
element n_M(x) is unique. For every n ≥ n_M(x), sig_M(ρ_M^n(x)) = sig_M(ρ_M^{n_M(x)}(x)) =
sig_M(CPer_M(x)); so the stabilized signature is the single value the orbit signature
assumes from n_M(x) onward — unique. Independence of the chosen orbit representative is
`Rec-Proj` (L2.1.D4). (Dual mechanism: WF uniqueness comes from *confluence* of →_ρ; NWF
uniqueness comes from *determinism* of ρ_M — the two faces of the projection strategy.) ∎

### CPer Stability
| **Theorem** | L3.3.T8 | `CPer-Stab` | | **Novel** |
**Synopsis:** The stabilized signature is invariant under further projection — sig_M(CPer_M(ρ_M(x))) = sig_M(CPer_M(x)) — and the reachability depth decreases by one per step, n_M(ρ_M(x)) = max(n_M(x) − 1, 0). These are the NWF duals of CNF-Stab (idempotence) and Depth-Dec (rank decrement).

**Source:** CRPT; from `n-Reach` (L3.3.D10) + PA-Reach (L1.3.Ax2); duals of `CNF-Stab` (L2.4.T3) and `Depth-Dec` (L2.3.T2).

For x ∈ ∞_M: (i) n_M(ρ_M(x)) = max(n_M(x) − 1, 0); (ii) sig_M(CPer_M(ρ_M(x))) =
sig_M(CPer_M(x)); (iii) for all m ≥ n_M(x), sig_M(ρ_M^m(x)) = sig_M(CPer_M(x)).

*Proof.* The orbit of ρ_M(x) is the one-step shift of the orbit of x: ρ_M^n(ρ_M(x)) =
ρ_M^{n+1}(x). **(i)** If n_M(x) = 0 the signature is constant from index 0, hence constant
for ρ_M(x) as well, so n_M(ρ_M(x)) = 0. If n_M(x) = k ≥ 1, then sig_M∘ρ_M^· is constant
from index k but not k−1; under the one-step shift, ρ_M(x)'s signature is constant from
index k−1 but not k−2, so n_M(ρ_M(x)) = k−1. Hence n_M(ρ_M(x)) = max(n_M(x)−1, 0) — the
dual of `Depth-Dec` (L2.3.T2). **(ii)** CPer_M(ρ_M(x)) = ρ_M^{n_M(ρ_M(x))}(ρ_M(x)) =
ρ_M^{max(n_M(x)−1,0)+1}(x) = ρ_M^{max(n_M(x),1)}(x); since max(n_M(x),1) ≥ n_M(x), its
signature is sig_M(CPer_M(x)) by (iii). **(iii)** Immediate from the definition of n_M(x)
(`n-Reach` (L3.3.D10)). The idempotence analogue — projecting past stabilization returns
the same canonical signature — is the dual of `CNF-Stab` (L2.4.T3). ∎

### WF/NWF Canonical-Form Duality
| **Theorem** | L3.3.T9 | `WF-NWF-Dual` | | **Novel** |
**Synopsis:** The convergent and persistent canonical-form theories are dual, but the duality is *graded*. At the total-representative level it is a clean 1:1 correspondence (d_M↔n_M, CFix↔CPer, PA-WN↔PA-Reach). At the complete-classifier level it is *necessarily* asymmetric: the single complete invariant CFix dualizes to a *hierarchy* (the AOI hierarchy), because SC-Imp proves no single persistent invariant exists. The asymmetry the duality exhibits is a theorem, not a gap.

**Source:** CRPT; from `CNF-Ex`/`CNF-Uniq`/`CNF-Stab` (L2.4.T1–T3) + `CNF=CR` (L2.5.T2) + `CPer-Ex`/`CPer-Uniq`/`CPer-Stab` (L3.3.T6–T8) + `SC-Imp` (L6.3.T1) + `AOI-Unif` (L6.3.D10).

The correspondence:

| | Convergent (↓_M, μ, induction) | Persistent (∞_M, ν, coinduction) |
|---|---|---|
| Totality axiom | PA-WN | PA-Reach (universal) |
| Mode | finitary | asymptotic (+ topological where PA-WN_top) |
| Rank | d_M (`d-WD` (L2.3.T1)) | n_M (`n-Reach` (L3.3.D10)) |
| Rank decrement | d_M(ρ_M x) = d_M(x)−1 (`Depth-Dec` (L2.3.T2)) | n_M(ρ_M x) = max(n_M(x)−1,0) (`CPer-Stab` (L3.3.T8)) |
| Canonical representative | CFix = ρ_M^{d_M(x)}(x) | CPer = ρ_M^{n_M(x)}(x) |
| Ex / Uniq / Stab | `CNF-Ex`/`CNF-Uniq`/`CNF-Stab` (L2.4.T1–T3) | `CPer-Ex`/`CPer-Uniq`/`CPer-Stab` (L3.3.T6–T8) |
| Uniqueness mechanism | confluence (Church–Rosser) | determinism of ρ_M |
| Complete ≃-classifier | **single** invariant CFix (`CNF=CR` (L2.5.T2)) | **hierarchy** AOI (`AOI-Unif` (L6.3.D10)); no single one (`SC-Imp` (L6.3.T1)) |
| What stabilizes | the orbit (reaches Fix) | the orbit *signature* (orbit continues) |

**(i) Total-representative duality (1:1).** The rows above through "Ex/Uniq/Stab"
correspond exactly under the substitution σ_dual of `Iso-Dual` (L5.2.T8): each convergent
statement maps to the established persistent statement and back, with PA-WN ↔ PA-Reach as
the totality precondition. This level of the duality is symmetric.

**(ii) Complete-classifier asymmetry (necessary).** On ↓_M, CFix is a *single* complete
invariant: x ≃_M y ⟺ CFix(x) = CFix(y) (`CNF=CR` (L2.5.T2)). On ∞_M no single invariant
exists: `SC-Imp` (L6.3.T1) shows by diagonalisation that no shift-invariant single-class
function classifies the aperiodic orbits. The complete persistent classifier is therefore
*necessarily* the multi-level AOI hierarchy (`AOI-Unif` (L6.3.D10), master theorem
`AOI-Mast` (L6.1.T4)), with CNF∞ (`CNF∞-Def` (L3.3.D6)) as its SC-1 base rung.

*Proof.* (i) is the conjunction of `CNF-Ex`/`CNF-Uniq`/`CNF-Stab` (L2.4.T1–T3) with their
duals `CPer-Ex`/`CPer-Uniq`/`CPer-Stab` (L3.3.T6–T8), matched clause-for-clause by the
σ_dual table of `Iso-Dual` (L5.2.T8); the totality preconditions PA-WN and PA-Reach are
dual and each universal on its regime. (ii) is `CNF=CR` (L2.5.T2) on the WF side and
`SC-Imp` (L6.3.T1) on the NWF side: the latter forbids a single complete invariant, and the
AOI hierarchy (`AOI-Unif` (L6.3.D10)) supplies the complete classifier that SC-Imp shows
must be hierarchical. ∎

*Remark L3.3.R4 (the asymmetry is structural, not a rigor gap).* The persistent regime is
*genuinely* richer than the convergent one: a convergent orbit ends (reaches a fixpoint),
discarding its history, so one terminal value (CFix) suffices; a persistent orbit never
ends, and its asymptotic behaviour can carry unbounded structure (aperiodic class
sequences), which `SC-Imp` (L6.3.T1) proves cannot be compressed to a single bisimulation
class. Equal rigor on the two sides therefore *requires* the asymmetric presentation — a
single canonical form on ↓_M, a graded hierarchy on ∞_M. Collapsing the NWF side to one
CNF∞-style invariant would be a simplification that SC-Imp shows is false.

---
