# Example — Basic Loan Evaluation (CLE)

This example demonstrates how a lending action is evaluated through the Constitutional Lending Engine (CLE) using the four core predicates.

---

## 1. Inputs

- collateral_value = 150,000
- required_collateral = 100,000
- post_leverage = 2.5
- max_leverage = 3.0
- borrower_jurisdiction = 0xA1B2
- asset_jurisdiction = 0xA1B2
- Xt = 0.42
- Xt+1 = 0.39

---

## 2. Predicate Evaluation

### Collateral Predicate
150,000 ≥ 100,000  →  d1 = 1
### Leverage Predicate
2.5 ≤ 3.0  →  d2 = 1
### Jurisdiction Predicate
0xA1B2 == 0xA1B2  →  d3 = 1
### Risk Predicate (Supermartingale)
0.39 ≤ 0.42  →  d4 = 1
---

## 3. Admissibility Gate

\[
A(L) = d_1 \land d_2 \land d_3 \land d_4 = 1
\]

All predicates return 1 → **Loan is admissible**.

---

## 4. Output
approved = true audit_entry = { collateral_value: 150000, required_collateral: 100000, post_leverage: 2.5, max_leverage: 3.0, jurisdictions: 0xA1B2, Xt: 0.42, XtNext: 0.39, timestamp: <block.timestamp> }


