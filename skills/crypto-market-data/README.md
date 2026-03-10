# Crypto Market Data

**Professional-grade cryptocurrency and stock market data - no API key needed**

---

## 🎯 Overview

Access real-time cryptocurrency and stock market data without API keys. Zero external dependencies, perfect for quick integrations and prototyping.

---

## ✨ Features

- **No API Key Required** - Free tier available
- **Real-Time Prices** - Live price updates
- **Historical Data** - OHLCV data
- **Market Stats** - Market cap, volume, supply
- **Stock Data** - Company profiles and prices

---

## 📦 Installation

```bash
npm install @hybrid-labs/crypto-market-data
```

---

## 🚀 Quick Start

```javascript
const marketData = require('@hybrid-labs/crypto-market-data');

// Get current price
const btc = await marketData.getPrice('BTC');
console.log(`BTC: $${btc}`);

// Get market stats
const stats = await marketData.getStats('ETH');
console.log(stats);
// { marketCap: 200000000000, volume24h: 10000000000, supply: 120000000 }

// Get top 100 coins
const top100 = await marketData.getTopCoins(100);

// Get historical data
const history = await marketData.getHistory('BTC', {
  period: '1d',
  limit: 30
});
```

---

## 📖 API Reference

### `getPrice(symbol)`

Get current price for a cryptocurrency or stock.

---

### `getStats(symbol)`

Get market statistics (market cap, volume, supply).

---

### `getTopCoins(limit)`

Get top N cryptocurrencies by market cap.

---

### `getHistory(symbol, options)`

Get historical price data.

**Parameters:**
- `symbol` (string) - Asset symbol
- `options.period` (string) - 1h, 1d, 1w, 1M
- `options.limit` (number) - Number of data points

---

## 🔧 Configuration

No configuration needed - works out of the box!

---

## 📄 License

MIT License

**Version:** 1.0.0 | **Last Updated:** 2026-03-10
