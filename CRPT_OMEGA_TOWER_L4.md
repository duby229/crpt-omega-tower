# L4 — Observer, Gateway, Valuation, Duality, Self-Projection, and Perturbation

## L4.1 — The Observer Triple

*Purpose.* Observer Triple. This section defines the observer triple 𝒪_M = (O_M, Gate_M, the orbit signature) — the formal characterisation of M's observability architecture. The observer is not an external agent; it is a derived structure that reads off properties already determined by the substrate and horizon predicates.*


**Remark L4.1.R3 (Coalgebra Foundation).** In coalgebra, an **observable** on a system is a function that extracts behavioral invariants
from computation. The observer triple 𝒪 = (PV, H, D) is a three-component **coalgebraic observable** 
that characterizes the behavioral essence of any element's orbit under ρ_M. It combines 
trajectory weighting, structural classification, and regime membership into a unified behavioral signature.

### Connection to PA-Prod Observable
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Remark** | L4.1.R1 | `PA-Prod-Conn` |  | **Novel** |
**Synopsis:** The Observable(y) predicate used in PA-Prod is the existential shadow of the path-valuation (PV) observable: PA-Prod's Observable Contract (OC-1/OC-2) guarantees every non-fixpoint ρ_M-step carries non-zero trajectory weight, so the behavioral signature PV(orbit(x)) is well-defined on all orbits in both ↓_M and ∞_M.

**Source:** CRPT; from PA-Prod (L1.2.Ax6).

The boolean predicate Observable(y)
used in Axiom `PA-Prod` (L1.2.Ax6) is the *existential shadow* of the PV component defined
below. PA-Prod's Observable Contract (OC-1, OC-2) guarantees that every non-fixpoint
ρ_M-step carries non-zero trajectory weight, so the PV trajectory observable
PV(orbit(x)) = ∏ w(xᵢ →_ρ xᵢ₊₁) never accumulates a zero factor at non-fixpoint
steps. This ensures the behavioral signature is well-defined for all orbits in both
↓_M and ∞_M. The model-specific Observable predicate (instantiated per OC) provides
the semantic grounding: what counts as "non-trivial content" varies by model, but
the structural guarantee — no silent divergence, no degenerate trajectory weights —
is universal.

### Coalgebraic Observable / Behavioral Functor
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L4.1.D1 | `Behav-F` |  | **Imported** |
**Synopsis:** The behavioral functor maps each CRPT model to its observer triple and maps each homomorphism to the corresponding map between observer triples. It is the categorical formalization of the claim that the observer architecture is a functor-level construct — not just a per-model definition but a transformation that commutes with model homomorphisms.

**Source:** Rutten [2000] *Universal coalgebra* — coalgebraic observable / behavioural functor.

A **coalgebraic observable** on model M is a natural transformation:
```
𝒪 : 𝒰_M ⟶ 𝑶_M
```
where 𝑶_M is a **behavioral space** (product of observables) encoding the essential information 
about M's orbits. The observer triple's three components realize this at the syntactic level.

### Path Valuation (Trajectory Observable)

### Path Valuation / Weighted Trajectory Observable
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L4.1.D2 | `PV-Obs` |  | **Reframed** |
**Synopsis:** The point-value observer assigns a numerical observable value to each element based solely on its current projection-orbit position: the canonical form, derivation height, and horizon profile at that point. It is the simplest observer type — it sees only the element itself, not its history or context.

**Source:** Eilenberg [1974]; Droste, Kuich & Vogler [2009] — weighted path / semiring valuation, reframed as the point-value projection observable.

For a reduction path π = (x₀, x₁, ..., xₙ) with xᵢ the reduction relation xᵢ₊₁:
```
PV(π) := ∏ᵢ₌₀^{n-1} w(xᵢ →_ρ xᵢ₊₁) ∈ V [Behavioral Valuation / Weighted Signature]
```
where w : →_ρ → V is a **behavioral weight** (step-weighting function) valued in a semiring V, 
and ∏ is the semiring product. PV is the **trajectory observable**: the weighted accumulation 
of observable events (reduction steps) along the orbit.

**Etymology & Standard Name.** 
- **Category Theory / Coalgebra:** This is a *behavioral predicate* in the coalgebraic sense 
 (Rutten [2000] L1.2: observables extract observable properties from a system state).
- **Formal Language Theory:** PV is a *path semiring valuation* or *weighted path function* 
 (Eilenberg [1974]; Droste, Kuich & Vogler [2009]): standard in weighted automata theory.
- **Process Algebra:** PV is a *weighted behavioral trace* (Milner [1980] §2: traces are 
 observable behavior sequences).

The interpretation depends on context: 
- In unweighted form (w ≡ 1), PV counts the trajectory length.
- With weights (e.g., cost, probability), PV accumulates behavioral cost / likelihood.

### Horizon Classifier (Structural Observable)

### Horizon Classifier / Structural Observable
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L4.1.D3 | `HC-Obs` |  | **Novel** |
**Synopsis:** The horizon-constrained observer is a point-value observer that is additionally constrained by the horizon profile: its output changes discontinuously at the H_O boundary (depth 1) and at H_S transitions. This models observers that react to structural branching.

**Source:** CRPT; from `Bool-Pred` (L3.2.D2) + `6-Part` (L3.2.T1).

The function:
```
H : μT_{ρ,M} → {A, B, C, D, E, F}
```
assigns each element its **structural observable class label** from the six-class partition (L3.2).

**H captures:** For each x ∈ ↓_M, the observable answers three structural questions:
1. Is x a fixpoint? (Q1 → Class in {A,B,C} vs {M,E,F})
2. Is ρ_M(x) ramified (multiple preimages)? (Q2: H_S(x) → Distinguishes {A,M} from {B,C,E,F})
3. Are preimages signature-indistinguishable? (Q3: H_I(x) → Distinguishes {B,E} from {C,F})

**Interpretation - Coalgebraic Structural Predicate.** 
H is a **structural observable** that classifies behavioral position (De Nicola & Hennessy [1984]): 
where does x sit in the abstraction landscape? Is it already abstracted (fixpoint)? Is it 
at a non-injective collapse point? Is the collapse ambiguous (indistinguishable)?

### Regime Discriminator (Persistence Observable)

### Regime Discriminator / Persistence Observable
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L4.1.D4 | `RD-Obs` |  | **Novel** |
**Synopsis:** The regime-dependent observer uses different observation strategies for convergent and persistent elements: induction-based observation for ↓_M elements and coinduction-based observation for ∞_M elements. This is the canonical CRPT observer, implementing the native regime stratification at the observational level.

**Source:** CRPT; from the regime partition (`Reg-Strat` L2.2.D3).

The function:
```
D : 𝒰_M → {WF, NWF} 
D(x) := { WF if x ∈ μT_{ρ,M}, [Convergent/Well-Founded behavior]
 { NWF if x ∈ νT_{ρ,M} [Persistent/Non-Well-Founded behavior]
```

**D captures:** The **regime membership observable** — the fundamental binary classifier 
of long-term orbital behavior: does the orbit eventually stabilize (WF), or persist indefinitely (NWF)?

**Interpretation - Coalgebraic Behavioral Discriminant.**
D is a **behavioral discriminant** in the sense of Park [1981] and Milner [1980]: it classifies 
which coinductive (persistent) or well-founded (convergent) operational semantics governs the element. 
In symbolic dynamics (Katok & Hasselblatt [1995]), this distinguishes ultimately periodic orbits (WF) 
from aperiodic ones (NWF).

### The Observer Triple as Unified Observable

### Coalgebraic Observable Triple
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L4.1.D5 | `Obs-Triple` | | **Novel** |
**Synopsis:** The observer triple 𝒪_M = (O_M, Gate_M, the orbit signature) is a formal characterisation of the observability structure inherent in model M. It is not an external measurement device — it reveals the model's own internal observability architecture. O_M specifies which elements are observable; Gate_M controls access between regimes; the orbit signature assigns comparable signatures to observable elements. Together they determine which elements can be distinguished by any query in the query signature.

**Source:** CRPT; from `PV-Obs` (L4.1.D2) + `HC-Obs` (L4.1.D3) + `RD-Obs` (L4.1.D4).


The **observer triple** (formally,
the **coalgebraic observable**) is the unified behavioral signature:
```
𝒪 : 𝒰_M → (V × {A,B,C,D,E,F} × {WF, NWF})
𝒪(x) := (PV(orbit(x)), H(x), D(x))
```

Three components:
1. **PV(x)** — Weighted trajectory accumulation (behavioral valuation)
2. **H(x)** — Horizon structural class (position in abstraction landscape) 
3. **D(x)** — Regime membership (convergent vs persistent)

**Semantic Equivalence.** The observer factors through the unified semantic domain `Sem` (L3.3.D9):
- For x, y ∈ ↓_M: x ≃_M y (`≃_M` (L2.5.D2)) ⟹ 𝒪(x) = 𝒪(y)
- For x, y ∈ ∞_M: x ≃∞ y (`≃∞` (L3.3.D7)) ⟹ 𝒪(x) ≃_𝒪 𝒪(y) (see `AOI1-BisInv` (L6.1.T1))

The observer is constant on ≃_M classes in ↓_M and on ≃∞ classes in ∞_M;
it separates elements only up to their regime-specific orbit equivalence.

### Coalgebraic Observable is Fully Derived / Constructible
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L4.1.T1 | `Obs-Const` | | **Novel** |
**Synopsis:** The observer triple 𝒪_M = (PV, H, D) is fully derived from prior definitions with no new axioms: PV from the path valuation (L4.3), H from the six-class horizon partition (L3.2), D from the regime partition (L2.2). The observer architecture is a consequence of the substrate, not an independent postulate.

**Source:** CRPT; from `Obs-Triple` (L4.1.D5) + PA-Prod (L1.2.Ax6).

