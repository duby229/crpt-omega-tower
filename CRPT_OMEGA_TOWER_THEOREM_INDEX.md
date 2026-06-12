# CRPT ω-Tower — Theorem & Definition Index

**Status:** v1.0.0-rc7 (release candidate)  
**Date:** 2026-06-12  
**Coverage:** All levels L0–L8, Lω  
**Total:** 168 definitions · 255 theorems/lemmas/corollaries · 126 remarks · 9 projection axioms

---

## Part I — Index by Level

### L0 — Universal Projection Framework

| Label | Short Name | Tag | Type |
|-------|-----------|-----|------|
| L0.1.D1 | Projection System | `ProjSys` | Definition |
| L0.1.D2 | Fiber & Observable Equivalence | `Fiber` | Definition |
| L0.1.D3 | π-Observability | `Obs_π` | Definition |
| L0.1.T1 | Fiber Completeness | `Fiber-Compl` | Theorem |
| L0.1.T2 | Lift Monotonicity | `Lift-Mono` | Theorem |
| L0.1.T3 | CRPT as Fiber Instance | `CRPT-Fiber` | Theorem |
| L0.2.D1 | Convergent & Persistent Regime | `Conv`, `Pers` | Definition |
| L0.2.T1 | Regime Dichotomy | `Regime-Dich` | Theorem |
| L0.2.T2 | Universal Axiom Coverage | `Ax-Cov-U` | Theorem |
| L0.2.L1 | Conv-Regime Closure | `Conv-Closed` | Lemma |
| L0.2.T3 | CRPT Regimes as Instance | `CRPT-Regimes` | Theorem |
| L0.3.D1 | Universal Horizon Predicates | `H_S^π`, `H_I^π`, `H_O^π` | Definition |
| L0.3.T1 | Horizon Universality | `Horiz-Ind` | Theorem |
| L0.3.T2 | H_I Well-Definedness (Universal) | `H_I-WD-U` | Theorem |
| L0.3.T3 | H-Orbit Non-Invariance | `H-Orbit-NonInv` | Theorem |

### L1 — CRPT Substrate, Axioms, Regimes, and Modes

| Label | Short Name | Tag | Type |
|-------|-----------|-----|------|
| L1.1.D1 | CRPT Substrate | `Sub` | Definition |
| L1.1.D2 | Normal Forms | `NF` | Definition |
| L1.1.D3 | n-Step Reduction | `n-Step` | Definition |
| L1.1.D4 | Reflexive-Transitive Closure | `RT*` | Definition |
| L1.1.D5 | Divergence | `Div` | Definition |
| L1.1.D6 | Bisimulation | `Bisim` | Definition |
| L1.1.D7 | Bisimilarity Relation | `Bisim~` | Definition |
| L1.1.D8 | Observation Labelling | `Obs-Lab` | Definition |
| L1.1.T1 | Observation Labelling Well-Defined and Anchored | `Obs-Lab-WD` | Theorem |
| L1.1.L1 | Bisimulation Union Closure | `Bisim-Union` | Lemma |
| L1.1.L2 | Bisimilarity is Equivalence Relation | `≈-Eq` | Lemma |
| L1.3.D1 | Continuous Persistence | `CPer` | Definition |
| L1.3.T1 | PA-Reach Observable Extension | `Reach-ObsExt` | Theorem |
| L1.3.T2 | Finitary Realization of PA-Reach | `Reach-Fin` | Theorem |
| L1.3.T3 | Topological Realization of PA-Reach | `Reach-Top` | Theorem |
| L1.3.T4 | Decomposition of PA-Reach Realizations | `Reach-Decomp` | Theorem |
| L1.4.D1 | Regimes and Canonicalization Modes | `Mode` | Definition |
| L1.4.T1 | Regime Coexistence and Mode Coverage | `Mode-Comp` | Theorem |
| L1.4.T2 | Native CC | `Nat-CC` | Theorem |
| L1.7.D1 | Topological Separation | `TopSep` | Definition |
| L1.7.D2 | Topological Limit Structure | `Top-Lim` | Definition |
| L1.7.T1 | TopSep Uniqueness | `TopSep-Uniq` | Theorem |
| L1.7.Ax1 | PA-WN_top — Topological Weak Normalisation | `PA-WN_top` | Axiom |
| L1.7.T2 | Independence of PA-WN_top | `WNtop-Ind` | Theorem |
| L1.7.R1 | Topological Structure as Substrate Data | `Top-Inst` | Remark |

### L2 — Projection, Regime, Depth, Canonical Form, and Fibers

