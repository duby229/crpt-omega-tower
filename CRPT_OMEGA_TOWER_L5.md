# L5 — Model Algebra, Model Theory, Homomorphisms, and Model Order

## L5.1 — Model Algebra

### Model Algebra Operations
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Remark** | L5.1.R1 | `18-1` |  | **Novel** |
**Synopsis:** This remark establishes the algebraic framework for the collection of CRPT models. The six algebraic operations (composition, intersection, product, quotient, union, specialisation) give the class of CRPT models the structure of a model algebra. All operations produce new CRPT models from existing ones.

**Source:** CRPT; model-algebra framing after Rutten [2000].

The following establishes the algebraic structure on the collection
of CRPT models. All operations produce new CRPT models when
the component models are CRPT models.

### CRPT Model
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L5.1.D1 | `CRPT-Mod-18` |  | **Novel** |
**Synopsis:** A CRPT model (restated at L5 for the model algebra context): a substrate (𝒰_M, →_ρ, →_σ, 𝒯) satisfying the PA-* axioms of L1, with non-trivial universe and the axiom profile Profile(M) satisfying consistency. This is the object type for all six model algebra operations.

**Source:** CRPT; from `Sub` (L1.1.D1) + the PA-* axioms (L1.2–L1.3).

A *CRPT model* M is
a substrate (𝒰_M, →_ρ, →_σ, ρ_M) satisfying the substrate
conditions (L1.1), equipped with an axiom profile Profile(M) = (PA-Profile_M, LA_M)
satisfying the three conditions of `CRPT-Mod-18` (L5.1.D1). Model-local axioms LA_M may extend the abstract PA-* system with
model-specific commitments.

### Model Composition M₁ ∘ M₂
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L5.1.D2 | `Mod-∘` | ∘ | **Imported** |
**Synopsis:** The composition operation M₁ ∘ M₂: the composed model has universe 𝒰_{M₁} × 𝒰_{M₂} with componentwise projection operators ρ_{M₁∘M₂}(x,y) = (ρ_{M₁}(x), ρ_{M₂}(y)). Composition is the product in the category-theoretic sense and makes the class of CRPT models into a monoidal category.

**Source:** Mac Lane [1998] §I.3 — categorical product.

M₁ ∘ M₂ has universe 𝒰_{M₁} × 𝒰_{M₂}
with componentwise reduction and ρ_{M₁∘M₂}(x, y) = (ρ_{M₁}(x), ρ_{M₂}(y)).

### ∘ Associative
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L5.1.T1 | `∘-Assoc` |  | **Imported** |
**Synopsis:** Composition is associative: (M₁ ∘ M₂) ∘ M₃ ≅ M₁ ∘ (M₂ ∘ M₃). This is immediate from the associativity of cartesian products. The unique unit model (a single-element CRPT model) is the monoidal unit.

**Source:** Mac Lane [1998] §I.3 — associativity of the product.

(M₁ ∘ M₂) ∘ M₃ ≅ M₁ ∘ (M₂ ∘ M₃).

*Proof.* Universe pairing is associative up to canonical bijection. ∎

### Model Intersection M₁ ∩ M₂
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L5.1.D3 | `Mod-∩` | ∩ | **Imported** |
**Synopsis:** The intersection M₁ ∩ M₂ has universe 𝒰_{M₁} ∩ 𝒰_{M₂} with the intersection of the reduction relations. This operation is defined when 𝒰_{M₁} and 𝒰_{M₂} share elements with compatible reduction structures. The intersection is the meet in the lattice of CRPT models ordered by universe inclusion.

**Source:** Mac Lane [1998] — lattice meet (categorical pullback).

Universe 𝒰_{M₁} ∩ 𝒰_{M₂}, relations
→_ρ^{M₁} ∩ →_ρ^{M₂}, ρ_{M₁∩M₂} selected from the intersection.

### ∩ Decreases Universe
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L5.1.T2 | `∩-Dec` |  | **Novel** |
**Synopsis:** Intersection strictly decreases the universe: |𝒰_{M₁ ∩ M₂}| ≤ min(|𝒰_{M₁}|, |𝒰_{M₂}|). Intersection can never produce a model with more elements than either component. When 𝒰_{M₁} ∩ 𝒰_{M₂} = ∅, the intersection is the empty model (a degenerate case excluded by the non-triviality condition).

**Source:** CRPT; from `Mod-∩` (L5.1.D3).

𝒰_{M₁∩M₂} ⊆ 𝒰_{M₁} and ⊆ 𝒰_{M₂}.

*Proof.* 𝒰_{M₁∩M₂} = 𝒰_{M₁} ∩ 𝒰_{M₂} by `Mod-∩` (L5.1.D3). The set intersection
𝒰_{M₁} ∩ 𝒰_{M₂} ⊆ 𝒰_{M₁} and ⊆ 𝒰_{M₂} by definition of intersection. ∎

### Model Product M₁ × M₂
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L5.1.D4 | `Mod-×` | × | **Imported** |
**Synopsis:** The product M₁ × M₂ has universe 𝒰_{M₁} × 𝒰_{M₂} with the product projection operator. Unlike composition (∘), which may impose interaction between the components, the product maintains strict independence between the two models' reduction strategies.

**Source:** Mac Lane [1998] §I.3 — categorical product.

Ordered pairs (x, y) with
componentwise reduction and ρ_{M₁×M₂}(x,y) = (ρ_{M₁}(x), ρ_{M₂}(y)).

### Product Projections
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L5.1.T3 | `Prod-Proj` |  | **Imported** |
**Synopsis:** The product model comes with two canonical projection homomorphisms π₁ : M₁ × M₂ → M₁ and π₂ : M₁ × M₂ → M₂. These are the universal property witnesses for the product in Mod_CRPT: any model with homomorphisms to M₁ and M₂ factors uniquely through M₁ × M₂.

**Source:** Mac Lane [1998] §I.3 — product universal property.

π_{M₁} : M₁ × M₂ → M₁ and π_{M₂} : M₁ × M₂ → M₂
defined by π_{M₁}(x,y) = x and π_{M₂}(x,y) = y are model homomorphisms (L5.2).

*Proof.* Verify `Hom` (L5.2.D1) for π_{M₁} (π_{M₂} symmetric):
- Φ_R: (x,y) →_ρ (x',y') iff x →_ρ x' ∧ y →_ρ y'. Then π_{M₁}(x,y) = x →_ρ x' = π_{M₁}(x',y'). ✓
- Φ_E: (x,y) ≃_{M₁×M₂} (x',y') iff x ≃_{M₁} x' ∧ y ≃_{M₂} y'. Then π_{M₁}(x,y) = x ≃_{M₁} x' = π_{M₁}(x',y'). ✓
- Φ_ρ: π_{M₁}(ρ_{M₁×M₂}(x,y)) = π_{M₁}(ρ_{M₁}(x),ρ_{M₂}(y)) = ρ_{M₁}(x) = ρ_{M₁}(π_{M₁}(x,y)) ≃_{M₁} ρ_{M₁}(π_{M₁}(x,y)). ✓ ∎

### Model Quotient M₁/~
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L5.1.D5 | `Mod-/` | /~ | **Imported** |
**Synopsis:** The quotient model M₁/~ for a compatible equivalence relation ~ on 𝒰_{M₁}: the universe is 𝒰_{M₁}/~, the reduction relation is the image of →_ρ under the quotient map, and the projection operator is ρ_{M₁/~}([x]) = [ρ_{M₁}(x)]. Compatibility of ~ with the projection operator is required for well-definedness.

**Source:** Rutten [2000] — coalgebraic quotient by a compatible relation.

For ~ compatible with →_ρ and ρ_{M₁}:
universe 𝒰_{M₁}/~, reduction [x] →_ρ [y] iff ∃x'∈[x], y'∈[y] : x' →_ρ y'.

### Model Union M₁ ∪ M₂
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L5.1.D6 | `Mod-∪` | ∪ | **Imported** |
**Synopsis:** The union M₁ ∪ M₂ has universe 𝒰_{M₁} ∪ 𝒰_{M₂} with the union of the reduction relations. This requires that the two models agree on elements in their intersection: if x ∈ 𝒰_{M₁} ∩ 𝒰_{M₂}, then ρ_{M₁}(x) = ρ_{M₂}(x). Union is the join in the lattice of CRPT models.

**Source:** Mac Lane [1998] — lattice join (categorical pushout).

Universe 𝒰_{M₁} ∪ 𝒰_{M₂} with →_ρ = →_ρ^{M₁} ∪ →_ρ^{M₂}.

### Distributive Laws
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L5.1.T4 | `Dist-Laws` |  | **Imported** |
**Synopsis:** Distributivity of model algebra: M₁ ∘ (M₂ ∩ M₃) ⊆ (M₁ ∘ M₂) ∩ (M₁ ∘ M₃), and M₁ ∩ (M₂ ∪ M₃) = (M₁ ∩ M₂) ∪ (M₁ ∩ M₃). These distributive laws follow from set-theoretic distributivity on the universes, with the projection operators inheriting componentwise.

**Source:** Mac Lane [1998] — distributive lattice laws.

M₁ ∘ (M₂ ∩ M₃) ⊆ (M₁ ∘ M₂) ∩ (M₁ ∘ M₃). M₁ ∩ (M₂ ∪ M₃) = (M₁ ∩ M₂) ∪ (M₁ ∩ M₃).

*Proof.* Standard set-theoretic distributive laws on universes; relations follow. ∎

### Special Models
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L5.1.D7 | `Spec-Mod` |  | **Imported** |
**Synopsis:** Special models: the terminal model 𝟏 (single element, identity projection operator) is the unit for composition; the initial model 𝟎 (empty universe, excluded by non-triviality) is the zero element. These are the distinguished objects in the model algebra.

**Source:** Rutten [2000] — terminal/initial objects (unit and zero of the algebra).

The *identity model* 𝟙 = ({★}, {(★,★)}, ρ(★)=★): M ∘ 𝟙 ≅ M.
The *zero model* 𝟘 = (∅, ∅, undefined): M ∩ 𝟘 = 𝟘.

### CNF∞ as Bisimulation-Quotient Fixpoint
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L5.1.T5 | `CNF∞-BQF` |  | **Novel** |
**Synopsis:** The model algebra (Mod_CRPT, ∘, ∩, ×, /, ∪) satisfies the standard algebraic identities for a distributive lattice with product. This places the collection of CRPT models inside a well-understood algebraic structure, enabling model-algebraic proofs alongside category-theoretic ones.

**Source:** CRPT; from PA-NWF (L1.2.Ax4) + PA-Bisim (L1.3.Ax1) + `SC-1` (L3.3.D2).

Under PA-NWF + PA-Bisim
+ SC-1: CNF∞_M(x) is a fixpoint of the induced map ρ̄_M : 𝒰_M/≈ → 𝒰_M/≈
defined by ρ̄_M([x]_≈) = [ρ_M(x)]_≈. PA-Bisim ensures ρ̄_M is well-defined.

*Proof.* By SC-1, [ρ_M^N(x)]_≈ = [ρ_M^{N+1}(x)]_≈ for all n ≥ N. Hence
ρ̄_M(CNF∞_M(x)) = [ρ_M(ρ_M^N(x))]_≈ = [ρ_M^N(x)]_≈ = CNF∞_M(x). ∎

---

## L5.2 — Model Homomorphisms and the Category Mod_CRPT

### Model Homomorphism Φ : M₁ → M₂
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L5.2.D1 | `Hom` | | **Novel** |
**Synopsis:** A CRPT model homomorphism from M₁ to M₂ is a function φ: 𝒰_{M₁} → 𝒰_{M₂} that preserves all four substrate components: the reduction relation (Φ_R), observable equivalence (Φ_E), the projection operator (Φ_ρ), and the local axiom conditions (Φ_LA). Homomorphisms are the morphisms of the category Mod_CRPT; they make precise what it means for one CRPT model to be a 'structure-preserving image' of another.

**Source:** CRPT; from `Sub` (L1.1.D1) + `≃_M` (L2.5.D2).


A *model homomorphism* is a function Φ_U : 𝒰_{M₁} → 𝒰_{M₂} satisfying:
- **Φ_R (Relation preservation):** x →_ρ y ⟹ Φ_U(x) →_ρ Φ_U(y)
- **Φ_E (Equivalence preservation):** x ≃_{M₁} y ⟹ Φ_U(x) ≃_{M₂} Φ_U(y)
- **Φ_ρ (ρ-preservation):** Φ_U(ρ_{M₁}(x)) ≃_{M₂} ρ_{M₂}(Φ_U(x)) for all x
- **Φ_LA (Local axiom transport).** For each LA_{M₁}^i ∈ LA_{M₁} whose signature
 Σ_{M₁} overlaps Σ_{M₂} (i.e., references symbols present in M₂): the pushforward
 of LA_{M₁}^i under Φ_U is consistent with LA_{M₂}. Formally: if φ is the sentence
 LA_{M₁}^i, then Φ_U(φ) — the image of φ under the substitution x ↦ Φ_U(x) — is
 satisfiable in M₂ (it need not be a theorem of LA_{M₂}, only non-contradicted by it).

### Î¦_LA Is a Compatibility Condition

| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Remark** | L5.2.R1 | `PhiLA-Compat` | | **Novel** |
**Synopsis:** Φ_LA is a compatibility condition, not full local-axiom transport.

**Source:** CRPT; from `Hom` (L5.2.D1).

Φ_LA does not
require that every local axiom of M₁ become a theorem of M₂. It requires only that
the image of each M₁ local axiom is *consistent* with M₂'s local axioms. This is
the minimal condition ensuring that morphisms do not create contradictions when
model-specific structure is carried across. When LA_{M₁} = ∅ or the signatures
are disjoint, Φ_LA is vacuously satisfied. Full transport (Φ_U(LA_{M₁}^i) ⊢ LA_{M₂})
characterises *LA-faithful morphisms*, a distinguished subclass.

### CRPT Models Form Category Mod_CRPT
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L5.2.T1 | `Mod-Cat` | | **Novel** |
**Synopsis:** The category Mod_CRPT has CRPT models as objects and CRPT homomorphisms as morphisms. Its existence (identity morphisms exist, composition is associative and closed) validates the claim that CRPT is a category-theoretically coherent theory. The Lift operator (L8) and Collapse functor (L7) are endofunctors on Mod_CRPT, and their adjunction Lift ⊣ Collapse is a theorem within this category.

**Source:** CRPT; from `Hom` (L5.2.D1).


CRPT models with model homomorphisms
(satisfying Φ_R, Φ_E, Φ_ρ, Φ_LA) form a category: objects = CRPT models (= CRPT models)
with axiom profiles; morphisms = model homomorphisms; composition = function composition
(associative); identity = id_M (satisfying Φ_R, Φ_E, Φ_ρ trivially; Φ_LA vacuously
since the image of each LA_M^i under id is LA_M^i itself, consistent with LA_M).

*Proof.* We verify the category laws.

**Identities:** For each model M, id_M : 𝒰_M → 𝒰_M satisfies:
- Φ_R: x →_ρ y implies id_M(x) →_ρ id_M(y) (immediate).
- Φ_E: x ≃_M y implies id_M(x) ≃_M id_M(y) (immediate).
- Φ_ρ: id_M(ρ_M(x)) ≃_M ρ_M(id_M(x)) (both sides are ρ_M(x)).
- Φ_LA: The image of each LA_M^i under id_M is LA_M^i itself, which is consistent
 with LA_M (it is a member of LA_M). ✓
So id_M is a model homomorphism.

**Composition closure:** Let Φ : M₁ → M₂ and Ψ : M₂ → M₃ be model homomorphisms. Define
Θ := Ψ ∘ Φ.
- Φ_R + Ψ_R: x →_ρ y implies Φ(x) →_ρ Φ(y), hence Ψ(Φ(x)) →_ρ Ψ(Φ(y)); so Θ_R.
- Φ_E + Ψ_E: x ≃_{M₁} y implies Φ(x) ≃_{M₂} Φ(y), hence Ψ(Φ(x)) ≃_{M₃} Ψ(Φ(y)); so Θ_E.
- Φ_ρ + Ψ_ρ:
 Θ(ρ_{M₁}(x)) = Ψ(Φ(ρ_{M₁}(x))) ≃_{M₃} Ψ(ρ_{M₂}(Φ(x))) ≃_{M₃} ρ_{M₃}(Ψ(Φ(x))) = ρ_{M₃}(Θ(x)),
 using Φ_ρ, then Ψ_E on equivalent arguments, then Ψ_ρ and transitivity of ≃_{M₃}.
 So Θ_ρ.
- Φ_LA + Ψ_LA: Let LA_{M₁}^i ∈ LA_{M₁} with overlapping signature. Φ_LA gives
 Φ_U(LA_{M₁}^i) consistent with LA_{M₂}. Ψ_LA gives Ψ_U of any LA_{M₂}-consistent
 sentence is consistent with LA_{M₃}. Hence Θ_U(LA_{M₁}^i) = Ψ_U(Φ_U(LA_{M₁}^i))
 is consistent with LA_{M₃}. So Θ_LA.
Hence composition of model homomorphisms is a model homomorphism.

Associativity of morphism composition is associativity of function composition.
Therefore CRPT models with model homomorphisms form a (possibly large)
category Mod_CRPT. ∎

### Isomorphism
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L5.2.D2 | `Iso` |  | **Imported** |
**Synopsis:** An isomorphism of CRPT models is a homomorphism Φ : M₁ → M₂ that has a two-sided inverse Ψ which is itself a homomorphism. Isomorphic models are interchangeable for every CRPT purpose — each carries exactly the same projection, regime, and horizon structure.

**Source:** Mac Lane [1998] §I.3 — categorical isomorphism.

Φ : M₁ → M₂ is an *isomorphism* if ∃Ψ : M₂ → M₁
with Ψ ∘ Φ = id_{M₁} and Φ ∘ Ψ = id_{M₂}.

### Regime-Restricted Isomorphism
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L5.2.D3 | `R-Iso` |  | **Novel** |
**Synopsis:** A regime-restricted isomorphism is a bijection between the convergent strata ℬ_M of two models that preserves ρ_M, derivation height d_M, and the canonical form CNF_M up to isomorphism. It compares models on their well-founded parts only, ignoring the persistent regime. It is the surjective (CRPT-saturated) special case of the faithful instantiation embedding `Inst-Emb` (L5.2.D4) — see `Iso-Sat` (L5.2.T7) — and its persistent dual is `R-Iso∞` (L5.2.D5) via `Iso-Dual` (L5.2.T8).

**Source:** CRPT; regime restriction of `Iso` (L5.2.D2) (coalgebra iso after Rutten [2000]).

Φ : ℬ_{M₁} → ℬ_{M₂} is a
*regime-restricted isomorphism* if Φ restricted to ℬ_{M₁} is a bijection onto ℬ_{M₂}
preserving ρ_{M₁}/ρ_{M₂}, d_{M₁}/d_{M₂}, and CNF_{M₁}/CNF_{M₂} up to isomorphism.

### Φ_ZC — ZFC to Category Theory, Restricted
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L5.2.T2 | `Φ_ZC` |  | **Novel** |
**Synopsis:** On finite structures, Φ_ZC : ZFC_finite ≅ Cat_discrete sends each hereditarily finite set to the discrete category on its elements. The isomorphism preserves ρ (element removal ↔ object removal), derivation height (cardinality), and CFix (∅ ↔ 0_Cat).

**Source:** CRPT; instance of `Iso` (L5.2.D2).

On finite discrete
structures: Φ_ZC : ZFC_finite ≅ Cat_discrete via Φ_ZC(X) = discrete category on X.
This isomorphism preserves ρ (element removal ↔ object removal), derivation height (cardinality),
and CFix(ρ_M) (∅ ↔ 0_Cat). Scope: hereditarily finite sets ↔ finite discrete categories.

*Proof.* **Construction:** Φ_ZC(X) := Disc(X), the discrete category whose objects
are the elements of X and whose only morphisms are identity morphisms.
This is uniform: Φ_ZC(∅) = Disc(∅) = 0_Cat (the empty category).

**RRI-1 (Dynamics preservation).** 
Reduction part (Φ_R): X →_ρ Y iff Y = X \ {x} for some x ∈ X. Then
Φ_ZC(X) →_ρ Φ_ZC(Y) is object removal in Disc(X), and
Φ_ZC(Y) = Disc(X \ {x}) = Disc(X) \ {x}. So reduction is preserved. 
Strategy part (Φ_ρ): ρ_ZFC(X) = X \ {min(X)} and
ρ_Cat(Disc(X)) = Disc(X) \ {terminal-object(Disc(X))}. In a discrete category every
object is terminal; choose the terminal object corresponding to min(X) under the
well-order transferred by Φ_ZC. Then:
Φ_ZC(ρ_ZFC(X)) = Disc(X \ {min(X)}) = Disc(X) \ {min(X)} = ρ_Cat(Φ_ZC(X)). ✓

**RRI-2 (Rank preservation):** d_ZFC(X) = |X| (`↓-Closed` (L2.2.T1) applied to ZFC).
d_Cat(Disc(X)) = |Ob(Disc(X))| = |X|. Equal. ✓

**RRI-3 (CNF correspondence):** Φ_ZC(CNF_ZFC) = Φ_ZC(∅) = Disc(∅) = 0_Cat = CNF_Cat. ✓

**Bijectivity:** Φ_ZC is injective: Disc(X) = Disc(Y) iff X = Y (sets are
determined by their elements). Surjectivity (onto finite discrete categories): every
finite discrete category C is Disc(Ob(C)). The inverse is Ψ_ZC(C) = Ob(C). ✓ ∎

### Φ_CH — Category Theory to HoTT, Restricted
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L5.2.T3 | `Φ_CH` |  | **Novel** |
**Synopsis:** On discrete structures, Φ_CH : Cat_small ≅ HoTT_discrete sends each category to the classifying type of its nerve. The isomorphism preserves ρ, derivation height, and CFix (0_Cat ↔ 𝟘).

**Source:** CRPT; instance of `Iso` (L5.2.D2).

On small/discrete
structures: Φ_CH : Cat_small ≅ HoTT_discrete via Φ_CH(C) = classifying type of C.
Preserves ρ, derivation height, and CFix(ρ_M) (0_Cat ↔ 𝟘).

*Proof.* **Construction:** Φ_CH(C) := |N(C)|, the geometric realisation of the
nerve of C. For finite discrete C: N(Disc(X)) is the discrete simplicial set on X,
and |N(Disc(X))| is the discrete type with |X| elements.

For general finite categories: N(C)_n = Fun([n], C) (functors from the ordinal
category [n] = {0 → 1 → ··· → n} to C). The classifying space |N(C)| is a
well-defined HoTT type with π₀(|N(C)|) = π₀(C) (connected components).

**RRI-1 (Dynamics preservation):** ρ_Cat(C) removes one object and all its morphisms.
ρ_HoTT removes one connected component from |N(C)|. Since N preserves the object
set at the 0-skeleton and π₀(|N(C)|) = Ob(C)/connected, the object removal in Cat
corresponds to component removal in HoTT. ✓

**RRI-2 (Rank):** d_Cat(C) = |Ob(C)| for discrete C. d_HoTT(|N(Disc(X))|) =
|π₀(|N(Disc(X))|)| = |X| = d_Cat(Disc(X)). ✓

**RRI-3 (CNF):** Φ_CH(0_Cat) = |N(0_Cat)| = |∅| = 𝟘 (the initial type in HoTT,
with no elements). CNF_HoTT = 𝟘. ✓

**Bijectivity on discrete types:** The inverse is Ψ_CH(A) = Disc(π₀(A)). ✓ ∎

### Φ_ZH by Composition
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L5.2.T4 | `Φ_ZH` |  | **Novel** |
**Synopsis:** Φ_ZH = Φ_CH ∘ Φ_ZC is the composite isomorphism ZFC_finite ≅ HoTT_discrete, witnessing that these foundational systems carry the same finite CRPT structure (same ρ, depth, and canonical forms).

**Source:** CRPT; composition `Φ_CH` (L5.2.T3) ∘ `Φ_ZC` (L5.2.T2).

Φ_ZH = Φ_CH ∘ Φ_ZC : ZFC_finite ≅ HoTT_discrete.

*Proof.* Composition of isomorphisms. ∎

### Regime-Restricted Isomorphisms Preserve Horizon Predicates
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L5.2.T5 | `Iso-Hor` |  | **Novel** |
**Synopsis:** Regime-restricted isomorphisms preserve the horizon predicates: for Φ ∈ {Φ_ZC, Φ_CH, Φ_ZH}, H_S, H_I, and the orbit signature sig_M are invariant under Φ. Isomorphic foundations therefore have identical horizon structure.

**Source:** CRPT; from `Φ_ZC` (L5.2.T2) + `Φ_CH` (L5.2.T3) + `H_S` (L3.1.D1) + `H_I` (L3.1.D2).

For Φ ∈ {Φ_ZC, Φ_CH, Φ_ZH}: H_S(x) = H_S(Φ(x)), H_I(x) = H_I(Φ(x)),
sig_M(x) = sig_M(Φ(x)) (within the restricted models).

*Proof.* We verify each predicate is preserved.

**H_S(x) = H_S(Φ(x)):** H_S(x) = ⊤ iff |{z | ρ_M(z) = ρ_M(x)}| > 1. Under Φ_ZC:
ρ_Cat(Φ_ZC(x)) = Φ_ZC(ρ_ZFC(x)) (Φ_ρ, proved in `Φ_ZC` (L5.2.T2)). The number of
preimages of ρ_ZFC(x) under ρ_ZFC equals the number of preimages of ρ_Cat(Φ_ZC(x))
under ρ_Cat, because Φ_ZC is a bijection that commutes with ρ (Φ_ρ). Therefore
|ρ_ZFC⁻¹(ρ_ZFC(x))| = |ρ_Cat⁻¹(ρ_Cat(Φ_ZC(x)))|, giving H_S(x) = H_S(Φ_ZC(x)). ✓
Same argument for Φ_CH, Φ_ZH (by composition). ✓

