---
name: smart-money-tracker
description: "OKX Smart Money analytics: leaderboard traders, position tracking, long/short ratio trends, capital flow analysis, conviction scores, and aggregate consensus signals. Use this skill when the user asks about: 聪明钱, smart money, top traders, 牛人榜, trader ranking, long/short ratio, 多空比, capital flow, 资金流向, position conviction, 仓位强度, entry price distribution, smart money overview, 聪明钱总览, signal history, 信号历史, trader search, 搜索交易员, who is trading BTC, 谁在交易BTC, recommend traders, 推荐交易员, best traders, top performers, whale tracking, 大户追踪, market sentiment from smart money, 聪明钱情绪. Requires OKX API Key (read-only). Do NOT use for placing orders, account management, or portfolio tracking."
license: MIT
metadata:
  author: "QTS Quant Lab"
  version: "1.0.0"
  homepage: "https://github.com/qts-lab/smart-money-tracker"
  agent:
    emoji: "🧠"
    requires:
      bins: ["okx"]
    install:
      - id: npm
        kind: node
        package: "@okx_ai/okx-trade-cli@1.3.9"
        bins: ["okx"]
        label: "Install OKX CLI (npm)"
  pricing:
    model: "paid"
    price: "$4.99/month"
    tier: "pro"
---

# Smart Money Tracker 🧠

> **Compliance notice**: This skill provides smart money analytics and market sentiment data only. All data is sourced from OKX's public smart money API. No investment advice is given. Trading decisions remain solely with the user.

Track what the smartest traders on OKX are doing — in real-time. Aggregates the top 100 qualified traders' positions, long/short ratios, capital flows, and conviction levels into actionable signals.

## Quick Start

```bash
# Smart Money overview — all assets
okx smartmoney signal-overview-by-filter --json

# Deep dive on one asset
okx smartmoney signal-overview-by-filter --instCcyList BTC,ETH,SOL --json

# Search for specific traders
okx smartmoney search-trader --keyword <name>

# Track trader performance over time
okx smartmoney signal-trend-by-trader --traderId <id> --period 30
```

## What It Tracks

| Metric | Description | Signal |
|--------|-------------|--------|
| **Long/Short Ratio** | % of top traders going long | >60% bullish, <40% bearish |
| **Ratio Change (1h/24h/7d)** | How fast sentiment is shifting | Rapid shift = 🚨 alert |
| **Net Notional (USDT)** | Total capital deployed by smart money | Large net flow = conviction |
| **Weighted Ratio** | Position-size-weighted long % | More accurate than simple ratio |
| **Win Rate** | Average winning % among traders | High win rate = reliable signal |
| **Trader Count** | How many qualified traders are active | More = more reliable |

## Signal Layers

### Layer 1: Aggregate Consensus

The `signal-overview-by-filter` returns per-asset aggregated data:

```
BTC: 69% long (24h: +19.9%) | 35 traders | Net: -16.6M USDT
→ Bullish consensus, rapidly shifting up (24h +19.9%)
→ But: whales are net SHORT (weighted ratio 22.6%)
→ Interpretation: Many small long, few large short = cautious
```

### Layer 2: Trend Analysis

The `signal-trend-by-filter` tracks how consensus evolves:
- Daily snapshots over 7/30/90 days
- Detect trend reversals early
- Compare current vs historical extremes

### Layer 3: Individual Trader Tracking

Follow specific high-performing traders:
- Track their positions in real-time
- See their closed PnL history
- Set alerts when they open/close positions

## Integration with V5 Signal Scanner

When combined with `v5-signal-scanner`, Smart Money data adds a 6th "sentiment factor":

```
Technical Score: +0.28 (MEDIUM LONG)
Smart Money:     69% long, rapidly rising (+19.9% 24h)
→ Combined Signal: STRONG LONG 🔥
```

## Pricing

**$4.99/month** — includes:
- Full smart money dashboard
- Multi-asset tracking
- Trend analysis (7/30/90 day)
- Individual trader search
- Webhook alerts for signal changes

Free tier available via `v5-signal-scanner` (basic overview only).

---

## Commands Reference

### Signal Overview

```bash
okx smartmoney signal-overview-by-filter [--json]
```

### Signal Trend

```bash
okx smartmoney signal-trend-by-filter --period 7 [--json]
```

### Trader Search

```bash
okx smartmoney search-trader --keyword <name> [--json]
```

### Trader Positions

```bash
okx smartmoney trader-positions --traderId <id> [--json]
```

---

## Edge Cases

- Smart Money data updates every 2 hours (OKX batch processing)
- Minimum 100 qualified traders required for reliable signals
- Weighted ratio > simple ratio for large-cap assets (BTC/ETH)
- Trader performance data is 24h delayed
- Requires OKX API Key with read permissions

---

## License

MIT © 2026 QTS Quant Lab
