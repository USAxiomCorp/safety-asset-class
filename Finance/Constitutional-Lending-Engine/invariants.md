# Constitutional Lending Engine — Invariants

These invariants MUST hold for every lending transition evaluated by the CLE.  
If any invariant is violated, the transition is unconstitutional and MUST revert.

---

## I1 — Collateral Sufficiency
\[
\text{collateral\_value}(L) \ge \text{required\_collateral}(L)
\]

No loan may proceed unless collateral fully satisfies the constitutional minimum.

---

## I2 — Leverage Ceiling
\[
\text{post\_leverage}(L) \le \text{max\_leverage}
\]

The lending action must not push the borrower above the constitutional leverage limit.

---

## I3 — Jurisdiction Compatibility
\[
\text{jurisdiction\_hash} = \text{asset\_jurisdiction\_hash}
\]

Borrower and asset must share jurisdictional alignment.

---

## I4 — Supermartingale Risk Bound
\[
X_{t+1} \le X_t
\]

The lending action must not increase systemic or portfolio risk.

---

## I5 — Deterministic Admissibility
\[
A(L) = 1 \iff \bigwedge_{i=1}^{4} d_i(L) = 1
\]

All predicates must return 1 for the transition to be admissible.

---

## I6 — Immutable Audit Trail
Every approved lending action MUST emit an immutable audit entry containing:

- borrower identifier  
- asset identifier  
- predicate results  
- updated state variables  
- timestamp  

---

## I7 — Fixed-Point Convergence
Repeated lending actions under CLE must converge toward a stable constitutional state \(X^*\) when combined with SMRC modules.

This ensures long-term systemic stability.