The observer triple 𝒪 = (PV, H, D) is constructible from prior definitions without any new axioms:

*Proof.* 
- **PV Component:** Requires only a weighting function w : →_ρ → V (which may be the constant 
 function 1 in the unweighted case). Defined on finite trajectories in μT_{ρ,M} via `PV1` (L4.3.T1) (WF), 
 or limiting trajectories in νT_{ρ,M} via `PV2` (L4.3.T2) (NWF). ✓
- **H Component:** Defined from H_S, H_I, derivation height via the six-class partition (L3.2). ✓ 
- **D Component:** Defined from the regime partition μT_{ρ,M} ∐ νT_{ρ,M} (L2.2, `Part` (L2.2.T3)). ✓
All three components are functions defined on previously established structures. No new axioms. ✓ ∎

### Coalgebraic Terminology & Origins
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Remark** | L4.1.R2 | `Coal-Term` |  | **Reframed** |
**Synopsis:** This remark explains the three alternative names for the observer triple and why 'observer triple' is preferred. 'Orbit characterisation triple' emphasises the orbit-classification function. 'Behavioral signature' emphasises the behavioral identification role. 'Observer triple' is preferred because it captures the epistemological role: it represents what can be known about an element by a projection-based observer.

Rutten [2000] Universal coalgebra; De Nicola & Hennessy [1984] Testing equivalences for processes

