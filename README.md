<h1 align="center">🚨 Autonomous DevSecOps Triage Engine PRO</h1>

<h3 align="center">Enterprise-Grade Multi-Agent Incident Commander, Observability Metric Core & Self-Healing Telemetry Pipeline</h3>

<p align="center">
  <img src="https://img.shields.io/badge/Automation-n8n-FF6C37?style=for-the-badge&logo=n8n&logoColor=white" alt="n8n">
  <img src="https://img.shields.io/badge/Inference-Groq_API-F54E42?style=for-the-badge&logo=fastapi&logoColor=white" alt="Groq">
  <img src="https://img.shields.io/badge/Model_Mesh-OpenRouter-007ACC?style=for-the-badge&logo=openaccess&logoColor=white" alt="OpenRouter">
  <img src="https://img.shields.io/badge/Observability-Grafana-F46800?style=for-the-badge&logo=grafana&logoColor=white" alt="Grafana">
  <img src="https://img.shields.io/badge/Security-DevSecOps_Hardened-38A169?style=for-the-badge&logo=dataguard&logoColor=white" alt="Security">
</p>

<p align="center">
  <img src="assets/workflow-canvas.png" alt="Autonomous DevSecOps Triage Engine PRO Workflow Canvas" width="100%">
</p>

---

## 📖 The Evolution: Moving from Basic Automation to LLMOps

The original DevSecOps Triage Engine proved that AI could manage an incident response cycle. However, real production systems do not operate on a happy path. Network APIs fail, rate limits choke models, and independent AI agents can generate conflicting analyses or experience hallucinations.

The **PRO Version** represents a complete paradigm shift in AI orchestration. Instead of blindly executing sequential actions, **Triage Engine PRO** treats LLMs as raw compute resources that must be routed dynamically, audited heavily, and protected by deterministic code boundaries. It utilizes a highly resilient, self-healing **Evaluation Pipeline** featuring parallel agent swarms, confidence-aware QA gatekeeping, granular infrastructure exception handling, and real-time Grafana observability telemetry.

---

## 🏗️ Architectural Topology & Dual-Track Execution

The core runtime separates processing vectors into two distinct, isolated paths: a **Success Track** governed by a high-tier QA Auditor, and an **Error Track** that captures infrastructure faults (like LLM rate limits) to build machine-readable anomaly reports without crashing the pipeline.

```text
                              [ Reactive Incident Webhook ] 
                                             │
                                             ▼
                                  [ Data Preparer Node ]
                                             │
                                             ▼
                                  [ Supervisor Orchestrator ]
                                             │
             ┌───────────────────────────────┴───────────────────────────────┐
             ▼ (SUCCESS TRACK: Parallel Inference Swarm)                     ▼ (FAILURE TRACK: Active Fault Interception)
   ┌───────────────────┼───────────────────┐                         [ Node API Crash / Network Timeout ]
   ▼                   ▼                   ▼                                         │
┌─────────────┐ ┌─────────────┐ ┌─────────────┐                                      ▼
│  Hardcore   │ │   Risk      │ │   PR & Status │                                [ Switch Node ]
│  Developer  │ │  Evaluator  │ │   Manager   │                    ┌──────────────────┼──────────────────┐
└──────┬──────┘ └──────┬──────┘ └──────┬──────┘                    ▼                  ▼                  ▼
       │               │               │                      [429/Timeout]       [400/Bad Input]     [Other Exceptions]
       └───────────────┼───────────────┘                           │                  │                  │
                       ▼                                           └──────────────────┼──────────────────┘
              [ Merge by Position ]                                                   ▼
                       │                                                     [ Set Error Schemas ]
                       ▼                                                             │
              [ Auditing Inspector ]                                                 ▼
                       │                                                     [ Error Informer ]
                       ▼                                                             │
            [ Pass / Fail IF Gate ]                                                  │
             ┌─────────┴─────────┐                                                   │
             ▼ (Pass)            ▼ (Fail/Contradiction)                              │
             │                   └───────────────────┬───────────────────────────────┘
             ▼                                       ▼
  [ Update Grafana Dashboard ]             [ Deterministic Aggregator Layer ]
             │                                       │
             └───────────────────┬───────────────────┘
                                 ▼
                     [ Final Output Formatter ]
                                 │
         ┌───────────────┬───────┴───────┬───────────────┬───────────────┐
         ▼               ▼               ▼               ▼               ▼
  ┌────────────┐  ┌────────────┐  ┌────────────┐  ┌────────────┐  ┌────────────┐
  │ Slack Devs │  │ Gmail HTML │  │ Discord HQ │  │ GitHub     │  │ Telegram & │
  │ Markdown   │  │ Executives │  │ Rich Embed │  │ Bug Ticket │  │ Sheets Log │
  └────────────┘  └────────────┘  └────────────┘  └────────────┘  └────────────┘
```

