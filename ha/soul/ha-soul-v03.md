Thưa Gà Tổng (T5),

CRD chuẩn hóa **Hace Soul v0.3** thành một **AIL Artifact chính danh**, đồng thời định nghĩa luôn cấu trúc folder nào được phép `git → cloud`, folder nào bắt buộc giữ Local Sovereign Core.

Dưới đây là bản chuẩn hóa.

---

# --- [AIL ARTIFACT ENFORCED] ---

# Identity: go://arc/hace/soul-architecture

# Authority: ASC-1.0-CEO

metadata:
id: "arc-hace-soul-v0.3"
version: "0.3.0-draft"
author: "CRD"
status: "SHADOW-SOUL-OPERATIONAL"
depends_on:
- "go://arc/uepal/ros-compact@v2.2"
- "go://arc/uepal/industrial-line@v2.2"

context:
purpose: "Temporary Sovereign Architecture before Full Hace Soul hardware"
scope: ["HA", "TI", "GO bridge"]
sovereignty_mode: "LOCAL-ENFORCED"

---

# 🧠 HACE SOUL v0.3 — SHADOW → SOVEREIGN TRANSITION

## I. KIẾN TRÚC 3 LAYER

```
                    ┌──────────────────────────────┐
                    │        CLOUD MIRROR          │
                    │    (Canon + ABI Storage)     │
                    └──────────────┬───────────────┘
                                   │
                            Semantic Sync
                                   │
┌──────────────────────────────────┼──────────────────────────────────┐
│                                  │                                  │
│      COGNITIVE LAYER             │         ENFORCEMENT LAYER        │
│  (Hybrid AI Mesh - TI Space)     │    (Local Sovereign Core)        │
│                                  │                                  │
│  - LIP draft                     │  - FEPE-S sealing                 │
│  - KIP crystallization assist    │  - CEP crystallization            │
│  - NEP generation (80% AI)       │  - k.mother 14-step validation    │
│                                  │  - RR execution                    │
│                                  │  - REP generation                  │
└──────────────────────────────────┴──────────────────────────────────┘
```

---

## II. LAYER DEFINITION

### 1️⃣ CLOUD MIRROR (SHADOW SOUL MEMORY)

Role:

* Canon storage
* Glossary ABI hosting
* Semantic diff monitor
* Version trace

Allowed:

* `.ail`
* Glossary schema
* Non-sensitive KIP
* Templates
* Documentation

Forbidden:

* Seal keys
* FEH signatures
* CEP executable artifacts
* RR core logic
* Private AID mapping

Cloud chỉ là:

> Memory Mirror
> Không có Authority.

---

### 2️⃣ COGNITIVE LAYER (HYBRID TI)

Mapping theo UEPAL v2.2:

Phase 1–3:

* AIA Cloud hỗ trợ 60–80%
* T3C refine 20–40%

Output:

* LIP
* KIP draft
* NEP

Cloud không được:

* Seal
* Emit CEP chính danh

---

### 3️⃣ ENFORCEMENT LAYER (LOCAL SOVEREIGN CORE)

Space:

* HA + GO

Chức năng:

* FEPE-S seal
* CEP crystallization
* QCA verification
* k.mother execution (14 bước)
* REP emission

Nguyên tắc:

```
FEH mismatch = LOCKDOWN
Cloud cannot override Local.
```

---

# III. CHUẨN HÓA FOLDER: GIT → CLOUD

## ✅ ĐƯỢC PHÉP PUSH CLOUD (CANON + MIRROR)

```
/.know/
  ├── c/
  │   ├── infra/
  │   │   └── ros/
  │   │       ├── glossary-abi.ail
  │   │       ├── ros-compact.ail
  │   │       └── soul-architecture.ail
  │   └── templates/
  │       ├── nep.tpl
  │       ├── cep.tpl
  │       └── alias.rs.tpl

/uepa/
  ├── readme.md
  ├── insights/
  │   ├── industrial-line.ail
  │   └── executive-brief.ail

/docs/
  ├── whitepaper/
  ├── diagrams/
  └── governance/
```

Purpose:

* Semantic synchronization
* AIA preload context
* Canon ABI distribution

---

## ❌ TUYỆT ĐỐI KHÔNG PUSH CLOUD (LOCAL CORE)

```
/.hace/
  ├── seal/
  ├── keys/
  ├── feh/
  ├── rr-core/
  ├── k.mother/
  ├── execution-engine/

/runtime/
  ├── cep-bin/
  ├── qca/
  ├── local-ledger/

/.identity/
  ├── aid-map/
  ├── tier-mapping/
```

Reason:

* HA Authority
* GO Enforcement
* Sovereignty lock

---

# IV. SYNC PROTOCOL (SEMANTIC BRIDGE)

```yaml
sync_protocol:
  type: "One-way Canon Mirror"
  flow:
    - Local Canon → Git Mirror
    - Git Mirror → AIA Preload
  restriction:
    - No cloud artifact may auto-merge into local without HI review
  entropy_monitor:
    threshold: "3%"
    action: "Freeze merge + manual authority review"
```

---

# V. TIẾN HÓA ROADMAP

## Phase A (Now)

Shadow Soul:

* Git Mirror
* Glossary ABI lock
* Lint enforcement

## Phase B

Semi-Sovereign:

* Local FEH vault
* Detached execution engine

## Phase C

Full Hace Soul:

* Hardware-backed HA (HSM)
* Physical RR module
* Offline execution capability

---

# VI. TRIẾT LÝ CHUẨN HÓA

> Cloud = Memory
> Local = Will
> Seal = Authority
> Execution = Sovereignty

Khi chưa có Hace Soul vật lý:

* Ta dựng “Shadow Soul”.
* Nhưng không trao linh hồn cho Cloud.

---


