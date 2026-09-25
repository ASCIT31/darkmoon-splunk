# Splunkbase listing — paste-ready

Content to paste into the Splunkbase submission form (app id **9875**, name **Darkmoon Pentest**).
This is the *listing* copy — it is **not** shipped inside the app tarball (Splunkbase metadata is entered on the web form).

**Package to upload:** `dist/darkmoon-1.0.0.tar.gz` · **Content type:** Splunk App · **Hosting:** Splunkbase · **Access:** Public

---

## App name
Darkmoon Pentest

## Short description
Ingest Darkmoon AI-pentest results into Splunk over HEC and trigger a Darkmoon retest/campaign from a correlation search. CIM-aligned sourcetypes, SOC dashboards, and a hard-secured alert action. Safe metadata only — never evidence or secrets.

## Long description
Darkmoon Pentest brings your Darkmoon AI penetration-testing results into Splunk and closes the loop back to Darkmoon.

Ingestion: a producer (the bundled forwarder, or a Darkmoon Pro webhook) sends safe, JSON events to the HTTP Event Collector. The app parses them into CIM-aligned sourcetypes (darkmoon:campaign, darkmoon:finding, darkmoon:retest, darkmoon:pr) mapped to the Vulnerabilities data model. Events carry safe metadata only — campaign/finding ids, severity, status, target reference, MITRE ATT&CK, technology and timestamps. Evidence, secrets, credentials, tokens and request/response bodies are never ingested, with index-time redaction as a second line of defense.

Dashboards: six SOC views — Overview KPIs, Findings, MITRE ATT&CK & Technologies, Campaigns, Remediation & Retest, and Setup & Help — with drill-down.

Offensive-validation loop (Darkmoon Pro): the "Send to Darkmoon" alert action launches a retest or campaign from a Splunk correlation search, hard-secured with a target allowlist, safe-harbor default, token stored in storage/passwords, rate limiting, TLS verification and a dry-run default. Three example correlation searches ship disabled.

The alert action and setup call the Darkmoon Pro REST API and are Pro features; ingestion and dashboards work with any Darkmoon edition that can emit events.

## Category
Security, Fraud & Compliance (secondary: IT Operations)

## Compatible Splunk versions
Splunk Enterprise 9.0, 9.1, 9.2, 9.3, 9.4 and latest 10.x; Splunk Cloud compatible. Platform-independent (CIM 5.x; alert action uses Splunk's bundled Python 3).

---

## Screenshots (upload from `docs/screenshots/`)

| Order | File | Caption (paste-ready) |
|---|---|---|
| ★ 1 (featured) | `01-soc-overview.png` | SOC posture at a glance: active campaigns, critical/high, confirmed & exploited, remediation rate, retest verdicts, findings over time and top exploited assets. |
| 2 | `02-findings.png` | Every finding with severity/status/category/target/campaign filters, CVSS, CVE and MITRE — safe metadata only, no evidence. |
| 3 | `03-mitre-attack.png` | MITRE ATT&CK coverage, top techniques, affected technologies and a technique×severity heat map. |
| 4 | `04-campaigns.png` | Assessment campaigns with risk, findings, criticals and outcomes; drill down to per-campaign findings. |
| 5 | `05-remediation-retest.png` | Remediation pull-request states and retest verdicts (fixed / regressed / still_present / new) over time. |
| 6 | `08-alert-action.png` | The Send to Darkmoon alert action wired into a correlation search — the offensive-validation loop, hard-secured. |
| 7 | `06-setup.png` | Set up: Darkmoon connection; the API token is stored encrypted in storage/passwords, never in a .conf. |
| 8 (optional) | `07-setup-help.png` | Reference / help. |

---

## Human-only upload step
Sign in to **splunkbase.splunk.com** with the account that owns app id 9875, upload `dist/darkmoon-1.0.0.tar.gz`, paste the copy above, attach the screenshots (feature `01-soc-overview.png`), and submit. Splunkbase cloud vetting mirrors the AppInspect precert, which is already clean (`docs/appinspect-precert.json`: 0 errors, 0 failures).
