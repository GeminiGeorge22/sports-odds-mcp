# Sports Odds API (BetRivers, Unibet & 22 more books)

**Languages:** English · [简体中文](README.zh-CN.md) · [日本語](README.ja.md) · [한국어](README.ko.md) · [Español](README.es.md) · [Português (Brasil)](README.pt-BR.md) · [Deutsch](README.de.md) · [Français](README.fr.md) · [Русский](README.ru.md) · [Türkçe](README.tr.md)

Live odds from 24 Kambi-powered sportsbooks in one call — BetRivers (12 US states + Ontario), Unibet, Paf, Svenska Spel, ATG. One row per game with every book's price and the best price per outcome. Pay per call, no subscription.

- Apify Store: https://apify.com/publicrecords/sports-odds-api
- MCP server: https://mcp.apify.com?tools=publicrecords/sports-odds-api

## MCP endpoint

```
https://mcp.apify.com?tools=publicrecords/sports-odds-api
```

Transport: Streamable HTTP (hosted by Apify, see https://docs.apify.com/mcp).

## Auth

Sign in with Apify OAuth when your client prompts you, or send the header
`Authorization: Bearer <APIFY_TOKEN>` where `<APIFY_TOKEN>` is your own Apify API token.
Never commit a real token.

## Client setup

### Claude

Claude Code:

```
claude mcp add --transport http sports-odds "https://mcp.apify.com?tools=publicrecords/sports-odds-api"
```

Claude Desktop / claude.ai: Settings → Connectors → Add custom connector, and paste the MCP endpoint URL above.

### Cursor

`~/.cursor/mcp.json`:

```json
{
  "mcpServers": {
    "sports-odds": {
      "url": "https://mcp.apify.com?tools=publicrecords/sports-odds-api"
    }
  }
}
```

### VS Code

`.vscode/mcp.json`:

```json
{
  "servers": {
    "sports-odds": {
      "type": "http",
      "url": "https://mcp.apify.com?tools=publicrecords/sports-odds-api"
    }
  }
}
```

To use a token instead of OAuth, add `"headers": { "Authorization": "Bearer <APIFY_TOKEN>" }` next to `"url"`.

---

Disclosure: I maintain this Actor.

## Local stdio server (open source)

This repo also ships a small MCP server in [`src/`](src/) for clients that only run local stdio servers. It starts over stdio, connects to the hosted Apify MCP endpoint above with **your own** `APIFY_TOKEN`, and forwards `tools/list` and `tools/call` unchanged. The token is only sent in the `Authorization` header and is never logged.

```json
{
  "mcpServers": {
    "sports-odds": {
      "command": "npx",
      "args": ["-y", "github:GeminiGeorge22/sports-odds-mcp"],
      "env": { "APIFY_TOKEN": "YOUR_APIFY_TOKEN" }
    }
  }
}
```

Or from a clone:

```bash
git clone https://github.com/GeminiGeorge22/sports-odds-mcp.git
cd sports-odds-mcp && npm install
APIFY_TOKEN=YOUR_APIFY_TOKEN node src/server.js
```

Optional env: `APIFY_ACTORS` (comma-separated subset of the Actors above) and `APIFY_MCP_URL` (full endpoint override).

Tests run against an in-memory mock server, with no network and no token: `npm test`. Requires Node.js 18+.

## See also

- [Awesome Sports Odds MCP](https://github.com/GeminiGeorge22/awesome-sports-odds-mcp): a curated list of sports odds MCP servers, one provider per sportsbook.
- [ecommerce-search-rankings-mcp](https://github.com/GeminiGeorge22/ecommerce-search-rankings-mcp): E-commerce search results and product rankings across Amazon, eBay, Walmart, Google Shopping, AliExpress, Shopify and Etsy.
- [ecommerce-sales-mcp](https://github.com/GeminiGeorge22/ecommerce-sales-mcp): E-commerce sales signals: Amazon bestsellers and reviews, eBay sold prices, TikTok Shop and Etsy shop sales.
- [forecast-accuracy-mcp](https://github.com/GeminiGeorge22/forecast-accuracy-mcp): Forecast accuracy and track records: forecasts vs actuals, earnings beats, prediction markets, archived pages and news.
- [sports-betting-stats-mcp](https://github.com/GeminiGeorge22/sports-betting-stats-mcp): Sports betting odds and stats: sportsbook odds, player props, scores, xG, closing lines, horse racing.
- [etsy-sales-mcp](https://github.com/GeminiGeorge22/etsy-sales-mcp): Etsy search results and Etsy shop sales counters.
- [ats-jobs-mcp](https://github.com/GeminiGeorge22/ats-jobs-mcp): New job postings from Greenhouse, Lever, Ashby and SmartRecruiters.
- [gov-tenders-mcp](https://github.com/GeminiGeorge22/gov-tenders-mcp): Government tenders, grants, awards and council meetings.
