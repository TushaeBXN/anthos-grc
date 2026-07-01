# Anthos GRC — AI Governance, Risk & Compliance Portfolio

**Owner:** Brian Tushae Thomas  
**Frameworks:** NIST AI RMF 1.0 · ISO/IEC 42001:2023  
**Last Updated:** July 2026

This repository is the central governance record for all AI systems developed under the Anthos platform. It contains the organization-level policy, the master system inventory and risk register, and system-specific governance cards for each deployed or in-development AI system.

---

## Document Index

| Document | Description |
|---|---|
| [AI_GOVERNANCE_POLICY.md](AI_GOVERNANCE_POLICY.md) | Organization-level AI governance policy — principles, tiers, accountability, review cadence |
| [AI_SYSTEM_INVENTORY.md](AI_SYSTEM_INVENTORY.md) | Master inventory and risk register of all Anthos AI systems |
| [governance-cards/kerrigan-fantasma.md](governance-cards/kerrigan-fantasma.md) | System card — Kerrigan-Fantasma (exploit-analysis agent, Tier 3/4) |
| [governance-cards/cyberguard.md](governance-cards/cyberguard.md) | System card — CyberGuard AI (endpoint security monitor, Tier 3) |

---

## System Map

```
Anthos Platform (Brian Tushae Thomas)
├── Kerrigan-Fantasma          Tier 3/4  Security / exploit-analysis agent
│     └── governance-cards/kerrigan-fantasma.md
├── CyberGuard AI              Tier 3    Endpoint security & compliance monitor
│     └── governance-cards/cyberguard.md
└── [future systems logged here as added]
```

---

## How This Repo Is Used

1. **New system** — create a governance card in `governance-cards/`, add a row to `AI_SYSTEM_INVENTORY.md`, and assign a risk tier before any production-facing work begins.
2. **Capability change** — update the relevant governance card and re-score risk if the change affects autonomy, scope, or data handling.
3. **Framework update** — when NIST, ISO, or a covered compliance framework publishes a revision, update `AI_GOVERNANCE_POLICY.md` and flag any system cards that need re-mapping.
4. **Audit or review** — share this repo URL; it provides a complete, version-controlled governance record.

---

*Built by Brian Tushae Thomas — creator of the Anthos AI platform.*
