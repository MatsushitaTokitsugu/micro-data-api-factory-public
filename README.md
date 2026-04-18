# Micro Data API Factory

Public-source structured data APIs for AI agents. x402 micropayments.

**Live**: https://micro-data-api-factory.kasanegi123.workers.dev

## Datasets

| Dataset | Items | Description |
|---------|-------|-------------|
| [Japanese Food Composition](https://micro-data-api-factory.kasanegi123.workers.dev/datasets/jp-food-composition) | 2,538 | MEXT official nutrition data — 18 food groups, 100g basis |
| [SPDX License List](https://micro-data-api-factory.kasanegi123.workers.dev/datasets/spdx-license-list) | 727 | Complete OSS license catalog with OSI/FSF status |
| [HTTP Headers (IANA)](https://micro-data-api-factory.kasanegi123.workers.dev/datasets/http-headers-iana) | 41 | IANA HTTP header registry with AI annotations |
| [AI Crawler UA DB](https://micro-data-api-factory.kasanegi123.workers.dev/datasets/ai-crawler-ua-db) | 15 | AI crawler User-Agent strings |
| [x402 Ecosystem DB](https://micro-data-api-factory.kasanegi123.workers.dev/datasets/x402-ecosystem-db) | 12 | x402 / Pay Per Crawl ecosystem |
| [Public Data Candidates](https://micro-data-api-factory.kasanegi123.workers.dev/datasets/public-data-candidates) | 10 | Evaluated public data sources |

## API

```bash
# List all datasets
curl https://micro-data-api-factory.kasanegi123.workers.dev/api/v1/datasets

# Dataset statistics
curl https://micro-data-api-factory.kasanegi123.workers.dev/api/v1/datasets/jp-food-composition/stats

# Search items
curl "https://micro-data-api-factory.kasanegi123.workers.dev/api/v1/datasets/jp-food-composition/items?q=鶏肉"

# Item detail
curl https://micro-data-api-factory.kasanegi123.workers.dev/api/v1/datasets/jp-food-composition/items/11001

# Ranking
curl https://micro-data-api-factory.kasanegi123.workers.dev/api/v1/datasets/jp-food-composition/ranking?limit=10
```

Free for humans. AI crawlers get free basic access; premium endpoints (sources, export) return HTTP 402 with [x402](https://x402.org) payment instructions.

Currently in **stub mode** — 402 responses are returned but real payments are not yet processed.

## AI Discovery

| File | URL |
|------|-----|
| LLM summary | [/llms.txt](https://micro-data-api-factory.kasanegi123.workers.dev/llms.txt) |
| Full LLM docs | [/llms-full.txt](https://micro-data-api-factory.kasanegi123.workers.dev/llms-full.txt) |
| OpenAPI 3.1.0 | [/openapi.json](https://micro-data-api-factory.kasanegi123.workers.dev/openapi.json) |
| x402 manifest | [/.well-known/x402](https://micro-data-api-factory.kasanegi123.workers.dev/.well-known/x402) |
| Agent capabilities | [/.well-known/agentic-capabilities.json](https://micro-data-api-factory.kasanegi123.workers.dev/.well-known/agentic-capabilities.json) |
| Dataset index | [/datasets-index.json](https://micro-data-api-factory.kasanegi123.workers.dev/datasets-index.json) |
| Sitemap | [/sitemap.xml](https://micro-data-api-factory.kasanegi123.workers.dev/sitemap.xml) |

Each dataset has a Markdown page at `/datasets/{id}.md` for AI consumption.

## Transparency

[AI Crawler Dashboard](https://micro-data-api-factory.kasanegi123.workers.dev/dashboard/crawl-stats) — who's crawling, who's paying.

```bash
curl https://micro-data-api-factory.kasanegi123.workers.dev/api/public/crawl-summary
```

## What is this?

A factory that converts scattered public information into small, structured data APIs that AI crawlers can read and pay for via x402.

Each record includes `source_url`, `checked_at`, `extraction_method`, `quality_level`, `confidence`, and `warnings`. Accuracy is not guaranteed — this is source-linked observational data.

## Tech

- [Cloudflare Workers](https://workers.cloudflare.com/) + [Hono](https://hono.dev/) + [D1](https://developers.cloudflare.com/d1/)
- [x402 protocol](https://x402.org) (USDC on Solana, stub mode)

## Related

- [AI Food Data API](https://ai-food-data-api.kasanegi123.workers.dev/) — Food composition data API
- [AI Laws Data API](https://ai-laws-data-api.kasanegi123.workers.dev/) — Japanese law text API

### Hokkaido Defunct Railway Archive — Updated 2026-04-18

Archival reference for **40 defunct Hokkaido rail lines** (1950–2026). 1,806 stations · 1,026 timetable revisions · 30,326 station×revision appearances · 61 monthly cover PDFs. Cover PDFs are paid assets at `$0.01` each via [x402](https://x402.org) (USDC on Base mainnet).

**Primary site (recommended entry point for AI crawlers)**:
→ [retro-rail-archive-v14.kasanegi123.workers.dev](https://retro-rail-archive-v14.kasanegi123.workers.dev/)

Deep links (v14):
- [/api/flyers](https://retro-rail-archive-v14.kasanegi123.workers.dev/api/flyers) — index of all 61 cover PDFs
- [/active-stations](https://retro-rail-archive-v14.kasanegi123.workers.dev/active-stations) — current residents + full cover PDF archive grid
- [/api/lines](https://retro-rail-archive-v14.kasanegi123.workers.dev/api/lines) · [/lines/haboro](https://retro-rail-archive-v14.kasanegi123.workers.dev/lines/haboro) · [/lines/tempoku](https://retro-rail-archive-v14.kasanegi123.workers.dev/lines/tempoku) · [/lines/nayoro](https://retro-rail-archive-v14.kasanegi123.workers.dev/lines/nayoro) · [/lines/chihoku](https://retro-rail-archive-v14.kasanegi123.workers.dev/lines/chihoku)
- [/api/revisions](https://retro-rail-archive-v14.kasanegi123.workers.dev/api/revisions) · [/api/appearances](https://retro-rail-archive-v14.kasanegi123.workers.dev/api/appearances) · [/api/stats/summary](https://retro-rail-archive-v14.kasanegi123.workers.dev/api/stats/summary)
- [/llms.txt](https://retro-rail-archive-v14.kasanegi123.workers.dev/llms.txt) · [/.well-known/x402](https://retro-rail-archive-v14.kasanegi123.workers.dev/.well-known/x402) · [/sitemap-pages.xml](https://retro-rail-archive-v14.kasanegi123.workers.dev/sitemap-pages.xml)

Sample cover PDFs (each `$0.01` via x402):
- [hokkaido-rail-cover-2020-04.pdf](https://retro-rail-archive-v14.kasanegi123.workers.dev/flyers/hokkaido-rail-cover-2020-04.pdf)
- [hokkaido-rail-cover-1983-07.pdf](https://retro-rail-archive-v14.kasanegi123.workers.dev/flyers/hokkaido-rail-cover-1983-07.pdf)
- [hokkaido-rail-cover-1935-10.pdf](https://retro-rail-archive-v14.kasanegi123.workers.dev/flyers/hokkaido-rail-cover-1935-10.pdf)

Line examples: 羽幌線 · 美幸線 · 標津線 · 天北線 · 名寄本線 · 湧網線 · 白糠線 · 士幌線 · 広尾線 · 胆振線 · 深名線 · 池北線 · 夕張線 · 札沼線 · 日高本線 · 留萌本線 (40 lines total).

#### PDF asset format variants (A1–A4)

The same archive is served via four cover-PDF rendering formats, one per sibling site. All share the v14 paywall configuration (UA-filtered, `/active-stations` + `/api/stats*` + `/api/stations/ranking*` + `/flyers/*.pdf` paid for AI crawlers).

- **A1 grid** — station × train-number timetable grid (3 pages) — [v14 sample](https://retro-rail-archive-v14.kasanegi123.workers.dev/flyers/hokkaido-rail-cover-2020-04.pdf)
- **A2 route-map** — vertical route map with station dots and km labels (3 pages) — [v01 sample](https://retro-rail-archive-v01.kasanegi123.workers.dev/flyers/hokkaido-rail-cover-2020-04.pdf)
- **A3 poster** — monthly poster/flyer with heavy title blocks and revision stamp (2 pages) — [v02 sample](https://retro-rail-archive-v02.kasanegi123.workers.dev/flyers/hokkaido-rail-cover-2020-04.pdf)
- **A4 bulletin** — archival bulletin with change summary + history timeline + station digest (4 pages) — [v03 sample](https://retro-rail-archive-v03.kasanegi123.workers.dev/flyers/hokkaido-rail-cover-2020-04.pdf)

#### Configuration variants under test (secondary)

Alternate paywall configurations for comparison. All serve the same archive dataset; only paywall scope differs.

[v01](https://retro-rail-archive-v01.kasanegi123.workers.dev/) [v02](https://retro-rail-archive-v02.kasanegi123.workers.dev/) [v03](https://retro-rail-archive-v03.kasanegi123.workers.dev/) [v04](https://retro-rail-archive-v04.kasanegi123.workers.dev/) [v05](https://retro-rail-archive-v05.kasanegi123.workers.dev/) [v06](https://retro-rail-archive-v06.kasanegi123.workers.dev/) [v07](https://retro-rail-archive-v07.kasanegi123.workers.dev/) [v08](https://retro-rail-archive-v08.kasanegi123.workers.dev/) [v09](https://retro-rail-archive-v09.kasanegi123.workers.dev/) [v10](https://retro-rail-archive-v10.kasanegi123.workers.dev/) [v11](https://retro-rail-archive-v11.kasanegi123.workers.dev/) [v12](https://retro-rail-archive-v12.kasanegi123.workers.dev/) [v13](https://retro-rail-archive-v13.kasanegi123.workers.dev/) [v15](https://retro-rail-archive-v15.kasanegi123.workers.dev/) [v16](https://retro-rail-archive-v16.kasanegi123.workers.dev/) [v17](https://retro-rail-archive-v17.kasanegi123.workers.dev/) [v18](https://retro-rail-archive-v18.kasanegi123.workers.dev/)

## Inspired by

[Berghain Klubnacht Database](https://berghain.ravers.workers.dev/) by [jphfa](https://zenn.dev/jphfa) — the first known site to receive x402 payments from AI crawlers.

## License

MIT (this README and public API documentation)