| Label | Short Name | Tag | Type |
|-------|-----------|-----|------|
| L2.1.D1 | Projection Operator ρ_M | `ρ_M` | Definition |
| L2.1.D2 | Iterated Projection ρ_M^n | `ρ^n` | Definition |
| L2.1.D3 | Fixed-Point Set Fix(ρ_M) | `Fix` | Definition |
| L2.1.T1 | NF ⊆ Fix | `NF⊆Fix` | Theorem |
| L2.1.T2 | Fix = NF (deterministic case) | `Fix=NF` | Theorem |
| L2.1.T3 | Dead-End Fixpoints | `Dead-End` | Theorem |
| L2.1.D4 | Canonical Fixpoint Map CFix | `Rec-Proj` | Definition |
| L2.1.L1 | Fixpoint Stability | `Fix-Stab` | Lemma |
| L2.1.L2 | Unique Fixpoint | `UF` | Lemma |
| L2.1.T4 | Recursive Projection = Abstraction | `RP=Abs` | Theorem |
| L2.2.D1 | Predecessors Pre_ρ | `Pre_ρ` | Definition |
| L2.2.D2 | Convergent/Persistent Templates | `T^{conv/pers}` | Definition |
| L2.2.L1 | Level Monotonicity | `L-Mono` | Lemma |
| L2.2.D3 | Native Regime Stratification | `Reg-Strat` | Definition |
| L2.2.D4 | Convergent Regime ↓_M | `↓_M` | Definition |
| L2.2.D5 | Persistent Regime ∞_M | `∞_M` | Definition |
| L2.2.T7 | Infinity Duality | `Inf-Dual` | Theorem |
| L2.2.T8 | Regime Exhaustion | `Reg-Exh` | Theorem |
| L2.3.D2 | Derivation Height d_M | `d_M` | Definition |
| L2.3.T1 | Depth Poset | `d-WD` | Theorem |
| L2.4.D1 | Canonical Form Map CNF_M / CFix | `CFix-NM` | Definition |
| L2.4.T2 | Canonical Form Uniqueness | `CNF-Uniq` | Theorem |
| L2.5.D1 | Normal-Form Fiber NFC_M | `NFC-NM` | Definition |
| L2.5.T1 | NFC Equivalence | `≃-Eq` | Theorem |
| L2.5.T2 | CNF = CR (Fiber Theorem) | `CNF=CR` | Theorem |

### L3 — Horizon, Classification, and Persistent Canonical Invariants

| Label | Short Name | Tag | Type |
|-------|-----------|-----|------|
| L3.1.D1 | Structural Horizon H_S | `H_S` | Definition |
| L3.1.D2 | Invariant Horizon H_I | `H_I` | Definition |
| L3.1.D3 | Kernel Congruence | `Ker-Cong` | Definition |
| L3.1.D4 | Depth Horizon H_O | `H_O` | Definition |
| L3.1.D5 | Orbit Signature sig_M | `sig_M-NM` | Definition |
| L3.1.T2 | H_I Well-Definedness | `H_I-WD` | Theorem |
| L3.1.C1 | H_I Decidability | `H_I-Dec` | Corollary |
| L3.1.T1 | Signature Dependence | `Sig-Dep` | Theorem |
| L3.1.D6 | Horizon Predicate HP_M | `HP` | Definition |
| L3.1.T3 | Horizon Abstraction | `Hor-Abs` | Theorem |
| L3.2.D1 | Boolean Lattice | `Bool-Lat` | Definition |
| L3.2.D2 | Boolean Predicates on Classes | `Bool-Pred` | Definition |
| L3.2.L1 | Lattice Order | `Lat-Ord` | Lemma |
| L3.2.T1 | Six-Class Partition | `6-Part` | Theorem |
| L3.2.T2 | Class F is Empty | `F=∅` | Theorem |
| L3.3.D2–D5 | Scope Conditions SC-1 through SC-4 | `SC-1...SC-4` | Definitions |
| L3.3.D6 | Persistent Canonical Form CNF∞_M | `CNF∞-Def` | Definition |
| L3.3.T3–T4 | CNF∞ Existence / Uniqueness (SC-1) | `CNF∞-Ex`/`CNF∞-Uniq` | Theorems |
| L3.3.D10 | Reachability Depth n_M (dual of d_M) | `n-Reach` | Definition |
| L3.3.T6–T8 | CPer Existence / Uniqueness / Stability (total NWF canonical form) | `CPer-Ex`/`CPer-Uniq`/`CPer-Stab` | Theorems |
| L3.3.T9 | WF/NWF Canonical-Form Duality (graded; SC-Imp asymmetry) | `WF-NWF-Dual` | Theorem |

### L4 — Observer, Gateway, Valuation, Duality, Self-Projection, and Perturbation

