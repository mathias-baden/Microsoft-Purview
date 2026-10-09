# Defender for Cloud Apps — Policy Backup

A PowerShell script that exports every policy from **Microsoft Defender for Cloud Apps (MDCA)** via the API and writes each one as a JSON file to an Azure Storage container. Run it on a schedule and you have a versioned, restorable backup of your MDCA policy configuration — instead of hoping nobody edits a policy you can't rebuild.

- **Source:** MDCA REST API (`/cas/api/v1/policies/`), paged
- **Destination:** an Azure Storage blob container (one `.json` per policy)
- **Auth:** an Entra ID service principal (app ID + client secret) for Azure, plus an MDCA API token

## Why

MDCA policy config lives in the portal with no native "export all / restore" button. If a policy is changed or deleted — by you, a colleague, or a tenant migration — there's no clean way back unless you captured it first. This script gives you that capture: a flat set of JSON files you can diff, archive, or use to recreate a policy by hand.

## Requirements

- PowerShell with the **Az** module (`Connect-AzAccount`, `Az.Storage`)
- An **Entra ID service principal** with access to the target storage account
- An **MDCA API token** (Defender for Cloud Apps → Settings → Security extensions → API tokens)
- An existing **Azure Storage account + container** to write to

## Configuration

The script ships with placeholder values — replace all of them before running. **Do not commit real secrets**; pass them in from a secret store, Key Vault, or pipeline variables rather than hard-coding them:

| Placeholder | What to set |
|---|---|
| `YOUR APP ID` | Service principal (app) ID |
| `YOUR APP CLIENT SECRET` | Service principal client secret |
| `YOUR TENANT ID` | Entra ID tenant ID |
| `YOUR SUBSCRIPTION ID` | Azure subscription ID |
| `YOUR STORAGE ACCOUNT` / `YOUR RESSOURCE GROUP` | Target storage account and its resource group |
| `YOUR CONTAINER` | Blob container to write the JSON files to |
| `YOUR MDCA API TOKEN` | Defender for Cloud Apps API token |
| `https://yourtenant.portal.cloudappsecurity.com` | Your MDCA portal URL |

## Usage

```powershell
.\mdca-backup-demo.ps1
```

The script connects to Azure as the service principal, pages through every MDCA policy, writes each to a temp JSON file, and uploads it to `Policies\<policy name>.json` in your container.

> **Note:** this is a demo/reference script — review it and wire in your own secret handling before using it in production. Treat it as a starting point, not a turnkey tool.

## License

MIT — adapt freely.
