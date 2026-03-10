# DeFi Yield Optimizer

**Cross-protocol yield optimization for maximum APY**

---

## 🎯 Overview

Automatically scans multiple DeFi protocols to find the best yield opportunities and rebalances positions for maximum APY. Covers Aave, Compound, Curve, Yearn, Uniswap v3, and emerging L2 protocols.

---

## ✨ Features

- **Multi-Protocol Scanning** - Aave, Compound, Curve, Yearn, Uniswap v3
- **APY vs Risk Analysis** - Compare yields with risk metrics
- **Auto-Rebalancing** - Automatically move funds to best yield
- **TVL Tracking** - Monitor protocol health
- **Gas Optimization** - Factor in gas costs for net APY

---

## 📦 Installation

```bash
npm install @hybrid-labs/defi-yield-optimizer
```

---

## 🚀 Quick Start

```javascript
const optimizer = require('@hybrid-labs/defi-yield-optimizer');

// Find best yield for USDC
const opportunities = await optimizer.findBestYield({
  token: 'USDC',
  minAPY: 5,
  maxRisk: 'medium',
  chains: ['ethereum', 'arbitrum', 'optimism']
});

console.log(opportunities);
// [
//   { protocol: 'Aave', apy: 8.5, risk: 'low', tvl: 500000000 },
//   { protocol: 'Curve', apy: 12.3, risk: 'medium', tvl: 200000000 }
// ]

// Auto-rebalance to best yield
await optimizer.rebalance({
  from: 'Compound',
  to: 'Aave',
  amount: 1000,
  token: 'USDC'
});
```

---

## 📊 Supported Protocols

| Protocol | Chains | Avg APY | Risk Level |
|----------|--------|---------|------------|
| Aave | ETH, ARB, OP | 5-10% | Low |
| Compound | ETH | 4-8% | Low |
| Curve | ETH, ARB, OP | 8-15% | Medium |
| Yearn | ETH, FTM | 10-20% | Medium |
| Uniswap v3 | ETH, ARB, OP | 15-50% | High |

---

## 🔧 Configuration

```javascript
await optimizer.init({
  wallet: '0x...',
  chains: ['ethereum', 'arbitrum', 'optimism'],
  minAPY: 5,
  maxSlippage: 1,
  gasPriceLimit: 50 // gwei
});
```

---

## 📄 License

MIT License

**Version:** 1.0.0 | **Last Updated:** 2026-03-10
