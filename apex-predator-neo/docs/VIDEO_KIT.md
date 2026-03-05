# VIDEO PRODUCTION KIT — APEX PREDATOR NEO × Binance OpenClaw

---

## 60-SECOND SCREEN RECORDING SCRIPT

### Setup
- Open the live demo (GitHub Pages or the .jsx artifact)
- Full screen, dark room, no other tabs visible
- Screen record at 1080p minimum

### Shot List (60 seconds total)

**0-5s: HOOK**
Show the dashboard loading with live prices streaming in.
Text overlay: "I built an autonomous HFT AI for Binance 🦈"

**5-15s: LIVE DATA**
Scroll slowly through the ticker strip showing REAL prices.
Zoom into BTC orderbook updating in real-time.
Text: "Real Binance WebSocket data. Not simulated."

**15-25s: TRIANGLE SCANNER**
Show the triangle table with spreads updating every 2 seconds.
Highlight a positive spread briefly.
Text: "Scanning 40+ triangle paths every 2 seconds"

**25-35s: AI CHAT**
Type "status" → show the AI responding with live data.
Type "confluence" → show the 7-module breakdown.
Text: "AI assistant with full system awareness"

**35-50s: MODULES**
Slow scroll through the 8 AI nodes + ConfluenceEngine + APM cards.
Pause on SpoofHunter to show spoof count incrementing.
Text: "8 distributed AI nodes · 7 confluence filters · 4 APM weapons"

**50-60s: CLOSE**
Scroll to the tech stack chips.
Final text overlay:
"APEX PREDATOR NEO v666.1
OpenClaw Skill for Binance
All 7 Binance AI Agent Skills integrated
github.com/leoklein/apex-predator-neo
#BinanceOpenClaw #CryptoAI"

### Audio
- No voiceover needed (captions carry the story)
- Optional: dark ambient/electronic background music (royalty-free)

---

## THUMBNAIL SPECS (1200x675px for X, 1080x1080 for Square)

### Design Brief
- Background: pure black (#05060a) with subtle gold grid lines
- Center: 🦈 emoji or shark silhouette in gold (#f0b429)
- Top text: "APEX PREDATOR NEO" (Outfit 900, gold gradient)
- Middle: "8 AI Nodes × Binance" (white, large)
- Bottom: "#BinanceOpenClaw" (mono, cyan)
- Bottom-right: Binance logo mark (yellow diamond)
- Visual: screenshot of the live dashboard embedded at 40% opacity as background texture

### Create in Canva
1. New design → Custom 1200x675
2. Background: #05060a
3. Add rectangle → #f0b42910 → full bleed (grid texture feel)
4. Text block center:
   - "🦈 APEX PREDATOR NEO" → Outfit Black → gold
   - "8 AI Nodes × 7 Binance Skills" → white → 36pt
   - "OpenClaw Skill · Live Demo" → mono → cyan → 18pt
5. Bottom bar: "#BinanceOpenClaw #CryptoAI" → 14pt → dimmed
6. Export PNG

---

## CLAWHUB PUBLISH STEPS

### 1. Prepare files
Your SKILL.md is ready. Create a `_meta.json`:

```json
{
  "name": "apex-predator-neo",
  "version": "666.1.0",
  "description": "Autonomous triangular arbitrage AI for Binance with 8 distributed nodes, 7-module ConfluenceEngine, and all 7 Binance AI Agent Skills",
  "author": "leoklein",
  "tags": ["binance", "trading", "hft", "arbitrage", "ai-agent", "defi"],
  "requires": {
    "bins": ["curl", "jq", "python3", "docker", "redis-cli"],
    "env": ["BINANCE_API_KEY", "BINANCE_SECRET"]
  }
}
```

### 2. Submit to ClawHub

```bash
# Option A: Via OpenClaw CLI
clawhub publish ./apex-predator-neo

# Option B: Via GitHub (paste URL in OpenClaw chat)
# Push your repo, then paste:
# https://github.com/leoklein/apex-predator-neo

# Option C: Submit PR to openclaw/skills
# Fork https://github.com/openclaw/skills
# Add your skill under skills/leoklein/apex-predator-neo/
# PR with SKILL.md + _meta.json
```

### 3. Verify
```bash
openclaw add @leoklein/apex-predator-neo
# Test in testnet mode
```

---

## SUBMISSION CHECKLIST

- [ ] GitHub repo live: github.com/leoklein/apex-predator-neo
- [ ] Live demo deployed (GitHub Pages or Vercel)
- [ ] SKILL.md in repo root
- [ ] _meta.json in repo root
- [ ] Video recorded (60s screen capture)
- [ ] Thumbnail created (Canva)
- [ ] X post: quote repost official announcement + video
- [ ] Binance Square post: full writeup + video/images
- [ ] Fill out Binance submission form
- [ ] Optional: publish to ClawHub