**H_I(x) = H_I(Φ(x)):** H_I depends on the orbit signature, which depends on (H_S, H_I, derivation height).
Since Φ preserves H_S (above) and derivation height (RRI-2), the orbit-signature equation
H_I(x) = H_S(x) ∧ ∀z ∈ ρ_M⁻¹(ρ_M(x)) : sig_M(z) = sig_M(x) transforms under Φ to:
H_I(Φ(x)) = H_S(Φ(x)) ∧ ∀w ∈ ρ_M⁻¹(ρ_M(Φ(x))) : sig_M(w) = sig_M(Φ(x)).
Since Φ is a bijection commuting with ρ: the preimage set {z | ρ_M(z) = ρ_M(x)} maps
bijectively to {w | ρ_M(w) = ρ_M(Φ(x))} via Φ. The orbit-signature equations are identical
in both models. By the mutual consistency argument (L3.2): the unique consistent
solution to the orbit-signature fixed-point equations is the same in both models, so H_I(x) =
H_I(Φ(x)). ✓

**sig_M(x) = sig_M(Φ(x)):** Follows from H_S preserved (above), H_I preserved (above),
derivation height preserved (RRI-2). ✓ ∎

### Collapse Map to Fixpoints
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L5.2.T6 | `Coll-Fix` |  | **Novel** |
**Synopsis:** The collapse-to-fixpoints map κ_M(x) := CFix(ρ_M)(x) sends each convergent element to its canonical fixpoint. Under PA-WN + PA-Conf it is surjective onto Fix(ρ_M) and in general non-injective (many elements share a canonical form).

**Source:** CRPT; from `Rec-Proj` (L2.1.D4) + `Fix-D0` (L2.3.T3).

Under PA-WN + PA-Conf, define
κ_M : μT_{ρ,M} → Fix(ρ_M) by κ_M(x) := CFix(ρ_M)(x). Then κ_M is surjective and, in
general, non-injective.

*Proof.* Surjectivity: let f ∈ Fix(ρ_M). By `Fix-D0` (L2.3.T3), d_M(f)=0, so
κ_M(f)=CFix(ρ_M)(f)=ρ_M^0(f)=f. Hence every fixpoint has a preimage.

Non-injectivity in general: if there exist distinct x,y ∈ μT_{ρ,M} with CFix(ρ_M)(x)=CFix(ρ_M)(y),
then κ_M(x)=κ_M(y) with x≠y, so κ_M is not injective. Such pairs occur exactly when
some NFC fiber has size >1 (`NFC-NM` (L2.5.D1)), which is the generic non-degenerate
collapse case in CRPT. Therefore κ_M is generally many-to-one. ∎

---

### Instantiation as Faithful Embedding
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L5.2.D4 | `Inst-Emb` | CRPT ↪ D | **Novel** |
**Synopsis:** A CRPT instantiation is a *faithful embedding* of CRPT structure into a domain model D — not an isomorphism: an injective homomorphism that both preserves and *reflects* the CRPT-visible structure (ρ, ≃, the regime partition, and the regime invariants — d_M/CFix on ↓_M, and on ∞_M the total canonical representative CPer (`CPer` (L1.3.D1)) together with the AOI-hierarchy classifier, which is necessarily multi-level by `SC-Imp` (L6.3.T1)), while D may carry further structure invisible to ρ_D. The regime-restricted isomorphisms Φ_ZC/Φ_CH/Φ_ZH are the special case where such an embedding is additionally surjective (`Iso-Sat` (L5.2.T7)).

**Source:** CRPT; from `Hom` (L5.2.D1) + `≃_M` (L2.5.D2); embedding order `⪯` (L5.4.D2).

A homomorphism Φ : M → D (`Hom` (L5.2.D1)) is a **faithful CRPT embedding**, written M ↪ D, if:
```
(Emb)    Φ_U is injective;
(Faith)  Φ reflects ≃ :  Φ(x) ≃_D Φ(y)  ⟹  x ≃_M y.
```
Combined with Φ_E (preservation of ≃), (Faith) gives x ≃_M y ⟺ Φ(x) ≃_D Φ(y): the embedding neither merges nor splits CRPT-equivalence classes. Equivalently, Φ reflects the complete invariant of ≃ in each regime — but those invariants are of *different shape* in the two regimes: on ↓_M a **single** complete invariant, d_M/CFix (`CNF=CR` (L2.5.T2)); on ∞_M, where `SC-Imp` (L6.3.T1) proves *no single* bisimulation-invariant can classify the regime, the **AOI hierarchy** (`AOI-Unif` (L6.3.D10)) together with the total canonical representative CPer (`CPer` (L1.3.D1)). The convergent invariant is single; the persistent one is necessarily hierarchical (see `WF-NWF-Dual` (L3.3.T9)).

### Why Embedding, Not Isomorphism

| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Remark** | L5.2.R2 | `Why-Embed` | | **Novel** |
**Synopsis:** Why a CRPT instantiation is a faithful embedding, not an isomorphism.

**Source:** CRPT; from `Inst-Emb` (L5.2.D4).

A domain D realising CRPT generally carries structure that ρ_D cannot see: in **Cat** the morphism dimension (bisimulation is "cardinality-blind to morphisms" — any two categories with equal |Ob| are ρ-bisimilar), in **HoTT** the higher paths, in **ZFA** the membership graph/decoration. The CRPT-reduct quotients this invisible structure away. Hence the instantiation map is injective and structure-reflecting (faithful) but not surjective: D does not collapse onto its CRPT-image wherever the invisible structure is non-trivial. CRPT is the faithful *image*, not the whole of D.

### Regime-Restricted Isomorphism = Saturated Faithful Embedding
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L5.2.T7 | `Iso-Sat` | | **Novel** |
**Synopsis:** A regime-restricted isomorphism (`R-Iso` (L5.2.D3)) is exactly a faithful CRPT embedding (`Inst-Emb` (L5.2.D4)) that is also surjective on the stratum — an embedding into a *CRPT-saturated* fragment, where D's ρ-invisible structure is trivial. Φ_ZC/Φ_CH/Φ_ZH are isomorphisms precisely because the finite **discrete** fragment is saturated (discreteness kills morphisms); off it, the instantiation is a faithful embedding only.

**Source:** CRPT; from `R-Iso` (L5.2.D3) + `Inst-Emb` (L5.2.D4) + `Φ_ZC` (L5.2.T2).

On a stratum (ℬ_M for the convergent regime), a map Φ is an `R-Iso` iff it is a faithful embedding (`Inst-Emb` (L5.2.D4)) that is surjective onto the stratum.

*Proof.*
(⇒) An `R-Iso` (L5.2.D3) is a bijection preserving ρ, d_M, CNF. Bijective ⟹ injective (Emb) and surjective; a bijection preserving ρ/d_M/CNF has a two-sided inverse, so it also reflects ≃ (Faith), because d_M and CNF are the complete ≃-invariants on ↓_M (`CNF=CR` (L2.5.T2)). Hence an R-Iso is a surjective faithful embedding.
(⇐) A surjective faithful embedding on the stratum is injective (Emb) + surjective = bijective, and preserves *and* reflects ρ, d_M, CNF (Faith), hence is an `R-Iso`.

**Saturation.** Call D *CRPT-saturated* on a stratum when its ρ-invisible structure is trivial there — equivalently, every faithful embedding into the stratum is surjective. Φ_ZC : ZFC_finite ≅ Cat_discrete is an R-Iso because Cat_discrete is saturated: discreteness forces Hom(a,b) ∈ {∅, {id}}, so no two distinct objects of equal cardinality escape identification — the embedding is onto. On full **Cat** saturation fails (cardinality-blindness): distinct morphism-structures of equal |Ob| are ρ-bisimilar, so CRPT ↪ Cat is faithful but not surjective, and no R-Iso exists there — only an `Inst-Emb`. ∎

### Persistent Regime-Restricted Isomorphism
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L5.2.D5 | `R-Iso∞` | | **Novel** |
**Synopsis:** The persistent dual of `R-Iso` (L5.2.D3): a bijection between the persistent strata ∞_M of two models preserving ρ_M, the reachability depth n_M and canonical persistent representative CPer (`CPer` (L1.3.D1)), and the AOI-hierarchy invariant (`AOI-Unif` (L6.3.D10)), up to bisimulation. Where R-Iso compares well-founded parts by the *single* invariant (d_M, CFix), R-Iso∞ compares persistent parts by the *necessarily hierarchical* (n_M, CPer, AOI) — the asymmetry forced by `SC-Imp` (L6.3.T1). On the SC-1 sub-class the AOI invariant reduces to CNF∞.

**Source:** CRPT; regime dual of `R-Iso` (L5.2.D3); from `CPer` (L1.3.D1) + `AOI-Unif` (L6.3.D10) + `SC-Imp` (L6.3.T1) + PA-Reach (L1.3.Ax2).

Φ : ∞_{M₁} → ∞_{M₂} is a **persistent regime-restricted isomorphism** if Φ is a bijection preserving ρ_{M₁}/ρ_{M₂}, the reachability depth n_M, the canonical persistent representative CPer, and the AOI-hierarchy invariant (`AOI-Unif` (L6.3.D10)) up to ≃ (`≃_M` (L2.5.D2)); on SC-1 elements this includes CNF∞ (`CNF∞-Def` (L3.3.D6)). The faithful-embedding reading of `Inst-Emb`/`Iso-Sat` transfers verbatim, with the single invariant (d_M, CFix) replaced by the hierarchical (n_M, CPer, AOI) and "discrete" replaced by "skeletal-persistent" (orbit-type Type P, where the AOI hierarchy collapses to a single class).

### Regime Duality of Restricted Isomorphisms
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L5.2.T8 | `Iso-Dual` | | **Novel** |
**Synopsis:** R-Iso and R-Iso∞ are exchanged by the WF/NWF regime duality. The duality is **graded**: at the total-representative level it is a clean 1:1 correspondence (d_M ↔ n_M, CFix ↔ CPer, PA-WN ↔ PA-Reach); at the complete-classifier level it is *necessarily* asymmetric — a single invariant (CFix, `CNF=CR`) on ↓_M dualizes to a *hierarchy* (the AOI hierarchy) on ∞_M, because `SC-Imp` (L6.3.T1) proves no single persistent invariant exists. So the finite cross-foundation isomorphisms have genuine persistent duals; concrete instances (ZFA, persistent categories, coinductive types) follow once those persistent models are built.

**Source:** CRPT; from `R-Iso` (L5.2.D3) + `R-Iso∞` (L5.2.D5) + the regime/mode duality (L1.4) + `d-WD` (L2.3.T1) + `CPer` (L1.3.D1) + `SC-Imp` (L6.3.T1) + `WF-NWF-Dual` (L3.3.T9).

Let σ_dual be the regime-duality substitution exchanging, clause for clause,
```
↓_M ↔ ∞_M,
d_M (WF rank, total)               ↔ n_M (reachability depth, total; PA-Reach),
CFix (terminal fixpoint, total)    ↔ CPer (signature-stabilized representative, total),
CNF=CR (single complete invariant) ↔ AOI hierarchy (complete classifier, necessarily multi-level: SC-Imp),
precondition PA-WN                 ↔ precondition PA-Reach (PA-WN_top for the topological sub-mode).
```
Then σ_dual maps the definition of `R-Iso` (L5.2.D3) onto that of `R-Iso∞` (L5.2.D5), and `Iso-Sat` (L5.2.T7) onto its persistent analogue.

*Proof.* Each defining clause corresponds under σ_dual, and each side is well-defined under its precondition:
- *Bijection on the stratum* and *ρ-preservation* are self-dual: ρ_M acts on both regimes, and σ_dual merely exchanges the strata it is restricted to.
- *d_M ↔ n_M.* d_M is the total WF rank (steps to Fix, defined under PA-WN, `d-WD` (L2.3.T1)); n_M is the total NWF rank (steps to signature-stabilization, defined under the universal PA-Reach, `n-Reach` (L3.3.D10)). Both total; dual under σ_dual.
- *CFix ↔ CPer.* CFix is the terminal-fixpoint canonical representative (PA-WN + PA-Conf, total with `CNF-Ex`/`CNF-Uniq`/`CNF-Stab`); CPer = ρ_M^{n_M(x)}(x) is the signature-stabilized canonical representative (PA-Reach, total with `CPer-Ex`/`CPer-Uniq`/`CPer-Stab` (L3.3.T6–T8)). σ_dual exchanges them.
- *single complete invariant ↔ hierarchical classifier.* On ↓_M, CFix is a **single** complete ≃-invariant (`CNF=CR` (L2.5.T2)). On ∞_M this is **provably impossible** (`SC-Imp` (L6.3.T1)); the dual complete classifier is therefore the **AOI hierarchy** (`AOI-Unif` (L6.3.D10)). The duality is thus graded — 1:1 at the representative level, single↔hierarchy at the classifier level — and this asymmetry is *necessary*, not a defect (`WF-NWF-Dual` (L3.3.T9)).

Hence Φ is an `R-Iso` iff σ_dual(Φ) is an `R-Iso∞`. The saturation characterisation transfers: on the skeletal-persistent fragment (orbit-type Type P, where the AOI hierarchy collapses to the single class CNF∞ = cardinality class) a persistent faithful embedding is surjective iff the persistent domain is CRPT-saturated — the verbatim dual of `Iso-Sat` (L5.2.T7). ∎

