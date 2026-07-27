# Australian Energy Market Commission (aemc)

The Australian Energy Market Commission (AEMC) is the independent statutory rule maker for Australia's energy markets, established in 2005 and based in Sydney. It makes and amends the National Electricity Rules, National Gas Rules and National Energy Retail Rules, conducts market reviews, and advises the Energy and Climate Change Ministerial Council. It sits upstream of every other body in the Australian energy value chain — it writes the obligations that AEMO operates, that the AER enforces, and that retailers and networks must meet — but it operates no market systems and holds no consumer data itself. AEMC publishes no developer portal and no documented API — but it does run one real machine-readable surface it never advertised: an undocumented, entirely anonymous JSON API behind its Energy Rules application, serving the full versioned text of all three rule books.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/aemc/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/aemc/refs/heads/main/apis.yml)

## Tags

- Energy
- Australia
- Energy Markets
- Electricity
- Gas
- Utilities
- Regulation
- Smart Metering
- Consumer Data Right
- Government

## Timestamps

- **Created:** 2026-07-27
- **Modified:** 2026-07-27

## APIs

### AEMC Energy Rules API — undocumented, anonymous, real

`https://energy-rules.aemc.gov.au/api/v1` — the JSON API behind AEMC's [Energy Rules application](https://energy-rules.aemc.gov.au/). It serves the consolidated, versioned text of all three rule books, with per-version PDF and DOCX artefacts, the full chapter/part/division/rule/clause tree, per-node rule text, full-text search within a version, and the complete defined-terms glossary.

| Rule book | Type code | Versions | Current |
|---|---|---|---|
| National Electricity Rules | `ner` | 304 | v251 (id 803, from 2026-07-23) |
| National Gas Rules | `ngr` | 115 | v92 (id 800, from 2026-07-16) |
| National Energy Retail Rules | `nerr` | 65 | v51 (id 802, from 2026-07-01) |

Verified live on 2026-07-27: **entirely anonymous** — no API key, OAuth, cookie or CSRF token. Responses carry `x-ratelimit-limit: 1000`, served through AWS API Gateway in front of a Laravel app (`data`/`links`/`meta` envelope, `page`/`perPage` pagination). Every path is keyed by the rule version **id**, not the version number — passing the number returns HTTP 404.

AEMC publishes **no** OpenAPI, documentation, terms of use, SLA, support channel, versioning or deprecation policy for it. [`openapi/aemc-energy-rules-openapi-derived.yml`](openapi/aemc-energy-rules-openapi-derived.yml) is therefore a **derived** specification — every route taken from AEMC's own production JavaScript bundle and probed live, with the HTTP status recorded in `x-evidence` on each operation. Treat it as subject to change without notice.

### What is still absent

Probed on 2026-07-27: `developer.`, `developers.`, `api.`, `docs.`, `data.`, `rules.` and `energyrules.aemc.gov.au` do not resolve; on the corporate site `/developers`, `/api`, `/docs`, `/openapi.json`, `/swagger.json`, `/api-docs`, `/jsonapi`, `/graphql`, `/apis.json`, `/.well-known/apis.json` and `/.well-known/openid-configuration` all return 404, and `/.well-known/security.txt`, `/llms.txt` and `/ai.txt` are blocked at the edge (403). `portal.aemc.gov.au` resolves but does not answer on 443. The other machine-readable surface on the corporate domain is the Drupal site feed at [/rss.xml](https://www.aemc.gov.au/rss.xml) (HTTP 200), recorded as a common property rather than as an API.

## Artifacts

- [Derived OpenAPI 3.1 — 9 operations](openapi/aemc-energy-rules-openapi-derived.yml) · [overlay](overlays/aemc-energy-rules-overlay.yaml)
- [Captured example responses](examples/_index.yml) — real bodies from live anonymous calls
- [Authentication](authentication/aemc-authentication.yml) · [Conventions](conventions/aemc-conventions.yml) · [Errors](errors/aemc-problem-types.yml) · [Rate limits](rate-limits/aemc-rate-limits.yml)
- [Data model](data-model/aemc-data-model.yml) · [Lifecycle](lifecycle/aemc-lifecycle.yml) · [Rule version changelog](changelog/aemc-changelog.yml) · [Conformance](conformance/aemc-conformance.yml)
- [Agent skills](skills/_index.yml) — look up a rule, search and resolve defined terms, track versions over time
- [Candidate MCP tool list](mcp/aemc-mcp.yml) (AEMC publishes no MCP server) · [Agentic access contracts](agentic-access/aemc-agentic-access.yml)
- [llms.txt](llms/aemc-llms.txt) · [Well-known probes](well-known/aemc-well-known.yml) · [Domain security](security/aemc-domain-security.yml)

## Data

The [AEMC Data portal](https://www.aemc.gov.au/news-centre/data-portal) (HTTP 200) is seven HTML interactive chart projects — Residential Electricity Price Trends, Annual Market Performance Review and Retail Energy Competition Review — whose newest release is 2021. No CSV, XLSX, ZIP, API or data licence statement was found on the portal index or on the child pages probed. AEMC is not a publishing organisation on data.gov.au.

Open Australian energy market data lives with AEMO, the market operator AEMC writes rules for — not with AEMC.

## Mandate posture

- **Regime recorded:** smart-meter-infrastructure — the mandate AEMC *imposes*, not one it is subject to. AEMC is not a Consumer Data Right data holder.
- **Status:** designated-not-live.
- **Instrument:** final determination and final rules for *Real-time data for consumers*, published **18 December 2025**. All customers and their AEMO-accredited representatives may request real-time data from their smart meter; Metering Coordinators must facilitate access under AEMO's real-time data procedures; **AEMO must publish those procedures by 30 November 2026**; new smart meters installed from **30 November 2028** must wirelessly communicate real-time data free of charge.
- **Why not live:** the technical standards do not exist yet. There is no endpoint, no schema, and no register of accredited representatives to verify. A completed rule change is a mandate, not an implementation.
- **Consumer Data Right (energy)** is a separate instrument, designated by Treasury, regulated by the ACCC, standardised by the Data Standards Body, and live in the National Electricity Market since November 2022 with retailers as primary data holders and AEMO as secondary data holder and gateway. AEMC plays no part in operating it.

## Properties

- [Website](https://www.aemc.gov.au/)
- [About](https://www.aemc.gov.au/about-us)
- [Contact](https://www.aemc.gov.au/contact-us)
- [Documentation](https://www.aemc.gov.au/regulation/energy-rules)
- [Data Portal](https://www.aemc.gov.au/news-centre/data-portal)
- [Blog](https://www.aemc.gov.au/news-centre/media-releases)
- [RSS](https://www.aemc.gov.au/rss.xml)
- [Regulation](https://www.aemc.gov.au/regulation/energy-rules/national-electricity-rules)
- [Rule Changes](https://www.aemc.gov.au/our-work/changing-energy-rules/rule-changes)
- [Energy Rules application](https://energy-rules.aemc.gov.au/)
- [Terms of Use](https://www.aemc.gov.au/terms-use)
- [Privacy](https://www.aemc.gov.au/terms-use/privacy)

## Maintainers

- Kin Lane — kin@apievangelist.com
