# Revenue Operations

**SaaS revenue optimization with pipeline coverage and forecast accuracy**

---

## 🎯 Overview

Analyze pipeline coverage, track forecast accuracy with MAPE, and calculate GTM efficiency metrics for SaaS revenue optimization. Essential for revenue teams and CFOs.

---

## ✨ Features

- **Pipeline Coverage** - Quota vs pipeline analysis
- **Forecast Accuracy** - MAPE (Mean Absolute Percentage Error)
- **GTM Efficiency** - CAC, LTV, payback period
- **Revenue Attribution** - Multi-touch attribution
- **Dashboard Metrics** - Real-time revenue KPIs

---

## 📦 Installation

```bash
npm install @hybrid-labs/revenue-operations
```

---

## 🚀 Quick Start

```javascript
const revOps = require('@hybrid-labs/revenue-operations');

// Calculate pipeline coverage
const coverage = await revOps.calculateCoverage({
  quota: 100000,
  pipeline: 350000
});
console.log(`Coverage: ${coverage.ratio}x`); // 3.5x

// Get forecast accuracy
const accuracy = await revOps.getForecastAccuracy({
  actuals: [90, 95, 100, 105],
  forecasts: [85, 90, 98, 102]
});
console.log(`MAPE: ${accuracy.mape}%`); // 5.2%

// GTM efficiency metrics
const metrics = await revOps.getGTMMetrics({
  revenue: 500000,
  cac: 50000,
  ltv: 150000,
  paybackMonths: 12
});
console.log(metrics);
// { ltvCacRatio: 3.0, paybackPeriod: 12, efficiency: 0.85 }
```

---

## 📊 Key Metrics

| Metric | Formula | Benchmark |
|--------|---------|-----------|
| Pipeline Coverage | Pipeline / Quota | 3-4x |
| Forecast Accuracy (MAPE) | MAPE | <10% |
| LTV:CAC Ratio | LTV / CAC | 3:1 |
| Payback Period | CAC / MRR | <12 months |
| GTM Efficiency | (Revenue - Cost) / Revenue | >70% |

---

## 🎨 Advanced Usage

### Revenue Forecasting

```javascript
const forecast = await revOps.forecastRevenue({
  historical: [100, 110, 120, 130],
  growthRate: 0.1,
  periods: 3
});
// [143, 157, 173]
```

### Cohort Analysis

```javascript
const cohorts = await revOps.analyzeCohorts({
  customers: customerData,
  metric: 'retention',
  periods: 12
});
```

---

## 🔧 Configuration

```javascript
await revOps.init({
  currency: 'USD',
  fiscalYearStart: '2026-01-01',
  defaultCoverage: 3.0
});
```

---

## 📄 License

MIT License

**Version:** 1.0.0 | **Last Updated:** 2026-03-10
