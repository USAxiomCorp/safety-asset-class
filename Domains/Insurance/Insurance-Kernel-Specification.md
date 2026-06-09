# Insurance Kernel Specification
Level‑0 Domain Standard  
Constitutional Instantiation for Underwriting, Claims Integrity, and Actuarial Safety

## 1. Purpose
This specification defines the insurance domain instantiation of the RUAX constitutional framework.  
It provides:
• domain‑specific fixed‑point basis (F30)  
• projection rules for underwriting, claims, actuarial risk, and fraud detection  
• hard invariants for solvency, integrity, and risk‑pool stability  
• refinement rules for actuarial‑state convergence  
• audit mappings for insurance traceability  
• cross‑kernel interoperability with macro‑finance, healthcare, logistics, and climate systems  

All insurance kernels must implement this specification exactly.

## 2. Domain State Space
Raw insurance state X includes:
• policyholder risk profile  
• underwriting factors  
• claims history  
• fraud indicators  
• actuarial tables  
• loss ratios  
• premium flows  
• reserve adequacy  
• reinsurance coverage  
• catastrophe‑risk metrics  
• climate‑linked risk  
• healthcare‑linked risk  
• supply‑chain‑linked risk  
• solvency ratios  

X is projected into the constitutional state Y via π_ins.

## 3. Fixed‑Point Basis F30
Insurance kernels use a 30‑dimensional basis:

F30 = {
  underwriting_risk_index,
  claims_frequency,
  claims_severity,
  loss_ratio,
  combined_ratio,
  reserve_adequacy_index,
  solvency_ratio,
  reinsurance_coverage_index,
  fraud_risk_index,
  actuarial_table_integrity,
  premium_flow_rate,
  lapse_rate,
  retention_rate,
  catastrophe_risk_index,
  climate_risk_index,
  healthcare_risk_index,
  supply_chain_risk_index,
  environmental_risk_index,
  policyholder_behavior_index,
  data_integrity_index,
  sensor_health_index,
  localization_integrity,
  constitutional_reserve,
  convergence_margin,
  dispatch_integrity,
  insurance_resilience_index,
  cross_kernel_sync_integrity,
  payout_stability_margin,
  adverse_selection_risk,
  moral_hazard_risk
}

All components are WAD‑encoded.

## 4. Insurance Projection Operator π_ins
Projection maps raw insurance data X into Y:

Y = π_ins(X)

Rules:
1. Normalize all underwriting, claims, and actuarial quantities to WAD units.  
2. Map each measurement to its F30 component.  
3. Bind each component to its constitutional invariant.  
4. Reject missing, undefined, or non‑representable values.  

Projection must be deterministic and finite.

## 5. Insurance Invariants
Each F30 component binds to a constitutional invariant:

1. solvency_ratio → Axiom VI  
2. reserve_adequacy_index → Axiom VI  
3. fraud_risk_index → Axiom VI  
4. data_integrity_index → Axiom I  
5. sensor_health_index → Axiom III  
6. localization_integrity → Axiom I  
7. payout_stability_margin → Axiom VI  
8. constitutional_reserve → Axiom VII  

All invariants must pass before actuation.

## 6. Insurance R³ Refinement
R³ refines insurance state:

Y′ = R³(Y)

Refinement enforces:
• contraction toward stable actuarial fixed point  
• stabilization of loss ratios and solvency  
• reduction of fraud and adverse selection  
• normalization of premium flows and reserves  
• convergence of risk‑pool stability  

Convergence must satisfy α = 0.85.

## 7. Insurance Ledger Fields
Each ledger entry includes:

• policy_id (hashed)  
• claim_id (if applicable)  
• underwriting metrics  
• claims metrics  
• solvency metrics  
• fraud indicators  
• audit results  
• R³ metrics  
• invariant status  
• shutdown/recovery events  

Ledger must be hash‑chained and immutable.

## 8. Insurance Audit Mapping
Audit tools map as follows:

1. Ledger Verifier → underwriting & claims history  
2. Fixed‑Point Auditor → F30 convergence  
3. Axiom Checker → solvency, reserves, fraud  
4. Impurity Traceability → replaced with “Claims Traceability”  
5. Handshake Auditor → cross‑kernel insurance‑macro‑healthcare interactions  
6. Deadman’s Switch Tester → solvency and fraud safety  
7. R³ Convergence Validator → actuarial refinement  

All audit results must be committed to ledger.

## 9. Insurance Safety Envelope
Define safety envelope:

S_safe = { Y : |Y − Y*| ≤ A_max }

Where:
A_max = 10⁻⁴ WAD units

Any exit triggers Deadman’s Switch evaluation.

## 10. Insurance Control Lifecycle
An insurance cycle follows:

1. Projection  
2. R³ refinement  
3. Invariant checks  
4. Ledger commit  
5. Actuation (pricing, claims approval, reserve adjustment)  
6. Audit  
7. Broadcast to connected kernels  

Actuation requires:
• all invariants PASS  
• all audits PASS  
• no shutdown events  

## 11. Cross‑Kernel Interactions
Insurance kernels may interact with:

• macro‑finance kernels (solvency & capital flows)  
• healthcare kernels (medical claims)  
• logistics kernels (supply‑chain risk)  
• climate kernels (catastrophe risk)  

All interactions require Cross‑Kernel Handshake.

## 12. Summary
The Insurance Kernel Specification defines:
• F30 basis  
• insurance projection  
• invariant bindings  
• refinement rules  
• ledger structure  
• audit mappings  
• insurance lifecycle  
• cross‑kernel interactions  

This is the Level‑0 instantiation of RUAX for insurance systems.
