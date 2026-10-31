---
name: arastir
description: Kullanıcı "/araştır" veya "/arastir" yazıp bir video linki (YouTube, Shorts, TikTok, Instagram Reels vb.) verdiğinde çalışır. Videoyu ve konusunu araştırma skill'leriyle inceler ve Türkçe bir araştırma raporu çıkarır.
argument-hint: "<video linki> [ek not]"
---

# /araştır

Girdi: bir video linki, isteğe bağlı olarak kullanıcının notu. Link yoksa iste.

Bu iş ücretsizdir; ücretli bir servise ihtiyaç doğarsa CLAUDE.md'deki onay kuralını uygula.

## Adımlar

1. **Video bilgisi** — `yt-dlp --dump-json --skip-download <link>` ile başlık, kanal, süre, izlenme, beğeni, yorum sayısı, yayın tarihi. yt-dlp yoksa `pip install -U yt-dlp`.
2. **Metin** — `youtube-transcript` MCP'si ile konuşma metnini al (YouTube dışı linklerde veya MCP başarısızsa `dissect`'in transkripsiyonunu kullan).
3. **Format analizi** — `dissect` skill'i ile videoyu çöz: hook, kesmeler, geçişler, tempo, yazı/altyazı stili, ses, yapı. Blueprint'i proje klasörüne kaydet.
4. **Konu araştırması** — Videonun ana konusunu 2-5 kelimeye indir ve `scout` skill'i ile o konudaki en iyi videoları bul (`--hooks` ile). `YOUTUBE_API_KEY` yoksa bu adımı atla ve raporda belirt.
5. **Rapor** — `research/<tarih>-<kısa-konu>/` altına yaz.

## Rapor (Türkçe, `rapor.md`)

- **Özet** — video ne anlatıyor, 3-5 madde
- **Neden çalışıyor** — hook, yapı, tempo, görsel stil; dissect'ten sayılarla
- **Rakamlar** — izlenme, etkileşim oranı, konudaki diğer videolarla kıyas
- **Konudaki en iyi videolar** — scout'tan ilk 10, başlık + kanal + izlenme + hook
- **Tekrarlanan kalıplar** — öne çıkan videolarda ortak hook ve formatlar
- **Bizim için fikirler** — bu formatta yapılabilecek 3-5 video fikri, her biri için hook önerisi
- **Dosyalar** — blueprint, Excel, transcript yolları

Bir adım başarısız olursa (ör. YouTube engeli) bunu raporda açıkça yaz; eksik veriyi uydurma.
