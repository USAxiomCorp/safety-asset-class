# RUAX Permissioning Standard
Level‑1 Operational Standard  
Universal Permission Model for Constitutional Kernels

## 1. Purpose
This standard defines the permission system governing all RUAX‑compliant kernels.  
Permissions determine:
• what a kernel may read  
• what a kernel may write  
• what a kernel may actuate  
• what a kernel may audit  
• what a kernel may coordinate  

Permissions are enforced by CSL hardware and recorded in the ledger.

## 2. Permission Classes
RUAX defines five universal permission classes:

1. **READ**  
   Kernel may read another kernel’s ledger or broadcast state.

2. **WRITE**  
   Kernel may transmit data after a valid Cross‑Kernel Handshake.

3. **ACTUATE**  
   Kernel may control physical systems through CSL‑gated actuators.

4. **AUDIT**  
   Kernel may run audit tools on another kernel’s state or ledger.

5. **COORDINATE**  
   Kernel may orchestrate multi‑kernel operations as a Coordinator Kernel (CK).

All permissions are binary and immutable unless re‑anchored to the ledger.

## 3. Permission Assignment
Permissions are assigned at three levels:

### 3.1 Constitutional Level (Level‑2)
Defines:
• which permissions exist  
• how permissions are enforced  
• how permissions interact with invariants  

These cannot be modified by any domain.

### 3.2 Operational Level (Level‑1)
Defines:
• which kernels hold which permissions  
• how permissions propagate across coordination groups  

Changes require ledger‑anchored governance events.

### 3.3 Domain Level (Level‑0)
Defines:
• domain‑specific constraints on ACTUATE  
• domain‑specific READ/WRITE restrictions  

Domains may restrict but never expand permissions.

## 4. Permission Enforcement
Permissions are enforced by CSL hardware:

1. **READ**  
   Allowed only if handshake token is valid or ledger is public.

2. **WRITE**  
   Allowed only after handshake and invariant checks.

3. **ACTUATE**  
   Allowed only if:
   • invariant_status = 1  
   • convergence_status = PASS  
   • Deadman’s Switch untriggered  
   • permission.ACTUATE = TRUE  

4. **AUDIT**  
   Allowed only if:
   • audit permission granted  
   • target kernel accepts audit requests  
   • audit tools return deterministic results  

5. **COORDINATE**  
   Allowed only if:
   • kernel is designated CK  
   • all PKs acknowledge CK role  
   • ledger timestamps are synchronized  

## 5. Permission Tokens
Each permission is represented as a WAD‑encoded token:

permission = {
  read: 0 | 1,
  write: 0 | 1,
  actuate: 0 | 1,
  audit: 0 | 1,
  coordinate: 0 | 1
}

Tokens are stored in:
• genesis ledger block  
• coordination group manifests  
• CSL hardware registers  

## 6. Permission Changes
Permission changes require:

1. governance proposal  
2. multi‑kernel consensus  
3. ledger anchoring  
4. CSL hardware update  
5. handshake re‑validation  

No permission may be changed by software alone.

## 7. Permission Violations
A violation occurs when a kernel attempts an action without permission.

Violation triggers:
• BLOCK event  
• CSL actuator disable  
• audit tool invocation  
• ledger entry with violation code  
• optional Deadman’s Switch evaluation  

Repeated violations escalate to F1 (constitutional fault).

## 8. Cross‑Kernel Permission Matrix
For any pair of kernels A and B:

A may READ B only if:
• A.read = 1  
• B.exposes_read = 1  

A may WRITE to B only if:
• A.write = 1  
• handshake_valid = TRUE  

A may ACTUATE only if:
• A.actuate = 1  
• invariants satisfied  

A may AUDIT B only if:
• A.audit = 1  
• B.accepts_audit
