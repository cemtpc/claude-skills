# claude-skills

Claude Code skill'leri. `.claude/skills/` altındadır; bu depoyla açılan her Claude Code oturumunda otomatik yüklenir.

## Skill'ler

| Paket | Kaynak | Skill'ler |
|---|---|---|
| Remotion | https://github.com/remotion-dev/skills | `remotion-*` (12 skill) |
| HyperFrames | https://github.com/heygen-com/hyperframes | `hyperframes`, `hyperframes-cli`, `hyperframes-registry`, `media-use`, `figma`, `slideshow`, `remotion-to-hyperframes`, `reverse-any-video` |
| FFmpeg | https://github.com/kajisho5/ffmpeg-skill | `ffmpeg-skill` |
| Video Edit (Instagram Reels) | https://github.com/tenfoldmarc/video-edit-skill | `video-edit` |
| Vertical Video Editing (9:16 shorts) | https://github.com/nopefallacy/vertical-video-editing-skills | `video-editing` |
| Story Skills (hikaye/roman yazımı) | https://github.com/danjdewhurst/story-skills | `story-init`, `premise-workshop`, `plot-structure`, `chapter-writing`, `character-management`, `worldbuilding` ve diğerleri (24 skill) |
| Drama Skills (dikey kısa dizi) | https://github.com/zenstory-ai/drama-skills | `short-drama` (ana skill) ve `short-drama-*` (10 skill) |
| Dissect (videoyu analiz edip şablon çıkarma) | https://github.com/0xpratzyy/dissect | `dissect` |

### OpenMontage

OpenMontage (https://github.com/calesthio/OpenMontage, AGPLv3) bağımsız bir proje olduğu için buraya kopyalanmadı. Kullanmak için:

```bash
git clone https://github.com/calesthio/OpenMontage.git
cd OpenMontage && make setup
```

Sonra Claude Code'u o klasörde açın.

## Gereksinimler

- ffmpeg 6.1+ (`brew install ffmpeg`)
- Node.js 20+ (`brew install node`) — Remotion ve HyperFrames
- Python 3.11+ (`brew install python@3.12`)
- yt-dlp — video indirme (`brew install yt-dlp`)

Not: Remotion ticari kullanımda şirketler için lisans gerektirebilir. Her paketin lisansı kendi kaynak deposundadır (`licenses/` klasörüne bakın).
