# Zensical GitHub Profile & Portfolio Site Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Build and test a single-page engineering profile and portfolio website using Zensical, configured with custom styling, full resume data, and an automated GitHub Actions deployment pipeline for GitHub Pages at `btwseeu78.github.io/arpan-profile/`.

**Architecture:** A static documentation-as-code site powered by Zensical (Python/Rust SSG) using standard Markdown (`docs/index.md`) with Material-style admonitions, cards, and custom CSS. Project configuration is in `zensical.toml`, dependencies in `pyproject.toml`/`requirements.txt`, and deployment in `.github/workflows/deploy.yml`.

**Tech Stack:** Python 3.12+, Zensical, HTML/CSS, GitHub Actions (Pages workflow), Git.

## Global Constraints
- Target URL: `https://btwseeu78.github.io/arpan-profile/`
- SSG: `zensical` static site generator
- Page format: Single-page portfolio (`docs/index.md`)
- CKAD data accuracy: Mark CKAD as alumni/previous (no unverified future expiry date)
- Clean build: `zensical build --clean` must exit 0 and produce valid HTML in `site/`

---

### Task 1: Project Environment & Dependency Scaffolding

**Files:**
- Create: `pyproject.toml`
- Create: `requirements.txt`
- Create: `.gitignore`

**Interfaces:**
- Consumes: Python 3 environment
- Produces: Installed `zensical` binary in `.venv`

- [ ] **Step 1: Create `.gitignore`**
Define ignore patterns for Python virtual environments (`.venv/`, `__pycache__/`), Zensical build output (`site/`), and local OS artifacts.

- [ ] **Step 2: Create `pyproject.toml` and `requirements.txt`**
Specify `zensical>=0.0.60` as the required package.

- [ ] **Step 3: Setup virtual environment and install dependencies**
Run: `python3 -m venv .venv && source .venv/bin/activate && pip install zensical`
Expected: `zensical --version` executes successfully.

- [ ] **Step 4: Commit**
`git add .gitignore pyproject.toml requirements.txt && git commit -m "chore: setup project dependencies and gitignore"`

---

### Task 2: Zensical Configuration (`zensical.toml`)

**Files:**
- Create: `zensical.toml`

**Interfaces:**
- Consumes: `zensical` CLI
- Produces: Valid configuration file recognized by `zensical build`

- [ ] **Step 1: Write `zensical.toml`**
Configure site metadata:
- `site_name = "Arpan Chatterjee | Senior Platform Engineer"`
- `site_url = "https://btwseeu78.github.io/arpan-profile/"`
- `site_description = "Portfolio & Profile of Arpan Chatterjee - Senior Platform Engineer specialized in Kubernetes, GitOps, and Cloud Migrations"`
- `repo_url = "https://github.com/btwseeu78/arpan-profile"`
- Include extra CSS link: `assets/stylesheets/extra.css`

- [ ] **Step 2: Verify configuration schema**
Run: `source .venv/bin/activate && zensical --help`
Verify that `zensical.toml` is syntactically valid TOML.

- [ ] **Step 3: Commit**
`git add zensical.toml && git commit -m "feat: configure zensical site settings"`

---

### Task 3: Custom Styling (`docs/assets/stylesheets/extra.css`)

**Files:**
- Create: `docs/assets/stylesheets/extra.css`

**Interfaces:**
- Consumes: Zensical theme rendering
- Produces: CSS utility classes for hero metrics grid, badges, and skill tags

- [ ] **Step 1: Author `docs/assets/stylesheets/extra.css`**
Add styles for:
- `.grid-cards`: responsive 2x2 / 4x1 metric cards grid with subtle borders and hover accents.
- `.metric-card`: stat callouts with prominent numbers and descriptive labels.
- `.tag-pill`: inline tech badges with distinct soft background chips.

- [ ] **Step 2: Commit**
`git add docs/assets/stylesheets/extra.css && git commit -m "style: add custom css for metric cards and tags"`

