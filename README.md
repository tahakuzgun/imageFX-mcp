# imageFX-mcp
Cursor MCP kullanımı için düzenlenmiş Google Labs ImageFX API

## Yetkilendirme Belgesi Nasıl Alınır?

1. [ImageFX](https://labs.google/fx/tools/image-fx) sayfasını ziyaret edin
2. Geliştirici araçlarını açın ve aşağıdaki kodu yapıştırarak token'ınızı çıkarın

```javascript
let script = document.querySelector("#__NEXT_DATA__");
let obj = JSON.parse(script.textContent);
let authToken = obj['props']['pageProps']['session']['access_token'];

window.prompt("Yetkilendirme belgesini kopyalayın: ", authToken);
```

Belirtilen token'ı kopyalayıp `.auth` dosyasına kaydedin. Ardından aşağıdaki komutu çalıştırabilirsiniz:

```bash
bun run generate --prompt "mor kedi" --authf "[.auth_dosyasinin_yolu]"
```

`NOT`: Yetkilendirme belgeleri yaklaşık 3 gün sonra sona erer.

## Cursor MCP Olarak Kullanım

Bu proje, Cursor IDE'de Managed Code Project (MCP) olarak kullanılabilir. Cursor, projenizi açtığınızda MCP özelliklerini otomatik olarak tanıyacaktır.

## Kullanım

```bash
bun run generate [-h] [--auth AUTH] [--seed SEED] [--count COUNT] [--prompt PROMPT] [--authf AUTHF] [--dir DIR]

Terminalinizden doğrudan ImageFX görüntüleri oluşturun

Opsiyonel argümanlar:
  -h, --help       yardım mesajını göster ve çık
  --auth AUTH      Görüntü oluşturma için yetkilendirme belirteci
  --seed SEED      Referans görüntü için seed değeri (Varsayılan: null)
  --count COUNT    Oluşturulacak görüntü sayısı (Varsayılan: 4)
  --prompt PROMPT  Görüntü oluşturma için komut
  --authf AUTHF    Düz metin '.auth' dosyasından yetkilendirme belirtecini oku
  --dir DIR        Oluşturulan görüntülerin kaydedileceği konum (Varsayılan: .)
```