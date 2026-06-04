# RAC Audit Chain — Glossary
## Foundation for Aligned Intelligence, Truth, and Humanity (FAITH)

This glossary defines the formal terminology used throughout the RAC Audit Chain specification.  
All definitions are normative and required for SAC certification, R³ refinement, RUAX execution, MVL legality, and CSL enforcement.

---

## A

### **Audit Chain (RAC)**
The immutable, cryptographically verifiable chain of execution and refinement traces.

### **Audit Integrity**
The guarantee that all traces and blocks are tamper‑evident and immutable.

### **Attribution Record**
A RAC‑anchored record identifying the operator, rule, and execution path responsible for a system action.

---

## B

### **Block**
A structured, immutable container of trace entries.

### **BlockHash**
The SHA3‑256 hash of a RAC block.

### **Boundary Event**
A RAC‑logged event triggered when execution approaches or attempts to cross a constitutional or legal boundary.

---

## C

### **Chain Continuity**
The requirement that each block references the previous block hash.

### **CSL Verification**
Hardware‑level confirmation that a block or trace is valid.

---

## D

### **Deterministic Replay**
The ability to reproduce system behavior exactly from RAC traces.

### **Digest**
A cryptographic hash representing a trace or block.

---

## E

### **Execution Path**
The ordered sequence of operator steps recorded in a trace.

### **Enforcement Layer**
One of the RAC enforcement layers: trace, block, chain, or hardware.

---

## F

### **FAITH**
The governing authority responsible for maintaining RAC and the entire constitutional safety stack.

### **Forward Integrity**
The property that tampering with any block invalidates all subsequent blocks.

---

## H

### **Hardware Boundary Event**
A CSL‑generated event indicating a hardware‑detected violation.

---

## L

### **Legal Replayability**
The ability to reproduce legal decisions exactly from RAC traces.

---

## M

### **Merkle Proof**
A cryptographic proof that a trace entry is included in a RAC block.

### **Merkle Root**
The root hash of the Merkle tree constructed from trace entries.

---

## O

### **OperatorID**
The identifier of the operator responsible for a trace entry.

---

## R

### **RAC Anchor**
A cryptographic link between a trace entry and its containing block.

### **RAC Block**
A structured, immutable record containing trace entries and cryptographic metadata.

### **RAC Boundary Event**
A RAC‑logged event triggered by a violation or attempted violation.

### **Refinement Replay**
The ability to reconstruct the R³ refinement sequence exactly.

---

## S

### **Signature**
An Ed25519 signature verifying block authenticity.

### **State Hash**
A cryptographic hash representing the system state before or after execution.

---

## T

### **Trace Entry**
A structured record of operator execution, constraint checks, legal checks, and boundary events.

### **TraceID**
A unique identifier for a trace entry.

---

# Authority
The RAC Glossary is maintained exclusively by FAITH and may be amended only through the governance processes defined in the Foundation Charter.
