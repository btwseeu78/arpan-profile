# Skills-First Hero & Keyword Strip Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Refactor the profile hero to replace enterprise stat boxes with a subtle experience badge and a prominent keyword skills badge cloud highlighting core freelance competencies (Kubernetes, Helm, Argo Ecosystem, Go, Kubebuilder, Gateway API, Crossplane/Terraform, OpenTelemetry, Cloud Migration, MCP).

**Architecture:** Update CSS in `docs/assets/stylesheets/extra.css` to add modern badge-cloud and skill-chip styles. Update markdown in `docs/index.md` to incorporate the skills banner and experience pill while removing large metric boxes. Rebuild and verify static output with `zensical build --clean`.

**Tech Stack:** Zensical, CSS, Markdown, Python 3.12+.

## Global Constraints
- Target URL: `https://btwseeu78.github.io/arpan-profile/`
- No cluster/workload/uptime box cards in hero
- Keep total experience (`🎯 9+ Years Experience`) subtle in top metadata pills
- Build verification: `zensical build --clean` must exit 0 and render clean HTML

---

### Task 1: Update CSS Styles for Hero & Skills Cloud

**Files:**
- Modify: `docs/assets/stylesheets/extra.css`

**Interfaces:**
- Consumes: Zensical theme CSS variables
- Produces: Styles for `.skills-cloud`, `.skill-pill`, and clean hover states

- [ ] **Step 1: Replace metric card CSS with skill cloud CSS**
Remove `.grid-cards` and `.metric-card`. Add styling for `.skills-cloud`, `.skills-cloud-title`, and `.skill-pill` supporting both light and dark (`slate`) modes.

- [ ] **Step 2: Commit styling change**
`git add docs/assets/stylesheets/extra.css && git commit -m "style: add styles for hero skills cloud and remove metric cards"`

---

### Task 2: Update Profile Content in `docs/index.md`

**Files:**
- Modify: `docs/index.md`

**Interfaces:**
- Consumes: Resume keywords & CSS classes
- Produces: Updated markdown hero

- [ ] **Step 1: Add experience pill to contact/metadata bar**
Include `🎯 9+ Years Experience` in `.contact-bar`.

- [ ] **Step 2: Replace metric boxes with Core Focus & Keyword Skills strip**
Add badges for `☸️ Kubernetes`, `⎈ Helm`, `🐙 Argo Ecosystem`, `🐹 Go (Golang)`, `⚙️ Kubebuilder`, `🔀 Gateway API`, `☁️ Terraform & Crossplane`, `📡 OpenTelemetry`, `🚀 Cloud Migration`, and `🤖 MCP`.

- [ ] **Step 3: Commit content change**
`git add docs/index.md && git commit -m "feat: replace metric boxes with skills-first keyword cloud"`

---

### Task 3: Build & Verification

**Files:**
- Generates: `site/`

**Interfaces:**
- Consumes: `docs/index.md`, `extra.css`
- Produces: Clean HTML build

- [ ] **Step 1: Execute clean build**
Run: `./.venv/bin/zensical build --clean`
Verify exit code 0 and no errors.

- [ ] **Step 2: Verify HTML output and live preview**
Check that `site/index.html` contains the new keyword skills and has removed the stat boxes.

- [ ] **Step 3: Commit any final adjustments**
Ensure working tree is clean.
