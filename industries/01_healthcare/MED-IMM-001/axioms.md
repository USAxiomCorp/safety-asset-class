# Immune Axiom Registry (Aimm)
## Constitutional Mathematics + WAD Arithmetic Form

---

## READ ME (Human‑Readable Summary)

This file defines the **mathematical rules** an immune (IMM) state must satisfy to be considered **constitutionally admissible**.

The immune system is modeled as:

- an **innate response manifold** (pattern recognition, inflammation, complement)  
- an **adaptive response manifold** (T cells, B cells, antigen specificity)  
- a **tolerance manifold** (self‑recognition, regulatory circuits)  
- a **cytokine‑network manifold** (signaling topology, gradients, cascades)  
- an **antigen‑processing manifold** (presentation, affinity, clearance)  

This file uses:

- **Constitutional Mathematics** to define the IMM manifold  
- **WAD Arithmetic** to measure deviation from canonical immune states  
- **R3 recursion** to guarantee convergence to a valid immune fixed point  
- **Mathematical safety** (unsafe states cannot exist in the manifold)  

If an immune state violates ANY axiom below, it is **non‑existent** in the constitutional system.

---

## FORMAL DEFINITIONS

Let:

- \( S_{\text{imm}} \subset \mathbb{R}^n \) — immune state manifold  
- \( s \in S_{\text{imm}} \) — a specific immune state  
- \( F_{\text{imm}} \) — set of admissible immune fixed points  

Weighted Absolute Deviation (WAD):

\[
\text{WAD}(s, s') = \sum_{i=1}^{n} w_i \cdot |s_i - s'_i|
\]

---

# Axiom IMM1 — Innate Response Invariance

Let \( i(s) \) be the innate response subvector.

1. Consistency:
\[
\text{WAD}(i(s), i_{\text{ref}}) \le \varepsilon_{\text{innate}}
\]

2. If violated:
\[
s \notin S_{\text{imm}}
\]

---

# Axiom IMM2 — Adaptive Response Determinism

Let \( a(s) \) be the adaptive response subvector.

1. Nearest canonical adaptive class:
\[
\ell = \arg\min_{k \in L_{\text{adaptive}}} \text{WAD}(a(s), a_k)
\]

2. Threshold:
\[
\text{WAD}(a(s), a_\ell) \le \varepsilon_{\text{adaptive}}
\]

---

# Axiom IMM3 — Tolerance Consistency

Let \( t(s) \) be the tolerance subvector (self‑recognition, regulatory circuits).

1. Tolerance mapping:
\[
t(s) = f_{\text{tolerance}}(i(s), a(s))
\]

2. Bound:
\[
\text{WAD}(t(s), t_{\text{ref}}) \le \varepsilon_{\text{tolerance}}
\]

---

# Axiom IMM4 — Cytokine‑Network Equilibrium

Let \( c(s) \) be the cytokine‑network subvector.

1. Equilibrium class:
\[
\ell = \arg\min_{k \in L_{\text{cytokine}}} \text{WAD}(c(s), c_k)
\]

2. Threshold:
\[
\text{WAD}(c(s), c_\ell) \le \varepsilon_{\text{cytokine}}
\]

If violated:
\[
s \notin S_{\text{imm}}
\]

---

# Axiom IMM5 — Antigen‑Processing Coherence

Let \( p(s) \) be the antigen‑processing subvector.

1. Coupling condition:
\[
\text{WAD}(p(s), a(s)) \le \varepsilon_{\text{antigen}}
\]

2. If mismatch exceeds tolerance:
\[
s \notin S_{\text{imm}}
\]

---

# Axiom IMM6 — R3‑Invariance of Immune Identity

Let \( \iota(s) \) be the immune identity subvector.

1. Identity class:
\[
\iota(s) = \arg\min_{k \in I_{\text{imm}}} \text{WAD}(\iota(s), \iota_k)
\]

2. R3 invariance:
If \( s^* = \lim_{k\to\infty} R3^k(s_0) \), then:
\[
\iota(s_0) = \iota(s^*)
\]

---

# Axiom IMM7 — Global Immune Admissibility

A state \( s \) is admissible iff:

1. \( s \in S_{\text{imm}} \)  
2. IMM1–IMM6 all hold  
3. Global bound:
\[
\text{WAD}(s, s_{\text{ref}}) \le \varepsilon_{\text{imm}}
\]

---

# CSL Hook Definition

For any evaluated immune state \( s \):

- **csl_event** = "imm_axiom_e
