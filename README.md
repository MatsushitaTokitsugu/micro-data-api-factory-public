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

### Defunct Japanese Railway Archive (Variant Test Series)

x402 paywall configuration A/B test sites. Each variant differs in UA filtering and paywall scope; binary timetable PDFs at `$0.01` via x402.

**JR Haboro Line (1927–1987)** — 27 stations, 141.1 km
[v01](https://retro-rail-archive-v01.kasanegi123.workers.dev/) [v02](https://retro-rail-archive-v02.kasanegi123.workers.dev/) [v03](https://retro-rail-archive-v03.kasanegi123.workers.dev/) [v04](https://retro-rail-archive-v04.kasanegi123.workers.dev/) [v05](https://retro-rail-archive-v05.kasanegi123.workers.dev/) [v06](https://retro-rail-archive-v06.kasanegi123.workers.dev/) [v07](https://retro-rail-archive-v07.kasanegi123.workers.dev/) [v08](https://retro-rail-archive-v08.kasanegi123.workers.dev/) [v09](https://retro-rail-archive-v09.kasanegi123.workers.dev/) [v10](https://retro-rail-archive-v10.kasanegi123.workers.dev/) [v11](https://retro-rail-archive-v11.kasanegi123.workers.dev/) [v12](https://retro-rail-archive-v12.kasanegi123.workers.dev/) [v13](https://retro-rail-archive-v13.kasanegi123.workers.dev/) [v14](https://retro-rail-archive-v14.kasanegi123.workers.dev/) [v15](https://retro-rail-archive-v15.kasanegi123.workers.dev/) [v16](https://retro-rail-archive-v16.kasanegi123.workers.dev/) [v17](https://retro-rail-archive-v17.kasanegi123.workers.dev/) [v18](https://retro-rail-archive-v18.kasanegi123.workers.dev/)

**JR Bihoro Line (1924–1985)** — 6 stations, 21.2 km
[v01](https://retro-rail-bihoro-v01.kasanegi123.workers.dev/) [v02](https://retro-rail-bihoro-v02.kasanegi123.workers.dev/) [v03](https://retro-rail-bihoro-v03.kasanegi123.workers.dev/) [v04](https://retro-rail-bihoro-v04.kasanegi123.workers.dev/) [v05](https://retro-rail-bihoro-v05.kasanegi123.workers.dev/) [v06](https://retro-rail-bihoro-v06.kasanegi123.workers.dev/) [v07](https://retro-rail-bihoro-v07.kasanegi123.workers.dev/) [v08](https://retro-rail-bihoro-v08.kasanegi123.workers.dev/) [v09](https://retro-rail-bihoro-v09.kasanegi123.workers.dev/) [v10](https://retro-rail-bihoro-v10.kasanegi123.workers.dev/) [v11](https://retro-rail-bihoro-v11.kasanegi123.workers.dev/) [v12](https://retro-rail-bihoro-v12.kasanegi123.workers.dev/) [v13](https://retro-rail-bihoro-v13.kasanegi123.workers.dev/) [v14](https://retro-rail-bihoro-v14.kasanegi123.workers.dev/) [v15](https://retro-rail-bihoro-v15.kasanegi123.workers.dev/) [v16](https://retro-rail-bihoro-v16.kasanegi123.workers.dev/) [v17](https://retro-rail-bihoro-v17.kasanegi123.workers.dev/) [v18](https://retro-rail-bihoro-v18.kasanegi123.workers.dev/)

**JR Shibetsu Line (1933–1989)** — 13 stations, 116.9 km
[v01](https://retro-rail-shibetsu-v01.kasanegi123.workers.dev/) [v02](https://retro-rail-shibetsu-v02.kasanegi123.workers.dev/) [v03](https://retro-rail-shibetsu-v03.kasanegi123.workers.dev/) [v04](https://retro-rail-shibetsu-v04.kasanegi123.workers.dev/) [v05](https://retro-rail-shibetsu-v05.kasanegi123.workers.dev/) [v06](https://retro-rail-shibetsu-v06.kasanegi123.workers.dev/) [v07](https://retro-rail-shibetsu-v07.kasanegi123.workers.dev/) [v08](https://retro-rail-shibetsu-v08.kasanegi123.workers.dev/) [v09](https://retro-rail-shibetsu-v09.kasanegi123.workers.dev/) [v10](https://retro-rail-shibetsu-v10.kasanegi123.workers.dev/) [v11](https://retro-rail-shibetsu-v11.kasanegi123.workers.dev/) [v12](https://retro-rail-shibetsu-v12.kasanegi123.workers.dev/) [v13](https://retro-rail-shibetsu-v13.kasanegi123.workers.dev/) [v14](https://retro-rail-shibetsu-v14.kasanegi123.workers.dev/) [v15](https://retro-rail-shibetsu-v15.kasanegi123.workers.dev/) [v16](https://retro-rail-shibetsu-v16.kasanegi123.workers.dev/) [v17](https://retro-rail-shibetsu-v17.kasanegi123.workers.dev/) [v18](https://retro-rail-shibetsu-v18.kasanegi123.workers.dev/)

## Inspired by

[Berghain Klubnacht Database](https://berghain.ravers.workers.dev/) by [jphfa](https://zenn.dev/jphfa) — the first known site to receive x402 payments from AI crawlers.

## License

MIT (this README and public API documentation)
