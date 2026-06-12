# CRPT ω-Tower — Global Architecture & Navigation

**Status:** CRPT ω-Tower  
**Date:** 

---

## Overview: What Is This Document?

This document provides a **unified map** of the entire ω-tower specification (L0–Lω). It shows:
- **What each level does** (purpose, scope, dependencies)
- **How levels depend on each other** (formal dependency graph)
- **What symbols recur across levels** (cross-level glossary)
- **Where key theorems appear** (theorem cross-reference by topic)

This is **not** a substitute for reading the tower itself—it's a **navigation aid** for finding concepts and understanding the architecture.

---

## L1.1. The Ten Levels: One-Line Descriptions

| Level | Purpose | Dependence |
|-------|---------|-----------|
| **L0** | Universal projection framework (π-systems, fibers, observability) | None |
| **L1–L2** | CRPT substrate instantiation + regime partition (convergent/persistent) | L0 |
| **L3–L4** | Horizon predicates (H_S, H_I, H_O) + observer architecture (six-class partition) | L1–L2 |
| **L5–L6** | Model algebra and homomorphism theory | L1–L4 |
| **L7** | Categorical collapse operator and functoriality | L5–L6 |
| **L8** | Tower construction (Lift operator) and horizontal-vertical duality | L1–L7 |
| **Lω** | Meta-application: CRPT applied to itself as a model | L0–L8 |

---

## L1.2–L1.5. Dependency Graph (DAG Structure)

```
                    L0 (Universal Framework)
                    |
        ____________|_____________
        |                         |
        L1                       [Instance]
        |
    ____|____
    |       |
    L2      L3-L4
    |       |
    |_______|
        |
    ____|____
    |       |
    L5     [Horizons]
    |
    L6
    |
    L7
    |
    L8 (Tower)
    |
    Lω (Meta-CRPT)
```

**Legend:**
- Solid line: logical dependency (must define before use)
- Vertical: sequential (need L_n to understand L_{n+1})
- [Instance]: CRPT is an instance of L0 framework; both are presented at L1

---

## L2.1. Cross-Level Glossary of Recurring Symbols

### Universal & Model-Independent Symbols

| Symbol | Meaning | First Defined | Levels Used |
|--------|---------|---------------|-------------|
| 𝒰 | Universe of elements | L0 | L0–Lω |
| π | Projection map (universal) | L0 | L0–L8 |
| CNF_π | Canonical form under π | L0 | L0–L8 |
| L_π(x) | Fiber of x under π | L0 | L0–L3 |
| ≃_π | Observable equivalence (universal) | L0 | L0–L8 |
| Fix(π) | Fixed-point set | L0 | L0–Lω |

### CRPT Model-Specific Symbols

| Symbol | Meaning | First Defined | Levels Used |
|--------|---------|---------------|-------------|
| →_ρ | Reduction relation | L1 | L1–Lω |
| →_σ | Structural relation | L1 | L1–Lω |
| ρ_M | Projection operator of model M | L1 | L1–Lω |
| CNF_M | Canonical normal form in M | L2 | L2–Lω |
| CFix(ρ_M) | Canonical fixpoint | L2 | L2–Lω |
| NFC_M(f) | Normal-form fiber | L2 | L2–Lω |
| ≃_M | Observable equivalence in M | L2 | L2–Lω |
| ↓_M | Convergent regime | L2 | L2–Lω |
| ∞_M | Persistent regime | L2 | L2–Lω |
| d_M(x) | Derivation height | L2 | L2–Lω |

### Horizon Predicates & Observer

| Symbol | Meaning | First Defined | Levels Used |
|--------|---------|---------------|-------------|
| H_S(x) | Structural horizon | L3 | L3–Lω |
| H_I(x) | Invariant horizon | L3 | L3–Lω |
| H_O(x) | Depth horizon (boundary) | L3 | L3–L8 |
| sig_M(x) | Signature (H_I classifier) | L3 | L3–Lω |
| O_M | Observer triple | L4 | L4–Lω |
| Gate_M | Gateway (O_M component) | L4 | L4–L8 |

### Model Algebra & Categories

| Symbol | Meaning | First Defined | Levels Used |
|--------|---------|---------------|-------------|
| Mod_CRPT | Category of CRPT models | L5 | L5–Lω |
| Φ | Model homomorphism | L5 | L5–Lω |
| Collapse(M) | Quotient by observable equivalence | L7 | L7–Lω |
| κ_M | Collapse map to fixpoints | L7 | L7–Lω |

### Tower & Lift

