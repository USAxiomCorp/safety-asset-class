# Constitutional Mapping Operator M (Banking, WAD)

The Constitutional Mapping Operator M defines how raw banking events are
translated into constitutional states under the Banking Kernel. All mapping
rules MUST be expressible in Weak Arithmetic Decidability (WAD): finite sets,
integer quantities, bounded inequalities, and deterministic transitions.

---

## 1. Purpose of Operator M

Operator M is the gateway from the external event space into the constitutional
Banking State. It:

- validates raw events against WAD constraints
- rejects inadmissible or impure events
- maps admissible events into canonical ledger updates
- ensures all resulting states remain constitutional and invariant-preserving

M is **total** over admissible events and **rejecting** over inadmissible ones.

---

## 2. Raw Event Model (WAD)

A RawEvent E is defined as:

- `type`: {deposit, withdrawal, credit_issue, credit_repay, transfer}
- `amount`: integer ≥ 0
- `source_account_id`: integer (may be null for deposits)
- `destination_account_id`: integer (may be null for withdrawals)
- `timestamp`: integer (monotonic)
- `flags`: finite set of tags (e.g., {high_risk, blacklisted})

All fields are finite and integer-bounded → WAD-expressible.

---

## 3. Constitutional State Model (Input/Output)

### 3.1 Input State S

S consists of:

- finite set of Accounts
- finite set of Customers
- finite set of Instruments
- finite set of LedgerEntries
- finite set of ComplianceRecords

All numeric attributes are integers (balances, exposures, risk scores).

### 3.2 Output State S'

S' is the updated constitutional state after applying M(E) if E is admissible.
If E is inadmissible, S' = S and E is rejected.

---

## 4. Admissibility Checks (WAD)

Before mapping, M performs admissibility checks:

1. **Amount Non-Negativity**
   - `amount ≥ 0`

2. **Account Existence**
   - If `source_account_id` is provided → source account MUST exist.
   - If `destination_account_id` is provided → destination account MUST exist.

3. **Risk Bounds**
   - `risk_score(source) ≤ MAX_RISK`
   - `risk_score(destination) ≤ MAX_RISK`

4. **Flags Purity**
   - `blacklisted ∉ flags`

5. **Invariant Preservation (Pre-check)**
   - Applying E MUST NOT violate:
     - solvency: `assets - liabilities ≥ 0`
     - liquidity: `liquid_assets ≥ MIN_LIQUIDITY`
     - exposure: `customer_exposure ≤ MAX_EXPOSURE`
     - balance: `balance ≥ 0`

All checks are finite arithmetic comparisons and set membership → WAD-decidable.

If any check fails, E is rejected and S remains unchanged.

---

## 5. Mapping Rules by Event Type (WAD)

For admissible events, M maps E into canonical ledger and state updates.

### 5.1 Deposit

- Source: external (no source_account_id)
- Destination: `destination_account_id`

Rules:

1. `new_balance(destination) = old_balance(destination) + amount`
2. Create LedgerEntry:
   - `entry_id`: new integer
   - `amount = amount`
   - `source_account = external`
   - `destination_account = destination`
   - `timestamp = E.timestamp`
3. Update exposure and invariants as needed.

All operations are integer additions and finite set insertions.

### 5.2 Withdrawal

- Source: `source_account_id`
- Destination: external

Rules:

1. Check `old_balance(source) ≥ amount`
2. `new_balance(source) = old_balance(source) - amount`
3. Create LedgerEntry:
   - `source_account = source`
   - `destination_account = external`
4. Re-check invariants (solvency, liquidity, exposure).

All operations are integer subtractions and finite set insertions.

### 5.3 Credit Issue

- Source: bank credit facility
- Destination: `destination_account_id`

Rules:

1. Create Instrument (loan):
   - `principal = amount`
   - `rate = integer ≥ 0`
   - `term = integer ≥ 0`
2. Check exposure:
   - `customer_exposure + amount ≤ MAX_EXPOSURE`
3. `new_balance(destination) = old_balance(destination) + amount`
4. Create LedgerEntry for disbursement.

All operations are integer arithmetic and finite set insertions.

### 5.4 Credit Repay

- Source: `source_account_id`
- Destination: bank credit facility

Rules:

1. Check `old_balance(source) ≥ amount`
2. `new_balance(source) = old_balance(source) - amount`
3. Reduce loan principal:
   - `new_principal = old_principal - amount`
4. Create LedgerEntry for repayment.

All operations are integer subtractions and comparisons.

### 5.5 Transfer

- Source: `source_account_id`
- Destination: `destination_account_id`

Rules:

1. Check `old_balance(source) ≥ amount`
2. `new_balance(source) = old_balance(source) - amount`
3. `new_balance(destination) = old_balance(destination) + amount`
4. Create LedgerEntry with both accounts.

All operations are integer additions/subtractions.

---

## 6. Compliance Anchoring

For every mapped event E:

1. Create ComplianceRecord:
   - `record_id`: new integer
   - `entry_id`: LedgerEntry.entry_id
   - `rule_id`: integer representing applied rule set
   - `satisfied`: {true, false}

2. Compliance evaluation is WAD:
   - finite rules
   - integer thresholds
   - boolean satisfaction

Every LedgerEntry MUST have at least one ComplianceRecord.

---

## 7. Determinism and Replay

Operator M is deterministic:

- Given S and E, the resulting S' is unique.
- No randomness, no branching, no ambiguity.

Replay property:

- Replaying all admissible events in order via M MUST yield the same S'.

This is guaranteed because:

- all operations are integer arithmetic
- all sets are finite
- all checks are WAD-decidable

---

## 8. Constitutional Summary

The Constitutional Mapping Operator M for Banking:

- validates raw events via WAD constraints
- rejects inadmissible or impure events
- maps admissible events into canonical ledger and state updates
- preserves all constitutional invariants
- remains fully deterministic and WAD-decidable

M is the constitutional bridge between external financial events and the
internal Banking Kernel state.
