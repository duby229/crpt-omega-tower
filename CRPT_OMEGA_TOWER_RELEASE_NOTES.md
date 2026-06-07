# CRPT ω-Tower — Release Notes

**Status:** CRPT ω-Tower  
**Date:**   
**Document set:** CRPT_OMEGA_TOWER_*.md (L0–L8, Lω, and support files)

---

## Version 1.0

### What This Release Is

This is the first release of the **CRPT ω-Tower Specification** — a formal, stratified presentation of Compositional Recursive Projection Theory organized as a ten-level tower (L0–L8 plus the meta-level Lω).

### Scope

The ω-tower covers:

- **L0** — Universal projection framework (π-systems, fibers, observability, universal horizon predicates). Foundations from Lawvere/Schanuel fiber theory and ARS.
- **L1–L2** — CRPT substrate instantiation: the nine PA-* axioms, six axiom profiles, projection operator ρ_M, regime partition (↓_M, ∞_M), derivation height, canonical form map, and NFC fibers.
- **L3–L4** — Horizon predicates (H_S, H_I, H_O), orbit signature, the six-class partition, observer triple 𝒪_M, gateway GW, projection valuation, five duality theorems, self-projection, and coherent perturbation.
- **L5–L6** — Model algebra (∘, ∩, ×, /, ∪), model homomorphisms, the formal theory T_CRPT / Σ_CRPT, persistent orbit classification (AP/EP/P), AOI impossibility, NWF horizons (Classes A*–F*), regime-type determinacy, and degeneracy.
- **L7** — Categorical collapse, Galois insertion, the quotient projection π_M, kernel fibration, abstraction-collapse duality, the category Mod_CRPT, Lift as endofunctor, and the Lift ⊣ Collapse adjunction.
- **L8** — Free monoidal algebra FMA, the Lift operator, fixpoints-to-basics theorem, horizon inheritance under Lift, PA-* axiom preservation, the Tower construction, faithful embedding, NWF-extended Lift*, horizontal-vertical duality, discriminability, tower ω-category, and fractality.
- **Lω** — Self-application: CRPT instantiated on its own anchor constructs 𝒰_CRPT as a CRPT model. Self-horizon classification, rank ordering m_CRPT, tower-of-towers, self-consistency fixed point, anchor fractality, and the formal closure of the theory on itself.

### Support Files

| File | Purpose |
|------|---------|
| `CRPT_OMEGA_TOWER_GLOBAL_MAP.md` | Tower dependency DAG, level summaries, cross-level notation, theorem index overview |
| `CRPT_OMEGA_TOWER_PREFACE.md` | Conceptual introduction: What is CRPT? Why this tower? What is the HOA? |
| `CRPT_OMEGA_TOWER_READING_GUIDE.md` | Four reading paths by audience; prerequisite map; proof depth explanation |
| `CRPT_OMEGA_TOWER_COMMON_PITFALLS.md` | 12 documented misconceptions with corrections and cross-references |
| `CRPT_OMEGA_TOWER_THEOREM_INDEX.md` | Complete theorem, lemma, corollary, and definition index by level and by concept |
| `CRPT_OMEGA_TOWER_DEFINITIONS_INDEX.md` | Alphabetical symbol reference, notation standardization rules, dependency map, axiom profiles |
| `CRPT_OMEGA_TOWER_RELEASE_NOTES.md` | This document |

---

## Formal Properties

The specification achieves the following formal properties:

- **Notation consistency:** All symbols are standardized across L0–Lω: →_ρ (base), →_ρ* (closure), →_ρ^n (n-step), →_ρ^{Lift} (lifted); ρ_M in L1+; NFC_M(f); ≃_M in L1+.
- **Mathematical completeness:** All theorems have complete proofs. All imported constructs are properly cited.
- **Substrate properties:** →_ρ^{Lift} ⊆ →_σ^{Lift} is proved (L8.6.T1). The properties of →_σ^{Lift} are established (L8.10.L1). Every Lift(M) is pure well-founded with ∞_{Lift(M)} = ∅ (L8.10.C2).
- **Tower correctness:** The tower M_n is defined (L8.4.D1). The query signature is invariant Q_{M_n} = Q_{M_0} (L8.4.T2). The tower is strictly infinite — no two levels are isomorphic (L8.6.T3). The cardinality of Q_M is specified (L8.10.R3).
- **Category theory:** Mod_CRPT is defined (L7.2.D1). Collapse(M) is a (pure-WF) CRPT model (L7.1.T4). Lift ⊣ Collapse adjunction is proved (L7.2.T4).
- **Self-application (Lω):** The self-reduction →_{ρ_CRPT} is acyclic — the self-substrate is a DAG (Lω.7.L1). The self-substrate is finite: |𝒰_CRPT| < ω (Lω.7.R1). The self-substrate is well-founded: ∞_CRPT = ∅ (Lω.7.T1). The unique projective fixed point is L1.1.D1 (Lω.7.T2).

