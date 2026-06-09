# Constitutional Safety Layer (CSL) Specification
Level‑2 Meta‑Constitutional Standard  
Hardware–Software Boundary for RUAX Kernels

## 1. Purpose
The Constitutional Safety Layer (CSL) is the hardware boundary that enforces:
• invariant preservation  
• actuator gating  
• Deadman’s Switch logic  
• admissibility checks  
• handshake verification  
• ledger‑anchored state transitions  

No kernel may actuate without passing through the CSL.

## 2. CSL Architecture
The CSL consists of five hardware units:

1. Invariant Evaluation Unit (IEU)  
2. R³ Convergence Monitor (RCM)  
3. Actuator Gate Controller (AGC)  
4. Ledger Attestation Unit (LAU)  
5. Handshake Verification Unit (HVU)

All units operate in pure WAD arithmetic.

## 3. Invariant Evaluation Unit (IEU)
Inputs:
• constitutional state Y  
• invariant thresholds  
• WAD precision W  

Outputs:
• invariant_status = 1 | 0  
• failing_component (optional)

Rules:
1. Evaluate all invariants 𝕀ᵢ(Y).  
2. If any invariant fails, invariant_status = 0.  
3. No software may override IEU output.

## 4. R³ Convergence Monitor (RCM)
Inputs:
• Yₖ, Yₖ₋₁, Y*  
• α = 0.85  
• k_max = 7  

Outputs:
• contraction_ratio rₖ  
• distance_to_fixed_point dₖ  
• convergence_status = PASS | FAIL  

Rules:
1. Compute rₖ = |Yₖ − Yₖ₋₁| / |Yₖ₋₁ − Yₖ₋₂|  
2. Compute dₖ = |Yₖ − Y*|  
3. If rₖ > α or dₖ > A_max → FAIL  

## 5. Actuator Gate Controller (AGC)
Inputs:
• invariant_status  
• convergence_status  
• Deadman’s Switch latch  

Outputs:
• actuator_enable = TRUE | FALSE  

Rules:
1. actuator_enable = TRUE only if:
   • invariant_status = 1  
   • convergence_status = PASS  
   • Deadman’s Switch not triggered  
2. Any violation → actuator_enable = FALSE  
3. Hardware latch prevents re‑enable until reset.

## 6. Ledger Attestation Unit (LAU)
Inputs:
• previous ledger hash  
• proposed entry fields  

Outputs:
• ledger_valid = TRUE | FALSE  
• entry_hash  

Rules:
1. Recompute SHA3‑256 hash chain.  
2. Reject any mismatch.  
3. Reject any entry with invariant_status = 0.  
4. Reject any entry missing R³ metrics.

## 7. Handshake Verification Unit (HVU)
Inputs:
• handshake token  
• constitutional hash  
• fixed‑point vector Y*  

Outputs:
• handshake_valid = TRUE | FALSE  

Rules:
1. Verify SHA3‑256 constitutional hash match.  
2. Verify |Y*ₐ − Y*ᵦ| < ε_handshake.  
3. Verify R³ challenge‑response.  
4. Reject all external data without valid handshake.

## 8. CSL Enforcement Rules
Before any actuation:
1. IEU must output invariant_status = 1  
2. RCM must output convergence_status = PASS  
3. LAU must validate ledger chain  
4. HVU must validate handshake (if external data)  
5. Deadman’s Switch must be untriggered  

Failure of any rule → immediate hardware block.

## 9. CSL Reset Path
Reset requires:
1. physical hardware reset  
2. reload of constitutional parameters  
3. reconstruction of last valid Yₜ from ledger  
4. R³ convergence to Y*  
5. re‑verification of invariants  
6. re‑activation of AGC  

No software‑only reset is permitted.

## 10. Summary
The CSL defines:
• invariant enforcement  
• convergence monitoring  
• actuator gating  
• ledger attestation  
• handshake verification  
• hardware‑level shutdown  
• deterministic reset  

All RUAX kernels must implement the CSL exactly as specified.
