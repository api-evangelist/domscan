---
name: domscan-find-available-domain
description: Find and shortlist an available, well-priced domain for a new product or brand — suggestions, availability, brand scoring, and registrar price comparison.
api: DomScan API
operations: [suggestDomains, checkDomainAvailability, bulkCheckDomains, getDomainScore, compareBrandNames, getTlds, getPrices, comparePrices, recipeBrandLaunch]
generated: '2026-09-03'
method: generated
source: openapi/domscan-openapi.json + llms/domscan-llms.txt
---

# Find an available domain

1. **Brainstorm:** `suggestDomains` (`GET /v1/suggest`) generates AI-powered names from keywords (2 credits, 5 with availability checked).
2. **Check availability:** `checkDomainAvailability` (`GET /v1/status?name=<label>&tlds=...`) for one label across TLDs; `bulkCheckDomains` (`POST /v1/status/bulk`) for up to 50 complete domain names.
3. **Rank the candidates:** `getDomainScore` (`GET /v1/score`) scores brand quality; `compareBrandNames` (`POST /v1/score/compare`) ranks multiple names side by side.
4. **Price it:** `getTlds` (`GET /v1/tlds`) for TLD options, `getPrices` (`GET /v1/prices`) for registrar pricing, `comparePrices` (`GET /v1/prices/compare`) for standard rows plus official exact-domain quotes.
5. **Pre-launch checklist:** `recipeBrandLaunch` (`GET /v1/recipes/brand-launch`) bundles readiness checks before you commit.

The `name` parameter for availability is the bare label (e.g. `acme`, not `acme.com`); bulk endpoints want complete domain names.
