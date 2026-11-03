# API de odds esportivas (BetRivers, Unibet e outras casas Kambi) — servidor MCP

**API de odds esportivas, odds ao vivo e comparador de odds** em uma única chamada: preços atuais das casas de apostas que usam a plataforma Kambi (BetRivers, Unibet, Paf, Svenska Spel, ATG e outras). Retorna uma linha por jogo com a odd de cada casa e a melhor odd para cada resultado. Bom para comparar odds, achar apostas de valor, alimentar modelos de previsão e montar dashboards.

Funciona com Claude, Cursor, VS Code e outros clientes de IA pelo servidor MCP hospedado pela Apify. Você não precisa manter nenhum scraper.

## Casos de uso

- Comparar odds entre casas e achar a melhor
- Acompanhar odds de futebol, basquete, tênis e hóquei
- Obter dados de odds estruturados para modelos e análises
- Perguntar ao seu assistente em português: "Qual jogo da Premier League hoje à noite paga mais pela vitória do mandante?"

## Endpoint MCP

```
https://mcp.apify.com?tools=publicrecords/sports-odds-api
```

Transport: Streamable HTTP (Apify: https://docs.apify.com/mcp)

## Autenticação

Entre com Apify OAuth quando o cliente pedir, ou envie o cabeçalho `Authorization: Bearer <APIFY_TOKEN>` com o seu próprio token de API da Apify. Nunca faça commit de um token real. As execuções são cobradas na sua própria conta Apify.

## Configuração do cliente

### Claude Code

```
claude mcp add --transport http sports-odds "https://mcp.apify.com?tools=publicrecords/sports-odds-api"
```

Claude Desktop / claude.ai: Configurações → Connectors → Adicionar conector personalizado e cole o endpoint MCP acima.

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

Para usar token em vez de OAuth, adicione `"headers": { "Authorization": "Bearer <APIFY_TOKEN>" }` ao lado de `"url"`.

## Links

- Página na Apify Store: https://apify.com/publicrecords/sports-odds-api
- Documentação completa em inglês: [README.md](README.md)

> Somente dados de odds; não oferece serviços de apostas. Siga a legislação do seu país.

---

Aviso: eu mantenho este Actor.
