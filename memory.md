# Coding Agent Memory — UiPathCLI_RACE_HERMES

> **Purpose:** Persist the agent's thought process, context, and decisions across session compressions. Read this first when resuming work on this project.

---

## Project Overview

**Repo:** https://github.com/Laurentcadieux/UiPathCLI_RACE_HERMES
**Local path:** /home/uipath-coder/UiPathCLI_RACE_HERMES
**Git remote:** git@github.com-uipath-race:Laurentcadieux/UiPathCLI_RACE_HERMES.git
**Branch:** main
**Git user:** Laurent Cadieux <laurent@cadieux.dev>

**Goal:** Store Coding Agent projects for UiPath Cloud deployment via the UiPath CLI (`uip`) and UiPath Skills.

## Environment

- **Machine:** /home/uipath-coder (Linux, no sudo)
- **Node.js:** v22.23.1
- **UiPath CLI:** `uip` v1.202.1 at `~/.npm-global/bin/uip` (PATH in .bashrc + .profile)
- **UiPath Skills:** 27 skills installed at `~/.agents/skills/`
- **Hermes skill:** `uipath-cli` created (software-development category)
- **Deploy key:** `~/.ssh/uipath-race-hermes` (ed25519, added as deploy key with write access)
- **SSH config:** `github.com-uipath-race` host alias configured

## Key Commands

```bash
# Always set PATH first (or source .bashrc)
export PATH="$HOME/.npm-global/bin:$PATH"

# Git operations
cd /home/uipath-coder/UiPathCLI_RACE_HERMES
git pull origin main
git add -A && git commit -m "..." && git push origin main

# UiPath CLI
uip --version
uip login                          # interactive auth (not done yet)
uip orchestrator folders list      # verify connection
uip solution pack --path Solution  # pack solution
uip solution publish --path Solution --folder <FOLDER>
```

## Current State

### Solution in repo: Maestro Case
- **Solution ID:** bed6e0a3-2878-4294-a5f8-79556618d332
- **Project ID:** 310f8375-a5a7-4449-b1b1-9bdc76d04587
- **Type:** CaseManagement (Maestro)
- **Flow:** Trigger 1 → Stage 1 (required, exits when tasks complete) → Case completion rule 1
- **Status:** Scaffold/template only — no real automation logic yet
- **Files:**
  - `Solution/Solution.uipx` — manifest
  - `Solution/Maestro Case/project.uiproj` — project config
  - `Solution/Maestro Case/caseplan.case` — case plan definition
  - `Solution/Maestro Case/caseplan.case.bpmn` — BPMN process (1270 lines)
  - `Solution/Maestro Case/entry-points.json` — 1 entry point ("Trigger 1")
  - `Solution/Maestro Case/bindings_v2.json` — empty (no resource bindings)
  - `Solution/resources/solution_folder/package/Maestro_Case.json` — package def
  - `Solution/resources/solution_folder/process/caseManagement/Maestro_Case.json` — process config

### Not yet done
- **Authentication:** `uip login` not executed — no UiPath Orchestrator credentials provided yet
- **Deployment:** Solution not packed or published
- **Real automation:** Maestro Case is a starter template, no real workflow logic

## Project Structure

```
UiPathCLI_RACE_HERMES/
├── RaceTime.md                  # Timeline log (timestamps + steps)
├── memory.md                    # This file (agent context)
├── README.md                    # Project overview
├── .gitignore                   # Secrets, build artifacts
├── Solution/                    # UiPath solution (Maestro Case)
├── solutions/                   # Placeholder for future solutions
├── agents/                      # Placeholder for UiPath agents
├── deploy/
│   ├── environments/            # dev.json, test.json, prod.json
│   └── pipelines/              # CI/CD definitions (empty)
├── orchestrator/
│   ├── folders.json            # DEV, TEST, PROD folders
│   ├── assets.json             # Empty
│   └── queues.json             # Empty
├── skills/                     # Custom skill extensions (empty)
└── docs/
    ├── AUTHENTICATION.md       # Auth setup guide
    ├── DEPLOYMENT.md           # Deploy guide
    └── SKILLS.md               # 27 UiPath skills reference
```

## Tracking Files

| File | Purpose |
|------|---------|
| `RaceTime.md` | Timeline of all steps with UTC timestamps |
| `memory.md` | This file — agent thought process and context |

## Rules

1. **Always update RaceTime.md** after each step with UTC timestamp
2. **Always update memory.md** when state changes (new files, auth done, deployment, etc.)
3. **Never commit secrets** — .env, credentials, tokens are gitignored
4. **Use `uip` CLI** for all UiPath operations (not the web UI)
5. **Git config** is set per-repo: user.email = "laurent@cadieux.dev", user.name = "Laurent Cadieux"

## Next Steps (waiting on user)

- User will ask to create a UiPath project — waiting for instructions
- Need UiPath Orchestrator credentials to run `uip login`
- Need to know what automation to build in the Maestro Case
