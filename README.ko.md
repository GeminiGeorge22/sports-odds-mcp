# 스포츠 배당률 API (BetRivers, Unibet 등 Kambi 계열 북메이커) — MCP 서버

**스포츠 배당률 API / 실시간 배당 데이터 / 배당 비교**. Kambi 계열 북메이커(BetRivers, Unibet, Paf, Svenska Spel, ATG 등)의 최신 배당을 한 번의 호출로 가져옵니다. 경기당 한 행으로, 북메이커별 배당과 선택지별 최고 배당을 함께 돌려줍니다. 배당 비교, 밸류 베팅 탐색, 예측 모델, 대시보드에 적합합니다.

Apify가 호스팅하는 MCP 서버로 Claude, Cursor, VS Code 같은 AI 클라이언트에서 바로 쓸 수 있습니다. 크롤러를 직접 운영할 필요가 없습니다.

## 주요 활용

- 여러 북메이커의 배당을 한눈에 비교해 최고 배당 찾기
- 축구·농구·테니스·아이스하키 경기 배당 모니터링
- 예측 모델과 분석용 구조화된 배당 데이터 수집
- AI 어시스턴트에 한국어로 질문: "오늘 밤 프리미어리그에서 홈 승 배당이 가장 높은 경기는?"

## MCP 엔드포인트

```
https://mcp.apify.com?tools=publicrecords/sports-odds-api
```

Transport: Streamable HTTP (Apify: https://docs.apify.com/mcp)

## 인증

클라이언트가 요청하면 Apify OAuth로 로그인하거나, 헤더 `Authorization: Bearer <APIFY_TOKEN>`(본인의 Apify API 토큰)을 보내세요. 실제 토큰은 저장소에 커밋하지 마세요. 실행 비용은 본인의 Apify 계정에 청구됩니다.

## 클라이언트 설정

### Claude Code

```
claude mcp add --transport http sports-odds "https://mcp.apify.com?tools=publicrecords/sports-odds-api"
```

Claude Desktop / claude.ai: 설정 → Connectors → 사용자 지정 커넥터 추가 후 위 MCP 엔드포인트를 붙여 넣으세요.

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

OAuth 대신 토큰을 쓰려면 `"url"` 옆에 `"headers": { "Authorization": "Bearer <APIFY_TOKEN>" }`를 추가하세요.

## 링크

- Apify Store 페이지: https://apify.com/publicrecords/sports-odds-api
- 영어 전체 설명: [README.md](README.md)
- 함께 보기: [Awesome Sports Odds MCP](https://github.com/GeminiGeorge22/awesome-sports-odds-mcp) (엄선 목록)

> 배당 데이터만 제공하며 베팅 서비스는 제공하지 않습니다. 거주 지역의 법령을 지켜 주세요.

---

고지: 이 Actor는 제가 관리합니다.
