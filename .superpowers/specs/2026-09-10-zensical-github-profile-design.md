# Design Specification: Zensical-Powered GitHub Profile & Portfolio Site

- **Target Owner:** Arpan Chatterjee (`btwseeu78`)
- **Hosting URL:** `https://btwseeu78.github.io/arpan-profile/`
- **Engine:** Zensical Static Site Generator (Python/Rust SSG)
- **Deployment:** GitHub Pages via GitHub Actions workflow
- **Date:** 2026-09-10

---

## 1. Objectives & Scope
Create a professional, interactive single-page portfolio and engineering profile website hosted on GitHub Pages at `btwseeu78.github.io/arpan-profile/` using Zensical.

The site showcases Arpan Chatterjee's 9 years of Senior Platform Engineering experience across Kubernetes, cloud infrastructure (GCP/Azure), GitOps pipelines, Open Source CNCF contributions, and modern automation (including Model Context Protocol).

---

## 2. Architecture & File Structure

```text
arpan-profile/
├── .github/
│   └── workflows/
│       └── deploy.yml              # Automated build & deploy to GitHub Pages
├── docs/
│   ├── assets/
│   │   └── stylesheets/
│   │       └── extra.css           # Custom styling for metric cards and tags
│   └── index.md                    # Main single-page interactive portfolio
├── .gitignore                      # Python venv, site/ build output, cache
├── pyproject.toml                  # Python package configuration with zensical
├── requirements.txt                # pip dependency specification
└── zensical.toml                   # Zensical site configuration
```

---

## 3. Zensical Configuration (`zensical.toml`)
- **Project Identity:**
  - `site_name`: "Arpan Chatterjee | Senior Platform Engineer"
  - `site_url`: "https://btwseeu78.github.io/arpan-profile/"
  - `site_description`: "Senior Platform Engineer specializing in Kubernetes, GitOps, Cloud Migrations, and CNCF open source."
  - `repo_url`: "https://github.com/btwseeu78/arpan-profile"
- **Theme & Navigation:**
  - Palette toggle: automatic dark and light mode support
  - Navigation features: right-hand table of contents, search, back-to-top button
  - Extra stylesheet: `assets/stylesheets/extra.css`

---

## 4. Content Architecture (`docs/index.md`)

The single page will feature structured sections:

### 4.1 Hero & Executive Overview
- Name: **Arpan Chatterjee**
- Title: **Senior Platform Engineer | Kubernetes, Cloud Infrastructure & Migration Specialist**
- Contact & Metadata Pills: `🎯 9+ Years Experience`, `📍 Kolkata, India`, Email (`arpan.b.chatterjee@gmail.com`), GitHub (`github.com/btwseeu78`), LinkedIn (`linkedin.com/in/arpan-chatterjee-85479880`), Medium (`btwseeu78.medium.com`).
- **Core Focus & Keyword Skills Strip (replaces large metric boxes for freelance/consulting focus):**
  - `☸️ Kubernetes` &bull; `⎈ Helm` &bull; `🐙 Argo Ecosystem (ArgoCD, Rollouts, Workflows)` &bull; `🐹 Go (Golang)` &bull; `⚙️ Kubebuilder (Custom Operators)` &bull; `🔀 Gateway API` &bull; `☁️ Terraform & Crossplane` &bull; `📡 OpenTelemetry` &bull; `🚀 Cloud Migration` &bull; `🤖 MCP (Model Context Protocol)`

### 4.2 Core Competencies Matrix
- **Kubernetes & Containers:** Kubernetes, Helm, Gateway API, Kubebuilder (Custom Operators), Kueue, Argo Rollouts, Sveltos, Cluster Autoscaler.
- **Infrastructure as Code & Cloud:** Terraform, Crossplane, Google Cloud (GKE), Microsoft Azure, AWS, Self-Service APIs.
- **GitOps & Delivery:** ArgoCD, Flux (Flux2), Kargo, Argo Workflows, Argo Rollouts, Flagger, GitLab CI, Tekton, Kaniko.
- **Observability & FinOps:** OpenTelemetry, Datadog, Prometheus, Grafana, Distributed Tracing, Spot Orchestration, Resource Right-Sizing.
- **Security & Compliance:** Open Policy Agent (OPA), CrowdStrike Falcon, Oligo Runtime Security, Zero-CVE Production Hardening.
- **Programming & Automation:** Golang, Python, Ansible, Bash, Model Context Protocol (MCP) for AI-to-Infrastructure automation.

