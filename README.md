# claude-skills

Claude Code skill'leri. `.claude/skills/` altındadır; bu depoyla açılan her Claude Code oturumunda otomatik yüklenir.

## Skill'ler

| Paket | Kaynak | Skill'ler |
|---|---|---|
| Remotion | https://github.com/remotion-dev/skills | `remotion-*` (12 skill) |
| HyperFrames | https://github.com/heygen-com/hyperframes | `hyperframes`, `hyperframes-cli`, `hyperframes-registry`, `media-use`, `figma`, `slideshow`, `remotion-to-hyperframes`, `reverse-any-video` |
| FFmpeg | https://github.com/kajisho5/ffmpeg-skill | `ffmpeg-skill` |

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

Not: Remotion ticari kullanımda şirketler için lisans gerektirebilir. Her paketin lisansı kendi kaynak deposundadır (`licenses/` klasörüne bakın).
