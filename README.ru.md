# API коэффициентов на спорт (BetRivers, Unibet и другие букмекеры Kambi) — MCP-сервер

**API спортивных коэффициентов, live-коэффициенты и сравнение коэффициентов** за один запрос: актуальные линии букмекеров на платформе Kambi (BetRivers, Unibet, Paf, Svenska Spel, ATG и другие). Одна строка на матч: коэффициент каждого букмекера и лучший коэффициент для каждого исхода. Подходит для сравнения коэффициентов, поиска валуйных ставок, прогнозных моделей и дашбордов.

Работает в Claude, Cursor, VS Code и других ИИ-клиентах через MCP-сервер, размещённый на Apify. Свой парсер поддерживать не нужно.

## Сценарии

- Сравнение коэффициентов разных букмекеров и поиск лучшего
- Мониторинг линий по футболу, баскетболу, теннису и хоккею
- Структурированные данные коэффициентов для моделей и аналитики
- Вопрос ИИ-ассистенту по-русски: «В каком матче АПЛ сегодня самый высокий коэффициент на победу хозяев?»

## MCP-эндпоинт

```
https://mcp.apify.com?tools=publicrecords/sports-odds-api
```

Transport: Streamable HTTP (Apify: https://docs.apify.com/mcp)

## Авторизация

Войдите через Apify OAuth, когда клиент попросит, или передайте заголовок `Authorization: Bearer <APIFY_TOKEN>` со своим токеном Apify API. Никогда не коммитьте настоящий токен. Запуски оплачиваются с вашего собственного аккаунта Apify.

## Настройка клиента

### Claude Code

```
claude mcp add --transport http sports-odds "https://mcp.apify.com?tools=publicrecords/sports-odds-api"
```

Claude Desktop / claude.ai: Настройки → Connectors → Добавить свой коннектор и вставьте MCP-эндпоинт выше.

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

Чтобы использовать токен вместо OAuth, добавьте `"headers": { "Authorization": "Bearer <APIFY_TOKEN>" }` рядом с `"url"`.

## Ссылки

- Страница в Apify Store: https://apify.com/publicrecords/sports-odds-api
- Полная документация на английском: [README.md](README.md)
- См. также: [Awesome Sports Odds MCP](https://github.com/GeminiGeorge22/awesome-sports-odds-mcp) (подборка)

> Только данные о коэффициентах; услуги приёма ставок не предоставляются. Соблюдайте законы своей страны.

---

Раскрытие: этот Actor поддерживаю я.
