# RUAX Inter‑Kernel Coordination Protocol
Level‑1 Operational Standard  
Deterministic Multi‑Kernel Coordination for Constitutional Systems

## 1. Purpose
This protocol defines how multiple RUAX‑compliant kernels coordinate actions across industries.  
It ensures:
• deterministic ordering  
• invariant‑safe coordination  
• cross‑kernel consistency  
• ledger‑anchored synchronization  
• no semantic drift  

All coordination must follow this protocol.

## 2. Kernel Coordination Roles
Each kernel participating in coordination must declare one of the following roles:

1. **Coordinator Kernel (CK)**  
   Orchestrates ordering, timing, and synchronization.

2. **Participant Kernel (PK)**  
   Executes actions under CK scheduling.

3. **Observer Kernel (OK)**  
   Reads state but does not act or influence ordering.

Roles are recorded in each kernel’s ledger.

## 3. Coordination Preconditions
Before coordination begins:

1. All kernels must complete the Cross‑Kernel Handshake.  
2. All kernels must share identical constitutional hashes.  
3. All kernels must have converged to the same Y*.  
4. All kernels must have synchronized ledger timestamps within Δt ≤ 10⁻⁶ s.  
5. All kernels must pass CSL self‑tests.

If any precondition fails → coordination aborts.

## 4. Coordination Cycle
Each coordination cycle consists of:

1. **Propose**  
   CK broadcasts proposed action A_t.

2. **Project**  
   Each PK computes Y_t = π_D(X_t).

3. **Refine**  
   Each PK computes Y′_t = R³(Y_t).

4. **Verify**  
   Each PK checks invariants and R³ metrics.

5. **Commit**  
   If all PKs return PASS, CK commits A_t to its ledger and broadcasts commit token.

6. **Actuate**  
   PKs actuate only after receiving commit token.

7. **Anchor**  
   All kernels anchor the coordination event to their ledgers.

## 5. Deterministic Ordering Rules
To prevent race conditions:

1. CK assigns a global sequence number seq_t.  
2. All PKs must process actions in seq_t order.  
3. No kernel may skip or reorder actions.  
4. Ledger entries must reflect seq_t exactly.  
5. Any deviation triggers F4 (communication fault).

## 6. Coordination Safety Rules
Coordination must halt if:

• any PK reports invariant violation  
• any PK reports R³ divergence  
• any PK fails to respond within timeout
