# Machine‑Verifiable Law (MVL) — Top‑Layer Constitutional Standard  
Version: 0.1.0  
Maintainer: Foundation for Aligned Intelligence Truth and Humanity (FAITH)  
Status: Draft Standard  

---

## 1. Purpose and Scope

The Machine‑Verifiable Law (MVL) Standard defines how statutory, regulatory, and constitutional legal sources are transformed into deterministic, machine‑executable predicates within the Constitutional Axiomatic Intelligence (CAI) ecosystem.

MVL establishes:

- The legal‑to‑predicate compilation pipeline  
- The injective mapping from law to CSL predicates  
- Requirements for formal verification  
- Zero‑knowledge legal proof requirements  
- Cross‑jurisdictional encoding rules  
- Immutable legal anchoring  

This is the **root‑layer standard** for all MVL‑related documents.

---

## 2. Legal Source Corpus

MVL applies to all legal sources, including:

- Statutes  
- Regulations  
- Constitutional provisions  
- Administrative rules  
- Industry‑specific compliance frameworks  
- International standards  

Each legal source MUST be:

- Identified  
- Versioned  
- Cryptographically hashed  
- Anchored to a jurisdiction code  

---

## 3. Legal‑to‑Predicate Compilation Pipeline

MVL defines a four‑stage compilation pipeline:

### Stage 1 — Semantic Extraction  
Identify operative legal clauses, obligations, prohibitions, and thresholds.

### Stage 2 — Axiomatic Decomposition  
Convert each clause into a set of atomic legal axioms.

### Stage 3 — Predicate Construction  
Transform each axiom into a Boolean predicate:

\[
d_i : S \times A \rightarrow \{0,1\}
\]

### Stage 4 — Formal Verification  
Each predicate MUST be accompanied by:

- A machine‑checked proof of correctness  
- A traceable link to the legal source  
- A zero‑knowledge proof schema  

This pipeline MUST be deterministic and reproducible.

---

## 4. Injective Mapping Requirement

MVL requires an injective mapping:

\[
A_{\text{cmp}} : \mathcal{L}_{\text{legal}} \rightarrow \mathcal{F}_{\text{stat}}
\]

Where:

- \(\mathcal{L}_{\text{legal}}\) = legal clauses  
- \(\mathcal{F}_{\text{stat}}\) = runtime predicates  

Injectivity ensures:

- No predicate exists without a legal source  
- No legal clause maps to multiple predicates  
- No “regulatory dark matter” is permitted  

This is a mandatory invariant.

---

## 5. Predicate Requirements

Each predicate MUST satisfy:

- Determinism  
- Statelessness  
- WAD‑encoded thresholds  
- Formal verification  
- Zero‑knowledge compatibility  
- Jurisdictional isolation  

A predicate MUST NOT:

- Depend on machine learning  
- Depend on probabilistic inference  
- Depend on mutable configuration  
- Depend on external state  

---

## 6. Jurisdictional Encoding

Each predicate MUST include:

- **jurisdiction_code**  
- **legal_source_hash**  
- **version_id**  
- **effective_date**  
- **sunset_date** (if applicable)  

Jurisdiction codes MUST be immutable.

---

## 7. Zero‑Knowledge Legal Proofs

Each admissibility evaluation MUST produce:

\[
\pi = \text{ZK‑Prove}(d_i(s, a) = 1)
\]

Requirements:

- Proof MUST NOT reveal regulated data  
- Proof MUST be independently verifiable  
- Proof MUST be reconstructible from ledger state  

This ensures legal compliance is provable without exposing private information.

---

## 8. Cross‑Domain Projection Rules

When a legal obligation spans multiple domains:

- Predicates MUST be decomposed into domain‑specific components  
- Projection MUST preserve legal meaning  
- No predicate may contradict its parent clause  

Cross‑domain projection MUST be deterministic.

---

## 9. Immutable Legal Anchoring

Each legal clause MUST be anchored via:

- SHA‑3 hash of the full text  
- Jurisdiction code  
- Version identifier  
- Effective date  

Anchors MUST be:

- Immutable  
- Publicly verifiable  
- Stored in the Meta‑Ledger  

---

## 10. Relationship to Other Standards

MVL depends on:

- CAI Core Standard  
- CSL Specification  
- R3 Operator Standard  
- WAD Arithmetic Standard  

MVL governs:

- MVL‑Constraint‑Definitions  
- MVL‑Enforcement‑Rules  
- MVL‑Integration  
- MVL‑Glossary  
- All subordinate MVL specifications  

---

## 11. Versioning and Amendments

This standard is maintained by FAITH.  
Amendments follow the FAITH Standards Governance Charter.
