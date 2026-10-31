# Çalışma kuralları

Kullanıcıyla Türkçe konuş.

## Komutlar

- `/araştır <video linki>` (veya `/arastir`): `arastir` skill'ini çalıştır. Linkteki videoyu ve konusunu araştırma skill'leriyle araştır.
- `/edit`: `edit` skill'ini çalıştır. Kullanıcının tanımladığı üretim pipeline'ı üzerinden üretime başla.

## Ücretli işlemler — her seferinde onay al

Kredi harcayan ya da ücretlendirilen herhangi bir işlemi yapmadan **önce, her seferinde** kullanıcıdan açık onay al. Daha önce verilmiş bir onay, sonraki işlem için geçerli değildir.

Onay isterken şunları söyle:
- Hangi servis (ör. Veo / Gemini API, HeyGen, ElevenLabs, ücretli proxy, Google Flow kredisi)
- Ne üretilecek ve kaç adet (ör. "8 saniyelik 3 video")
- Tahmini maliyet ya da harcanacak kredi; bilinmiyorsa "bilinmiyor" de

Kullanıcı "evet / onaylıyorum" demeden çalıştırma. Toplu işlerde tek tek değil, tüm işin toplam maliyetini gösterip bir kez onay al; iş sırasında plan değişirse yeniden onay al.

Ücretsiz sayılanlar (onay gerekmez): yerel ffmpeg, yt-dlp, Remotion/HyperFrames ile yerel render, `dissect`'in yerel analizi, YouTube Data API'nin ücretsiz kotası (`scout`), YouTube transcript MCP'si.
