# Microsoft Sentinel | SOC Threat Hunting & Authentication Monitoring

Hands-on cybersecurity portfolio project documenting a Microsoft Sentinel workbook in a cyber-range SOC environment, with supporting Microsoft Defender for Endpoint (MDE) hunting workflows.

> **Evidence note:** The original workbook requires organizational authentication. Screenshots and actual results have not been independently verified or included. Query examples below are templates; they must be validated against the tables available in your environment.

## Project overview

This project focuses on investigating inbound authentication origins, suspicious remote access, and potentially malicious endpoint processes. The intended workflow is to query relevant logs, filter noisy events, enrich public source IPs with geographic context, and pivot to endpoint telemetry for investigation.

## Tools and skills

- Microsoft Sentinel / Azure Log Analytics
- Microsoft Defender for Endpoint (MDE) Advanced Hunting
- Kusto Query Language (KQL)
- Authentication analysis, source-IP enrichment, process investigation
- SOC documentation and incident triage

## Investigation workflow

1. Confirm which tables are present in the Sentinel workspace and inspect the available time range.
2. Find inbound authentication events, then examine successful and failed logons.
3. Identify external source IPs and enrich them with approximate geographic data.
4. Pivot to MDE process events for suspicious PowerShell or other execution.
5. Document findings, limitations, and any validated indicators.

## KQL examples

- [`queries/sentinel-inbound-authentication.kql`](queries/sentinel-inbound-authentication.kql) — Sentinel-compatible example for the `DeviceLogonEvents` table **only if it is ingested into Log Analytics**.
- [`queries/mde-powershell-hunting.kql`](queries/mde-powershell-hunting.kql) — Defender Advanced Hunting query for PowerShell process activity.
- [`queries/check-tables.kql`](queries/check-tables.kql) — Identify available Log Analytics tables before selecting a data source.

**Important:** MDE Advanced Hunting and Sentinel Logs are different query environments. `DeviceLogonEvents` may be available in Defender but absent from your Sentinel Log Analytics workspace. Do not interpret zero results as proof of no attack.

## Screenshots

Add sanitized screenshots from your own authenticated environment to the `screenshots/` folder:

| Screenshot | What to capture |
|---|---|
| `01-workbook-overview.png` | Workbook title and overview visualizations |
| `02-inbound-authentication.png` | Authentication origins visualization, including time filter |
| `03-kql-query-results.png` | Successful query and results with sensitive fields redacted |
| `04-mde-advanced-hunting.png` | Relevant MDE hunting query and results |

**Do not upload:** access tokens, account email addresses, subscription or tenant identifiers, internal IPs/hostnames, personal information, or unapproved organizational data. Obtain permission to publish cyber-range screenshots. Avoid treating generated artwork as evidence screenshots.

## Findings and limitations

This repository documents an investigative method. No specific compromise, attack source, geographic attribution, incident count, or containment action is claimed without validated log evidence. Add observed findings after reviewing the actual query results.

## LinkedIn Featured description

**Title:** Microsoft Sentinel & Defender for Endpoint | SOC Threat Hunting Project

**Description:** Hands-on cybersecurity portfolio project demonstrating KQL investigations, authentication monitoring, endpoint threat hunting, and SOC investigation workflows using Microsoft Sentinel, Azure Log Analytics, and Microsoft Defender for Endpoint.

## Source workbook

The workbook is hosted in a private Microsoft security tenant. The original link may be accessible only to authorized users. For public portfolio sharing, link to this repository instead.
