# Microsoft Purview

Scripts, KQL and tools for **Microsoft Purview** — Information Protection, DLP and Insider Risk — built from real-world deployments. Each one solves a specific problem I hit on a customer engagement and couldn't find a clean answer to.

🌐 Written up in more depth at [mathiasbaden.com](https://mathiasbaden.com)

## 🧰 Tools

### ⭐ [MIP Scanner Report](./Microsoft%20Purview%20Information%20Protection%20Scanner/)
Turns the Microsoft Purview Information Protection Scanner's raw `DetailedReport` CSV into a single, self-contained **per-user HTML report** — share-by-share SIT findings, a stale-data (GDPR) flag, and a click-to-browse file list. Read-only, 100% client-side.
`PowerShell` · `Information Protection Scanner` · `reporting`

### [Sensitivity Label Downgrade Detection](./Sensitivity%20Label%20Downgrade/)
A near-real-time detection that alerts when a file's sensitivity label is downgraded *out* of a sensitive tier — e.g. HR / Highly Confidential → Public. A KQL query plus a Microsoft 365 Defender custom detection rule. Includes the NRT `summarize` gotcha that makes rules silently stop alerting.
`KQL` · `sensitivity labels` · `custom detection rule`

## 🔗 Related

### [Defender for Cloud Apps — Policy Backup](./Defender%20for%20Cloud%20Apps%20-%20Policy%20Backup/)
A PowerShell script that backs up every Defender for Cloud Apps (MDCA) policy as JSON to Azure Storage. Lives here because MDCA's data-security capabilities are converging into Purview.
`PowerShell` · `MDCA API` · `Azure Storage`

## A note on the examples

Any label IDs, tenant IDs, secrets, or account names in these files are **placeholders**. Replace them with your own before running anything — each tool's readme says where.

## License

MIT — Copyright (c) 2026 Mathias Baden Frederiksen — [mathiasbaden.com](https://mathiasbaden.com). Adapt freely.

---

⭐ If something here helps, a star helps others find it too.
