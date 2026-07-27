# Australian Energy Market Commission (aemc)

The Australian Energy Market Commission (AEMC) is the independent statutory rule maker for Australia's energy markets, established in 2005 and based in Sydney. It makes and amends the National Electricity Rules, National Gas Rules and National Energy Retail Rules, conducts market reviews, and advises the Energy and Climate Change Ministerial Council. It sits upstream of every other body in the Australian energy value chain — it writes the obligations that AEMO operates, that the AER enforces, and that retailers and networks must meet — but it operates no market systems and holds no consumer data itself. Its API posture is honest to state: there is none.

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

None. The AEMC publishes no API and no developer portal.

Probed on 2026-07-27: `developer.`, `developers.`, `api.`, `docs.`, `data.`, `rules.` and `energyrules.aemc.gov.au` do not resolve; `/developers`, `/api`, `/docs`, `/openapi.json`, `/swagger.json`, `/api-docs`, `/jsonapi`, `/graphql`, `/apis.json`, `/.well-known/apis.json` and `/.well-known/openid-configuration` all return 404. The only machine-readable surface on the domain is the Drupal site feed at [/rss.xml](https://www.aemc.gov.au/rss.xml) (HTTP 200), which is recorded as a common property rather than as an API.

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

## Maintainers

- Kin Lane — kin@apievangelist.com
