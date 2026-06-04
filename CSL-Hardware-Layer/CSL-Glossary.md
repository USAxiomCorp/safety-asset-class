# Constitutional Safety Layer (CSL) — Glossary
## Foundation for Aligned Intelligence, Truth, and Humanity (FAITH)

This glossary defines the formal terminology used throughout the CSL Hardware Layer specification.  
All definitions are normative and required for SAC certification, RUAX execution, R³ refinement, MVL legality, and RAC auditability.

---

## A

### **Arithmetic Bound (Hardware)**
The maximum allowable numerical error enforced by hardware‑level WAD arithmetic.

### **Audit Anchor (Hardware)**
A hardware‑generated cryptographic link between CSL traces and RAC blocks.

---

## B

### **Boundary Condition (Hardware)**
A constitutional or legal limit that CSL enforces physically.

### **Boundary Enforcement Unit (BEU)**
The CSL subsystem responsible for detecting and blocking boundary violations.

---

## C

### **CSL**
The Constitutional Safety Layer — the Tier 3 hardware enforcement substrate of SAC.

### **CSL Verification**
Hardware‑level confirmation that execution adhered to constitutional and legal constraints.

### **Constraint Evaluation Unit (CEU)**
The CSL subsystem that evaluates constitutional and legal constraints at the silicon level.

---

## D

### **Deterministic Hardware Execution**
The requirement that hardware produce identical results for identical inputs.

### **Deterministic Hardware Replay**
The ability to reproduce execution exactly from CSL traces.

---

## E

### **Enforcement Layer (Hardware)**
One of the CSL enforcement subsystems: CEU, BEU, HTU, or RIU.

### **Escalation (Hardware)**
A hardware‑triggered escalation when uncertainty exceeds the maximum allowable threshold.

---

## F

### **Fixed‑Point Verification (Hardware)**
CSL verification that a refinement fixed‑point satisfies all constraints.

---

## H

### **Hardware Boundary Event**
A CSL‑generated event triggered when execution approaches or attempts to cross a boundary.

### **Hardware Trace Unit (HTU)**
The CSL subsystem that generates hardware‑level traces.

---

## I

### **Interrupt (Hardware)**
A hardware‑triggered halt caused by constraint failure, legal failure, or boundary violation.

---

## L

### **Legal Enforcement (Hardware)**
The physical enforcement of MVL legal constraints.

---

## O

### **Operator Verification (Hardware)**
CSL verification of operator ID, state hashes, and arithmetic bounds.

---

## P

### **Physical Immutability**
The property that CSL prevents modification of anchored traces and blocks.

### **Projection (Hardware)**
The act of projecting a state back into the constitutional boundary at the hardware level.

---

## R

### **Rollback (Hardware)**
A hardware‑triggered reversion to the last safe checkpoint.

### **Rollback & Interrupt Unit (RIU)**
The CSL subsystem responsible for halting and reverting unsafe execution.

---

## S

### **State Hash (Hardware)**
A cryptographic hash representing the system state
