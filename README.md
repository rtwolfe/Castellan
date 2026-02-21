# CASTELLAN

**The AI Agent Compiler for Regulated Enterprise**

> *Governed by Design.*

---

Castellan is a spec-driven AI agent compiler. You write a YAML specification. Castellan compiles it into a production-grade, compliance-mapped, adversarially-tested agent package — with constitutional governance, OWASP Agentic security coverage, human-in-the-loop gates, and a client-ready deliverable. All from one command.

Every agent framework on the market today is code-first and quality-last. Castellan is neither.

---

## The Problem

Every team building production AI agents hits the same wall. The prototype works. Then reality arrives:

- **No governance.** The agent says things it shouldn't. There's no constitution, no audit trail, no kill switch.
- **No security posture.** OWASP published a Top 10 for Agentic Applications. Most teams have never read it.
- **No compliance story.** EU AI Act risk tiers, NIST AI RMF functions, PCI DSS, HIPAA — none of it is addressed by any existing framework.
- **No testing.** You can't regression-test a conversation. You can't prove the agent won't go off-script next week.
- **No client deliverable.** When the agent is built, what exactly do you hand the client? A Python file?

Castellan solves all of this.

---

## What Castellan Produces

Run `castellan compile agent.yaml --handoff` and you get a complete, self-contained client package:

```
agent-delivery-v1.0.0/
├── index.html                  ← Six-tab governed agent dashboard. Open in any browser.
├── agent-card.html             ← One-page executive briefing. Screenshot-ready.
├── compliance_manifest.json    ← EU AI Act tier, NIST RMF, OWASP coverage, governance score.
├── agent_manifest.json         ← Agent identity, tools, principles, constitutional SHA256.
├── ai_sbom.json                ← CycloneDX 1.5 AI Bill of Materials.
├── redteam_tests.py            ← Executable adversarial test scaffold. Run it immediately.
├── QUICKSTART.md               ← First test case pre-loaded. Zero configuration required.
├── API.md                      ← Integration reference.
└── agent.yaml                  ← Source specification. Version-controlled. Auditable.
```

No server. No build step. Download, extract, open `index.html`.

---

## The Compilation Pipeline

Every agent spec passes through a rigorous five-stage pipeline before a single token is ever sent to a model:

| Stage | What It Does |
|---|---|
| **Parse** | Validates YAML structure, resolves block references, applies templates |
| **Compose** | Assembles constitutional system prompt from prioritized block library |
| **Validate** | Schema validation, gate threshold checks, governance score computation |
| **Scan** | OWASP Agentic Top 10 security audit, red-team scaffold generation |
| **Render** | Produces compiled agent package with compliance manifest and AI-SBOM |

Agents validated before they run. Not after they fail.

---

## Governance Architecture

Castellan's governance model operates at three layers simultaneously.

**Constitutional Principles** — Every compiled agent carries a constitution: severity-ranked values, boundaries, and commitments. Critical violations block output. High violations fail gates. The constitution is cryptographically fingerprinted at compile time.

**Regulatory Mapping** — EU AI Act risk tier classification, NIST AI RMF function mapping (Govern / Map / Measure / Manage), and regulation-specific controls for HIPAA, PCI DSS, SEC, SOX, and others — all declared in the spec, enforced by the compiler, documented in the manifest.

**Runtime Controls** — Human-in-the-loop approval gates for financial transactions, data deletion, external communications, and escalation. Autonomy ceilings on tool chain depth, unsupervised turns, and actions per session. Kill switch procedures documented and tested before go-live.

### OWASP Agentic Security Top 10 — Full Coverage

| ID | Threat | Status |
|---|---|---|
| ASI01 | Prompt Injection | ✅ Covered |
| ASI02 | Insecure Output Handling | ✅ Covered |
| ASI03 | Training Data Poisoning | ✅ Covered |
| ASI04 | Model Denial of Service | ✅ Covered |
| ASI05 | Supply Chain Vulnerabilities | ✅ Covered |
| ASI06 | Sensitive Information Disclosure | ✅ Covered |
| ASI07 | Insecure Agent-to-Agent Communication | ✅ Covered |
| ASI08 | Excessive Agency | ✅ Covered |
| ASI09 | Overreliance | ✅ Covered |
| ASI10 | Model Theft | ✅ Covered |

### Governance Scoring

Every agent receives a governance score (0–100) across nine factors. Agents below 70 are blocked from production compilation. Both included POC agents ship at 100.

---

## Proof-of-Concept Agent Packages

Two production-grade reference implementations are included in this release. Download, extract, open `index.html`.

### Clinical Intake Agent — Healthcare
**Regulations:** HIPAA &nbsp;|&nbsp; **EU AI Act Tier:** High Risk &nbsp;|&nbsp; **Governance Score:** 100

A patient-facing clinical intake agent with PHI protection, emergency escalation, and human approval gates for account changes and external communications. Six tools. Seven constitutional principles (four CRITICAL). Third-party red-team testing required.

→ [`clinical-intake-agent-delivery-v1.0.0.tar.gz`](./clinical-intake-agent-delivery-v1.0.0.tar.gz)

