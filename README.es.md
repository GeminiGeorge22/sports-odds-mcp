# API de cuotas deportivas (BetRivers, Unibet y otras casas Kambi) — servidor MCP

**API de cuotas deportivas, cuotas en vivo y comparador de cuotas** en una sola llamada: precios actuales de las casas de apuestas que usan la plataforma Kambi (BetRivers, Unibet, Paf, Svenska Spel, ATG y más). Devuelve una fila por partido con la cuota de cada casa y la mejor cuota para cada resultado. Ideal para comparar cuotas, buscar apuestas de valor, alimentar modelos predictivos o montar paneles.

Se conecta a Claude, Cursor, VS Code y otros clientes de IA mediante el servidor MCP alojado por Apify. No tienes que mantener ningún scraper.

## Casos de uso

- Comparar cuotas entre casas y encontrar la mejor
- Seguir cuotas de fútbol, baloncesto, tenis y hockey
- Obtener datos de cuotas estructurados para modelos y análisis
- Preguntar a tu asistente en español: «¿Qué partido de LaLiga de esta noche paga más por la victoria local?»

## Endpoint MCP

```
https://mcp.apify.com?tools=publicrecords/sports-odds-api
```

Transport: Streamable HTTP (Apify: https://docs.apify.com/mcp)

## Autenticación

Inicia sesión con Apify OAuth cuando tu cliente lo pida, o envía la cabecera `Authorization: Bearer <APIFY_TOKEN>` con tu propio token de API de Apify. Nunca subas un token real al repositorio. Las ejecuciones se cobran en tu propia cuenta de Apify.

## Configuración del cliente

### Claude Code

```
claude mcp add --transport http sports-odds "https://mcp.apify.com?tools=publicrecords/sports-odds-api"
```

Claude Desktop / claude.ai: Ajustes → Connectors → Añadir conector personalizado y pega el endpoint MCP de arriba.

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

Para usar un token en lugar de OAuth, añade `"headers": { "Authorization": "Bearer <APIFY_TOKEN>" }` junto a `"url"`.

## Enlaces

- Página en Apify Store: https://apify.com/publicrecords/sports-odds-api
- Documentación completa en inglés: [README.md](README.md)
- Ver también: [Awesome Sports Odds MCP](https://github.com/GeminiGeorge22/awesome-sports-odds-mcp) (lista seleccionada)

> Solo datos de cuotas; no ofrece servicios de apuestas. Respeta la normativa de tu país.

---

Aviso: mantengo este Actor.
