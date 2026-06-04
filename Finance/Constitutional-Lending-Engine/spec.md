# Constitutional Lending Engine — Specification

The Constitutional Lending Engine (CLE) evaluates all lending actions through a deterministic admissibility gate composed of RUAX predicates. A lending transition is only permitted if all predicates return 1.

---

## 1. State Variables

- `collateral_value` — on-chain valuation of posted collateral.
- `required_collateral` — minimum collateral required for the loan.
- `post_leverage` — leverage ratio after the proposed loan.
- `max_leverage` — constitutional leverage ceiling.
- `jurisdiction_hash` — borrower jurisdiction identifier.
- `asset_jurisdiction_hash` — asset jurisdiction identifier.
- `Xt` — current risk metric (WAD).
- `Xt+1` — proposed risk metric after loan.

---

## 2. Predicate Definitions

### 2.1 Collateral Predicate
d1(L) = 1  iff  collateral_value(L) ≥ required_collateral(L)
### 2.2 Leverage Predicate
d2(L) = 1  iff  post_leverage(L) ≤ max_leverage
### 2.3 Jurisdiction Predicate
d3(L) = 1  iff  jurisdiction_hash == asset_jurisdiction_has
### 2.4 Risk Predicate (Supermartingale)h
d4(L) = 1  iff  Xt+1 ≤ Xt
---

## 3. Admissibility Gate

A lending action is admissible iff:

\[
A(L) = d_1(L) \land d_2(L) \land d_3(L) \land d_4(L)
\]

If \(A(L) = 0\), the transaction MUST revert.

---

## 4. Outputs

- `approved = true/false`
- `audit_entry` (immutable)
- `updated_state` (if approved)