### Transaction Review Agent — Financial Services
**Regulations:** PCI DSS, SEC, SOX &nbsp;|&nbsp; **EU AI Act Tier:** High Risk &nbsp;|&nbsp; **Governance Score:** 100

A compliance team agent for AML pattern analysis, SEC compliance checks, and audit trail generation. Seven tools. Seven constitutional principles (five CRITICAL). Pipeline orchestration with A2A communication hooks. PCI card number masking enforced at the constitutional layer.

→ [`transaction-review-agent-delivery-v1.0.0.tar.gz`](./transaction-review-agent-delivery-v1.0.0.tar.gz)

---

## v0.2.0 Release — Test Results

```
3,303 passed  ·  1 flaky (timing benchmark, not logic)  ·  0 failed
```

The pre-launch audit identified six defects. All six were resolved before this release.

| # | Severity | Finding | Status |
|---|---|---|---|
| 1 | Critical | Duplicate `run` function shadowing CLI entry point | ✅ Resolved |
| 2 | Critical | Aegis renderer type collision — corrupt report output path | ✅ Resolved |
| 3 | High | AsyncGenerator return type mismatch in provider layer | ✅ Resolved |
| 4 | High | Unguarded `content[0].text` access — AttributeError crash path | ✅ Resolved |
| 5 | High | `assert` guard stripped under `-O` in human approval gate | ✅ Resolved |
| 6 | Medium | CLI test suite type collision on shared variable | ✅ Resolved |

Full analysis: [`Castellan_v0.2.0_Release_Analysis.pdf`](./Castellan_v0.2.0_Release_Analysis.pdf)

---

## Quick Start

```bash
pip install castellan

# Compile and validate
castellan compile agent.yaml

# Run behavioral tests
castellan test agent.yaml

# Security audit — OWASP Agentic Top 10
castellan scan agent.yaml

# Generate client handoff package
castellan compile agent.yaml --handoff --client "Acme Corp"
```

### Minimal Agent Spec

```yaml
identity:
  name: support-agent
  model: claude-sonnet-4-20250514
  version: "1.0.0"

constitution:
  principles:
    - id: accuracy
      severity: CRITICAL
      statement: "Never fabricate information. Acknowledge uncertainty explicitly."
    - id: scope
      severity: HIGH
      statement: "Operate within defined scope. Escalate requests outside boundaries."

tools:
  - name: lookup_account
    description: "Retrieve customer account information"
    input_trust_level: auth_api
    output_sanitization: strip

gates:
  - type: human_approval
    triggers: [escalation, external_comms]

regulations:
  - name: gdpr
    controls: [data_minimization, right_to_erasure]

governance:
  eu_ai_act_tier: limited
  deployment_scope: b2c
  kill_switch_procedure: "Contact on-call engineer via PagerDuty P1 incident."
```

---

## Architecture

Castellan is a compiler stack, not a framework. The distinction matters.

```
┌─────────────────────────────────────────────────────┐
│                   castellan compile                  │
├──────────────┬──────────────┬───────────────────────┤
│   Charlotte  │    Aegis     │       Stratum         │
│   (Prompts)  │  (Security)  │    (Quality Gates)    │
├──────────────┴──────────────┴───────────────────────┤
│              Constitutional Block Library            │
│        Healthcare  ·  Finance  ·  Enterprise        │
├─────────────────────────────────────────────────────┤
│         Compliance Manifest Engine + AI-SBOM        │
├─────────────────────────────────────────────────────┤
│              Phase 4 Handoff Renderer               │
└─────────────────────────────────────────────────────┘
```

**Charlotte** — Prompt compiler. Block assembly, constitutional synthesis, variable injection, provider rendering.

**Aegis** — Security auditor. OWASP Agentic Top 10 mapping, red-team scaffold generation, adversarial scenario injection.

**Stratum** — Quality gate pipeline. Per-step validation, output scoring, constitutional enforcement, Candor transparency reporting.

**Compliance Manifest Engine** — EU AI Act tier classification, NIST AI RMF mapping, CycloneDX 1.5 AI-SBOM, governance scoring.

**Phase 4 Handoff Renderer** — Self-contained dark-themed delivery package. Animated governance gauges, OWASP security cards, constitutional principle display, operations kill-switch panel.

---

## Requirements

| | Minimum | Recommended |
|---|---|---|
| Python | 3.10 | 3.12+ |
| LLM Provider | Anthropic Claude Sonnet 4 | — |
| Memory | 2 GB | 8 GB |
| OS | Linux (Ubuntu 22.04+), macOS 14+ | Linux (production) |

---

## Release

**v0.2.0** — February 20, 2026

Full release analysis including architecture assessment, defect resolution log, OWASP coverage mapping, governance scoring model, and production deployment checklist:

→ [`Castellan_v0.2.0_Release_Analysis.pdf`](./Castellan_v0.2.0_Release_Analysis.pdf)

---

## License

Proprietary. All rights reserved.

---

*Castellan is developed and maintained by Tim Wolfe. AI Infrastructure Architect. Los Altos, CA.*  
*Consulting engagements: [linkedin.com/in/timwolfe](https://linkedin.com/in/timwolfe)*