| Symbol | Meaning | First Defined | Levels Used |
|--------|---------|---------------|-------------|
| Lift(M) | Free lift to FMA level | L8 | L8–Lω |
| FMA(Q_M) | Free monoidal algebra on Q_M | L8 | L8–Lω |
| Q_M | Abstraction quotient (queries) | L8 | L8–Lω |
| M_n | Tower level n = Lift^n(M_0) | L8 | L8–Lω |
| ρ_Lift | Projection operator on Lift(M) | L8 | L8–Lω |

### Meta-Level (Lω)

| Symbol | Meaning | First Defined | Levels Used |
|--------|---------|---------------|-------------|
| 𝒰_CRPT | Self-substrate (all constructs) | Lω | Lω |
| →_ρ_CRPT | Logical dependency in CRPT | Lω | Lω |
| ρ_CRPT | Immediate dependency operator | Lω | Lω |
| Self_CRPT | CRPT as its own model | Lω | Lω |

---

## L2.2. Theorem Index by Topic

### Projection & Observability (L0)

- **L0.1.T1 [Fiber-Compl]:** Fiber completeness—fiber is complete cert of observability boundary
- **L0.1.T2 [Lift-Mono]:** Lift monotonicity—finer projections yield smaller lifts
- **L0.1.T3 [Univ-Ind]:** H_S, H_I, H_O as universal indicators (L0 framework applies everywhere)

### CRPT Substrate & Regimes (L1–L2)

- **L1.1.T1 [Sub-Axiom]:** Substrate axioms (PA-WN, PA-Conf, PA-Fix)
- **L2.2.T1 [Regime-Part]:** ↓_M ∪ ∞_M = 𝒰_M (partition into regimes)
- **L2.2.T2 [Regime-Prop]:** Regime properties (disjointness, exhaustiveness)
- **L2.3.T1 [Depth-Dec]:** Derivation height decreases under ρ_M iteration

### Horizons & Observability (L3)

- **L3.1.T1 [H_S-Ramif]:** H_S defines ramification locus of ρ_M
- **L3.1.T2 [H_I-Kernel-Local]:** H_I is kernel-local (respects observable equivalence)
- **L3.1.T3 [H_O-Boundary]:** H_O marks boundary layer (depth = 1)

### Six-Class Partition (L4)

- **L4.1.T1 [Six-Class]:** Six-class partition {A,B,C,D,E,F} (Boolean lattice structure)
- **L4.2.T1 [No-F]:** Class F is empty in deterministic models
- **L4.3.T1 [Observer-Preserv]:** Observer triple preserves partition under homomorphisms

### Model Algebra (L5)

- **L5.2.T1 [Mod-Cat]:** Mod_CRPT forms a category (objects=models, morphisms=homomorphisms)
- **L5.2.T1 [Iso-Hor]:** Regime-restricted isomorphisms preserve horizons
- **L5.4.T1 [Hom-Compose]:** Homomorphism composition is associative

### Collapse & Functoriality (L7)

- **L7.1.T4 [Collapse-Model]:** Collapse(M) remains a CRPT model
- **L7.2.T4 [Lift⊣Coll]:** Collapse has left adjoint (Lift)
- **L7.3.T1 [F-Func]:** F is a functor Mod_CRPT → ωCat (the tower functor)

### Tower & Lift (L8)

- **L8.1.T1 [Tower-Seq]:** Tower T(M_0) = {M_n | M_{n+1} = Lift(M_n)}
- **L8.1.T2 [Query-Stabil]:** Q_{M_n} = Q_{M_0} (query signature invariant)
- **L8.1.T3 [Tower-Inf]:** Tower is infinite in height
- **L8.2.T1 [Lift-Mech]:** Lift operator mechanics and properties
- **L8.3.T1 [HV-Duality]:** Horizontal-vertical duality (width vs. depth in tower)

### Meta-Application (Lω)

- **Lω.1.T1 [Self-Model]:** Self_CRPT is a CRPT model
- **Lω.2.T1 [CRPT-Acyclic]:** →_ρ_CRPT is acyclic (no circular dependencies)
- **Lω.3.T1 [CRPT-WF]:** Self_CRPT is pure well-founded (∞_CRPT = ∅)
- **Lω.4.T1 [Lω-FixedPt]:** Lω is fixed point of Lift operator
- **Lω.5.T1 [Lω-Unique]:** Lω is unique fixed point (self-application is unambiguous)

---

## L2.3. Definitions Index by Topic

### Universal Framework (L0)

