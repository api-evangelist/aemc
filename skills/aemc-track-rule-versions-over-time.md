---
name: Track energy rule versions over time
description: Find which version of the Australian energy rules was in force on a given date, and diff a clause between two consolidations.
api: openapi/aemc-energy-rules-openapi-derived.yml
operations: [listRuleVersions, getRuleTableOfContents, getRuleContent]
generated: '2026-07-27'
method: generated
---

# Track energy rule versions over time

Every consolidation of the National Electricity, Gas and Energy Retail Rules is retained and
addressable, with commencement and start dates — 304 NER versions, 115 NGR and 65 NERR as at
2026-07-27. That makes point-in-time compliance questions answerable.

## Steps

1. **Find the version in force on a date.** `listRuleVersions` with `searchDate`:
   `GET /rules/ner/versions?searchDate=2020-01-01&perPage=1`. Verified 2026-07-27 — that call
   returns NER version 132. Read `commencement_date`, `start_date`, `end_date`, `is_current` and
   `archived` from the result, and keep the `id`.
2. **Or walk the history.** `GET /rules/{ruleType}/versions?page=1&perPage=30` pages newest-first
   through the history (`meta.total` is the count). `showAll=true` returns everything in one
   response and ignores `perPage` — 4.5 MB for `ner`, so only use it when you genuinely need the
   whole series.
3. **Get the published artefacts.** Each version carries `files.pdf` and `files.docx`: the full
   document, the coversheet/contents, and one file per chapter, each with `name`, `filename`, `size`
   and an absolute `path` on AEMC's S3 bucket. The `hash` field is the content hash that appears in
   those paths.
4. **Compare a clause across versions.** For each version id, call `getRuleTableOfContents`
   (`GET /rules/{versionId}/toc`), find the node whose `index` matches the citation you care about
   (e.g. `11.Part ZF`) — node ids are **not** stable across versions, so match on `index` and
   `title`, never on id — then call `getRuleContent` on each and compare the `content` HTML.
5. **Report with citations.** Always state the rule book, version number, and the date the version
   started, for both sides of any comparison.

## Rules of engagement

- **Match on `index`, not on node id, across versions.** Ids are per-version.
- **Version id, not version number,** in every path parameter.
- **`is_current` and `archived`** are the authoritative status flags; a version can be approved but
  superseded.
- **This is legal text.** Reproduce it and cite it; do not restate a rule as advice, and do not
  imply AEMC endorses the retrieval path — this API is undocumented and unsupported.
- **Anonymous and rate-limited by header only** (`x-ratelimit-limit: 1000`); no published policy.
- Full-history calls are large — send `Accept-Encoding: gzip` and cache aggressively.