| Label | Short Name | Tag | Type |
|-------|-----------|-----|------|
| L4.1.D1 | Behavioral Functor | `Behav-F` | Definition |
| L4.1.D2 | Point-Value Observer | `PV-Obs` | Definition |
| L4.1.D3 | Horizon-Constrained Observer | `HC-Obs` | Definition |
| L4.1.D4 | Regime-Dependent Observer | `RD-Obs` | Definition |
| L4.1.D5 | observable triple 𝒪_M | `Obs-Triple` | Definition |
| L4.1.T1 | Observer Consistency | `Obs-Const` | Theorem |
| L4.1.T2 | Naturality of the Semantic Residue | `Obs-Nat` | Theorem |
| L4.1.T3 | Observer Preservation Profile | `Obs-Pres` | Theorem |
| L4.2.D1 | Gateway GW | `GW` | Definition |
| L4.2.T1 | Regime Connectivity | `Reg-Conn` | Theorem |
| L4.3.D1–D4 | Projection Valuation (VS, Step-W, FRH, PV-WF) | `PV1...PV-WF` | Definitions |
| L4.3.T1 | Projection Valuation Theorem | `PV1` | Theorem |
| L4.3.C1 | PV Corollary | `PV1C` | Corollary |
| L4.4.T1–T5 | Five Duality Theorems | `Dual-1...Dual-5` | Theorems |
| L4.5.D1–D3 | Inversion Horizon / CPD / CIH | `Inv-Hor`, `CPD`, `CIH` | Definitions |
| L4.5.T1–T2 | Inversion Theorems | `Inv-1`, `Inv-2` | Theorems |
| L4.6.T1 | Self-Projection Theorem | `SP1` | Theorem |
| L4.7.T1–T2 | Coherent Perturbation Theorems | `CP-1`, `CP-2` | Theorems |

### L5 — Model Algebra, Homomorphisms, and Model Theory

| Label | Short Name | Tag | Type |
|-------|-----------|-----|------|
| L5.1.D1–D6 | Model Algebra Operations (∩, ×, /∼, ∪, Spec — partial meet ∩) | Multiple | Definitions |
| L5.1.T1–T5 | Algebra Law Theorems | Multiple | Theorems |
| L5.2.D1 | Model Homomorphism Hom | `Hom` | Definition |
| L5.2.T1 | Mod_CRPT Category | `Mod-Cat` | Theorem |
| L5.5.D1 | The Category Mod_CRPT | `Mod_CRPT-Cat` | Definition |
| L5.5.D2 | Identity Morphism | `Id-Mor` | Definition |
| L5.5.T1 | Composition Closure | `Comp-Closed` | Theorem |
| L5.5.T2 | Category Laws | `Cat-Laws` | Theorem |
| L5.5.T3 | Homomorphisms Preserve Structure | `Hom-Pres` | Theorem |
| L5.2.D3 | Regime-Restricted Isomorphism | `R-Iso` | Definition |
| L5.2.T2–T6 | Φ_ZC / Φ_CH / Φ_ZH, horizon & collapse preservation | Multiple | Theorems |
| L5.2.D4 | Instantiation = Faithful Embedding | `Inst-Emb` | Definition |
| L5.2.T7 | R-Iso = Saturated Faithful Embedding | `Iso-Sat` | Theorem |
| L5.2.D5 | Persistent Regime-Restricted Isomorphism | `R-Iso∞` | Definition |
| L5.2.T8 | Regime Duality of Restricted Isomorphisms | `Iso-Dual` | Theorem |
| L5.2–L5.2 | Formal Theory T_CRPT / Σ_CRPT | Multiple | Definitions |
| L5.3.T1 | Model Correspondence | `Mod-Corr` | Theorem |
| L5.3.T3 | Category Equivalence | `Cat-Eq` | Theorem |
| L5.2 | Scope Boundaries | — | Remark |
| L5.3.T4 | FOL Finiteness | `FOL-Fin` | Theorem |
| L5.4.T1–T3 | Model Order Theorems | Multiple | Theorems |

### L6 — Persistent Orbit Invariants, NWF Horizons, Model Selection, and Degeneracy

| Label | Short Name | Tag | Type |
|-------|-----------|-----|------|
| L6.1.D1–D3 | Orbit Type (OT, OS, OC) | `OT`, `OS`, `OC` | Definitions |
| L6.1.T1–T4 | AOI Impossibility Theorems | `AOI1`–`AOI-Mast` | Theorems |
| L6.2.D1 | Orbit-Type Classification (AP/EP/P) | `OTC` | Definition |
| L6.2.T1 | Orbit-Type Partition | `OT-Part` | Theorem |
| L6.2.D2 | Three-Tier Framework | `3-Tier` | Definition |
| L6.2.T2 | Tier Compatibility | `Tier-Compat` | Theorem |
| L6.2.T3 | AP Irreducibility | `AP-Irred` | Theorem |
| L6.3.T1 | SC-Impossibility | `SC-Imp` | Theorem |
| L6.4.D1–D3 | NWF Horizon Partition (Classes A*–F*) | Multiple | Definitions |
| L6.4.T1–T3 | NWF Horizon Theorems | Multiple | Theorems |
| L6.5.D1 | Regime-Type Determinacy | `RTD` | Definition |
| L6.5.T1 | Regime Type is Substrate-Determined | `RTD-Det` | Theorem |
| L6.5.T2–T4 | Regime-Type Decidability / Undecidability / Non-Internalisability | `RTD-Dec`, `RTD-Und`, `RTD-NI` | Theorems |
| L6.5.T5 | Regime-Type Trichotomy | `RegType-Tri` | Theorem |
| L6.6.D1 | Degeneracy Condition | `Dege-Inv` | Definition |
| L6.6.T1–T2 | Degeneracy Theorems | Multiple | Theorems |