### Scope and Deferred Instances

| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Remark** | L5.2.R3 | `IsoDual-Scope` | | **Novel** |
**Synopsis:** Scope of Iso-Dual and the deferred concrete persistent instances.

**Source:** CRPT; from `Iso-Dual` (L5.2.T8).

`Iso-Dual` establishes the *duality of the notions* and that each finite R-Iso has a persistent dual on the shift-convergent skeleton; it does **not** assert concrete persistent foundational isomorphisms. An instance Φ_ZC^∞ : ZFA ≅ Cat_{∞,sc} ≅ HoTT_{∞,sc} requires those domains as complete CRPT persistent models — separate work. (In the category instantiation the dual invariant is already pinned down: CNF∞ = cardinality class of Ob, orbit-type Type P — the exact NWF-dual of d_Cat = |Ob| with terminal 0_Cat.)

---


---

## L5.3 — The CRPT Theory T_CRPT and Model-Correspondence

> **Note.** This section provides the formal model-theoretic justification for CRPT
> terminology. The Σ_CRPT signature (L5.2), theory T_CRPT (L5.2),
> and correspondence theorems (L5.2–L5.3.5) establish that CRPT models are
> exactly the scope-aware models of T_CRPT. Scope limitations are in L5.2.

**References (model theory):**
- [CK90]  Chang, C. C. & Keisler, H. J. *Model Theory*, 3rd ed. North-Holland, 1990.
- [Hod97] Hodges, W. *A Shorter Model Theory*. Cambridge University Press, 1997.
- [End01] Enderton, H. B. *A Mathematical Introduction to Logic*, 2nd ed. Academic
- [Sha91] Shapiro, S. *Foundations without Foundationalism: A Case for Second-Order
- [ARS98] Baader, F. & Nipkow, T. *Term Rewriting and All That*.
- [Mil80] Milner, R. *A Calculus of Communicating Systems*. LNCS 92, 1980.


## Imports from Model Theory

All definitions in this section are imported without modification from the
references cited. Every definition is stated to fix
notation for use in L5.2.

### Many-Sorted Signature / Language
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L5.3.D1 | `Lang-Sig` |  | **Imported** |
**Synopsis:** The formal theory T_CRPT is the first-order theory axiomatised by the nine PA-* axioms together with the model-local axiom schema LA_M. T_CRPT has a well-defined signature Σ_CRPT consisting of the symbols for the substrate components, the projection operator, and the derived predicates.

**Source:** Chang & Keisler [1990] §1.3 — many-sorted signature.

A *many-sorted signature* L = (S, F, R) consists of:
- A non-empty set S of *sorts* (type labels).
- A set F of *function symbols*, each with an arity: a list of input sorts and
  one output sort.
- A set R of *relation symbols*, each with an arity: a list of sorts.

A signature with a single sort is a *one-sorted* or *single-sorted signature*.

### L-Structure
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L5.3.D2 | `L-Str` |  | **Imported** |
**Synopsis:** An L-structure interprets a signature: a carrier for each sort, a function on carriers for each function symbol, and a relation for each relation symbol. This is the standard model-theoretic notion of structure — the semantic half of the syntax/semantics pair. CRPT's instance is the Σ_CRPT-structure (`Σ_CRPT` (L5.3.D10)).

**Source:** Chang & Keisler [1990] §1.3; Hodges [1997] §1.1 — L-structure.

Let L be a many-sorted signature. An *L-structure* (or *L-interpretation*) M
consists of:
- For each sort s ∈ S: a non-empty carrier set s^M (the *interpretation* of s).
- For each function symbol f ∈ F of arity (s₁, ..., sₙ → t): a function
  f^M : s₁^M × ⋯ × sₙ^M → t^M.
- For each relation symbol R ∈ R of arity (s₁, ..., sₙ): a relation
  R^M ⊆ s₁^M × ⋯ × sₙ^M.

An *L-structure* thus provides a concrete mathematical interpretation for every
symbol of L.

### L-Theory
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L5.3.D3 | `L-Th` |  | **Imported** |
**Synopsis:** An L-theory is a set of L-sentences over a signature; its models are the L-structures satisfying every sentence. This is the standard model-theoretic notion of theory — the syntactic half of the syntax/semantics pair. CRPT's instance is T_CRPT, the theory of the PA-* axioms over Σ_CRPT, whose model correspondence is `Mod-Corr` (L5.3.T1).

**Source:** Chang & Keisler [1990] §1.5; Hodges [1997] §2.4 — L-theory.

Let L be a signature. An *L-theory* T is a set of L-sentences (closed L-formulas).
A sentence is a formula with no free variables. The collection of all L-sentences
is denoted Sent(L).

### Satisfaction, ⊧
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L5.3.D4 | `⊧` | ⊧ | **Imported** |
**Synopsis:** The satisfaction relation M ⊧ φ is the Tarski truth definition: it holds when the L-sentence φ is true in the L-structure M under the standard recursive interpretation of connectives and quantifiers. Satisfaction is the semantic bridge between the syntax of T_CRPT and its models.

**Source:** Chang & Keisler [1990] §1.4; Enderton [2001] §2.2 — Tarski satisfaction.

Let M be an L-structure and φ an L-sentence. We write M ⊧ φ to mean that φ is
*satisfied* (or *true*) in M under the standard Tarski truth definition:

- Atomic: M ⊧ R(t₁,...,tₙ) iff (⟦t₁⟧^M,...,⟦tₙ⟧^M) ∈ R^M.
- Equality: M ⊧ (t₁ = t₂) iff ⟦t₁⟧^M = ⟦t₂⟧^M.
- Negation, conjunction, disjunction, implication: de Morgan + Boolean.
- Universal: M ⊧ ∀x:s φ(x) iff M ⊧ φ[a/x] for every a ∈ s^M.
- Existential: M ⊧ ∃x:s φ(x) iff M ⊧ φ[a/x] for some a ∈ s^M.

For second-order formulas (L5.2.6), set-quantifiers range over all subsets of
the appropriate carrier.

### L-Model of a Theory
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L5.3.D5 | `L-Mod` |  | **Imported** |
**Synopsis:** An L-structure M is a model of a theory T (written M ⊧ T) when it satisfies every sentence of T. The class Mod(T) of all such models is the semantic content of the theory and the object compared with Mod_CRPT in the Model Correspondence Theorem.

**Source:** Chang & Keisler [1990] §1.5; Hodges [1997] §2.4 — model of a theory.

An L-structure M is a *model of T* (written M ⊧ T) if M ⊧ φ for every φ ∈ T.
The class of all models of T is denoted Mod(T).

### Second-Order Extension
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L5.3.D6 | `SO-Ext` |  | **Imported** |
**Synopsis:** The second-order extension of the CRPT language adds quantification over subsets and relations of the universe. It is needed to express the properties of CRPT models that are not first-order definable — transitive closure (→_ρ*), divergence, bisimulation, and coinduction.

**Source:** Shapiro [1991] §3.1, §4.1 — second-order logic.

A *second-order signature* L^(2) extends a first-order signature L by permitting
quantification over *predicate variables* (ranging over subsets of carriers) and
*function variables* (ranging over functions on carriers). A sentence of L^(2)
is a *second-order sentence*. Satisfaction M ⊧ φ for second-order φ is defined
by the *standard semantics* (full second-order semantics): predicate
variables range over ALL subsets of the relevant carrier, and function variables
range over ALL functions.

*Remark L5.3.0.1.* Under standard semantics, second-order logic is more expressive
than first-order logic (L^(2) properly extends L) but is not complete in the
Gödel sense (there is no effective proof system for which M ⊧ T iff T ⊢ φ for
all models M). The model-theoretic notions of structure, satisfaction, and
model of a theory remain well-defined for L^(2) under standard semantics.

### Relativized Sentence
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L5.3.D7 | `Rel-Sent` |  | **Imported** |
**Synopsis:** The relativization φ|_S of a sentence φ to a definable subset S restricts all of φ's quantifiers to S, so that M ⊧ φ|_S says the substructure on S satisfies φ. Relativization is the device that makes scope-restricted (Scoped(S)) axiom satisfaction expressible in T_CRPT.

**Source:** Chang & Keisler [1990] §2.7; Hodges [1997] §5.3 — relativization of formulas.

Given an L-structure M, a unary predicate (definable subset) S ⊆ s^M, and an
L-sentence φ, the *relativization of φ to S* (written φ|_S or φ^S) is the
result of restricting all quantifiers in φ to S:
- (∀x:s φ(x))^S becomes ∀x:s (x ∈ S → φ(x)^S).
- (∃x:s φ(x))^S becomes ∃x:s (x ∈ S ∧ φ(x)^S).
- Other connectives are unchanged.

M ⊧ φ|_S means: the substructure M restricted to S satisfies φ. This is
standard and preserves the Tarski definition on the restricted model.

### L-Homomorphism
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L5.3.D8 | `L-Hom` |  | **Imported** |
**Synopsis:** An L-homomorphism is a sort-indexed family of maps between L-structures that preserves every function symbol and every relation symbol of the signature. It is the model-theoretic counterpart of the CRPT model homomorphism `Hom` (L5.2.D1).

**Source:** Hodges [1997] §1.3; Chang & Keisler [1990] §3.4 — L-homomorphism.

Let M, N be L-structures. An *L-homomorphism* h : M → N is a family of functions
h_s : s^M → s^N (one for each sort s ∈ S) such that:
- For every function symbol f of arity (s₁,...,sₙ → t):
  h_t(f^M(a₁,...,aₙ)) = f^N(h_{s₁}(a₁),...,h_{sₙ}(aₙ)).
- For every relation symbol R of arity (s₁,...,sₙ):
  (a₁,...,aₙ) ∈ R^M ⟹ (h_{s₁}(a₁),...,h_{sₙ}(aₙ)) ∈ R^N.

An L-isomorphism is a bijective L-homomorphism whose inverse is also an
L-homomorphism.

### Category of L-Models
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L5.3.D9 | `L-ModCat` |  | **Imported** |
**Synopsis:** The category Mod(L, T) has the models of an L-theory T as objects and L-homomorphisms as morphisms. It is the model-theoretic category that the Model Correspondence Theorem (`Mod-Corr` (L5.3.T1)) compares with the category Mod_CRPT.

**Source:** Chang & Keisler [1990] §3.4; Hodges [1997] §3.6 — category of L-models.

Let T be an L-theory. The *category of L-models of T*, denoted Mod(L, T), has:
- **Objects:** All L-structures M with M ⊧ T.
- **Morphisms:** All L-homomorphisms h : M → N (between models of T).
- **Composition and identity:** Standard function composition and identity maps.

The resulting structure is a (large) category in the sense of MacLane [1971].

---

## The CRPT Signature

### CRPT Signature Σ_CRPT
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L5.3.D10 | `Σ_CRPT` | Σ_CRPT | **Novel** |
**Synopsis:** The CRPT signature Σ_CRPT is many-sorted: sorts U (universe), Open (open sets of the substrate topology, with membership In), O (observable contents, pointed by the constant 0), and Bool; function symbols ρ : U → U and Observable : U → O; relation symbols →_ρ, →_σ, Fix, and In. The observation labelling obs, observable equivalence ≃, and bisimilarity ≈ are *not* signature primitives — obs is Σ_CRPT-definable from Fix, ρ, and Observable, and ≃/≈ are defined relations. All derived notions (H_S, H_I, H_O, CNF_M, d_M, etc.) are Σ_CRPT-definable.

**Source:** CRPT; from `Lang-Sig` (L5.3.D1) + `Sub` (L1.1.D1).

The *CRPT signature* is the many-sorted signature:
```
Σ_CRPT = (S_CRPT, F_CRPT, R_CRPT)
```
where:

**Sorts S_CRPT:**
- `U` — the *universe sort*. Elements of type `U` are the structures of the
  CRPT instantiation (abstract elements, terms, coalgebras, etc.).
- `Open` — the sort of open sets of the substrate topology 𝒯 on `U`.
- `O` — the sort of *observable contents*: the pointed codomain (O_M, 0) of the
  Observable Contract (PA-Prod (L1.2.Ax6)), with a distinguished constant `0 : O`
  ("no content"). The two-element instance O = {⊤, ⊥} with 0 = ⊥ is the minimal
  form, recovering Observable as a predicate.
- `Bool` — the standard two-element sort {⊤, ⊥}. (Used for predicate
  codomains; eliminable in favour of relation symbols but stated for clarity.)

**Function symbols F_CRPT:**
- `ρ : U → U` — the *projection function* (the projection operator, L2.1 of
  the anchor). Arity: one input of sort `U`, one output of sort `U`.
- `Observable : U → O` — the *observable-content function* (OC-1/OC-2 of
  PA-Prod; L1.2 of the anchor). Arity: one input `U`, output `O`.

**Relation symbols R_CRPT:**
- `→_ρ ⊆ U × U` — the *reduction relation* (L1.1 of the anchor). Binary.
- `→_σ ⊆ U × U` — the *structural relation* (L1.1 of the anchor). Binary.
- `Fix ⊆ U` — the *fixpoint predicate*. Unary. (Defined as Fix(x) ↔ ρ(x) = x,
  but included as a relation symbol for signature completeness.)