---

## 🧠 Strategic AI Model Mesh (The Orchestration Rationale)

Relying on a single AI model for complex system architecture leads to context drift and latency bottlenecks. This engine uses a **decoupled multi-model mesh**, routing specific operational tasks to models explicitly optimized for those workloads:

| Agent Role | Assigned Model | Provider | Strategic Rationale |
| --- | --- | --- | --- |
| **Supervisor & QA Inspector** | `llama-3.3-70b-versatile` | Groq | **The State Machine:** Operates on Groq's ultra-low latency compute layers. Chosen for its strict instruction-following capabilities. It acts purely as a routing and validation gatekeeper, ensuring strict JSON schema compliance and cross-examining worker agents for hallucinations. |
| **Hardcore Developer** | `gemini-2.5-flash-lite` | OpenRouter | **The Forensic Analyst:** Code forensics requires parsing massive, chaotic stack traces. Gemini 2.5 Flash offers a massive context window and rapid processing speed, making it perfect for isolating broken scripts and writing pseudo-code patches. |
| **Risk Evaluator** | `gemma-4-31b-it` | OpenRouter | **The Compliance Auditor:** Strong logical weighting and security guardrails make Gemma ideal for threat modeling, calculating CVE impact, and defining strict network isolation protocols without hallucinating fake vulnerabilities. |
| **PR & Status Manager** | `gpt-oss-20b` | OpenRouter | **The Communicator:** Excellent at synthesizing highly technical jargon into clear, empathetic human prose for public status pages, while keeping internal Slack updates crisp and operational. |
| **Error Informer** | `gpt-oss-120b` | Groq | **The Telemetry Engine:** A heavyweight model deployed strictly on the Error Track to parse complex n8n infrastructure crashes and translate raw pipeline failures into actionable executive summaries. |

---

## 📊 Internal Data Ledger Schemas (n8n Data Tables)

To ensure full historical transparency, individual sub-agents interact directly with native **n8n Data Tables**. This ensures an immutable audit log is generated *during* the execution turn, independent of external API delivery success.

### 1. Forensics Databank (`Store Debugging Attempt`)

- `incident_id`
- `target_file`
- `line_number`
- `patch_snippet`

### 2. Compliance Databank (`Store Evaluation Attempt`)

- `incident_id`
- `risk_score`
- `compliance_impact`
- `containment_protocol`

### 3. Communications Databank (`Store Current Status`)

- `incident_id`
- `slack_published`
- `status_page_published`

---

## 🛠️ Advanced Engineering Pillars

### 1. Parallel Agent Swarm & Confidence Scoring

Instead of running agents sequentially, the Developer, Risk Evaluator, and PR Manager execute **simultaneously**. Every agent outputs a **Confidence Score (0.0–1.0)** to quantify certainty.

### 2. The QA Inspector (Gatekeeper Node)

Before any data reaches external systems, the Inspector validates consistency between all AI outputs. Contradictions or low confidence automatically reroute execution to the Error Track.

### 3. Self-Healing Error Track & Regex Switching

Rate limits, bad requests, or infrastructure failures are intercepted through deterministic routing instead of crashing the workflow.

### 4. Real-Time Grafana Telemetry

Every successful execution pushes structured metrics into Grafana, including classifications, risk scores, and confidence metrics.

---

## 🚀 Installation & Setup

### Prerequisites

- n8n v1+
- Groq API Key
- OpenRouter API Key
- GitHub PAT
- Slack/Discord Webhooks
- Telegram Bot
- Gmail OAuth/App Password
- Google Sheets Credentials
- Grafana (Optional)

### Deployment

1. Clone the repository.

```text
n8n-gitops-ci-cd-pipeline/
├── assets/
│   └── workflow-canvas.png
├── workflows/
│   └── n8n-gitops-ci-cd-pipeline.json
├── LICENSE
└── README.md
```

2. Import the workflow JSON into n8n.
3. Connect all credentials.
4. Create three n8n Data Tables:
   - Store Debugging Attempt
   - Store Evaluation Attempt
   - Store Current Status
5. Activate the workflow.

---
