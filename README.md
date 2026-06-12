# CRPT ω-Tower

A self-contained formal development of **CRPT** (Compositional Recursive Projection Theory):
a projection-axiom framework over a two-regime substrate (convergent ↓_M and persistent
∞_M), with canonical-form theory, horizon classification, an observer architecture, model
algebra, a categorical self-structure, the Lift/Tower construction, and a self-application
level (Lω) in which the theory is applied to itself.

## Status

**v1.0.0-rc6** — release candidate. The projection-axiom basis, the WF/NWF duality, and the
categorical self-structure are audited for internal consistency (cross-references, labelling,
axiom-count, and proof rigor). rc6 applies CRPT to its own specification: the new
Self-Sectioning theory (Lω.8) reads the spec as a pure-WF CRPT model whose sections are
fibers of the Source-anchor projection, with boundary soundness decided by the theory's own
horizon predicates and reprise sections emptied by `F=∅`; the section set is re-drawn
accordingly (new topology-interface section L1.7; L4.8 retired; L5.5's category laws proved;
Lift-sibling criteria stated), labels are normalized to the fiber structure, every
cross-reference is a validated hyperlink, and a final correctness audit supplied all missing
proofs, sources, and synopses. rc4 derived the observation labelling from PA-Prod, restated
PA-Reach as its meaning with realization theorems, and resolved the two-mode question. rc3
and rc2 established the labelled bisimilarity, regime-aware equivalences, rendering, and the
model-neutral, legacy-free, engine-free presentation.

## Reading order

Start with the front matter, then the levels in order:

1. [Preface](CRPT_OMEGA_TOWER_PREFACE.md) — informal orientation
2. [Reading Guide](CRPT_OMEGA_TOWER_READING_GUIDE.md) — suggested paths by background
3. [Index](CRPT_OMEGA_TOWER_INDEX.md) · [Global Map](CRPT_OMEGA_TOWER_GLOBAL_MAP.md) · [Common Pitfalls](CRPT_OMEGA_TOWER_COMMON_PITFALLS.md)
4. Levels: [L0](CRPT_OMEGA_TOWER_L0.md) · [L1](CRPT_OMEGA_TOWER_L1.md) · [L2](CRPT_OMEGA_TOWER_L2.md) · [L3](CRPT_OMEGA_TOWER_L3.md) · [L4](CRPT_OMEGA_TOWER_L4.md) · [L5](CRPT_OMEGA_TOWER_L5.md) · [L6](CRPT_OMEGA_TOWER_L6.md) · [L7](CRPT_OMEGA_TOWER_L7.md) · [L8](CRPT_OMEGA_TOWER_L8.md) · [Lω](CRPT_OMEGA_TOWER_Lω.md)

## Reference

- [Theorem & Definition Index](CRPT_OMEGA_TOWER_THEOREM_INDEX.md) — every labelled item by level, with tags
- [Definitions Index](CRPT_OMEGA_TOWER_DEFINITIONS_INDEX.md)
- [Release Notes](CRPT_OMEGA_TOWER_RELEASE_NOTES.md)

## Conventions

Every formal item carries a stable label `L⟨level⟩.⟨section⟩.⟨kind⟩⟨n⟩` (e.g. `L1.2.Ax1`,
`L3.3.T9`) and a short tag (e.g. `` `PA-WN` ``, `` `WF-NWF-Dual` ``). Cross-references cite
both, as `` `Tag` (Label) ``, and every cross-reference is a **hyperlink** to the cited
construct's subsection (projection axioms are cited without backticks, `PA-X (Label)`,
likewise hyperlinked). Labels are placed by the fiber discipline of [`Self-Sect` (Lω.8.T1)](CRPT_OMEGA_TOWER_Lω.md#sections-are-fibers):
a construct lives in the section of its primary Source anchor, and the section map
(CRPT_OMEGA_TOWER_SECTION_MAP.md) records the resulting census.
