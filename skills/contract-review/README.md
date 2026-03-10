# Contract Review

**Legal contract analysis with 41 risk categories (CUAD dataset)**

---

## 🎯 Overview

Analyze legal contracts using the CUAD dataset (41 risk categories). Supports NDA, SaaS, M&A, employment, payment/merchant, and finder/broker agreements. Identifies red flags and suggests redlines.

---

## ✨ Features

- **41 Risk Categories** - Comprehensive coverage
- **Red Flag Detection** - Automatic identification
- **Redline Suggestions** - Suggested improvements
- **Market Standards** - Compare to industry norms
- **Multi-Contract Types** - NDA, SaaS, M&A, Employment

---

## 📦 Installation

```bash
npm install @hybrid-labs/contract-review
```

---

## 🚀 Quick Start

```javascript
const contractReview = require('@hybrid-labs/contract-review');

// Analyze contract
const analysis = await contractReview.analyze({
  text: contractText,
  type: 'SaaS'
});

// Get red flags
const redFlags = analysis.getRedFlags();
console.log(redFlags);
// [
//   { category: 'Liability Cap', risk: 'high', clause: '...' },
//   { category: 'Termination', risk: 'medium', clause: '...' }
// ]

// Get suggested redlines
const redlines = await contractReview.suggestRedlines({
  clause: 'Indemnification',
  riskLevel: 'high'
});

// Compare to market standards
const comparison = await contractReview.compareToMarket({
  contractType: 'SaaS',
  clauses: analysis.clauses
});
```

---

## 📊 Risk Categories

### Financial Risks
- Liability cap
- Insurance requirements
- Payment terms
- Price increase rights

### Legal Risks
- Indemnification
- Termination rights
- Governing law
- Dispute resolution

### Operational Risks
- Service level agreements
- Data protection
- Intellectual property
- Non-compete clauses

---

## 🎨 Advanced Usage

### Batch Analysis

```javascript
const results = await contractReview.batchAnalyze({
  contracts: [contract1, contract2, contract3],
  type: 'NDA'
});
```

### Custom Rules

```javascript
await contractReview.addRule({
  name: 'Maximum Liability',
  pattern: /liability.*limited.*\$(\d+)/,
  risk: 'high',
  threshold: 1000000
});
```

---

## 🔧 Configuration

```javascript
await contractReview.init({
  defaultType: 'SaaS',
  riskThreshold: 'medium',
  includeSuggestions: true
});
```

---

## 📄 License

MIT License

**Version:** 1.0.0 | **Last Updated:** 2026-03-10
