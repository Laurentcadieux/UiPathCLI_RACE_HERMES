# UiPath CLI RACE HERMES

Coding Agent project for deploying UiPath Cloud automations via the UiPath CLI (`uip`) and UiPath Skills.

## What This Repo Does

This repository contains:
- **UiPath automation projects** — solutions, agents, and workflows managed via `uip` CLI
- **Deployment configurations** — CI/CD pipeline configs for Orchestrator deployment
- **Skills integration** — UiPath coding agent skills for building, deploying, and operating automations
- **Infrastructure as Code** — Orchestrator folder structure, assets, queues, and environment configs

## Prerequisites

- **UiPath CLI** (`uip`) v1.197+ — installed at `~/.npm-global/bin/uip`
- **Node.js 22+**
- **UiPath Orchestrator** tenant access
- **27 UiPath Skills** installed at `~/.agents/skills/`

## Project Structure

```
UiPathCLI_RACE_HERMES/
├── README.md                    # This file
├── solutions/                   # UiPath solution projects
│   └── README.md
├── agents/                      # UiPath agent projects
│   └── README.md
├── deploy/                      # Deployment configs
│   ├── environments/           # Per-environment configs (dev, test, prod)
│   └── pipelines/              # CI/CD pipeline definitions
├── orchestrator/               # Orchestrator resource definitions
│   ├── folders.json             # Folder structure
│   ├── assets.json             # Shared assets
│   ├── queues.json             # Queue definitions
│   └── environments/           # Environment-specific overrides
├── skills/                      # Custom UiPath skill extensions
│   └── README.md
├── docs/                        # Documentation
│   ├── DEPLOYMENT.md            # Step-by-step deployment guide
│   ├── AUTHENTICATION.md        # Auth setup (interactive + CI/CD)
│   └── SKILLS.md               # UiPath Skills reference
└── .gitignore
```

## Quick Start

```bash
# Authenticate to UiPath Orchestrator
uip login

# Verify connection
uip orchestrator folders list

# Initialize a new solution
uip solution init --name my-automation

# Pack the solution
uip solution pack --path solutions/my-automation

# Publish to Orchestrator
uip solution publish --path solutions/my-automation --folder <FOLDER>
```

## Environments

| Environment | Purpose | Orchestrator Folder |
|-------------|---------|---------------------|
| DEV | Development & testing | `DEV` |
| TEST | Pre-production validation | `TEST` |
| PROD | Production | `PROD` |

## Authentication

### Interactive (developer machine)
```bash
uip login
```

### CI/CD (external app credentials)
```bash
uip login --client-id <ID> --client-secret <SECRET> --tenant <TENANT>
```

See [docs/AUTHENTICATION.md](docs/AUTHENTICATION.md) for detailed setup.

## UiPath Skills

27 skills installed covering: RPA, Agents, Maestro, Process Mining, Governance, Test, Insights, and more.

See [docs/SKILLS.md](docs/SKILLS.md) for the full reference.

## License

Private — Laurent Cadieux