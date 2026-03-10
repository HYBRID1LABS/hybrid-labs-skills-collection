# Agent Memory Store

**Shared semantic memory for AI agents with SQLite persistence**

---

## 🎯 Overview

Agent Memory Store provides a shared semantic memory system for AI agents. Built on SQLite with vector similarity search, it enables agents to remember context, learnings, and user preferences across sessions.

---

## ✨ Features

- **Vector Similarity Search** - Find relevant memories by meaning, not keywords
- **TTL-Based Decay** - Automatic memory expiration
- **Cross-Agent Sharing** - Multiple agents access the same memory
- **Automatic Compaction** - Prevents database bloat
- **Type Safety** - Structured memory types (USER_FACT, PREFERENCE, DECISION, etc.)

---

## 📦 Installation

```bash
npm install @hybrid-labs/agent-memory-store
```

---

## 🚀 Quick Start

```javascript
const memory = require('@hybrid-labs/agent-memory-store');

// Initialize
await memory.init({
  dbPath: './memory.db',
  vectorDimensions: 384
});

// Store a memory
await memory.store({
  type: 'USER_PREFERENCE',
  content: 'User prefers concise responses',
  metadata: { userId: 'user-123' },
  ttl: 86400000 // 24 hours
});

// Search memories
const results = await memory.search('response style', {
  limit: 5,
  minScore: 0.7
});

console.log(results);
// [{ content: 'User prefers concise responses', score: 0.89, ... }]
```

---

## 📖 API Reference

### `memory.store(options)`

Store a new memory.

**Parameters:**
- `options.type` (string) - Memory type (USER_FACT, PREFERENCE, DECISION, ENTITY, EPISODE)
- `options.content` (string) - Memory content
- `options.metadata` (object) - Optional metadata
- `options.ttl` (number) - Time to live in milliseconds

**Returns:** Promise with memory ID

---

### `memory.search(query, options)`

Search memories by semantic similarity.

**Parameters:**
- `query` (string) - Search query
- `options.limit` (number) - Max results (default: 10)
- `options.minScore` (number) - Minimum similarity score (0-1)
- `options.type` (string) - Filter by memory type

**Returns:** Array of memories with scores

---

### `memory.delete(id)`

Delete a memory by ID.

---

### `memory.compact()`

Compact and optimize the database.

---

## 🎨 Use Cases

### User Preferences

```javascript
await memory.store({
  type: 'PREFERENCE',
  content: 'User likes voice notes over text',
  metadata: { channel: 'telegram' }
});
```

### Session Context

```javascript
await memory.store({
  type: 'EPISODE',
  content: 'User asked about crypto trading strategies',
  metadata: { sessionId: 'session-456', timestamp: Date.now() }
});
```

### Learnings

```javascript
await memory.store({
  type: 'DECISION',
  content: 'Use qwen3:8b for draft writing, qwen3.5:397b for final optimization',
  metadata: { category: 'model-routing' }
});
```

---

## 🔧 Configuration

```javascript
await memory.init({
  dbPath: './memory.db',
  vectorDimensions: 384,
  maxMemories: 10000,
  autoCompact: true,
  compactThreshold: 0.8
});
```

---

## 📄 License

MIT License

**Version:** 1.0.0 | **Last Updated:** 2026-03-10
