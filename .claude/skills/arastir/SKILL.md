---
name: arastir
description: Kullanıcı "/araştır" veya "/arastir" yazdığında çalışır. Dört mod vardır - video linki (yalnızca o video), "kanalı araştır" (yalnızca o kanal), "konuyu araştır" (o konudaki kanallar ve videolar), "script araştır" (senaryo, hikâyeleştirme ve dramatizasyon teknikleri). Türkçe rapor çıkarır.
argument-hint: "<video linki> | kanalı araştır <kanal> | konuyu araştır <konu> | script araştır <konu veya link>"
---

# /araştır

Önce kullanıcının isteğinden **modu** belirle, sonra yalnızca o modun adımlarını uygula. Mod belirsizse sor; tahmin etme.

| Kullanıcı ne yazdı | Mod |
|---|---|
| Sadece bir video linki (YouTube, Shorts, TikTok, Reels vb.) | **1. Video** |
| "kanalı araştır" + kanal linki / @kanal adı | **2. Kanal** |
| "konuyu araştır" + konu | **3. Konu** |
| "script araştır" + konu veya link | **4. Script** |

**Kapsam kuralı (en önemli):** Kullanıcının verdiği şeyin dışına çıkma.
- Video linkinde başka video veya kanal arama, `scout` çalıştırma, rakip listesi çıkarma.
- Kanal modunda başka kanal arama, benzer kanal önerme.
- Yalnızca Konu modunda farklı kanallar ve videolar aranır.

Hepsi ücretsizdir; ücretli bir servise ihtiyaç doğarsa CLAUDE.md'deki onay kuralını uygula. Bir adım başarısız olursa (ör. YouTube engeli) raporda açıkça yaz; eksik veriyi uydurma.

Çıktılar `research/<tarih>-<kısa-ad>/` altına, rapor `rapor.md` olarak (Türkçe).

---

## 1. Video — yalnızca o video

1. **Bilgi** — `yt-dlp --dump-json --skip-download <link>`: başlık, kanal, süre, izlenme, beğeni, yorum sayısı, yayın tarihi, açıklama.
2. **Metin** — `youtube-transcript` MCP'si; YouTube dışı linkte veya başarısızsa `dissect`'in transkripsiyonu.
3. **Format** — `dissect` ile videoyu çöz: hook, kesmeler, geçişler, tempo, kamera, yazı/altyazı stili, renk, ses ve müzik, yapı.

Rapor:
- **Özet** — video ne anlatıyor (3-5 madde)
- **Rakamlar** — izlenme, etkileşim oranı (beğeni+yorum / izlenme), yayından bu yana geçen süre
- **Hook** — ilk 3-5 saniye: ne söyleniyor, ne gösteriliyor, neden işe yarıyor
- **Yapı** — bölüm bölüm akış, zaman damgalarıyla
- **Kurgu ve görsel stil** — dissect'ten sayılarla (kesme sıklığı, ortalama plan süresi, yazı stili, renk)
- **Ses** — müzik, efektler, ses seviyesi, konuşma temposu
- **Neden çalışıyor** — en güçlü 3-5 unsur
- **Bu formatta video yapmak için** — uygulanabilir tarif (blueprint'e bağlı)
- **Dosyalar** — blueprint, transcript yolları

## 2. Kanal — yalnızca o kanal

1. **Kanal bilgisi** — YouTube Data API (`YOUTUBE_API_KEY`) `channels` uç noktası: abone, toplam izlenme, video sayısı, açılış tarihi. Anahtar yoksa `yt-dlp` ile alınabileni al.
2. **Videolar** — `yt-dlp --flat-playlist --dump-json <kanal>/videos` ve `<kanal>/shorts`; son ~50 video için izlenme, süre, tarih.
3. **En iyi videolar** — izlenmeye ve kanal ortalamasına göre öne çıkan (outlier) ilk 5-10 video; bunların metnini `youtube-transcript` ile al, hook'larını çıkar. İstenirse en iyi 1-2 videoya `dissect`.

Rapor:
- **Kanal özeti** — niş, hedef kitle, rakamlar
- **Yükleme düzeni** — sıklık, gün, uzun video / Shorts oranı
- **En iyi videolar** — başlık, izlenme, kanal ortalamasının kaç katı, hook
- **Tekrarlanan kalıplar** — başlık kalıpları, hook türleri, süre, format, küçük resim tarzı
- **Ne işe yaramıyor** — ortalamanın altında kalan videoların ortak noktaları
- **Çıkarımlar** — bu kanaldan alınabilecek 3-5 ders

## 3. Konu — o konudaki kanallar ve videolar

1. **Arama** — `scout` skill'i ile konuyu ara (`--hooks`, gerekirse `--sort breakout`). `YOUTUBE_API_KEY` yoksa söyle ve dur.
2. **Kanallar** — sonuçlardaki kanalları grupla: abone, konudaki video sayısı, ortalama izlenme.
3. **Öne çıkanlar** — en iyi 3-5 videonun metnini al, hook'larını karşılaştır.

Rapor:
- **Konunun durumu** — talep, rekabet, yükselen alt konular
- **Öne çıkan kanallar** — ilk 10, rakamlar ve her birinin farkı
- **En iyi videolar** — ilk 10, başlık + kanal + izlenme + hook
- **Ortak kalıplar** — hook, format, süre, başlık
- **Boşluklar ve fırsatlar** — az işlenmiş açılar, 3-5 video fikri
- **Dosyalar** — scout Excel'i

## 4. Script — senaryo ve hikâye anlatımı

Odak yalnızca **senaryo**: kurgu, görsel, ses analizi yapma.

- **Link verildiyse**: o videonun metni (`youtube-transcript`).
- **Konu verildiyse**: `scout` ile konudaki en iyi 5-10 videoyu bul, metinlerini al ve bunları incele.

Story-skills bilgisini kullan (`plot-structure`, `scene-craft`, `theme-craft`, `genre-craft`, `character-management`); kısa dikey drama için `short-drama-write` yaklaşımı.

Her script için:
- **Hook** — ilk cümle(ler) ve türü: soru, şok iddia, merak boşluğu, sonu başta gösterme, çatışma, vaat
- **Yapı** — kullanılan çerçeve (ör. problem-çözüm, üç perde, kahramanın yolculuğu, ters kronoloji, liste, öncesi-sonrası), zaman damgalarıyla
- **Hikâyeleştirme** — karakter, hedef, engel, risk (stake), dönüm noktası, çözüm
- **Dramatizasyon** — gerilim nasıl kuruluyor ve yükseltiliyor; ritim, sessizlik, ifşa (reveal) zamanlaması, duygu inişleri-çıkışları
- **Tutma teknikleri** — açık döngüler (open loop), ileriye işaret, "ama / bu yüzden" bağlaçları, tekrar eden motifler, cliffhanger
- **Dil** — cümle uzunluğu, hitap, konuşma tonu, kelime seçimi, dakikadaki kelime sayısı
- **Kapanış ve CTA** — nasıl bitiyor, izleyiciye ne yaptırıyor

Rapor:
- Her script için yukarıdaki döküm (alıntılarla)
- **Ortak teknikler** — videoların paylaştığı yöntemler
- **Script şablonu** — bu teknikleri kullanan, doldurulabilir bir taslak (bölüm bölüm, süreleriyle)
- **Örnek** — şablonla yazılmış kısa bir örnek giriş (hook + ilk 20 saniye)
