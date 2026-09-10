# Arpan Chatterjee — Senior Platform Engineer Profile

[![Deploy to GitHub Pages](https://github.com/btwseeu78/arpan-profile/actions/workflows/deploy.yml/badge.svg)](https://github.com/btwseeu78/arpan-profile/actions/workflows/deploy.yml)
[![Live Site](https://img.shields.io/badge/Live%20Site-btwseeu78.github.io%2Farpan--profile-blue)](https://btwseeu78.github.io/arpan-profile/)
[![Built with Zensical](https://img.shields.io/badge/SSG-Zensical-green)](https://zensical.org)

Personal portfolio and engineering profile website of **Arpan Chatterjee**, Senior Platform Engineer specializing in Kubernetes, Cloud Infrastructure, GitOps Delivery Pipelines, and CNCF Open Source.

---

## 🚀 Live Site
The website is automatically built and deployed to GitHub Pages at:
👉 **[https://btwseeu78.github.io/arpan-profile/](https://btwseeu78.github.io/arpan-profile/)**

---

## 📁 Repository Structure

```text
arpan-profile/
├── .github/
│   └── workflows/
│       └── deploy.yml              # GitHub Actions Pages deployment
├── docs/
│   ├── assets/
│   │   └── stylesheets/
│   │       └── extra.css           # Custom styling for metric cards & tags
│   ├── superpowers/                # Design specs & implementation plans
│   └── index.md                    # Main single-page interactive portfolio
├── .gitignore                      # Ignore venv, site/ build output
├── pyproject.toml                  # Python package configuration
├── requirements.txt                # pip dependency specification
├── zensical.toml                   # Zensical configuration file
└── README.md                       # Project documentation
```

---

## 💻 Local Development

### Prerequisites
- Python 3.10+ (Python 3.12 recommended)
- `pip` or `uv`

### 1. Setup Virtual Environment
```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

### 2. Preview Locally with Live Reload
```bash
zensical serve
```
Open your browser at `http://localhost:8000/arpan-profile/` (or `http://localhost:8000/`).

### 3. Build Static Site
```bash
zensical build --clean
```
The static HTML, CSS, and JS output will be generated inside the `site/` folder.

---

## 🚢 Continuous Deployment (GitHub Pages)

Whenever code is pushed to `main` (or triggered via `workflow_dispatch`), the GitHub Actions workflow in `.github/workflows/deploy.yml` will:
1. Check out the repository.
2. Install `zensical`.
3. Run `zensical build --clean`.
4. Upload the generated `site/` directory as an artifact.
5. Deploy to GitHub Pages automatically.

> **Note for GitHub Pages Setup:**  
> In your GitHub repository (`btwseeu78/arpan-profile`), go to **Settings > Pages > Build and deployment > Source** and select **GitHub Actions**.
