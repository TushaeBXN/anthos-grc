# AI Governance Policy

**Organization:** Anthos Platform (Brian Tushae Thomas)  
**Frameworks:** NIST AI RMF 1.0 · ISO/IEC 42001:2023  
**Version:** 1.0  
**Effective Date:** July 2026  
**Classification:** Internal

---

## 1. Purpose

This policy establishes the principles, accountability structure, and operational controls that govern the development, deployment, and ongoing management of AI systems built under the Anthos platform. It applies to all AI systems — regardless of size, stage, or deployment status — and serves as the parent document for all system-specific governance cards.

The policy is designed to be proportionate: lightweight controls for low-risk systems, structural safeguards for high-risk and dual-use systems.

---

## 2. Scope

This policy applies to:

- All AI models, agents, and AI-augmented tools developed or operated by Anthos
- All deployment environments: local, cloud, and hybrid
- All downstream products or interfaces that expose AI capability to end users

---

## 3. Governing Frameworks

| Framework | Application |
|---|---|
| **NIST AI RMF 1.0** | Primary risk management structure (GOVERN, MAP, MEASURE, MANAGE) |
| **ISO/IEC 42001:2023** | AI management system requirements — accountability, documentation, continual improvement |
| **NIST SP 800-53** | Security and privacy controls applied to AI system infrastructure |
| **OWASP LLM Top 10** | Vulnerability guidance for language-model-based components |

---

## 4. Risk Tier Definitions

All AI systems are assigned a risk tier at intake. Tier assignment drives the required controls and review cadence.

| Tier | Label | Description | Examples |
|---|---|---|---|
| **Tier 1** | Minimal | No consequential real-world decisions; output is informational only; easily reversible | Code autocomplete, grammar tools |
| **Tier 2** | Low | Output informs decisions but a human reviews before acting; limited harm if wrong | Summarization, classification aids |
| **Tier 3** | High | Output directly influences security, compliance, or safety decisions; material harm if wrong | CyberGuard AI, compliance scoring systems |
| **Tier 4** | Unacceptable (restricted) | Unrestricted deployment would present unacceptable risk; dual-use capability requiring structural containment | Kerrigan-Fantasma in external/unrestricted mode |

Tier 4 does not mean the system cannot be developed — it means it cannot be deployed without structural safeguards reducing effective risk to Tier 3 or below.

---

## 5. Accountability

| Role | Responsibility |
|---|---|
| **Platform Owner (Tushae Thomas)** | Final accountability for all systems; sole approver for Tier 3/4 scope changes, new deployments, and responsible-disclosure decisions |
| **System Owner** | Maintains the system-specific governance card; ensures controls are implemented and logs are current; escalates anomalies to the Platform Owner |
| **Developer / Operator** | Implements controls defined in the governance card; does not expand system scope or autonomy without Platform Owner approval |

For the current scale of the Anthos platform, the Platform Owner and System Owner roles are held by the same individual. As the platform scales, these should be separated.

---

## 6. Authorization Requirements

Before any AI system takes action against a target outside its authorized environment, the following must be documented:

1. **Legal authorization** — written permission from the system owner of the target (e.g., signed rules of engagement, bug bounty scope confirmation, contract)
2. **Scope definition** — explicit boundaries of what the system is authorized to do, to what targets, and for how long
3. **Platform Owner sign-off** — recorded in the system's governance card or a separate authorization memo

This requirement is absolute for Tier 3 and Tier 4 systems. No verbal authorization is sufficient.

---

## 7. Controls by Tier

| Control | Tier 1 | Tier 2 | Tier 3 | Tier 4 |
|---|---|---|---|---|
| Governance card required | — | Recommended | **Required** | **Required** |
| Inventory entry required | — | Recommended | **Required** | **Required** |
| Human review before consequential action | Recommended | **Required** | **Required** | **Required** |
| Execution logging | — | Recommended | **Required** | **Required (immutable)** |
| Network isolation from production | — | — | Recommended | **Required** |
| Responsible-disclosure review before publication | — | — | Recommended | **Required** |
| Kill-switch / deauthorization procedure | — | — | Recommended | **Required (tested)** |
| Quarterly risk review | — | — | **Required** | **Required** |
| Capability-milestone review | — | — | Recommended | **Required** |

---

## 8. Data Handling

- AI systems should process the minimum data necessary to perform their stated function.
- Sensitive data (credentials, PII, system telemetry) must not be transmitted outside the authorized environment without explicit user consent.
- Training data derived from real incidents or real system activity must be anonymized before use in any externally shared artifact.

---

## 9. Disclosure & Publication

- Functional exploit code, offensive automation, or model weights with significant dual-use potential are not published without a responsible-disclosure review.
- System governance cards may be published publicly to demonstrate governance posture; they must not include information that itself constitutes a security risk (e.g., specific vulnerability details, internal network topology).
- AI-generated compliance scores and security findings are labeled as self-assessments; they are not represented as equivalent to formal audits or certifications.

---

## 10. Review & Maintenance

| Trigger | Action |
|---|---|
| **Quarterly** | Review all Tier 3/4 governance cards; update risk scores if context has changed |
| **Capability milestone** | Re-assess risk tier and controls for any system that increases autonomy, network reach, or target scope |
| **Framework revision** | Update policy and affected governance cards when NIST, ISO, or a covered compliance framework publishes a material revision |
| **Incident** | Document incident, root-cause, and corrective action in the affected system's governance card within 72 hours |

---

## 11. Relationship to System-Specific Cards

This policy defines the floor. Each system's governance card in [`governance-cards/`](governance-cards/) documents:

- The system-specific risk assessment
- Which controls from Section 7 are implemented and how
- Any system-specific prohibited uses or additional safeguards beyond this policy
- The escalation path for that system

Where a governance card is more restrictive than this policy, the governance card governs.

---

*Version 1.0 — July 2026*  
*Platform Owner: Brian Tushae Thomas*
