# 体育赔率 API（BetRivers、Unibet 等 Kambi 体育博彩公司）— MCP 服务器

**体育赔率 API / 实时赔率数据 / 赔率比较**：一次调用即可拿到多家 Kambi 体系博彩公司（BetRivers、Unibet、Paf、Svenska Spel、ATG 等）的实时盘口。每场比赛一行，包含每家公司的赔率，以及每个投注选项的最高赔率，适合做赔率对比、价值投注筛选、量化模型和数据看板。

通过 Apify 托管的 MCP 服务器接入 Claude、Cursor、VS Code 等 AI 客户端，无需自己部署爬虫。

## 典型用途

- 多家博彩公司赔率横向对比（找最优赔率）
- 足球、篮球、网球、冰球等赛事实时盘口监控
- 为量化/预测模型提供结构化赔率数据
- 在 AI 助手里直接用中文提问：「今晚英超哪场比赛的主胜赔率最高？」

## MCP 地址

```
https://mcp.apify.com?tools=publicrecords/sports-odds-api
```

Transport: Streamable HTTP (Apify: https://docs.apify.com/mcp)

## 鉴权

客户端提示时使用 Apify OAuth 登录；或在请求头中加入 `Authorization: Bearer <APIFY_TOKEN>`（填写你自己的 Apify API Token）。请勿把真实 Token 提交到代码仓库。运行费用计入你自己的 Apify 账户。

## 客户端配置

### Claude Code

```
claude mcp add --transport http sports-odds "https://mcp.apify.com?tools=publicrecords/sports-odds-api"
```

Claude Desktop / claude.ai：设置 → Connectors → 添加自定义连接器，粘贴上面的 MCP 地址。

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

如需使用 Token 而不是 OAuth，在 `"url"` 旁加入 `"headers": { "Authorization": "Bearer <APIFY_TOKEN>" }`。

## 链接

- Apify Store 页面: https://apify.com/publicrecords/sports-odds-api
- 英文完整说明: [README.md](README.md)

> 仅提供赔率数据，不提供任何投注服务。请遵守你所在地区的法律法规。

---

说明：本 Actor 由我维护。