### L7 — Categorical Collapse, Functoriality, and Model-Theory Fibration

| Label | Short Name | Tag | Type |
|-------|-----------|-----|------|
| L7.1.D1 | Galois Insertion α_M ⊣ γ_M | `GI` | Definition |
| L7.1.T1 | Galois Connection | `GC` | Theorem |
| L7.1.C1–C3 | GC Corollaries | `GC1`–`GC3` | Corollaries |
| L7.1.D2 | Quotient Projection π_M | `Quot-Proj` | Definition |
| L7.1.L1 | π Surjectivity | `π-Sur` | Lemma |
| L7.1.T2 | Kernel Fibration | `Ker-Fib` | Theorem |
| L7.1.D3 | Abstraction Quotient Q_M | `Ab-Quot` | Definition |
| L7.1.T3 | Abstraction-Collapse Duality | `Abs-Coll` | Theorem |
| L7.1.D4 | Collapse Operator | `Collapse-Def` | Definition |
| L7.1.T4 | Collapse(M) is a (pure-WF) CRPT Model | `Collapse-Model` | Theorem |
| L7.1.C4 | Quotient Projection is a Homomorphism | `Collapse-Hom` | Corollary |
| L7.1.D5 | Persistent Galois Insertion α∞ ⊣ γ∞ | `GI∞` | Definition |
| L7.1.T5 | Persistent Galois Connection (graded; SC-Imp) | `GC∞` | Theorem |
| L7.2.D1 | Category Mod_CRPT | `Mod_CRPT` | Definition |
| L7.2.T1 | Mod_CRPT is a Category (≃-quotient hom-sets) | `Mod-Cat-Q` | Theorem |
| L7.2.D2–D2 | ω-Category Structure / Natural Transformations | `ω-Cat`, `η-Nat` | Definitions |
| L7.2.T2 | η Composition | `η-Comp` | Theorem |
| L7.2.T3 | Lift as Endofunctor | `Lift-Endo` | Theorem |
| L7.2.D5 | Collapse Functor | `Coll-F` | Definition |
| L7.2.T4 | Lift ⊣ Collapse Adjunction | `Lift⊣Coll` | Theorem |
| L7.3.T1 | CRPT Functor | `F-Func` | Theorem |

### L8 — Tower Construction and Horizontal-Vertical Duality

