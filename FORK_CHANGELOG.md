# Augurium.ai OpenClaw Fork — Changelog

> Fork of [openclaw/openclaw](https://github.com/openclaw/openclaw) (MIT License)
> Maintained by [Agenticware LLC](https://github.com/Agenticware)

## 2026-02-10 — Initial Fork Setup

**Base version:** openclaw v2026.2.9

### Added
- `openclaw.json` — 3-agent config (Luna/Atlas/Nova) with OpenRouter MiMo V2 Flash
- `workspace/SOUL.md` — Cosmic Sophistication shared persona
- `workspace/TOOLS.md` — Environment-specific tool notes
- `workspace/luna/IDENTITY.md` — Luna agent (Fantasy 5, purple, intuitive)
- `workspace/atlas/IDENTITY.md` — Atlas agent (PowerBall, red, strategic)
- `workspace/nova/IDENTITY.md` — Nova agent (Mega Millions, blue, analytical)
- `skills/predict-numbers/SKILL.md` — Prediction generation skill
- `skills/draw-history/SKILL.md` — Historical draw retrieval skill
- `skills/theory-breakdown/SKILL.md` — Pillar analysis skill
- `skills/astrology-aspects/SKILL.md` — Astrological aspects skill
- `skills/prediction-accuracy/SKILL.md` — Accuracy metrics skill
- `skills/knowledge-graph/SKILL.md` — Neo4j graph exploration skill
- `FORK_CHANGELOG.md` — This file

### Modified
- `package.json` — Rebranded to `augurium-openclaw`, added Agenticware metadata
- `.env.example` — Added `FASTAPI_URL`, `INTERNAL_API_KEY` vars
- `Dockerfile` — Copies workspace/config into image, binds to LAN by default

## 2026-02-10 — Deployment Fixes

### Fixed
- Removed `tools` from `agents.defaults` (not valid in OpenClaw schema; use root-level `tools` instead)
- Changed `session.maxIdleMinutes` → `session.idleMinutes` (correct schema field name)
- Increased container memory limit from 1GB to 2GB (gateway OOMs during startup at 1GB)
- Added `NODE_OPTIONS=--max-old-space-size=1536` to container env
- Increased `start_period` from 30s to 60s for health check

### Disabled via config (not deleted)
- Voice/audio streaming
- Canvas/whiteboard
- Browser automation
- File manager
- Telegram, Discord, WhatsApp channels (enable post-MVP)
