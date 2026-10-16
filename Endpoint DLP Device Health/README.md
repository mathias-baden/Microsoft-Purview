# Endpoint DLP Device Health

Advanced Hunting queries that find every device where Endpoint DLP isn't actually enforcing your policies, using the `DlpInfo` column in the `DeviceInfo` table.

📖 **Full walkthrough:** [Access Endpoint DLP Device Data with Advanced Hunting](https://mathiasbaden.com/posts/endpoint-dlp-device-data-advanced-hunting.html)

## Queries

| File | What it does |
|---|---|
| [01-explore-dlpinfo.kql](01-explore-dlpinfo.kql) | Look at the raw `DlpInfo` JSON |
| [02-overview.kql](02-overview.kql) | Count healthy vs. problem devices |
| [03-devices-to-fix.kql](03-devices-to-fix.kql) | One row per device, with what's wrong and who uses it |
| [04-stale-policy.kql](04-stale-policy.kql) | Devices behind on the latest policy change |
| [05-detection-rule.kql](05-detection-rule.kql) | Custom detection rule (run every 24h, entity: Device) |

## Requirements

- Devices onboarded to Endpoint DLP, with at least one DLP policy targeting devices
- Access to Advanced Hunting in the Microsoft Defender portal (e.g. Security Reader)

## Author

Mathias Baden Frederiksen · [mathiasbaden.com](https://mathiasbaden.com)
