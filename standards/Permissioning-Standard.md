# Permissioning (PERM) — Top‑Layer Constitutional Standard  
Version: 0.1.0  
Maintainer: Foundation for Aligned Intelligence Truth and Humanity (FAITH)  
Status: Draft Standard  

---

## 1. Purpose and Scope

The Permissioning (PERM) Standard defines the **top‑layer constitutional rules** for identity, authority, and access control within CAI‑conformant systems.

PERM governs:

- how identities are created and anchored,  
- how authority is assigned and constrained,  
- how permissions are evaluated through CSL,  
- how governance interacts with permissioning,  
- how cross‑domain permissions are projected,  
- and how all permissioning decisions are recorded in the Meta‑Ledger.

This standard sits **above** all mid‑layer permissioning documents in your repository.

---

## 2. Constitutional Permissioning Boundary

Permissioning MUST occur **inside** the constitutional boundary.

This means:

- No identity may bypass CSL  
- No permission may override safety or legal constraints  
- No authority may exceed constitutional limits  
- No permission may bypass R3 refinement  
- No permission may bypass ledger recording  
- No external system may inject unauthorized identities  

Permissioning MUST be deterministic and immutable at the constitutional level.

---

## 3. Identity Model

Each identity \(I\) MUST include:

- **identity_hash**  
- **jurisdiction_code**  
- **role_code**  
- **public_key**  
- **creation_ledger_hash**  
- **zero‑knowledge identity proof**  

Identities MUST be:

- immutable  
- cryptographically anchored  
- jurisdictionally scoped  
- WAD‑encoded where applicable  

Identities MUST NOT:

- be mutable  
- be revocable without ledger record  
- be created outside KINIT  

---

## 4. Authority Model

Authority is defined as a set of constitutional capabilities:

\[
\mathcal{A}(I) = \{ a_1, a_2, \ldots, a_n \}
\]

Authority MUST satisfy:

- **Least Authority Principle** — identities receive only the minimum required authority  
- **Constitutional Supremacy** — authority cannot override constitutional rules  
- **Jurisdictional Isolation** — authority is scoped to jurisdiction  
- **Deterministic Evaluation** — authority MUST be evaluated through CSL  

Authority MUST NOT:

- be granted dynamically without ledger record  
- be granted through probabilistic or ML‑based methods  
- exceed constitutional constraints  

---

## 5. Permission Evaluation

A permission check is defined as:

\[
P(I, a, s) = A_{\text{perm}}(I, a, s)
\]

Where:

\[
A_{\text{perm}} = \prod_{i=1}^{m} d_i(I, a, s)
\]

Requirements:

- If \(A_{\text{perm}} = 1\): permission is granted  
- If \(A_{\text{perm}} = 0\): permission is denied  
- No override path is permitted  
- All permission decisions MUST be ledger‑committed  
- All permission decisions MUST produce zero‑knowledge proofs  

---

## 6. Immutable Permissioning Constraints

The following constraints MUST be immutable:

### P1 — No Constitutional Override  
Permissions cannot override constitutional rules.

### P2 — No Safety Override  
Permissions cannot weaken safety thresholds.

### P3 — No Legal Override  
Permissions cannot weaken legal constraints.

### P4 — No Jurisdictional Override  
Permissions cannot alter jurisdictional anchors.

### P5 — No Ledger Override  
Permissions cannot modify or delete ledger entries.

### P6 — No R3 Override  
Permissions cannot alter contraction factors or refinement logic.

---

## 7. Cross‑Domain Permissioning

When permissioning spans multiple domains:

- Projection MUST follow Cross‑Domain‑Projection‑Standard  
- No domain may weaken another domain’s constraints  
- The strictest constraint MUST prevail  
- All domains MUST converge under R3  
- Permissioning MUST remain deterministic  

---

## 8. Permissioning Ledger Requirements

Each permissioning decision MUST produce a ledger entry containing:

- identity hash  
- action hash  
- permission evaluation  
- admissibility bit  
- jurisdictional metadata  
- zero‑knowledge permission proof  
- previous ledger hash  

The permissioning ledger MUST be:

- immutable  
- append‑only  
- publicly verifiable  

---

## 9. Zero‑Knowledge Permission Proofs

Each permissioning decision MUST produce:

\[
\pi_{\text{perm}} = \text{ZK‑Prove}(A_{\text{perm}}(I, a, s) = 1)
\]

Proofs MUST:

- Not reveal private data  
- Be independently verifiable  
- Be reconstructible from ledger state  

---

## 10. Relationship to Other Standards

PERM depends on:

- CAI Core Standard  
- CSL Specification  
- R3 Operator Standard  
- WAD Arithmetic Standard  
- Machine‑Verifiable‑Law Standard  
- Constitutional Safety Layer Standard  
- Cross‑Domain Projection Standard  
- Meta‑Ledger Standard  
- Meta‑Governance Standard  

PERM governs:

- RUAX‑Permissioning‑Standard.md (mid‑layer)  
- Domain‑specific permissioning protocols  
- Identity and authority management systems  

---

## 11. Versioning and Amendments

This standard is maintained by FA
