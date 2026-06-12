# CRPT ω-Tower — Release Notes

**Status:** v1.0.0-rc6 (release candidate)  
**Date:** 2026-06-12  
**Document set:** CRPT_OMEGA_TOWER_*.md (L0–L8, Lω, and support files)

---

## Version 1.0.0-rc6 (2026-06-12)

Changes since rc4 (rc5 was an internal milestone, folded into this release):

- **Self-Sectioning (new theory).** The tower now carries its own sectioning discipline: `Spec-Sub` (Lω.8.D1) reads the specification as a pure-WF CRPT model (constructs as universe, primary Source anchors as ρ, citations as →_σ); `Self-Sect` (Lω.8.T1) proves sections are fibers, boundary soundness is the H_S/H_I criterion, sibling sections require stated membership criteria, and reprise sections are Class-F configurations — empty by `F=∅`; `Sect-Census` (Lω.8.R1) makes sectioning computable. Companion artifact: CRPT_OMEGA_TOWER_SECTION_MAP.md (the generated fiber census).
- **Boundary rulings.** New section L1.7 "The Substrate Topology" collects the 𝒯-interface fiber (TopSep, Top-Lim, TopSep-Uniq, PA-WN_top — now L1.7.Ax1 — WNtop-Ind, Top-Inst); L1.2/L1.3 headers state their membership criteria (regime-local step axioms vs regime-universal orbit axioms); L8.2/L8.6/L8.10 are declared Lift siblings with stated criteria, L8.10 retitled "The Reduction Structure of Lift(M)", and the shifted purpose paragraphs of L8.2/L8.6/L8.10 restored; L4.8 retired (a self-declared restatement of `F=∅` — the no-reprise law applied to itself); L5.5 re-scoped as the category-laws theory with new constructs `Id-Mor`, `Comp-Closed`, `Cat-Laws` (Mod_CRPT's category-hood proved, not asserted); Inf-Dual's three homes (L0.6 / L2.2.T7 / L8.6) and the self-consistency pair (L0.10 / Lω.5) carry explicit scope divisions.
- **Hyperlinked references.** All cross-references — 1,961 at release — are markdown hyperlinks to the cited construct's subsection, in both convention forms (backticked tags and PA-* axiom citations), with GitHub-compatible anchors validated against the actual heading slug sets. Link text preserves the `Tag` (Label) convention.
- **Final correctness audit.** 26 constructs carried pre-convention bare citation lines (or none): all now have convention-conformant Sources with internal anchors. 17 theorems/lemmas/corollaries lacked proofs (the six L0 instance theorems among them): rigorous proofs supplied; Twr-Hor's proof relocated into its own block. 22 placeholder synopses replaced with real ones. Regressions repaired: Sig-Strat's pre-rc4 persistent-signature form, L0.8.T2's tier mapping (now aligned with `3-Tier` and citing L1.7.Ax1), L0.2.T3's coverage bullets, Bool-typed Observable leftovers in the formal PA-Prod statement and an LA_M example, plus substitution artifacts in L0.1.T3 and L0.9.T2.
- **Label normalization (54 relabels).** Labels now reflect the fiber structure: topology constructs moved to L1.7; remark sequences renumbered to physical order in eleven sections; L5.5 theorem numbering normalized; L8.10.C2 → C1. Reference rewriting was map-driven and collision-safe; historical release notes untouched. Migration map:

| Old label | New label |
|---|---|
| L1.2.Ax7 | L1.7.Ax1 |
| L1.2.D1 | L1.7.D1 |
| L1.2.D2 | L1.7.D2 |
| L1.2.R1 | L1.2.R2 |
| L1.2.R2 | L1.2.R1 |
| L1.2.T1 | L1.7.T1 |
| L1.4.R3 | L1.7.R1 |
| L1.4.T3 | L1.7.T2 |
| L2.2.R1 | L2.2.R5 |
| L2.2.R2 | L2.2.R6 |
| L2.2.R3 | L2.2.R2 |
| L2.2.R4 | L2.2.R3 |
| L2.2.R5 | L2.2.R4 |
| L2.2.R6 | L2.2.R8 |
| L2.2.R7 | L2.2.R1 |
| L2.2.R8 | L2.2.R7 |
| L3.1.R1 | L3.1.R6 |
| L3.1.R10 | L3.1.R7 |
| L3.1.R11 | L3.1.R3 |
| L3.1.R2 | L3.1.R8 |
| L3.1.R3 | L3.1.R9 |
| L3.1.R4 | L3.1.R10 |
| L3.1.R5 | L3.1.R1 |
| L3.1.R6 | L3.1.R2 |
| L3.1.R7 | L3.1.R4 |
| L3.1.R8 | L3.1.R5 |
| L3.1.R9 | L3.1.R11 |
| L4.1.R4 | L4.1.R3 |
| L5.3.R1 | L5.3.R2 |
| L5.3.R2 | L5.3.R3 |
| L5.3.R3 | L5.3.R4 |
| L5.3.R4 | L5.3.R5 |
| L5.3.R5 | L5.3.R1 |
| L5.5.T1 | L5.5.T3 |
| L5.5.T2 | L5.5.T1 |
| L5.5.T3 | L5.5.T2 |
| L6.3.R3 | L6.3.R5 |
| L6.3.R5 | L6.3.R3 |
| L7.1.R1 | L7.1.R2 |
| L7.1.R2 | L7.1.R1 |
| L7.2.R1 | L7.2.R2 |
| L7.2.R2 | L7.2.R1 |
| L8.10.C2 | L8.10.C1 |
| L8.6.R2 | L8.6.R3 |
| L8.6.R3 | L8.6.R4 |
| L8.6.R4 | L8.6.R5 |
| L8.6.R5 | L8.6.R6 |
| L8.6.R6 | L8.6.R2 |
| Lω.5.R1 | Lω.5.R2 |
| Lω.5.R2 | Lω.5.R1 |
| Lω.7.R1 | Lω.7.R2 |
| Lω.7.R2 | Lω.7.R3 |
| Lω.7.R3 | Lω.7.R4 |
| Lω.7.R4 | Lω.7.R1 |

- **Audit at release.** 553 constructs (167 definitions · 251 theorems/lemmas/corollaries · 126 remarks · 9 projection axioms); 0 dangling references, 0 tag mismatches, 0 duplicate labels or tags, 0 order/gap violations, 0 broken links, every theorem proved, every construct sourced, anchor DAG well-founded.

## Version 1.0.0-rc4 (2026-06-11)

Changes since rc3 (no theorem statements weakened; one axiom strengthened to its meaning):

- **The observation labelling is derived, not primitive.** New `Obs-Lab` (L1.1.D8) defines obs from the Observable Contract of PA-Prod — a normal form is its own atomic observable; a non-fixpoint emits the content of its projection step — with `Obs-Lab-WD` (L1.1.T1) proving NF-injectivity, regime separation, no-silent-labels (productivity is what makes the labelled reading non-degenerate), and Σ_CRPT-definability, so model-hood-as-satisfaction (`Mod-Corr` (L5.3.T1)) is well-posed with no new primitive. The contract codomain is generalised to a pointed set (O_M, 0), Bool minimal; Σ_CRPT gains the sort O.
- **PA-Reach is the meaning itself; the mechanisms are theorems.** PA-Reach (L1.3.Ax2) now asserts that every persistent orbit has a canonically representable asymptotic destination — ω_≈(x) non-empty, finite, ρ_M-closed, attracting — with CPer_M(x) its canonical representative. The reach mechanisms are realization theorems: recurrence (`PA-Reach-Fin` (L1.3.T2), eventual periodicity *derived* from PA-Bisim equivariance), convergence (`PA-Reach-Top` (L1.3.T3), the limit a fixpoint by continuity), and their composite (`PA-Reach-Decomp` (L1.3.T4)) — no third mechanism exists.
- **Exactly two modes; "asymptotic" is the analysis layer.** `Mode` (L1.4.D1) redefined: a mode is a reach mechanism — recurrence (finitary) or convergence (topological) — the same pair serving both regimes (PA-WN's d_M / PA-Reach's n_M; PA-WN_top). Asymptotic orbit invariance is not a mode: the AOI is the invariant theory of the destination, defined unconditionally and finitely presentable in either mode. "Asymptotic mode" is purged tower-wide.
- **The persistent signature is CRPT-native.** sig_M on ∞_M is the observation trace up to tail-equivalence (`sig_M-NM` (L3.1.D5)); H_I^top compares approach traces for tail-equivalence; the ℝ^ℕ profile and Hölder comparisons are demoted to an instantiation remark (`sig-Metric` (L3.1.R11)).
- **Twelve-class partition corrected.** `12-Part-EE` (L3.2.T3) no longer claims F_∞ empty (the kernel-uniformity collapse is convergent-regime-specific; F_∞ is inhabitable); the class table reads every row uniformly through x's own orbit-limit.
- **Spectrum and complexity corrected.** `Spec-Def` (L6.3.D6) is existence-only (no sum clause); `Freq-Sum` (L6.3.L2) scoped to finite B̃ with the infinite-B̃ failure exhibited; `OS-21B` (L6.3.D5) typed over bisimulation classes with the five-class spectrum as derived push-forward (`OS-Push` (L6.3.R5)); `OC-21B` (L6.3.D9) κ reads the recurrent tail classes; SC-1 synopses corrected to the singleton-tail reading; `SC-k` (L6.3.D12) defines the family it names.
- **Encodings and the tower ω-category.** `Enc` (L4.6.D1) injectivity is denotational; `Twr-ωCat` (L8.7.D2) horizontal composition made explicit (left whiskering in-level under the strip-last convention; right action through the tower embeddings) with the interchange law scoped accordingly (`Twr-ωCat-T` (L8.7.T1)).
- **Editorial.** PV2/PV-Dual synopses and proofs corrected (the duality is now actually stated and proved); L-Str/L-Th synopses describe their own definitions; Inf-Dual's quantifier and NFC slips repaired; source-line substitution artifacts fixed; ω-Cat notation unified.
- **Audit.** 0 dangling references, 0 tag/location mismatches, 0 bare table rows, 0 duplicate labels, balanced fences. Totals: 166 definitions · 249 theorems/lemmas/corollaries · 125 remarks · 9 projection axioms.

## Version 1.0.0-rc3 (2026-06-09)

Changes since rc2, all corrective (no theorem statements weakened):

- **Structure.** Promoted the remaining substantive inline remarks (e.g. the WN-vs-SN remark in PA-WN) to standalone subsections with the standard heading + table + Synopsis + Source.
- **Spec findings.** Resolved seven post-rc2 issues surfaced by the implementation audit: (1) the observer triple is invariant under bisimilarity ≈, not ≃_M — only the regime component is ≃_M-invariant (`Obs-Triple` (L4.1.D5), `Sem-Base` (L3.3.R3)); (2) bisimilarity defined on the labelled substrate so `PA-Bisim` is non-vacuous (`Bisim` (L1.1.D6)); (3) ≃_M made regime-aware — CFix-equality on ↓_M, ≃∞ on ∞_M in asymptotic mode (`≃_M` (L2.5.D2)); (4) FMA flat word-length grading; (5) standardised Lift strip convention; (6) Collapse(M) discrete with κ a morphism in Mod_CRPT_≃ (`Collapse-Hom` (L7.1.C4)); (7) L6.4 NWF horizons restated with asymptotic invariants only (≈, ≃∞, CPD), reserving topological forms for the PA-WN_top tier.
- **References.** Corrected `Tag` (Label) citations to name the actual construct tag (`d_M` (L2.3.D2); removed a stale self-citation at L2.4.T5).
- **Audit.** 0 dangling references, 0 tag/location mismatches, 0 mis-rendering table rows, balanced code fences.

## Version 1.0.0-rc2 (2026-06-08)

Changes since rc1, all on the same content (no theorem statements weakened):

- **Rendering.** Every labelled item (Definition/Theorem/Lemma/Corollary/Remark/Axiom) now renders as a proper table; fixed duplicate headings, unescaped pipes in table cells, and the theorem-index column layout.
- **Structure.** Every labelled item has its own subsection: 65 previously-inline remarks/corollaries were promoted to the standard heading + table (new stable tags) + Synopsis + Source.
- **Consistency.** Canonicalised Class F to (Fix, H_S, H_I) = (⊤,⊤,⊤) with a correct emptiness proof; unified the model-homomorphism definition on Hom (L5.2.D1); resolved the L0 self-substrate status (L0 excluded; L1.1.D1 the unique root). Added remark Lω.5.R2 (self-consistency, not generativity).
- **Abstractness.** Removed all applied-domain language (the tower is model-neutral), all legacy/historical phrasing, and all references to downstream tooling (engine-free). Theory name set to Compositional Recursive Projection Theory.
- **Audit.** 0 dangling references, 0 tag/location mismatches, 0 mis-rendering table rows.

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
| **Total** | | **∼12,838 lines** |

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
