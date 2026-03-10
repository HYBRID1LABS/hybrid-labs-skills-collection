# Crypto Arbitrage Scanner

**Real-time cross-exchange arbitrage opportunity detection**

---

## 🎯 Overview

Scan multiple exchanges simultaneously to find price differences and triangular arbitrage opportunities. Real-time alerts with profit calculations including fees.

---

## ✨ Features

- **Multi-Exchange Scanning** - Binance, Coinbase, Kraken, KuCoin, etc.
- **Triangular Arbitrage** - Detect 3-leg arbitrage opportunities
- **Real-Time Alerts** - Instant notifications for profitable opportunities
- **Fee Calculation** - Net profit after all fees
- **Execution Speed** - <100ms detection to alert

---

## 📦 Installation

```bash
npm install @hybrid-labs/crypto-arbitrage-scanner
```

---

## 🚀 Quick Start

```javascript
const scanner = require('@hybrid-labs/crypto-arbitrage-scanner');

// Scan for opportunities
const opportunities = await scanner.scan({
  exchanges: ['Binance', 'Coinbase', 'Kraken'],
  minProfit: 0.5, // 0.5% minimum profit after fees
  pairs: ['BTC/USDT', 'ETH/USDT', 'SOL/USDT']
});

console.log(opportunities);
// [
//   {
//     buyExchange: 'Binance',
//     sellExchange: 'Coinbase',
//     pair: 'BTC/USDT',
//     profit: 1.2, // %
//     buyPrice: 45000,
//     sellPrice: 45540
//   }
// ]

// Find triangular arbitrage
const triangular = await scanner.findTriangular({
  base: 'USDT',
  path: ['BTC', 'ETH', 'USDT'],
  minProfit: 0.3
});
```

---

## 📊 Opportunity Types

1. **Spatial Arbitrage** - Buy on Exchange A, sell on Exchange B
2. **Triangular Arbitrage** - Trade 3 pairs in a loop (e.g., USDT→BTC→ETH→USDT)
3. **Statistical Arbitrage** - Mean reversion opportunities

---

## 🔧 Configuration

```javascript
await scanner.init({
  exchanges: ['Binance', 'Coinbase', 'Kraken'],
  updateInterval: 1000, // 1 second
  minProfit: 0.5,
  maxSlippage: 0.2,
  includeFees: true
});
```

---

## 📄 License

MIT License

**Version:** 1.0.0 | **Last Updated:** 2026-03-10
