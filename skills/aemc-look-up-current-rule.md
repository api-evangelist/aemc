---
name: Look up a rule in the current Australian energy rules
description: Resolve the current version of the National Electricity, Gas or Energy Retail Rules and read a specific chapter, rule or clause from it.
api: openapi/aemc-energy-rules-openapi-derived.yml
operations: [listRuleVersions, getRuleTableOfContents, getRuleContent]
generated: '2026-07-27'
method: generated
---

# Look up a rule in the current Australian energy rules

Use the AEMC Energy Rules API (`https://energy-rules.aemc.gov.au/api/v1`) to read the consolidated
text of a rule book. No authentication is required — every call below is anonymous.

Rule books: `ner` (National Electricity Rules), `ngr` (National Gas Rules), `nerr` (National Energy
Retail Rules). `nel` and the `-wa` variants return an empty list.

## Steps

1. **Resolve the current version.** Call `listRuleVersions` with the rule book:
   `GET /rules/ner/versions?perPage=1`. Take `data[0].id` — that is the **version id** (e.g. 803 for
   NER v251). Confirm `is_current` is `1`. Never use `data[0].version` (the version *number*) as a
   path parameter — every downstream endpoint returns HTTP 404 if you do.
2. **Get the structure.** Call `getRuleTableOfContents`: `GET /rules/{versionId}/toc`. The response
   is a recursive tree of nodes with `title`, `index` (the citation, e.g. `1.1.1`), `chapter`,
   `content_type` (`chapter`, `part`, `division`, `rule`, `clause`, `chapter_schedule`,
   `part_schedule`) and `links.self` of the form `content/<id>`. Use `listRuleChapters`
   (`GET /rules/{versionId}/chapters`) instead when you only need the top-level chapter list.
3. **Read the rule.** Take the node id from `links.self` and call `getRuleContent`:
   `GET /rules/{versionId}/content/{contentId}`. The response carries the node, its `parent`, its
   `children` and — for leaf nodes — `content` as an **HTML string**. Sanitise the HTML before
   passing it on. The `meta` block tells you whether the version is `approved`, `current` or
   `archived`.
4. **Cite properly.** Quote the rule using `index` + `title` plus the rule book name and version
   number from step 1 (e.g. "NER v251, clause 1.1.1 References to the Rules"). The rules change
   often — NER moved to v251 on 2026-07-23 — so a citation without a version is unsafe.

## Rules of engagement

- **Version id, not version number.** This is the one mistake that breaks every call.
- **Read-only.** The public surface is GET-only. There is no idempotency contract because there is
  nothing to mutate. Do not attempt the administrative approval route present in AEMC's client
  bundle.
- **Errors.** Failures return `{"message":"Not found"}` with HTTP 404 — not RFC 9457. An unknown
  rule book is *not* an error: it returns HTTP 200 with an empty `data` array, so check
  `meta.total`. An unmatched path returns the site's HTML shell with HTTP 200, so assert the
  response content type is `application/json`.
- **Rate limits.** Responses carry `x-ratelimit-limit: 1000` and `x-ratelimit-remaining`. No policy
  is published; back off on your own budget.
- **Send `Accept-Encoding: gzip`** (curl `--compressed`) — responses are gzip-encoded.
- **Undocumented API.** AEMC publishes no documentation, terms of use, SLA or support channel for
  this surface. It can change without notice. Do not present it as an AEMC-supported product.
- **Legal text is not legal advice.** Return the rule text and its citation; do not paraphrase a
  rule as an obligation.