### 4.3 Professional Experience (Chronological)
- **Renault Nissan Technology & Business Centre India (RNTBCI)** (Jan 2025 – Present)
  - Role: *Platform Engineer*
  - Key Outcomes: 35 GKE clusters, 10,000+ workloads, Gateway API handling 6,000–7,000 URLs, 40% MTTD reduction via OpenTelemetry, 30% cloud spend reduction via FinOps, GitOps pipeline automation under 4 hours, MCP AI-to-infra automation.
- **Accenture India** (Sep 2021 – Dec 2024)
  - Role: *Transformation Specialist*
  - Key Outcomes: Migrated 30+ services on-prem to cloud, reusable multi-cloud Terraform modules (60% faster provisioning), Crossplane self-service APIs (45% ticket reduction), custom Kubebuilder operators, Datadog observability.
- **PwC India** (Oct 2020 – Sep 2021)
  - Role: *Associate Cloud Engineer*
  - Key Outcomes: 3 high-performance K8s clusters for data platform processing >500GB daily, 99.95% availability.
- **Tata Consultancy Services (TCS)** (Sep 2019 – Oct 2020)
  - Role: *Associate Cloud Engineer*
  - Key Outcomes: Monitoring architecture across 20+ servers (45% incident reduction), Ansible automation for 200+ servers cutting patch cycles from 2 weeks to 3 days.
- **Capgemini India** (Nov 2016 – Sep 2019)
  - Role: *Associate Consultant*
  - Key Outcomes: Synthetic monitoring across 15+ user journeys for McDonald's Cloud Application, Docker & Kubernetes internal deployments.

### 4.4 Open Source Contributions & Publications
- `kubernetes-sigs/kueue`: Contributed Helm chart enhancement parametrizing IngressClass, PriorityClass, and imagePullSecrets (merged PR #5815).
- `GoogleCloudPlatform/kubectl-ai`: Added Server-Sent Events (SSE) transport mode for MCP server integration (merged PR #418).
- `aquasecurity/trivy-operator`: Added `_json_key` authentication support for private GCR/GAR image scanning (merged PR #1404).
- `repo-lister`: Maintainer of open-source Go CLI tool for cross-registry image management with Sigstore/Cosign signing (`github.com/btwseeu78/repo-lister`).
- **Technical Articles**: Published on Kubernetes, GitOps, Helm, Kind, and Tekton at `btwseeu78.medium.com`.

### 4.5 Certifications & Education
- **Certifications:**
  - Certified Kubernetes Application Developer (CKAD) (Alumni / Previous)
  - Google Cloud Certified Associate Cloud Engineer (GCP ACE)
  - Microsoft Certified: Azure Fundamentals (AZ-900)
  - Red Hat Certified Engineer (RHCE)
  - Red Hat Certified Administrator (RHCSA)
- **Education:**
  - B.Tech in Computer Science and Engineering — Meghnad Saha Institute of Technology, Kolkata (Grade: 7.8/10)

---

## 5. GitHub Pages Deployment Pipeline (`.github/workflows/deploy.yml`)
- Triggered on push to `main` branch and manual dispatch.
- Workflow job steps:
  1. Checkout repository with `actions/checkout@v4`.
  2. Configure GitHub Pages environment with `actions/configure-pages@v5`.
  3. Set up Python environment with `actions/setup-python@v5`.
  4. Install `zensical` from PyPI (`pip install zensical`).
  5. Execute `zensical build --clean`.
  6. Upload artifact from `site/` with `actions/upload-pages-artifact@v3`.
  7. Deploy artifact to GitHub Pages with `actions/deploy-pages@v4`.
