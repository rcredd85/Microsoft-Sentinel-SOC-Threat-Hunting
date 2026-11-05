# Microsoft Sentinel | Inbound Authentication Origins & SOC Threat Hunting

**Cyber Range portfolio project** | Microsoft Sentinel · Microsoft Defender for Endpoint · Azure Log Analytics · KQL

## Project overview

This hands-on cybersecurity project demonstrates threat hunting and security monitoring using Microsoft Sentinel, Microsoft Defender for Endpoint, Azure Log Analytics, and Kusto Query Language (KQL).

The investigation focuses on analyzing inbound Windows authentication activity, identifying suspicious remote access patterns, evaluating authentication failures and successes, and visualizing the geographic origins of source IP addresses.

Using Microsoft Sentinel workbooks and endpoint security telemetry, I developed an investigative workflow to support the identification of potential brute-force attacks, unauthorized access attempts, and other suspicious authentication behavior.

**Project Objectives:**
- Analyze inbound authentication events using KQL.
- Investigate suspicious login failures and successful authentications.
- Visualize source IP geolocation using Microsoft Sentinel workbooks.
- Correlate authentication activity with endpoint telemetry.
- Identify potential indicators of compromise.
- Document findings and investigative limitations.

**Skills Demonstrated:** Threat Hunting | Microsoft Sentinel | Microsoft Defender XDR | KQL | SIEM Monitoring | Log Analysis | Incident Investigation | Security Visualization

> **Portfolio evidence:** The screenshot below comes from the actual workbook. IP addresses and account names were redacted for public sharing. Counts shown are observed dashboard values, not proof of malicious activity. This is a static screenshot, not a publicly accessible live workbook.

## Inbound authentication origins map

![Redacted Microsoft Sentinel inbound authentication map and source-IP breakdown](screenshots/inbound-authentication-origins-redacted.png)

The map plots geographically enriched authentication origins; the workbook labels bubble size as **total attempts**. The table provides **attempts, successes, failures, device counts, and accounts** by source IP.

### Investigation observations

- One displayed source has **317 attempts: 18 successes, 299 failures, across 28 devices**. This merits closer review for password spraying or other distributed targeting patterns, but the screenshot does not establish intent.
- Another displayed source has **610 attempts: 301 successes and 309 failures across 2 devices**. Mixed outcomes justify checking account identities, timing, and logon types.
- Other rows show sources with only successful logons. A success count alone is not evidence of compromise.
- IP geolocation is approximate; it does not establish the physical location of an attacker.

## Analyst workflow

1. Review time window, data freshness, and workbook filters.
2. Identify sources with unusual failure ratios, large device reach, or successful logons following failures.
3. Pivot to `DeviceLogonEvents` for affected devices, accounts, logon types, and timestamps.
4. Correlate with `DeviceProcessEvents`, `DeviceNetworkEvents`, and other available MDE telemetry.
5. Document evidence, alternative explanations, and recommended next steps. Do not claim compromise without corroborating evidence.

## Included KQL files

- [`queries/sentinel-inbound-authentication.kql`](queries/sentinel-inbound-authentication.kql) — starter authentication investigation query
- [`queries/mde-powershell-hunting.kql`](queries/mde-powershell-hunting.kql) — starter PowerShell investigation query
- [`queries/check-tables.kql`](queries/check-tables.kql) — workspace table validation

**Note:** The included queries are educational starting points and have not been verified against the workbook's exact schema or settings. The original workbook's KQL was not accessible from the provided private link.

## Tools and skills

Microsoft Sentinel, Microsoft Defender for Endpoint, Azure Log Analytics, Kusto Query Language, authentication analysis, geographic visualization, endpoint threat hunting, and incident investigation.

## Access and data handling

The source workbook is in an organization-controlled Microsoft security tenant. Recruiters may not have access to the live workbook. This repository provides a public, static view of the work. Before publishing, review the screenshot and queries for any remaining confidential details, and follow your organization's data-sharing policy.
