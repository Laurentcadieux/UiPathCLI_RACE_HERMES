# Authentication Guide

## Interactive Login (Developer Machine)

```bash
uip login
```

Opens browser for OAuth login to UiPath Platform.

## External App (CI/CD)

```bash
uip login \
  --client-id <CLIENT_ID> \
  --client-secret <CLIENT_SECRET> \
  --tenant <TENANT_NAME>
```

### Creating an External App

1. Go to UiPath Automation Cloud → Admin → External Apps
2. Click "Add Application"
3. Name: `uipath-race-hermes`
4. Type: Confidential Application
5. Grant scopes: `Orchestrator`, `Solution Manager`
6. Copy Client ID and Client Secret

## Check Auth Status

```bash
uip auth status
```

## Logout

```bash
uip logout
```
