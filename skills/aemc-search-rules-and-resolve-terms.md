---
name: Search the energy rules and resolve defined terms
description: Full-text search one version of the Australian energy rules and expand the capitalised defined terms in the result.
api: openapi/aemc-energy-rules-openapi-derived.yml
operations: [listRuleVersions, searchRuleVersion, getRuleContent, getGlossaryMenu, listGlossaryTermsByLetter, getGlossaryTerm]
generated: '2026-07-27'
method: generated
---

# Search the energy rules and resolve defined terms

The energy rules are written in defined terms — a clause is unreadable until its capitalised terms
are expanded. This skill searches a rule version and then resolves the terms the result depends on.

## Steps

1. **Resolve the version id.** `listRuleVersions` (`GET /rules/{ruleType}/versions?perPage=1`) →
   `data[0].id`. Search is always scoped to one version; there is no cross-version search.
2. **Search.** `searchRuleVersion`: `GET /rules/{versionId}/search?query=smart+meter&page=1&perPage=30`.
   Add `chapter=<n>` to restrict to a chapter; omit it for all chapters. Each hit returns
   `search_content` (the matched snippet), `index`, `title`, `chapter`, `content_type`, the `parent`
   node, and `links.self` pointing at the full content resource. Pagination lives in `meta`
   (`current_page`, `last_page`, `total`, `next_page_url`) — note this endpoint puts the page URLs
   in `meta`, unlike `listRuleVersions` which uses a sibling `links` object.
3. **Open the hit.** Follow `links.self` (or call `getRuleContent` with the node id) to get the full
   rule text.
4. **Expand the defined terms.** Rule text is HTML. Cross-references to defined terms appear as
   anchors carrying `data-link-type="glossary"` and `data-content="term_<slug>"`. For each one call
   `getGlossaryTerm`: `GET /rules/{versionId}/glossary/term_<slug>` — strip any leading `#` from the
   anchor href first. The response is `{"success":"true","data":{term_id, term, definition}}`.
5. **Browse the glossary when you have no anchor.** `getGlossaryMenu`
   (`GET /rules/{versionId}/glossary/menu`) returns every defined term grouped by first letter;
   `listGlossaryTermsByLetter` (`GET /rules/{versionId}/glossary/by-letter/a`) returns the full
   records for one letter, including `text_definition` (plain text), `alternatives` (other word
   forms), `sourced_from` (the chapter that defines it) and whether the definition is `global`.

## Rules of engagement

- **Definitions are version-scoped.** Resolve terms against the same `versionId` you searched, and
  cite the version number in any answer.
- **`text_definition` before `definition`** when you need plain text — `definition` is HTML.
- **Anonymous, read-only, undocumented.** No key, no OAuth. AEMC publishes no documentation, terms
  of use or SLA for this API; it may change without notice.
- **404 means "not found", 200 does not always mean "found".** Empty `data` with HTTP 200 is the
  response for an unknown rule book, and unmatched paths return the site's HTML shell at HTTP 200 —
  assert `Content-Type: application/json`.
- **Rate limits.** `x-ratelimit-limit: 1000` / `x-ratelimit-remaining` are returned; there is no
  published quota policy. Resolving every term on a long clause can be dozens of calls — cache by
  `term_identifier` + `versionId`.
