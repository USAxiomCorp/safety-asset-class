# Machine‑Verifiable Law (MVL) — Constraint Definitions
## Foundation for Aligned Intelligence, Truth, and Humanity (FAITH)

Machine‑Verifiable Law (MVL) transforms legal rules into constitutional constraints that can be enforced by R³, RUAX, RAC, and CSL.  
This document defines the formal structure of MVL constraints and the canonical constraint families used across SAC‑compliant systems.

MVL is the legal substrate of the Safety Asset Class.

---

# 1. Purpose of MVL Constraints

MVL ensures that:

- legal rules become mathematically enforceable,
- compliance is deterministic and auditable,
- violations are physically impossible at Tier 3,
- refinement cannot escape legal boundaries,
- all legal constraints are RAC‑anchored.

MVL is the bridge between law and computation.

---

# 2. MVL Constraint Structure

An MVL constraint is a predicate:

\[
L : S \rightarrow \{\text{true}, \text{false}\}
\]

Every legal rule must be mapped to a constitutional constraint:

\[
L \iff C
\]

This mapping is bijective and normative.

---

# 3. MVL Constraint Families

MVL defines **five canonical constraint families**.

---

## 3.1 Safety Constraints

These constraints ensure that system behavior does not create unacceptable risk.

Examples:

### 3.1.1 Harm Prevention Constraint
\[
\text{Risk}(S) \le R_{\text{max}}
\]

### 3.1.2 Hazard Avoidance Constraint
\[
S \notin \mathcal{H}
\]

Where \( \mathcal{H} \) is the hazard set.

---

## 3.2 Privacy Constraints

These constraints enforce legal privacy protections.

### 3.2.1 Data Minimization Constraint
\[
|D_{\text{collected}}| \le D_{\text{min}}
\]

### 3.2.2 Purpose Limitation Constraint
\[
\text{Use}(D) \subseteq \text{Purpose}_{\text{allowed}}
\]

---

## 3.3 Autonomy Constraints

These constraints govern autonomous decision‑making.

### 3.3.1 Human‑Override Constraint
\[
\text{OverrideAvailable}(S) = \text{true}
\]

### 3.3.2 Escalation Constraint
\[
\text{Uncertainty}(S) > U_{\text{max}} \implies \text{Escalate}
\]

---

## 3.4 Transparency Constraints

These constraints ensure explainability and auditability.

### 3.4.1 Traceability Constraint
\[
\exists T : T = \text{Trace}(S)
\]

### 3.4.2 Explainability Constraint
\[
\text{Explain}(S) \neq \emptyset
\]

---

## 3.5 Accountability Constraints

These constraints ensure that responsibility