| Label | Short Name | Tag | Type |
|-------|-----------|-----|------|
| L8.1.D1 | Free Monoidal Algebra FMA | `FMA` | Definition |
| L8.1.L1 | FMA Well-Foundedness | `FMA-WF` | Lemma |
| L8.1.L2 | FMA Unique Decomposition | `FMA-UD` | Lemma |
| L8.1.D2 | Canonical Projection on FMA | `FMA-Proj` | Definition |
| L8.1.L3 | FMA-Proj satisfies C1 and C3 | `FMA-C1C3` | Lemma |
| L8.2.D1 | Abstraction Quotient Q_M | `Ab-Quot-28` | Definition |
| L8.2.D2 | Lift Operator | `Lift-Def` | Definition |
| L8.2.D3 | Canonical Inclusion ι_M | `Can-Incl` | Definition |
| L8.2.T1 | Fixpoints-to-Basics | `Fix-Bas` | Theorem |
| L8.2.C1 | Lift Depth | `Lift-Depth` | Corollary |
| L8.2.T2 | Horizon Inheritance under Lift | `Hor-Lift` | Theorem |
| L8.3.T1 | Lift preserves PA-WN | `Lift-WN` | Theorem |
| L8.3.T2 | Lift preserves PA-Conf | `Lift-Conf` | Theorem |
| L8.3.T3 | Lift preserves WF-Canon | `Lift-WFCanon` | Theorem |
| L8.3.T4 | Lift Compatibility with CRPT | `Lift-Compat` | Theorem |
| L8.4.D1 | Tower Sequence Tower(M) | `Tower` | Definition |
| L8.4.T1 | Tower Existence | `Twr-Ex` | Theorem |
| L8.4.T2 | NFC Partition is Tower Invariant (Q_{M_n} ≅ Q_M) | `NFC-TInv` | Theorem |
| L8.4.T4 | Tower Growth Resolution (trichotomy) | `Twr-Growth` | Theorem |
| L8.4.T3 | Faithful Embedding of Tower Levels | `Faith-Emb` | Theorem |
| L8.5.D1 | NWF Abstraction Quotient Q_M^* | `NWF-Quot` | Definition |
| L8.5.D2 | NWF-Extended Lift Lift*(M) | `Lift∞` | Definition |
| L8.5.T1 | NWF Periodicity | `NWF-Per` | Theorem |
| L8.5.T2 | Lift*(M) satisfies PA-NWF | `Lift∞-NWF` | Theorem |
| L8.6.T1 | Horizontal-Vertical Duality | `HV-Dual` | Theorem |
| L8.6.T3 | Information Loss at Tower Horizon | `Info-Loss` | Theorem |
| L8.6.T4 | σ-Paths are Not a Third Regime | `σ-Not3rd` | Theorem |
| L8.6.T2 | Tower Horizon Characterization | `Twr-Hor` | Theorem |
| L8.6.D1–D2 | Tower Image / Discriminability | `Twr-Img`, `Twr-Disc` | Definitions |
| L8.6.T6 | Discriminability Survival | `Disc-Surv` | Theorem |
| L8.6.T7 | Tower Abstraction Thesis | `Twr-AThesis` | Theorem |
| L8.7.D2–D2 | Tower ω-Category / ω-Cat Structure | `Twr-ωCat`, `ω-Cat-Str` | Definitions |
| L8.7.T2 | Self-Ontological Soundness | `Self-Ont` | Theorem |
| L8.7.T1 | Tower ω-Category Theorem | `Twr-ωCat-T` | Theorem |
| L8.8.T1 | Axiom Completeness-Consistency | `Ax-CC` | Theorem |
| L8.8.T2 | OR5 Coverage | `OR5-Cover` | Theorem |
| L8.8.T3 | OR5 Functoriality | `OR5-Func` | Theorem |
| L8.8.C1 | Regime Naturality | `Reg-Nat` | Corollary |
| L8.5.D1 | NWF Abstraction Quotient Q_M^* | `NWF-Quot` | Definition |
| L8.9.T1 | Tower Tail Self-Similarity | `Twr-Tail-Sim` | Theorem |
| L8.9.D2 | CRPT-Fractal Projection System | `CRPT-Fractal` | Definition |
| L8.9.T2 | Every CRPT Tower is Fractal | `Twr-Fractal` | Theorem |
| **L8.10.L1** | **Properties of →_σ^{Lift}** | **`Prop-σ-Lift`** | **Lemma** |
| **L8.6.T1** | **→_ρ^{Lift} ⊆ →_σ^{Lift}** | **`Lift-Red-Struc`** | **Theorem** |
| **L8.6.C1** | **Substrate Compatibility of Lift** | — | **Corollary** |
| **L8.10.C1** | **Lift Creates Pure WF Models** | **`Lift-Pure-WF`** | **Corollary** |
| **L8.6.T3** | **Tower is Strictly Infinite** | **`Tower-Inf`** | **Theorem** |
| **L8.10.R3** | **Q_M Cardinality** | **`Q_M-Card`** | **Remark** |

### Lω — Meta-CRPT: CRPT Applied to Itself

| Label | Short Name | Tag | Type |
|-------|-----------|-----|------|
| Lω.1.D1 | Self-Substrate 𝒰_CRPT | `U_CRPT` | Definition |
| Lω.1.T1 | Self-Substrate is CRPT Model | `Self-Model` | Theorem |
| Lω.2.T1 | Self-Horizon Classification | `Self-Horiz` | Theorem |
| Lω.3.D1 | Rank Function m_CRPT | `m_CRPT` | Definition |
| Lω.4.T1 | Tower of Towers Structure | `Tower-of-Towers` | Theorem |
| Lω.5.T1 | Self-Consistency Fixed Point | `Self-FP` | Theorem |
| Lω.6.T1 | Anchor Fractality Theorem | `Anchor-Fractal` | Theorem |
| Lω.6.C1 | Fractal Claim is Internal | `Fractal-Internal` | Corollary |
| Lω.6.C2 | No Internal ω-State Introduced | `No-Internal-ω-State` | Corollary |
| **Lω.7.L1** | **→_{ρ_CRPT} is Acyclic** | **`CRPT-Acyclic`** | **Lemma** |
| **Lω.7.R2** | **Self_CRPT Universe is Finite** | **`Self-CRPT-Finite`** | **Remark** |
| **Lω.7.T1** | **∞_{CRPT} = ∅** | **`CRPT-WF`** | **Theorem** |
| **Lω.7.T2** | **L1.1.D1 is the Unique Projective Fixed Point** | **`Lω-FixedPt-Unique`** | **Theorem** |
| **Lω.8.D1** | **The Specification Substrate** | **`Spec-Sub`** | **Definition** |
| **Lω.8.T1** | **Sections are Fibers** | **`Self-Sect`** | **Theorem** |
| **Lω.8.D2** | **Rank Stratification of the Specification** | **`Spec-Rank`** | **Definition** |
| **Lω.8.D3** | **The Status Classification** | **`Status`** | **Definition** |
| **Lω.8.T2** | **Ranks versus Levels** | **`Rank-vs-Level`** | **Theorem** |
| **Lω.8.R1** | **The Census Discipline** | **`Sect-Census`** | **Remark** |

> **Bold rows** indicate theorems added at the Lω level.

---

## Part II — Index by Concept

