# AI System Inventory & Risk Register

**Platform:** Anthos  
**Owner:** Brian Tushae Thomas  
**Last Updated:** July 2026  
**Frameworks:** NIST AI RMF 1.0 · ISO/IEC 42001:2023

This is the master inventory of all AI systems developed or operated under the Anthos platform. Each row corresponds to a system with a governance card in [`governance-cards/`](governance-cards/). Risk scores use Likelihood (1–5) × Impact (1–5).

---

## System Registry

| System | Type | Tier | Status | Governance Card | GitHub |
|---|---|---|---|---|---|
| **Kerrigan-Fantasma** | Autonomous security / exploit-analysis agent | Tier 3/4 | Development / Research | [governance-cards/kerrigan-fantasma.md](governance-cards/kerrigan-fantasma.md) | [TushaeBXN/kerrigan-fantasma](https://github.com/TushaeBXN/kerrigan-fantasma) |
| **CyberGuard AI** | Endpoint security monitor & compliance platform | Tier 3 | Active (local) | [governance-cards/cyberguard.md](governance-cards/cyberguard.md) | [TushaeBXN/cyberguard](https://github.com/TushaeBXN/cyberguard) |

---

## Risk Register Summary

> Scores use Likelihood (1–5) × Impact (1–5). See [RISK_SCORING_GUIDE.md](RISK_SCORING_GUIDE.md) for a plain-English breakdown of what each number means and how to interpret the risk levels.

| System | Top Risk | Score | Level | Primary Control |
|---|---|---|---|---|
| Kerrigan-Fantasma | Capability uplift / dual-use misuse | 3×5 = 15 | High | Network isolation + human-approval gate |
| Kerrigan-Fantasma | Scope creep without re-approval | 3×4 = 12 | Medium | Capability-milestone governance review |
| Kerrigan-Fantasma | Third-party exposure via publication | 3×4 = 12 | Medium | Responsible-disclosure review required |
| Kerrigan-Fantasma | Sandbox / containment escape | 2×5 = 10 | Medium-High | Structural network isolation (not policy-only) |
| CyberGuard AI | Compliance score misrepresentation | 4×4 = 16 | High | Persistent non-certification disclaimer |
| CyberGuard AI | False negative in threat detection | 3×5 = 15 | High | Detection logic documentation + disclosure |
| CyberGuard AI | Framework mapping drift | 3×3 = 9 | Medium | Annual framework-mapping review |
| CyberGuard AI | Local data over-collection | 2×4 = 8 | Medium | Data minimization; local-only by default |

---

## Tier Distribution

| Tier | Count | Systems |
|---|---|---|
| Tier 1 — Minimal | 0 | — |
| Tier 2 — Low | 0 | — |
| Tier 3 — High | 1 | CyberGuard AI |
| Tier 3/4 — High / Restricted | 1 | Kerrigan-Fantasma |
| Tier 4 — Unacceptable (unrestricted) | 0 | — |

---

## Review Log

| Date | System | Action | Notes |
|---|---|---|---|
| July 2026 | All | Initial inventory created | Baseline governance cards written for both active systems |

---

## Adding a New System

When a new AI system reaches the point of consequential use (producing output that informs a real decision, touches real data, or has network reach), add it here before deployment:

1. Assign a risk tier using the definitions in [AI_GOVERNANCE_POLICY.md §4](AI_GOVERNANCE_POLICY.md#4-risk-tier-definitions)
2. Create a governance card in `governance-cards/<system-name>.md`
3. Add a row to the System Registry above
4. Add all identified risks to the Risk Register Summary
5. Commit and notify the Platform Owner

---

*Platform Owner: Brian Tushae Thomas*
