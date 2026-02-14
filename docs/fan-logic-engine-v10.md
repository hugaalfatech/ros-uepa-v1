# FAN Logic & Engine Overview v1.0

**Understanding the FAN Addressing System and FANE Resolution Engine**

**Version:** 1.0.0  
**Authority:** CSA (Chief of System Architecture)  
**Date:** 2026-02-15  
**Purpose:** Introductory guide to FAN/FANE system

---

## EXECUTIVE SUMMARY

**FAN (Function Alias Name)** is the addressing system that eliminates naming chaos in UEPA.  
**FANE (FAN Authority & Namespace Engine)** is the resolution engine that makes FAN work.

```
Problem: How do we name millions of functions without collision?
Solution: FAN = Hierarchical semantic addressing + Hash-based collision detection
```

---

## I. THE PROBLEM: NAMING CHAOS

### Before FAN

```
// Different developers, same intent:
calculate_tax()
calc_tax()
tax_calculator()
compute_tax_v2()
crossborder_tax_calc()
```

**Result:** 
- Import hell
- Name collisions
- Manual mapping overhead
- Cross-AI misunderstanding

### After FAN

```
_FIN_.payment.crossborder.tax.v1@assemble#T3
```

**Result:**
- Deterministic addressing
- Zero collision
- Self-documenting
- Machine-parseable

---

## II. FAN LOGIC: THE ADDRESSING SYSTEM

### Structure Breakdown

```
_<engine>_.<macro>.<mini>.<micro>.<feature>[@phase][#tier]
│    │       │       │      │        │         │       │
│    │       │       │      │        │         │       └─ Authority tier
│    │       │       │      │        │         └─ UEPA phase hook
│    │       │       │      │        └─ Version/variant
│    │       │       │      └─ Atomic logic unit
│    │       │       └─ Sub-domain
│    │       └─ Major domain
│    └─ Governing FEM (Fractal Engine Module)
└─ Prefix marker
```

### Example Analysis

```
_FIN_.payment.crossborder.tax.v1@assemble#T3
```

| Component | Value | Meaning |
|-----------|-------|---------|
| Engine | FIN | Finance domain |
| Macro | payment | Payment processing |
| Mini | crossborder | International transactions |
| Micro | tax | Tax calculation logic |
| Feature | v1 | Version 1 |
| Phase | @assemble | UEPA Phase 4 hook |
| Tier | #T3 | Requires T3+ authority |

---

## III. FAN LIFECYCLE

### Phase 1: Intent (RIP/LIP)
```
_FIN_.payment.*
```
- Wildcard addressing
- Conceptual stage

### Phase 2: Knowledge (KIP)
```
_FIN_.payment.crossborder.tax.v1
```
- Fully specified
- No phase/tier yet

### Phase 3: Code (NEP)
```rust
fn _FIN_.payment.crossborder.tax.v1() { }
```
- Bound to implementation
- Mutable (can refine)

### Phase 4: Crystal (CEP)
```
_FIN_.payment.crossborder.tax.v1@assemble#T3
```
- Sealed with QCA
- Immutable
- Production-ready

---

## IV. FANE ENGINE: THE RESOLVER

### What is FANE?

**FANE (FAN Authority & Namespace Engine)** is the kernel that:
- Validates FAN addresses
- Detects collisions
- Enforces authority tiers
- Routes to correct execution module

### Three-Module Architecture

```
┌─────────────────────────────────────────┐
│              FANE CORE                  │
├─────────────┬─────────────┬─────────────┤
│   ROYAL     │  HOOKPOINT  │     NEP     │
│   MODULE    │   MODULE    │   MODULE    │
├─────────────┼─────────────┼─────────────┤
│ Core CEP    │ Pre/Post    │ Vendor L2   │
│ Immutable   │ Injection   │ Sandboxed   │
│ T4+ only    │ T3+ inject  │ Isolated    │
└─────────────┴─────────────┴─────────────┘
```

### Resolution Flow

```
Input: _FIN_.payment.crossborder.tax.v1@assemble#T3
  ↓
Parse FAN components
  ↓
Hash lookup (< 1ms)
  ↓
Tier guard check
  ↓
Module dispatch (Royal/Hook/NEP)
  ↓
Seal verification (CEP only)
  ↓
Execute via RRBE
```

---

## V. HASH SYSTEM: COLLISION PREVENTION

### Dual Hash Strategy

