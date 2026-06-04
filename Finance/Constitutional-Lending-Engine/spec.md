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
