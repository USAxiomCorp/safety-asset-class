# Meta‑Ledger Specification
Level‑2 Meta‑Constitutional Standard  
Universal Ledger Format for RUAX Kernels

## 1. Purpose
The Meta‑Ledger defines the universal, domain‑agnostic ledger structure used by all constitutional kernels.  
It records:
• constitutional state commits  
• refinement history  
• invariant status  
• audit tool outputs  
• cross‑kernel handshake tokens  
• shutdown and recovery events  

All domain‑level ledgers inherit this structure without modification.

## 2. Ledger Entry Structure
Each ledger entry Lₖ is defined as:

Lₖ = {
  index: k,
  timestamp: tₖ,
  state_hash: H(Yₖ),
  mapping_hash: H(M(Yₖ)),
  invariant_status: 0 | 1,
  r3_metrics: {
    contraction_ratio: rₖ,
    distance_to_fixed_point: dₖ
  },
  audit: {
    tool_ids: [...],
    results: [...]
  },
  handshake: {
    token: H_token | null
  },
  shutdown: {
    triggered: true | false,
    reason: <string> | null
  },
  prev_hash: H(Lₖ₋₁),
  entry_hash: H(all_fields)
}

All fields are WAD‑encoded integers except strings and hashes.

## 3. Genesis Block
The genesis entry L₀ is defined as:

L₀ = H(D, F_m, α, W, Y*)

Where:
• D = constitutional axioms  
• F_m = fixed‑point basis  
• α = contraction factor  
• W = WAD precision  
• Y* = constitutional fixed point  

Genesis block is immutable and defines kernel identity.

## 4. Hashing Rules
All hashes use SHA3‑256 (FIPS 202).

state_hash = SHA3‑256(Yₖ)
mapping_hash = SHA3‑256(M(Yₖ))
entry_hash = SHA3‑256(serialized_entry)

prev_hash links entries into a tamper‑evident chain.

## 5. Commit Rules
A ledger entry may be committed only if:

1. 𝕀(Yₖ) = 1  
2. Deadman’s Switch not triggered  
3. R³ contraction ratio ≤ α  
4. audit tools (if invoked) return PASS  

If any condition fails:
• commit is blocked  
• BLOCK event is logged  
• no state transition occurs

## 6. Invariant Logging
Each entry records:

invariant_status = 1 if all invariants satisfied  
invariant_status = 0 if any invariant violated  

Violation automatically triggers Deadman’s Switch evaluation.

## 7. R³ Metrics
Each entry stores:

• contraction_ratio rₖ = |Yₖ − Yₖ₋₁| / |Yₖ₋₁ − Yₖ₋₂|  
• distance_to_fixed_point dₖ = |Yₖ − Y*|  

Both computed in pure WAD arithmetic.

## 8. Audit Integration
Audit tools append:

audit.tool_ids = [list of invoked tools]  
audit.results = [PASS | FAIL | INCONCLUSIVE]

If any FAIL occurs:
• commit is blocked
