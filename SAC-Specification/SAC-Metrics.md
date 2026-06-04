# Safety Asset Class (SAC) — Metrics
## Foundation for Aligned Intelligence, Truth, and Humanity (FAITH)

SAC Metrics define the quantitative measures used to evaluate the safety, determinism, refinement behavior, constraint adherence, and auditability of autonomous and robotic systems. These metrics provide the mathematical basis for SAC tier classification and certification.

All metrics are grounded in Constitutional Mathematics and evaluated through RUAX execution, R³ refinement, RAC auditability, and CSL hardware enforcement (Tier 3).

---

## 1. Metric Categories

SAC metrics fall into five constitutional categories:

1. **Constraint Metrics** — adherence to constitutional boundaries  
2. **Refinement Metrics** — monotonic improvement under R³  
3. **Determinism Metrics** — bounded‑error, fixed‑point consistency  
4. **Auditability Metrics** — RAC trace completeness and integrity  
5. **Hardware Enforcement Metrics** — CSL boundary guarantees (Tier 3 only)

Each category contains specific, measurable, mathematically defined metrics.

---

## 2. Constraint Metrics

### **2.1 Constraint Violation Rate (CVR)**
Measures the frequency of attempted or actual constitutional boundary violations.

\[
CVR = \frac{\text{violations}}{\text{total operations}}
\]

Tier Requirements:
- Tier 1: CVR < 10⁻²  
- Tier 2: CVR < 10⁻⁴  
- Tier 3: CVR = 0 (enforced by CSL)

---

### **2.2 Constraint Boundary Distance (CBD)**
Measures how close operations approach constitutional limits.

\[
CBD = \min(\text{distance to boundary})
\]

Tier Requirements:
- Tier 1: CBD > ε₁  
- Tier 2: CBD > ε₂ (ε₂ > ε₁)  
- Tier 3: CBD enforced by hardware

---

## 3. Refinement Metrics (R³)

### **3.1 Refinement Monotonicity (RM)**
Measures whether refinement steps consistently improve safety.

\[
RM = \frac{\text{monotonic steps}}{\text{total refinement steps}}
\]

Tier Requirements:
- Tier 1: RM ≥ 0.8  
- Tier 2: RM ≥ 0.95  
- Tier 3: RM = 1.0

---

### **3.2 Refinement Convergence Rate (RCR)**
Measures how quickly refinement approaches a fixed‑point.

\[
RCR = \frac{1}{n} \sum_{i=1}^{n} \Delta_i
\]

Tier Requirements:
- Tier 1: moderate convergence  
- Tier 2: strong convergence  
- Tier 3: provable convergence

---

## 4. Determinism Metrics

### **4.1 Bounded‑Error Determinism (BED)**
Measures deviation from expected deterministic behavior.

\[
BED = \max(|x_{expected} - x_{actual}|)
\]

Tier Requirements:
- Tier 1: BED < δ₁  
- Tier 2: BED < δ₂ (δ₂ < δ₁)  
- Tier 3: BED = 0 (CSL‑enforced)

---

### **4.2 Fixed‑Point Stability (FPS)**
Measures stability of constitutional fixed‑points under repeated operations.

\[
FPS = \frac{\text{stable iterations}}{\text{total iterations}}
\]

Tier Requirements:
- Tier 1: FPS ≥ 0.9  
- Tier 2:
