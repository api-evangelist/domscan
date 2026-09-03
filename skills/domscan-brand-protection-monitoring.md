---
name: domscan-brand-protection-monitoring
description: Detect typosquatting threats against a brand, generate a protection report, and stand up continuous monitoring with email/webhook alerts.
api: DomScan API
operations: [analyzeTyposquattingThreats, generateTyposquattingReport, getProtectionScore, createBrandMonitor, triggerBrandScan, getBrandMonitorStatus, updateBrandMonitorAlerts, deleteBrandMonitor, recipeThreatAssessment]
generated: '2026-09-03'
method: generated
source: openapi/domscan-openapi.json + llms/domscan-llms.txt
---

# Brand protection and typosquat monitoring

1. **Scan for live threats:** `analyzeTyposquattingThreats` (`GET /v1/typos/threats`) runs a live typosquatting scan; `getProtectionScore` (`GET /v1/typos/score`) summarizes exposure.
2. **Report for stakeholders:** `generateTyposquattingReport` (`GET /v1/typos/report`) produces the full brand-protection report; `recipeThreatAssessment` (`GET /v1/recipes/threat-assessment`) is the compound alternative.
3. **Monitor continuously:** `createBrandMonitor` (`POST /v1/brand-monitor`) with optional `alert_email` and `alert_webhook` destinations. Alerts fire on new typosquatting registrations.
4. **Operate the monitor:** `triggerBrandScan` (`POST /v1/brand-monitor/scan`) forces a scan; `getBrandMonitorStatus` (`GET /v1/brand-monitor/status`) reads detailed status; `updateBrandMonitorAlerts` (`PUT /v1/brand-monitor/alerts`) changes destinations.
5. **Reversal:** `deleteBrandMonitor` (`DELETE /v1/brand-monitor`) removes the monitor at any time.

Rate limits: free tier sustains 120 req/min (burst 60); honor `Retry-After` on 429.
