# Microsoft Security Scripts

Practical scripts and KQL for **Microsoft Purview**, **Microsoft Defender** and **Defender for Cloud Apps** — pulled straight from real-world deployments. Each one solves a specific problem I hit on a customer engagement and couldn't find a clean answer to.

🌐 Written up in more depth at [mathiasbaden.com](https://mathiasbaden.com)

## 🧰 Tools

### ⭐ [MIP Scanner Report](./Microsoft%20Purview/Microsoft%20Information%20Protection%20Scanner/)
Turns the Microsoft Purview Information Protection Scanner's raw `DetailedReport` CSV into a single, self-contained **per-user HTML report** — share-by-share SIT findings, a stale-data (GDPR) flag, and a click-to-browse file list. Read-only, 100% client-side.
`PowerShell` · `Information Protection Scanner` · `reporting`

### [Sensitivity Label Downgrade Detection](./Advanced%20Hunting/Sensitivity%20Label%20Downgrade/)
A Microsoft 365 Defender **Advanced Hunting** KQL query (plus a custom detection rule) that alerts in near real-time when a file's sensitivity label is downgraded *out* of a sensitive tier — e.g. HR / Highly Confidential → Public. Includes the NRT `summarize` gotcha that makes rules silently stop alerting.
`KQL` · `CloudAppEvents` · `custom detection rule`

### [Defender for Cloud Apps — Policy Backup](./Microsoft%20Defender%20for%20Cloud%20Apps/Backup/)
A PowerShell script that pulls every MDCA policy via the API and backs each one up as JSON to an Azure Storage container — a versioned, restorable copy of your policy config.
`PowerShell` · `MDCA API` · `Azure Storage`

## A note on the examples

Any label IDs, tenant IDs, secrets, or account names in these files are **placeholders**. Replace them with your own before running anything — each tool's readme says where.

## License

MIT — Copyright (c) 2026 Mathias Baden Frederiksen — [mathiasbaden.com](https://mathiasbaden.com). Adapt freely.

---

⭐ If something here helps, a star helps others find it too.