---

## Known Limitations

1. **Machine verification absent.** All proofs are written in rigorous natural-language mathematical style. No Lean 4 / Coq formalization exists. Machine-checked verification is the primary goal for future work.

2. **Inline examples deferred.** Four worked examples (L0: finite sets, L1: ℕ with decrement, L8: tower of ℕ, Lω: self-application) are not yet inserted inline.

3. **Categorical diagrams in ASCII.** The seven structural diagrams (tower dependency, fiber structure, six-class Boolean lattice, observer triple, Lift operator, horizontal-vertical duality, collapse/quotient) are ASCII-approximated in GLOBAL_MAP.md. Full TikZ rendering requires a LaTeX build environment.

---

## Future Work

- Lean 4 formalization of L0–L4 (core projection and horizon theory)
- Four inline worked examples (one per level: L0, L1, L8, Lω)
- Seven TikZ diagrams embedded in level files
- Full forward-reference elimination (topological sort of definitions within L1–L8)
- Complete citation sweep across all proofs
- Application notes: CRPT instantiated in ZFC, HoTT, λ-calculus, and process algebra

---

## Document Inventory

| File | Description | Lines (approx.) |
|------|-------------|----------------|
| CRPT_OMEGA_TOWER_INDEX.md | Master index | 60 |
| CRPT_OMEGA_TOWER_GLOBAL_MAP.md | Tower architecture and navigation | 300 |
| CRPT_OMEGA_TOWER_PREFACE.md | Conceptual introduction | 350 |
| CRPT_OMEGA_TOWER_READING_GUIDE.md | Reading paths and prerequisites | 250 |
| CRPT_OMEGA_TOWER_COMMON_PITFALLS.md | 12 documented pitfalls | 380 |
| CRPT_OMEGA_TOWER_L0.md | Universal projection framework | 873 |
| CRPT_OMEGA_TOWER_L1.md | Substrate, axioms, native modes | 1177 |
| CRPT_OMEGA_TOWER_L2.md | Projection, regime, depth, canonical form | 1107 |
| CRPT_OMEGA_TOWER_L3.md | Horizon, classification, invariants | 1066 |
| CRPT_OMEGA_TOWER_L4.md | Observer, gateway, valuation, duality | 805 |
| CRPT_OMEGA_TOWER_L5.md | Model algebra, homomorphisms, model theory | 1200 |
| CRPT_OMEGA_TOWER_L6.md | Persistent orbits, NWF horizons, selection | 2022 |
| CRPT_OMEGA_TOWER_L7.md | Categorical collapse, functoriality | 525 |
| CRPT_OMEGA_TOWER_L8.md | Tower construction, HV-duality | 1347 |
| CRPT_OMEGA_TOWER_Lω.md | Meta-CRPT self-application | 656 |
| CRPT_OMEGA_TOWER_THEOREM_INDEX.md | Complete theorem/definition index | 280 |
| CRPT_OMEGA_TOWER_DEFINITIONS_INDEX.md | Symbol reference and notation rules | 220 |
| CRPT_OMEGA_TOWER_RELEASE_NOTES.md | This document | 220 |
| **Total** | | **~12,838 lines** |

---

## Attribution

CRPT ω-Tower builds on the following imported mathematical traditions:

- **Fiber/projection theory:** Lawvere, Schanuel — *Conceptual Mathematics* (fiber bundles, epi/mono factorization)
- **Abstract Rewriting Systems:** Baader & Nipkow — *Term Rewriting and All That* [1]; Terese — *Term Rewriting Systems* [10]
- **Bisimulation/coalgebra:** Milner [8], Park [9], Rutten [12], Jacobs [13]
- **Category theory:** MacLane — *Categories for the Working Mathematician*; Awodey — *Category Theory*
- **Fixpoint theory:** Tarski, Knaster-Tarski theorem (lattice fixed points)
- **Non-well-founded sets:** Aczel [11]
- **Topological dynamics:** Katok & Hasselblatt [7]

Full bibliography: see References section in CRPT_OMEGA_TOWER_Lω.md.

The novel content of CRPT — H_S, H_I, H_O, six-class partition, observer triple, Lift operator, tower construction, and self-application — is original.

---

*End of Release Notes.*
