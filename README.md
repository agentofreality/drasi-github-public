# drasi-project/.github

Org-level configurations, reusable workflows, community health files, and agentic workflow templates for the [Drasi](https://drasi.io) project.

## Repository Structure

```
.github/workflows/          Reusable CI workflows (called via workflow_call)
├── rust-unit-test.yaml      Rust test: caching, Redis, system deps, toolchain
└── rust-lint.yaml           Rust lint: clippy + fmt, caching, system deps

workflow-templates/          Starter templates (shown in Actions → New workflow)
├── rust-unit-test.yml
├── rust-unit-test.properties.json
├── rust-lint.yml
└── rust-lint.properties.json

agentic-workflows/           Copilot agentic workflow source files (.md)
├── README.md                Setup and sync instructions
└── drasi-issue-researcher.md

ISSUE_TEMPLATE/              Org-default issue forms
├── bug.yaml
├── feature.yaml
├── engineering.yaml
└── config.yaml

CODE_OF_CONDUCT.md           Inherited by all repos without their own
CONTRIBUTING.md              Inherited by all repos without their own
SECURITY.md                  Inherited by all repos without their own
pull_request_template.md     Inherited by all repos without their own
AI_POLICY.md                 AI usage policy
MENTORSHIP.md                Mentorship program info
CHECKLIST.md                 Per-repo migration checklist
LICENSE                      Apache-2.0
profile/README.md            Org profile (github.com/drasi-project)
```

## How It Works

### Reusable Workflows

Repos call centralized CI workflows instead of duplicating pipeline definitions:

```yaml
# In any Drasi repo
jobs:
  test:
    uses: drasi-project/.github/.github/workflows/rust-unit-test.yaml@main
  lint:
    uses: drasi-project/.github/.github/workflows/rust-lint.yaml@main
```

See each workflow file for available inputs and defaults.

### Community Health Files

GitHub automatically inherits these files for any repo in the `drasi-project` org that doesn't define its own:

- `CODE_OF_CONDUCT.md`
- `CONTRIBUTING.md`
- `SECURITY.md`
- `ISSUE_TEMPLATE/`
- `pull_request_template.md`

A repo can override any of these by adding its own version.

### Starter Workflow Templates

When someone clicks **Actions → New workflow** in any org repo, they'll see Drasi-specific templates (e.g., "Drasi Rust Unit Tests", "Drasi Rust Lint") auto-suggested when a `Cargo.toml` is detected.

### Agentic Workflows

Copilot agentic workflows cannot be called cross-repo. The `.md` source files are maintained here as the single source of truth, but must be copied to each repo and compiled with `gh aw compile`. See [agentic-workflows/README.md](agentic-workflows/README.md) for instructions.

## Adding a New Repo

See [CHECKLIST.md](CHECKLIST.md) for the full per-repo migration/onboarding checklist.

