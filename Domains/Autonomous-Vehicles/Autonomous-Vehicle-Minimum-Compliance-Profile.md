# Autonomous Vehicle Domain — Minimum Compliance Profile (MCP)

**RUAX Level‑0 Domain Specification**  
**Autonomous Vehicle Minimum Compliance Profile (MCP_av)**

The Minimum Compliance Profile defines the **absolute minimum constitutional requirements** an Autonomous Vehicle kernel must satisfy to be considered valid under RUAX.  
These requirements ensure:

- deterministic behavior  
- invariant‑bound safety  
- WAD‑encoded representability  
- purity‑gate admissibility  
- cross‑kernel interoperability  
- auditability and replayability  

Any AV kernel that fails MCP_av is **non‑constitutional** and must not actuate.

---

# 1. Purpose

MCP_av ensures:

- all constitutional components are present  
- all safety‑critical fields are valid  
- all invariants are decidable  
- all projection and refinement steps are admissible  
- all ledger entries are complete  
- all cross‑kernel interactions are integrity‑checked  

This is the **minimum bar** for AV constitutional compliance.

---

# 2. MCP Structure

The MCP consists of:

- **[State Requirements](ca://s?q=Explain_AV_MCP_State_Requirements)**  
- **[Projection Requirements](ca://s?q=Explain_AV_MCP_Projection_Requirements)**  
- **[Invariant Requirements](ca://s?q=Explain_AV_MCP_Invariant_Requirements)**  
- **[Refinement Requirements](ca://s?q=Explain_AV_MCP_Refinement_Requirements)**  
- **[Safety Envelope Requirements](ca://s?q=Explain_AV_MCP_Safety_Envelope_Requirements)**  
- **[Purity Gate Requirements](ca://s?q=Explain_AV_MCP_Purity_Gate_Requirements)**  
- **[Ledger Requirements](ca://s?q=Explain_AV_MCP_Ledger_Requirements)**  
- **[Cross‑Kernel Requirements](ca://s?q=Explain_AV_MCP_Cross_Kernel_Requirements)**  

All must be satisfied.

---

# 3. State Requirements

The AV kernel must provide:

- **[complete_F31_state](ca://s?q=Explain_AV_MCP_Complete_F31_State)** — all 31 components present  
- **[wad_encoding](ca://s?q=Explain_AV_MCP_WAD_Encoding)** — all values integer‑scaled  
- **[representability](ca://s?q=Explain_AV_MCP_Representability)** — no undefined or missing values  
- **[bounded_values](ca://s?q=Explain_AV_MCP_Bounded_Values)** — all values within domain bounds  

Missing or non‑WAD values → **MCP failure**.

---

# 4. Projection Requirements

π_av must:

- **[normalize_inputs](ca://s?q=Explain_AV_MCP_Normalize_Inputs)** — all raw values normalized  
- **[bind_axioms](ca://s?q=Explain_AV_MCP_Bind_Axioms)** — all F31 components bound to axioms  
- **[encode_wad](ca://s?q=Explain_AV_MCP_Encode_WAD)** — all values WAD‑encoded  
- **[reject_invalid](ca://s?q=Explain_AV_MCP_Reject_Invalid)** — reject missing, undefined, or out‑of‑range inputs  

Projection failure → **MCP failure**.

---

# 5. Invariant Requirements

All invariants must be:

- **[decidable](ca://s?q=Explain_AV_MCP_Invariant_Decidability)** — computable in finite steps  
- **[pass_before_actuation](ca://s?q=Explain_AV_MCP_Invariant_Pass)** — all must pass  
- **[axiom_bound](ca://s?q=Explain_AV_MCP_Axiom_Bound)** — bound to constitutional axioms  
- **[risk_safe](ca://s?q=Explain_AV_MCP_Risk_Safe)** — collision and TTC thresholds satisfied  

Invariant failure → **MCP failure**.

---

# 6. Refinement Requirements

R³ must:

- **[satisfy_contraction](ca://s?q=Explain_AV_MCP_Contraction)** —  
  \[
  \|Y' - Y^*\| \le 0.85 \cdot \|Y - Y^*\|
  \]

- **[reduce_risk](ca://s?q=Explain_AV_MCP_Reduce_Risk)** — risk must not increase  
- **[improve_stability](ca://s?q=Explain_AV_MCP_Improve_Stability)** — stability indices must improve or remain stable  
- **[preserve_wad](ca://s?q=Explain_AV_MCP_Preserve_WAD)** — no floating‑point values  

Refinement failure → **MCP failure**.

---

# 7. Safety Envelope Requirements

The AV state must satisfy:

\[
\|Y - Y^*\| \le A_{max}
\]

Where:

\[
A_{max} = 10^{-4} \text{ WAD units}
\]

Envelope violation → **MCP failure**.

---

# 8. Purity Gate Requirements

PG_av must evaluate to:

\[
PG_{av} = 1
\]

This requires:

- **[projection_admissible](ca://s?q=Explain_AV_MCP_PG_Projection)**  
- **[invariants_pass](ca://s?q=Explain_AV_MCP_PG_Invariants)**  
- **[risk_monotonicity](ca://s?q=Explain_AV_MCP_PG_Risk)**  
- **[actuator_bounds](ca://s?q=Explain_AV_MCP_PG_Actuators)**  
- **[sensor_integrity](ca://s?q=Explain_AV_MCP_PG_Sensors)**  
- **[localization_integrity](ca://s?q=Explain_AV_MCP_PG_Localization)**  
- **[constitutional_reserve](ca://s?q=Explain_AV_MCP_PG_Reserve)**  

Purity failure → **MCP failure**.

---

# 9. Ledger Requirements

Each control cycle must log:

- **[state](ca://s?q=Explain_AV_MCP_Ledger_State)** — full F31  
- **[invariants](ca://s?q=Explain_AV_MCP_Ledger_Invariants)** — pass/fail + values  
- **[r3_metrics](ca://s?q=Explain_AV_MCP_Ledger_R3)** — contraction, stability, risk  
- **[safety
