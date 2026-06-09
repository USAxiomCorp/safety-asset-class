# RUAX Operational Fault Model
Level‑1 Operational Standard  
Universal Fault Classification, Detection, and Recovery for RUAX Kernels

## 1. Purpose
This standard defines the universal fault model for all RUAX‑compliant kernels.  
It ensures:
• deterministic fault classification  
• invariant‑safe recovery  
• cross‑kernel consistency  
• ledger‑anchored fault evidence  
• predictable escalation behavior  

All industries inherit this model without modification.

## 2. Fault Classes
RUAX defines four universal fault classes:

### F1 — Constitutional Fault
Violations of:
• invariants  
• R³ contraction  
• fixed‑point identity  
• CSL hardware integrity  
• Deadman’s Switch conditions  

F1 faults are the most severe and require immediate shutdown.

### F2 — Ledger Fault
Violations of:
• hash chain integrity  
• missing ledger entries  
• invalid commit attempts  
• mismatched timestamps  

F2 faults require rollback and re‑anchoring.

### F3 — Projection Fault
Violations of:
• domain → constitutional mapping  
• normalization errors  
• missing domain inputs  
• non‑WAD‑representable values  

F3 faults result in BLOCK and re‑projection.

### F4 — Communication Fault
Violations of:
• Cross‑Kernel Handshake  
• message ordering  
• message corruption  
• expired handshake tokens  
• coordination timeouts  

F4 faults require handshake reset and replay.

## 3. Fault Detection Pipeline
Fault detection occurs in the following order:

1. **Projection Check**  
   Detects F3 faults.

2. **Invariant Check**  
   Detects F1 faults.

3. **R³ Convergence Check**  
   Detects F1 faults.

4. **Ledger Attestation**  
   Detects F2 faults.

5. **Handshake Verification**  
   Detects F4 faults.

6. **Coordination Ordering Check**  
   Detects F4 faults.

Fault classification is deterministic based on the first failing stage.

## 4. Fault Escalation Levels
Each fault maps to an escalation level:

### Level 0 — PASS
No fault detected.

### Level 1 — WARNING
Minor deviation detected.  
Actions:
• log warning  
• schedule early periodic audit  

### Level 2 — VIOLATION
F2, F3, or F4 fault detected.  
Actions:
• BLOCK commit  
• run event‑driven audit  
• notify coordinator kernels  

### Level 3 — CRITICAL
F1 fault detected.  
Actions:
• trigger Deadman’s Switch evaluation  
• disable actuators  
• enter SAFE‑HALT state  
• require operator intervention  

Escalation level is recorded in the ledger.

## 5. Fault Recovery Paths
Each fault class has a deterministic recovery path:

### F1 Recovery — Constitutional Fault
1. Trigger Deadman’s Switch  
2. Disable actuators  
3. Log shutdown event  
4. Require physical reset  
5. Re‑initialize kernel  
6. Re‑run R³ to re‑establish Y*  
7. Verify invariants  
8. Resume only after CSL passes self‑test

### F2 Recovery — Ledger Fault
1. Roll back to last valid ledger entry  
2. Recompute state from Yₜ  
3. Re‑anchor corrected ledger entry  
4. Resume refinement loop

### F3 Recovery — Projection Fault
1. Emit BLOCK  
2. Request new domain inputs  
3. Re‑project X → Y  
4. Resume refinement loop

### F4 Recovery — Communication Fault
1. Reset handshake  
2. Request replay of last message  
3. Re‑verify ordering  
4. Resume coordination

## 6. Fault Evidence Format
Each fault must generate a ledger entry containing:

• fault_class (F1–F4)  
• escalation_level (0–3)  
• timestamp  
• failing_component  
• invariant_status  
• R³ metrics  
• handshake status (if applicable)  
• recovery_path  
• verification_hash  

Format matches the Meta‑Ledger Specification.

## 7. Cross‑Kernel Fault Propagation
If a fault occurs during coordination:

1. CK broadcasts FAULT token  
2. All PKs halt actuation  
3. All kernels anchor fault event  
4. CK initiates recovery protocol  
5. Coordination resumes only after consensus

No kernel may ignore a propagated fault.

## 8. Determinism
Given:
• constitutional parameters  
• projection operator  
• ledger state  
• handshake state  
• coordination state  

Fault classification and recovery are uniquely determined.

No nondeterminism is permitted.

## 9. Summary
The RUAX Operational Fault Model defines:
• universal fault classes  
• detection pipeline  
• escalation levels  
• recovery paths  
• fault evidence format  
• cross‑kernel propagation  
• deterministic behavior  

All RUAX kernels must implement this fault model exactly.
