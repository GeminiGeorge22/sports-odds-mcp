# Sportwetten-Quoten-API (BetRivers, Unibet und weitere Kambi-Buchmacher) — MCP-Server

**Quoten-API für Sportwetten, Live-Quoten und Quotenvergleich** mit einem einzigen Aufruf: aktuelle Quoten der Buchmacher auf der Kambi-Plattform (BetRivers, Unibet, Paf, Svenska Spel, ATG und weitere). Pro Spiel eine Zeile mit der Quote jedes Anbieters und der besten Quote je Ausgang. Geeignet für Quotenvergleiche, Value-Bet-Suche, Prognosemodelle und Dashboards.

Läuft in Claude, Cursor, VS Code und anderen KI-Clients über den von Apify gehosteten MCP-Server. Kein eigener Scraper nötig.

## Anwendungsfälle

- Quoten mehrerer Buchmacher vergleichen und die beste finden
- Quoten für Fußball, Basketball, Tennis und Eishockey verfolgen
- Strukturierte Quotendaten für Modelle und Analysen abrufen
- Den KI-Assistenten auf Deutsch fragen: „Welches Bundesliga-Spiel heute hat die höchste Quote auf Heimsieg?“

## MCP-Endpunkt

```
https://mcp.apify.com?tools=publicrecords/sports-odds-api
```

Transport: Streamable HTTP (Apify: https://docs.apify.com/mcp)

## Authentifizierung

Melde dich mit Apify OAuth an, wenn dein Client danach fragt, oder sende den Header `Authorization: Bearer <APIFY_TOKEN>` mit deinem eigenen Apify-API-Token. Committe niemals ein echtes Token. Ausführungen werden über dein eigenes Apify-Konto abgerechnet.

## Client-Einrichtung

### Claude Code

```
claude mcp add --transport http sports-odds "https://mcp.apify.com?tools=publicrecords/sports-odds-api"
```

Claude Desktop / claude.ai: Einstellungen → Connectors → Benutzerdefinierten Connector hinzufügen und den MCP-Endpunkt oben einfügen.

### Cursor (`~/.cursor/mcp.json`)

```json
{
  "mcpServers": {
    "sports-odds": {
      "url": "https://mcp.apify.com?tools=publicrecords/sports-odds-api"
    }
  }
}
```

### VS Code (`.vscode/mcp.json`)

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

Für ein Token statt OAuth `"headers": { "Authorization": "Bearer <APIFY_TOKEN>" }` neben `"url"` ergänzen.

## Links

- Seite im Apify Store: https://apify.com/publicrecords/sports-odds-api
- Vollständige Doku auf Englisch: [README.md](README.md)

> Nur Quotendaten, keine Wettdienste. Bitte beachte die Gesetze in deinem Land.

---

Hinweis: Ich pflege diesen Actor.
