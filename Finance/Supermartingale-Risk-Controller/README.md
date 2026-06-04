# Supermartingale Risk Controller (SMRC)

The Supermartingale Risk Controller is a RUAX-compliant financial intelligence module that enforces a non-increasing risk envelope over time for a controlled economic variable \(X_t\).

It implements the supermartingale condition introduced in Russell, “Constitutional Axiomatic Intelligence (CAI): The Russell Unified Axiomatic Stack” (SSRN-6875078, June 1, 2026):

\[
\mathbb{E}[X_{t+1} \mid \mathcal{F}_t] \le X_t
\]

## Purpose

- **Bound risk:** Ensure expected future risk never exceeds current risk.
- **Enforce hard limits:** Clamp all updates between \(X_{\min}\) and \(X_{\max}\).
- **Guarantee admissibility:** Reject any transition that violates the supermartingale or bounds.
- **Support RUAX deployments:** Plug directly into on-chain financial systems as a constitutional risk primitive.

## Controlled Variable

- \(X_t\): WAD-scaled risk metric (e.g., leverage ratio, VaR proxy, exposure index).

## Guarantees

- Expected future risk is non-increasing.
- All updates respect constitutional bounds.
- All transitions are admissibility-gated and auditable.
