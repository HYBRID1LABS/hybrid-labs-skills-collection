# Memory Tiering

**Automatic memory tiering (HOT/WARM/COLD) for optimal context usage**

---

## 🎯 Overview

Memory Tiering automatically organizes memories into three tiers based on access frequency and recency. This optimizes context window usage and reduces token costs by keeping only relevant memories in active context.

---

## ✨ Features

- **HOT Tier** - Frequently accessed memories (always in context)
- **WARM Tier** - Occasionally accessed (loaded on demand)
- **COLD Tier** - Rarely accessed (archived, searchable)
- **Automatic Migration** - Memories move between tiers based on usage
- **Cost Optimization** - Reduces token usage by 40-60%

---

## 📦 Installation

```bash
npm install @hybrid-labs/memory-tiering
```

---

## 🚀 Quick Start

```javascript
const tiering = require('@hybrid-labs/memory-tiering');

// Configure tiers
await tiering.configure({
  hotThreshold: 10,        // Last 10 accesses = HOT
  warmThreshold: 100,      // Last 100 accesses = WARM
  coldAfter: 86400000,     // 24h without access = COLD
  autoMigrate: true
});

// Add memory
await tiering.store({
  type: 'USER_FACT',
  content: 'User is located in Spain'
});

// Access memory (automatically updates tier)
await tiering.access('memory-id-123');

// Optimize tiers
await tiering.optimize();
```

---

## 📊 Tier Definitions

| Tier | Access Frequency | Context | Use Case |
|------|-----------------|---------|----------|
| **HOT** | Last 10 accesses | Always loaded | Active conversation context |
| **WARM** | Last 100 accesses | On-demand | Recent projects, ongoing tasks |
| **COLD** | Older than threshold | Archived only | Historical data, old learnings |

---

## 🔧 Configuration

```javascript
await tiering.configure({
  hotThreshold: 10,
  warmThreshold: 100,
  coldAfter: 86400000,
  autoMigrate: true,
  checkInterval: 3600000, // Check every hour
  metrics: true
});
```

---

## 📈 Metrics

```javascript
const stats = await tiering.getStats();
console.log(stats);
// {
//   hot: 10,
//   warm: 50,
//   cold: 200,
//   total: 260,
//   tokenSavings: '45%'
// }
```

---

## 📄 License

MIT License

**Version:** 1.0.0 | **Last Updated:** 2026-03-10
