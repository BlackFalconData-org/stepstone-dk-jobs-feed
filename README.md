# StepStone DK Jobs Feed

Extract structured data from [stepstone.dk](https://stepstone.dk) — structured job listings from stepstone.dk — Denmark's StepStone portal for management and specialist positions.

**[StepStone DK Scraper - Denmark Jobs on Apify →](https://apify.com/blackfalcondata/stepstone-dk-scraper?fpr=1h3gvi)**

---

## Key features





**Search with filters** — Search by keyword and location. Filter by region, employment type, remote work, and more.

**Detail enrichment** — Fetch full job descriptions, salary data, employer profiles, contact information for each listing.

**Incremental mode** — Only get new or changed listings since your last run. Content hash per listing — no duplicates, no re-processing.

**Compact output** — Emit core fields only (AI-agent / MCP-friendly). Keeps response size small for LLM workflows.

**Description truncation** — Cap description length per listing to control output size and cost.

**Result cap** — Stop after N listings (up to 1.250). Set to 0 for the full catalog.

**Export anywhere** — Download as JSON, CSV, or Excel. Stream via Apify API, webhooks, or integrations with Make, Zapier, Airbyte, Keboola.

**Structured data** — Every listing returns the same schema with consistent field naming. All fields always present — `null` when unavailable, never omitted.

---

## Use cases





**Data pipeline automation**
Integrate with your ETL pipeline to collect structured listings from stepstone.dk on a schedule. Export to CSV, JSON, or directly to your database. Use compact mode to control output size.

**Market research**
Monitor listings, track trends, and analyze market dynamics with structured, deduplicated data from stepstone.dk.

**Change monitoring**
Run daily or hourly in incremental mode to capture only new, updated, or expired listings. Perfect for price-tracking, churn analysis, and alerting pipelines.

**Lead generation**
Extract employer contact details alongside listings to build outreach lists for recruiters, staffing agencies, or B2B sales teams.

**AI / LLM training data**
Structured JSON per listing is ready for RAG pipelines, embeddings, and agent workflows. Compact mode trims tokens for LLM context windows.

---

## Quick start

```json
{
  "query": "software",
  "maxResults": 50,
  "includeDetails": true
}
```

---

## Input parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `query` | string | — | Job search keywords (e.g. 'software engineer', 'projektleder'). |
| `location` | string | — | Free-text location (city or area name). Use Region for structured filtering. |
| `region` | enum | — | Filter by Danish region or area. |
| `employmentType` | enum | — | Filter by employment type. |
| `remoteWork` | enum | — | Filter by remote work availability. |
| `workingHours` | enum | — | Filter by working hours type. |
| `jobAge` | enum | — | Only show jobs posted within this period. |
| `maxResults` | integer | `50` | Maximum total results (0 = unlimited). |
| `includeDetails` | boolean | `false` | Fetch full job descriptions from detail pages. Slower but provides complete descriptions. |
| `descriptionMaxLength` | integer | `0` | Truncate description to N characters. 0 = no truncation. |
| `compact` | boolean | `false` | Core fields only (for AI-agent/MCP workflows). |
| `incrementalMode` | boolean | `false` | Only output new/changed jobs compared to previous run. |
| `stateKey` | string | — | Stable identifier for tracked universe. Different stateKeys maintain separate tracking. |

---

## FAQ

<!-- WRITE: 4-6 Q&A pairs relevant to this product -->

**Is it legal to scrape stepstone.dk?**
Web scraping of publicly available data is generally legal. This actor only accesses publicly visible information. Always check the target site's terms of service for your specific use case.

**How does incremental mode work?**
Each listing gets a content hash. On subsequent runs, only new or changed listings are emitted — saving time, compute, and storage.

---

## Known limitations

<!-- WRITE: 4-6 honest limitations -->

- <!-- WRITE: limitation 1 -->
- <!-- WRITE: limitation 2 -->


## Output fields

Every listing returns the same 29-field schema. Missing values are `null` — never omitted.

- `jobId`
- `tid`
- `title`
- `company`
- `workplaceCompany`
- `location`
- `fullAddress`
- `city`
- `zipCode`
- `latitude`
- `longitude`
- `description`
- `employmentType`
- `workingHours`
- `remoteWork`
- `remoteWorkLabel`
- `postedDate`
- `expiresDate`
- `applicationDeadline`
- `applyUrl`
- `url`
- `portalUrl`
- `companyLogoUrl`
- `companyWebsite`
- `contactEmail`
- `contactPhone`
- `salaryText`
- `scrapedAt`
- `source`


## Sample output

One object per listing. Here is a real example from a production run:

```json
{
  "jobId": "8eddb3138d2be78639ebce196eed6fe30d9d05e3a55dd741f1d61cd1fe1b25d8",
  "tid": "h1647246",
  "title": "Technical Lead",
  "company": "PC SCHEMATIC A/S",
  "workplaceCompany": "PC SCHEMATIC A/S",
  "location": "Roskilde",
  "fullAddress": "Gammel Marbjergvej 15, 4000 Roskilde",
  "city": "Roskilde",
  "zipCode": "4000",
  "latitude": 55.6470652,
  "longitude": 12.1407991,
  "description": "Do you want to lead the technical development of the electrical automation software of the future?\n\nWe are looking for a Technical Lead to join our development team.\n\nAre you an ex…"
}
```

*Truncated — full records contain 29 fields. See Output fields for the complete schema.*


**[Try StepStone DK Scraper - Denmark Jobs now — $5 free credit, no credit card →](https://apify.com/blackfalcondata/stepstone-dk-scraper?fpr=1h3gvi)**


## Pricing

Pay only for what you extract. No subscription required — Apify's free $5 credit covers thousands of results.

| Event | Price (USD) |
| --- | --- |
| Actor Start | $0.01 |
| Result | $0.002 |

See the [actor on Apify](https://apify.com/blackfalcondata/stepstone-dk-scraper?fpr=1h3gvi) for current pricing.

---

## Related products by Black Falcon Data





- [StepStone Scraper](https://apify.com/blackfalcondata/stepstone-scraper?fpr=1h3gvi) — Job listings from 18 European portals
- [Indeed Job Scraper](https://apify.com/blackfalcondata/indeed-job-scraper?fpr=1h3gvi) — Indeed job listings with salary data
- [Glassdoor Job Scraper](https://apify.com/blackfalcondata/glassdoor-job-scraper?fpr=1h3gvi) — Glassdoor listings with company ratings
- [Arbeitsagentur Scraper](https://apify.com/blackfalcondata/arbeitsagentur-scraper?fpr=1h3gvi) — Germany's official job portal (1M+ listings)
- [SEEK Scraper](https://apify.com/blackfalcondata/seek-scraper?fpr=1h3gvi) — Australia & NZ's largest job board
- [Naukri Scraper](https://apify.com/blackfalcondata/naukri-scraper?fpr=1h3gvi) — India's largest job portal


## Getting started with Apify

New to Apify? [Create a free account with $5 credit](https://console.apify.com/sign-up?fpr=1h3gvi) — no credit card required.

1. [Sign up free](https://console.apify.com/sign-up?fpr=1h3gvi) — $5 credit included
2. Open the actor and paste your input
3. Click Start — results download as JSON, CSV, or Excel

Need more volume? [See pricing](https://apify.com/pricing?fpr=1h3gvi).

---


## About Black Falcon Data

Black Falcon Data builds production-grade web scrapers for job boards and marketplace data. Browse our full actor catalog at [www.blackfalcondata.com](https://www.blackfalcondata.com).

---
---

*Last updated: 2026 03*
