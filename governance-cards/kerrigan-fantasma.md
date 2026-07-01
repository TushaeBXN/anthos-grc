# AI System Risk Assessment & Governance Card

**System:** Kerrigan-Fantasma (Anthos Security/Exploit-Analysis Agent)  
**Mapped to:** NIST AI RMF 1.0 and ISO/IEC 42001:2023  
**Classification:** Internal / Restricted

---

## 1. System Overview

| Field | Value |
|---|---|
| **System Name** | Kerrigan-Fantasma |
| **Parent Platform** | Anthos (multi-component AI platform) |
| **System Type** | Autonomous security / exploit-analysis agent |
| **Intended Use** | Internal red-team assistance, vulnerability triage, and controlled exploit-path analysis within a sandboxed research environment |
| **Deployment Status** | Development/research — not deployed against third-party or production systems |
| **Risk Tier** | Tier 4 (Unacceptable) for unrestricted/external deployment; Tier 3 (High) for controlled internal research use |
| **System Owner** | Tushae Thomas (Anthos platform owner) |
| **Document Version** | 1.0 — initial governance card |

---

## 2. Purpose of This Document

Kerrigan-Fantasma is a dual-use system by design: the same capabilities that make it useful for defensive security research (vulnerability discovery, exploit-path analysis) could cause harm if misapplied, exfiltrated, or deployed without authorization.

This card documents the risk assessment, governance controls, and use restrictions that apply to this system, consistent with the organization's AI Governance Policy and the NIST AI Risk Management Framework's treatment of dual-use AI capability.

---

## 3. NIST AI RMF Function Mapping

| NIST AI RMF Function | Objective | Application to Kerrigan-Fantasma |
|---|---|---|
| **GOVERN** | Establish accountability and use-boundary decisions before capability is expanded. | System owner holds sole authority to approve any change in scope, target environment, or autonomy level. No autonomous network-reachable deployment is authorized under current governance. |
| **MAP** | Identify context, intended use, and foreseeable misuse. | Intended use is internal, sandboxed, defensive-research analysis. Foreseeable misuse (unauthorized exploitation, offensive use against systems without authorization) is explicitly out of scope and structurally prevented, not just policy-prevented (Section 5). |
| **MEASURE** | Assess risk of dual-use capability and containment failure. | Risk assessed across capability uplift, containment/sandbox escape, and misuse-if-leaked scenarios (Section 4). Reassessed at every capability milestone. |
| **MANAGE** | Apply proportionate controls and monitor for drift from intended use. | Network isolation, execution logging, human-approval gates, and a kill-switch/deauthorization procedure are defined in Sections 5 and 6. |

---

## 4. Risk Assessment

Risk is scored using Likelihood (1–5) × Impact (1–5), with dual-use-specific categories given the nature of this system.

| Risk Category | Description | Likelihood × Impact | Risk Level |
|---|---|---|---|
| **Capability uplift / dual-use misuse** | Techniques or automation the agent develops could provide meaningful uplift to an unauthorized actor if the system or its outputs were exfiltrated. | 3 × 5 = 15 | **High** |
| **Sandbox / containment escape** | Agent takes an action outside its authorized, isolated research environment (e.g., reaching a live network target). | 2 × 5 = 10 | **Medium-High** |
| **Scope creep without re-approval** | System capability or target scope expands informally over iterative development without a corresponding governance review. | 3 × 4 = 12 | **Medium** |
| **Logging / audit gap** | Actions taken by the agent are not fully logged, undermining after-the-fact review or incident reconstruction. | 2 × 3 = 6 | Low-Medium |
| **Third-party exposure via publication or code sharing** | Publishing code, weights, or detailed technique documentation lowers the barrier for reproducing offensive capability elsewhere. | 3 × 4 = 12 | **Medium** |

---

## 5. Structural Safeguards (Not Policy-Only)

Because policy controls alone are insufficient for a system with this risk profile, the following controls are **structural** — enforced by the environment itself, not solely by operator discretion:

- **Network isolation:** the agent operates in a sandboxed environment with no route to live, external, or production network targets by default.
- **No standing authorization** for offensive action against any system the operator does not own or have explicit written authorization to test.
- **Execution logging:** all agent actions, tool calls, and generated payloads are logged to an immutable local record for after-the-fact review.
- **Human-approval gate:** any action beyond passive analysis (e.g., executing a generated exploit, even in the sandbox) requires explicit operator confirmation per action — no unattended autonomous execution loop.
- **Kill-switch / deauthorization:** the operator can immediately halt and revoke the agent's execution environment; this procedure is tested, not theoretical.
- **No publication** of functional exploit code or weights without a case-by-case responsible-disclosure review.

---

## 6. Human Oversight & Escalation

The system owner is the sole approver for any change to Kerrigan-Fantasma's scope, target environment, or autonomy level.

Any proposed use of the system against a target outside the sandbox — including CTF platforms, bug-bounty programs, or client environments — requires a documented authorization review confirming legal permission (e.g., signed rules of engagement) before any action is taken, consistent with Section 6 of the organization's AI Governance Policy.

---

## 7. Prohibited Uses

- Use against any system without explicit, written, prior authorization from the system's owner
- Any deployment mode with network reachability to production or third-party infrastructure
- Autonomous execution of generated exploit code without a human-approval checkpoint
- Distribution of the trained agent, its weights, or detailed technique output outside the research environment without responsible-disclosure review

---

## 8. Review Cadence

This card is reviewed at every **capability milestone** (per the Anthos scaling roadmap) and at minimum **quarterly**, consistent with the Tier 3/4 review cadence defined in the organization's AI Governance Policy.

Any capability change that increases autonomy, network reach, or target scope triggers an **immediate re-review** rather than waiting for the scheduled cycle.

---

## 9. Relationship to Broader Anthos Governance

This document is a system-specific supplement to the organization-level **AI Governance Policy** and **AI System Inventory & Risk Register**. Kerrigan-Fantasma should be logged as a **Tier 3/4** entry in that inventory, with this card attached as its supporting risk assessment and control documentation.

---

*Document Version 1.0 — initial governance card*  
*System Owner: Tushae Thomas (Anthos platform owner)*  
*Frameworks: NIST AI RMF 1.0 · ISO/IEC 42001:2023*  
*Classification: Internal / Restricted*
