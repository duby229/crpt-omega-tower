# CRPT — Abstract Anchor: Omega Tower Specification Index

This is the canonical multi-file specification for the CRPT ω-indexed tower. Each level is presented in its own file for clarity and modularity. All files in this index together constitute the sole source of truth for the CRPT abstract anchor.

## Structure

- [# L0 — Universal Projection Framework](CRPT_OMEGA_TOWER_L0.md)
  *Substrate-independent statement of all major CRPT theorems for an arbitrary projection system Π. CRPT is instantiated as one example. All L0 Instance theorems carry corrected cross-references into L1–L8.*

- [# L1 — CRPT Substrate, Axioms, Regimes, and Modes](CRPT_OMEGA_TOWER_L1.md)
  *The substrate definition (L1.1.D1), the nine PA-\* axioms (L1.2–L1.4), and the six axiom profiles (Pure-WF through NWF-Full). Includes WF-Canon (L1.7.T1) and Nat-CC (L1.4.T2).*

- [# L2 — Projection, Regime, Depth, Canonical Form, and Fibers](CRPT_OMEGA_TOWER_L2.md)
  *The projection operator ρ_M (L2.1.D1), the two-regime partition ↓_M / ∞_M (L2.2.D4–D2), derivation height d_M (L2.3.D2), the canonical form map CFix(ρ_M) (L2.4.D1), and NFC fibers (L2.5.D1). Includes Inf-Dual (L2.2.T7) and Reg-Exh (L2.2.T8).*

- [# L3 — Horizon, Classification, and Persistent Canonical Invariants](CRPT_OMEGA_TOWER_L3.md)
  *Horizon predicates H_S, H_I, H_O (L3.1.D1–D4), orbit signature sig_M (L3.1.D5), H_I-WD kernel theorem (L3.1.T2), the six-class partition (L3.2.D2, L3.2.T1), the twelve-class native extension (L3.4), and CNF∞_M (L3.3.D6) with SC-1 through SC-4 (L3.3.D2–D5).*

- [# L4 — Observer, Gateway, Valuation, Duality, Self-Projection, and Perturbation](CRPT_OMEGA_TOWER_L4.md)
  *The Observable Triple 𝒪 (L4.1), Gateway / PA-Reach (L4.2), Projection Valuation (L4.3), the five Duality theorems (L4.4), Inversion Horizon / CPD / CIH (L4.5), Self-Projection (L4.6), and Coherent Perturbation (L4.7).*

- [# L5 — Model Algebra, Model Theory, Homomorphisms, and Model Order](CRPT_OMEGA_TOWER_L5.md)
  *Model Algebra (L4.8/L5.1), Homomorphisms and Mod_CRPT (L5.2), the CRPT formal theory T_CRPT / Σ_CRPT (L5.2–L5.2) including Mod-Corr (L5.3.T1), Cat-Eq (L5.3.T3), Scope Boundaries (L5.2), and FOL-Fin (L5.3.T4). Model Order (L5.3).*

- [# L6 — Persistent Orbit Invariants, NWF Horizons, Regime-Type Determinacy, and Degeneracy](CRPT_OMEGA_TOWER_L6.md)
  *Asymptotic orbit invariants (L6.1), orbit-type three-tier framework (L6.2), full AOI proofs including SC-Imp (L6.3), NWF horizon partition A*–F* (L6.4), regime-type determinacy (L6.5), and degeneracy (L6.6).*

- [# L7 — Categorical Collapse, Functoriality, and Model-Theory Fibration](CRPT_OMEGA_TOWER_L7.md)
  *Abstraction as epimorphism / Galois insertion (L7.1), CRPT's own structure shown categorical by self-application (L7.2), and the CRPT functor (L7.3).*

- [# L8 — Tower, Horizontal-Vertical Duality, Fractality, and Strict Omega-Categories](CRPT_OMEGA_TOWER_L8.md)
  *The Tower construction (L8.1), HV-Duality (L8.6), Strict ω-Category structure (L8.7), CRPT-Fractal definition and Twr-Fractal theorem (L8.5), and Native Framework Validation (L8.8).*

- [# Lω — Meta-CRPT: The Theory Applied to Itself](CRPT_OMEGA_TOWER_Lω.md)
  *Self-substrate definition 𝒰_CRPT (Lω.1), Self-Horizon classification (Lω.2), rank function m_CRPT (Lω.3), Tower-of-Towers (Lω.4), Self-FP fixed-point uniqueness theorem (Lω.5), Anchor-Fractal closure (Lω.6), and the Notation Index (LR.32).*

## Cross-File Reference Convention

All constructs are identified by their §-label (e.g., `L3.1.T2`) which is unique
across the entire anchor. L-level addresses (e.g., `L3.1.2a`) indicate the file and
section. Cross-file references use the form: `TheoremName (§x.y.Tz, Lfile.section)`.

## Dependency Order

```
L0          ← standalone (no CRPT-specific dependencies)
L1          ← L0
L2          ← L0, L1
L3          ← L0, L1, L2
L4          ← L0, L1, L2, L3
L5          ← L0, L1, L2, L3, L4
L6          ← L0, L1, L2, L3, L4, L5
L7          ← L0–L6
L8          ← L0–L7
Lω          ← L0–L8 (all prior levels)
```

See each file for the full details of that level.

- [# L8 — Tower Construction, Horizontal-Vertical Duality, and Fractality](CRPT_OMEGA_TOWER_L8.md)
  *The Free Monoidal Algebra FMA(Q_M) (L8.1), the Lift operator (L8.2), Fixpoints-to-Basics (L8.2), horizon inheritance (L8.2), PA-* preservation (L8.3), the Tower sequence (L8.4), faithful embedding (L8.4), NWF-extended Lift* (L8.5), Horizontal-Vertical Duality (L8.6), discriminability (L8.6), tower ω-category (L8.7), axiom consistency (L8.8), tail self-similarity and CRPT-Fractal theorem (L8.5). **CRPT additions:** L8.6 supplementary lemmas (`Prop-σ-Lift`, `Lift-Red-Struc`, `Lift-Pure-WF`, `Tower-Inf`, `Q_M-Card`).*

- [# Lω — Meta-CRPT: CRPT Applied to Itself](CRPT_OMEGA_TOWER_Lω.md)
  *Self-substrate 𝒰_CRPT (Lω.1), self-horizon classification (Lω.2), rank function m_CRPT (Lω.3), tower of towers (Lω.4), self-consistency fixed point (Lω.5), anchor fractality (Lω.6). **CRPT additions:** Lω.7 supplementary lemmas (`CRPT-Acyclic`, `Self-CRPT-Finite`, `CRPT-WF`, `Lω-FixedPt-Unique`).*

---

## CRPT Support Files

- [# Global Map](CRPT_OMEGA_TOWER_GLOBAL_MAP.md) — Tower dependency DAG, level summaries, cross-level notation glossary, theorem cross-reference
- [# Preface](CRPT_OMEGA_TOWER_PREFACE.md) — Conceptual introduction to CRPT, the tower, and the HOA
- [# Reading Guide](CRPT_OMEGA_TOWER_READING_GUIDE.md) — Four reading paths; prerequisite map; proof depth explanation
- [# Common Pitfalls](CRPT_OMEGA_TOWER_COMMON_PITFALLS.md) — 12 documented misconceptions with corrections
- [# Theorem Index](CRPT_OMEGA_TOWER_THEOREM_INDEX.md) — Complete index of all definitions, theorems, lemmas, and corollaries by level and concept
- [# Definitions Index](CRPT_OMEGA_TOWER_DEFINITIONS_INDEX.md) — Alphabetical symbol reference, notation rules, dependency map, axiom profiles
- [# Release Notes](CRPT_OMEGA_TOWER_RELEASE_NOTES.md) — Document inventory, known limitations, and future work
