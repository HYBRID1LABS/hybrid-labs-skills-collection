# Multi-Agent Coordinator

**Orchestrate multiple AI agents with defined roles and workflows**

---

## 🎯 Overview

The Multi-Agent Coordinator enables you to build teams of AI agents with specialized roles, clear task routing, and automated handoff protocols. Perfect for complex workflows that require multiple areas of expertise.

---

## ✨ Features

- **Role-Based Assignment** - Define agent roles (researcher, writer, reviewer, etc.)
- **Task Lifecycle Management** - Automated workflow: inbox → spec → build → review → done
- **Async Communication** - Agents communicate without blocking
- **Artifact Sharing** - Share files, code, and results between agents
- **Model Routing** - Assign different models based on task complexity
- **Progress Tracking** - Real-time status updates for each task

---

## 📦 Installation

```bash
npm install @hybrid-labs/multi-agent-coordinator
```

### Prerequisites

- Node.js 18+
- OpenClaw framework
- Access to AI models (Ollama, OpenAI, etc.)

---

## 🚀 Quick Start

### Basic Example

```javascript
const coordinator = require('@hybrid-labs/multi-agent-coordinator');

// Initialize coordinator
const team = await coordinator.create({
  name: 'Content Team',
  agents: {
    researcher: {
      model: 'qwen3.5:397b-cloud',
      specialty: 'research',
      maxTokens: 8000
    },
    writer: {
      model: 'qwen3:8b',
      specialty: 'content-creation',
      maxTokens: 4000
    },
    reviewer: {
      model: 'qwen3:8b',
      specialty: 'quality-assurance',
      maxTokens: 4000
    }
  }
});

// Assign a task
const task = await team.assignTask({
  title: 'Write blog post about AI trends',
  description: 'Research and write a 2000-word article about 2026 AI trends',
  workflow: ['research', 'write', 'review'],
  priority: 'high'
});

// Monitor progress
task.on('status-change', (status) => {
  console.log(`Task ${task.id} is now: ${status}`);
});

// Wait for completion
const result = await task.waitForCompletion();
console.log('Final output:', result.output);
```

---

## 📖 API Reference

### `coordinator.create(config)`

Create a new agent team.

**Parameters:**
- `config.name` (string) - Team name
- `config.agents` (object) - Agent definitions with roles

**Returns:** Team instance

---

### `team.assignTask(options)`

Assign a new task to the team.

**Parameters:**
- `options.title` (string) - Task title
- `options.description` (string) - Detailed description
- `options.workflow` (array) - Sequence of agent roles
- `options.priority` (string) - low|medium|high|critical
- `options.deadline` (Date) - Optional deadline

**Returns:** Task instance

---

### `task.waitForCompletion()`

Wait for task to complete through all workflow stages.

**Returns:** Promise with final output

---

## 🎨 Advanced Usage

### Custom Handoff Protocol

```javascript
const team = await coordinator.create({
  name: 'Dev Team',
  handoffProtocol: {
    requireApproval: true,
    autoAssign: false,
    notifyOnComplete: true
  }
});
```

### Parallel Task Execution

```javascript
// Assign multiple tasks in parallel
const tasks = await Promise.all([
  team.assignTask({ title: 'Task 1', workflow: ['research', 'write'] }),
  team.assignTask({ title: 'Task 2', workflow: ['research', 'write'] }),
  team.assignTask({ title: 'Task 3', workflow: ['research', 'write'] })
]);
```

### Error Handling

```javascript
task.onError((error) => {
  console.error('Task failed:', error);
  // Retry or escalate
  task.retry({ maxAttempts: 3 });
});
```

---

## 📊 Use Cases

### 1. Content Production Pipeline

```javascript
const contentTeam = await coordinator.create({
  agents: {
    researcher: { model: 'qwen3.5:397b', specialty: 'research' },
    writer: { model: 'qwen3:8b', specialty: 'writing' },
    editor: { model: 'qwen3:8b', specialty: 'editing' },
    seo: { model: 'qwen3:8b', specialty: 'seo-optimization' }
  }
});

await contentTeam.assignTask({
  title: 'SEO Blog Post',
  workflow: ['researcher', 'writer', 'editor', 'seo']
});
```

### 2. Code Review Process

```javascript
const devTeam = await coordinator.create({
  agents: {
    developer: { model: 'qwen3.5:397b', specialty: 'coding' },
    reviewer: { model: 'qwen3:8b', specialty: 'code-review' },
    tester: { model: 'qwen3:8b', specialty: 'testing' }
  }
});

await devTeam.assignTask({
  title: 'Implement feature X',
  workflow: ['developer', 'reviewer', 'tester']
});
```

### 3. Customer Support Escalation

```javascript
const supportTeam = await coordinator.create({
  agents: {
    tier1: { model: 'qwen2.5:7b', specialty: 'basic-support' },
    tier2: { model: 'qwen3:8b', specialty: 'technical-support' },
    specialist: { model: 'qwen3.5:397b', specialty: 'expert-support' }
  }
});
```

---

## 🔧 Configuration

### Model Routing

```javascript
const config = {
  modelRouting: {
    simple: 'qwen2.5:7b',      // Heartbeats, data pulling
    medium: 'qwen3:8b',         // Analysis, drafting
    complex: 'qwen3.5:397b'     // Strategy, architecture
  }
};
```

### Memory Settings

```javascript
const config = {
  memory: {
    shared: true,               // Enable shared memory
    persistence: 'sqlite',      // Storage backend
    ttl: 86400000              // 24 hours
  }
};
```

---

## 🧪 Testing

```bash
npm test
```

### Example Test

```javascript
describe('Multi-Agent Coordinator', () => {
  it('should assign task to team', async () => {
    const team = await coordinator.create({ /* ... */ });
    const task = await team.assignTask({ /* ... */ });
    expect(task.status).toBe('pending');
  });
});
```

---

## 📝 Best Practices

1. **Define Clear Roles** - Each agent should have a specific specialty
2. **Use Appropriate Models** - Match model complexity to task requirements
3. **Set Deadlines** - Prevent tasks from running indefinitely
4. **Monitor Progress** - Use event listeners for real-time updates
5. **Handle Errors** - Implement retry logic and escalation paths

---

## 🔗 Related Skills

- [agent-memory-store](../agent-memory-store) - Shared memory for agents
- [memory-tiering](../memory-tiering) - Optimize memory usage
- [token-manager](../token-manager) - Monitor context windows

---

## 📄 License

MIT License - See LICENSE file for details.

---

**Version:** 1.0.0  
**Last Updated:** 2026-03-10  
**Maintainer:** Hybrid Labs Team