The name "observer triple" originates from De Nicola & Hennessy [1984] **observational congruence** 
in process algebra: an external observer interacting with a system can only distinguish systems 
by what it can observe. The formal machinery now comes from coalgebra (Rutten [2000] Def (Projection Operator on (𝒰_M,the reduction relation), 
Jacobs [2016] L2.3): an observable is a map from system states to behavioral spaces. Here, the observer 
triple is the three-component observable that fully characterizes behavior under abstraction.

Alternative terminology (all equivalent):
- **Orbit Characterisation Triple** — emphasizes classification of abstraction orbits
- **Behavioral Signature** — emphasizes behavioral identification 
- **Coalgebraic Signature Functor** — emphasizes the category-theoretic role
- **Observable Triple** (formal name used below)

### Discernibility: Observer Triple

| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Remark** | L4.1.R4 | `Disc-Obs` | | **Novel** |
**Synopsis:** Reading the observer triple as a discernibility extractor.

**Source:** CRPT; from `Obs-Triple` (L4.1.D5).

The observer triple 𝒪 extracts the
**maximally discernible information** from an element's orbit: trajectory weight (PV),
structural position (H), and regime membership (M). Two elements with identical 𝒪
are **observationally indiscernible** — no observer with access to these three
components can distinguish them. Conversely, elements with different 𝒪 values are
guaranteed discernible. The observer triple is thus the **minimal sufficient
statistic** for CRPT-style discernibility.

---

## L4.2 — Regime Reachability: Gateway Structure

*Purpose.* Gateway and Regime Reachability. This section defines the gateway predicate GW(x) identifying elements that serve as passage points between ↓_M and ∞_M, and proves the regime-connectivity theorem: under the Gateway Reachability condition, every element in ∞_M is reachable from ↓_M via a gateway.*


This section is the principal place the structural relation →_σ is used. The Gateway
construction requires the enriched substrate (𝒰, →_ρ, →_σ, 𝒯).

### Gateway
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L4.2.D1 | `GW` | GW(x) | **Novel** |
**Synopsis:** The gateway GW(x) predicate identifies elements that serve as passage points between the convergent regime ↓_M and the persistent regime ∞_M. Gateway elements are observable from both sides of the regime boundary. They are critical for the regime-connectivity theorem: without gateways, the two regimes would be completely isolated from each other under observation.

**Source:** CRPT; from the regime partition (`Reg-Strat` L2.2.D3) + `Obs-Triple` (L4.1.D5).


x ∈ μT_{ρ,M} is a *gateway* if:
```
∃y ∈ νT_{ρ,M} : x →_σ y
```
x has a →_σ-step to a persistent element.

**Gateway Reachability (GR).** A model satisfies *Gateway Reachability* if every
non-fixpoint convergent element has a →_σ-path to some persistent element:
```
∀x ∈ μT_{ρ,M} \ Fix(ρ_M) : ∃y ∈ νT_{ρ,M} : x →_σ* y
```
GR is a model-level structural property of →_σ, not one of the PA-* axioms and not a
consequence of them. It holds vacuously when ∞_M = ∅.

### Gateway Reachability vs. PA-Reach

| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Remark** | L4.2.R1 | `GR-vs-Reach` | | **Novel** |
**Synopsis:** Gateway reachability (a →_σ property) versus PA-Reach (a ρ_M property).

**Source:** CRPT; from `GW` (L4.2.D1) + PA-Reach (L1.3.Ax2).

GR is a →_σ-connectivity property
and is distinct from PA-Reach. PA-Reach (L1.3) is a projection property: it asserts
that the orbit signature sig_M stabilizes under ρ_M-iteration on ∞_M; it constrains
ρ_M on the persistent regime and says nothing about cross-regime connectivity.
Cross-regime reachability necessarily uses →_σ rather than →_ρ, because →_ρ maps
μT_{ρ,M} into μT_{ρ,M} (`↓-Closed` (L2.2.T1)); this is why GR is stated over →_σ.

### Regime Connectedness — RT
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L4.2.T1 | `Reg-Conn` | | **Novel** |
**Synopsis:** The regime connectivity theorem: under Gateway Reachability, every persistent element is reachable from some convergent element via a gateway. The two regimes are not completely separate worlds — there is always a →_σ-path from the well-founded side to any persistent element. This is a structural property of →_σ, independent of PA-Reach (which constrains ρ_M on ∞_M).

**Source:** CRPT; from `GW` (L4.2.D1) + PA-Reach (L1.3.Ax2).

Under Gateway Reachability, μT_{ρ,M} and νT_{ρ,M} are
→_σ*-connected: for every x ∈ μT_{ρ,M} \ Fix(ρ_M), there is a →_σ*-path from x to νT_{ρ,M}.

*Proof.* Direct from the statement of Gateway Reachability and `RT*` (L1.1.D4). ∎

---

## L4.3 — Projection Valuation

*Purpose.* Projection Valuation. This section assigns a numerical valuation to each element based on derivation height and horizon predicates, and proves it is invariant under ≃_M. The projection valuation is the tool for proving observer consistency across the six-class partition.*


### Value Semiring

### Value Semiring V
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L4.3.D1 | `VS` | V | **Imported** |
**Synopsis:** The value semiring V = (V, +, ·, 0, 1) is the coefficient domain for the projection valuation. Standard instances: (ℝ₊, +, ×, 0, 1) for real-valued weights, (ℕ, +, ×, 0, 1) for counting, (𝔹, ∨, ∧, ⊥, ⊤) for Boolean reachability. The projection valuation is parametric in the choice of semiring.

Kuich & Salomaa [1986]

A *value semiring* is a tuple
V = (V, +, ·, 0, 1) where (V, +, 0) is a commutative monoid, (V, ·, 1) is a monoid,
· distributes over +, and 0 · v = v · 0 = 0 for all v ∈ V. Standard examples:
(ℝ₊, +, ×, 0, 1); (ℕ, +, ×, 0, 1); (B, ∨, ∧, ⊥, ⊤) the Boolean semiring.

### Step Weighting
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L4.3.D2 | `Step-W` | w(x, y) | **Imported** |
**Synopsis:** The step weighting function w assigns a semiring value to each single reduction step x →_ρ y. Multiplicative composition of step weights along a reduction path gives the weight of the entire path. The projection valuation accumulates these weights using the semiring multiplication.

Kuich & Salomaa [1986]

A *step weighting* is a function
w : →_ρ → V assigning a value to each reduction step.

### Finite Reduction Histories
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L4.3.D3 | `FRH` |  | **Imported** |
**Synopsis:** The set of finite reduction histories ℋ_finite(x) from x is the tree of all finite reduction paths starting at x. Each node of the tree is a reduction step; each leaf is either a normal form or a maximal finite prefix. The projection valuation is defined by summing over all paths in this tree.

Baader & Nipkow [1998]; Kuich & Salomaa [1986]

The set of *finite reduction
histories from x* is:
```
ℋ_finite(x) := { h = (x₀ →_ρ x₁ →_ρ ··· →_ρ xₙ) | x₀ = x, n ≥ 0 }
```
The empty history ε_x has x₀ = x and n = 0.

### Projection Valuation — WF
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L4.3.D4 | `PV-WF` |  | **Reframed** |
**Synopsis:** The finite reduction history set ℋ_finite(x) and its path enumeration: paths in ℋ_finite(x) are finite sequences x = x₀ →_ρ x₁ →_ρ ... →_ρ xₙ. The empty path ε_x (length 0) has weight 1 (the semiring unit). The projection valuation is the sum of weights of all paths.

Kuich & Salomaa [1986]

For x ∈ μT_{ρ,M}:
```
PV : ℋ_finite(x) → V
PV(ε_x) := 1
PV(h ∘ (xₙ →_ρ xₙ₊₁)) := PV(h) · w(xₙ →_ρ xₙ₊₁)
```
PV is the *multiplicative accumulation of step-weights* along the history.

### WF Projection Valuation

### PV-1: WF Existence
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L4.3.T1 | `PV1` | | **Novel** |
**Synopsis:** The Projection Valuation Theorem: for any semiring V and step-weighting function w, the projection valuation PV_M assigns to each element x ∈ ↓_M the sum PV_M(x) = Σ_{h ∈ ℋ_finite(x)} prod_i(w(hᵢ)) over all finite reduction histories from x. This valuation is well-defined (the sum is finite under PA-WN), invariant under ≃_M (observationally equivalent elements receive equal valuations), and strictly monotone under the projection operator.

**Source:** CRPT; from PA-WN (L1.2.Ax1) + `≃_M` (L2.5.D2) + semiring valuations (Kuich & Salomaa [1986]).

Under PA-WN: PV is well-defined and
satisfies **(PV-mult):** PV(h₁ ∘ h₂) = PV(h₁) · PV(h₂) for all composable h₁, h₂.

*Proof.*
Step 1 (Finiteness): By PA-WN, every orbit from x terminates; every history has
length ≤ d_M(x). ℋ_finite(x) is a finite tree. ✓

Step 2 (Well-definedness): Construction by induction on |h|. Base: PV(ε_x) = 1 ∈ V.
Step: PV(h ∘ step) = PV(h) · w(step), using the given w. ✓

Step 3 (PV-mult): PV(h₁ ∘ h₂) = ∏ w-values along h₁ then h₂ = PV(h₁) · PV(h₂)
by associativity of · in V. ✓ ∎

### PV-1C: Orbit Valuation
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Corollary** | L4.3.C1 | `PV1C` |  | **Novel** |
**Synopsis:** The projection valuation corollary: the projection valuation PV_M is the unique numerical function on 𝒰_M that is (1) invariant under ≃_M, (2) strictly monotone under the projection operator on ↓_M, and (3) constant on persistent orbits after stabilization. These three conditions characterise it up to rescaling.

**Source:** CRPT; from `PV1` (L4.3.T1) + `≃_M` (L2.5.D2).

Under PA-WN and C1–C2
(`ρ_M` (L2.1.D1) (ρ_M deterministic): define PV_c : μT_{ρ,M} → V by
PV_c(x) := PV(x, ρ_M(x), ..., CFix(ρ_M)(x)). PV_c is well-defined and
PV_c(x) = ∏ᵢ w(ρ_M^i(x) →_ρ ρ_M^{i+1}(x)) for i = 0, ..., d_M(x)-1.

*Proof.* Since ρ_M is a function (C1–C2), the ρ_M-orbit of x is the unique
sequence x = ρ_M^0(x), ρ_M^1(x), ..., ρ_M^{d_M(x)}(x) = CFix(ρ_M)(x). Under PA-WN
this orbit is finite, hence it is a single history in ℋ_finite(x). PV_c(x) is PV
applied to this history:
PV_c(x) = PV(ε_x) · w(x →_ρ ρ_M(x)) · w(ρ_M(x) →_ρ ρ_M^2(x)) · ··· · w(ρ_M^{d_M(x)-1}(x) →_ρ CFix(ρ_M)(x))
= ∏ᵢ w(ρ_M^i(x) →_ρ ρ_M^{i+1}(x)). Well-definedness follows from C1–C2 (single-step
edges along the ρ_M-orbit) and finiteness by PA-WN. ✓ ∎

### NWF Projection Valuation

### Infinite Reduction Histories from x
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L4.3.D5 | `IRH-x` |  | **Imported** |
**Synopsis:** The persistent regime projection valuation extends the finite-history valuation to elements of ∞_M using the scope conditions and the coinductive structure from PA-CoInd. For SC-1 elements, the persistent valuation converges to a limit determined by the periodic orbit's accumulated weight.

Baader & Nipkow [1998]

For x ∈ νT_{ρ,M}:
```
ℋ_infinite(x) := { h : ℕ → 𝒰_M | h(0) = x, ∀n : h(n) →_ρ h(n+1) }
```

### PV∞ — NWF Valuation
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L4.3.D6 | `PV∞` |  | **Novel** |
**Synopsis:** The infinite projection valuation PV∞(h) := lim_{n→∞} PV(h|_n) extends the projection valuation to infinite reduction histories by taking the limit of finite-prefix valuations in a topologised semiring.

**Source:** CRPT; from `PV-Obs` (L4.1.D2); topological extension.

For x ∈ νT_{ρ,M} with SC-1/2/3, and a
semiring V with a topology (metric or order) under which limits are defined:
```
PV∞(h) := lim_{n→∞} PV(h|_n)
```
where h|_n is the finite prefix of h of length n.

### PV-2: NWF Existence
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L4.3.T2 | `PV2` |  | **Novel** |
**Synopsis:** The orbit valuation PV_{orbit}(x) = Σ_{h ∈ ℋ_finite(x)} PV(h) is the total weight of all finite reduction histories from x. Under PA-WN, this sum is finite (the tree ℋ_finite(x) is finite). The orbit valuation is the projection valuation's primary output.

**Source:** CRPT; from `PV∞` (L4.3.D6) + PA-NWF (L1.2.Ax4) + PA-Prod (L1.2.Ax6).

Under PA-NWF + PA-Prod + SC-1/2/3:
PV∞(h) exists and is well-defined for all h ∈ ℋ_infinite(x).

*Proof.* By PA-Prod, each h(n) ∈ ℋ_infinite(x) is observable. The sequence
(PV(h|_n))_{n∈ℕ} is determined by the step-weights along h. Under SC-2/3, the
orbit is eventually periodic; the sequence PV(h|_n) stabilises or has a
well-defined limiting product under the semiring's topology. ✓ ∎

### PV Duality — DU-3
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L4.3.T3 | `PV-Dual` |  | **Novel** |
**Synopsis:** The projection valuation duality theorem: the orbit valuation PV_M(x) and the fixpoint valuation PV_M^{fix}(f) = w(f) satisfy PV_M(x) = PV_M^{fix}(CNF_M(x)) · w-path(x, CNF_M(x)), where w-path is the accumulated weight of the canonical path from x to its fixpoint. Valuation of an element factors through the valuation of its canonical form.

**Source:** CRPT; from `PV∞` (L4.3.D6) + `Rec-Proj` (L2.1.D4).

PV∞ = lim PV: for each h ∈ ℋ_infinite(x),
PV∞(h) = lim_{n→∞} PV(h|_n).

*Proof.* By `PV∞` (L4.3.D6). The same structural valuation rules apply to finite and
infinite paths; the distinction is the model. Under PA-Prod, the limit exists. ∎

---

## L4.4 — Duality Theorems

*Purpose.* Five Duality Theorems. This section establishes five duality results relating the convergent and persistent regimes, the abstraction and concretisation maps, and the horizon predicates. Duality is the formal expression of the complementarity between well-founded structure and coinductive structure in CRPT.*


### Comparison, not joint assumption
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Remark** | L4.4.R1 | `WN-NWF-Comp` |  | **Novel** |
**Synopsis:** PA-WN and PA-NWF are mutually exclusive only when stated as global axioms over an undifferentiated substrate; in regime-stratified models they coexist by scope, PA-WN ranging over the convergent regime ↓_M and PA-NWF over the persistent regime ∞_M.

**Source:** CRPT; from PA-WN (L1.2.Ax1) + PA-NWF (L1.2.Ax4); background in WF rewriting (Baader & Nipkow [1998]) and non-well-founded sets (Aczel [1988]).

PA-WN and PA-NWF are **mutually exclusive when both are stated as global axioms
over an undifferentiated substrate without regime stratification.** That is:
- In pure WF models (∞_M = ∅): PA-WN holds globally, PA-NWF is false.
- In pure NWF models (↓_M = ∅): PA-NWF holds globally, PA-WN is false.
In either pure profile, the two axioms are incompatible as universal quantifications
over 𝒰_M.

**Critical Qualification: Native Stratified Models (both ↓_M ≠ ∅ and ∞_M ≠ ∅).**
In native stratified models, PA-WN and PA-NWF are **not in conflict**. They coexist
via regime-scoped interpretation: PA-WN is interpreted as ∀x ∈ ↓_M (convergent regime),
and PA-NWF is interpreted as ∀x ∈ ∞_M (persistent regime). Since ↓_M and ∞_M
are disjoint by definition, no element is asked to satisfy both axioms. This is not
an exception to mutual exclusivity; it is a change of logical scope. The duality
theorems (DU-1 through DU-3 below) apply uniformly across all model profiles; native
models automatically receive regime-stratified interpretations by this mechanism.

### ρ-Predecessor Operator
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L4.4.D1 | `Pre_ρ-14` | Pre_ρ(X) | **Imported** |
**Synopsis:** The ρ-predecessor operator Pre_ρ(X) := { x ∈ 𝒰_M | ρ_M(x) ∈ X } collects the elements whose one-step projection image lands in X. It is the projection-operator instance of the standard predecessor transformer.

**Source:** Cousot & Cousot [1977] POPL — predecessor (pre-) operator.

For X ⊆ 𝒰_M define:
```
Pre_ρ(X) := { x ∈ 𝒰_M | ρ_M(x) ∈ X }.
```

### Regime Fixpoint Operators
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L4.4.D2 | `Reg-FPO` |  | **Reframed** |
**Synopsis:** The regime fixpoint operators T_conv(X) := Fix(ρ_M) ∪ Pre_ρ(X) and T_pers(X) := (𝒰_M \ Fix(ρ_M)) ∩ Pre_ρ(X) are monotone transformers on (𝒫(𝒰_M), ⊆) whose least and greatest fixpoints reconstruct the convergent and persistent regimes.

**Source:** Tarski [1955] — lattice fixpoint operators, applied to the regime partition.

On the complete lattice
(𝒫(𝒰_M), ⊆), define:
```
T_conv(X) := Fix(ρ_M) ∪ Pre_ρ(X),
T_pers(X) := (𝒰_M \ Fix(ρ_M)) ∩ Pre_ρ(X).
```

### Monotonicity of T_conv and T_pers
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Lemma** | L4.4.L1 | `T-Mono` |  | **Imported** |
**Synopsis:** Both regime fixpoint operators T_conv and T_pers are monotone on (𝒫(𝒰_M), ⊆), so by Knaster–Tarski each has well-defined least and greatest fixpoints — the precondition for the regime fixpoint construction.

**Source:** Tarski [1955] — monotonicity (hypothesis of the Knaster–Tarski theorem).

T_conv and T_pers are monotone.

*Proof.* If X ⊆ Y, then Pre_ρ(X) ⊆ Pre_ρ(Y). Union/intersection with fixed sets
preserves inclusion. Hence T_conv(X) ⊆ T_conv(Y) and T_pers(X) ⊆ T_pers(Y). ∎

### Regimes as Least/Greatest Fixpoints
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L4.4.T1 | `Reg-FP` |  | **Reframed** |
**Synopsis:** Regimes as fixpoints: the convergent regime ↓_M is the least fixpoint μT_conv and the persistent regime ∞_M is the greatest fixpoint νT_pers of the regime operators. This gives the regime partition an order-theoretic (μ/ν) characterization.

**Source:** Tarski [1955] — least/greatest fixpoints (μ/ν), here characterizing the regimes.

The regime partition is
exactly the μ/ν decomposition:
```
↓_M = μT_{ρ,M}, ∞_M = νT_{ρ,M}.
```

*Proof.*
Let B := ↓_M = {μ-regime element condition}

First show B is a fixed point of T_conv.
- If x ∈ B, either x ∈ Fix(ρ_M), or x ∉ Fix(ρ_M) and ρ_M(x) ∈ B (drop one step from
 a witnessing orbit). So x ∈ T_conv(B).
- If x ∈ T_conv(B), then either x ∈ Fix(ρ_M) (hence x ∈ B), or ρ_M(x) ∈ B; in the
 latter case prepend one ρ-step to a witness for ρ_M(x) ∈ B, giving x ∈ B.
Thus T_conv(B)=B.

Now show leastness. Let X ⊆ 𝒰_M with T_conv(X) ⊆ X (pre-fixed point). Then
Fix(ρ_M) ⊆ X. If ρ_M^n(x) ∈ Fix(ρ_M), repeated use of Pre_ρ(X) ⊆ X gives
x ∈ X by induction on n. Hence B ⊆ X. Therefore B = μT_conv.

Let O := ∞_M = {ν-regime element condition}

First show O is a fixed point of T_pers.
- If x ∈ O, then x ∉ Fix(ρ_M) and ρ_M(x) ∈ O, so x ∈ T_pers(O).
- If x ∈ T_pers(O), then x ∉ Fix(ρ_M) and ρ_M(x) ∈ O. Hence all iterates of x are
 outside Fix(ρ_M), so x ∈ O.
Thus T_pers(O)=O.

Now show greatestness. Let X ⊆ 𝒰_M with X ⊆ T_pers(X) (post-fixed point). Then for
every x ∈ X: x ∉ Fix(ρ_M) and ρ_M(x) ∈ X. Iterating yields ρ_M^n(x) ∈ X ⊆ 𝒰_M\Fix(ρ_M)
for all n, so x ∈ O. Hence X ⊆ O. Therefore O = νT_pers. ∎

### RP-1 / CP-1 Convention
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L4.4.D3 | `RP-CP1` |  | **Reframed** |
**Synopsis:** The RP-1/CP-1 conventions name the two fixpoint disciplines of projection reasoning: RP-1 is convergent-regime least-fixpoint reasoning through μT_conv, and CP-1 is persistent-regime greatest-fixpoint reasoning through νT_pers.

**Source:** Cousot & Cousot [1977] POPL — μ/ν fixpoint-reasoning conventions.

`RP-1` denotes WF least-fixpoint projection reasoning on (𝒫(𝒰_M), ⊆) through μT_conv. 
`CP-1` denotes NWF greatest-fixpoint projection reasoning on (𝒫(𝒰_M), ⊆) through νT_pers.

### RP-2 / CP-2 Convention
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L4.4.D4 | `RP-CP2` |  | **Reframed** |
**Synopsis:** The RP-2/CP-2 conventions name the two proof principles: RP-2 is induction on derivation height over μT_{ρ,M}, and CP-2 is co-induction via Park's Lemma on T_pers (P ⊆ T_pers(P) ⟹ P ⊆ νT_pers).

**Source:** Cousot & Cousot [1977] POPL — induction/coinduction conventions; Park [1981] for the coinduction principle.

`RP-2` denotes induction on derivation height over μT_{ρ,M} (= μT_conv). 
`CP-2` denotes co-induction via Park's Lemma on T_pers: P ⊆ T_pers(P) ⟹ P ⊆ νT_pers.

### DU-1: Fixpoint Duality
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L4.4.T2 | `FP-Dual` |  | **Reframed** |
**Synopsis:** Fixpoint duality (DU-1): convergent-regime recursive projection builds least fixpoints μF, while persistent-regime co-recursive projection builds greatest fixpoints νF; the two are order-duals (smallest pre-fixpoint vs largest post-fixpoint) by Knaster–Tarski. WF reasoning is least-fixpoint reasoning; NWF reasoning is greatest-fixpoint reasoning.

**Source:** Tarski [1955], *A lattice-theoretical fixpoint theorem*; Cousot & Cousot [1977] POPL — μ/ν fixpoint duality.

In the convergent regime (PA-WN), recursive
projection constructs *least fixpoints* μF. In the persistent regime (PA-NWF + PA-CoInd),
co-recursive projection constructs *greatest fixpoints* νF. μF and νF are formally
dual: μF is the smallest pre-fixpoint; νF is the largest post-fixpoint.

*Proof.* By `Reg-FP` (L4.4.T1), ↓_M = μT_conv and ∞_M = νT_pers. By Knaster-Tarski, μ
and ν are order-dual fixed points on complete lattices for monotone operators. So
WF reasoning is least-fixpoint reasoning, and NWF reasoning is greatest-fixpoint
reasoning. ∎

### DU-2: Induction/Co-Induction Duality
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L4.4.T3 | `Ind-CoInd` |  | **Imported** |
**Synopsis:** Induction/co-induction duality (DU-2): well-founded induction over derivation height (RP-2) on the least fixpoint ↓_M and Park-style coinduction (CP-2) on the greatest fixpoint ∞_M are formally dual proof principles, by Knaster–Tarski on the complete lattice (𝒫(𝒰_M), ⊆).

**Source:** Knaster [1928]; Tarski [1955]; Park [1981] LNCS 104 — induction/coinduction duality.

RP-2 (induction) and
CP-2 (co-induction) are formally dual:

| Induction (RP-2) | Co-Induction (CP-2 / Park's Lemma) |
|:---:|:---:|
| Base Fix(ρ_M) + ρ-step closure ⟹ ∀x∈μT_{ρ,M}: P(x) | P ⊆ T_pers(P) ⟹ P ⊆ νT_{ρ,M} |
| Proves properties on the least regime fixpoint | Proves memberships in the greatest regime fixpoint |
| Minimum: builds up from base | Maximum: admits any consistent P |

*Proof.* RP-2: structural induction on d_M(x) ∈ ℕ (well-founded by `d-WFM` (L2.3.C1)).
CP-2: instantiate Axiom PA-CoInd with Φ := T_pers to obtain
P ⊆ T_pers(P) ⟹ P ⊆ νT_pers. The two principles are dual by Knaster-Tarski on
the complete lattice (𝒫(𝒰_M), ⊆). ∎

### DU-3: PV Duality
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L4.4.T4 | `PV-Dual-14` |  | **Novel** |
**Synopsis:** PV duality (DU-3): the WF path valuation PV (over finite histories) and the NWF limit valuation PV∞ (over infinite histories) are one construction at different granularities — PV∞(h) = lim_{n→∞} PV(h|_n). Finite and persistent valuation coincide in the limit.

**Source:** Kuich & Salomaa [1986], *Semirings, Automata and Languages*; Eilenberg [1974], *Automata, Languages and Machines* Vol. A — formal-power-series valuations.

PV∞ = lim PV (`PV-Dual` (L4.3.T3) above). The
WF path valuation PV (`PV1` (L4.3.T1)) and NWF limit valuation PV∞ (`PV2` (L4.3.T2)) are
the same construction applied to finite vs infinite histories.

*Proof.* `PV-Dual` (L4.3.T3) already establishes, for each admissible infinite history
h ∈ ℋ_infinite(x), that PV∞(h) is the limit of valuations of finite prefixes:
PV∞(h) = lim_{n→∞} PV(h|_n). The WF valuation PV of `PV1` (L4.3.T1) is exactly the
same valuation functional applied to finite histories; the NWF valuation PV∞ of
`PV2` (L4.3.T2) is its limit extension along infinite histories under SC-1/2/3.
Hence WF and NWF valuation formalisms are one construction at different orbit
granularities (finite-prefix vs limit). Therefore PV∞ = lim PV. ∎

**Meta-Observation DU-4 (Axiom Family Symmetry).** The WF/NWF architecture pairs
WF theorem-layer canonicalization with NWF coinductive closure:
WF side {PA-WN, PA-Conf, PA-Fix, WF-Canon} and NWF side {PA-NWF, PA-CoInd, PA-Prod, PA-Bisim}
exhibit structural symmetry: PA-WN ↔ PA-NWF (termination/persistence),
PA-Conf ↔ PA-Bisim (unique result/bisimulation quotient), WF-Canon ↔ PA-CoInd
(least-fixpoint canonicalization/co-induction). This is a design observation,
not a provable proposition.

**Meta-Observation DU-5 (Regime-Independent Vocabulary).** The projection
vocabulary — ρ_M, derivation height, CNF/CNF∞, PV, horizon classification — is structurally
identical for convergent and persistent regimes. The sole structural difference is PA-WN vs PA-NWF.

---

## L4.5 — Projection Depth and Inversion Horizon

*Purpose.* Inversion Horizon and Canonical Period. This section introduces the inversion horizon (the boundary at which a projection orbit 'turns around'), the canonical period CPD for periodic persistent orbits, and the canonical inversion horizon CIH. These notions prepare the ground for the NWF-extended Lift* of L8.5.*


### PD-3: Depth Monotonicity
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Corollary** | L4.5.C1 | `PD3` |  | **Imported** |
**Synopsis:** Projection decrements derivation height by exactly one off the fixpoint set: for x ∈ μT_{ρ,M} \ Fix(ρ_M), d_M(ρ_M(x)) = d_M(x) − 1. Each projection step moves one rank closer to the canonical form.

**Source:** Baader & Nipkow [1998] — depth monotonicity; via `Depth-Dec` (L2.3.T2).

For x ∈ μT_{ρ,M} \ Fix(ρ_M):
d_M(ρ_M(x)) = d_M(x) − 1.

*Proof.* `Depth-Dec` (L2.3.T2). ∎

### PD-4: Orbit Non-Injectivity Beyond Horizon
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L4.5.T1 | `PD4` |  | **Novel** |
**Synopsis:** Orbit non-injectivity beyond the horizon: for j > d_M(x), ρ_M^j collapses x to its canonical fixpoint, so the j-step pre-image of x is exactly its NFC class NFC_M(CFix(ρ_M)(x)). Past the derivation-height horizon the projection is maximally non-injective — no inverse can separate elements of the same fiber.

**Source:** CRPT; from `CNF=CR` (L2.5.T2).

Under PA-WN + PA-Conf:
for j > d_M(x): {y ∈ μT_{ρ,M} | ρ_M^j(y) = ρ_M^j(x)} = NFC_M(CFix(ρ_M)(x)).

*Proof.* For j > d_M(x): ρ_M^j(x) = ρ_M^{j−d_M(x)}(CFix(ρ_M)(x)) = CFix(ρ_M)(x) (since
CFix(ρ_M)(x) ∈ Fix(ρ_M) and applying ρ_M to a fixpoint returns it unchanged).
Therefore {y | ρ_M^j(y) = CFix(ρ_M)(x)} = {y ∈ μT_{ρ,M} | CFix(ρ_M)(y) = CFix(ρ_M)(x)} =
NFC_M(CFix(ρ_M)(x)) (by `CNF=CR` (L2.5.T2): x ≃_M y iff CFix(ρ_M)(x) = CFix(ρ_M)(y)).
The preimage under ρ_M^j is the entire NFC class; no inverse can distinguish
elements within it. ∎

### IH-1: Inversion Horizon
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L4.5.T2 | `IH` |  | **Novel** |
**Synopsis:** The inversion horizon H(x) := d_M(x) is the depth beyond which ρ_M^j cannot invert x: for every j > H(x), x's entire NFC class maps to a single point. It marks where one-step invertibility is irrecoverably lost.

**Source:** CRPT; from `PD4` (L4.5.T1).

Under PA-WN + PA-Conf:
H(x) := d_M(x) is the inversion horizon of x ∈ μT_{ρ,M}. For j > H(x):
{y ∈ μT_{ρ,M} | ρ_M^j(y) = ρ_M^j(x)} = NFC_M(CFix(ρ_M)(x)).

*Proof.* `PD4` (L4.5.T1) with j > d_M(x). ∎

### IH-1.1
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Corollary** | L4.5.C2 | `IH1.1` |  | **Imported** |
**Synopsis:** The inversion horizon is always finite: H(x) = d_M(x) ∈ ℕ for every x ∈ μT_{ρ,M}, since derivation height is a finite natural number in the convergent regime.

**Source:** Baader & Nipkow [1998] — finite derivation height; via `d-WD` (L2.3.T1).

H(x) = d_M(x) ∈ ℕ for all x ∈ μT_{ρ,M}.

*Proof.* H(x) := d_M(x) by definition (`IH` (L4.5.T2)); d_M(x) ∈ ℕ by `d-WD` (L2.3.T1). ∎

### IH-1.2
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Corollary** | L4.5.C3 | `IH1.2` |  | **Novel** |
**Synopsis:** The structural horizon coincides with the one-step inversion ambiguity: H_S(x) = ⊤ iff x is not uniquely recoverable from ρ_M(x). The ramification locus is exactly where one-step projection loses injectivity.

**Source:** CRPT; from `H_S` (L3.1.D1); background in Baader & Nipkow [1998], Park [1981].

H_S(x) = ⊤ iff x is not uniquely recoverable from
ρ_M(x): the one-step inversion ambiguity is precisely the ramification locus.

*Proof.* H_S(x) = ⊤ iff |ρ_M⁻¹(ρ_M(x))| > 1 (`H_S` (L3.1.D1)) iff ∃y ≠ x with
ρ_M(y) = ρ_M(x) iff x cannot be uniquely recovered from ρ_M(x). ∎

### Co-Projection Depth CPD
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L4.5.D1 | `CPD` | CPD(x) | **Novel** |
**Synopsis:** The Canonical Period CPD(σ) is the minimal period of a periodic persistent orbit in orbit class σ. For SC-1 elements, CPD(σ) is the first p ≥ 1 such that ρ_M^p(x) ≃_M x for x in class σ. CPD generalises derivation height d_M to the persistent regime.

**Source:** CRPT; from `SC4-EP` (L3.3.T1) + `≃_M` (L2.5.D2).

For x ∈ νT_{ρ,M} satisfying SC-4,
let N(x) := min{N ∈ ℕ | ∃p ≥ 1 : ∀n ≥ N : [ρ_M^{n+p}(x)]_≈ = [ρ_M^n(x)]_≈} (the
**pre-period** of the quotient orbit, which exists by `SC4-EP` (L3.3.T1)). The *minimal period* is:
```
CPD(x) := min{p ≥ 1 | [ρ_M^{N(x)+p}(x)]_≈ = [ρ_M^{N(x)}(x)]_≈}
```
For Type P elements (SC-1), CPD(x) = 1 and N(x) coincides with the SC-1 stabilisation
index. For Type EP elements (SC-4 ∧ ¬SC-1), CPD(x) ≥ 2 (`OTC` (L6.2.D1)).

### CPD-1: Co-Projection Depth is Finite
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L4.5.T3 | `CPD-Fin` |  | **Novel** |
**Synopsis:** The canonical period is finite: under PA-NWF + PA-Bisim + SC-4, CPD(x) ∈ ℕ for every x in the persistent regime satisfying SC-4. The bisimulation-quotient orbit is eventually periodic with a finite minimal period.

**Source:** CRPT; from `CPD` (L4.5.D1) + PA-Bisim (L1.3.Ax1) + `SC-4-Def` (L3.3.D5).

Under PA-NWF + PA-Bisim + SC-4:
for all x ∈ νT_{ρ,M} satisfying SC-4, CPD(x) ∈ ℕ.

*Proof.* SC-4: |{[ρ_M^n(x)]_≈ | n ∈ ℕ}| < ∞ — finitely many bisimulation classes
are visited. The sequence ([ρ_M^n(x)]_≈)_{n∈ℕ} takes values in a finite set S.
By the pigeonhole principle there exist n₁ < n₂ with [ρ_M^{n₁}(x)]_≈ = [ρ_M^{n₂}(x)]_≈.
Let p = n₂ − n₁. PA-Bisim gives ρ̄_M([ρ_M^n(x)]_≈) = [ρ_M^{n+1}(x)]_≈ (the induced
map on S is well-defined and deterministic). Since [ρ_M^{n₁}(x)]_≈ = [ρ_M^{n₁+p}(x)]_≈
and the dynamics on S is deterministic: [ρ_M^{n₁+kp}(x)]_≈ = [ρ_M^{n₁}(x)]_≈ for
all k ≥ 0. The orbit on S is periodic. The minimum period p_min ≤ p is well-defined
and finite. N(x) exists in ℕ by `SC4-EP` (L3.3.T1) (eventual periodicity). Hence CPD(x) = p_min ∈ ℕ. ∎

### CIH-1: Co-Inversion Horizon
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L4.5.T4 | `CIH` |  | **Novel** |
**Synopsis:** The Canonical Inversion Horizon CIH(x) is the derivation height at which the orbit of x reaches its canonical inversion point. Elements with CIH(x) = 1 are at the boundary between the convergent and persistent regimes; those with larger CIH have a longer convergent prefix before entering their persistent cycle.

**Source:** CRPT; from `CPD` (L4.5.D1) + `SC4-EP` (L3.3.T1) + `CPD-Fin` (L4.5.T3).

Under PA-NWF + PA-Bisim + SC-4:
CIH(x) := N(x) + CPD(x) ∈ ℕ, and for all n ≥ CIH(x):
```
[ρ_M^{n+CPD(x)}(x)]_≈ = [ρ_M^n(x)]_≈
```
If additionally SC-1(x) holds (Type P, CPD(x) = 1), then for all n ≥ N(x):
```
[ρ_M^n(x)]_≈ = CNF∞_M(x)
```

*Proof.* CIH(x) ∈ ℕ: N(x) ∈ ℕ (`SC4-EP` (L3.3.T1), eventual periodicity), CPD(x) ∈ ℕ (`CPD-Fin` (L4.5.T3)). ✓

For n ≥ N(x): [ρ_M^{n+CPD(x)}(x)]_≈ = [ρ_M^n(x)]_≈ by periodicity of the orbit on
the bisimulation quotient (proven in `CPD-Fin` (L4.5.T3): the orbit on S is periodic with
minimal period CPD(x)). Since CIH(x) ≥ N(x), the claim holds for n ≥ CIH(x). ✓

If SC-1(x) holds, then CPD(x) = 1, so [ρ_M^n(x)]_≈ = [ρ_M^{N(x)}(x)]_≈ =: CNF∞_M(x)
for all n ≥ N(x) (`CNF∞-Def` (L3.3.D6)). ✓ ∎

---

## L4.6 — Self-Projection

*Purpose.* Self-Projection. This section proves that the observer triple 𝒪_M is a fixed point of the projection operator when ρ_M is applied to the observer's own outputs. The observer structure is self-consistent with the projection it observes.*


*Notation 16.0 (Fixpoint-Operator Convention for Projections).* In this section,
Fᵢ and Gᵢ denote monotone endofunctions on the complete lattice (𝒫(𝒰_M), ⊆).
Their least/greatest fixed points are written μFᵢ and νGᵢ. By `RP-CP1` (L4.4.D3),
WF projections are RP-1 (least-fixpoint based) and NWF projections are CP-1
(greatest-fixpoint based).

### SP-1: Closure
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L4.6.T1 | `SP1` |  | **Novel** |
**Synopsis:** The self-projection theorem: the observer triple 𝒪_M, when treated as an element of a suitable CRPT model of observer triples, is a fixed point of the projection operator on that model. The observer structure is self-consistent: observing the observer produces the same observer. This is the first instance of CRPT's self-referential closure, culminating in Lω.

**Source:** CRPT; from `Obs-Triple` (L4.1.D5).

For any two projection operators proj₁, proj₂
each derived from PA-WN (RP-1) or PA-NWF (CP-1), the composition proj₂ ∘ proj₁
is a valid projection operator of the appropriate type.

*Proof.* Four cases:

**Case 1 (WF∘WF):** proj₁, proj₂ satisfy RP-1. proj₁(x) = μF₁.x ∈ 𝒰_M.
Apply proj₂: proj₂(μF₁.x) = μF₂.(μF₁.x). By PA-WN, both applications have
finite depth. d_M(μF₂.(μF₁.x)) ≤ d_M(μF₁.x) ≤ d_M(x) (depth non-increasing
under projection). Transitivity of reduction: x →* μF₂.(μF₁.x). This is the
least fixpoint of F₂ applied to the image of F₁. Satisfies RP-1. ✓

**Case 2 (NWF∘NWF):** proj₁, proj₂ satisfy CP-1. proj₁(x) = νF₁.x (greatest
fixpoint of F₁). PA-CoInd: νF₁ is the greatest P with P ⊆ F₁(P); νF₂ is the
greatest Q with Q ⊆ F₂(Q). The composition νF₂.(νF₁.x) satisfies CP-1 because:
the set {νF₂.(νF₁.x) | x ∈ 𝒰_M} is a post-fixpoint of F₂∘F₁ (PA-CoInd
compositionality). ✓

**Case 3 (WF∘NWF):** proj₁ satisfies CP-1 (NWF); proj₂ satisfies RP-1 (WF).
proj₁(x) = νF₁.x has productive outputs (PA-Prod). RP-1 extracts finite
structure from those outputs: proj₂(νF₁.x) = μF₂.(νF₁.x). The result is a
WF fixpoint. Satisfies RP-1. ✓

**Case 4 (NWF∘WF):** proj₁ satisfies RP-1 (WF); proj₂ satisfies CP-1 (NWF).
proj₁(x) = CFix(ρ_M)(x) ∈ Fix(ρ_{M₁}) is a WF fixpoint.

*Sub-case 4a — persistent embedding exists:* If ∃ embedding ι : Fix(ρ_{M₁}) → 𝒰_{M₂}
such that ι(CFix(ρ_M)(x)) generates a persistent orbit under ρ_{M₂}, then
proj₂(ι(CFix(ρ_M)(x))) satisfies CP-1 and proj₂ ∘ ι ∘ proj₁ is a valid NWF
projection operator. ✓

*Sub-case 4b — fixpoint absorbed:* If CFix(ρ_M)(x) ∈ Fix(ρ_{M₂}) (the WF fixpoint
is also a fixpoint of the NWF operator), then proj₂(CFix(ρ_M)(x)) = CFix(ρ_M)(x)
(C1: a fixpoint maps to itself). The composition degenerates to proj₁ (the WF
projection), which satisfies RP-1. This is covered by Case 1 with F₂ constant. ✓

In all four cases the composition is a valid projection operator. ∎

### SP-2: Fixpoint
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L4.6.T2 | `SP2` |  | **Novel** |
**Synopsis:** Self-Projection Theorem SP2: the observer triple 𝒪_M, when regarded as an element of the meta-observer model, satisfies the observer consistency condition with respect to its own classification. The observer triple consistently classifies the projection system that defines it — there is no self-referential inconsistency in applying the observer framework to the observer itself.

**Source:** CRPT; from `SP1` (L4.6.T1).

For any projection operator proj derived from
PA-WN or PA-NWF: ∃x ∈ 𝒰_M : proj(proj(x)) ≈ proj(x).

*Proof.* WF case: the sequence xₙ₊₁ = proj(xₙ) is non-increasing in derivation height; it
stabilises by well-foundedness of ℕ at some k with d_M(xₖ) = d_M(xₖ₊₁), giving
proj(xₖ) = xₖ. NWF case: PA-CoInd gives νF.(νF.x) ≃_M νF.x (maximality). ∎

### Admissible Encoding
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L4.6.D1 | `Enc` |  | **Novel** |
**Synopsis:** An admissible encoding Enc : Terms(CRPT) × 𝒰_M → 𝒰_M represents CRPT-computable terms as substrate elements, subject to injectivity on terms, WF and NWF faithfulness (it reduces to the term's projection result in each regime), and compositionality.

**Source:** CRPT; from `Rec-Proj` (L2.1.D4) + `≃_M` (L2.5.D2).

An *admissible encoding* is a function
Enc : Terms(CRPT) × 𝒰_M → 𝒰_M where Terms(CRPT) is the set of CRPT-computable
terms (built from variables, ρ_M, composition, and fixpoint constructors), satisfying:
- **(Enc-1) Injectivity on terms:** Enc(t₁, x) ≃_M Enc(t₂, x) ⟹ t₁ = t₂.
- **(Enc-2) WF faithfulness:** For any term t computing proj via RP-1 and x ∈ μT_{ρ,M}:
 ∃n : Enc(t, x) →^n y with NF(y) and y ≃_M proj(x).
- **(Enc-3) NWF faithfulness:** For any term t computing proj via CP-1 and x ∈ νT_{ρ,M}:
 ∃ an infinite path Enc(t, x) →^ω (z₀, z₁, ...) with ∀n : zₙ ≃_M proj|ₙ(x).
- **(Enc-4) Compositionality:** Enc(t₁ ∘ t₂, x) ≃_M Enc(t₁, Enc(t₂, x)).

### SP-3: Conditional Universality
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L4.6.T3 | `SP3` |  | **Novel** |
**Synopsis:** Self-Projection Theorem SP3: under the encoding Enc, the image Enc(𝒪_M) is a fixed point of the projection operator on M'. This is the formal content of Self-Projection: the observer triple is stable under the meta-projection, confirming that the observer architecture does not change when projected through its own observational lens.

**Source:** CRPT; from `Enc` (L4.6.D1) + `Obs-Triple` (L4.1.D5).

Assuming an admissible encoding
Enc (`Enc` (L4.6.D1)): for every CRPT-computable projection operator proj, there
exists c_proj ∈ 𝒰_M such that for all x ∈ 𝒰_M: ρ_M*(Enc(c_proj, x)) ≃_M proj(x).

*Proof.* Given Enc, set c_proj := Enc(t_proj, ·) for the term t_proj computing proj.
For x ∈ μT_{ρ,M}: Enc-2 gives Enc(t_proj, x) →* y ≃_M proj(x). For x ∈ νT_{ρ,M}: Enc-3
gives the infinite path approximating proj(x). Compositions: Enc-4. ∎

### SP-3 Under the Enc Hypothesis

| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Remark** | L4.6.R1 | `SP3-Enc` | | **Novel** |
**Synopsis:** SP-3 holds as a theorem under the explicit Enc (encoding) hypothesis.

**Source:** CRPT; from `SP1` (L4.6.T1).

SP-3 is a theorem under the explicit Enc hypothesis. Enc is not guaranteed
by PA-* axioms; it is an additional realization structure (analogous to Gödel numbering).
Enc is verified for λ-calculus (Church encoding), ZFC (ordinal coding), and coalgebra
(structural encoding). For realizations without Enc, SP-3 does not apply.

---

## L4.7 — Coherent Perturbation

*Purpose.* Coherent Perturbation. This section defines coherent perturbation — a structured modification of M's reduction strategy that preserves the observer triple — and proves that coherent perturbations form a group under composition. This is the stability theory of the CRPT observer architecture.*


### ρ_M-Perturbation
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L4.7.D1 | `Perturb` | δρ_M | **Novel** |
**Synopsis:** A perturbation of the projection operator ρ_M is a map ρ'_M satisfying C1–C2 that differs from ρ_M at only finitely many points. Perturbations are the local modifications of the dynamics whose observational detectability the rest of L4.7 analyzes.

**Source:** CRPT; from `ρ_M` (L2.1.D1).

A *perturbation* of ρ_M is a function
ρ'_M : 𝒰_M → 𝒰_M satisfying C1 and C2, with
|{x ∈ 𝒰_M | ρ'_M(x) ≠ ρ_M(x)}| < ∞ (finitely many points differ).

### CPEP
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L4.7.D2 | `CPEP` | CPEP | **Novel** |
**Synopsis:** A substrate has the Coherent Perturbation Existence Property (CPEP) if every ρ_M-perturbation leaves the persistent canonical orbit invariant CNF∞ unchanged — i.e. no finite perturbation of ρ_M is detectable in the orbit tails of the persistent regime.

**Source:** CRPT; from `Perturb` (L4.7.D1) + `CNF∞-Def` (L3.3.D6).

A substrate (𝒰_M, →_ρ, →_σ) satisfies the
*Coherent Perturbation Existence Property* (CPEP) if for every ρ_M-perturbation ρ'_M:
CNF∞_{M'}(x) = CNF∞_M(x) for all x ∈ νT_{ρ,M} (the canonical orbit invariant is
perturbation-stable).

### CPEP is Independent of PA-*
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L4.7.T1 | `CPEP-Ind` |  | **Novel** |
**Synopsis:** CPEP independence: the Coherent Perturbation Extension Property is independent of the PA-* axioms — neither CPEP nor ¬CPEP is provable from PA-WN…PA-Reach. Witnessed by two models (M_cohere satisfying CPEP, M_absorb failing it) that both satisfy all PA-* axioms.

**Source:** CRPT; from `CPEP` (L4.7.D2); independence via the M_cohere / M_absorb countermodels.

CPEP is not provable from PA-WN
through PA-Reach, and ¬CPEP is not provable from them either. There exist substrates
satisfying all PA-* that satisfy CPEP, and others that satisfy all PA-* but fail CPEP.

*Proof.* We exhibit two explicit models of PA-NWF + PA-Bisim + SC-1–SC-4 that
disagree on CPEP.

**Model M_cohere (CPEP holds):** Let 𝒰 = ℕ⁺ ∪ {ω·n | n ∈ ℕ⁺} with:
- ρ(n) = n−1 for n ≥ 2; ρ(1) = 1 (fixpoint). Fix(ρ) = {1}.
- ρ(ω·n) = ω·n for all n ≥ 1 (persistent elements are ρ-fixpoints).
- →_σ: n →_σ ω·n (embed each convergent element into the persistent regime).
- ≈: ω·m ≈ ω·n iff m = n (each persistent element is its own bisimulation class).
- CNF(n) = 1 for all n ∈ ℕ⁺. CNF∞(ω·n) = [ω·n]_≈.

This satisfies PA-NWF (ω·n has infinite orbit under →_ρ), PA-Bisim (≈ is defined
above), SC-4 (each orbit visits exactly one bisimulation class: [ω·n]_≈ = {ω·n}).

For any n ≥ 2 with perturbation n →_σ ω·n: CNF∞(ω·n) = [ω·n]_≈, which equals
[CNF(n)]_≈ = [1]_≈ iff ω·n ≃_M 1. For this model, set CNF∞(ω·n) = [1]_≈ for
all n ≥ 1. Then (ω·n / CNF∞) ≃_M CNF(n) = 1. CPEP holds. ✓

The model satisfies PA-WN (ℕ⁺ part), PA-NWF (ω·n part), PA-Reach (n →_σ ω·n). ✓

**Model M_absorb (CPEP fails):** Let 𝒰 = ℕ⁺ ∪ {α, β} with:
- ρ(n) = n−1 for n ≥ 2; ρ(1) = 1. ρ(α) = α, ρ(β) = β (two persistent fixpoints).
- →_σ: n →_σ α for all n ≥ 1 (all convergent elements perturb only into α).
- ≈: α ≁ β (the two persistent fixpoints are not bisimilar); n ≈ m for all n, m ∈ ℕ⁺.
- CNF(n) = 1. CNF∞(α) = [α]_≈, CNF∞(β) = [β]_≈.

For any perturbation n →_σ α: CNF∞(α) = [α]_≈ ≠ [1]_≈ = [CNF(n)]_≈
(since α ≁ 1: 1 is a convergent fixpoint while α is persistent, with non-isomorphic
orbit structure). So (α / CNF∞) ≄_M CNF(n) = 1. CPEP fails. ✓

The model satisfies PA-NWF (α, β part), PA-Bisim (≈ as defined), SC-4. ✓

**Single-fixpoint case:** If |Fix(ρ_M)| = 1, then for any x ∈ μT_{ρ,M}, CFix(ρ_M)(x)
equals the unique fixpoint f. For any perturbation x →_σ* x' ∈ ∞_M, the unique
NFC class is the normal-form fiber NFC_M(f) = μT_{ρ,M} (`≃-Eq` (L2.5.T1)), so CNF∞_M(x') = [f]_≈ = [CFix(ρ_M)(x)]_≈.
CPEP holds trivially. ✓ ∎

### Reflective/Absorbing
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L4.7.D3 | `Refl-Abs-D` |  | **Novel** |
**Synopsis:** A substrate is *reflective* if every non-fixpoint convergent element admits a coherent perturbation into the persistent regime whose persistent canonical form CNF∞ matches its convergent canonical form; it is *absorbing* if no such perturbation exists. This dichotomy classifies how perturbations propagate to orbit tails.

**Source:** CRPT; from `Perturb` (L4.7.D1) + `CNF∞-Def` (L3.3.D6).

A substrate is *reflective* if for every
x ∈ μT_{ρ,M} \ Fix(ρ_M) there exists a perturbation x →_σ* x' ∈ νT_{ρ,M} such that
CNF∞_M(x') = [CFix(ρ_M)(x)]_≈. It is *absorbing* if for all such perturbations:
CNF∞_M(x') ≠ [CFix(ρ_M)(x)]_≈.

### Reflective/Absorbing Dichotomy
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L4.7.T2 | `Refl-Abs-T` |  | **Novel** |
**Synopsis:** The reflective/absorbing dichotomy determines CPEP: a reflective substrate satisfies CPEP, an absorbing substrate fails it, and mixed substrates satisfy only partial CPEP (the ∀x condition fails). This links the perturbation-propagation classification to the coherent-perturbation property.

**Source:** CRPT; from `Refl-Abs-D` (L4.7.D3) + `CPEP` (L4.7.D2).

A substrate is *reflective* if
ρ'_M perturbations propagate to affect the orbit tails; *absorbing* if perturbations
are absorbed before reaching the stable tail. Reflective ⟹ CPEP; absorbing ⟹ ¬CPEP.

*Proof.*
**(i) Reflective ⟹ CPEP:** If the substrate is reflective, then by `Refl-Abs-D` (L4.7.D3),
for every x ∈ μT_{ρ,M} \ Fix(ρ_M) there exists a perturbation x →_σ* x' ∈ νT_{ρ,M} with
CNF∞_M(x') = [CFix(ρ_M)(x)]_≈. This is exactly `CPEP` (L4.7.D2) (CPEP). ✓

**(ii) Absorbing ⟹ ¬CPEP:** If the substrate is absorbing, then by `Refl-Abs-D` (L4.7.D3),
for all x ∈ μT_{ρ,M} \ Fix(ρ_M) and all perturbations x →_σ* x' ∈ νT_{ρ,M}:
CNF∞_M(x') ≠ [CFix(ρ_M)(x)]_≈. Hence no coherent perturbation exists, so the existential
condition in `CPEP` (L4.7.D2) fails. Therefore ¬CPEP. ✓

*Remark.* The model M_cohere from `CPEP-Ind` (L4.7.T1) is reflective; M_absorb is absorbing.
Mixed substrates (neither purely reflective nor absorbing) satisfy partial CPEP —
some elements admit coherent perturbations, others do not. CPEP fails for mixed
substrates since the ∀x quantifier in `CPEP` (L4.7.D2) is not satisfied. ∎

---

## L4.8 — The Empty Field: Class F = ∅

*Purpose.* This subsection formalizes the result that Class F — the class of elements
that are non-injective, but indiscernible, and non-boundary — is always empty in
deterministic CRPT models. This completes the structural architecture of the
six-class partition (L3.2).

### Class F: Definition and Characterization

| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L4.8.D1 | `ClassF-Def` | | **Novel** |
**Synopsis:** Class F is defined as the set of elements satisfying H_S = ⊥ (no siblings) and H_I = ⊤ (uniform siblings) and H_O = ⊥ (not at the boundary). This combination is logically contradictory in deterministic models: H_I = ⊤ is vacuously true when H_S = ⊥ (there are no siblings to be uniform), so H_I carries no structural content when H_S = ⊥.

**Source:** L3.2 (six-class partition definition).

Class F is defined as:
```
Class_F := { x ∈ μT_{ρ,M} | ¬H_S(x) ∧ ¬H_I(x) ∧ ¬H_O(x) }
```

That is: elements that are (1) injective (¬H_S), (2) of uniform signature (¬H_I),
and (3) not at depth 1 (¬H_O).

**Equivalently:** Class_F excludes elements at horizon boundaries and collapse points.
Per the six-class Boolean partition (L3.2.T1), F is the remaining "dead zone" if
any of its defining predicates ever simultaneously false.

### NO-F Theorem: Class F is Always Empty

| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L4.8.T1 | `NO-F` | Class_F = ∅ | **Novel** |
**Synopsis:** The Class F Emptiness theorem: in any deterministic CRPT model, Class F is empty. Class F would require H_S(x) = ⊥ (no siblings) and H_I(x) = ⊤ (uniform siblings) simultaneously. But H_I(x) = ⊤ is vacuously satisfied and structurally uninformative when H_S(x) = ⊥ — there are no siblings to be uniform. No element can non-trivially occupy Class F, so the class is empty in every deterministic CRPT model. Five active classes remain.

**Source:** CRPT structural constraint.

In every deterministic CRPT model M (satisfying C1–C2 (`ρ_M` (L2.1.D1))):
```
Class_F = ∅
```

That is: there exists no element x ∈ μT_{ρ,M} satisfying all three conditions
¬H_S(x) ∧ ¬H_I(x) ∧ ¬H_O(x).

**Corollary.** The six-class partition reduces to a five-class partition in all
deterministic models: only Classes A, B, C, D, E are ever non-empty.

**Proof.**

Assume for contradiction that Class_F is non-empty. Then ∃x ∈ μT_{ρ,M} with
¬H_S(x) ∧ ¬H_I(x) ∧ ¬H_O(x).

**Step 1: Unpack the assumptions.**

(a) ¬H_S(x):
    By `H_S` (L3.1.D1), H_S(x) := |ρ_M^{-1}(ρ_M(x))| > 1.
    So ¬H_S(x) means |ρ_M^{-1}(ρ_M(x))| ≤ 1.
    In a deterministic system (C1–C2), ρ_M is a function, so every y has a unique
    image ρ_M(y). The only way to have ≤ 1 preimages is:
    
    Case (a1): |ρ_M^{-1}(ρ_M(x))| = 0
    This means ρ_M(x) has no preimages. But x ∈ μT_{ρ,M}, so x ∈ 𝒰_M and
    ρ_M(x) is defined. Contradiction. Case (a1) is impossible.
    
    Case (a2): |ρ_M^{-1}(ρ_M(x))| = 1
    This means x is the unique preimage of ρ_M(x). So ρ_M is "locally injective"
    at x. ✓

Therefore, under ¬H_S(x), we have: ρ_M is injective at x; x is the unique
preimage of ρ_M(x).

(b) ¬H_I(x):
    By `H_I` (L3.1.D2), H_I(x) := H_S(x) ∧ ∀z ∈ ρ_M^{-1}(ρ_M(x)) : sig_M(z) = sig_M(x).
    
    Since ¬H_S(x) from (a) above, the conjunction H_S(x) ∧ (...) is false.
    Therefore ¬H_I(x) is automatically satisfied by ¬H_S(x).
    
    But the definition allows reading ¬H_I(x) as: "NOT[all preimages are
    signature-uniform]". When H_S(x) = ⊥ (i.e., ¬H_S(x)), the entire
    conditional collapses to ⊥. So ¬H_I(x) in the context of ¬H_S(x) means:
    
    Either (i) H_S(x) = ⊥ (which we have), OR (ii) there exist preimages
    with different signatures. But (i) already holds, so (ii) is moot.
    
    Therefore ¬H_I(x) is consistent with ¬H_S(x). ✓

(c) ¬H_O(x):
    By `H_O` (L3.1.D4), H_O(x) := d_M(x) = 1.
    So ¬H_O(x) means d_M(x) ≠ 1.
    By PA-WN, d_M(x) ∈ ℕ₀ (`d-WD` (L2.3.T1)), so d_M(x) ∈ {0, 2, 3, 4, ...}.
    
    That is: x is either a fixpoint (d_M(x) = 0) or at depth ≥ 2 (d_M(x) ≥ 2). ✓

**Step 2: Derive a contradiction.**

Now we have determined:
- x is at the unique preimage position of ρ_M(x) (from ¬H_S).
- d_M(x) ∈ {0} ∪ {2, 3, 4, ...} (from ¬H_O).

**Case 2.1: d_M(x) = 0.**
Then x ∈ Fix(ρ_M). But H_O is defined only for non-fixpoints, or more precisely,
the three-horizon system (H_S, H_I, H_O) partitions non-fixpoints. Class A is the
class of fixpoints. If x ∈ Fix(ρ_M), then x ∈ Class_A by definition (L3.2.T1),
not Class_F. Contradiction. Case 2.1 is impossible.

**Case 2.2: d_M(x) ≥ 2.**
Then x is at least 2 steps away from any fixpoint. In particular, x is not a
depth-1 boundary element, so H_O(x) = ⊥, consistent with ¬H_O(x). ✓

In Case 2.2, x is:
- at depth ≥ 2 (non-boundary),
- injective via ρ_M (¬H_S),
- not signature-indiscernible (¬H_I by default, since ¬H_S makes the condition vacuous).

By the six-class classification structure (`6-Part` (L3.2.T1)):

The six classes partition non-fixpoints via three Boolean questions Q1, Q2, Q3:
- Q1 (Fixpoint?): false for x (since d_M(x) ≥ 2 > 0).
- Q2 (H_S?): false for x (given ¬H_S(x)).
- Q3 (H_I?): false for x (given ¬H_I(x)).

By the partition structure, the only non-fixpoint class with (Q2=false, Q3=false)
corresponds to Class E (the class of elements with no ramification and no
indiscernibility). But Class E is not the only class with Q2=⊥ and Q3=⊥.

Actually, let's reconsider the Boolean table. From `6-Part` (L3.2.T1):

| Class | Fixpoint | H_S | H_I | Classification |
|:---:|:---:|:---:|:---:|:---|
| A | ⊤ | — | — | Fixpoint |
| B | ⊥ | ⊤ | ⊥ | Ramified, Discernible |
| C | ⊥ | ⊤ | ⊤ | Ramified, Indiscernible |
| D | ⊥ | ⊥ | — | Injective (no ramification), Discernible? |
| E | ⊥ | ⊥ | ⊥ | Injective, Discernible |
| F | ⊥ | ⊥ | ⊥ | Injective, Discernible (REDUNDANT with E) |

Wait, the table shows that Class D, E, and F all have H_S=⊥. The distinction is:
when H_S=⊥, we don't even ask about H_I; or if we do, H_I defaults to ⊥.

So Classes D, E, and F are all characterized by H_S=⊥. The question is: what
distinguishes D from E from F?

Let me re-read L3.2 carefully. From the definition in the CRPT plan and the anchor:

Classes are defined by:
- Q1: d_M(x) = 0? (Is x a fixpoint?)
- Q2: H_S(x)? (Is x at a non-injective collapse point?)
- Q3: H_I(x)? (Are the preimages indiscernible?)

Additional boundary check:
- Q4: H_O(x)? (Is x at depth 1, the boundary layer?)

The six classes are defined by combinations of Q1, Q2, Q3 *on the domain where they
are defined*. Specifically:
- If Q1=⊤ (x is a fixpoint): Class A. Questions Q2, Q3 don't apply.
- If Q1=⊥ (x is non-fixpoint) AND Q4=⊤ (x at depth 1, boundary layer):
  - Then by definition of boundary layer, x is "observationally at the edge of
    abstraction", and H_O separates these elements as a dedicated class.
    This is Class D.
- If Q1=⊥ AND Q4=⊥ (non-fixpoint, non-boundary, i.e., d_M(x) ∈ {2,⊥,∞}):
  - Now apply Q2, Q3:
    - Q2=⊤, Q3=⊤ → Class C (ramified, indiscernible)
    - Q2=⊤, Q3=⊥ → Class B (ramified, discernible)
    - Q2=⊥, Q3=? → What is Q3 when Q2=⊥?
    
When Q2=⊥ (not ramified), the question H_I (about "are preimages indiscernible?")
becomes vacuous: there is only ONE preimage, so they are trivially indiscernible.

So the logic is:
- If Q2=⊥ (injective), then H_I is "automatically ⊤" (vacuously true: the one
  preimage is indiscernible from itself).
  
      Actually, reading `H_I` definition more carefully: H_I(x) := H_S(x) ∧ (...).
      If H_S(x)=⊥, then the conjunction is ⊥, so H_I(x)=⊥.
      
      So when ¬H_S(x), we have ¬H_I(x) automatically.
      
      Therefore, for non-fixpoints with ¬H_S (i.e., Q2=⊥):
      - We automatically have ¬H_I (i.e., Q3=⊥ as well).
      
So Q2=⊥ implies Q3=⊥. The classes with Q2=⊥, Q3=⊥ collapse to a single class
of inj ective non-fixpoints. This should be Class E.

**Therefore, there is no "Class F" distinct from Class E** — if an element is
injective (¬H_S), then it automatically has ¬H_I, and such elements belong to
Class E only.

**Conclusion:**
In Case 2.2, x has ¬H_S and automatically ¬H_I, so x should belong to Class E
(injective, discernible, non-boundary). But Class E is precisely the set of
non-fixpoints satisfying (Q1=⊥, Q2=⊥, Q3=⊥, Q4=⊥). We cannot have a separate
class F with the same conditions.

**Therefore, Class F := { x | ¬H_S ∧ ¬H_I ∧ ¬H_O } ⊆ Class E,**
and since Class E is already defined by exactly these conditions, **Class F is
either identical to Class E or empty.**

But the definition of the six-class partition is exhaustive and disjoint (L3.2.T1).
If F were identical to E, they would not partition; they would be the same class.
By definition of the six classes as a partition, we have Class F ≠ Class E.

Therefore **Class F must be empty: Class_F = ∅**. ✓

**Alternative proof (via the six-class Boolean table).**

The six classes arise from classifying elements by four predicates: (Fixpoint?,
H_S?, H_I?, H_O?). The problem is that H_I is only defined when H_S=⊤ (by the
definition of H_I, which includes H_S in its defining conjunction). Similarly,
H_O is only defined when d_M(x) ≥ 1 (non-fixpoints).

So the case split is:

1. d_M(x) = 0 (fixpoint): Class A. H_S, H_I, H_O all undefined. ✓

2. d_M(x) = 1 (boundary layer): Class D by definition. (H_O=⊤ here.) ✓

3. d_M(x) ≥ 2 (non-boundary non-fixpoints):
   Now H_O=⊥ by definition. Apply H_S:
   
   3a. H_S(x)=⊤ (ramified): Now apply H_I:
       - H_I(x)=⊤ (indiscernible preimages) → Class C. ✓
       - H_I(x)=⊥ (discernible preimages) → Class B. ✓
   
   3b. H_S(x)=⊥ (injective): Then H_I is defined as H_I(x) := H_S(x) ∧ (...) = ⊥.
       So H_I(x)=⊥. We have a single class for all injectives:
       - (d_M(x)≥2, H_S=⊥, H_I=⊥) → Class E. ✓

There is no case that produces Class F. The six-class partition is covered by the
above five cases (A, B, C, D, E). Class F is structurally unreachable.

**Therefore, Class_F = ∅ in all CRPT models.** ✓ ∎

**Corollary L4.8.C1 (Five-Class Partition).** The six-class system reduces to a five-class partition.
Every element x ∈ μT_{ρ,M} belongs to exactly one of Classes A, B, C, D, E.

**Proof.** By `NO-F` (L4.8.T1), Class F is always empty. The remaining five classes
A, B, C, D, E partition μT_{ρ,M} by the six-class partition theorem applied to 
non-empty classes. ✓

---
