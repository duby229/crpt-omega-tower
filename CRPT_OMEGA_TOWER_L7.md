# L7 — Categorical Collapse, Functoriality, and Model-Theory Fibration

## L7.1 — Abstraction as Epimorphism / Collapse

**Provenance.** The Cousot-Cousot abstraction framework is [Formalized — Cousot &
Cousot 1977, L1.2–L1.5]. The orbit equivalence quotient is [Formalized — standard ARS
(Baader & Nipkow L1.2)]. Exhibiting these ρ_M-derived
constructs *as* a category-theoretic collapse, epimorphism/kernel formalism, and functorial
image — i.e. showing CRPT's own structure is categorical — is [Novel: CRPT Self-Categoricity].

### The Abstraction Function and Galois Insertion

### Galois Insertion / Recursive Projection Pair
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L7.1.D1 | `GI` | α_M⊣γ_M | **Reframed** |
**Synopsis:** CRPT's abstraction-concretisation duality — built entirely from ρ_M — *is itself* a Galois insertion α_M ⊣ γ_M between 𝒰_M and the query signature; the categorical structure is a consequence of the projection machinery, not an assumption underlying it. α_M sends each element to its canonical fiber class; γ_M selects a canonical representative. Their adjointness means abstracting and then concretising yields an element observationally equivalent to the original — the round-trip is lossless at the observational level.

**Source:** Ore [1944] *Galois Connexions*; Birkhoff [1940] *Lattice Theory* — Galois connection / adjoint pair.

*Reframing Note.* **Source form:** Galois connection / adjoint pair between posets (Ore [1944]; Birkhoff [1940]). **CRPT form:** the abstraction–concretisation pair α_M ⊣ γ_M built internally from ρ_M, sharpened to a Galois **insertion** (α_M ∘ γ_M = id). **The delta:** the connection is not posited between externally given posets — both maps are constructed from the projection operator — and the insertion property is established, not assumed. **Justification:** mathematical — insertion is what makes Q_M a genuine retract of 𝒰_M, grounding the Collapse construction of L7.1.


Under PA-WN and PA-Conf, define:
```
α_M : ↓_M → Fix(ρ_M) α_M(x) := CFix(ρ_M)(x) [Abstraction / upper adjoint]
γ_M : Fix(ρ_M) → ↓_M γ_M(f) := f [Concretisation / lower adjoint / inclusion]
```
The pair (α_M, γ_M) is a **Galois insertion** between (↓_M, ≤_ρ) and (Fix(ρ_M), =).

*Standard name:* Galois insertion (Cousot & Cousot [1977]): a Galois connection
where the abstraction function α is surjective. The ambient posets are (↓_M, ≤_ρ) on
the concrete side and (Fix(ρ_M), =) on the abstract side — both defined from ρ_M and
the PA-* derived machinery, with no new structure introduced. The specialization from the
general order-theoretic setting is required because the posets are the model-specific
ρ_M-reachability order and the degenerate equality order on fixpoints.

### Galois Connection — Full Biconditional
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L7.1.T1 | `GC` |  | **Novel** |
**Synopsis:** The Galois Connection theorem establishes the adjointness α_M ⊣ γ_M: the abstraction map α_M and concretisation map γ_M satisfy x ≤ γ_M(α_M(x)) and α_M(γ_M(f)) = f for all x ∈ 𝒰_M and f ∈ Q_M. This means abstracting and concretising always produces something above x in the reduction order, and the round-trip concretisation-then-abstraction is the identity.

