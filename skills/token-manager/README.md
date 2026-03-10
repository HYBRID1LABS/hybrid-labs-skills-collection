# Token Manager

**Real-time context window monitoring and optimization**

---

## 🎯 Overview

Token Manager monitors token usage in real-time and provides alerts before hitting context limits. Prevents context truncation and optimizes model routing decisions.

---

## ✨ Features

- **Real-Time Monitoring** - Track token usage as it happens
- **Smart Alerts** - Warnings at 50% and 80% capacity
- **Auto-Summarization** - Automatically summarize old context
- **Model Routing** - Recommend optimal model based on token needs
- **Cost Tracking** - Monitor token costs across sessions

---

## 📦 Installation

```bash
npm install @hybrid-labs/token-manager
```

---

## 🚀 Quick Start

```javascript
const tokenManager = require('@hybrid-labs/token-manager');

// Initialize
await tokenManager.init({
  maxTokens: 8192,
  alertThresholds: [0.5, 0.8]
});

// Listen for alerts
tokenManager.on('warning', (data) => {
  console.log(`⚠️ Context usage: ${data.percentage}%`);
  console.log(`Tokens used: ${data.used} / ${data.total}`);
});

tokenManager.on('critical', (data) => {
  console.log(`🚨 CRITICAL: ${data.percentage}% - Action needed!`);
});

// Get current usage
const usage = await tokenManager.getUsage();
console.log(usage);
// { used: 4096, total: 8192, percentage: 50, remaining: 4096 }

// Get optimization suggestions
const suggestions = await tokenManager.getOptimizations();
console.log(suggestions);
// ['Summarize messages older than 1h', 'Move old memories to COLD tier']
```

---

## 📖 API Reference

### `tokenManager.getUsage()`

Get current token usage statistics.

**Returns:** `{ used, total, percentage, remaining }`

---

### `tokenManager.getOptimizations()`

Get suggestions for reducing token usage.

**Returns:** Array of optimization recommendations

---

### `tokenManager.reset()`

Reset token counter for new conversation.

---

## 🎨 Use Cases

### Session Monitoring

```javascript
// Check before sending message
const usage = await tokenManager.getUsage();
if (usage.percentage > 80) {
  await tokenManager.summarizeOldContext();
}
```

### Model Routing

```javascript
const usage = await tokenManager.getUsage();
if (usage.remaining < 2000) {
  // Switch to smaller model
  model = 'qwen2.5:7b';
} else {
  model = 'qwen3.5:397b';
}
```

---

## 🔧 Configuration

```javascript
await tokenManager.init({
  maxTokens: 8192,
  alertThresholds: [0.5, 0.8],
  autoSummarize: true,
  summarizeAt: 0.9,
  trackCosts: true
});
```

---

## 📄 License

MIT License

**Version:** 1.0.0 | **Last Updated:** 2026-03-10
