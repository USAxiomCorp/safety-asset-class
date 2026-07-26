# Banking Entity Space (WAD)

The Banking Entity Space defines all admissible entities in the Banking Domain.
All entities, attributes, and relations MUST be expressible in Weak Arithmetic
Decidability (WAD): finite sets, integer quantities, bounded relations, and
deterministic constraints.

---

## 1. Core Constitutional Entities

### 1.1 Account
A constitutional financial container with:
- balance: integer ≥ 0
- risk_score: integer in [0, 100]
- status: {active, frozen, closed}

### 1.2 Customer
A constitutional identity with:
- customer_id: integer
- accounts: finite set of Account
- exposure: integer ≥ 0

### 1.3 Instrument
A financial instrument with:
- type: {deposit, loan, security}
- principal: integer ≥ 0
- rate: integer ≥ 0
- term: integer ≥ 0

### 1.4 LedgerEntry
A deterministic financial event with:
- entry_id: integer
- amount: integer ≥ 0
- source_account: Account
- destination_account: Account
- timestamp: integer (monotonic)

### 1.5 SettlementBatch
A finite, ordered set of LedgerEntry:
- batch_id: integer
- entries: finite list of LedgerEntry
- total_amount: integer ≥ 0

### 1.6 ComplianceRecord
A constitutional compliance artifact:
- record_id: integer
- entry_id: integer
- rule_id: integer
- satisfied: {true, false}

---

## 2. WAD Constraints

### 2.1 Finite Entity Sets
All entity collections MUST be finite:
- finite customers
- finite accounts
- finite instruments
- finite ledger entries
- finite compliance records

### 2.2 Integer‑Bounded Attributes
All numeric attributes MUST be integers:
- balances
- exposures
- principal
- rates
- timestamps
- risk scores

### 2.3 Deterministic Relations
All relations MUST be WAD‑decidable:
1. Each LedgerEntry maps to exactly one source and one destination Account.
2. Each ComplianceRecord maps to exactly one LedgerEntry.
3. Each SettlementBatch contains a finite list of LedgerEntries.
4. Each Customer has a finite set of Accounts.

### 2.4 Constitutional Bounds
1. balance ≥ 0  
2. exposure ≥ 0  
3. risk_score ∈ [0, 100]  
4. principal ≥ 0  
5. rate ≥ 0  
6. term ≥ 0  

All constraints are finite arithmetic comparisons.

---

## 3. Deterministic Entity Behavior (WAD)

### 3.1 Account Behavior
- balance updates are integer additions/subtractions
- risk_score updates are integer assignments
- status transitions are finite and enumerated

### 3.2 Instrument Behavior
- principal changes via integer arithmetic
- rate and term remain integer‑bounded
- no fractional or non‑deterministic values allowed

### 3.3 LedgerEntry Behavior
- amount is integer
- timestamp is integer and strictly increasing
- mapping to accounts is deterministic

### 3.4 SettlementBatch Behavior
- total_amount = Σ(entries.amount)
- Σ is finite and integer‑bounded
- ordering is deterministic

### 3.5 ComplianceRecord Behavior
- satisfied ∈ {true, false}
- rule evaluation is finite arithmetic

---

## 4. Constitutional Summary

The Banking Entity Space ensures that all banking entities are:

- finite  
- integer‑bounded  
- deterministically related  
- WAD‑decidable  
- constitutionally admissible  

This file defines the foundational state space for all Banking Kernel operations.
