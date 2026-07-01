# Risk Scoring Guide

**Platform:** Anthos  
**Applies to:** All governance cards and the AI System Inventory & Risk Register

This guide explains how risks are scored across all Anthos AI systems. The goal is a consistent, readable number that tells you — at a glance — how seriously to treat a given risk and what to do about it.

---

## How the Score Works

Every risk gets two numbers, each from 1 to 5:

**Score = Likelihood × Impact**

Multiply them together. The result falls between 1 and 25.

---

## Likelihood — "How likely is this to happen?"

| Score | Label | What it means in plain terms |
|---|---|---|
| **1** | Very Unlikely | Would require a rare combination of failures or a highly motivated attacker with inside access. Don't lose sleep over it, but document it. |
| **2** | Unlikely | Could happen, but would need something to go noticeably wrong. Worth a control, but not an urgent one. |
| **3** | Possible | A realistic scenario under normal operating conditions. Treat it as something that will eventually occur if left unaddressed. |
| **4** | Likely | Expect this to happen at some point. Controls here are not optional. |
| **5** | Almost Certain | This will happen without active prevention. Immediate structural control required. |

---

## Impact — "How bad is it if this happens?"

| Score | Label | What it means in plain terms |
|---|---|---|
| **1** | Negligible | Inconvenient at most. Easily corrected, no lasting harm. |
| **2** | Minor | Some disruption or data exposure, but contained and recoverable. |
| **3** | Moderate | Noticeable harm — incorrect security conclusions, reputational damage, or a user making a bad decision based on bad output. |
| **4** | Significant | Material harm — an organization fails an audit because of a misleading compliance score, or sensitive data is exposed to the wrong party. |
| **5** | Severe | Could enable real-world exploitation, physical harm, major legal liability, or irreversible damage. The kind of outcome that makes headlines. |

---

## Risk Levels — "What does my score mean?"

| Score Range | Risk Level | What to do |
|---|---|---|
| **1 – 5** | Low | Document it and move on. Review annually. No urgent action needed. |
| **6 – 9** | Medium | Implement a control within the next review cycle. Monitor for changes. |
| **10 – 14** | Medium-High | Prioritize this. A control should be in place or actively in progress. |
| **15 – 19** | High | Treat as a blocking issue. Do not expand system scope or autonomy until this risk has a structural control, not just a policy. |
| **20 – 25** | Critical | Stop. This risk profile makes the system unsafe to operate in its current form. Escalate to Platform Owner immediately. |

---

## Worked Examples

### Example 1 — CyberGuard: Compliance Score Misrepresentation

> A user treats an automated compliance score as equivalent to a formal ISO 27001 audit.

- **Likelihood: 4** — Enterprise users routinely over-rely on automated tooling; this is a realistic, common failure mode.
- **Impact: 4** — An organization could make audit decisions or report false readiness to regulators based on the score.
- **Score: 4 × 4 = 16 → High**
- **Control:** Every score displays a persistent disclaimer that it is a self-assessment, not a certification.

---

### Example 2 — Kerrigan-Fantasma: Capability Uplift / Dual-Use Misuse

> The agent's techniques or outputs are exfiltrated and used by an unauthorized actor.

- **Likelihood: 3** — Requires the system or its outputs to be leaked, which is not trivial — but the system's research context means outputs circulate in documentation and code.
- **Impact: 5** — Functional exploit automation or offensive techniques in the wrong hands could enable real-world attacks against third-party systems.
- **Score: 3 × 5 = 15 → High**
- **Control:** Network isolation, no publication of functional exploit code without responsible-disclosure review, execution logging.

---

### Example 3 — Kerrigan-Fantasma: Logging / Audit Gap

> The agent takes actions that are not fully captured in logs.

- **Likelihood: 2** — Logging is implemented; a gap would require a deliberate bypass or a silent failure.
- **Impact: 3** — Without a full audit trail, after-the-fact incident reconstruction is impossible, but the harm is investigative rather than directly enabling an attack.
- **Score: 2 × 3 = 6 → Medium**
- **Control:** Immutable local execution log; log integrity verified at each session start.

---

## Why This Method

The Likelihood × Impact approach is used by NIST, ISO 27005, and most enterprise risk frameworks because it forces you to think about two separate questions before assigning a priority. A catastrophic outcome that is nearly impossible (1 × 5 = 5) shouldn't consume the same resources as a moderately bad outcome that will definitely happen (5 × 3 = 15). The score reflects both dimensions.

It is intentionally simple. The goal is a consistent, defensible number — not a false sense of mathematical precision. Scores should be reviewed and updated when context changes, not treated as permanent facts.

---

*See [AI_SYSTEM_INVENTORY.md](AI_SYSTEM_INVENTORY.md) for the full risk register.*  
*See [AI_GOVERNANCE_POLICY.md](AI_GOVERNANCE_POLICY.md) for controls by risk tier.*
