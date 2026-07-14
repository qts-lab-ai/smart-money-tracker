# Smart Money Tracker 🧠

**Track what OKX's smartest traders are doing — in real time.**

[![Version](https://img.shields.io/badge/version-1.0.0-blue)](https://github.com/qts-lab-ai/smart-money-tracker)
[![License](https://img.shields.io/badge/license-MIT-green)](LICENSE)
[![OKX Marketplace](https://img.shields.io/badge/OKX-Marketplace-orange)](https://www.okx.com/agent-tradekit/skills)

> **Aggregate long/short ratios, position conviction, and capital flows from OKX's top 100 traders. Turn whale movement into your edge.**

---

## 🚀 Install

```bash
# OKX AI Agent
npx skills add qts-lab-ai/smart-money-tracker

# Requires OKX CLI
npm install -g @okx_ai/okx-trade-cli
```

---

## 📊 What It Tracks

| Metric | Description |
|--------|-------------|
| Long/Short Ratio | Top traders' aggregate position direction |
| Conviction Score | How strongly traders believe (position size + leverage) |
| Capital Flow | Net USD inflow/outflow per symbol |
| Whale Alerts | Unusually large position changes (top 5%) |
| Sentiment Shift | Direction change in the last 1h/4h/24h |

---

## 📟 Example

```
🧠 Smart Money — 07/14 13:00
━━━━━━━━━━━━━━━━━━━━━━
BTC  🟢 69% long ↑1h  (42 traders)
ETH  🟢 63% long ↑1h  (38 traders)
SOL  🟡 52% long →1h  (29 traders)
DOGE 🔴 67% short ↓1h (22 traders)
XRP  🟢 71% long ↑4h  (31 traders)
```

---

## 💰 Pricing

| Plan | Price | Features |
|------|-------|----------|
| **Pro** | $4.99/mo | All symbols, 1h/4h/24h history, whale alerts |

---

## 📄 License

MIT © 2026 QTS Quant Lab
