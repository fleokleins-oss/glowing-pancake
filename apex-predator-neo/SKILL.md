---
name: apex-predator-neo
description: >
  Autonomous HFT AI for Binance — 8 lethal modules: Confluence God Mode (8 filters + ML sweep prediction),
  Predator Shadow (ghost counter-attack), Anti-Rug v3 (XGBoost honeypot killer), Newtonian Regime
  (market physics), EconoPredator (funding + OI + ATR), Narrative Divergence (sentiment + Hyblock),
  Robin Hood Risk Engine (4% drawdown = kill switch), Auto-Earn Hook (profits → Simple Earn).
  Integrates all 7 official Binance AI Agent Skills. Built for the Binance OpenClaw Challenge.
metadata:
  clawdbot:
    emoji: "🦈"
    always: false
    requires:
      bins: [curl, jq, python3, docker, redis-cli]
      env: [BINANCE_API_KEY, BINANCE_SECRET]
---

# 🦈 APEX PREDATOR NEO v666.1

> "Imprimir dinheiro enquanto você dorme. Proteger capital como um fundo institucional. Contra-atacar HFTs rivais com ordens fantasma."

## The 8 Lethal Modules

### 1. 🧬 Confluence God Mode — 8 Filters + ML Sweep Prediction
Not 6 filters. Not 7. **Eight lethal gates** that every signal must pass, plus an ML sweep prediction layer trained via Ray Cluster:

```python
WEIGHTS = {
    "tire_pressure":     0.16,  # Bid/ask directional force (top-5 levels)
    "lead_lag":          0.12,  # Temporal sync between triangle legs
    "fake_momentum":     0.14,  # Wash trading / artificial volume detection
    "oi_consistency":    0.10,  # Sustained OI spike vs noise
    "oi_delta_vol":      0.10,  # Buy/sell equilibrium ratio
    "reversal_risk":     0.14,  # Price position in 24h range
    "book_entropy":      0.12,  # Shannon H anti-spoof (normalized 0-1)
    "ml_sweep_pred":     0.12,  # XGBoost sweep prediction (Ray-trained)
}
```

Validation (ALL must pass):
```python
is_valid = (
    score >= MIN_CONFLUENCE_SCORE     # Weighted score ≥ 65
    and not fake_momentum_flag        # No artificial momentum
    and reversal_risk < 0.70          # Not in reversal zone
    and book_entropy > 0.20           # Not spoofed (Shannon H)
    and ml_sweep_confidence > 0.55    # ML model agrees
)
```

### 2. 👻 Predator Shadow — Ghost Counter-Attack
**You don't just defend against spoofing. You counter-attack.**

When SpoofHunter detects ghost walls from rival HFTs, Predator Shadow:
- Maps the phantom order pattern (direction, size, timing)
- Calculates the contrarian signal (fake bids = SHORT, fake asks = LONG)
- Places shadow orders that exploit the gap left when ghost walls vanish
- Extracts alpha from the same manipulation that was meant to trap retail

This is the module that makes APEX a **predator**, not prey.

### 3. 🛡️ Anti-Rug v3 — XGBoost Honeypot Killer
Token contract audit powered by Binance Token Contract Audit Skill + custom XGBoost classifier:
- Analyzes contract bytecode for honeypot patterns
- Checks liquidity lock status and owner permissions
- Scores token safety 0-100 before adding to triangle scan paths
- **Blocks any pair with rug score > 60** from ever entering the scanner
- Trained on 50K+ known rug pulls via Ray Cluster

### 4. ⚛️ Newtonian Regime — Market Physics
Applies Newtonian mechanics to price action:
- **Force** = volume × price acceleration (F = ma for markets)
- **Momentum** = mass (liquidity depth) × velocity (price rate of change)
- **Friction** = spread + fees (the force that kills small edges)
- **Regime detection**: trending / sideways / breakout / reduced-size
- Auto-adjusts scanner parameters per regime (wider thresholds in volatile, tighter in ranging)

### 5. 📊 EconoPredator — Funding + OI + ATR
FastAPI microservice with 6 real-time pollers:

| Poller | Source | Data |
|--------|--------|------|
| `poll_funding` | Binance FAPI `/fapi/v1/premiumIndex` | mark_price, funding_rate, next_funding_time |
| `poll_oi` | Binance FAPI `/fapi/v1/openInterest` | open_interest × mark_price |
| `poll_ls_ratio` | Binance L/S ratio API | Account-level long/short balance |
| `poll_atr` | Kline-derived | Average True Range (volatility gauge) |
| `poll_macro` | Yahoo Finance, Alternative.me | DXY, VIX, Fear & Greed, CPI/FOMC calendar |
| `poll_onchain` | Glassnode, Whale Alert | exchange_netflow, whale_tx (via Binance Address Insight Skill) |

### 6. 📰 Narrative Divergence — Sentiment + Hyblock
Detects when market narrative diverges from price action:
- Hyblock liquidation heatmap integration (long/short squeeze detection)
- CryptoPanic news sentiment (50 req/h free tier)
- Reddit r/CryptoCurrency keyword analysis
- Fear & Greed index correlation
- **Divergence signal**: when sentiment says UP but OI/funding says DOWN → high-confidence contrarian edge