| Definition | Notation | First Use |
|-----------|----------|-----------|
| Projection system | Π | L0.1.D1 |
| Fiber | L_π(x) | L0.1.D2 |
| Observable equivalence | ≃_π | L0.1.D2 |
| Observability | Obs_π(I,x) | L0.1.D3 |
| Convergent regime | Conv(π) | L0.2.D1 |
| Persistent regime | Pers(π) | L0.2.D2 |

### CRPT Instantiation (L1–L2)

| Definition | Notation | First Use |
|-----------|----------|-----------|
| CRPT model | M | L1.1.D1 |
| Reduction relation | →_ρ | L1.1.D1 |
| Structural relation | →_σ | L1.1.D1 |
| Projection operator | ρ_M | L2.1.D1 |
| Regime partition | ↓_M, ∞_M | L2.2.D1, L2.2.D2 |
| Derivation height | d_M(x) | L2.3.D1 |
| Canonical normal form | CNF_M(x) | L2.1.D1 |
| Canonical fixpoint | CFix(ρ_M)(x) | L2.1.D1 |
| Normal-form fiber | NFC_M(f) | L2.2.D2 |

### Horizons & Observer (L3–L4)

| Definition | Notation | First Use |
|-----------|----------|-----------|
| Structural horizon | H_S(x) | L3.1.D1 |
| Invariant horizon | H_I(x) | L3.1.D2 |
| Depth horizon | H_O(x) | L3.1.D3 |
| Signature | sig_M(x) | L3.1.D5 |
| Observer triple | O_M | L4.1.D1 |
| Gateway | Gate_M | L4.2.D1 |

### Collapse & Functoriality (L5–L7)

| Definition | Notation | First Use |
|-----------|----------|-----------|
| Model category | Mod_CRPT | L5.1.D1 |
| Model homomorphism | Φ: M₁→M₂ | L5.2.D1 |
| Model isomorphism | M₁ ≅ M₂ | L5.4.D1 |
| Collapse operator | Collapse(M) | L7.1.D4 |
| Collapse quotient map | κ_M | L7.1.D4 |

### Tower & Lift (L8)

| Definition | Notation | First Use |
|-----------|----------|-----------|
| Free monoidal algebra | FMA(A) | L8.1.D1 |
| Abstraction quotient | Q_M | L8.1.D2 |
| Lift operator | Lift(M) | L8.2.D1 |
| Tower sequence | M_n, T(M_0) | L8.1.D3 |
| Tower level | M_n = Lift^n(M_0) | L8.1.D3 |

### Meta-Application (Lω)

| Definition | Notation | First Use |
|-----------|----------|-----------|
| Self-substrate | 𝒰_CRPT | Lω.1.D1 |
| Logical dependency | →_ρ_CRPT | Lω.1.D1 |
| Dependency operator | ρ_CRPT | Lω.1.D2 |
| CRPT as model | Self_CRPT | Lω.1.D3 |

---

## L2.4. How to Navigate This Tower

**Starting Points:**

- **I want to understand what CRPT is:** Read PREFACE (conceptual), then L0–L2 (formal foundation)
- **I need to find a specific theorem:** See Theorem Index (L2.2 above) by topic
- **I need to find a definition:** See Definitions Index (L2.3 above)
- **I am lost on dependencies:** See Dependency Graph (L1.2–L1.5 above)
- **I need to know what symbols mean:** See Glossary (L2.1 above)

**Reading Paths:**

- **Path A (Pure Mathematician):** L0 → L1–L2 → L3–L4 → L5–L7 → L8 → Lω (complete formal tower)
- **Path B (Type Theorist):** L0, L5, L7, L8, Lω (category-theoretic view)
- **Path C (Computer Scientist):** L0, L1–L4, L6–L8 (fixpoint/orbit/algorithm view)
- **Path D (Logician):** L0–L2, Lω (foundation + self-application)

---

## L2.5. Citation Guide for Academic Use

**For the ω-tower specification, cite:**

```bibtex
@techreport{CRPT2026,
  title={CRPT $\omega$-Tower Specification (CRPT ω-Tower)},
  author={[Author]},
  type={Formal Theory Documentation},
  institution={CRPT Project},
  year={2026},
  month={May},
  note={Levels L0--L$\omega$ with formal proofs}
}
```

**For specific levels, cite the level and theorem:**

```
Example: "By Theorem L4.2.T1 [No-F] (CRPT2026), Class F is empty..."
```

**For imported results, cite the original:**

```
Example: "By Park [1981] Theorem 2.3 (bisimulation determinism), 
as applied in Theorem L2.1.T2..."
```

---

**End of Global Map**
