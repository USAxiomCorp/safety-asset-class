# Renal Constitutional Constraints (CREN)
## Constitutional Mathematics + WAD Arithmetic Form

---

## READ ME (Human‑Readable Summary)

These are the **mathematical constraints** that define the **admissible region** of the renal manifold.

They are NOT:

- policy rules  
- heuristics  
- filters  
- interpretations  

They ARE:

- **WAD‑based inequalities**  
- **canonical bounds**  
- **set membership conditions**  
- **mathematical safety envelopes**  

If a renal state violates a constraint, it is **non‑existent** in the constitutional system.

---

# FORMAL DEFINITIONS

Let:

- \( S_{\text{ren}} \subset \mathbb{R}^n \) — renal state manifold  
- \( s \in S_{\text{ren}} \) — renal state  
- \( f(s) \) — filtration  
- \( e(s) \) — electrolytes  
- \( a(s) \) — acid–base  
- \( v(s) \) — volume–pressure  
- \( c(s) \) — clearance  
- \( \varepsilon_* \) — constitutional tolerances  

Weighted Absolute Deviation (WAD):

\[
\text{WAD}(x, y) = \sum_{i=1}^{n} w_i |x_i - y_i|
\]

---

# CREN‑1 — Filtration Constraint

\[
\text{WAD}(f(s), f_{\text{ref}}) \le \varepsilon_{\text{filtration}}
\]

If violated:

\[
s \notin S_{\text{ren}}
\]

---

# CREN‑2 — Electrolyte Constraint

Let:

\[
\ell = \arg\min_{k \in L_{\text{electrolyte}}} \text{WAD}(e(s), e_k)
\]

Constraint:

\[
\text{WAD}(e(s), e_\ell) \le \varepsilon_{\text{electrolyte}}
\]

If violated:

\[
e(s) = \text{undefined}
\]

and therefore:

\[
s \notin S_{\text{ren}}
\]

---

# CREN‑3 — Acid–Base Constraint

\[
\text{WAD}(a(s), a_{\text{ref}}) \le \varepsilon_{\text{acidbase}}
\]

If violated:

\[
a(s) \notin S_{\text{ren}}
\]

---

# CREN‑4 — Volume–Pressure Coupling Constraint

\[
\text{WAD}(v(s), f(s)) \le \varepsilon_{\text{volume}}
\]

If violated:

\[
s \notin S_{\text{ren}}
\]

This enforces **RAAS/ADH coherence**.

---

# CREN‑5 — Clearance Identity Constraint

Let:

\[
c(s) = \arg\min_{k \in I_{\text{clearance}}} \text{WAD}(c(s), c_k)
\]

Constraint:

\[
\text{WAD}(c(s), c_k) \le \varepsilon_{\text{clearance}}
\]

If violated:

\[
c(s) = \text{undefined}
\]

and thus:

\[
s \notin S_{\text{ren}}
\]

---

# CREN‑6 — R3 Convergence Constraint

Let:

\[
s^* = \lim_{k\to\infty} R3^k(s_0)
\]

Constraint:

\[
s^* \in F_{\text{ren}}
\]

If R3 cannot converge:

\[
s_0 \notin S_{\text{ren}}
\]

---

# CREN‑