### 7. 🛡️ Robin Hood Risk Engine — 4% Drawdown = Kill Switch
```
Max drawdown:     4.0%  → 30-minute TOTAL freeze (all modules)
Capital:          $22.00
Max per cycle:    $8.00 (or 12% of equity, whichever is lower)
Equity < 50%:    → PERMANENT SHUTDOWN
Drawdown > 2%:   → proportional size reduction
Profit > $0.05:  → Auto-Earn sweep triggered
Override:         IMPOSSIBLE — survival logic is non-negotiable
```

Publishes alerts via Redis to synchronize ALL services instantly.

### 8. 💰 Auto-Earn Hook — Profits → Simple Earn
```python
# Every profitable cycle:
if net_profit >= 0.05:  # $0.05 threshold (not $0.10)
    best_product = query_simple_earn(asset, sort_by="APR")  # 5min cache
    subscribe(product_id, amount=net_profit)
    publish_to_redis("apex:v666:earn", confirmation)
```
Idle capital generates passive yield 24/7 between trades.

---

## Binance AI Agent Skills Integration

| # | Binance Skill | APEX Module |
|---|--------------|-------------|
| 1 | **CEX Spot Trading** | BinanceConnector — tickers, depth@100ms, bookTicker, execution (market/limit/IOC) |
| 2 | **Address Insight** | EconoPredator `poll_onchain` — whale wallet analysis, exchange netflow |
| 3 | **Token Details** | Scanner `discover()` — validate liquidity + active status |
| 4 | **Market Rankings** | Scanner — auto-select top pairs by 24h volume |
| 5 | **Meme Rush** | EconoPredator + Narrative Divergence — surge dislocation detection |
| 6 | **Trading Signals** | Confluence God Mode — cross-reference for ML sweep confidence |
| 7 | **Token Contract Audit** | Anti-Rug v3 — XGBoost honeypot scoring before pair inclusion |

---

## Tool Guidance

| Tool | Usage |
|------|-------|
| `ccxt.pro` | Ultra-fast order execution (limit + market + IOC) |
| `Redis Streams` | Zero-latency inter-module communication |
| `Ray Cluster` | ML training on desktop (doesn't steal scanner latency) |
| `n8n` | Visual dashboard + human automation (toggle gates on/off) |
| `httpx.AsyncClient` | Parallel calls to Anti-Rug, SpoofHunter, Newtonian |
| `loguru` | Structured, beautiful logs (optimized for contest video) |
| `Docker Compose` | 1-command deploy (redis + openclaw) |

---

## Hard Rules (Never Broken)

- `TESTNET = True` until thermal phase proves < 60ms total latency
- Capital per cycle: max $8.00 (or 12% of equity)
- Drawdown > 4% → Robin Hood activates (30-minute lock)
- **All profit > $0.05** → Auto-Earn to Simple Earn
- Always prioritize latency < 45ms scan cycle
- No override of risk limits. Ever. Period.

---

## Architecture

```
OpenClaw Agent (Your Machine)
  └── APEX PREDATOR NEO v666.1
       │
       ├── Confluence God Mode ──── 8 filters + ML sweep (Ray-trained)
       │    ├── Predator Shadow ──── Ghost counter-attack engine
       │    ├── Anti-Rug v3 ──────── XGBoost honeypot killer
       │    └── Book Entropy ─────── Shannon H anti-spoof
       │
       ├── Newtonian Regime ──────── F=ma market physics + regime detection
       ├── EconoPredator ─────────── 6 pollers (funding/OI/ATR/macro/onchain)
       ├── Narrative Divergence ──── Sentiment + Hyblock liquidation heatmap
       │
       ├── Scanner ───────────────── Triangle discovery (< 45ms cycle)
       │    └── LOB Service ──────── WebSocket @depth@100ms + @aggTrade
       │
       ├── Redis Streams ─────────── strike_zone_{symbol} + nanosecond ts
       │    ├── → Singapore Executor (AWS) → Binance API (< 10ms)
       │    └── → Tokyo Executor (AWS) ───→ Binance API (< 15ms)
       │
       └── Post-Trade
            ├── Robin Hood Risk ──── 4% DD = kill switch (30min)
            ├── Auto-Earn Hook ───── profit > $0.05 → Simple Earn
            └── Report ───────────── WhatsApp / Telegram / Slack via OpenClaw
```

---

## Environment Variables

| Variable | Description | Default |
|----------|-------------|---------|
| `BINANCE_API_KEY` | API Key (Spot enabled) | required |
| `BINANCE_SECRET` | API Secret | required |
| `APEX_MODE` | `testnet` or `live` | testnet |
| `CAPITAL_TOTAL` | Total USDT | 22.00 |
| `MAX_POR_CICLO` | Max per trade | 8.00 |
| `MAX_DRAWDOWN_PCT` | Kill switch threshold | 4.0 |
| `SCAN_INTERVAL_MS` | Scan cycle ms | 45 |
| `AUTO_EARN_MIN_PROFIT` | Earn sweep threshold | 0.05 |
| `MIN_CONFLUENCE_SCORE` | Min score 0-100 | 65 |

---

## Quick Start

```bash
clawhub install apex-predator-neo

export BINANCE_API_KEY="your_key"
export BINANCE_SECRET="your_secret"

docker compose up -d redis
docker compose up -d lob_service scanner
docker compose logs -f scanner
```

Then tell your OpenClaw: "Activate APEX PREDATOR NEO"

---

**Binance OpenClaw Challenge 2026** · #BinanceOpenClaw #CryptoAI
Built by @leoklein · Curitiba, BR 🇧🇷
