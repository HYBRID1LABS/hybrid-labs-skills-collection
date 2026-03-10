# Contributing to Hybrid Labs Skills Collection

Thank you for your interest in contributing! This document provides guidelines for contributing to the project.

---

## 🎯 How to Contribute

### 1. **Reporting Bugs**

Before creating bug reports, please check existing issues. When creating a bug report, include:

- Clear title and description
- Steps to reproduce
- Expected vs actual behavior
- Environment details (Node.js version, OS, etc.)
- Code examples if applicable

**Example:**
```markdown
**Bug:** binance-pro fails on WebSocket connection

**Steps to Reproduce:**
1. Install skill: `npm install ./skills/binance-pro`
2. Run example: `node examples/stream.js`
3. Error: "WebSocket connection failed"

**Expected:** Connection established
**Actual:** Connection timeout after 30s

**Environment:**
- Node.js: 18.17.0
- OS: macOS 14.0
- Skill version: 1.2.0
```

---

### 2. **Suggesting Features**

Feature suggestions are welcome! Please provide:

- Use case description
- Why this feature matters
- Example usage
- Potential implementation approach

---

### 3. **Code Contributions**

#### Pull Request Process

1. **Fork the repository**
2. **Create a branch** (`git checkout -b feature/amazing-feature`)
3. **Make your changes**
4. **Test thoroughly** (see Testing section below)
5. **Update documentation** if needed
6. **Commit** with clear messages
7. **Push** and create a Pull Request

#### Code Style

- Use ES6+ syntax
- Follow existing code patterns
- Add JSDoc comments for functions
- Keep functions small and focused
- Use meaningful variable names

**Example:**
```javascript
/**
 * Get current price for a trading pair
 * @param {string} symbol - Trading pair (e.g., 'BTCUSDT')
 * @returns {Promise<number>} Current price
 */
async function getPrice(symbol) {
  const ticker = await binance.futuresPrice(symbol);
  return parseFloat(ticker.price);
}
```

---

### 4. **Documentation Contributions**

Documentation improvements are highly valued! You can:

- Fix typos or unclear explanations
- Add examples
- Improve installation guides
- Translate documentation

---

## 🧪 Testing Requirements

Before submitting a PR, ensure:

### Unit Tests
```bash
npm test
```

### Integration Tests
```bash
npm run test:integration
```

### Linting
```bash
npm run lint
```

### Type Checking (if applicable)
```bash
npm run typecheck
```

---

## 📝 Skill Structure

When contributing a new skill, follow this structure:

```
skills/your-skill-name/
├── README.md           # Overview and use cases
├── installation.md     # Setup instructions
├── SKILL.md           # OpenClaw skill definition
├── index.js           # Main skill logic
├── examples/
│   ├── basic.js       # Simple usage example
│   └── advanced.js    # Complex use case
├── tests/
│   └── index.test.js  # Unit tests
└── package.json       # Dependencies
```

---

## 🔍 Code Review Process

All PRs are reviewed by the Hybrid Labs team. Review criteria:

1. **Functionality** - Does it work as described?
2. **Code Quality** - Is the code clean and maintainable?
3. **Documentation** - Is it well documented?
4. **Tests** - Are there adequate tests?
5. **Security** - No hardcoded credentials, proper error handling
6. **Performance** - No obvious performance issues

---

## 🚀 Release Process

Releases are versioned using [Semantic Versioning](https://semver.org/):

- **MAJOR** - Breaking changes
- **MINOR** - New features (backward compatible)
- **PATCH** - Bug fixes (backward compatible)

---

## 📜 Code of Conduct

### Our Pledge

We pledge to make participation in our project a harassment-free experience for everyone.

### Expected Behavior

- Be respectful and inclusive
- Accept constructive criticism
- Focus on what's best for the community
- Show empathy towards others

### Unacceptable Behavior

- Harassment or discrimination
- Trolling or insulting comments
- Publishing others' private information
- Other unethical or unprofessional conduct

---

## 🏆 Recognition

Contributors will be recognized in:

- **README.md** - Top contributors section
- **RELEASE.md** - Contributors to each release
- **Discord** - Contributor role and special channels

---

## 📬 Questions?

- **Discord:** [Join our community](https://discord.gg/hybrid-labs)
- **Email:** hybrid.1labs@gmail.com
- **Issues:** Create an issue with the "question" label

---

**Thank you for contributing to Hybrid Labs Skills Collection! 🚀**

*Your contributions help build the future of autonomous AI agents.*
