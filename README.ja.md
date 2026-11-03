# スポーツオッズ API（BetRivers・Unibet ほか Kambi 系ブックメーカー）— MCP サーバー

**スポーツオッズ API / リアルタイムオッズ / オッズ比較**。Kambi 系ブックメーカー（BetRivers、Unibet、Paf、Svenska Spel、ATG など）の最新オッズを 1 回の呼び出しでまとめて取得できます。1 試合 1 行で、各ブックメーカーのオッズと、選択肢ごとの最高オッズを返します。オッズ比較、バリューベット探し、予測モデル、ダッシュボード作りに向いています。

Apify がホストする MCP サーバー経由で Claude・Cursor・VS Code などの AI クライアントから直接使えます。スクレイパーを自分で運用する必要はありません。

## 主な使い方

- 複数ブックメーカーのオッズを横並びで比較し、最高オッズを見つける
- サッカー・バスケットボール・テニス・アイスホッケーなどの試合オッズを監視
- 予測モデルや分析用に構造化されたオッズデータを取得
- AI アシスタントに日本語で質問：「今夜のプレミアリーグでホーム勝利のオッズが一番高い試合は？」

## MCP エンドポイント

```
https://mcp.apify.com?tools=publicrecords/sports-odds-api
```

Transport: Streamable HTTP (Apify: https://docs.apify.com/mcp)

## 認証

クライアントに表示される Apify OAuth でサインインするか、ヘッダー `Authorization: Bearer <APIFY_TOKEN>`（ご自身の Apify API トークン）を送ってください。実際のトークンはリポジトリにコミットしないでください。実行料金はご自身の Apify アカウントに計上されます。

## クライアント設定

### Claude Code

```
claude mcp add --transport http sports-odds "https://mcp.apify.com?tools=publicrecords/sports-odds-api"
```

Claude Desktop / claude.ai：設定 → Connectors → カスタムコネクタを追加し、上の MCP エンドポイントを貼り付けます。

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

OAuth の代わりにトークンを使う場合は、`"url"` の横に `"headers": { "Authorization": "Bearer <APIFY_TOKEN>" }` を追加します。

## リンク

- Apify Store ページ: https://apify.com/publicrecords/sports-odds-api
- 英語版の詳しい説明: [README.md](README.md)
- 関連: [Awesome Sports Odds MCP](https://github.com/GeminiGeorge22/awesome-sports-odds-mcp) (厳選リスト)

> 提供するのはオッズデータのみで、賭けのサービスは提供しません。お住まいの地域の法令に従ってご利用ください。

---

開示：この Actor は私がメンテナンスしています。