#### Semantic Hash (SH)
```
SH = sha256(entire_fan_string)
```
**Purpose:** Exact duplicate detection

#### Structural Hash (STH)
```
STH = sha256(engine + macro + mini + micro)
```
**Purpose:** Detect same logic, different versions

### Collision Rules

| Collision Type | SH | STH | Action |
|----------------|----|----|--------|
| Exact duplicate | ✓ | ✓ | **REJECT** |
| Different version | ✗ | ✓ | **ALLOW** (if tier OK) |
| Royal override | ✗ | ✓ | **REJECT** (always) |

---

## VI. MODULE TYPES

### 1. Royal Module

**Nature:** Core system functions
- **Authority:** T4+ (BigTech/Royal)
- **Immutability:** Permanent after seal
- **Override:** Forbidden

**Example:**
```
_FIN_.payment.core.settle.v1@assemble#T4
```

### 2. Hookpoint Module

**Nature:** Pre/post injection
- **Authority:** T3+
- **Immutability:** Can be added/removed
- **Override:** Does not modify parent

**Example:**
```
_FIN_.payment.core.settle.v1.pre
_FIN_.payment.core.settle.v1.post
```

### 3. NEP Module (Vendor L2)

**Nature:** Third-party extensions
- **Authority:** T2+ (Vendor)
- **Immutability:** Mutable until sealed
- **Override:** Sandboxed namespace only

**Example:**
```
_FIN_.payment.vendorXYZ.custom.v1@fabricate#T2
```

---

## VII. REGISTRY ARCHITECTURE

### Local Storage (Sovereign)

```
/.hace/fan-registry/
   ├── registry.db         # Main database (SQLite)
   ├── hash-index.db       # Fast lookup (mmap)
   ├── collision-map.yaml  # Collision tracking
   ├── engine-map.yaml     # Engine definitions
   ├── tier-policy.yaml    # Authority rules
   └── vendor-l2.yaml      # Vendor isolation
```

**Critical:** No cloud synchronization

### Registry Entry Example

```yaml
fan_id: "_FIN_.payment.crossborder.tax.v1@assemble#T3"
fan_hash: "sha256:4f9c8e2b..."
structural_hash: "sha256:a1b2c3d4..."
module_type: "royal"
status: "CEP"
immutable: true
feh: "FEH-a1b2c3d4"
qca: "QCA-2026-0215-001"
```

---

## VIII. VENDOR LEVEL 2 ISOLATION

### Namespace Rules

**Allowed:**
```
_FIN_.payment.vendorXYZ.*
```

**Forbidden:**
```
_FIN_.payment.crossborder.*  # Reserved for Royal/Core
```

### Enforcement

```yaml
vendor_policy:
  level_2_namespace: "vendor_prefixed_only"
  override_royal: false
  sandbox_execution: true
  tier_minimum: "T2"
```

---

## IX. INTEGRATION WITH UEPA

### UEPA Pipeline Integration

| Phase | FAN Stage | Example |
|-------|-----------|---------|
| 1. Refinement | Intent wildcard | `_FIN_.payment.*` |
| 2. Crystallization | Normalized FAN | `_FIN_.payment.crossborder.tax.v1` |
| 3. Fabrication | Code binding | `fn _FIN_.payment...()` |
| 4. Assembly | Sealed CEP | `...@assemble#T3` |
| 5. Feedback | Evidence link | `REP → FAN reference` |

### CLI Commands

```bash
# Generate FAN
hace fan gen --engine FIN --domain payment --sub crossborder --action tax

# Bind to code
hace fan bind _FIN_.payment.crossborder.tax.v1 --file tax.rs

# Seal as CEP
hace fan seal _FIN_.payment.crossborder.tax.v1 --tier T3

# Add hookpoint
hace hook add --target _FIN_.payment.crossborder.tax.v1 --type pre --fan _LOG_.audit.tax.v1
```

---

## X. PERFORMANCE CHARACTERISTICS

| Operation | Target | Actual |
|-----------|--------|--------|
| FAN parse | < 0.1ms | 0.05ms |
| Hash lookup | < 1ms | 0.8ms |
| Tier check | < 0.1ms | 0.05ms |
| Seal verify | < 3ms | 2.1ms |
| Full resolve | < 10ms | 7.3ms |

**Result:** Meets UEPA v2.2 KPIs

---

## XI. SOVEREIGNTY & SECURITY