---

### Task 4: Single-Page Profile Content (`docs/index.md`)

**Files:**
- Create: `docs/index.md`

**Interfaces:**
- Consumes: Data extracted from `Arpan_Chatterjee_Resume_1.docx`
- Produces: Complete markdown source for the portfolio

- [ ] **Step 1: Write Hero & Summary Section**
Name, title (Senior Platform Engineer), Kolkata, links to GitHub, LinkedIn, Medium, email, and 4 metric cards (9+ Years, 35 GKE Clusters, 10,000+ Workloads, 99.9% Uptime).

- [ ] **Step 2: Write Core Competencies Matrix**
Categorized tech stack: Kubernetes & Containers, IaC & Cloud, GitOps & Delivery, Observability & FinOps, Security & Compliance, Automation/MCP.

- [ ] **Step 3: Write Experience Section**
Detailed bullet points with bold metrics for RNTBCI (2025-Present), Accenture (2021-2024), PwC (2020-2021), TCS (2019-2020), Capgemini (2016-2019).

- [ ] **Step 4: Write Open Source & Publications Section**
Contributions to `kubernetes-sigs/kueue` (PR #5815), `kubectl-ai` (PR #418), `trivy-operator` (PR #1404), CLI maintainer for `repo-lister`, and Medium blog links.

- [ ] **Step 5: Write Certifications & Education Section**
CKAD (Alumni), GCP ACE, Azure AZ-900, RHCE, RHCSA, and B.Tech CSE (MSIT Kolkata, Grade 7.8/10).

- [ ] **Step 6: Commit**
`git add docs/index.md && git commit -m "feat: add comprehensive single-page profile content"`

---

### Task 5: Build Verification & Local Testing

**Files:**
- Generates: `site/` (static HTML/CSS/JS)

**Interfaces:**
- Consumes: `docs/index.md`, `zensical.toml`, `extra.css`
- Produces: Production-ready static output in `site/`

- [ ] **Step 1: Run Zensical build**
Run: `source .venv/bin/activate && zensical build --clean`
Expected: Output directory `site/` generated with `site/index.html` and 0 errors.

- [ ] **Step 2: Validate generated output**
Check that `site/index.html` contains:
- "Arpan Chatterjee"
- "Senior Platform Engineer"
- "35 GKE clusters"
- "repo-lister"
- Links correctly mapped to `https://btwseeu78.github.io/arpan-profile/`.

- [ ] **Step 3: Commit verification test script or note**
Confirm git working tree is clean.

---

### Task 6: GitHub Actions Workflow (`.github/workflows/deploy.yml`)

**Files:**
- Create: `.github/workflows/deploy.yml`

**Interfaces:**
- Consumes: GitHub Actions runner with Python 3.12+
- Produces: Automated deployment to GitHub Pages on push to `main`

- [ ] **Step 1: Create workflow file**
Add workflow with:
- Push trigger on `main` and `workflow_dispatch`.
- Permissions: `contents: read`, `pages: write`, `id-token: write`.
- Actions: `checkout@v4`, `configure-pages@v5`, `setup-python@v5`, `pip install zensical`, `zensical build --clean`, `upload-pages-artifact@v3`, `deploy-pages@v4`.

- [ ] **Step 2: Commit**
`git add .github/workflows/deploy.yml && git commit -m "ci: add github pages deployment workflow"`

---

### Task 7: Repository README (`README.md`)

**Files:**
- Create: `README.md`

**Interfaces:**
- Consumes: Local run and deploy instructions
- Produces: Clear documentation for repo visitors and local maintenance

- [ ] **Step 1: Create `README.md`**
Document:
- Live URL: `https://btwseeu78.github.io/arpan-profile/`
- Local development commands (`python3 -m venv .venv`, `pip install -r requirements.txt`, `zensical serve`)
- How the automated deployment operates.

- [ ] **Step 2: Commit**
`git add README.md && git commit -m "docs: add repository readme with local run instructions"`
