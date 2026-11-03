# Spor bahis oranları API'si (BetRivers, Unibet ve diğer Kambi bahis şirketleri) — MCP sunucusu

**Spor bahis oranları API'si, canlı oranlar ve oran karşılaştırma** tek çağrıda: Kambi altyapısını kullanan bahis şirketlerinin (BetRivers, Unibet, Paf, Svenska Spel, ATG ve diğerleri) güncel oranları. Her maç için tek satır: her şirketin oranı ve her sonuç için en yüksek oran. Oran karşılaştırma, value bet arama, tahmin modelleri ve panolar için uygundur.

Apify'ın barındırdığı MCP sunucusu üzerinden Claude, Cursor, VS Code ve diğer yapay zekâ istemcilerinde çalışır. Kendi kazıyıcınızı yönetmeniz gerekmez.

## Kullanım alanları

- Birden çok bahis şirketinin oranlarını karşılaştırıp en iyisini bulma
- Futbol, basketbol, tenis ve buz hokeyi oranlarını takip etme
- Modeller ve analiz için yapılandırılmış oran verisi alma
- Asistana Türkçe sorun: "Bu akşam Premier Lig'de ev sahibi galibiyetine en yüksek oranı veren maç hangisi?"

## MCP uç noktası

```
https://mcp.apify.com?tools=publicrecords/sports-odds-api
```

Transport: Streamable HTTP (Apify: https://docs.apify.com/mcp)

## Kimlik doğrulama

İstemciniz sorduğunda Apify OAuth ile giriş yapın veya kendi Apify API anahtarınızla `Authorization: Bearer <APIFY_TOKEN>` başlığını gönderin. Gerçek bir anahtarı asla depoya göndermeyin. Çalıştırmalar kendi Apify hesabınıza faturalanır.

## İstemci kurulumu

### Claude Code

```
claude mcp add --transport http sports-odds "https://mcp.apify.com?tools=publicrecords/sports-odds-api"
```

Claude Desktop / claude.ai: Ayarlar → Connectors → Özel bağlayıcı ekle ve yukarıdaki MCP uç noktasını yapıştırın.

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

OAuth yerine anahtar kullanmak için `"url"` yanına `"headers": { "Authorization": "Bearer <APIFY_TOKEN>" }` ekleyin.

## Bağlantılar

- Apify Store sayfası: https://apify.com/publicrecords/sports-odds-api
- İngilizce tam belge: [README.md](README.md)
- Ayrıca bakın: [Awesome Sports Odds MCP](https://github.com/GeminiGeorge22/awesome-sports-odds-mcp) (seçkin liste)

> Yalnızca oran verisi sunar; bahis hizmeti sunmaz. Lütfen ülkenizin yasalarına uyun.

---

Açıklama: Bu Actor'ı ben geliştiriyor ve bakımını yapıyorum.