**Source:** CRPT; categorical form of [`RP=Abs` (L2.1.T4)](CRPT_OMEGA_TOWER_L2.md#recursive-projection--abstraction), from [PA-WN (L1.2.Ax1)](CRPT_OMEGA_TOWER_L1.md#pa-wn--weak-normalisation) + [PA-Conf (L1.2.Ax2)](CRPT_OMEGA_TOWER_L1.md#pa-conf--confluence--church-rosser) + C1 ([`ρ_M` (L2.1.D1)](CRPT_OMEGA_TOWER_L2.md#projection-operator-ρ_m)).

*Novelty Note.* **Basis (credited):** [`RP=Abs` (L2.1.T4)](CRPT_OMEGA_TOWER_L2.md#recursive-projection--abstraction) + [PA-WN (L1.2.Ax1)](CRPT_OMEGA_TOWER_L1.md#pa-wn--weak-normalisation) + [PA-Conf (L1.2.Ax2)](CRPT_OMEGA_TOWER_L1.md#pa-conf--confluence--church-rosser) + [`ρ_M` (L2.1.D1)](CRPT_OMEGA_TOWER_L2.md#projection-operator-ρ_m). **New:** The Galois Connection theorem establishes the adjointness α_M ⊣ γ_M: the abstraction map α_M and concretisation map γ_M satisfy x ≤ γ_M(α_M(x)) and α_M(γ_M(f)) = f for all x ∈ 𝒰_M and f ∈ Q_M. **Why it does not follow:** the statement is not an unfolding of the basis; the proof in the body supplies the argument that connects them.

```
∀x ∈ ↓_M, ∀f ∈ Fix(ρ_M) : α_M(x) = f ⟺ x ≤_ρ γ_M(f)
```
Equivalently:
```
∀x ∈ ↓_M, ∀f ∈ Fix(ρ_M) : CFix(ρ_M)(x) = f ⟺ x ≤_ρ f
```

*Proof.* This is [`RP=Abs` (L2.1.T4)](CRPT_OMEGA_TOWER_L2.md#recursive-projection--abstraction), proved in full in L2.1 using [`Fix-Stab` (L2.1.L1)](CRPT_OMEGA_TOWER_L2.md#fixpoints-are-ρ_m-stable) and [`UF` (L2.1.L2)](CRPT_OMEGA_TOWER_L2.md#unique-reachable-fixpoint).
The proof uses PA-WN (existence of d_M(x) ∈ ℕ via [`Depth-Dec` (L2.3.T2)](CRPT_OMEGA_TOWER_L2.md#strict-depth-decrease) and [`Fix-D0` (L2.3.T3)](CRPT_OMEGA_TOWER_L2.md#fixpoints-have-depth-zero)), PA-Conf (uniqueness
of the fixpoint reached), and C1 (Step-or-Fix property). No additional structure
is required. ∎

### GC1 — Retraction
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Corollary** | L7.1.C1 | `GC1` |  | **Derived** |
**Synopsis:** Corollary: the abstraction map α_M is surjective — every element of Q_M is the canonical form of some element of 𝒰_M. This follows immediately from the Galois connection: α_M ∘ γ_M = id_{Q_M}.

**Source:** CRPT; corollary of [`GC` (L7.1.T1)](CRPT_OMEGA_TOWER_L7.md#galois-connection--full-biconditional).

*Derivation:* composed from [`GC` (L7.1.T1)](CRPT_OMEGA_TOWER_L7.md#galois-connection--full-biconditional); no content beyond the composition.

α_M ∘ γ_M = id_{Fix(ρ_M)}.

*Proof.* For f ∈ Fix(ρ_M): by [`GC` (L7.1.T1)](CRPT_OMEGA_TOWER_L7.md#galois-connection--full-biconditional) (←) with x = f, f ≤_ρ f (reflexive,
k = 0 witnesses ρ_M^0(f) = f), so CFix(ρ_M)(f) = f. Thus α_M(γ_M(f)) = CFix(ρ_M)(f) = f. ∎

### GC2 — Upper Adjunction
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Corollary** | L7.1.C2 | `GC2` |  | **Derived** |
**Synopsis:** Corollary: the concretisation map γ_M is injective — distinct elements of Q_M give distinct canonical representatives in 𝒰_M. No two fiber classes share a canonical representative.

**Source:** CRPT; corollary of [`GC` (L7.1.T1)](CRPT_OMEGA_TOWER_L7.md#galois-connection--full-biconditional).

*Derivation:* composed from [`GC` (L7.1.T1)](CRPT_OMEGA_TOWER_L7.md#galois-connection--full-biconditional); no content beyond the composition.

γ_M ∘ α_M ≥ id_{↓_M} in the ≃_M
preorder: x ≃_M γ_M(α_M(x)) for all x ∈ ↓_M.

*Proof.* γ_M(α_M(x)) = CFix(ρ_M)(x). By [`GC` (L7.1.T1)](CRPT_OMEGA_TOWER_L7.md#galois-connection--full-biconditional) (→): CFix(ρ_M)(x) = CFix(ρ_M)(x) implies
x ≤_ρ CFix(ρ_M)(x), so ∃k = d_M(x): ρ_M^k(x) = CFix(ρ_M)(x), giving x →_ρ* CFix(ρ_M)(x).
By [`≃_M` (L2.5.D2)](CRPT_OMEGA_TOWER_L2.md#church-rosser-orbit-equivalence-notation-_m), x ≃_M CFix(ρ_M)(x) = γ_M(α_M(x)). ∎

### GC3 — Preserves Equivalence
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Corollary** | L7.1.C3 | `GC3` |  | **Derived** |
**Synopsis:** Corollary: the unit of the Galois connection η_x = γ_M(α_M(x)) satisfies η_x ≃_M x — the canonical representative of x's fiber class is observationally equivalent to x. The round-trip abstraction-then-concretisation preserves observational equivalence.

**Source:** CRPT; corollary of [`GC` (L7.1.T1)](CRPT_OMEGA_TOWER_L7.md#galois-connection--full-biconditional) via [`CNF=CR` (L2.5.T2)](CRPT_OMEGA_TOWER_L2.md#cnf-fiber--church-rosser-quotient).

*Derivation:* composed from [`GC` (L7.1.T1)](CRPT_OMEGA_TOWER_L7.md#galois-connection--full-biconditional) + [`CNF=CR` (L2.5.T2)](CRPT_OMEGA_TOWER_L2.md#cnf-fiber--church-rosser-quotient); no content beyond the composition.

x ≃_M y ⟹ α_M(x) = α_M(y).

*Proof.* By the CNF-Fibre Theorem ([`CNF=CR` (L2.5.T2)](CRPT_OMEGA_TOWER_L2.md#cnf-fiber--church-rosser-quotient)): x ≃_M y iff CFix(ρ_M)(x) = CFix(ρ_M)(y),
i.e., α_M(x) = α_M(y). ∎

### Relationship to L2.1

| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Remark** | L7.1.R1 | `GC-vs-L2.1` | | **Novel** |
**Synopsis:** GC restates the L2.1 Galois connection in the (α_M, γ_M) notation.

**Source:** CRPT; from [`GC` (L7.1.T1)](CRPT_OMEGA_TOWER_L7.md#galois-connection--full-biconditional) + [`GI` (L7.1.D1)](CRPT_OMEGA_TOWER_L7.md#galois-insertion--recursive-projection-pair).

*Novelty Note.* **Basis (credited):** [`GC` (L7.1.T1)](CRPT_OMEGA_TOWER_L7.md#galois-connection--full-biconditional) + [`GI` (L7.1.D1)](CRPT_OMEGA_TOWER_L7.md#galois-insertion--recursive-projection-pair). **New:** GC restates the L2.1 Galois connection in the (α_M, γ_M) notation. **Why it does not follow:** the stated observation is the contribution; the basis does not state it.

[`GC` (L7.1.T1)](CRPT_OMEGA_TOWER_L7.md#galois-connection--full-biconditional) here is the L2.1 Galois
connection theorem in the (α_M, γ_M) notation of [`GI` (L7.1.D1)](CRPT_OMEGA_TOWER_L7.md#galois-insertion--recursive-projection-pair).
Corollaries [`GC1` (L7.1.C1)](CRPT_OMEGA_TOWER_L7.md#gc1--retraction)–[`GC3` (L7.1.C3)](CRPT_OMEGA_TOWER_L7.md#gc3--preserves-equivalence) are classical consequences of the biconditional, which is
strictly stronger than the three corollaries individually.

### The Collapse Map as Epimorphism and Kernel Structure

### Canonical Epimorphism / Quotient Projection
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L7.1.D2 | `Quot-Proj` | π_M | **Specialized** |
**Synopsis:** The quotient projection π_M : 𝒰_M → Q_M sends each element to its fiber equivalence class. It is surjective (every class has at least one element), and its fibers are exactly the normal-form fibers NFC_M(f). This is the CRPT instantiation of the standard quotient map.

**Source:** Mac Lane [1998] §I.3 — canonical quotient map; applied to [`≃_M` (L2.5.D2)](CRPT_OMEGA_TOWER_L2.md#church-rosser-orbit-equivalence-notation-_m) on ↓_M.

The *canonical quotient projection* is the epimorphism:
```
π_M : ↓_M ↠ Q_M π_M(x) := [x]_{≃_M} = NFC_M(CFix(ρ_M)(x))
```
where Q_M := ↓_M/≃_M = {NFC_M(f) | f ∈ Fix(ρ_M)} is the **abstraction quotient**.

### π_M is Surjective / Epic
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Lemma** | L7.1.L1 | `π-Sur` |  | **Novel** |
**Synopsis:** Surjectivity of the quotient projection: every element of Q_M = ↓_M/≃_M is the image of at least one element of 𝒰_M under π_M. This is immediate from the definition of the quotient.

**Source:** CRPT; from [`Quot-Proj` (L7.1.D2)](CRPT_OMEGA_TOWER_L7.md#canonical-epimorphism--quotient-projection).

*Novelty Note.* **Basis (credited):** [`Quot-Proj` (L7.1.D2)](CRPT_OMEGA_TOWER_L7.md#canonical-epimorphism--quotient-projection). **New:** Surjectivity of the quotient projection: every element of Q_M = ↓_M/≃_M is the image of at least one element of 𝒰_M under π_M. **Why it does not follow:** the statement is not an unfolding of the basis; the proof in the body supplies the argument that connects them.

π_M is surjective onto Q_M: for every fiber
F ∈ Q_M, there exists x ∈ ↓_M with π_M(x) = F (choose any x ∈ F).

*Proof.* Every F ∈ Q_M is a non-empty ≃_M-class ([`≃_M` (L2.5.D2)](CRPT_OMEGA_TOWER_L2.md#church-rosser-orbit-equivalence-notation-_m)); choosing any x ∈ F gives π_M(x) = F by [`Quot-Proj` (L7.1.D2)](CRPT_OMEGA_TOWER_L7.md#canonical-epimorphism--quotient-projection). ∎

### Kernel of Epimorphism / Fiber Characterisation
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L7.1.T2 | `Ker-Fib` | | **Novel** |
**Synopsis:** The Kernel Fibration theorem establishes that the kernel of the quotient projection π_M — the equivalence relation ker(π_M) = {(x,y) | π_M(x) = π_M(y)} = ≃_M — is a CRPT fibration: the canonical projection on fibers is itself a CRPT projection operator on the quotient. This makes the quotient structure a genuine CRPT model.

**Source:** CRPT; from [`Quot-Proj` (L7.1.D2)](CRPT_OMEGA_TOWER_L7.md#canonical-epimorphism--quotient-projection) + [`≃_M` (L2.5.D2)](CRPT_OMEGA_TOWER_L2.md#church-rosser-orbit-equivalence-notation-_m).

*Novelty Note.* **Basis (credited):** [`Quot-Proj` (L7.1.D2)](CRPT_OMEGA_TOWER_L7.md#canonical-epimorphism--quotient-projection) + [`≃_M` (L2.5.D2)](CRPT_OMEGA_TOWER_L2.md#church-rosser-orbit-equivalence-notation-_m). **New:** The Kernel Fibration theorem establishes that the kernel of the quotient projection π_M — the equivalence relation ker(π_M) = {(x,y) | π_M(x) = π_M(y)} = ≃_M — is a CRPT fibration: the canonical projection on fibers is itself a CRPT projection operator on the quotient. **Why it does not follow:** the statement is not an unfolding of the basis; the proof in the body supplies the argument that connects them.

The kernel of π_M (the fiber over any point) is exactly the ≃_M-equivalence class:
```
ker(π_M) = {(x, x') ∈ ↓_M × ↓_M | π_M(x) = π_M(x')}
 = {(x, x') | x ≃_M x'}
 = {(x, x') | CFix(ρ_M)(x) = CFix(ρ_M)(x')}
```

For each f ∈ Fix(ρ_M), the preimage fiber is:
```
π_M⁻¹(NFC_M(f)) = NFC_M(f) := {x ∈ ↓_M | CFix(ρ_M)(x) = f}
```

*Proof.* The displayed chain: π_M(x) = π_M(x′) iff x and x′ lie in the same quotient class ([`Quot-Proj` (L7.1.D2)](CRPT_OMEGA_TOWER_L7.md#canonical-epimorphism--quotient-projection)) iff x ≃_M x′ iff CFix(ρ_M)(x) = CFix(ρ_M)(x′) ([`≃_M` (L2.5.D2)](CRPT_OMEGA_TOWER_L2.md#church-rosser-orbit-equivalence-notation-_m)). Hence ker(π_M) = ≃_M, and each π_M-fiber is exactly one ≃_M-class — the fibration is by observable equivalence. ∎

### Abstraction Quotient as Fiber Space
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L7.1.D3 | `Ab-Quot` | Q_M | **Novel** |
**Synopsis:** The abstraction quotient Q_M = ↓_M/≃_M is the set of observational equivalence classes of convergent elements. Each class [x] ∈ Q_M is a normal-form fiber NFC_M(f) for some f ∈ Fix(ρ_M). Q_M is the universe of Lift(M): its elements become the atomic generators of the free monoidal algebra FMA(Q_M).

**Source:** CRPT; from [`≃_M` (L2.5.D2)](CRPT_OMEGA_TOWER_L2.md#church-rosser-orbit-equivalence-notation-_m) + [`Fix` (L2.1.D3)](CRPT_OMEGA_TOWER_L2.md#fixpoint-set).

*Novelty Note.* **Basis (credited):** [`≃_M` (L2.5.D2)](CRPT_OMEGA_TOWER_L2.md#church-rosser-orbit-equivalence-notation-_m) + [`Fix` (L2.1.D3)](CRPT_OMEGA_TOWER_L2.md#fixpoint-set). **New:** The abstraction quotient Q_M = ↓_M/≃_M is the set of observational equivalence classes of convergent elements. **Why it does not follow:** the basis supplies the ingredients; the notion assembled from them, and the role it is defined to play in the theory, is introduced here rather than entailed.

Q_M is the **fiber space** (set of equivalence classes / normal form fibers) of π_M:
```
Q_M = ↓_M/≃_M = {NFC_M(f) | f ∈ Fix(ρ_M)} [One fiber per fixpoint]
|Q_M| = |Fix(ρ_M)| [Surjectivity of CFix(ρ_M)]
```

Each element of Q_M is an equivalence class — the normal-form fiber NFC_M(f) ⊆ ↓_M —
consisting of all convergent elements with the same canonical abstraction f.

### The Duality: Abstraction Equals Collapse / Functional Representation

### Abstraction-Collapse Duality / Functorial Representation
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L7.1.T3 | `Abs-Coll` | | **Novel** |
**Synopsis:** The Abstraction-Collapse Duality theorem: Collapse(M) is the model whose universe is Q_M with the quotient projection as its projection operator, and the Galois insertion α_M ⊣ γ_M realises the duality α_M = π_M (abstraction = collapse) and γ_M = canonical section (concretisation = section of π_M).

**Source:** CRPT; from [`GI` (L7.1.D1)](CRPT_OMEGA_TOWER_L7.md#galois-insertion--recursive-projection-pair) + [`GC` (L7.1.T1)](CRPT_OMEGA_TOWER_L7.md#galois-connection--full-biconditional).

*Novelty Note.* **Basis (credited):** [`GI` (L7.1.D1)](CRPT_OMEGA_TOWER_L7.md#galois-insertion--recursive-projection-pair) + [`GC` (L7.1.T1)](CRPT_OMEGA_TOWER_L7.md#galois-connection--full-biconditional). **New:** The Abstraction-Collapse Duality theorem: Collapse(M) is the model whose universe is Q_M with the quotient projection as its projection operator, and the Galois insertion α_M ⊣ γ_M realises the duality α_M = π_M (abstraction = collapse) and γ_M = canonical section (concretisation = section of π_M). **Why it does not follow:** the statement is not an unfolding of the basis; the proof in the body supplies the argument that connects them.

The abstraction function α_M and collapse map π_M are complementary descriptions 
of the same quotient structure:

**(i) Abstraction as Canonical Section:**
```
α_M(x) = CFix(ρ_M)(x) [the canonical representative of π_M(x)]
```
α_M selects, from each fiber π_M⁻¹(fiber), the unique fixpoint representative in that fiber.

**(ii) Collapse as Quotient / Image Factorisation:**
```
π_M = class_map ∘ CNF_map
```
where CNF_map : ↓_M → Fix(ρ_M) is α_M, and class_map : Fix(ρ_M) → Q_M is the map
f ↦ NFC_M(f). π_M is the composition of abstraction followed by fiber classification.

**(iii) Commutative Diagram (Category-Theoretic Factorisation):**
```
↓_M ———α_M———→ Fix(ρ_M)
 | |
 | | class_map: f ↦ NFC_M(f)
 π_M ↓
 ↓ Q_M ≅ Q_M
 Q_M ————=————→ Q_M
```
(The bottom map is the identity on Q_M; α_M is injective on each ≃_M-class.)

**(iv) Semantic Equivalence:**
For any x ∈ ↓_M:
- **Trajectory view (abstraction):** Iterate ρ_M exactly d_M(x) times to reach CFix(ρ_M)(x).
- **Partition view (collapse):** Partition ↓_M into fibers {NFC_M(f) | f ∈ Fix(ρ_M)};
 x belongs to fiber NFC_M(CFix(ρ_M)(x)); multiple concrete elements x, x' in the same fiber 
 collapse to a single abstract representative CFix(ρ_M)(x) = CFix(ρ_M)(x').

*Proof.*
**(i)–(ii):** Immediate from definitions. α_M(x) = CFix(ρ_M)(x) ([`GI` (L7.1.D1)](CRPT_OMEGA_TOWER_L7.md#galois-insertion--recursive-projection-pair)). 
π_M(x) = [x]_{≃_M} = NFC_M(CFix(ρ_M)(x)) by the CNF-Fibre Theorem (7.2). ✓

**(iii):** The diagram commutes:
- Top-right-bottom: α_M(x) = CFix(ρ_M)(x), then class_map(CFix(ρ_M)(x)) = NFC_M(CFix(ρ_M)(x)) = π_M(x). ✓
- The map Fix(ρ_M) → Q_M is well-defined ([`π-Sur` (L7.1.L1)](CRPT_OMEGA_TOWER_L7.md#π_m-is-surjective--epic)): NFC_M is a bijection.
- π_M is surjective ([`π-Sur` (L7.1.L1)](CRPT_OMEGA_TOWER_L7.md#π_m-is-surjective--epic)); α_M restricted to any fiber is a injection to Fix(ρ_M). ✓

**(iv):** Semantics equivalence follows from the definitions. ∎

### Two Complementary Framings of the Same Structure
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Remark** | L7.1.R2 | `2-Frame` |  | **Novel** |
**Synopsis:** The abstraction-collapse duality can be described in two complementary framings. The abstraction framing focuses on the reduction trajectory x → ρ_M(x) → ... → CNF_M(x), treating the projection operator as a reduction strategy. The collapse framing focuses on the quotient map π_M: 𝒰_M → Q_M, treating the canonical form as an equivalence class. Both framings describe the same mathematical object — the Galois insertion — and are interchangeable for all formal purposes.

**Source:** CRPT; from [`Abs-Coll` (L7.1.T3)](CRPT_OMEGA_TOWER_L7.md#abstraction-collapse-duality--functorial-representation).

*Novelty Note.* **Basis (credited):** [`Abs-Coll` (L7.1.T3)](CRPT_OMEGA_TOWER_L7.md#abstraction-collapse-duality--functorial-representation). **New:** The abstraction-collapse duality can be described in two complementary framings. **Why it does not follow:** the stated observation is the contribution; the basis does not state it.

The abstraction-collapse duality reflects two perspectives on one object:

- **Abstraction framing (Process):** Focus on the *trajectory* x → ρ_M(x) → ··· → CFix(ρ_M)(x). 
 Here ρ_M is a reduction operator, d_M(x) is reduction depth / derivation height, and CFix(ρ_M)(x) 
 is the fixpoint reached. This framing is natural for reasoning about termination, reduction 
 strategies, and sequential computation (Baader & Nipkow [1998] ARS theory).

- **Collapse framing (Structure):** Focus on the *quotient* ↓_M ↠ Q_M. Here π_M is a 
 canonical epimorphism, the fibers ker(π_M) are the ≃_M-equivalence classes, and Q_M is 
 the set of abstraction classes. This framing is natural for reasoning about equivalences, 
 partitions, and what information is *preserved* vs. *lost* during abstraction 
 (Category Theory language: Adamek-Herrlich-Strecker [1990] §5M, Mac Lane [1998] §IV.5).

Both framings describe the same mathematical structure: the reduction relation →_ρ and the
equivalence ≃_M together induce a unique quotient structure. The six-class partition of ↓_M 
(L3.2) classifies each element by its position in this structure:
- Whether it is already a fixpoint (Q1: in Fix(ρ_M)?)
- Whether its image under ρ_M has multiple preimages (Q2: H_S(x)?) 
- Whether those preimages are distinguishable by the orbit signature (Q3: H_I(x)?)

---

## Collapse Operator and Well-Formedness

*Purpose.* This subsection establishes that the collapse operator (quotient construction)
from the abstraction-collapse duality preserves CRPT model status. That is, collapsing
a CRPT model by its observable equivalence yields another valid CRPT model.

### Collapse Operator Definition

| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L7.1.D4 | `Collapse-Def` | Collapse(M) | **Novel** |
**Synopsis:** The Collapse operator at L7: Collapse(M) is the CRPT model with universe 𝒰_M/≃_M (its convergent part is the abstraction quotient Q_M = ↓_M/≃_M), projection operator ρ_{Collapse(M)} = [ρ_M(−)] (the quotient of ρ_M), and structural relation →_σ^{Collapse} = [→_σ] (the quotient of →_σ). Collapse is the categorical left adjoint to the canonical inclusion Mod_{CRPT,WF} ↪ Mod_CRPT.

**Source:** CRPT; from [`≃_M` (L2.5.D2)](CRPT_OMEGA_TOWER_L2.md#church-rosser-orbit-equivalence-notation-_m) + [`Mod-/` (L5.1.D4)](CRPT_OMEGA_TOWER_L5.md#model-quotient-m₁).

*Novelty Note.* **Basis (credited):** [`≃_M` (L2.5.D2)](CRPT_OMEGA_TOWER_L2.md#church-rosser-orbit-equivalence-notation-_m) + [`Mod-/` (L5.1.D4)](CRPT_OMEGA_TOWER_L5.md#model-quotient-m₁). **New:** The Collapse operator at L7: Collapse(M) is the CRPT model with universe 𝒰_M/≃_M (its convergent part is the abstraction quotient Q_M = ↓_M/≃_M), projection operator ρ_{Collapse(M)} = [ρ_M(−)] (the quotient of ρ_M), and structural relation →_σ^{Collapse} = [→_σ] (the quotient of →_σ). **Why it does not follow:** the basis supplies the ingredients; the notion assembled from them, and the role it is defined to play in the theory, is introduced here rather than entailed.

For a CRPT model M, define the **collapse** of M by observable equivalence as:
```
Collapse(M) := (𝒰_M / ≃_M, →_ρ^{Collapse}, ρ_{Collapse})
```
where:
- **Universe:** 𝒰_{Collapse(M)} := 𝒰_M / ≃_M (the quotient by observable equivalence)
- **Reduction:** [x]_≃ →_ρ^{Collapse} [y]_≃ ⟺ ∃x', y' with x ≃_M x', y ≃_M y', x' →_ρ y'
- **Operator:** ρ_{Collapse}([x]_≃) := [ρ_M(x)]_≃ (well-defined by equivalence preservation of ρ_M)
- **Equivalence:** [x]_≃ ≃_{Collapse} [y]_≃ just when [x]_≃ = [y]_≃ (equality of classes, trivial)

The canonical quotient projection is:
```
κ : 𝒰_M → 𝒰_{Collapse(M)},  κ(x) := [x]_{≃_M}
```

*Regime structure of the quotient.* On ↓_M the quotient restricts to Q_M = ↓_M/≃_M; on ∞_M,
≃_M identifies persistent elements sharing a topological limit ([`CFix-NM` (L2.4.D1)](CRPT_OMEGA_TOWER_L2.md#canonical-normal-form-map--native-form)), so the
persistent part requires the topological mode (PA-WN_top). The *finer, total* persistent
abstraction is ≃∞ (the ω-limit set, [`≃∞` (L3.3.D7)](CRPT_OMEGA_TOWER_L3.md#--persistent-orbit-equivalence)) realised by the persistent Galois
insertion [`GI∞` (L7.1.D5)](CRPT_OMEGA_TOWER_L7.md#persistent-galois-insertion-α--γ); the regime-aware *complete* observable abstraction is the
semantic projection π_sem onto Sem(M) = Q_M ⊔ Q∞_M ([`Sem` (L3.3.D9)](CRPT_OMEGA_TOWER_L3.md#unified-semantic-domain-semm)). Collapse (via ≃_M) is
the topological-mode realisation of that complete abstraction; in all cases the result is
pure-WF ([`Collapse-Model` (L7.1.T4)](CRPT_OMEGA_TOWER_L7.md#collapse-is-a-crpt-model)).

### Collapse is a CRPT Model

| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L7.1.T4 | `Collapse-Model` | | **Novel** |
**Synopsis:** The Collapse Model theorem: Collapse(M) is a valid CRPT model, and it is a **pure-WF** one — every ≃_M-class is a fixpoint and ρ_{Collapse} = id. This is forced, not optional: ρ_M always preserves the canonical form / limit (ρ_M(x) ≃_M x), so the induced operator on ≃_M-classes is the identity. Collapse(M) is therefore the discrete model of M's canonical observables — the reflector onto pure-WF models ([`Collapse-Def` (L7.1.D4)](CRPT_OMEGA_TOWER_L7.md#collapse-operator-definition)). The persistent dynamics of M are not lost but *relocated* to the persistent abstraction Q∞_M via the dual Galois insertion [`GI∞` (L7.1.D5)](CRPT_OMEGA_TOWER_L7.md#persistent-galois-insertion-α--γ).

**Source:** CRPT; from [`Collapse-Def` (L7.1.D4)](CRPT_OMEGA_TOWER_L7.md#collapse-operator-definition) + [`CNF=CR` (L2.5.T2)](CRPT_OMEGA_TOWER_L2.md#cnf-fiber--church-rosser-quotient) + [`Fix=NF` (L2.1.T2)](CRPT_OMEGA_TOWER_L2.md#fix--nf).

*Novelty Note.* **Basis (credited):** [`Collapse-Def` (L7.1.D4)](CRPT_OMEGA_TOWER_L7.md#collapse-operator-definition) + [`CNF=CR` (L2.5.T2)](CRPT_OMEGA_TOWER_L2.md#cnf-fiber--church-rosser-quotient) + [`Fix=NF` (L2.1.T2)](CRPT_OMEGA_TOWER_L2.md#fix--nf). **New:** The Collapse Model theorem: Collapse(M) is a valid CRPT model, and it is a **pure-WF** one — every ≃_M-class is a fixpoint and ρ_{Collapse} = id. **Why it does not follow:** the statement is not an unfolding of the basis; the proof in the body supplies the argument that connects them.

If M is a CRPT model, then Collapse(M) is a CRPT model, and it is pure-WF
(∞_{Collapse(M)} = ∅).

**Proof.**

*Key fact (ρ_M is ≃_M-trivial).* For every x ∈ 𝒰_M, CFix(ρ_M)(ρ_M(x)) = CFix(ρ_M)(x):
on ↓_M because ρ_M(x) lies on x's orbit to the same fixpoint, and on ∞_M because ρ_M(x)
has the same orbit tail, hence the same topological limit ([`CFix-NM` (L2.4.D1)](CRPT_OMEGA_TOWER_L2.md#canonical-normal-form-map--native-form)). By
[`CNF=CR` (L2.5.T2)](CRPT_OMEGA_TOWER_L2.md#cnf-fiber--church-rosser-quotient), therefore **ρ_M(x) ≃_M x for all x**.

**Step 1: well-definedness, and ρ_{Collapse} = id.**
- ≃_M is ρ_M-compatible: if x ≃_M x' then ρ_M(x) ≃_M x ≃_M x' ≃_M ρ_M(x') (key fact +
  transitivity; equivalently C2, bisimulation equivariance, [`ρ_M` (L2.1.D1)](CRPT_OMEGA_TOWER_L2.md#projection-operator-ρ_m)). Hence
  ρ_{Collapse}([x]_≃) := [ρ_M(x)]_≃ is representative-independent.
- By the key fact, [ρ_M(x)]_≃ = [x]_≃, so **ρ_{Collapse} = id_{Q_M}**. Likewise, if
  x →_ρ y then y ≃_M x (y is on x's orbit to the same canonical form), so x and y
  fall in the **same** class. Hence **→_ρ^{Collapse} is empty** — every class is a
  fixpoint of ρ_{Collapse} = id, i.e. a normal form — and Collapse(M) is **discrete**
  (no reduction edges, not even self-loops). A reduction step of M maps under κ to an
  *equality* of classes, not an edge; this is why κ is a homomorphism only in the
  ≃-quotient category Mod_CRPT_≃ ([`Collapse-Hom` (L7.1.C4)](CRPT_OMEGA_TOWER_L7.md#quotient-projection-is-a-model-homomorphism)). ✓

**Step 2: Collapse(M) is a pure-WF CRPT model.** With ρ_{Collapse} = id, every class is a
fixpoint and a normal form: Fix(ρ_{Collapse}) = NF(→_ρ^{Collapse}) = Q_M = 𝒰_{Collapse(M)}.

(i) **PA-WN.** Every element is already its own normal form: ρ_{Collapse}^0([x]_≃) =
[x]_≃ ∈ Fix(ρ_{Collapse}), so d_{Collapse} ≡ 0. ✓
(ii) **PA-Conf.** ρ_{Collapse} = id is a total deterministic function and →_ρ^{Collapse}
has only self-loops, so confluence is trivial. ✓
(iii) **PA-Fix.** ρ_{Collapse}([x]_≃) = [x]_≃ for every class, and every class is a normal
form (only self-loops); hence ρ_{Collapse}([x]) = [x] ⟺ NF([x]), i.e.
Fix(ρ_{Collapse}) = NF(→_ρ^{Collapse}) ([`Fix=NF` (L2.1.T2)](CRPT_OMEGA_TOWER_L2.md#fix--nf)). ✓
(iv) **PA-NWF — not inherited, by design.** Since ρ_{Collapse} = id, no class has a
non-terminating orbit: ∞_{Collapse(M)} = ∅. Collapse abstracts *every* orbit —
convergent or persistent — to its canonical observable (its ≃_M-class), so Collapse(M)
is **pure-WF**. This is exactly the reflector property of [`Collapse-Def` (L7.1.D4)](CRPT_OMEGA_TOWER_L7.md#collapse-operator-definition):
Collapse is left adjoint to the inclusion Mod_{CRPT,WF} ↪ Mod_CRPT, hence valued in
pure-WF models. The persistent content of M is *relocated*, not destroyed: it is recorded
in the persistent abstraction Q∞_M ([`Q∞` (L3.3.D8)](CRPT_OMEGA_TOWER_L3.md#persistent-orbit-quotient-q_m)) through the dual Galois insertion
[`GI∞` (L7.1.D5)](CRPT_OMEGA_TOWER_L7.md#persistent-galois-insertion-α--γ), and the complete observable abstraction of M is the regime-aware
semantic projection onto Sem(M) = Q_M ⊔ Q∞_M ([`Sem` (L3.3.D9)](CRPT_OMEGA_TOWER_L3.md#unified-semantic-domain-semm)).
(v) **PA-Prod, PA-WN_top, PA-Reach** are vacuous (∞_{Collapse(M)} = ∅: their persistent
antecedents are never met). **PA-CoInd** holds: with ∞_{Collapse(M)} = ∅ the greatest
fixpoint of the persistence functional is empty, satisfied vacuously (and, in full SOL,
it follows from PA-NWF's vacuous truth via [`Ax-Ind` (L1.6.T1)](CRPT_OMEGA_TOWER_L1.md#axiom-independence)). **PA-Bisim** holds: with
ρ_{Collapse} = id, bisimilarity ≈ coincides with class equality = ≃_{Collapse}, so
x ≈ y ⟹ x ≃_{Collapse} y trivially. ✓

Therefore Collapse(M) is a CRPT model, and a pure-WF one. ∎

### Degenerate Horizons of the Collapse

| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Remark** | L7.1.R3 | `Collapse-DegHor` | | **Derived** |
**Synopsis:** Why Collapse(M) has degenerate (Class E only) horizons.

**Source:** CRPT; from [`Collapse-Model` (L7.1.T4)](CRPT_OMEGA_TOWER_L7.md#collapse-is-a-crpt-model) + [`GI∞` (L7.1.D5)](CRPT_OMEGA_TOWER_L7.md#persistent-galois-insertion-α--γ).

*Derivation:* composed from [`Collapse-Model` (L7.1.T4)](CRPT_OMEGA_TOWER_L7.md#collapse-is-a-crpt-model) + [`GI∞` (L7.1.D5)](CRPT_OMEGA_TOWER_L7.md#persistent-galois-insertion-α--γ); no content beyond the composition.

Because Collapse(M) is discrete
(every class an isolated fixpoint), its horizon structure is degenerate: the six-class
partition (L3.2) reduces to **Class E** (the fixpoints) alone. This is consistent with
Collapse being the *maximal* abstraction — it retains the canonical observables and
discards all orbit dynamics. The discarded orbit/horizon information of M is preserved
elsewhere: in Sem(M) ([`Sem` (L3.3.D9)](CRPT_OMEGA_TOWER_L3.md#unified-semantic-domain-semm)) and, for the persistent regime, in the AOI
hierarchy ([`AOI-Unif` (L6.3.D10)](CRPT_OMEGA_TOWER_L6.md#unified-aoi)).

### Quotient Projection is a Model Homomorphism

| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Corollary** | L7.1.C4 | `Collapse-Hom` | | **Derived** |
**Synopsis:** The Collapse Homomorphism theorem: the quotient map κ : 𝒰_M → Q_M is a CRPT homomorphism from M to Collapse(M) **in the ≃-quotient category Mod_CRPT_≃** ([`Mod-Cat-Q` (L7.2.T1)](CRPT_OMEGA_TOWER_L7.md#mod_crpt-is-a-category-with--quotient-hom-sets)), where Φ_R is interpreted up to ≃. Since Collapse(M) is discrete (ρ_{Collapse} = id, no reduction edges), a reduction step x →_ρ y maps to the *equality* κ(x) = κ(y) — because y ≃_M x — which satisfies Φ_R up to ≃ without requiring a literal edge. κ is the canonical surjective collapse homomorphism.

**Source:** CRPT; from [`Collapse-Def` (L7.1.D4)](CRPT_OMEGA_TOWER_L7.md#collapse-operator-definition) + [`Hom` (L5.2.D1)](CRPT_OMEGA_TOWER_L5.md#model-homomorphism-φ--m₁--m₂) + [`Mod-Cat-Q` (L7.2.T1)](CRPT_OMEGA_TOWER_L7.md#mod_crpt-is-a-category-with--quotient-hom-sets).

*Derivation:* composed from [`Collapse-Def` (L7.1.D4)](CRPT_OMEGA_TOWER_L7.md#collapse-operator-definition) + [`Hom` (L5.2.D1)](CRPT_OMEGA_TOWER_L5.md#model-homomorphism-φ--m₁--m₂) + [`Mod-Cat-Q` (L7.2.T1)](CRPT_OMEGA_TOWER_L7.md#mod_crpt-is-a-category-with--quotient-hom-sets); no content beyond the composition.

The quotient projection κ : M → Collapse(M), κ(x) = [x]_{≃_M}, is a morphism in Mod_CRPT_≃.

**Proof (in Mod_CRPT_≃, [`Mod-Cat-Q` (L7.2.T1)](CRPT_OMEGA_TOWER_L7.md#mod_crpt-is-a-category-with--quotient-hom-sets), where the morphism conditions are read up to ≃).**
- **(κ_R, up to ≃):** If x →_ρ y in M, then y ≃_M x (the reduct lies on x's orbit to the same canonical form, under PA-Conf / orbit confluence), so κ(x) = [x]_≃ = [y]_≃ = κ(y). The up-to-≃ relation-preservation condition — κ(x) →_ρ^{Collapse} κ(y) **or** κ(x) ≃_{Collapse} κ(y) — holds because κ(x) = κ(y). (Collapse(M) is discrete: ρ_{Collapse} = id and there are no literal →_ρ^{Collapse} edges, so Φ_R can only be met up to ≃, the morphism-equality convention of [`Mod-Cat-Q` (L7.2.T1)](CRPT_OMEGA_TOWER_L7.md#mod_crpt-is-a-category-with--quotient-hom-sets).)
- **(κ_E):** If x ≃_M y, then [x]_≃ = [y]_≃ in Collapse(M) — trivially ≃_{Collapse}-equivalent. ✓
- **(κ_ρ):** κ(ρ_M(x)) = [ρ_M(x)]_≃ = [x]_≃ = ρ_{Collapse}([x]_≃) = ρ_{Collapse}(κ(x)) (using ρ_M(x) ≃_M x and ρ_{Collapse} = id). ✓
- **(κ_LA):** the image of each local axiom of M is consistent with the local-axiom set of the discrete Collapse(M). ✓

Hence κ is a morphism in Mod_CRPT_≃ — the canonical surjective collapse homomorphism. The strict-Φ_R reading is recovered only on the trivial part (classes with no internal reduction); on classes that absorb a reduction step, Φ_R holds up to ≃, never as a literal self-loop. ∎

### Persistent Galois Insertion

The WF Galois insertion [`GI` (L7.1.D1)](CRPT_OMEGA_TOWER_L7.md#galois-insertion--recursive-projection-pair) abstracts the convergent regime onto its canonical
forms, α_M : ↓_M → Fix(ρ_M). Collapse(M) showed that on the *convergent* regime this is the
whole story (ρ_{Collapse} = id). The persistent regime carries its own dual abstraction,
onto the persistent canonical classes.

### Persistent Galois Insertion α∞ ⊣ γ∞
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L7.1.D5 | `GI∞` | α∞_M ⊣ γ∞_M | **Novel** |
**Synopsis:** The persistent dual of the Galois insertion [`GI` (L7.1.D1)](CRPT_OMEGA_TOWER_L7.md#galois-insertion--recursive-projection-pair): α∞ abstracts each persistent element to its ω-limit class (its ≃∞-class in Q∞_M), and γ∞ selects a representative orbit. It is the ∞_M-regime abstraction; together with α_M on ↓_M it assembles into the regime-aware semantic projection π_sem onto Sem(M).

**Source:** CRPT; persistent dual of [`GI` (L7.1.D1)](CRPT_OMEGA_TOWER_L7.md#galois-insertion--recursive-projection-pair); from [`≃∞` (L3.3.D7)](CRPT_OMEGA_TOWER_L3.md#--persistent-orbit-equivalence) + [`Q∞` (L3.3.D8)](CRPT_OMEGA_TOWER_L3.md#persistent-orbit-quotient-q_m) + [`Sem` (L3.3.D9)](CRPT_OMEGA_TOWER_L3.md#unified-semantic-domain-semm).

*Novelty Note.* **Basis (credited):** [`GI` (L7.1.D1)](CRPT_OMEGA_TOWER_L7.md#galois-insertion--recursive-projection-pair) + [`≃∞` (L3.3.D7)](CRPT_OMEGA_TOWER_L3.md#--persistent-orbit-equivalence) + [`Q∞` (L3.3.D8)](CRPT_OMEGA_TOWER_L3.md#persistent-orbit-quotient-q_m) + [`Sem` (L3.3.D9)](CRPT_OMEGA_TOWER_L3.md#unified-semantic-domain-semm). **New:** The persistent dual of the Galois insertion [`GI` (L7.1.D1)](CRPT_OMEGA_TOWER_L7.md#galois-insertion--recursive-projection-pair): α∞ abstracts each persistent element to its ω-limit class (its ≃∞-class in Q∞_M), and γ∞ selects a representative orbit. **Why it does not follow:** the basis supplies one side; the counterpart it names is built where that machinery is absent — the construction itself is the content.

Define
```
α∞_M : ∞_M → Q∞_M      α∞_M(x) := ω_≈(x) = [x]_{≃∞}     [persistent abstraction / upper adjoint]
γ∞_M : Q∞_M → ∞_M      γ∞_M(q) := a chosen orbit representative x_q with ω_≈(x_q) = q
                                                          [persistent concretisation / lower adjoint]
```
(γ∞ exists by surjectivity of the quotient map x ↦ ω_≈(x); a section is a choice of one
representative per ≃∞-class.) The pair (α∞, γ∞) is a **persistent Galois insertion**
between (∞_M, ≃∞-preorder) and (Q∞_M, =), the exact ∞_M-dual of α_M ⊣ γ_M onto Fix(ρ_M).

*Full abstraction.* The convergent abstraction α_M ([`GI` (L7.1.D1)](CRPT_OMEGA_TOWER_L7.md#galois-insertion--recursive-projection-pair)) and the persistent
abstraction α∞ together are the regime-aware semantic projection
π_sem = α_M ⊔ α∞ : 𝒰_M → Q_M ⊔ Q∞_M = Sem(M) ([`Sem` (L3.3.D9)](CRPT_OMEGA_TOWER_L3.md#unified-semantic-domain-semm)). Collapse(M) is the image of
α_M; the persistent content abstracted away by Collapse is precisely the image of α∞.

### Persistent Galois Connection
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L7.1.T5 | `GC∞` | | **Novel** |
**Synopsis:** The persistent Galois insertion satisfies the three adjunction identities dual to `GC1`–`GC3` (L7.1.C1–C3): α∞ ∘ γ∞ = id (retraction), γ∞ ∘ α∞ ⊒ id in the ≃∞-preorder (unit), and α∞ preserves ≃∞. By [`SC-Imp` (L6.3.T1)](CRPT_OMEGA_TOWER_L6.md#single-class-impossibility) the *complete* persistent abstraction is graded: GC∞ is the ≃∞ (ω-limit) level, refined by the AOI hierarchy.

**Source:** CRPT; from [`GI∞` (L7.1.D5)](CRPT_OMEGA_TOWER_L7.md#persistent-galois-insertion-α--γ) + [`≃∞-Eq` (L3.3.T5)](CRPT_OMEGA_TOWER_L3.md#-is-an-equivalence-relation); persistent dual of [`GC` (L7.1.T1)](CRPT_OMEGA_TOWER_L7.md#galois-connection--full-biconditional).

*Novelty Note.* **Basis (credited):** [`GI∞` (L7.1.D5)](CRPT_OMEGA_TOWER_L7.md#persistent-galois-insertion-α--γ) + [`≃∞-Eq` (L3.3.T5)](CRPT_OMEGA_TOWER_L3.md#-is-an-equivalence-relation) + [`GC` (L7.1.T1)](CRPT_OMEGA_TOWER_L7.md#galois-connection--full-biconditional). **New:** The persistent Galois insertion satisfies the three adjunction identities dual to `GC1`–`GC3` (L7.1.C1–C3): α∞ ∘ γ∞ = id (retraction), γ∞ ∘ α∞ ⊒ id in the ≃∞-preorder (unit), and α∞ preserves ≃∞. **Why it does not follow:** the dual side lacks the original's machinery, so the duality is constructed rather than transported; the proof in the body builds the replacement.

(i) **Retraction (dual of [`GC1` (L7.1.C1)](CRPT_OMEGA_TOWER_L7.md#gc1--retraction)):** α∞_M ∘ γ∞_M = id_{Q∞_M}.
(ii) **Unit (dual of [`GC2` (L7.1.C2)](CRPT_OMEGA_TOWER_L7.md#gc2--upper-adjunction)):** x ≃∞ γ∞_M(α∞_M(x)) for all x ∈ ∞_M.
(iii) **Equivalence preservation (dual of [`GC3` (L7.1.C3)](CRPT_OMEGA_TOWER_L7.md#gc3--preserves-equivalence)):** x ≃∞ y ⟹ α∞_M(x) = α∞_M(y).

*Proof.* (i) For q ∈ Q∞_M, γ∞(q) = x_q with ω_≈(x_q) = q; then α∞(γ∞(q)) = ω_≈(x_q) = q. ✓
(ii) γ∞(α∞(x)) = x_{[x]} with ω_≈(x_{[x]}) = ω_≈(x), i.e. x ≃∞ γ∞(α∞(x)) by [`≃∞` (L3.3.D7)](CRPT_OMEGA_TOWER_L3.md#--persistent-orbit-equivalence). ✓
(iii) x ≃∞ y ⟺ ω_≈(x) = ω_≈(y) ([`≃∞` (L3.3.D7)](CRPT_OMEGA_TOWER_L3.md#--persistent-orbit-equivalence)), i.e. α∞(x) = α∞(y). ✓
The three identities are the verbatim ∞_M-duals of `GC1`–`GC3` (L7.1.C1–C3), with Fix(ρ_M)
replaced by Q∞_M and ≃_M by ≃∞. ∎

### Graded Abstraction

| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Remark** | L7.1.R4 | `Graded-Abs` | | **Derived** |
**Synopsis:** Why a single Galois insertion cannot give the complete persistent abstraction.

**Source:** CRPT; from [`GC∞` (L7.1.T5)](CRPT_OMEGA_TOWER_L7.md#persistent-galois-connection) + [`SC-Imp` (L6.3.T1)](CRPT_OMEGA_TOWER_L6.md#single-class-impossibility).

*Derivation:* composed from [`GC∞` (L7.1.T5)](CRPT_OMEGA_TOWER_L7.md#persistent-galois-connection) + [`SC-Imp` (L6.3.T1)](CRPT_OMEGA_TOWER_L6.md#single-class-impossibility); no content beyond the composition.

On ↓_M the
Galois insertion lands on the *complete* invariant (CFix; [`CNF=CR` (L2.5.T2)](CRPT_OMEGA_TOWER_L2.md#cnf-fiber--church-rosser-quotient)). On ∞_M,
[`SC-Imp` (L6.3.T1)](CRPT_OMEGA_TOWER_L6.md#single-class-impossibility) shows no single bisimulation-invariant is complete, so α∞ — which lands
on the ω-limit class ≃∞ — captures only the *asymptotic-support* level. The complete
persistent abstraction is therefore a **graded family** of insertions, one per level of the
AOI hierarchy ([`AOI-Unif` (L6.3.D10)](CRPT_OMEGA_TOWER_L6.md#unified-aoi)), with α∞ its base (≃∞) rung. This is the
Galois-theoretic shadow of the graded WF/NWF duality ([`WF-NWF-Dual` (L3.3.T9)](CRPT_OMEGA_TOWER_L3.md#wfnwf-canonical-form-duality)): a single
insertion on the convergent side, a graded family on the persistent side.

---

## L7.2 — CRPT's Own Structure is Categorical

This section is a **self-application**: it turns CRPT's own machinery on CRPT itself. The
objects are CRPT models, the morphisms are CRPT homomorphisms, and the operators are CRPT's
own projection-derived constructs — `ρ_M`, Collapse (the ≃_M-quotient), and Lift (the free
extension). We show that *these* assemble, with no imported structure, into a category
(`Mod_CRPT`), an ω-category (the tower), an adjoint pair (`Lift ⊣ Collapse`), and a functor
(`F`). The conclusion is that CRPT is **intrinsically categorical**: its categoricity is a
theorem *about* CRPT, generated by recursive projection, not a foundation CRPT is built upon.

The category-theoretic vocabulary (Mac Lane, Cousot, Ore, Birkhoff) is used only to *name*
the structures ρ_M already produces — it supplies standard terminology, not authority or
prior assumptions. (Exhibiting category theory itself as a CRPT *model* is a separate
matter, handled by instantiation, not here; L7's claim is solely about CRPT's own structure.)

### The Category of CRPT Models

### Category Mod_CRPT
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L7.2.D1 | `Mod_CRPT` | Mod_CRPT | **Novel** |
**Synopsis:** The category Mod_CRPT at L7: objects are CRPT models (substrates satisfying the PA-* axioms), morphisms are CRPT homomorphisms (functions satisfying Φ_R, Φ_E, Φ_ρ, Φ_LA). The categorical structure — identity, composition, associativity — is verified here using the Galois insertion and quotient constructions of L7.1.

**Source:** CRPT; from [`Hom` (L5.2.D1)](CRPT_OMEGA_TOWER_L5.md#model-homomorphism-φ--m₁--m₂) + [`CRPT-Mod-18` (L5.1.D1)](CRPT_OMEGA_TOWER_L5.md#crpt-model).

*Novelty Note.* **Basis (credited):** [`Hom` (L5.2.D1)](CRPT_OMEGA_TOWER_L5.md#model-homomorphism-φ--m₁--m₂) + [`CRPT-Mod-18` (L5.1.D1)](CRPT_OMEGA_TOWER_L5.md#crpt-model). **New:** The category Mod_CRPT at L7: objects are CRPT models (substrates satisfying the PA-* axioms), morphisms are CRPT homomorphisms (functions satisfying Φ_R, Φ_E, Φ_ρ, Φ_LA). **Why it does not follow:** the basis supplies the ingredients; the notion assembled from them, and the role it is defined to play in the theory, is introduced here rather than entailed.

The category Mod_CRPT has:

A model may satisfy any subset of {PA-WN, PA-Conf, PA-Fix, PA-NWF, PA-CoInd, PA-Prod, PA-WN_top, PA-Bisim, PA-Reach}, or none.

**Morphisms:** A model homomorphism Φ : M₁ → M₂ is exactly a CRPT homomorphism in the canonical sense of [`Hom` (L5.2.D1)](CRPT_OMEGA_TOWER_L5.md#model-homomorphism-φ--m₁--m₂) — a function Φ : 𝒰_{M₁} → 𝒰_{M₂} satisfying its four conditions:
- **Φ_R (Relation preservation):** x →_ρ y ⟹ Φ(x) →_ρ Φ(y)
- **Φ_E (Equivalence preservation):** x ≃_{M₁} y ⟹ Φ(x) ≃_{M₂} Φ(y)
- **Φ_ρ (Strategy compatibility):** Φ(ρ_{M₁}(x)) ≃_{M₂} ρ_{M₂}(Φ(x))
- **Φ_LA (Local-axiom compatibility):** the pushforward of each local axiom of M₁ is consistent with LA_{M₂} ([`Hom` (L5.2.D1)](CRPT_OMEGA_TOWER_L5.md#model-homomorphism-φ--m₁--m₂))

(The canonical homomorphism imposes no separate →_σ-preservation condition.)

**Composition:** (Ψ ∘ Φ)(x) := Ψ(Φ(x)) 
**Identity:** id_M(x) := x

### Mod_CRPT is a Category (with ≃-Quotient Hom-Sets)
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L7.2.T1 | `Mod-Cat-Q` |  | **Novel** |
**Synopsis:** That Mod_CRPT is a category — objects CRPT models, morphisms CRPT homomorphisms, with identities, associativity, and closure under composition — is proved in full at [`Mod-Cat` (L5.2.T1)](CRPT_OMEGA_TOWER_L5.md#crpt-models-form-category-mod_crpt) and is not repeated here. L7's added content is the morphism-equality convention the functorial layer requires: hom-sets are taken up to ≃-pointwise equality (Φ ≈ Φ′ iff Φ(x) ≃ Φ′(x) for all x). This relation is a congruence for composition (via Φ_E), so it yields a well-defined quotient category Mod_CRPT_≃ in which ρ-preservation (Φ_ρ) and the Lift ⊣ Collapse triangle identities ([`Lift⊣Coll` (L7.2.T4)](CRPT_OMEGA_TOWER_L7.md#lift--collapse-is-an-adjoint-pair)) hold as strict equalities, not merely up to ≃.

**Source:** CRPT; from [`Mod-Cat` (L5.2.T1)](CRPT_OMEGA_TOWER_L5.md#crpt-models-form-category-mod_crpt) + [`Hom` (L5.2.D1)](CRPT_OMEGA_TOWER_L5.md#model-homomorphism-φ--m₁--m₂) + [`≃_M` (L2.5.D2)](CRPT_OMEGA_TOWER_L2.md#church-rosser-orbit-equivalence-notation-_m).

*Novelty Note.* **Basis (credited):** [`Mod-Cat` (L5.2.T1)](CRPT_OMEGA_TOWER_L5.md#crpt-models-form-category-mod_crpt) + [`Hom` (L5.2.D1)](CRPT_OMEGA_TOWER_L5.md#model-homomorphism-φ--m₁--m₂) + [`≃_M` (L2.5.D2)](CRPT_OMEGA_TOWER_L2.md#church-rosser-orbit-equivalence-notation-_m). **New:** That Mod_CRPT is a category — objects CRPT models, morphisms CRPT homomorphisms, with identities, associativity, and closure under composition — is proved in full at [`Mod-Cat` (L5.2.T1)](CRPT_OMEGA_TOWER_L5.md#crpt-models-form-category-mod_crpt) and is not repeated here. **Why it does not follow:** the statement is not an unfolding of the basis; the proof in the body supplies the argument that connects them.

That Mod_CRPT is a category — identities, closure under composition, associativity — is established with full proof at [`Mod-Cat` (L5.2.T1)](CRPT_OMEGA_TOWER_L5.md#crpt-models-form-category-mod_crpt) (the category laws verified there directly from Φ_R, Φ_E, Φ_ρ, Φ_LA). We do not duplicate it. What the categorical layer of L7 additionally needs is that the hom-sets carry a well-behaved equivalence under which the projection-compatibility condition Φ_ρ — stated only up to ≃ — and the adjunction of [`Lift⊣Coll` (L7.2.T4)](CRPT_OMEGA_TOWER_L7.md#lift--collapse-is-an-adjoint-pair) become strict. That is the content established here.

**Morphism equality up to ≃.** For homomorphisms Φ, Φ′ : M₁ → M₂ define
```
Φ ≈ Φ′  :⟺  ∀x ∈ 𝒰_{M₁} : Φ(x) ≃_{M₂} Φ′(x).
```

*Proof (≈ is a composition congruence).* On each hom-set, ≈ is reflexive, symmetric, and transitive because ≃_{M₂} is an equivalence relation ([`≃-Eq` (L2.5.T1)](CRPT_OMEGA_TOWER_L2.md#_m-is-an-equivalence-relation)). For congruence under composition, let Φ ≈ Φ′ : M₁ → M₂ and Ψ ≈ Ψ′ : M₂ → M₃. For every x ∈ 𝒰_{M₁}:
- Ψ(Φ(x)) ≃_{M₃} Ψ(Φ′(x)), applying Ψ's equivalence-preservation Φ_E to Φ(x) ≃_{M₂} Φ′(x);
- Ψ(Φ′(x)) ≃_{M₃} Ψ′(Φ′(x)), by Ψ ≈ Ψ′ instantiated at the point Φ′(x).

By transitivity of ≃_{M₃}, Ψ(Φ(x)) ≃_{M₃} Ψ′(Φ′(x)); since x was arbitrary, Ψ ∘ Φ ≈ Ψ′ ∘ Φ′. Hence ≈ descends to composition, and the quotient category **Mod_CRPT_≃** — same objects, hom-sets Hom(M₁,M₂)/≈ — is well-defined. ∎

*Consequence.* In Mod_CRPT_≃, Φ_ρ reads ρ̄_{M₂} ∘ Φ̄ = Φ̄ ∘ ρ̄_{M₁} as a strict equality of morphisms (the witnessing ≃ is quotiented away), and the unit/counit triangle identities of [`Lift⊣Coll` (L7.2.T4)](CRPT_OMEGA_TOWER_L7.md#lift--collapse-is-an-adjoint-pair) hold as equalities. Mod_CRPT_≃ is the category in which the functorial results of L7.2–L7.3 are stated.

### ω-Categories and Natural Transformations

### ω-Category in CRPT
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L7.2.D2 | `ω-Cat` | C^ω_CRPT | **Imported** |
**Synopsis:** The tower Tower(M₀) carries an ω-category structure: the tower levels are 0-cells, the Lift maps Mₙ → Mₙ₊₁ are 1-cells, natural transformations between Lift maps are 2-cells, and so on for each finite dimension. This infinite-dimensional categorical structure organises the tower's levels into a coherent whole.

**Source:** Street [1987], *The algebra of oriented simplexes*, J. Pure Appl. Algebra 49; Ehresmann [1965]; Leinster [2004] *Higher Operads* §7.1.

An ω-category is a sequence:
```
C = (D⁰, D¹, D², ..., {F_n : D_n → D_{n+1}}_{n≥0})
```
where each Dⁿ is a model, each F_n : Dⁿ → Dⁿ⁺¹ is a model homomorphism, and the sequence extends infinitely for all n ∈ ℕ.

The Dⁿ are the **layers** or **dimensions** of the ω-category (corresponding to rank levels in the Free Lift tower).

### Natural Transformation between ω-Categories
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L7.2.D3 | `η-Nat` | η: F₁→F₂ | **Imported** |
**Synopsis:** A natural transformation η : F ⟹ G between CRPT functors assigns to each CRPT model M a CRPT homomorphism η_M : F(M) → G(M) such that for every CRPT homomorphism φ : M → N, G(φ) ∘ η_M = η_N ∘ F(φ). Natural transformations are the 2-cells of the ω-category structure on the tower.

**Source:** Mac Lane [1998] *Categories for the Working Mathematician* §II.4 — natural transformations.

Given ω-categories C and C', a natural transformation η : C ⇒ C' is a family {η_n : M^n → M'^n}_{n≥0} of model homomorphisms such that for all n ≥ 0, the following diagrams commute (up to ≃ equivalence):

```
M^n ----F_n----> M^{n+1}
 | |
 |η_n |η_{n+1}
 v v
M'^n ---F'_n---> M'^{n+1}
```

That is: η_{n+1} ∘ F_n ≃ F'_n ∘ η_n.

### Composition of Natural Transformations
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L7.2.T2 | `η-Comp` |  | **Imported** |
**Synopsis:** Vertical composition of natural transformations: if η : F ⟹ G and ε : G ⟹ H, their vertical composite ε ∘ η : F ⟹ H is defined component-wise as (ε ∘ η)_M = ε_M ∘ η_M. This standard categorical operation is verified to produce a CRPT natural transformation.

**Source:** Mac Lane [1998] *Categories for the Working Mathematician* §II.4 — vertical composition of natural transformations.

If η : C ⇒ C' and μ : C' ⇒ C'' are natural transformations between ω-categories, then (μ ∘ η)_n := μ_n ∘ η_n : M^n → M''^n is a natural transformation C ⇒ C''.

*Proof.* Naturality of each component follows from composition of model homomorphisms. ✓ ∎

### The Free Lift as a Functor

### Free Lift Functor Lift : Mod_CRPT → Mod_CRPT
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L7.2.D4 | `Lift-F` | Lift | **Novel** |
**Synopsis:** The Lift Functor at L7: the Lift operator is an endofunctor on Mod_CRPT mapping each model M to Lift(M) and each homomorphism φ : M₁ → M₂ to Lift(φ) : Lift(M₁) → Lift(M₂). Functoriality — Lift(id) = id and Lift(ψ ∘ φ) = Lift(ψ) ∘ Lift(φ) — is verified from the free monoidal algebra construction.

**Source:** CRPT; from [`FMA` (L8.1.D1)](CRPT_OMEGA_TOWER_L8.md#free-monoidal-algebra-fmaa) + [`Lift-Def` (L8.2.D2)](CRPT_OMEGA_TOWER_L8.md#free-lift-of-m).

*Novelty Note.* **Basis (credited):** [`FMA` (L8.1.D1)](CRPT_OMEGA_TOWER_L8.md#free-monoidal-algebra-fmaa) + [`Lift-Def` (L8.2.D2)](CRPT_OMEGA_TOWER_L8.md#free-lift-of-m). **New:** The Lift Functor at L7: the Lift operator is an endofunctor on Mod_CRPT mapping each model M to Lift(M) and each homomorphism φ : M₁ → M₂ to Lift(φ) : Lift(M₁) → Lift(M₂). **Why it does not follow:** the basis supplies the ingredients; the notion assembled from them, and the role it is defined to play in the theory, is introduced here rather than entailed.

For a model M = (𝒰_M, →_ρ, →_σ, ρ_M), the **free lift** is:

```
Lift(M) := (FMA(Q_M), →_ρ^{Lift}, →_σ^{Lift}, ρ_{Lift(M)})
```

where:
- Q_M := ↓_M / ≃_M (the quotient of convergent elements by equivalence; see L7.2)
- FMA(Q_M) is the free monoidal algebra on Q_M (generators: elements of Q_M; composite terms: products)
- →_ρ^{Lift} is left-stripping: t₁ · t₂ →_ρ t₁ (and atomic terms have no outgoing edges)
- →_σ^{Lift} := →_ρ^{Lift} ∪ {left-right commutativity: (t₁·t₂) ↔ (t₂·t₁)}
- ρ_{Lift(M)} iteratively left-strips: ρ_{Lift(M)}(t₁ · t₂) := t₁, and ρ_{Lift(M)}(a) := a for atomic a

(Full definition: see L7.3–27.4.)

### Lift is an Endofunctor on Mod_CRPT
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L7.2.T3 | `Lift-Endo` | | **Novel** |
**Synopsis:** The Lift operator is an endofunctor on Mod_CRPT: it maps models to models (proved in L8.3) and maps CRPT homomorphisms φ : M₁ → M₂ to CRPT homomorphisms Lift(φ) : Lift(M₁) → Lift(M₂) by acting on the free monoidal algebra generators. Functoriality (Lift(id) = id, Lift(ψ ∘ φ) = Lift(ψ) ∘ Lift(φ)) is verified.

**Source:** CRPT; from [`Lift-F` (L7.2.D4)](CRPT_OMEGA_TOWER_L7.md#free-lift-functor-lift--mod_crpt--mod_crpt) + [`FMA` (L8.1.D1)](CRPT_OMEGA_TOWER_L8.md#free-monoidal-algebra-fmaa).

*Novelty Note.* **Basis (credited):** [`Lift-F` (L7.2.D4)](CRPT_OMEGA_TOWER_L7.md#free-lift-functor-lift--mod_crpt--mod_crpt) + [`FMA` (L8.1.D1)](CRPT_OMEGA_TOWER_L8.md#free-monoidal-algebra-fmaa). **New:** The Lift operator is an endofunctor on Mod_CRPT: it maps models to models (proved in L8.3) and maps CRPT homomorphisms φ : M₁ → M₂ to CRPT homomorphisms Lift(φ) : Lift(M₁) → Lift(M₂) by acting on the free monoidal algebra generators. **Why it does not follow:** the statement is not an unfolding of the basis; the proof in the body supplies the argument that connects them.

For any model M ∈ Ob(Mod_CRPT), we have Lift(M) ∈ Ob(Mod_CRPT). Moreover, Lift extends to morphisms: if Φ : M₁ → M₂, then Lift(Φ) : Lift(M₁) → Lift(M₂) defined by:
```
Lift(Φ)(a) := atom(Φ(a)) [for atomic a ∈ Q_{M₁}]
Lift(Φ)(t₁ · t₂) := Lift(Φ)(t₁) · Lift(Φ)(t₂) [for composites]
```
is a model homomorphism, with Lift(id_M) = id_{Lift(M)} and Lift(Ψ ∘ Φ) = Lift(Ψ) ∘ Lift(Φ).

*Proof.* 
- FMA(Q_{M₁}) is inductively generated; extension by structure-recursion is well-defined.
- Φ_R: if t = s₁ · s₂ →_ρ s₁ = t', then Lift(Φ)(t) = Lift(Φ)(s₁) · Lift(Φ)(s₂) →_ρ Lift(Φ)(s₁) = Lift(Φ)(t'). ✓
- Φ_ρ: for atomic a, Lift(Φ)(ρ_{Lift(M₁)}(a)) = Lift(Φ)(a) = atom(Φ(a)) ≃ ρ_{Lift(M₂)}(atom(Φ(a))) = ρ_{Lift(M₂)}(Lift(Φ)(a)). ✓
- Functoriality: identity and composition preserved by induction. ✓ ∎

### The Collapse Functor and Adjoint Pair

### Collapse Functor Collapse : Mod_CRPT → Mod_CRPT
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L7.2.D5 | `Coll-F` | Collapse | **Novel** |
**Synopsis:** The Collapse functor maps each CRPT model M to its collapsed model Collapse(M) = Q_M (the abstraction quotient with quotient projection as projection operator) and maps each CRPT homomorphism φ : M₁ → M₂ to the induced map Collapse(φ) : Q_{M₁} → Q_{M₂}. Collapse is the right adjoint to Lift in the Lift ⊣ Collapse adjunction.

**Source:** CRPT; from [`Collapse-Def` (L7.1.D4)](CRPT_OMEGA_TOWER_L7.md#collapse-operator-definition).

*Novelty Note.* **Basis (credited):** [`Collapse-Def` (L7.1.D4)](CRPT_OMEGA_TOWER_L7.md#collapse-operator-definition). **New:** The Collapse functor maps each CRPT model M to its collapsed model Collapse(M) = Q_M (the abstraction quotient with quotient projection as projection operator) and maps each CRPT homomorphism φ : M₁ → M₂ to the induced map Collapse(φ) : Q_{M₁} → Q_{M₂}. **Why it does not follow:** the basis supplies the ingredients; the notion assembled from them, and the role it is defined to play in the theory, is introduced here rather than entailed.

For a model M:
```
Collapse(M) := M / ≃_M
```
the quotient model obtained by identifying all ρ_M-equivalent elements into equivalence classes.

Formally: 𝒰_{Collapse(M)} := {[x]_{≃_M} : x ∈ 𝒰_M}; [x] →_ρ [y] iff ∃x' ∈ [x], y' ∈ [y] : x' →_ρ y'; ρ_{Collapse(M)}([x]) := [ρ_M(x)].

### Lift ⊣ Collapse is an Adjoint Pair
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L7.2.T4 | `Lift⊣Coll` |  | **Derived** |
**Synopsis:** Lift ⊣ Collapse adjunction: the free-lift functor is left adjoint to the collapse functor, with natural bijection Mod_CRPT(Lift(M), M′) ≅ Mod_CRPT(M, Collapse(M′)). Lifting then collapsing recovers the original model up to observational equivalence.

**Source:** CRPT; from [`Lift-F` (L7.2.D4)](CRPT_OMEGA_TOWER_L7.md#free-lift-functor-lift--mod_crpt--mod_crpt) + [`Coll-F` (L7.2.D5)](CRPT_OMEGA_TOWER_L7.md#collapse-functor-collapse--mod_crpt--mod_crpt).

*Derivation:* composed from [`Lift-F` (L7.2.D4)](CRPT_OMEGA_TOWER_L7.md#free-lift-functor-lift--mod_crpt--mod_crpt) + [`Coll-F` (L7.2.D5)](CRPT_OMEGA_TOWER_L7.md#collapse-functor-collapse--mod_crpt--mod_crpt); no content beyond the composition.

The functors Lift and Collapse form an adjoint pair Lift ⊣ Collapse, with natural bijection:

```
Mod_CRPT(M, Collapse(M')) ≅ Mod_CRPT(Lift(M), M')
```

natural in both M and M'.

*Proof.* 

**Unit η_M : M → Collapse(Lift(M)):** For each x ∈ 𝒰_M, under PA-WN + PA-Conf, x has a unique normal form CFix(ρ_M)(x) ∈ Q_M. Define η_M(x) := [atom(CFix(ρ_M)(x))]_{≃}, the equivalence class containing the atom corresponding to x's normal form.

**Counit ε_M : Lift(Collapse(M)) → M:** For a term t ∈ FMA(Q_{Collapse(M)}), define ε_M by structural recursion:
- Atoms: ε_M(atom([x])) := x (pick a representative of the equivalence class [x])
- Composites: ε_M(t₁ · t₂) := ε_M(t₁) (reverse the left-strip by taking left component)

Well-definedness on equivalence classes follows from the fact that all representatives of [x] are ≃-equivalent.

**Triangle identities:** (These are stated in the quotient category Mod_CRPT_≃ of [`Mod-Cat-Q` (L7.2.T1)](CRPT_OMEGA_TOWER_L7.md#mod_crpt-is-a-category-with--quotient-hom-sets), where hom-sets are taken up to ≃-pointwise equality. There the identities hold as strict equalities of morphisms, using CFix(ρ_M)(x) ≃_M x — equivalently [CFix(ρ_M)(x)]_{≃_M} = [x]_{≃_M}.)

1. **Left triangle:** ε_M ∘ Lift(η_M) = id_M.
 - For x ∈ 𝒰_M: Lift(η_M)(atom(x)) = atom(η_M(x)) = atom([atom(CFix(ρ_M)(x))])
 - Then ε_M(atom([atom(CFix(ρ_M)(x))])) = CFix(ρ_M)(x).
 - Since CFix(ρ_M)(x) ≃_M x, in the quotient category [CFix(ρ_M)(x)] = [x], so this is id_M on [x]. ✓

2. **Right triangle:** Collapse(ε_M) ∘ η_{Collapse(M)} = id_{Collapse(M)}.
 - For [x] ∈ 𝒰_{Collapse(M)}: η_{Collapse(M)}([x]) = [atom(CNF_{Collapse(M)}([x]))]
 - Collapse(ε_M)([atom(CNF_{Collapse(M)}([x]))]) = [ε_M(atom(CNF_{Collapse(M)}([x])))]
 - Since Collapse(M) = M/≃_M, CNF on the quotient maps each class to itself, giving id_{Collapse(M)} on [x]. ✓

**Naturality:** For all morphisms Φ : M → M' and ψ : Collapse(M') → M'', the diagrams involving η and ε commute naturally. ✓

Therefore Lift ⊣ Collapse. ∎

### Scope of the Two Collapse Adjunctions
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Remark** | L7.2.R1 | `Coll-Adj-Scope` |  | **Novel** |
**Synopsis:** Collapse carries two compatible adjoint roles, stated precisely. It is the *reflector* onto pure-WF models (Collapse ⊣ ι, left adjoint to the inclusion Mod_{CRPT,WF} ↪ Mod_CRPT, [`Collapse-Def` (L7.1.D4)](CRPT_OMEGA_TOWER_L7.md#collapse-operator-definition)) and the *right* adjoint of the free-lift functor (Lift ⊣ Collapse, [`Lift⊣Coll` (L7.2.T4)](CRPT_OMEGA_TOWER_L7.md#lift--collapse-is-an-adjoint-pair)). A functor may be simultaneously a left and a right adjoint to different functors; there is no conflict. Both adjunctions are stated in the ≃-quotient category Mod_CRPT_≃ ([`Mod-Cat-Q` (L7.2.T1)](CRPT_OMEGA_TOWER_L7.md#mod_crpt-is-a-category-with--quotient-hom-sets)), where the triangle identities are strict.

**Source:** CRPT; from [`Collapse-Model` (L7.1.T4)](CRPT_OMEGA_TOWER_L7.md#collapse-is-a-crpt-model) + [`Lift⊣Coll` (L7.2.T4)](CRPT_OMEGA_TOWER_L7.md#lift--collapse-is-an-adjoint-pair) + [`Mod-Cat-Q` (L7.2.T1)](CRPT_OMEGA_TOWER_L7.md#mod_crpt-is-a-category-with--quotient-hom-sets).

*Novelty Note.* **Basis (credited):** [`Collapse-Model` (L7.1.T4)](CRPT_OMEGA_TOWER_L7.md#collapse-is-a-crpt-model) + [`Lift⊣Coll` (L7.2.T4)](CRPT_OMEGA_TOWER_L7.md#lift--collapse-is-an-adjoint-pair) + [`Mod-Cat-Q` (L7.2.T1)](CRPT_OMEGA_TOWER_L7.md#mod_crpt-is-a-category-with--quotient-hom-sets). **New:** Collapse carries two compatible adjoint roles, stated precisely. **Why it does not follow:** the stated observation is the contribution; the basis does not state it.

Three points make the categorical placement exact:

1. **Corestriction.** By [`Collapse-Model` (L7.1.T4)](CRPT_OMEGA_TOWER_L7.md#collapse-is-a-crpt-model) every Collapse(M) is pure-WF, so Collapse
factors through the inclusion as a functor Collapse : Mod_CRPT_≃ → Mod_{CRPT,WF}. The
adjunction [`Lift⊣Coll` (L7.2.T4)](CRPT_OMEGA_TOWER_L7.md#lift--collapse-is-an-adjoint-pair) is the **free ⊣ forgetful** adjunction for this
corestriction: Lift(M) = FMA(Q_M) is free on the observables Q_M, and Collapse forgets a
model to its observable (pure-WF) reflection. The natural bijection
Mod(Lift M, M′) ≅ Mod(M, Collapse M′) is freeness of FMA composed with the discreteness of
Collapse M′.

2. **Reflection.** The same Collapse, viewed as Mod_CRPT_≃ → Mod_{CRPT,WF} ↪ Mod_CRPT, is the
reflector Collapse ⊣ ι: the unit κ : M → Collapse(M) ([`Collapse-Hom` (L7.1.C4)](CRPT_OMEGA_TOWER_L7.md#quotient-projection-is-a-model-homomorphism)) is the
universal arrow to a pure-WF model. Left-adjoint-to-ι and right-adjoint-to-Lift are distinct
statements about distinct functor pairs, both true.

3. **Strictness.** Both adjunctions live in Mod_CRPT_≃ ([`Mod-Cat-Q` (L7.2.T1)](CRPT_OMEGA_TOWER_L7.md#mod_crpt-is-a-category-with--quotient-hom-sets)); the
up-to-≃ unit/counit of [`Lift⊣Coll` (L7.2.T4)](CRPT_OMEGA_TOWER_L7.md#lift--collapse-is-an-adjoint-pair) are equalities there, so the triangle
identities are strict and the adjunctions are honest (not merely bicategorical). ∎

### Regime Invariance of Categorical Structures
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Remark** | L7.2.R2 | `Reg-Inv` |  | **Novel** |
**Synopsis:** The Lift ⊣ Collapse adjunction holds in both the WF and NWF settings without modification. The adjunction is regime-invariant: whether models have persistent elements or not, the unit and counit of the adjunction are defined the same way and satisfy the triangle identities. The categorical machinery of L7.2 is regime-oblivious.

**Source:** CRPT; from [`Lift⊣Coll` (L7.2.T4)](CRPT_OMEGA_TOWER_L7.md#lift--collapse-is-an-adjoint-pair).

*Novelty Note.* **Basis (credited):** [`Lift⊣Coll` (L7.2.T4)](CRPT_OMEGA_TOWER_L7.md#lift--collapse-is-an-adjoint-pair). **New:** The Lift ⊣ Collapse adjunction holds in both the WF and NWF settings without modification. **Why it does not follow:** the stated observation is the contribution; the basis does not state it.

**Category-Theoretic Regime Invariance.**
The functorial structures (adjoints, natural transformations, ω-categories) are regime-invariant in the native framework:

- **Lift functor:** Preserve regime partition. If M = ↓_M ∐ ∞_M, then Lift(M) = ↓_{Lift(M)} ∐ ∞_{Lift(M)} with canonical maps between regimes.
- **Collapse functor:** Regime-*aware* abstraction (not regime-preserving). Collapse applies the ≃_M-quotient uniformly across ↓_M and ∞_M, abstracting convergent orbits to fixpoints (α_M) and persistent orbits to their ω-limit classes (α∞, [`GI∞` (L7.1.D5)](CRPT_OMEGA_TOWER_L7.md#persistent-galois-insertion-α--γ)); the result Collapse(M) is itself **pure-WF** ([`Collapse-Model` (L7.1.T4)](CRPT_OMEGA_TOWER_L7.md#collapse-is-a-crpt-model)). The persistent content is retained in Q∞_M / Sem(M), not in Collapse(M)'s dynamics.
- **Adjoint pair:** The adjunction Lift ⊣ Collapse holds in the native setting whether elements are finitely convergent or topologically persistent.
- **Natural transformations:** Unit η and counit ε are regime-agnostic; they commute with projection to/from ↓_M and ∞_M.

This means the categorical machinery (§L7.1–30) operates identically regardless of whether models include a topological component or not. The tower (L8.1) is regime-oblivious: it automatically handles both classical and analytic models without modification.

---

## L7.3 — The CRPT Functor and Tower Structure

### The CRPT Functor: Definition and Functoriality

### The CRPT Functor F
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L7.3.D1 | `F-CRPT` | F | **Novel** |
**Synopsis:** The CRPT functor F : Mod_CRPT → ω-Cat sends each CRPT model M to its tower Tower(M) viewed as an ω-category (with Lift maps as 1-cells, natural transformations as 2-cells, etc.) and sends each CRPT homomorphism φ : M₁ → M₂ to the tower-level-wise induced functor Tower(φ).

**Source:** CRPT; from [`Lift-F` (L7.2.D4)](CRPT_OMEGA_TOWER_L7.md#free-lift-functor-lift--mod_crpt--mod_crpt) + [`ω-Cat` (L7.2.D2)](CRPT_OMEGA_TOWER_L7.md#ω-category-in-crpt).

*Novelty Note.* **Basis (credited):** [`Lift-F` (L7.2.D4)](CRPT_OMEGA_TOWER_L7.md#free-lift-functor-lift--mod_crpt--mod_crpt) + [`ω-Cat` (L7.2.D2)](CRPT_OMEGA_TOWER_L7.md#ω-category-in-crpt). **New:** The CRPT functor F : Mod_CRPT → ω-Cat sends each CRPT model M to its tower Tower(M) viewed as an ω-category (with Lift maps as 1-cells, natural transformations as 2-cells, etc.) and sends each CRPT homomorphism φ : M₁ → M₂ to the tower-level-wise induced functor Tower(φ). **Why it does not follow:** the basis supplies the ingredients; the notion assembled from them, and the role it is defined to play in the theory, is introduced here rather than entailed.

Define F : Mod_CRPT → ωCat (where ωCat is the category of ω-categories with natural transformations) as:

**On objects:** For M ∈ Ob(Mod_CRPT):
```
F(M) := (M, Lift(M), Lift²(M), Lift³(M), ..., {Lift : Lift^n(M) → Lift^{n+1}(M)}_{n≥0})
```
the **tower** (infinite sequence) generated by iterated application of Lift.

**On morphisms:** For a model homomorphism Φ : M₁ → M₂, define the natural transformation:
```
F(Φ) : F(M₁) ⇒ F(M₂)
```
with components F(Φ)_n := Lift^n(Φ) : Lift^n(M₁) → Lift^n(M₂) (iterated application of Lift to Φ).

### F is a Functor Mod_CRPT → ωCat
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L7.3.T1 | `F-Func` | | **Novel** |
**Synopsis:** The CRPT functor F : Mod_CRPT → ω-Cat is a genuine functor — it preserves identities (F(id_M) = id) and composition (F(ψ ∘ φ) = F(ψ) ∘ F(φ)), which follows from the levelwise functoriality of Lift on the tower.

**Source:** CRPT; from [`F-CRPT` (L7.3.D1)](CRPT_OMEGA_TOWER_L7.md#the-crpt-functor-f) + [`Lift-Endo` (L7.2.T3)](CRPT_OMEGA_TOWER_L7.md#lift-is-an-endofunctor-on-mod_crpt).

*Novelty Note.* **Basis (credited):** [`F-CRPT` (L7.3.D1)](CRPT_OMEGA_TOWER_L7.md#the-crpt-functor-f) + [`Lift-Endo` (L7.2.T3)](CRPT_OMEGA_TOWER_L7.md#lift-is-an-endofunctor-on-mod_crpt). **New:** The CRPT functor F : Mod_CRPT → ω-Cat is a genuine functor — it preserves identities (F(id_M) = id) and composition (F(ψ ∘ φ) = F(ψ) ∘ F(φ)), which follows from the levelwise functoriality of Lift on the tower. **Why it does not follow:** the statement is not an unfolding of the basis; the proof in the body supplies the argument that connects them.

The assignment F : M ↦ F(M) and Φ ↦ F(Φ) defines a functor.

*Proof.*
- **F(M) is an ω-category:** Each F(M) is an ordered sequence of models with morphisms Lift^n : Lift^n(M) → Lift^{n+1}(M). ✓

- **F(Φ) is a natural transformation:** For each n, the diagrams commute:
 ```
 Lift^n(M₁) --Lift^n--> Lift^{n+1}(M₁)
 | |
 |Lift^n(Φ) |Lift^{n+1}(Φ)
 v v
 Lift^n(M₂) --Lift^n--> Lift^{n+1}(M₂)
 ```
 This follows because Lift^{n+1}(Φ) = Lift(Lift^n(Φ)) and Lift is a functor, so composition is preserved. ✓

- **Functoriality:**
 - F(id_M)_n = Lift^n(id_M) = id_{Lift^n(M)}. ✓
 - F(Ψ ∘ Φ)_n = Lift^n(Ψ ∘ Φ) = Lift^n(Ψ) ∘ Lift^n(Φ) = F(Ψ)_n ∘ F(Φ)_n. ✓

Therefore F : Mod_CRPT → ωCat is a functor. ∎

### Tower Functoriality: Morphisms Induce Natural Transformations

### Tower Functoriality
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L7.3.T2 | `Twr-Func` |  | **Novel** |
**Synopsis:** Tower functoriality: if Φ : M₁ → M₂ is a CRPT homomorphism, the induced maps Φₙ := Lift^n(Φ) : Lift^n(M₁) → Lift^n(M₂) form a natural transformation F(Φ) : F(M₁) ⇒ F(M₂) between the tower ω-categories. The tower construction is functorial: it commutes with model homomorphisms.

**Source:** CRPT; from [`Lift-Endo` (L7.2.T3)](CRPT_OMEGA_TOWER_L7.md#lift-is-an-endofunctor-on-mod_crpt).

*Novelty Note.* **Basis (credited):** [`Lift-Endo` (L7.2.T3)](CRPT_OMEGA_TOWER_L7.md#lift-is-an-endofunctor-on-mod_crpt). **New:** Tower functoriality: if Φ : M₁ → M₂ is a CRPT homomorphism, the induced maps Φₙ := Lift^n(Φ) : Lift^n(M₁) → Lift^n(M₂) form a natural transformation F(Φ) : F(M₁) ⇒ F(M₂) between the tower ω-categories. **Why it does not follow:** the statement is not an unfolding of the basis; the proof in the body supplies the argument that connects them.

Let Φ : M₁ → M₂ be a model homomorphism. Then the family {Φ_n := Lift^n(Φ) : Lift^n(M₁) → Lift^n(M₂)}_{n≥0} forms a natural transformation F(Φ) : F(M₁) ⇒ F(M₂) between the ω-categories F(M₁) and F(M₂).

*Proof.* Each Φ_n is a model homomorphism (by [`Lift-Endo` (L7.2.T3)](CRPT_OMEGA_TOWER_L7.md#lift-is-an-endofunctor-on-mod_crpt)). Naturality (commutativity of tower diagrams) follows from functoriality of Lift. ✓ ∎

### Model Isomorphisms Induce Omega-Category Isomorphisms
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Corollary** | L7.3.C1 | `Iso-ωCat` |  | **Derived** |
**Synopsis:** Tower isomorphism corollary: if Φ : M₁ → M₂ is a CRPT model isomorphism, then F(Φ) : F(M₁) → F(M₂) is an isomorphism of tower ω-categories. Isomorphic base models produce isomorphic towers. This confirms that the tower invariants are genuine model invariants.

**Source:** CRPT; corollary of [`Twr-Func` (L7.3.T2)](CRPT_OMEGA_TOWER_L7.md#tower-functoriality).

*Derivation:* composed from [`Twr-Func` (L7.3.T2)](CRPT_OMEGA_TOWER_L7.md#tower-functoriality); no content beyond the composition.

If Φ : M₁ → M₂ is a model isomorphism (bijective, with Φ_R, Φ_E, Φ_ρ as equalities), then F(Φ) : F(M₁) → F(M₂) is an isomorphism of ω-categories (each component Φ_n is a model isomorphism).

*Proof.* Bijectivity of Φ is preserved under Lift: Lift(Φ) is bijective iff Φ is bijective (FMA structure is preserved). By induction, all Φ_n are bijective. The preservation conditions are inherited through functoriality. ✓ ∎

**Application.** The model isomorphisms of L5.2 are established only on the finite/discrete
restricted models — [`Φ_ZC` (L5.2.T2)](CRPT_OMEGA_TOWER_L5.md#φ_zc--zfc-to-category-theory-restricted): ZFC_finite ≅ Cat_discrete, [`Φ_CH` (L5.2.T3)](CRPT_OMEGA_TOWER_L5.md#φ_ch--category-theory-to-hott-restricted):
Cat_discrete ≅ HoTT_discrete, and their composite [`Φ_ZH` (L5.2.T4)](CRPT_OMEGA_TOWER_L5.md#φ_zh-by-composition): ZFC_finite ≅
HoTT_discrete. Applying the corollary to exactly those isomorphisms gives tower isomorphisms
over the restricted models:
```
F(Φ_ZC) : Tower(ZFC_finite)  ≅ Tower(Cat_discrete)
F(Φ_CH) : Tower(Cat_discrete) ≅ Tower(HoTT_discrete)
F(Φ_ZH) : Tower(ZFC_finite)  ≅ Tower(HoTT_discrete)
```
So the finite/discrete fragments of these foundations generate isomorphic towers level by
level, not merely isomorphic base models. This is *not* a claim about the unrestricted
foundational systems: extending it to full ZFC, full category theory, or full HoTT requires
each as a complete CRPT tower model, which is separate work and is not assumed here. (In
particular Cat_discrete is the discrete-category fragment that L5.2.T2 constructs — not the
full category-theory model.)

### Self-Application and Consistency

### Self-Application is Consistent
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L7.3.T3 | `Self-App` |  | **Novel** |
**Synopsis:** The CRPT functor F is self-applicable: F can be applied to the meta-model Mod_CRPT itself (treating Mod_CRPT as a CRPT model under its dependency structure) to produce F(Mod_CRPT), an ω-category of increasingly abstract model categorisations. No circularity arises because the dependency structure is acyclic and well-founded.

**Source:** CRPT; from [`F-Func` (L7.3.T1)](CRPT_OMEGA_TOWER_L7.md#f-is-a-functor-mod_crpt--ωcat) + acyclicity/well-foundedness of the dependency relation (cf. [`CRPT-Acyclic` (Lω.7.L1)](CRPT_OMEGA_TOWER_Lω.md#lω7l1--crpt-acyclic-the-self-reduction-is-acyclic)).

*Novelty Note.* **Basis (credited):** [`F-Func` (L7.3.T1)](CRPT_OMEGA_TOWER_L7.md#f-is-a-functor-mod_crpt--ωcat) + [`CRPT-Acyclic` (Lω.7.L1)](CRPT_OMEGA_TOWER_Lω.md#lω7l1--crpt-acyclic-the-self-reduction-is-acyclic). **New:** The CRPT functor F is self-applicable: F can be applied to the meta-model Mod_CRPT itself (treating Mod_CRPT as a CRPT model under its dependency structure) to produce F(Mod_CRPT), an ω-category of increasingly abstract model categorisations. **Why it does not follow:** the statement is not an unfolding of the basis; the proof in the body supplies the argument that connects them.

The category Mod_CRPT itself may be viewed as a meta-model. When F is applied to this meta-model, F(Mod_CRPT) generates a well-defined ω-category of increasingly abstract categorizations of models.

This self-application creates no circularity because:

1. **Rank separation:** The category Mod_CRPT itself occupies rank 0 of the meta-hierarchy. Lift(Mod_CRPT) is at rank 1, etc.

2. **Acyclicity:** The dependency relation on 𝒰_{Mod_CRPT} is acyclic—every element ultimately depends on primitive axioms and definitions, not on itself.

3. **Termination:** Every element of 𝒰_{Mod_CRPT} reaches a canonical normal form in finitely many ρ_M-steps under the meta-reduction relation.

*Proof.* Items (1)–(3) are exactly the well-foundedness and non-circularity conditions
required for self-application of F to define a valid higher-level model category.
Hence self-application is consistent under these conditions. ✓ ∎

### Model Theories as Fibers of a Fibration

### Model Theory Fibration
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Definition** | L7.3.D2 | `Mod-Fib` | π_CRPT | **Novel** |
**Synopsis:** The model-theory fibration: the CRPT functor F is a fibration over ω-Cat. The fiber over a tower ω-category T is the class of all CRPT models M with F(M) ≅ T. Different domain instantiations (set theory, type theory, process algebra) are different fibers of the same fibration — they have the same tower structure but different base models.

**Source:** CRPT; from [`F-Func` (L7.3.T1)](CRPT_OMEGA_TOWER_L7.md#f-is-a-functor-mod_crpt--ωcat).

*Novelty Note.* **Basis (credited):** [`F-Func` (L7.3.T1)](CRPT_OMEGA_TOWER_L7.md#f-is-a-functor-mod_crpt--ωcat). **New:** The model-theory fibration: the CRPT functor F is a fibration over ω-Cat. **Why it does not follow:** the basis supplies the ingredients; the notion assembled from them, and the role it is defined to play in the theory, is introduced here rather than entailed.

Consider the category Base of specific CRPT models to be classified. The CRPT functor induces a **fibration**:

```
π : ωCat_CRPT → Base
```

where ωCat_CRPT is the full subcategory of ωCat consisting of towers generated by F instantiated on base models.

The **fiber over a point M ∈ Base** is:
```
π⁻¹(M) := {F(M), and all compatible towers}
```
the collection of all ω-categories related to the instantiation of CRPT on model M.

### Model Theories as Fiber Objects
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Theorem** | L7.3.T4 | `Mod-Fib-T` |  | **Novel** |
**Synopsis:** The fibration theorem: each model instantiation Φ : M₁ → M₂ (a homomorphism between instantiations) is a fiber map in the model-theory fibration. The natural transformation F(Φ) : F(M₁) ⇒ F(M₂) witnesses the fact that different domain theories with compatible reduction structures share tower-level structure.

**Source:** CRPT; from [`Mod-Fib` (L7.3.D2)](CRPT_OMEGA_TOWER_L7.md#model-theory-fibration) + [`F-Func` (L7.3.T1)](CRPT_OMEGA_TOWER_L7.md#f-is-a-functor-mod_crpt--ωcat).

*Novelty Note.* **Basis (credited):** [`Mod-Fib` (L7.3.D2)](CRPT_OMEGA_TOWER_L7.md#model-theory-fibration) + [`F-Func` (L7.3.T1)](CRPT_OMEGA_TOWER_L7.md#f-is-a-functor-mod_crpt--ωcat). **New:** The fibration theorem: each model instantiation Φ : M₁ → M₂ (a homomorphism between instantiations) is a fiber map in the model-theory fibration. **Why it does not follow:** the statement is not an unfolding of the basis; the proof in the body supplies the argument that connects them.

Each model instantiation is not a separate theoretical framework—it is the **fiber F(M)** where M is the specific model.

Multiple model instantiations are **related by natural transformations**: if Φ : M₁ → M₂ is a model homomorphism (relating two instantiations via a common reduction structure), then F(Φ) : F(M₁) ⇒ F(M₂) is a natural transformation at all levels of the respective towers.

*Proof.* Immediate from [`F-Func` (L7.3.T1)](CRPT_OMEGA_TOWER_L7.md#f-is-a-functor-mod_crpt--ωcat) and [`Mod-Fib` (L7.3.D2)](CRPT_OMEGA_TOWER_L7.md#model-theory-fibration). ✓ ∎

### Unified Architecture
| Type | Label | Tag | Notation | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Remark** | L7.3.R1 | `Unif-Arch` |  | **Novel** |
**Synopsis:** The self-application of the CRPT functor at the meta-level anticipates Lω: applying F to the self-substrate 𝒰_CRPT (the collection of all tower constructs under their dependency relation) produces a tower whose fixed point is 𝒰_CRPT itself. This remark foreshadows the self-consistency fixed point theorem of Lω.5.

**Source:** CRPT; from [`F-CRPT` (L7.3.D1)](CRPT_OMEGA_TOWER_L7.md#the-crpt-functor-f); foreshadows the Lω self-consistency fixed point.

*Novelty Note.* **Basis (credited):** [`F-CRPT` (L7.3.D1)](CRPT_OMEGA_TOWER_L7.md#the-crpt-functor-f). **New:** The self-application of the CRPT functor at the meta-level anticipates Lω: applying F to the self-substrate 𝒰_CRPT (the collection of all tower constructs under their dependency relation) produces a tower whose fixed point is 𝒰_CRPT itself. **Why it does not follow:** the stated observation is the contribution; the basis does not state it.

All model instantiations follow the **same pattern** (apply the same functor F). All relationships are captured by **natural transformations** (model homomorphisms inducing morphisms of towers). The theoretical machinery is **unified**: one functor F.

To instantiate CRPT to a new model M, one provides:
1. An encoding of M as a model (define 𝒰_M, →_ρ, →_σ, ρ_M)
2. Verification of any desired axioms (PA-WN, PA-Conf, etc.)
3. Identification of key reduction relations and normal forms
4. The tower F(M) and its classification (six-class partition, observable triple, etc.) follow automatically.

This is theoretically more elegant and computationally more systematic than maintaining separate model-specific theories.

---
