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

## Inspired by

[Berghain Klubnacht Database](https://berghain.ravers.workers.dev/) by [jphfa](https://zenn.dev/jphfa) — the first known site to receive x402 payments from AI crawlers.

## License

MIT (this README and public API documentation)