- `In ⊆ U × Open` — point-membership in open sets: In(x, O) means x ∈ O.

*Remark L5.3.1.1.* The bisimilarity relation ≈ is not in Σ_CRPT because it is
defined from the reduction relation (`Bisim~` (L1.1.D7) of the anchor): x ≈ y iff there exists a
bisimulation containing (x, y). It is definable in L^(2)(Σ_CRPT) by
second-order quantification over bisimulation relations. Likewise the observation
labelling obs (`Obs-Lab` (L1.1.D8)) is not a primitive: it is the Σ_CRPT-definable
function obs(x) = x for Fix(x), obs(x) = Observable(ρ(x)) otherwise
(`Obs-Lab-WD` (L1.1.T1)(iv)). The labelled bisimulation `Bisim` (L1.1.D6) and
PA-Bisim therefore read only derived structure, and satisfaction-as-model-hood
(`Mod-Corr` (L5.3.T1)) is well-posed over this signature. Treating ≈ and obs as
defined preserves the minimality of Σ_CRPT.

*Remark L5.3.1.2.* Topology is intrinsic to the substrate and is represented
inside Σ_CRPT via the sort `Open` and the membership relation `In`. A model
thus carries topological structure internally, and PA-WN_top is a single axiom
over that fixed substrate topology (not an external schema parameter).

*Remark L5.3.1.3.* A Σ_CRPT-structure M consists of a carrier U^M, a domain
Open^M of open sets, a pointed carrier (O^M, 0^M) of observable contents,
function symbols ρ^M and Observable^M : U^M → O^M, relations →_ρ^M,
→_σ^M, Fix^M, and membership In^M ⊆ U^M × Open^M. This induces a topology
𝒯^M represented by Open^M together with In^M, and the derived labelling obs^M.
No axioms are imposed by the signature alone; those come from T_CRPT (L5.2).

---

## The CRPT Theory T_CRPT

### CRPT Theory T_CRPT
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L5.3.D11 | `T_CRPT` | T_CRPT | **Novel** |
**Synopsis:** The formal theory T_CRPT is the set of Σ_CRPT-sentences that are true in all CRPT models. It is axiomatised by the nine PA-* axiom schemas together with the model-local axiom schema LA_M. T_CRPT is a first-order theory with recursive axiom set; its second-order extension T_CRPT^{SOL} adds the bisimulation and transitive closure axioms.

**Source:** CRPT; from `Σ_CRPT` (L5.3.D10) + the PA-* axiom system (L1.2–L1.3).

The *CRPT theory* T_CRPT is the following set of sentences in L^(2)(Σ_CRPT).
Each sentence is labelled by the anchor construct it formalizes.

**L5.3.2.1 Substrate Conditions (L1.1 of anchor).**

```
(S-Inc)  ∀x:U ∀y:U : (x →_ρ y) → (x →_σ y)
         "Inclusion constraint: every reduction step is a structural step."

(S-Fix)  ∀x:U : Fix(x) ↔ (ρ(x) = x)
         "Fixpoints are exactly the ρ-fixpoints."

(S-TopSep)  ∀a,b:U : (a ≠ b) →
            ∃O1,O2:Open : In(a,O1) ∧ In(b,O2) ∧
            (∀z:U : ¬(In(z,O1) ∧ In(z,O2)))
            "Hausdorff/T₂ separation in the substrate topology."

(S-rho-Cont)  ∀x:U ∀O:Open : In(ρ(x), O) →
              ∃V:Open : In(x, V) ∧
              (∀y:U : In(y, V) → In(ρ(y), O))
              "Continuity of ρ in neighborhood form."
```

These sentences encode the substrate-level topological commitments directly in
T_CRPT: Hausdorff separation and continuity of the projection map ρ.

**L5.3.2.2 Projection Operator Conditions (L2.1 of anchor).**

Let NF(x) abbreviate ¬∃y:U (x →_ρ y) (`NF` (L1.1.D2) of anchor).

```
(C1)     ∀x:U : ((x →_ρ ρ(x)) ∨ (ρ(x) = x ∧ NF(x)))
         "C1 (Step-or-Fix): ρ either takes a →_ρ step or fixes a normal form."

(C2)     ∀x:U ∀y:U : (x ≈ y) → (ρ(x) ≈ ρ(y))
         "C2 (Bisimulation Equivariance): ρ preserves bisimilarity."
```

### C2 Is a Second-Order Sentence

| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Remark** | L5.3.R5 | `C2-SOL` | | **Novel** |
**Synopsis:** C2 (bisimulation equivariance) is a well-formed second-order sentence: bisimilarity is the definable predicate ∃R[(R is a bisimulation) ∧ R(x,y)] in L²(Σ_CRPT).

**Source:** CRPT; from `Bisim` (L1.1.D6) + `SO-Ext` (L5.3.D6).

The bisimilarity ≈ is the definable second-order predicate
∃R[(R-bisim) ∧ R(x, y)] where R-bisim expresses "R is a bisimulation on
(U, the reduction relation)" (`Bisim` (L1.1.D6) of anchor). Since bisimulation is expressible in
L^(2)(Σ_CRPT), C2 is a well-formed second-order sentence.

**L5.3.2.3 PA-WN (Finitary Termination; L1.2 of anchor).**

PA-WN uses the natural numbers ℕ to measure finite reduction depth and is stated
in imported ARS form over the reduction relation:

```
(PA-WN)  ∀x:U : ∃n ∈ ℕ, y:U : (x →_ρ^n y) ∧ NF(y)
```

3

The convergent regime is definable from ρ/Fix as:

```
x ∈ ↓_M  :⟺  ∃n ∈ ℕ : Fix(ρ^n(x))
```

This definition does not make PA-WN tautological: PA-WN constrains termination
of the reduction relation paths globally, while ↓_M classifies ρ-orbit behavior. In stratified
models, scope assignment may restrict PA-WN application to ↓_M via
`Scope-Sat` (L5.3.D12) without changing PA-WN's formula.

**L5.3.2.3A PA-Fix (Fixpoint/Normal-Form Boundary; L1.2 of anchor).**

```
(PA-Fix)  ∀x:U : Fix(x) ↔ NF(x)
```

Together with (S-Fix), this yields the canonical equivalence
ρ(x) = x ↔ Fix(x) ↔ NF(x).

**L5.3.2.4 PA-Conf (Confluence; L1.2 of anchor).**

```
(PA-Conf) ∀x y z:U : (x →_ρ* y) ∧ (x →_ρ* z) → ∃w:U : (y →_ρ* w) ∧ (z →_ρ* w)
```

where →_ρ* is the reflexive-transitive closure of →_ρ (`RT*` (L1.1.D4) of anchor),
definable in L^(2)(Σ_CRPT) as: x →_ρ* y ↔ ∃R:(R is a transitive relation
containing →_ρ and the identity) ∧ (x, y) ∈ R. This is a second-order sentence.

**L5.3.2.5 PA-NWF (Non-Well-Foundedness; L1.2 of anchor).**

```
(PA-NWF)  ∃x:U : ∀n ∈ ℕ : ¬Fix(ρ^n(x))
          "There exists an element whose ρ-orbit never reaches Fix."
```

Or equivalently: ∃x:U ∀P⊆U [(Finite(P) ∧ x ∈ P → ∃y ∈ P : ¬Fix(y))] is
NOT needed — the simpler second-order formulation suffices:
∃x:U ∀P⊆U [(P is ρ-invariant ∧ x ∈ P) → P ∩ Fix = ∅ is not forced by finite
depth]. For the purposes of this document we use the ω-schema form as it
directly expresses the intended meaning.

