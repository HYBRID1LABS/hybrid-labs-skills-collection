# Binance Pro

**Complete Binance trading integration - spot & futures with up to 125x leverage**

---

## 🎯 Overview

Binance Pro is the most comprehensive Binance integration available. Trade spot and futures, manage positions, set stop-loss/take-profit, and access real-time market data. Production-tested with €50,000+ in automated trading volume.

---

## ✨ Features

- **Spot Trading** - Market, limit, stop-limit orders
- **Futures Trading** - Up to 125x leverage, isolated/cross margin
- **Real-Time Data** - Price streams, order book, trades
- **Position Management** - Track PnL, margin ratio, liquidation price
- **Risk Management** - Stop-loss, take-profit, trailing stops
- **Account Management** - Balances, orders, trade history

---

## 📦 Installation

```bash
npm install @hybrid-labs/binance-pro
```

### Prerequisites

- Binance account
- API keys (enable Spot & Futures trading)
- Node.js 18+

---

## 🚀 Quick Start

```javascript
const binance = require('@hybrid-labs/binance-pro');

// Initialize with API keys
await binance.init({
  apiKey: 'your-api-key',
  apiSecret: 'your-api-secret',
  testnet: false // Set to true for testing
});

// Get current price
const btcPrice = await binance.getPrice('BTCUSDT');
console.log(`BTC: $${btcPrice}`);

// Place spot market order
const order = await binance.placeOrder({
  symbol: 'BTCUSDT',
  side: 'BUY',
  type: 'MARKET',
  quantity: 0.001
});

// Open futures position
const position = await binance.futuresOpen({
  symbol: 'BTCUSDT',
  side: 'LONG',
  leverage: 10,
  quantity: 0.01
});

// Set stop-loss and take-profit
await binance.setStopLoss('BTCUSDT', {
  stopPrice: 42000,
  quantity: 0.01
});

await binance.setTakeProfit('BTCUSDT', {
  stopPrice: 48000,
  quantity: 0.01
});
```

---

## 📖 API Reference

### Spot Trading

#### `binance.placeOrder(options)`

Place a spot order.

**Parameters:**
- `symbol` (string) - Trading pair (e.g., 'BTCUSDT')
- `side` (string) - BUY or SELL
- `type` (string) - MARKET, LIMIT, STOP_LOSS, etc.
- `quantity` (number) - Amount to trade
- `price` (number) - Price (for LIMIT orders)

**Returns:** Order details

---

#### `binance.getPrice(symbol)`

Get current market price.

**Returns:** Current price (number)

---

#### `binance.getBalance(asset)`

Get balance for a specific asset.

**Returns:** `{ free, locked, total }`

---

### Futures Trading

#### `binance.futuresOpen(options)`

Open a futures position.

**Parameters:**
- `symbol` (string) - Trading pair
- `side` (string) - LONG or SHORT
- `leverage` (number) - 1-125
- `quantity` (number) - Position size
- `marginType` (string) - ISOLATED or CROSSED

**Returns:** Position details

---

#### `binance.futuresClose(symbol)`

Close an open position.

**Returns:** PnL and close details

---

#### `binance.setStopLoss(symbol, options)`

Set stop-loss for a position.

**Parameters:**
- `symbol` (string) - Trading pair
- `stopPrice` (number) - Trigger price
- `quantity` (number) - Amount to close

---

#### `binance.setTakeProfit(symbol, options)`

Set take-profit for a position.

---

### Market Data

#### `binance.subscribePrice(symbol, callback)`

Subscribe to real-time price updates.

**Example:**
```javascript
binance.subscribePrice('BTCUSDT', (price) => {
  console.log(`BTC: $${price}`);
});
```

---

#### `binance.get24hStats(symbol)`

Get 24-hour statistics.

**Returns:** `{ volume, high, low, change, changePercent }`

---

## 🎨 Advanced Examples

### Grid Trading Strategy

```javascript
const grid = await binance.createGrid({
  symbol: 'BTCUSDT',
  lowerPrice: 40000,
  upperPrice: 50000,
  grids: 10,
  investment: 1000
});

await grid.start();
```

### DCA (Dollar-Cost Averaging)

```javascript
const dca = await binance.createDCA({
  symbol: 'BTCUSDT',
  amount: 100, // USDT per buy
  interval: 'daily', // daily, weekly, monthly
  time: '09:00' // CET
});

await dca.start();
```

### Portfolio Tracking

```javascript
const portfolio = await binance.getPortfolio();
console.log(portfolio);
// {
//   totalValue: 10500,
//   pnl: 500,
//   pnlPercent: 5.0,
//   positions: [...]
// }
```

---

## 🔧 Configuration

```javascript
await binance.init({
  apiKey: 'your-key',
  apiSecret: 'your-secret',
  testnet: false,
  recvWindow: 5000,
  rateLimit: true,
  autoReconnect: true
});
```

---

## 🛡️ Security Best Practices

1. **Use Testnet First** - Test strategies on testnet before live trading
2. **Enable IP Whitelist** - Restrict API key to your IP
3. **Limit Permissions** - Only enable necessary permissions
4. **Monitor Activity** - Regularly check trade history
5. **Use Stop-Loss** - Always protect positions

---

## 📊 Error Handling

```javascript
try {
  const order = await binance.placeOrder({ /* ... */ });
} catch (error) {
  if (error.code === 'INSUFFICIENT_BALANCE') {
    console.log('Not enough funds');
  } else if (error.code === 'INVALID_PRICE') {
    console.log('Price format error');
  } else {
    console.error('Trading error:', error);
  }
}
```

---

## 🔗 Related Skills

- [crypto-arbitrage-scanner](../crypto-arbitrage-scanner) - Find arbitrage opportunities
- [defi-yield-optimizer](../defi-yield-optimizer) - DeFi yield farming
- [crypto-market-data](../crypto-market-data) - Market data

---

## 📄 License

MIT License

**Version:** 1.0.0 | **Last Updated:** 2026-03-10 | **Production Tested:** ✅
