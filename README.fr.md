# API de cotes sportives (BetRivers, Unibet et autres bookmakers Kambi) — serveur MCP

**API de cotes sportives, cotes en direct et comparateur de cotes** en un seul appel : les cotes actuelles des bookmakers qui utilisent la plateforme Kambi (BetRivers, Unibet, Paf, Svenska Spel, ATG, etc.). Une ligne par match avec la cote de chaque bookmaker et la meilleure cote pour chaque issue. Idéal pour comparer les cotes, repérer les value bets, nourrir un modèle de prédiction ou un tableau de bord.

Fonctionne dans Claude, Cursor, VS Code et d'autres clients IA grâce au serveur MCP hébergé par Apify. Aucun scraper à maintenir.

## Cas d'usage

- Comparer les cotes de plusieurs bookmakers et trouver la meilleure
- Suivre les cotes en football, basket, tennis et hockey
- Récupérer des données de cotes structurées pour vos modèles et analyses
- Demander à votre assistant en français : « Quel match de Ligue 1 ce soir a la meilleure cote pour la victoire à domicile ? »

## Endpoint MCP

```
https://mcp.apify.com?tools=publicrecords/sports-odds-api
```

Transport: Streamable HTTP (Apify: https://docs.apify.com/mcp)

## Authentification

Connectez-vous avec Apify OAuth quand votre client le demande, ou envoyez l'en-tête `Authorization: Bearer <APIFY_TOKEN>` avec votre propre jeton d'API Apify. Ne commitez jamais un vrai jeton. Les exécutions sont facturées sur votre propre compte Apify.

## Configuration du client

### Claude Code

```
claude mcp add --transport http sports-odds "https://mcp.apify.com?tools=publicrecords/sports-odds-api"
```

Claude Desktop / claude.ai : Paramètres → Connectors → Ajouter un connecteur personnalisé, puis collez l'endpoint MCP ci-dessus.

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

Pour utiliser un jeton plutôt qu'OAuth, ajoutez `"headers": { "Authorization": "Bearer <APIFY_TOKEN>" }` à côté de `"url"`.

## Liens

- Page sur l'Apify Store: https://apify.com/publicrecords/sports-odds-api
- Documentation complète en anglais: [README.md](README.md)

> Données de cotes uniquement ; aucun service de pari. Respectez la réglementation de votre pays.

---

Transparence : je maintiens cet Actor.
