
<p align="center">
  <img src="docs/WhatsApp Image 2026-03-18 at 13.16.32.jpeg" alt="ByteHubble Logo" width="300"/>
</p>




<div align="center">

<br/>

```
███████╗██╗   ██╗███╗   ██╗████████╗██████╗  █████╗  ██████╗ ██████╗ ███████╗
╚══███╔╝╚██╗ ██╔╝████╗  ██║╚══██╔══╝██╔══██╗██╔══██╗██╔═══██╗██╔══██╗██╔════╝
  ███╔╝  ╚████╔╝ ██╔██╗ ██║   ██║   ██████╔╝███████║██║   ██║██████╔╝███████╗
 ███╔╝    ╚██╔╝  ██║╚██╗██║   ██║   ██╔══██╗██╔══██║██║   ██║██╔═══╝ ╚════██║
███████╗   ██║   ██║ ╚████║   ██║   ██║  ██║██║  ██║╚██████╔╝██║     ███████║
╚══════╝   ╚═╝   ╚═╝  ╚═══╝   ╚═╝   ╚═╝  ╚═╝╚═╝  ╚═╝ ╚═════╝ ╚═╝     ╚══════╝
```

### Autonomous AI-Powered SRE Platform for Kubernetes Self-Healing

<br/>

[![License: MIT](https://img.shields.io/badge/License-MIT-22c55e?style=for-the-badge)](LICENSE)
[![Python 3.11+](https://img.shields.io/badge/Python-3.11+-3b82f6?style=for-the-badge&logo=python&logoColor=white)](https://python.org)
[![Kubernetes](https://img.shields.io/badge/Kubernetes-Ready-326CE5?style=for-the-badge&logo=kubernetes&logoColor=white)](https://kubernetes.io)
[![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=for-the-badge&logo=fastapi&logoColor=white)](https://fastapi.tiangolo.com)
[![React](https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB)](https://reactjs.org)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-316192?style=for-the-badge&logo=postgresql&logoColor=white)](https://www.postgresql.org)

![Version](https://img.shields.io/badge/version-v0.1.0--beta-blue)
![License](https://img.shields.io/badge/license-MIT-green)
![Python](https://img.shields.io/badge/python-3.11-blue)
![Kubernetes](https://img.shields.io/badge/kubernetes-ready-blue)

[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat-square)](CONTRIBUTING.md)
[![GitHub Stars](https://img.shields.io/github/stars/yourusername/zyntraops?style=flat-square)](https://github.com/yourusername/zyntraops/stargazers)
[![Contributors](https://img.shields.io/github/contributors/yourusername/zyntraops?style=flat-square)](https://github.com/yourusername/zyntraops/graphs/contributors)

<br/>

> **ZyntraOps detects, diagnoses, and remediates Kubernetes incidents autonomously —**
> **cutting MTTR from 60 minutes to under 10 seconds.**

<br/>

[**Get Started**](#-quick-start) · [**Architecture**](#-architecture) · [**AI Engine**](#-ai-engine) · [**API Reference**](#-api-reference) · [**Contributing**](#-contributing) · [**Roadmap**](#-roadmap)

<br/>

</div>

---

## 🏢 About ByteHubble

ZyntraOps is developed under **ByteHubble**, a technology initiative focused on building AI-driven infrastructure and cloud-native platforms.

### 🚀 Our Vision

To reinvent how systems operate by combining:

- Artificial Intelligence
- Cloud Infrastructure
- Automation-first engineering

We aim to build systems that:
- Detect problems automatically
- Understand root causes intelligently
- Fix issues without human intervention

### 💡 What We Focus On

- AI-powered DevOps / SRE systems
- Autonomous infrastructure
- Scalable cloud-native platforms
- Intelligent observability

 - Reinvent Databases with AI” is just the beginning — ByteHubble is focused on redefining how modern systems think and act.

 - ## 🧠 What is ZyntraOps?

ZyntraOps is an **open-source autonomous SRE platform** that brings AI-native incident management to Kubernetes. It watches your cluster 24/7, catches failures the moment they happen, performs deep root-cause analysis using a hybrid of deterministic rule logic and large language models, and executes safe remediations — all within seconds.

It is not just another monitoring tool. ZyntraOps closes the entire loop: from **detection → diagnosis → decision → action → validation**, with a full audit trail and real-time dashboard.


## ❗ Why ZyntraOps?

Modern Kubernetes systems fail frequently.

But current workflow is slow:
- Alert → Engineer → Debug → Fix

ZyntraOps automates this loop:
→ Detect → Diagnose → Decide → Fix

This reduces downtime, human effort, and operational cost.

```
Traditional SRE Workflow            ZyntraOps Workflow
────────────────────────            ──────────────────────────
Alert fires       (2–5 min)         Event detected       (<1 sec)
↓                                   ↓
Engineer paged    (5–10 min)        AI collects evidence (<2 sec)
↓                                   ↓
Triage & investigation              Root cause analyzed  (<5 sec)
                  (15–30 min)       ↓
↓                                   Remediation proposed (<7 sec)
Manual remediation                  ↓
                  (10–20 min)       Safety gate validates (<8 sec)
↓                                   ↓
Verify & close    (5–10 min)        Cluster restored     (<10 sec)

MTTR: 37–75 minutes                 MTTR: 5–10 seconds
```

---

## ✨ Core Capabilities

### 🔭 Real-Time Kubernetes Monitoring

Continuously watches the Kubernetes event stream and pod states. No polling delays — instant detection via the event watcher (`detection/`).

| Incident Type | Detection Method |
|---|---|
| `CrashLoopBackOff` | Container exit code + restart count analysis |
| `ErrImagePull` / `ImagePullBackOff` | Registry event pattern matching |
| `OOMKilled` | Memory limit breach + container termination signal |
| `Pending` pods | Scheduling failure + resource constraint analysis |
| Deployment failures | Rollout status + replica health monitoring |

---

### 🤖 Hybrid AI Root Cause Analysis

A two-stage analysis pipeline that maximises accuracy while minimising latency:

```
Stage 1: Deterministic Rule Engine  (agent/pattern_layer.py)
  ├─ Pod logs analysis
  ├─ Container exit code lookup
  ├─ Known error pattern matching
  └─ Confidence scoring  →  >85%: direct result, skip Stage 2
             ↓ (if inconclusive)
Stage 2: LLM-Assisted Deep Analysis  (ai/)
  ├─ Full evidence context injection
  ├─ Multi-source correlation
  ├─ Structured reasoning chain
  └─ Remediation proposal with explanation
```

**Evidence collected per incident:**
- Pod logs (last N lines, configurable) and container exit codes
- `kubectl describe` output via `infrastructure/evidence_collector.py`
- Kubernetes events scoped to the affected namespace
- Restart history and deployment / ReplicaSet configuration

**Supported AI backends:**

| Backend | Mode | Best For |
|---|---|---|
| [Ollama](https://ollama.com) + `llama3` / `qwen2.5:14b` | Local / Air-gapped | Privacy, offline clusters |
| OpenAI `gpt-4o` | Cloud | High accuracy at scale |
| Anthropic `claude-3-5-sonnet` | Cloud | Reasoning-heavy analysis |

Switching providers is a single line in `.env` — no code changes needed.

---

### 🛡️ Human-in-the-Loop Safety Gate

ZyntraOps **never mutates your cluster without passing the safety gate.** Every proposed action is validated by `agent/safety_guardrails.py` before execution.

**Supported remediation actions** (`infrastructure/remediation.py`):
- `restart_pod` — Delete pod and let the controller recreate it
- `rollback_deployment` — Revert to last stable revision
- `scale_deployment` — Adjust replica count
- `recreate_workload` — Full teardown and redeploy

**Built-in safety rules:**

```python
# agent/safety_guardrails.py
MAX_ACTIONS_PER_POD   = 3        # within a 5-minute window
ACTION_WINDOW_SECONDS = 300

BLOCKED_OPERATIONS = [           # hardcoded — cannot be overridden
    "delete_namespace",
    "delete_deployment",
    "delete_persistent_volume",
    "drain_node",
]

HIGH_RISK_ACTIONS = [            # require explicit engineer approval
    "rollback_deployment",
    "recreate_workload",
]
```

---

### 📊 Incident History & Full Audit Trail

Every incident is stored in PostgreSQL (`models/` + `migrations/`) with a complete record:

| Field | Description |
|---|---|
| `timestamp` | Detection time (microsecond precision) |
| `pod_name` / `namespace` | Affected workload |
| `root_cause` | AI-determined root cause |
| `confidence_score` | Analysis confidence (0–1) |
| `remediation_action` | Action taken or proposed |
| `approved_by` | Engineer who approved |
| `resolution_time` | Time from detection to cluster recovery |

Prometheus metrics at `/metrics` — drop into Grafana with the included dashboard (`observability/grafana-dashboard.json`).

---

## 🏗️ Architecture


<p align="center">
  <img src="docs/zyntraops_architecture.svg" alt="ZyntraOps Architecture" width="900"/>
</p>
<p align="center">
  End-to-end flow of ZyntraOps AI-powered SRE system
</p>


---

## 🚀 Quick Start

### Prerequisites

- [Docker](https://docs.docker.com/get-docker/) & Docker Compose v2+
- [kubectl](https://kubernetes.io/docs/tasks/tools/) configured and pointing at your cluster
- [Ollama](https://ollama.ai/) running locally (optional — for local LLM support)

---

### 1. Clone

```bash
git clone https://github.com/your-username/ZyntraOps.git
cd ZyntraOps
```

---

### 2. Configure

```bash
cp configs/.env.example configs/.env
```

Edit `configs/.env`:

```env
# ── AI Backend ─────────────────────────────────────────────────
# Provider: ollama | openai | anthropic
AI_PROVIDER=ollama
AI_MODEL=llama3

OLLAMA_HOST=http://host.docker.internal:11434
OPENAI_API_KEY=sk-...
ANTHROPIC_API_KEY=sk-ant-...

# ── Database ───────────────────────────────────────────────────
DATABASE_URL=postgresql://zyntraops:zyntraops@postgres:5432/zyntraops

# ── Notifications ──────────────────────────────────────────────
SLACK_WEBHOOK_URL=https://hooks.slack.com/services/...

# ── Safety ─────────────────────────────────────────────────────
REMEDIATION_DRY_RUN=false     # true = simulate without executing
MAX_ACTIONS_PER_POD=3
ACTION_WINDOW_SECONDS=300
```

---

### 3. Start All Services

```bash
docker compose up -d --build
```

| Container | Role |
|---|---|
| `sentinelops-backend` | FastAPI + investigation engine |
| `postgres` | Incident + audit storage |
| `prometheus` | Metrics scraping |
| `dashboard` | React frontend on `:3000` |

---

### 4. Verify Health

```bash
# All containers running
docker compose ps

# Backend health check
curl http://localhost:8080/ready

# Tail live logs
docker logs -f sentinelops-backend
```

---

### 5. Verify Ollama (if using local LLM)

```bash
docker exec -it sentinelops-backend sh
curl http://host.docker.internal:11434/api/tags
```

---

### 6. Verify Kubernetes Access

```bash
docker exec -it sentinelops-backend sh
kubectl get pods --all-namespaces
```

---

### 7. Fix metrics-server (if needed)

If `kubectl top pods` returns a `CrashLoopBackOff` on metrics-server:

```bash
# Check status first
kubectl get pods -n kube-system | grep metrics
# metrics-server-7cfb66fcc-svl87   0/1   CrashLoopBackOff   230 (3m30s ago)   24h

# Apply the fix (run inside the backend container)
kubectl patch deployment metrics-server -n kube-system --type='json' -p='[
  {"op":"replace","path":"/spec/template/spec/containers/0/args","value":[
    "--cert-dir=/tmp",
    "--secure-port=4443",
    "--kubelet-preferred-address-types=InternalIP,ExternalIP,Hostname",
    "--kubelet-use-node-status-port",
    "--kubelet-insecure-tls"
  ]}
]'

# Restart and verify
kubectl rollout restart deployment metrics-server -n kube-system
kubectl get pods -n kube-system | grep metrics

# Confirm it works
kubectl top pods
```

---

### 8. Trigger a Test Incident

```bash
# Create a crash-looping pod to trigger the full ZyntraOps pipeline
kubectl run crash-test \
  --image=busybox \
  --restart=Never \
  -- sh -c "exit 1"

# Watch ZyntraOps detect, analyze, and respond in real time
docker logs -f sentinelops-backend
```

---

### 9. Access Services

| Service | URL |
|---|---|
| React Dashboard | http://localhost:3000 |
| API Swagger UI | http://localhost:8080/docs |
| Prometheus Metrics | http://localhost:8080/metrics |
| WebSocket Stream | ws://localhost:8080/ws |

---

## 🤖 AI Engine

ZyntraOps sends the following evidence bundle to the AI engine for every incident:

```json
{
  "pod_name": "api-server-7d9f8b-xkz2p",
  "namespace": "production",
  "logs": "...",
  "events": "...",
  "exit_code": 1,
  "restart_count": 8,
  "describe_output": "..."
}
```

**Example AI response:**

```json
{
  "root_cause": "CrashLoopBackOff (exit 1)",
  "confidence": "high",
  "recommended_action": "restart_pod",
  "explanation": "Container repeatedly crashes on startup with exit code 1. Logs indicate a missing DATABASE_URL environment variable causing the application to fail before accepting connections."
}
```

**How the hybrid decision flow works:**

```
Rule Engine  (fast, deterministic, zero latency)
     +
AI Engine    (context-aware, handles novel edge cases)
     ↓
Decision Engine  →  picks safest action
     ↓
Safety Gate  →  rate limit · risk score · approval check
     ↓
Remediation Engine  →  executes
```

---

## 🧩 Project Structure

```
ZyntraOps/
├── agent/                       # Core investigation pipeline & orchestrator
│   ├── pattern_layer.py         # Rule engine — deterministic pattern matching
│   ├── decision_engine.py       # Hybrid Rule + AI decision logic
│   └── safety_guardrails.py     # Rate limiting, risk scoring, approval gate
├── ai/                          # Multi-LLM AI engine
│   ├── ollama_client.py         # Local LLM via Ollama
│   ├── openai_client.py
│   └── anthropic_client.py
├── api/                         # FastAPI REST + WebSocket layer
├── detection/                   # Kubernetes event watcher
├── infrastructure/
│   ├── evidence_collector.py    # Gathers logs, events, describe output
│   ├── remediation.py           # restart_pod · scale · rollback
│   └── db.py
├── services/
│   └── decision.py              # Decision engine service layer
├── notifications/               # Slack & alert integrations
├── observability/               # Prometheus metrics + Grafana dashboard
├── dashboard/                   # React frontend (live incidents, approvals)
├── models/                      # SQLAlchemy database models
├── migrations/                  # Alembic DB migrations
├── k8s/                         # Kubernetes manifests
│   └── k8s_tools.py             # kubectl wrapper utilities
├── configs/                     # App configuration & .env.example
├── scripts/                     # Setup and helper scripts
├── tests/                       # Unit & integration tests
├── docker-compose.yml
├── Dockerfile
├── alembic.ini
└── main.py                      # Entry point
```

---

## 📊 Observability

Prometheus metrics at `http://localhost:8080/metrics`:

| Metric | Description |
|---|---|
| `zyntraops_incidents_total` | Total incidents detected |
| `zyntraops_ai_latency_seconds` | AI engine response time histogram |
| `zyntraops_mttr_seconds` | Mean time to recovery |
| `zyntraops_active_incidents` | Currently open incidents |
| `zyntraops_remediation_total` | Total remediation actions executed |

Import the included Grafana dashboard: `observability/grafana-dashboard.json`.

---

## 🔒 Safety & Reliability

| Safeguard | Implementation |
|---|---|
| Max 3 actions per pod per 5 min | `agent/safety_guardrails.py` |
| Circuit breaker for AI failures | Auto-fallback to rule engine |
| Dry-run mode | `REMEDIATION_DRY_RUN=true` in `.env` |
| Blocked destructive operations | Hardcoded — cannot be overridden via config |
| High-risk action approval | 1-click approval in React dashboard |
| WebSocket auth + rate limits | Middleware in `api/` |

---

## 🧪 Testing

```bash
# Run all tests
pytest tests/

# With HTML coverage report
pytest tests/ --cov=. --cov-report=html

# Run a specific module
pytest tests/test_decision_engine.py -v
```

---

## 🌐 Frontend Development

```bash
cd dashboard/frontend
npm install
npm run dev
```

The React app connects to the FastAPI backend at `http://localhost:8080` and subscribes to the WebSocket stream at `ws://localhost:8080/ws` for live incident updates.

---

## 📖 API Reference

Full Swagger UI available at `http://localhost:8080/docs` when running locally.

| Method | Endpoint | Description |
|---|---|---|
| `GET` | `/ready` | Health check |
| `GET` | `/incidents` | List all incidents (paginated) |
| `GET` | `/incidents/{id}` | Incident detail with full AI analysis |
| `POST` | `/incidents/{id}/approve` | Approve a proposed remediation |
| `GET` | `/metrics` | Prometheus metrics |
| `WS` | `/ws` | Real-time incident stream |

---

## 🔮 Roadmap

- [ ] Adaptive learning — RCA accuracy improves over time from past incidents
- [ ] Multi-cluster support
- [ ] ML-based anomaly detection (beyond rule pattern matching)
- [ ] Helm chart for production Kubernetes deployment
- [ ] Auto-tuning remediation policies
- [ ] PagerDuty + OpsGenie notification integrations
- [ ] Advanced Grafana dashboards with charts and analytics

---

## 🤝 Contributing

Contributions are welcome! Here's how to get started:

1. Fork the repository
2. Create your feature branch: `git checkout -b feature/amazing-feature`
3. Commit your changes: `git commit -m 'feat: add amazing feature'`
4. Push to the branch: `git push origin feature/amazing-feature`
5. Open a Pull Request

Please ensure all tests pass (`pytest tests/`) and follow the existing code style. See [CONTRIBUTING.md](CONTRIBUTING.md) for detailed guidelines.

---

## 📄 License

Distributed under the MIT License. See [LICENSE](LICENSE) for more information.

---

## 👨‍💻 Author

**Abhishek Mishra** — DevOps · Cloud · AI Systems

> Passionate about building intelligent infrastructure that heals itself.

---

<div align="center">

⭐ If ZyntraOps saves you an on-call at 3 AM, give it a star — it helps others find it!

</div>
