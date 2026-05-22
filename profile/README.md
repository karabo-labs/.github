# karabo-labs

**Production-grade DevOps & MLOps infrastructure. Built from scratch.

[![Self-Hosted Runner](https://img.shields.io/badge/CI-Self--Hosted-2ea44f?logo=githubactions)](https://github.com/karabo-labs)
[![K3s](https://img.shields.io/badge/K3s-Production-FFC61C?logo=k3s)](https://github.com/karabo-labs/k3s-cluster)
[![MLflow](https://img.shields.io/badge/MLflow-Tracking-0194E2?logo=mlflow)](https://github.com/karabo-labs)
[![Terraform](https://img.shields.io/badge/Terraform-Multi--Cloud-844EBA?logo=terraform)](https://github.com/karabo-labs/multi-cloud-terraform)
[![Python](https://img.shields.io/badge/Python-3.11%2B-3776AB?logo=python)](https://python.org)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

---

## The Thesis

DevOps and MLOps aren't two disciplines — they're one pipeline. The same rigor you apply to CI/CD, IaC, and observability applies to model training, deployment, and drift monitoring. **karabo-labs** exists to prove that thesis with real infrastructure, real CI pipelines, and real deployed models — all on a single Hetzner VPS.

Everything here runs through a **self-hosted GitHub Actions runner** on that VPS. Every repo, every PR, every deploy — it's all real, all observable, all automated.

---

## The Stack

```
┌─────────────────────────────────────────────────────────────┐
│                     AI/ML Products                            │
│  ┌──────────┐ ┌──────────────┐ ┌──────────────────────────┐ │
│  │ RAG      │ │ ML Observ.   │ │ AI Model Gallery          │ │
│  │ Assistant│ │ Platform     │ │ 4 modalities, 1 pipeline  │ │
│  └────┬─────┘ └──────┬───────┘ └───────────┬──────────────┘ │
│       │              │                      │                 │
│  ┌────▼──────────────▼──────────────────────▼──────────────┐ │
│  │              karabo-ml CLI (pip install)                  │ │
│  │        RAG query · drift check · cluster management     │ │
│  └────────────────────────┬─────────────────────────────────┘ │
│                           │                                    │
│  ┌────────────────────────▼─────────────────────────────────┐ │
│  │         Platform Layer                                     │ │
│  │  ┌─────────────┐  ┌──────────────┐  ┌──────────────────┐ │ │
│  │  │ k3s Cluster  │  │ Multi-Cloud  │  │ GitHub Commenter │ │ │
│  │  │ GitOps +     │  │ Terraform    │  │ GHCR CI/CD       │ │ │
│  │  │ ArgoCD       │  │ Modules      │  │ Distroless       │ │ │
│  │  └─────────────┘  └──────────────┘  └──────────────────┘ │ │
│  └───────────────────────────────────────────────────────────┘ │
│                           │                                    │
│  ┌────────────────────────▼─────────────────────────────────┐ │
│  │         Infrastructure                                    │ │
│  │  ┌─────────────┐  ┌──────────────┐  ┌──────────────────┐ │ │
│  │  │ Hetzner VPS │  │ Self-Hosted  │  │ Monitoring       │ │ │
│  │  │ CX33 · 4C8G │  │ GH Runner    │  │ Netdata + Grafana│ │ │
│  │  │ Ubuntu 24.04│  │ Always-on    │  │ + Prometheus     │ │ │
│  │  └─────────────┘  └──────────────┘  └──────────────────┘ │ │
│  └───────────────────────────────────────────────────────────┘ │
└─────────────────────────────────────────────────────────────┘
```

---

## Repositories

### Platform & Infrastructure

| Repo | What It Does | Why It Matters |
|------|-------------|----------------|
| **[k3s-cluster](https://github.com/karabo-labs/k3s-cluster)** | GitOps-driven K3s on a single node — Ansible, ArgoCD, Helm, cert-manager, Prometheus/Grafana | Production reference architecture for edge Kubernetes. Every design decision documented with trade-offs. |
| **[multi-cloud-terraform](https://github.com/karabo-labs/multi-cloud-terraform)** | Reusable Terraform modules with multi-environment composition, CI validation, security scanning | IaC excellence — Checkov, TFLint, remote state, environment patterns. AWS-first, GCP/Azure ready. |
| **[github-commenter-deployment](https://github.com/karabo-labs/github-commenter-deployment)** | Containerized cloudposse/github-commenter — distroless Docker, GHCR CI/CD | Infrastructure glue. Shows CI/CD pipeline design for containerized tools. |

### AI/ML Products

| Repo | What It Does | Why It Matters |
|------|-------------|----------------|
| **[karabo-ml](https://github.com/karabo-labs/karabo-ml)** | `pip install karabo-ml` — MLOps & Platform CLI (RAG, drift detection, cluster management) | **The hero product.** A pip-installable CLI that ties the whole stack together. PyPI + GHCR distributed. |
| **[rag-devops-assistant](https://github.com/karabo-labs/rag-devops-assistant)** | Production RAG for DevOps docs — FastAPI + Qdrant + OpenTelemetry + k3s | Observability-first RAG with evaluation-gated CI. 9 custom Prometheus metrics, 13-panel Grafana dashboard. |
| **[ml-observability-platform](https://github.com/karabo-labs/ml-observability-platform)** | DistilBERT sentiment analysis + composite drift detection (PSI, confidence, label shift) + auto-retrain | End-to-end MLOps: train → deploy → monitor → retrain. All on $0 infra. |
| **[ai-model-gallery](https://github.com/karabo-labs/ai-model-gallery)** | 4 model modalities under one Gradio app — Vision-Language, Classification, Audio, Object Detection | Multi-model deployment showcase. All running CPU-only on HF Spaces free tier. |
| **[model-deployment-pipeline](https://github.com/karabo-labs/model-deployment-pipeline)** | Canary rollouts, automated rollback, Prometheus metrics, Grafana dashboards | Production deployment patterns for ML models. Prompt injection detection as the use case. |

---

## Key Metrics

| | |
|---|---|
| **Repos** | 8 public, all running through self-hosted CI |
| **CI/CD** | 100% GitHub Actions, self-hosted runner on VPS |
| **Cluster** | Single-node K3s with ArgoCD GitOps, cert-manager, Prometheus/Grafana |
| **Cloud** | Hetzner CX33 — 4 vCPU, 8GB RAM, 80GB SSD — €9.19/mo |
| **Location** | Johannesburg, South Africa (POPIA-compliant) |
| **MLflow** | Experiment tracking server on the same VPS |
| **Monitoring** | Netdata + Prometheus + Grafana + custom dashboards |
| **Distribution** | PyPI (Python packages) + GHCR (Docker images) |

---

## The Philosophy

- **Zero cloud debt.** Everything runs on cheap, predictable infrastructure. No surprise AWS bills.
- **Observability first.** Every service emits metrics before serving traffic. If it's deployed, it's monitored.
- **GitOps everything.** ArgoCD reconciles cluster state. CI gated on quality. No drift, no snowflakes.
- **Documented decisions.** Every architecture choice has a rationale, a trade-off, and a decision record.
- **Portfolio-grade.** Each repo is designed to tell a story in an interview or a resume.

---

## The Connective Tissue

What makes this more than a collection of repos? The **self-hosted GitHub Actions runner** on the VPS. Every repo's CI/CD pipeline runs through it — not GitHub's hosted runners. That means:

- Faster builds (no queue)
- Access to the VPS's local services (MLflow, Qdrant, K3s) during deployment
- Full control over the CI environment
- **$0 in CI compute costs**

The runner is the backbone. Everything else is a tenant on it.

---

*Built by [Karabo Oliphant](https://github.com/DynamicKarabo). DevOps engineer, MLOps builder, automation addict.*
