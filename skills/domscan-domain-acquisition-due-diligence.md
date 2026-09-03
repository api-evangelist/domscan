---
name: domscan-domain-acquisition-due-diligence
description: Evaluate a domain before buying or launching on it — availability, registration history, valuation, lifecycle, and a compound due-diligence read.
api: DomScan API
operations: [checkDomainAvailability, getDomainProfile, getWhois, getWhoisV2, getDomainValue, getDomainLifecycle, getDomainScore, recipeDueDiligence]
generated: '2026-09-03'
method: generated
source: openapi/domscan-openapi.json + llms/domscan-llms.txt
---

# Domain acquisition due diligence

Authenticate every call with `x-api-key: dsk_...` (or `Authorization: Bearer`). Watch `X-Credits-Charged` / `X-Credits-Remaining` on each response; a 402 means the credit balance is exhausted.

1. **Is it even available?** `checkDomainAvailability` (`GET /v1/status?name=<label>&tlds=com,io,...`). The `name` parameter is the label WITHOUT the TLD. Available across 1,100+ TLDs via RDAP.
2. **Who holds it now?** `getWhois` (`GET /v1/whois`) for the classic record, or `getWhoisV2` (`GET /v2/whois`) to merge normalized RDAP with WHOIS enrichment. `getDomainProfile` (`GET /v1/profile`) returns the normalized registration profile.
3. **What is it worth?** `getDomainValue` (`GET /v1/value`) for an algorithmic market valuation; `getDomainScore` (`GET /v1/score`) for brand-quality scoring.
4. **Where is it in its life?** `getDomainLifecycle` (`GET /v1/lifecycle`) — registration dates and lifecycle phase (grace, redemption, pendingDelete matter for drop-catching).
5. **One-shot compound read:** `recipeDueDiligence` (`GET /v1/recipes/due-diligence`) runs the complete acquisition analysis in one call (recipe pricing: 6-25 credits).

Errors return `error.{code,message,retryable,request_id}`; retry only when `retryable` is true and honor `Retry-After` on 429.