### Projection & Fibers
[`ProjSys` (L0.1.D1)](CRPT_OMEGA_TOWER_L0.md#projection-system) · [`Fiber` (L0.1.D2)](CRPT_OMEGA_TOWER_L0.md#fiber-and-observable-equivalence) · [`Obs_π` (L0.1.D3)](CRPT_OMEGA_TOWER_L0.md#π-observability) · [`ρ_M` (L2.1.D1)](CRPT_OMEGA_TOWER_L2.md#projection-operator-ρ_m) · [`Rec-Proj` (L2.1.D4)](CRPT_OMEGA_TOWER_L2.md#recursive-projection) · [`NFC-NM` (L2.5.D1)](CRPT_OMEGA_TOWER_L2.md#normal-form-fiber--native-form) · [`CNF=CR` (L2.5.T2)](CRPT_OMEGA_TOWER_L2.md#cnf-fiber--church-rosser-quotient) · [`Ab-Quot-28` (L8.2.D1)](CRPT_OMEGA_TOWER_L8.md#abstraction-quotient)

### Regimes (↓_M, ∞_M)
`Conv`, [`Pers` (L0.2.D1)](CRPT_OMEGA_TOWER_L0.md#convergent-and-persistent-elements) · [`Regime-Dich` (L0.2.T1)](CRPT_OMEGA_TOWER_L0.md#universal-regime-dichotomy) · [`↓_M` (L2.2.D4)](CRPT_OMEGA_TOWER_L2.md#convergent-regime-_m) · [`∞_M` (L2.2.D5)](CRPT_OMEGA_TOWER_L2.md#persistent-regime-_m) · [`Inf-Dual` (L2.2.T7)](CRPT_OMEGA_TOWER_L2.md#horizontal-vertical-infinity-duality) · [`Reg-Exh` (L2.2.T8)](CRPT_OMEGA_TOWER_L2.md#regime-exhaustiveness) · [`CRPT-WF` (Lω.7.T1)](CRPT_OMEGA_TOWER_Lω.md#lω7t1--crpt-wf-the-self-application-is-pure-well-founded)

### Canonical Forms & Depth
[`NF` (L1.1.D2)](CRPT_OMEGA_TOWER_L1.md#normal-form) · [`Fix` (L2.1.D3)](CRPT_OMEGA_TOWER_L2.md#fixpoint-set) · [`Fix=NF` (L2.1.T2)](CRPT_OMEGA_TOWER_L2.md#fix--nf) · [`CFix-NM` (L2.4.D1)](CRPT_OMEGA_TOWER_L2.md#canonical-normal-form-map--native-form) · [`CNF-Uniq` (L2.4.T2)](CRPT_OMEGA_TOWER_L2.md#cnf-uniqueness--orbit-scoped-uniqueness) · [`d_M` (L2.3.D2)](CRPT_OMEGA_TOWER_L2.md#rank-function--derivation-height-notation-d_m) · [`d-WD` (L2.3.T1)](CRPT_OMEGA_TOWER_L2.md#d_m-is-well-defined-on-μt_ρm) · [`CNF∞-Def` (L3.3.D6)](CRPT_OMEGA_TOWER_L3.md#canonical-orbit-invariant-cnf_m-ω-limit-quotient)

### Horizons (H_S, H_I, H_O)
[`H_S` (L3.1.D1)](CRPT_OMEGA_TOWER_L3.md#structural-horizon-h_s) · [`H_I` (L3.1.D2)](CRPT_OMEGA_TOWER_L3.md#invariant-horizon--kernel-congruence-predicate-h_i) · [`H_O` (L3.1.D4)](CRPT_OMEGA_TOWER_L3.md#abstraction-depth-horizon-h_o) · [`sig_M-NM` (L3.1.D5)](CRPT_OMEGA_TOWER_L3.md#orbit-signature--native-form) · [`H_I-WD` (L3.1.T2)](CRPT_OMEGA_TOWER_L3.md#h_i-well-definedness--general-kernel-theorem) · [`H_I-WD-U` (L0.3.T2)](CRPT_OMEGA_TOWER_L0.md#h_i-well-definedness--universal-kernel-theorem) · [`Hor-Abs` (L3.1.T3)](CRPT_OMEGA_TOWER_L3.md#horizons-as-abstraction-limits) · [`Hor-Lift` (L8.2.T2)](CRPT_OMEGA_TOWER_L8.md#horizon-inheritance-under-lift)

### Six-Class Partition
[`Bool-Pred` (L3.2.D2)](CRPT_OMEGA_TOWER_L3.md#independent-boolean-predicates) · [`6-Part` (L3.2.T1)](CRPT_OMEGA_TOWER_L3.md#six-classes-partition-μt_ρm-as-boolean-stratification) · [`F=∅` (L3.2.T2)](CRPT_OMEGA_TOWER_L3.md#class-f---in-every-deterministic-crpt-model)

### Observer Architecture
[`Obs-Triple` (L4.1.D5)](CRPT_OMEGA_TOWER_L4.md#coalgebraic-observable-triple) · [`Obs-Const` (L4.1.T1)](CRPT_OMEGA_TOWER_L4.md#coalgebraic-observable-is-fully-derived--constructible) · [`GW` (L4.2.D1)](CRPT_OMEGA_TOWER_L4.md#gateway) · [`Reg-Conn` (L4.2.T1)](CRPT_OMEGA_TOWER_L4.md#regime-connectedness--rt) · [`PV1` (L4.3.T1)](CRPT_OMEGA_TOWER_L4.md#pv-1-wf-existence) · [`SP1` (L4.6.T1)](CRPT_OMEGA_TOWER_L4.md#sp-1-closure)

### Model Algebra & Homomorphisms
[`CRPT-Mod-18` (L5.1.D1)](CRPT_OMEGA_TOWER_L5.md#crpt-model) · [`Hom` (L5.2.D1)](CRPT_OMEGA_TOWER_L5.md#model-homomorphism-φ--m₁--m₂) · [`Mod-Cat` (L5.2.T1)](CRPT_OMEGA_TOWER_L5.md#crpt-models-form-category-mod_crpt) · [`Mod_CRPT` (L7.2.D1)](CRPT_OMEGA_TOWER_L7.md#category-mod_crpt) · [`Mod-Cat-Q` (L7.2.T1)](CRPT_OMEGA_TOWER_L7.md#mod_crpt-is-a-category-with--quotient-hom-sets) · [`Iso` (L5.2.D2)](CRPT_OMEGA_TOWER_L5.md#isomorphism) · [`R-Iso` (L5.2.D3)](CRPT_OMEGA_TOWER_L5.md#regime-restricted-isomorphism) · [`Inst-Emb` (L5.2.D4)](CRPT_OMEGA_TOWER_L5.md#instantiation-as-faithful-embedding) · [`Iso-Sat` (L5.2.T7)](CRPT_OMEGA_TOWER_L5.md#regime-restricted-isomorphism--saturated-faithful-embedding) · [`R-Iso∞` (L5.2.D5)](CRPT_OMEGA_TOWER_L5.md#persistent-regime-restricted-isomorphism) · [`Iso-Dual` (L5.2.T8)](CRPT_OMEGA_TOWER_L5.md#regime-duality-of-restricted-isomorphisms)

### Categorical Structures (Adjunctions, Functors)
[`GI` (L7.1.D1)](CRPT_OMEGA_TOWER_L7.md#galois-insertion--recursive-projection-pair) · [`GC` (L7.1.T1)](CRPT_OMEGA_TOWER_L7.md#galois-connection--full-biconditional) · [`Abs-Coll` (L7.1.T3)](CRPT_OMEGA_TOWER_L7.md#abstraction-collapse-duality--functorial-representation) · [`Collapse-Model` (L7.1.T4)](CRPT_OMEGA_TOWER_L7.md#collapse-is-a-crpt-model) · [`GI∞` (L7.1.D5)](CRPT_OMEGA_TOWER_L7.md#persistent-galois-insertion-α--γ) · [`GC∞` (L7.1.T5)](CRPT_OMEGA_TOWER_L7.md#persistent-galois-connection) · [`Lift-Endo` (L7.2.T3)](CRPT_OMEGA_TOWER_L7.md#lift-is-an-endofunctor-on-mod_crpt) · [`Coll-F` (L7.2.D5)](CRPT_OMEGA_TOWER_L7.md#collapse-functor-collapse--mod_crpt--mod_crpt) · [`Lift⊣Coll` (L7.2.T4)](CRPT_OMEGA_TOWER_L7.md#lift--collapse-is-an-adjoint-pair) · [`F-Func` (L7.3.T1)](CRPT_OMEGA_TOWER_L7.md#f-is-a-functor-mod_crpt--ωcat)

### Lift Operator & Tower Construction
[`Lift-Def` (L8.2.D2)](CRPT_OMEGA_TOWER_L8.md#free-lift-of-m) · [`Tower` (L8.4.D1)](CRPT_OMEGA_TOWER_L8.md#crpt-tower-generated-by-m) · [`Twr-Ex` (L8.4.T1)](CRPT_OMEGA_TOWER_L8.md#tower-existence) · [`NFC-TInv` (L8.4.T2)](CRPT_OMEGA_TOWER_L8.md#nfc-partition-is-a-tower-invariant) · [`Faith-Emb` (L8.4.T3)](CRPT_OMEGA_TOWER_L8.md#faithful-embedding) · [`Lift-Red-Struc` (L8.10.T1)](CRPT_OMEGA_TOWER_L8.md#l810t1--lift-red-struc-reduction-includes-in-structure-for-lift) · [`Lift-Pure-WF` (L8.10.C1)](CRPT_OMEGA_TOWER_L8.md#l810c1--lift-pure-wf-lift-of-any-model-is-pure-wf) · [`Tower-Inf` (L8.10.T2)](CRPT_OMEGA_TOWER_L8.md#l810t2--tower-inf-the-crpt-tower-is-strictly-infinite) · [`Q_M-Card` (L8.10.R3)](CRPT_OMEGA_TOWER_L8.md#q_m-card-cardinality-of-the-query-signature)

### Well-Foundedness of Lift
[`FMA-WF` (L8.1.L1)](CRPT_OMEGA_TOWER_L8.md#well-foundedness-of-fma) · [`Lift-WN` (L8.3.T1)](CRPT_OMEGA_TOWER_L8.md#lift-preserves-pa-wn) · [`Lift-Conf` (L8.3.T2)](CRPT_OMEGA_TOWER_L8.md#lift-preserves-pa-conf) · [`Lift-Compat` (L8.3.T4)](CRPT_OMEGA_TOWER_L8.md#lift-of-a-crpt-model-is-crpt-compatible) · [`Prop-σ-Lift` (L8.10.L1)](CRPT_OMEGA_TOWER_L8.md#properties-of-_σlift)

### Horizontal-Vertical Duality
[`HV-Dual` (L8.6.T1)](CRPT_OMEGA_TOWER_L8.md#horizontal-vertical-duality) · [`Info-Loss` (L8.6.T3)](CRPT_OMEGA_TOWER_L8.md#information-loss-at-the-tower-horizon) · [`σ-Not3rd` (L8.6.T4)](CRPT_OMEGA_TOWER_L8.md#σ-paths-within-_m-fibers-are-not-a-third-regime) · [`Twr-Hor` (L8.6.T2)](CRPT_OMEGA_TOWER_L8.md#tower-horizon-characterization)

### Fractal & Self-Similarity
[`Twr-Tail-Sim` (L8.9.T1)](CRPT_OMEGA_TOWER_L8.md#l89t1--tower-tail-self-similarity) · [`CRPT-Fractal` (L8.9.D2)](CRPT_OMEGA_TOWER_L8.md#l89d2--crpt-fractal-projection-system) · [`Twr-Fractal` (L8.9.T2)](CRPT_OMEGA_TOWER_L8.md#l89t2--crpt-tower-fractality) · [`Anchor-Fractal` (Lω.6.T1)](CRPT_OMEGA_TOWER_Lω.md#anchor-fractal-closure)

### Self-Application (Lω)
[`U_CRPT` (Lω.1.D1)](CRPT_OMEGA_TOWER_Lω.md#lω1d1--self-substrate-𝒰_crpt-with-topology-and-bisimilarity) · [`Self-Model` (Lω.1.T1)](CRPT_OMEGA_TOWER_Lω.md#lω1t1--self-substrate-is-a-crpt-model) · [`Self-Horiz` (Lω.2.T1)](CRPT_OMEGA_TOWER_Lω.md#lω2t1--self-horizon-classification-of-the-anchor) · [`m_CRPT` (Lω.3.D1)](CRPT_OMEGA_TOWER_Lω.md#lω3d1--rank-function-m_crpt) · [`Tower-of-Towers` (Lω.4.T1)](CRPT_OMEGA_TOWER_Lω.md#lω4t1--tower-of-towers-structure) · [`Self-FP` (Lω.5.T1)](CRPT_OMEGA_TOWER_Lω.md#lω5t1--self-consistency-fixed-point) · [`CRPT-Acyclic` (Lω.7.L1)](CRPT_OMEGA_TOWER_Lω.md#lω7l1--crpt-acyclic-the-self-reduction-is-acyclic) · [`CRPT-WF` (Lω.7.T1)](CRPT_OMEGA_TOWER_Lω.md#lω7t1--crpt-wf-the-self-application-is-pure-well-founded) · [`Lω-FixedPt-Unique` (Lω.7.T2)](CRPT_OMEGA_TOWER_Lω.md#lω7t2--lω-fixedpt-unique-l11d1-is-the-unique-projective-fixed-point)

---

## Part III — Imported vs. Novel at a Glance

| Source | Items (approx.) | Examples |
|--------|----------------|---------|
| **Imported** (ARS, bisimulation, category theory, fiber theory) | ∼45 | `Bisim`, `≈-Eq`, `FMA`, `GI`, `η-Comp` |
| **Reframed** (anchor concepts presented in new organizational layer) | ∼12 | `H_O`, `Ab-Quot-28`, `Quot-Proj`, `Lift∞` |
| **Novel CRPT** (original constructions) | ∼100+ | `H_S`, `H_I`, `ρ_M`, `6-Part`, `F=∅`, `HV-Dual`, `Self-FP` |
| **Novel CRPT** (L8–Lω supplementary) | 10 | `Prop-σ-Lift`, `Lift-Red-Struc`, `Lift-Pure-WF`, `Tower-Inf`, `CRPT-Acyclic`, `CRPT-WF`, `Lω-FixedPt-Unique`, `Q_M-Card`, `Self-CRPT-Finite` |

---

*This index is auto-synthesized from the level files. For full formal statements and proofs, see the individual level files referenced by the label column.*