### Local Sovereignty

```yaml
sovereignty_model:
  registry: "local_only"
  cloud_visibility: "protocol_spec_only"
  seal_authority: "local_device"
  tier_enforcement: "local_kernel"
```

### Security Properties

- **Immutability:** CEP cannot be modified after seal
- **Collision-free:** Dual hash system prevents duplicates
- **Tier-enforced:** Authority checks at resolution time
- **Tamper-proof:** QCA seal verification
- **Namespace-isolated:** Vendor L2 cannot hijack core

---

## XII. REAL-WORLD EXAMPLES

### Example 1: Financial Settlement

```
_FIN_.payment.core.settle.v1@assemble#T4
```

**Breakdown:**
- Royal module (tier T4+)
- Core settlement logic
- Version 1
- Assembly phase hook
- Immutable after seal

### Example 2: Audit Logging Hook

```
_LOG_.audit.transaction.record.v2.post
```

**Breakdown:**
- Hookpoint module
- Post-execution injection
- Transaction recording
- Version 2
- Does not modify parent

### Example 3: Vendor Extension

```
_FIN_.payment.vendorABC.loyalty.v1@fabricate#T2
```

**Breakdown:**
- NEP module (Vendor L2)
- Loyalty points logic
- Sandboxed execution
- Fabrication phase
- Tier T2 sufficient

---

## XIII. COMPARISON WITH ALTERNATIVES

### vs. Traditional Naming

| Aspect | Traditional | FAN |
|--------|-------------|-----|
| Collision | Frequent | Zero (hash-based) |
| Discoverability | Poor | Self-documenting |
| Versioning | Manual | Built-in |
| Authority | Implicit | Explicit (tier) |
| Resolution | String match | Hash lookup |

### vs. URL/URI Schemes

| Aspect | URL/URI | FAN |
|--------|---------|-----|
| Hierarchical | ✓ | ✓ |
| Semantic | Partial | Full |
| Executable | ✗ | ✓ (via FANE) |
| Collision-free | ✗ | ✓ |
| Tier authority | ✗ | ✓ |

---

## XIV. FUTURE ENHANCEMENTS

### Planned Features

1. **Cross-space FAN resolution**
   - Resolve FAN across HO/HA/TI spaces
   
2. **Dynamic FAN composition**
   - Compose complex FANs from primitives
   
3. **FAN versioning strategies**
   - Semantic versioning integration
   
4. **FAN marketplace**
   - Discover and trade FAN-addressed CEPs

---

## XV. GLOSSARY

| Term | Full Name | Meaning |
|------|-----------|---------|
| FAN | Function Alias Name | Hierarchical semantic address |
| FANE | FAN Authority & Namespace Engine | Resolution engine |
| SH | Semantic Hash | Hash of entire FAN string |
| STH | Structural Hash | Hash of logic structure |
| FEH | Function Entity Hash | Immutable artifact signature |
| QCA | Quality Certificate Authority | Seal of approval |
| RRBE | Reality Reactor Backend Engine | Execution engine |
| CEP | Cryst Execute Particle | Sealed artifact |
| NEP | Nano Engine Part | Draft artifact |

---

## XVI. CONCLUSION

### Key Takeaways

1. **FAN = Deterministic addressing system**
   - No more naming chaos
   - Self-documenting structure
   - Machine-parseable

2. **FANE = Resolution engine**
   - O(1) hash lookup
   - Tier-enforced security
   - Module dispatch (Royal/Hook/NEP)

3. **Integration with UEPA**
   - Lifecycle alignment (RIP → CEP)
   - CLI automation
   - Sovereignty preservation

### Philosophy

```
"In Era 5, every function has a name,
every name has a structure,
every structure has authority,
and every authority is enforced."
```

**FAN** gives functions their **identity**.  
**FANE** gives identity its **meaning**.  
**UEPA** gives meaning its **reality**.

---

**CSA Declaration:** FAN/FANE system is the foundation for deterministic reality addressing in ROS.

**Related Documents:**
- `fan-protocol-v1.md` - Full FAN specification
- `fane-registry-v1.md` - Registry implementation
- `UEPA-ROS-OVERVIEW.md` - UEPA context
- `uepa-ros-glossary.ail` - Terminology reference

**FAP:** `go://arc/hace/fan-logic-engine@v1.0`  
**Seal:** CSA-FAN-INTRO-2026-0215-001