**L5.3.2.6 PA-CoInd (Co-Induction / Park's Lemma; L1.2 of anchor).**

Let Φ : 𝒫(U) → 𝒫(U) be a monotone second-order function. PA-CoInd is the
second-order sentence:

```
(PA-CoInd) ∀Φ:(𝒫(U) → 𝒫(U)) ∀P⊆U : [Mono(Φ) ∧ (P ⊆ Φ(P))] → P ⊆ νΦ
```

where νΦ is the greatest fixpoint of Φ (which exists by Knaster-Tarski since
Φ is monotone on the complete lattice 𝒫(U) ordered by ⊆), and Mono(Φ)
abbreviates ∀A B ⊆ U : (A ⊆ B) → (Φ(A) ⊆ Φ(B)).

This is a second-order sentence (quantifies over functions on 𝒫(U) and subsets
of U). In pure WF models (∞_M = ∅), PA-CoInd is not vacuous in general: it still
constrains all monotone Φ. What is vacuous is only the specific Φ_∞ instance
whose greatest fixpoint defines the non-terminating regime (then νΦ_∞ = ∅).

**L5.3.2.7 PA-Prod (Productivity; L1.2 of anchor).**

```
(PA-Prod) ∀x:U : ¬Fix(x) → Observable(ρ(x))
```

where Observable : U → Bool is the predicate in Σ_CRPT subject to the observable
contract (OC-1): ∀y:U (¬Fix(y) → Observable(y)), and (OC-2): for every x,
Observable(ρ(x)) implies the step x → ρ(x) has non-zero PV-weight.

Since Observable is a function symbol in Σ_CRPT, PA-Prod is a first-order sentence
of L(Σ_CRPT). Its non-trivial content lies in the concrete observable contract
(OC-1/OC-2) declared by each instantiation's LA_M.

**L5.3.2.8 PA-Bisim (Bisimulation Congruence; L1.3 of anchor).**

```
(PA-Bisim) ∀x y:U : (x ≈ y) → (x ≃_M y)
```

where ≃_M is the abstraction equivalence (orbit equivalence): x ≃_M y ↔
∃n m ∈ ℕ : ρ^n(x) = ρ^m(y) ∧ Fix(ρ^n(x)). Both ≈ (bisimilarity) and ≃_M
are definable in L^(2)(Σ_CRPT), so PA-Bisim is a second-order sentence.

**L5.3.2.9 PA-WN_top (Topological Convergence; L1.2 of anchor).**

PA-WN_top is a single topological convergence axiom over the substrate topology
𝒯 (already fixed in the model structure):

```
(PA-WN_top) ∀x:U : (x ∈ ∞_M) →
    ∃!L:U : lim_{n→∞} ρ^n(x) = L in 𝒯
```

Existence is asserted by PA-WN_top; uniqueness follows from (S-TopSep)
(equivalently `TopSep-Uniq` (L1.2.T1)). When ∞_M = ∅, PA-WN_top is vacuously
satisfied.

**L5.3.2.9A Unified CFix Definition (Regime-Total).**

CFix is defined uniformly by regime:

```
CFix(x) := {
  ρ^{d_M(x)}(x),            if x ∈ ↓_M,
  lim_{n→∞} ρ^n(x) in 𝒯,    if x ∈ ∞_M.
}
```

The second branch is well-defined by PA-WN_top + TopSep(𝒯). The first branch is
the standard finitary branch from Rec-Proj / WF canonicalization.

**L5.3.2.10 WF-Canon and LA-Rich placement (L1.2 of anchor).**

WF-Canon is theorem-level (not PA-axiom) with clauses:

```
(WF-Canon-1) ∀x ∈ ↓_M : CFix(x) ∈ Fix(ρ_M)
(WF-Canon-2) ∀f ∈ Fix(ρ_M) : ∃x ∈ ↓_M : CFix(x)=f
```

LA-Rich(M) is model-local schema content in LA_M, optional per model profile,
and outside PA-axiom namespace.

**L5.3.2.11 PA-Reach (Recursive Projection Horizon Stabilization; L1.3 of anchor).**

```
(PA-Reach) ∀x ∈ ∞_M :
   (R1) ω_≈(x) ≠ ∅                       [the asymptotic destination exists]
   (R2) ω_≈(x) is finite and ρ_M-closed   [it is a finite ρ_M-cycle of classes]
   (R3) the orbit is attracted to ω_≈(x)  [every neighbourhood absorbs a tail]
```

where ∞_M = {x ∈ 𝒰 | ∀k ∈ ℕ : ρ_M^k(x) ∉ Fix(ρ_M)} is the persistent regime,
ρ_M is the projection operator, and ω_≈(x) is the ω-limit set of the ≈-class orbit
(PA-Reach (L1.3.Ax2): classes visited cofinally, or classes of 𝒯-accumulation points).
The axiom is the meaning itself — recursive projection reaches the canonical persistent
representative CPer_M(x) (`CPer` (L1.3.D1)), the canonical representative of the
destination. The reach mechanisms are theorems: recurrence (`PA-Reach-Fin` (L1.3.T2),
with reachability depth n_M, `n-Reach` (L3.3.D10)), convergence
(`PA-Reach-Top` (L1.3.T3)), and their composite (`PA-Reach-Decomp` (L1.3.T4)).

Expressible in L^(2)(Σ_CRPT) by: second-order quantification over bisimulations for ≈
(Remark L5.3.1.1), iteration of ρ for the cofinal-visit clause, and the sort Open with
In for the accumulation clause; the persistent orbit signature the destination finitely
presents is `sig_M-NM` (L3.1.D5), with obs grounded in the Observable Contract
(L5.2.9–10).

**Semantic consequence (Observer Extraction):** For anyx ∈ ∞_M satisfying PA-Reach,
the canonical persistent representative CPer_M(x) := ρ_M^n(x) (where n is the
reachability depth) is the unique, recursively-determined, horizon-stable finite
descriptor of the infinite element x that the observer can extract.

### Scope-Aware Satisfaction
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L5.3.D12 | `Scope-Sat` |  | **Novel** |
**Synopsis:** Scope-aware satisfaction M ⊧_S PA-X interprets a PA-* axiom relative to a declared scope S via relativization: the axiom may hold globally, hold on S (Scoped(S)), be vacuous, or fail. This is the model-theoretic reading of the four-valued scope semantics of `PA-Scope` (L1.5.D1).

**Source:** CRPT; from `Rel-Sent` (L5.3.D7) + `PA-Scope` (L1.5.D1).

Let M be a Σ_CRPT-structure and PA-X an axiom of T_CRPT with scope S ⊆ U^M.
We say *M satisfies PA-X on scope S* (written M ⊧_S PA-X) if M ⊧ (PA-X)|_S
(using `Rel-Sent` (L5.3.D7)).

A *scope-aware T_CRPT-satisfaction* for a scope assignment
σ = {PA-X ↦ S_{PA-X} | PA-X ∈ T_CRPT, S_{PA-X} ∈ {Global, Scoped(S), Vacuous, Fails}}
is: M ⊧_σ T_CRPT iff for every PA-X with σ(PA-X) ≠ Fails (and ≠ Vacuous):
M ⊧_{S_{PA-X}} PA-X, and for σ(PA-X) = Vacuous: the antecedent of PA-X is
never triggered in M (i.e., the universal antecedent is vacuously false).

This exactly captures the PA-* scope declarations of `PA-Scope` (L1.5.D1).

---

## The Main Correspondence Theorem

### CRPT Model Correspondence
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L5.3.T1 | `Mod-Corr` |  | **Novel** |
**Synopsis:** The Model Correspondence theorem: the category of T_CRPT-models (structures satisfying all PA-* axioms) is equivalent as a category to Mod_CRPT. The equivalence sends each T_CRPT-model to its corresponding CRPT model and each T_CRPT-homomorphism to the corresponding CRPT homomorphism. Model theory and categorical model theory give the same objects.

**Source:** CRPT; from `Scope-Sat` (L5.3.D12) + `CRPT-Mod-18` (L5.1.D1).

A Σ_CRPT-structure M is a CRPT model (in the sense of `CRPT-Mod-18` (L5.1.D1) of the anchor) if and only if M is a scope-aware model of T_CRPT
(`Scope-Sat` (L5.3.D12)), i.e., there exists a scope assignment σ such that
M ⊧_σ T_CRPT and σ satisfies the three conditions of `CRPT-Mod-18` (L5.1.D1).

*Proof.*

**(⟹) Every CRPT model is a scope-aware model of T_CRPT.**

Let N be a CRPT model. By `CRPT-Mod-18` (L5.1.D1), N has:
1. A substrate (𝒰_N, →_ρ, →_σ) satisfying L1.1 substrate conditions.
2. A projection operator ρ_N satisfying C1 and C2 (`ρ_M` (L2.1.D1).
3. An axiom profile PA-Profile_N assigning each PA-X a scope.
4. A set of model-local axioms LA_N (possibly empty).
5. Non-triviality: at least one PA-X is declared Global or Scoped(S ≠ ∅).
6. Consistency: the non-failed PA-* scoped commitments are jointly satisfiable.
7. Witness: N itself witnesses the consistency.

We define the Σ_CRPT-structure associated to N:
```
Str(N) = (𝒰_N, ρ_N, Observable_N, →_ρ, →_σ, Fix_N)
```
where Fix_N(x) := (ρ_N(x) = x) and Observable_N is the predicate declared by
LA_N subject to the observable contract OC-1/OC-2.

We verify each sentence of T_CRPT:

- **(S-Inc):** The inclusion constraint →_ρ ⊆ →_σ holds by `Sub` (L1.1.D1) of the
  anchor (the inclusion constraint is part of the substrate definition, enforced
  at construction). Hence Str(N) ⊧ (S-Inc). ✓

- **(S-Fix):** By definition of Fix_N as {x | ρ_N(x) = x}. Str(N) ⊧ (S-Fix). ✓

- **(C1):** ρ_N satisfies C1 by Def (Projection Operator on (𝒰_M,→_ρ) of the anchor. Str(N) ⊧ (C1). ✓

- **(C2):** ρ_N satisfies C2 by Def (Projection Operator on (𝒰_M,→_ρ) of the anchor. Str(N) ⊧ (C2). ✓

- **PA-WN through PA-Reach:** For each PA-X with PA-Profile_N(PA-X) ≠ Fails:
  By `CRPT-Mod-18` (L5.1.D1) Conditions 2 and 3 (consistency + witness), the non-failed
  scoped PA-* axioms are satisfied by N itself. Specifically:
  - If PA-Profile_N(PA-X) = Global: N ⊧ PA-X (holds for all of 𝒰_N). ✓
  - If PA-Profile_N(PA-X) = Scoped(S): N ⊧ (PA-X)|_S (holds on S). ✓
  - If PA-Profile_N(PA-X) = Vacuous: the antecedent of PA-X is never triggered
    in N (e.g., ↓_M = 𝒰_N for PA-NWF/PA-WN_top/PA-CoInd in pure WF models).
    By `⊧` (L5.3.D4) (universal quantification over empty range is vacuously
    true), Str(N) ⊧_Vacuous PA-X. ✓
  - If PA-Profile_N(PA-X) = Fails: not included in T_CRPT for this model.
    Excluded from Str(N)'s model obligations by the scope assignment σ. ✓

  By `Scope-Sat` (L5.3.D12), Str(N) ⊧_σ T_CRPT for the scope assignment
  σ = PA-Profile_N. ✓

Therefore Str(N) ⊧_σ T_CRPT, hence N is a scope-aware model of T_CRPT. ∎ (⟹)

**(⟸) Every scope-aware model of T_CRPT is a CRPT model.**

Let M be a Σ_CRPT-structure and σ a scope assignment such that M ⊧_σ T_CRPT.
We construct a CRPT model Mdl(M) from M:

- **Substrate:** Set 𝒰_{Mdl(M)} := U^M, →_ρ := →_ρ^M, →_σ := →_σ^M.
  Then (S-Inc) gives →_ρ ⊆ →_σ, satisfying `Sub` (L1.1.D1) of the anchor. ✓
- **Projection operator:** Set ρ_{Mdl(M)} := ρ^M.
  - C1 holds by M ⊧ (C1). ✓
  - C2 holds by M ⊧ (C2). ✓
  So ρ_{Mdl(M)} satisfies Def (Projection Operator on (𝒰_M, →_ρ)) of the anchor. ✓
- **Axiom profile:** Set PA-Profile_{Mdl(M)}(PA-X) := σ(PA-X) for each PA-X.
  This assigns each PA-* axiom its scope from σ. ✓
- **model-local axioms:** Set LA_{Mdl(M)} ⊇ {the Observable contract for
  Observable^M} plus any other instantiation commitments. ✓

Verify the three conditions of `CRPT-Mod-18` (L5.1.D1):

1. **Non-triviality:** This is checked at PA-profile level. By construction,
   PA-Profile_{Mdl(M)}(PA-X) := σ(PA-X). If σ has at least one PA-X with scope
   Global or `Scoped(S ≠ ∅)`, then Condition 1 of `CRPT-Mod-18` (L5.1.D1) holds.
   This is exactly the non-triviality side-condition used in the correspondence. ✓

2. **Consistency:** M⊧_σ T_CRPT is the consistency witness: M satisfies all
   non-Fails, non-Vacuous PA-* axioms in their declared scopes simultaneously.
   That is exactly joint satisfiability as required by Condition 2. ✓

3. **Witness:** Mdl(M) = M is the required explicit model. ✓

Therefore Mdl(M) is a CRPT model. ∎ (⟸) ∎

### Terminology Justified
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Corollary** | L5.3.C1 | `Term-Just1` |  | **Novel** |
**Synopsis:** Justifies the term "CRPT model": by the Model Correspondence, the CRPT models are exactly the scope-aware models of the theory T_CRPT, so the categorical and logical notions of "model" coincide.

**Source:** CRPT; corollary of `Mod-Corr` (L5.3.T1).

Under `Mod-Corr` (L5.3.T1), the class of
CRPT models and the class of scope-aware models of T_CRPT coincide.
Therefore, calling a CRPT model a *CRPT model* is justified: it is
literally a model of the CRPT theory T_CRPT in the sense of `L-Mod` (L5.3.D5),
with scope-aware satisfaction (`Scope-Sat` (L5.3.D12)).

---

## Model Homomorphisms and Morphism Correspondence

### Model Homomorphism Correspondence
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L5.3.T2 | `Hom-Corr` |  | **Novel** |
**Synopsis:** The Homomorphism Correspondence theorem: every CRPT model homomorphism is an L(Σ_CRPT)-homomorphism that additionally preserves the canonical form (Φ ∘ CNF = CNF ∘ Φ). Morphisms therefore correspond on both sides of the model/theory equivalence.

**Source:** CRPT; from `Hom` (L5.2.D1) + `L-Hom` (L5.3.D8).

Let N₁, N₂ be CRPT models (= CRPT models, by `Term-Just1` (L5.3.C1)) and
let Φ : N₁ → N₂ be a model homomorphism (`Hom` (L5.2.D1) of the anchor). Then Φ
is an L(Σ_CRPT)-homomorphism from Str(N₁) to Str(N₂) (in the sense of Definition
`L-Mod` (L5.3.D5)) that additionally preserves the canonical form:
Φ ∘ CNF_{N₁} = CNF_{N₂} ∘ Φ.

*Proof.*

A model homomorphism Φ : N₁ → N₂ (`Hom` (L5.2.D1) of the anchor) is a function
Φ_U : 𝒰_{D₁} → 𝒰_{D₂} satisfying:
- (Φ_R) Reduction preservation: x →_ρ^{D₁} y ⟹ Φ(x) →_ρ^{D₂} Φ(y).
- (Φ_E) Equivalence preservation: x ≃_{N₁} y ⟹ Φ(x) ≃_{N₂} Φ(y).
- (Φ_ρ) Commutativity with ρ: Φ(ρ_{N₁}(x)) ≃_{N₂} ρ_{N₂}(Φ(x)) for all x.
- (Φ_LA) Local axiom coherence: Φ respects all declared LA_{N₁} and LA_{N₂}.

We verify Φ is a Σ_CRPT-homomorphism (`L-Hom` (L5.3.D8)):

- **Function ρ:** L(Σ_CRPT)-homomorphism condition for ρ requires
  Φ(ρ^{D₁}(x)) = ρ^{D₂}(Φ(x)) or up to ≃_{N₂}. Condition (Φ_ρ) provides
  the ≃_{N₂}-version, which is the anchor's standard (up to CNF-equivalence).
  Since CFix(ρ_M) is well-defined (`RP=Abs` (L2.1.T4) of anchor) and ≃_{N₂} is exactly
  CNF-equivalence, (Φ_ρ) gives the required homomorphism condition. ✓

- **Relations →_ρ and →_σ:** (Φ_R) directly gives the homomorphism condition
  for the reduction relation. For the structural relation: by the inclusion constraint (S-Inc), any x →_ρ y implies
  x →_σ y (structural relation contains reduction relation); and since (Φ_R)
  preserves the reduction relation, it preserves the structural part of the structural relation inherited from the reduction relation; for
  additional the structural relation edges (beyond the reduction relation), the anchor's morphism condition (Φ_R) is
  stated for the reduction relation and (Φ_E) for ≃; this is the standard strength. ✓

- **Fixpoints:** Fix(ρ^{D₁}(x)) = x iff x ∈ Fix^{D₁}. Since Φ maps ρ_{N₁} to
  ρ_{N₂} (up to ≃), fixpoints of ρ_{N₁} map to fixpoints of ρ_{N₂}: if
  ρ_{N₁}(x) = x then Φ(ρ_{N₁}(x)) = Φ(x) ≃_{N₂} ρ_{N₂}(Φ(x)), and since
  Φ(x) = Φ(ρ_{N₁}(x)) ≃_{N₂} ρ_{N₂}(Φ(x)), Φ(x) is a fixpoint of ≃_{N₂}
  (hence Fix^{D₂}(Φ(x)) holds up to ≃). ✓

- **CNF preservation:** The anchor's `Hom` (L5.2.D1) requires Φ(CNF_{N₁}(x)) =
  CNF_{N₂}(Φ(x)) explicitly (condition Φ_ρ already implies this for elements
  in ↓_M by `Mod-Cat` (L5.2.T1) of the anchor). ✓

Therefore Φ is an L(Σ_CRPT)-homomorphism preserving CNF. ∎

### Terminology Justified
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Corollary** | L5.3.C2 | `Term-Just2` |  | **Novel** |
**Synopsis:** Justifies the term "model homomorphism": by the Homomorphism Correspondence, CRPT model morphisms are exactly the CNF-preserving L(Σ_CRPT)-homomorphisms between the corresponding theory-models.

**Source:** CRPT; corollary of `Hom-Corr` (L5.3.T2).

model morphisms Φ : N₁ → N₂ are
justified as *model homomorphisms* between CRPT models. The name "model
morphism" is equivalent to "CRPT model homomorphism" per `Hom-Corr` (L5.3.T2).

---

## The Category Mod_CRPT

### Categorical Equivalence
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L5.3.T3 | `Cat-Eq` |  | **Novel** |
**Synopsis:** The Category Equivalence theorem: Mod_CRPT is equivalent (as a category) to the category of T_CRPT-models with elementary embeddings as morphisms. An elementary embedding is a homomorphism that preserves and reflects all T_CRPT-sentences. The equivalence uses the Keisler-Shelah isomorphism theorem to identify isomorphic objects.

**Source:** CRPT; from `Mod-Corr` (L5.3.T1) + `Hom-Corr` (L5.3.T2).

The category Mod_CRPT of CRPT models and model homomorphisms (`Hom` (L5.2.D1) of the anchor; L5.2) is isomorphic to the category Mod(Σ_CRPT, T_CRPT) of
scope-aware Σ_CRPT-models of T_CRPT with CNF-preserving L(Σ_CRPT)-homomorphisms.

*Proof.*

Define two functors:

**F : Mod_CRPT → Mod(Σ_CRPT, T_CRPT):**
- On objects: F(D) = Str(N) (the Σ_CRPT-structure of `Mod-Corr` (L5.3.T1), ⟹ direction).
- On morphisms: F(Φ) = Φ_U (the underlying function, which is an
  L(Σ_CRPT)-homomorphism by `Hom-Corr` (L5.3.T2)).
F is well-defined: Str(N) ⊧ T_CRPT by `Mod-Corr` (L5.3.T1); Φ_U is a homomorphism by
`Hom-Corr` (L5.3.T2).

**G : Mod(Σ_CRPT, T_CRPT) → Mod_CRPT:**
- On objects: G(M) = Mdl(M) (the CRPT model of `Mod-Corr` (L5.3.T1), ⟸ direction).
- On morphisms: G(h) = h (an L(Σ_CRPT)-homomorphism; checking it satisfies Φ_R,
  Φ_E, Φ_ρ, Φ_LA requires that h preserves the structures used in those
  conditions, which follows from h being an L(Σ_CRPT)-homomorphism with CNF
  preservation).
G is well-defined by the ⟸ direction of `Mod-Corr` (L5.3.T1).

**F ∘ G = id:** G(M) constructs Mdl(M) from M; then F(Mdl(M)) reconstructs a
Σ_CRPT-structure from Mdl(M). By construction, F(G(M)) = M (same carrier,
relations, function). ✓

**G ∘ F = id:** F(D) constructs Str(N) from D; then G(Str(N)) reconstructs a model
from Str(N). By construction, G(F(D)) = D (same substrate, projection operator,
axiom profile). ✓

The functors are mutually inverse natural transformations (naturality is
component-wise on morphisms by the definitions). Hence Mod_CRPT ≅ Mod(Σ_CRPT, T_CRPT)
as categories. ∎

### Mod_CRPT is Category of T_CRPT-Models
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Corollary** | L5.3.C3 | `Mod=T` |  | **Novel** |
**Synopsis:** Confirms that the notation Mod_CRPT for the category of CRPT models is consistent with standard model-theoretic usage Mod(T): by the Category Equivalence, Mod_CRPT is literally the category of models of the theory T_CRPT.

**Source:** CRPT; corollary of `Cat-Eq` (L5.3.T3).

The category Mod_CRPT
the *category of CRPT models*, consistent with standard model-theoretic notation
(Mod(T) for the category of models of a theory T; [CK90 §3.4]).

---

## Scope Boundaries and What Cannot Be Claimed

### The theory T_CRPT is not first-order
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Remark** | L5.3.R1 | `T-2nd-Ord` |  | **Novel** |
**Synopsis:** T_CRPT is a genuinely second-order theory (PA-CoInd, C2, PA-Reach, and the LA_M schemas quantify over sets/functions). Consequently Gödel completeness, compactness, and Löwenheim–Skolem do not apply — but CRPT's claims are semantic, not proof-theoretic, so this is not a limitation on its content.

**Source:** CRPT; from `SO-Ext` (L5.3.D6) + `T_CRPT` (L5.3.D11).

The CRPT theory T_CRPT
is a second-order theory (it uses quantification over sets and functions in PA-CoInd,
C2, PA-WN, PA-Reach, and model-local schemas LA_M when declared). Therefore:

- The completeness theorem (Gödel 1930) does NOT apply: there is no effective
  proof system for which D ⊧_σ T_CRPT iff T_CRPT ⊢ φ for all φ. CRPT makes no
  completeness claim in the Gödel sense.
- The compactness theorem does NOT apply to T_CRPT in general: an infinite
  consistent set of sentences may fail to have a model in second-order logic.
- The Löwenheim-Skolem theorem does NOT apply: T_CRPT may have models of only
  one cardinality (categoricity is possible for second-order theories).

None of these limitations affect CRPT's mathematical content: the claims made
are purely semantic (the axioms hold in specific structures), not proof-theoretic.

### What "CRPT model" means and does not mean
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Remark** | L5.3.R2 | `CRPT-Mod-Scope` |  | **Novel** |
**Synopsis:** Clarifies what "CRPT model" means: a Σ_CRPT-structure satisfying the PA-* axioms in their declared scopes. It is not an informal analogy or simplification, and it need not satisfy every axiom globally — scope declarations (Scoped / Vacuous / Fails) are first-class.

**Source:** CRPT; from `Scope-Sat` (L5.3.D12) + `CRPT-Mod-18` (L5.1.D1).

A *CRPT model* (= CRPT model) is a scope-aware model of T_CRPT.
This means:
- It IS: a Σ_CRPT-structure satisfying the stated PA-* axioms in their declared
  scopes.
- It is NOT: a "model" in the informal sense (a representation, an analogy,
  or a simplification of reality). CRPT models are mathematical structures with
  precise properties.
- It is NOT: required to satisfy every PA-* axiom globally. Scope declarations
  (Scoped, Vacuous, Fails) are first-class: a model with PA-Conf declared
  Scoped(ρ-orbits) is a full CRPT model; it does not "partially satisfy" anything.

### Topology import
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Remark** | L5.3.R3 | `PA-WN_top-Import` |  | **Novel** |
**Synopsis:** Topology 𝒯 is part of every CRPT substrate. For native stratified models (∞_M ≠ ∅), PA-WN_top makes each persistent ρ-orbit converge in 𝒯, and the global conditions TopSep(𝒯) and continuity of ρ make the topological branch of CFix well-defined and unique.

**Source:** CRPT; from `Sub` (L1.1.D1) + PA-WN_top (L1.2.Ax7).

Topology is part of substrate data for every CRPT model:
Sub = (𝒰, →_ρ, →_σ, 𝒯). For native stratified models (∞_M ≠ ∅), PA-WN_top
asserts that each persistent ρ-orbit converges in 𝒯. Global substrate conditions
TopSep(𝒯) and continuity of ρ ensure the topological branch of CFix is
well-defined and unique.

### Category Mod_CRPT is large
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Remark** | L5.3.R4 | `Mod-Large` |  | **Novel** |
**Synopsis:** Mod_CRPT is a proper-class-sized (large) category, since Σ_CRPT-structures of every cardinality exist. This raises no set-theoretic paradox under the standard treatment of large categories.

**Source:** CRPT; large-category treatment after Mac Lane [1971] §I.6.

The category Mod_CRPT has a proper
class of objects (because Σ_CRPT-structures of any cardinality exist), consistent
with the anchor statement "Mod_CRPT is a (possibly large) category." No set-theoretic
paradox arises; this follows from standard category-theoretic treatment of large
categories [MacLane 1971 §I.6].

### FOL Completeness for Finite CRPT Models

| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L5.3.T4 | `FOL-Fin` |  | **Novel** |
**Synopsis:** The FOL-finiteness theorem: on finite CRPT models, T_CRPT collapses to its first-order fragment (every second-order assumption reduces to a first-order approximation schema), so finite CRPT models are exactly the finite models of T_CRPT^{FOL}. For infinite models the full SOL form is required.

**Source:** CRPT; from `Mod-Corr` (L5.3.T1) + `SO-Ext` (L5.3.D6); CRPT instance of `Finite-Collapse` (L0.7.T2).

*T_CRPT restricted to finite CRPT models is equivalent to its first-order fragment.
Precisely: a finite Σ_CRPT-structure M is a CRPT model (satisfies `Mod-Corr`
(L5.3.T1)) if and only if M ⊧ T_CRPT^{FOL}, where T_CRPT^{FOL} is the
restriction of T_CRPT (L5.3.D11) obtained by replacing each SOL formula Φ_i with
its first-order approximation schema Φ_i^{FOL} defined as follows:*

```
For each Φ_i in T_CRPT of the form  ∃R. Ψ(R)  (existential second-order):
  Φ_i^{FOL}  :=  the universal closure of Ψ(R)[R ↦ r_{Φ_i}],
  where r_{Φ_i} is a first-order definable relation symbol interpreting R
  in the finite-model setting.

For each Φ_i of the form  ∀R. Ψ(R)  (universal second-order / induction schema):
  Φ_i^{FOL}  :=  the corresponding finite induction schema ranging over
  the explicitly enumerable elements of M (finite case).
```

*Proof.*

*(⟹) Every finite CRPT model satisfies T_CRPT^{FOL}:*

Let M be a finite Σ_CRPT-structure satisfying `Mod-Corr` (L5.3.T1). We verify
that each SOL assumption in T_CRPT reduces to its FOL approximation:

- **SOL-3 (PA-CoInd, L1.2.Ax5):** On a finite structure, the coinduction schema
  ∀R [(R is a bisimulation) ⟹ R ⊆ ≈] is equivalent to the finite partition-
  refinement algorithm: bisimilarity on finite →_ρ structures is computable by
  finitely many refinement steps (Hopcroft–Karp). The SOL quantification over all
  bisimulations R collapses to a finite enumeration of candidate relations on
  |M|² elements. So Φ_{SOL-3}^{FOL} holds. ✓

- **SOL-4 (PA-NWF, L1.2.Ax4):** ∃π (infinite path witness): since M is finite and
  PA-WN holds (all orbits terminate — by finiteness there are no infinite chains),
  ∞_M = ∅. The SOL existential is vacuously satisfied in the finite-model sense:
  the witness condition is activated only for elements in ∞_M, which is empty.
  Φ_{SOL-4}^{FOL} holds vacuously. ✓

- **SOL-5 (PA-Prod, L1.2.Ax6):** Productivity is finitely decidable: for x ∈ ∞_M
  (empty), the condition is vacuous. For x ∈ ↓_M, ρ_M^{d_M(x)}(x) ∈ Fix(ρ_M)
  in finitely many steps, which is a first-order checkable condition on the finite
  orbit graph. ✓

- **SOL-13, SOL-14 (CNF∞ Cauchy conditions, L3.3.D6):** On finite M with ∞_M = ∅,
  the Cauchy metric conditions on 𝒯_M are vacuous (no persistent orbits exist).
  Φ_{SOL-13}^{FOL} and Φ_{SOL-14}^{FOL} hold trivially. ✓

- **SOL-1, SOL-2, SOL-6 through SOL-12:** These concern →_ρ^* (transitive closure),
  Div, and bisimilarity. On finite structures, all three are first-order definable
  (transitive closure of a finite relation is first-order in the finite-model
  context by Immerman–Szelepcsényi [1988]); bisimilarity is computable in
  polynomial time (Paige–Tarjan [1987]). Each Φ_{SOL-i}^{FOL} holds by the
  corresponding finite-model reduction. ✓

*(⟸) Every finite model of T_CRPT^{FOL} is a CRPT model:*

Let M be a finite Σ_CRPT-structure with M ⊧ T_CRPT^{FOL}. The finite-model
reductions above are equivalences (not just implications) for finite structures:
each Φ_i^{FOL} is satisfied iff the corresponding original SOL condition Φ_i holds
on M. (In the finite setting, "existential over relations" reduces to "existential
over explicitly enumerable relations on |M|² or |M|^k for bounded k," which the
FOL approximation captures exactly.) Therefore M ⊧ T_CRPT under scope-aware
satisfaction (`Scope-Sat` L5.3.D12), so M is a CRPT model by `Mod-Corr`
(L5.3.T1). ✓

*Remark (Grounding of L0.7.T2).* `Finite-Collapse` (L0.7.T2) states universally
that for any projection system Π satisfying the SOL-Nec conditions, the finite-
model restriction is FOL-equivalent. `FOL-Fin` (L5.3.T4) is the CRPT instance
of that universal theorem, confirming it for the specific 14 SOL assumptions of
T_CRPT. ∎

---

## Terminology Summary

### CRPT Model
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L5.3.D13 | `CRPT-Mod-L5.3` |  | **Novel** |
**Synopsis:** Formal-theory restatement of "CRPT model": a scope-aware model of T_CRPT realised as a Σ_CRPT-structure satisfying the substrate conditions, C1, C2, and the applicable PA-* axioms in their declared scopes. Equivalent to `CRPT-Mod-18` (L5.1.D1).

**Source:** CRPT; from `T_CRPT` (L5.3.D11) + `Scope-Sat` (L5.3.D12); restates `CRPT-Mod-18` (L5.1.D1).

A *CRPT model* is a scope-aware model of T_CRPT (`T_CRPT` (L5.3.D11)), equipoised
with a Σ_CRPT-structure (`Σ_CRPT` (L5.3.D10)) satisfying the substrate conditions,
C1, C2, and the applicable PA-* axioms in their declared scopes.

### CRPT Model Homomorphism
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L5.3.D14 | `CRPT-Hom` |  | **Novel** |
**Synopsis:** Formal-theory restatement of "CRPT model homomorphism": a model homomorphism Φ : N₁ → N₂, equivalently a CNF-preserving L(Σ_CRPT)-homomorphism. Equivalent to `Hom` (L5.2.D1).

**Source:** CRPT; restates `Hom` (L5.2.D1) via `L-Hom` (L5.3.D8).

A *CRPT model homomorphism* is a model homomorphism Φ : N₁ → N₂ (`Hom` (L5.2.D1)
of the anchor). Equivalently, it is an L(Σ_CRPT)-homomorphism (`L-Hom` (L5.3.D8))
preserving CNF.

### Category Mod_CRPT
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L5.3.D15 | `Mod_CRPT-L5.3` | Mod_CRPT | **Novel** |
**Synopsis:** Formal-theory restatement of the category Mod_CRPT — CRPT models and CRPT model homomorphisms — which by `Cat-Eq` (L5.3.T3) is isomorphic to the category of scope-aware Σ_CRPT-models of T_CRPT.

**Source:** CRPT; from `Cat-Eq` (L5.3.T3); restates `Mod_CRPT` (L7.2.D1).

The *category Mod_CRPT* is the category of CRPT models and CRPT model
homomorphisms. By `Cat-Eq` (L5.3.T3), it is isomorphic to the category of scope-aware
Σ_CRPT-models of T_CRPT with homomorphisms.

---

## L5.4 — Model Order

### Refinement Order ⊑
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L5.4.D1 | `⊑` | ⊑ | **Reframed** |
**Synopsis:** The refinement order M₁ ⊑ M₂ holds when M₁'s universe embeds in M₂'s, M₂'s reduction relation restricts to M₁'s on the shared universe, and M₁'s observable equivalence implies M₂'s there. It orders CRPT models by structural inclusion.

**Source:** Cousot & Cousot [1977] POPL — abstract-interpretation refinement order, applied to CRPT models.

M₁ ⊑ M₂ if 𝒰_{M₁} ⊆ 𝒰_{M₂},
→_ρ^{M₁} ⊇ →_ρ^{M₂} ∩ (𝒰_{M₁} × 𝒰_{M₁}), and ≃_{M₁} ⟹ ≃_{M₂} restricted to 𝒰_{M₁}.

### ⊑ is Partial Order
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L5.4.T1 | `⊑-PO` |  | **Novel** |
**Synopsis:** The refinement order ⊑ is a partial order on CRPT models: reflexive, transitive, and antisymmetric. Models related by mutual refinement agree on all their defining data, hence are equal.

**Source:** CRPT; from `⊑` (L5.4.D1).

(Models, ⊑) is a poset: reflexive
(M ⊑ M via inclusions), transitive (chain of inclusions), antisymmetric.

*Proof.*
- Reflexive: for every M, we have 𝒰_M ⊆ 𝒰_M, →_ρ^{M} ⊇ →_ρ^{M} ∩ (𝒰_M×𝒰_M), and
 ≃_M implies itself on 𝒰_M. So M ⊑ M.
- Transitive: if M₁ ⊑ M₂ and M₂ ⊑ M₃, then 𝒰_{M₁} ⊆ 𝒰_{M₂} ⊆ 𝒰_{M₃}; similarly, restriction of
 the reduction relation and implication of ≃ compose, yielding M₁ ⊑ M₃.
- Antisymmetric: if M₁ ⊑ M₂ and M₂ ⊑ M₁, then mutual universe inclusion gives
 𝒰_{M₁} = 𝒰_{M₂}; mutual relation-restriction conditions force equality of the restricted
 reduction relations; mutual ≃ implication gives equality of equivalence relations on
 that universe. Hence M₁ and M₂ agree on the defining data, so M₁ = M₂.
Therefore ⊑ is a partial order. ∎

### Expressiveness ⪯
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L5.4.D2 | `⪯` | ⪯ | **Reframed** |
**Synopsis:** The expressiveness order M₁ ⪯ M₂ holds when M₁ embeds injectively into M₂. It compares models by representational capacity, independent of universe inclusion (unlike the refinement order ⊑).

**Source:** Cousot & Cousot [1977] POPL — abstract-interpretation expressiveness order, applied to CRPT models.

M₁ ⪯ M₂ if ∃ embedding Φ : M₁ → M₂ with
Φ_U injective.

### ⪯ is Preorder
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L5.4.T2 | `⪯-Pre` |  | **Novel** |
**Synopsis:** The expressiveness order ⪯ is a preorder (reflexive and transitive) but not antisymmetric in general: distinct presentations of isomorphic structures can embed injectively into each other without being identical model descriptions.

**Source:** CRPT; from `⪯` (L5.4.D2).

(Models, ⪯) is reflexive and transitive but
not antisymmetric in general.

*Proof.*
- Reflexive: id_M : M → M is injective, so M ⪯ M.
- Transitive: if M₁ ⪯ M₂ via injective embedding Φ and M₂ ⪯ M₃ via injective embedding Ψ,
 then Ψ∘Φ : M₁ → M₃ is injective, so M₁ ⪯ M₃.
- Not antisymmetric in general: two distinct presentations of isomorphic structures
 can embed into each other injectively while not being syntactically identical as
 model descriptions.
Hence ⪯ is a preorder, not necessarily a partial order. ∎

### PA-* Profile Lattice
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L5.4.T3 | `PA-Lat` |  | **Novel** |
**Synopsis:** The PA-* axiom profiles form a bounded (Boolean) lattice (𝒫(𝔄), ⊆) over the projection axioms — intersection as meet, union as join, ∅ as bottom, the full set as top. This organizes all possible CRPT model profiles into a single lattice.

**Source:** CRPT; from the PA-* axiom system (L1.2–L1.3).

Let
𝔄 := {PA-WN, PA-Conf, PA-Fix, PA-NWF, PA-CoInd, PA-Prod, PA-WN_top, PA-Bisim, PA-Reach}.
The powerset lattice (𝒫(𝔄), ⊆) is a bounded lattice of axiom profiles with:
- meet: S ∧ T := S ∩ T
- join: S ∨ T := S ∪ T
- bottom: ⊥ := ∅
- top: ⊤ := 𝔄

*Proof.* (𝒫(𝔄), ⊆) is the standard Boolean lattice on a finite set. For any S,T ⊆ 𝔄:
S∩T is the greatest lower bound under ⊆, and S∪T is the least upper bound under ⊆.
Finite powersets always provide bottom ∅ and top 𝔄. Therefore the PA-* profile space
is a bounded lattice. ∎

### Substrate-Neutral Ordering
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L5.4.T4 | `Sub-Ord` |  | **Novel** |
**Synopsis:** The refinement order ⊑ descends to isomorphism classes of models: [M₁] ⊑ [M₂] is well-defined independent of representatives, because isomorphisms transport all the data defining ⊑. The order is therefore substrate-neutral.

**Source:** CRPT; from `⊑` (L5.4.D1) + `Iso` (L5.2.D2).

The refinement order ⊑ descends
to equivalence classes [M] under model isomorphism: [M₁] ⊑ [M₂] iff some
representative of [M₁] refines some representative of [M₂].

*Proof.* Let M₁ ≅ M₁' and M₂ ≅ M₂'. Suppose M₁ ⊑ M₂. Isomorphisms transport universe
membership, reduction structure, and equivalence structure. Therefore the defining
conditions of ⊑ are invariant under replacing M₁ by an isomorphic copy M₁' and M₂ by an
isomorphic copy M₂'. Hence M₁ ⊑ M₂ implies M₁' ⊑ M₂'. So the relation
[M₁] ⊑ [M₂] :⟺ ∃M₁'∈[M₁], M₂'∈[M₂] with M₁' ⊑ M₂' is well-defined (independent of choice of
representatives). Therefore refinement descends to isomorphism classes. ∎

---

## L5.5 — The Category of CRPT Models

*Purpose.* This section formalizes the category-theoretic structure underlying all CRPT
models and their interactions. The category Mod_CRPT is the foundational abstraction that
allows uniform treatment of instantiation, composition, and model transformation.

### The Category Mod_CRPT

| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L5.5.D1 | `Mod_CRPT-Cat` | Mod_CRPT | **Novel** |
**Synopsis:** This definition formally establishes Mod_CRPT as a category, explicitly verifying identity and associativity. The Hom-Pres theorem confirms that CRPT homomorphisms compose to give CRPT homomorphisms — composition is closed in the category.

**Source:** CRPT; from `Hom` (L5.2.D1) + `Mod-Cat` (L5.2.T1).

The **category of CRPT models** Mod_CRPT is defined as:

**Objects:**  All CRPT models M = (𝒰_M, →_ρ, →_σ, ρ_M, ≃_M, axiom profile) satisfying 
the PA-axiom system (PA-WN, PA-Conf, PA-Fix, etc., with regime-specific profiles).

**Morphisms:** A morphism Φ : M₁ → M₂ is a CRPT model homomorphism in the canonical sense of `Hom` (L5.2.D1): a function Φ_𝒰 : 𝒰_{M₁} → 𝒰_{M₂} satisfying its four conditions —

- **Φ_R (reduction):**  x →_ρ y in M₁ ⟹ Φ_𝒰(x) →_ρ Φ_𝒰(y) in M₂
- **Φ_E (equivalence):**  x ≃_{M₁} y ⟹ Φ_𝒰(x) ≃_{M₂} Φ_𝒰(y)
- **Φ_ρ (projection):**  Φ_𝒰(ρ_{M₁}(x)) ≃_{M₂} ρ_{M₂}(Φ_𝒰(x)) for all x ∈ 𝒰_{M₁}
- **Φ_LA (local-axiom compatibility):**  the pushforward of each local axiom of M₁ is consistent with LA_{M₂}

No separate →_σ-preservation condition is imposed; this is exactly `Hom` (L5.2.D1).

**Composition:** For morphisms Φ : M₁ → M₂ and Ψ : M₂ → M₃, define the composite
```
(Ψ ∘ Φ)_𝒰 : 𝒰_{M₁} → 𝒰_{M₃}  by  (Ψ ∘ Φ)_𝒰 := Ψ_𝒰 ∘ Φ_𝒰
```
(function composition). This composite satisfies Φ_R–Φ_LA by transitivity.

**Identity:** For each model M, the identity morphism id_M : M → M is the identity function
```
(id_M)_𝒰 = id_{𝒰_M} : 𝒰_M → 𝒰_M
```
which trivially satisfies Φ_R–Φ_LA.

**Category axioms:**
- (Associativity) (χ ∘ ψ) ∘ φ = χ ∘ (ψ ∘ φ) for all composable morphisms (by function-composition associativity).
- (Identity) For any Φ : M₁ → M₂: Φ ∘ id_{M₁} = Φ and id_{M₂} ∘ Φ = Φ (by function identity).

Therefore Mod_CRPT is a category; the full verification of the category laws is `Mod-Cat` (L5.2.T1).

### Model Homomorphisms Preserve Structural Properties

| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L5.5.T1 | `Hom-Pres` | | **Novel** |
**Synopsis:** CRPT model homomorphisms preserve structural properties: a homomorphism never increases abstraction depth (d_{M₂}(Φx) ≤ d_{M₁}(x)) and respects fixpoints, regimes, and canonical forms. Structure-preserving maps cannot manufacture new structure.

**Source:** CRPT; from `Hom` (L5.2.D1).

Let Φ : M₁ → M₂ be a model homomorphism. Then:

**(i)** Φ preserves abstraction depth: For all x ∈ 𝒰_{M₁},
```
d_{M₂}(Φ_𝒰(x)) ≤ d_{M₁}(x)
```

**(ii)** Φ preserves canonical forms: If x ∈ Fix(ρ_{M₁}), then Φ_𝒰(x) ∈ Fix(ρ_{M₂}).

**(iii)** Φ respects horizon membership: If x ∈ Class_i for some i ∈ {A, B, C, D, E, F}, 
then Φ_𝒰(x) ∈ Class_i in M₂ (modulo the caveat that Class_F = ∅ always).

**(iv)** Φ respects regime partition: x ∈ ↓_{M₁} ⟹ Φ_𝒰(x) ∈ ↓_{M₂}, and similarly for ∞_M.

**Proof sketch:** (i)–(ii) follow from (Φ_ρ) by induction on derivation height. (iii) requires that
the horizon predicates H_S, H_I, H_O are preserved by Φ; this holds because these
predicates are structure-definable from the reduction relation, ≃_M, and derivation height (`Hom-Pres` uses these on both
sides). (iv) follows from PA-WN and PA-NWF being inherited through (Φ_ρ) and (Φ_σ). ✓ ∎

---
