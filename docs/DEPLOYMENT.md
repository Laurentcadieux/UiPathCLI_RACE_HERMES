# Deployment Guide

## Prerequisites

- UiPath CLI (`uip`) v1.197+
- Authenticated to UiPath Orchestrator
- Solution project packed (`.nupkg`)

## Deploy a Solution

```bash
# 1. Pack the solution
uip solution pack --path solutions/my-solution

# 2. Publish to DEV
uip solution publish --path solutions/my-solution --folder DEV

# 3. Verify deployment
uip orchestrator processes list --folder DEV
```

## Deploy an Agent

```bash
# 1. Pack the agent
uip agent pack --path agents/my-agent

# 2. Publish
uip agent publish --path agents/my-agent --folder DEV
```

## Promote DEV → TEST → PROD

```bash
# Promote to TEST
uip solution publish --path solutions/my-solution --folder TEST

# Promote to PROD
uip solution publish --path solutions/my-solution --folder PROD
```

## Environment Configuration

See `deploy/environments/` for per-environment settings.
