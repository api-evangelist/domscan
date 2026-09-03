---
name: domscan-email-deliverability-audit
description: Audit a domain's email authentication posture — SPF, DKIM, DMARC, transport policy, and Gmail/Outlook sender readiness.
api: DomScan API
operations: [getEmailAuth, checkDkim, discoverDkim, validateSpf, validateDmarc, getEmailCompliance, recipeEmailDeliverability]
generated: '2026-09-03'
method: generated
source: openapi/domscan-openapi.json + llms/domscan-llms.txt
---

# Email deliverability audit

1. **Full posture read:** `getEmailAuth` (`GET /v1/email-auth`) checks email auth records and mail transport policies in one call.
2. **Drill into DKIM:** `discoverDkim` (`GET /v1/tools/dkim/discover`) finds selectors; `checkDkim` (`GET /v1/tools/dkim/check`) validates a specific selector.
3. **Validate SPF and DMARC:** `validateSpf` (`POST /v1/tools/spf/validate`) and `validateDmarc` (`POST /v1/tools/dmarc/validate`). Builders (`buildSpf`, `buildDmarc`) and the SPF flattener (`flattenSpf`) fix what validation flags — tool builders cost 1 credit.
4. **Mailbox-provider readiness:** `getEmailCompliance` (`GET /v1/email/compliance`) checks Gmail and Outlook sender requirements for the domain.
5. **Compound audit:** `recipeEmailDeliverability` (`GET /v1/recipes/email-deliverability`) runs the complete deliverability analysis in one call.

All lookups are read-only and safe to repeat; per-call credit costs surface in `X-Credits-Charged`.
