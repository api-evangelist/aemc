# Australian Energy Market Commission

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

The Australian Energy Market Commission (AEMC) is the independent statutory rule maker for Australia's energy markets, established in 2005 and based in Sydney. It makes and amends the National Electricity Rules, National Gas Rules and National Energy Retail Rules, conducts market reviews, and advises the Energy and Climate Change Ministerial Council. It sits upstream of every other body in the Australian energy value chain — it writes the obligations that AEMO operates, that the AER enforces, and that retailers and networks must meet — but it operates no market systems and holds no consumer data itself. AEMC publishes no developer portal, no documented API, no OpenAPI and no open data product, and the corporate Drupal site at www.aemc.gov.au returns 404 for /api, /openapi.json, /swagger.json, /api-docs, /jsonapi and /graphql. It does, however, run one real machine-readable surface that it does not advertise — the Energy Rules application at energy-rules.aemc.gov.au is backed by an undocumented, entirely anonymous JSON API at /api/v1 that serves the full versioned text of all three rule books — 304 versions of the National Electricity Rules, 115 of the National Gas Rules and 65 of the National Energy Retail Rules — with a table of contents, per-clause content, full-text search, a complete defined-terms glossary and links to every published PDF and DOCX. That API is captured here as a derived OpenAPI built from AEMC's own production JavaScript bundle plus live probes. The other finding that matters is regulatory rather than technical — on 18 December 2025 the AEMC made a final rule giving all consumers and their AEMO-accredited representatives a right to real-time data from smart meters, with AEMO required to publish the technical procedures by 30 November 2026 and the meter obligation commencing 30 November 2028 — a mandate designated but not live, and separate from the Consumer Data Right, which is administered by Treasury, the ACCC and the Data Standards Body, with retailers as primary and AEMO as secondary data holder. AEMC is not a CDR data holder.

**Areas:** Energy · Australia · Energy Markets · Electricity · Gas · Utilities · Regulations · Smart Metering · Consumer Data Right · Government · Legal · Rules

## Australian Energy Market Commission on APIs.io

Everything profiled for Australian Energy Market Commission is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/aemc/](https://apis.io/providers/aemc/)** — or go straight to one of the APIs or properties below.

### APIs (5)

- [Australian Energy Market Commission Glossary API](https://apis.io/apis/aemc/aemc-glossary-api/) — Defined terms for a rule version.
- [Australian Energy Market Commission Rule Content API](https://apis.io/apis/aemc/aemc-rule-content-api/) — The structural tree of a rule version — chapters, parts, divisions, rules and clauses.
- [Australian Energy Market Commission Rule Versions API](https://apis.io/apis/aemc/aemc-rule-versions-api/) — Versions of the National Electricity, Gas and Energy Retail Rules, with their published PDF and DOCX artefacts.
- [Australian Energy Market Commission Search API](https://apis.io/apis/aemc/aemc-search-api/) — Full-text search within a single rule version.
- [Australian Energy Market Commission Settings API](https://apis.io/apis/aemc/aemc-settings-api/) — Application settings exposed to the client.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [aemc-energy-rules](https://apis.io/servers/aemc/aemc-energy-rules/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Aemc Agentic Access](https://apis.io/agentic-access/aemc/aemc-agentic-access/)

#### Examples (7)

Example requests and responses.

- [Aemc Energy Rules Getglossarymenu](https://apis.io/examples/aemc/aemc-energy-rules-getGlossaryMenu/)
- [Aemc Energy Rules Getglossaryterm](https://apis.io/examples/aemc/aemc-energy-rules-getGlossaryTerm/)
- [Aemc Energy Rules Getrulecontent](https://apis.io/examples/aemc/aemc-energy-rules-getRuleContent/)
- [Aemc Energy Rules Getruletableofcontents](https://apis.io/examples/aemc/aemc-energy-rules-getRuleTableOfContents/)
- [Aemc Energy Rules Listglossarytermsbyletter A](https://apis.io/examples/aemc/aemc-energy-rules-listGlossaryTermsByLetter-a/)
- [Aemc Energy Rules Listruleversions Ner](https://apis.io/examples/aemc/aemc-energy-rules-listRuleVersions-ner/)
- [Aemc Energy Rules Searchruleversion](https://apis.io/examples/aemc/aemc-energy-rules-searchRuleVersion/)

#### Collections (1)

Postman and Open Collection request collections.

- [AEMC Energy Rules API](https://apis.io/collections/aemc/open-aemc-energy-rules-openapi-derived/)

#### Overlays (1)

OpenAPI overlays, including conversational phrasing for each operation.

- [Aemc Energy Rules Overlay](https://apis.io/overlays/aemc/aemc-energy-rules-overlay/)

#### Security (2)

Authentication, trust centre, and vulnerability disclosure.

- [Aemc Authentication](https://apis.io/security/aemc/aemc-authentication/)
- [Aemc Domain Security](https://apis.io/security/aemc/aemc-domain-security/)

#### Rate limits (1)

Published request limits.

- [Aemc Rate Limits](https://apis.io/rate-limits/aemc/aemc-rate-limits/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://www.aemc.gov.au/)
- [Documentation](https://www.aemc.gov.au/regulation/energy-rules)
- [Support](https://www.aemc.gov.au/contact-us)
- [Blog](https://www.aemc.gov.au/news-centre/media-releases)
- [Terms of service](https://www.aemc.gov.au/terms-use)
- [Privacy policy](https://www.aemc.gov.au/terms-use/privacy)

## API Evangelist rating

**Kin Score 28.1** — thin · rubric 0.24.0 · scored 2026-10-17

| Facet | Score |
|---|---|
| Discoverability | 73.2 |
| Contract quality | 15.7 |
| Contract governance | 4.5 |
| Operational transparency | 15.8 |
| Developer ergonomics | 39.9 |
| Access clarity | 21.1 |

**Agent readiness 27.7** — agent-aware

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | na |
| MCP Server | — |
| Auth Clarity | bearer (partial credit) |
| Idempotency | na |
| Error Semantics | derived (partial credit) |
| OpenAPI Examples | partial |
| Rate Limit Signal | documented (partial credit) |
| Event Surface Described | — |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | na |
| Delegated Identity | — |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |

**Regulatory alignment 27.0** — Energy & Utilities

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/aemc/](https://apis.io/providers/aemc/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Australian Energy Market Commission: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/aemc/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
