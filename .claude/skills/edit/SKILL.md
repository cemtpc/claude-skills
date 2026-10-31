---
name: edit
description: Kullanıcı "/edit" yazdığında çalışır. Kullanıcının tanımladığı üretim pipeline'ı üzerinden video üretimine başlar.
argument-hint: "[proje veya girdi dosyaları]"
---

# /edit

## Pipeline

**Henüz tanımlanmadı.** Kullanıcı tüm süreci daha sonra aktaracak.

Pipeline tanımlanana kadar `/edit` çağrıldığında:
1. Kullanıcıya pipeline'ın henüz tanımlanmadığını söyle.
2. Süreci adım adım anlatmasını iste (girdi ne, hangi aşamalar, hangi araçlar, çıktı formatı).
3. Anlattığı süreci bu dosyanın "Pipeline" bölümüne yaz, depoya kaydet, sonra üretime başla.

## Kurallar

- Ücretli her işlemden önce CLAUDE.md'deki onay kuralını uygula (servis, adet, tahmini maliyet → onay).
- Kullanılabilecek skill'ler: `video-edit`, `video-editing`, `ffmpeg-skill`, `hyperframes*`, `remotion-*`, `short-drama*`, `dissect`.
