# Playwright Scraper Skill

**Advanced web scraping with anti-bot protection**

---

## 🎯 Overview

Playwright-based web scraping with anti-detection, proxy rotation, and session management. Successfully tested on complex sites like Discuss.com.hk and other anti-bot protected websites.

---

## ✨ Features

- **Anti-Bot Protection** - Bypass Cloudflare, Akamai, etc.
- **Proxy Rotation** - Automatic proxy switching
- **Session Management** - Persist cookies and localStorage
- **Screenshot Capture** - Full page or element screenshots
- **JavaScript Rendering** - Full browser automation

---

## 📦 Installation

```bash
npm install @hybrid-labs/playwright-scraper-skill
```

---

## 🚀 Quick Start

```javascript
const scraper = require('@hybrid-labs/playwright-scraper-skill');

// Scrape with anti-detection
const data = await scraper.scrape({
  url: 'https://example.com',
  selectors: {
    title: 'h1',
    content: '.article-body'
  },
  antiDetect: true,
  proxy: 'rotating',
  waitFor: 'networkidle'
});

// Take screenshot
await scraper.screenshot({
  url: 'https://example.com',
  path: './screenshot.png',
  fullPage: true
});
```

---

## 🎨 Advanced Usage

### Handle Login

```javascript
await scraper.login({
  url: 'https://example.com/login',
  credentials: {
    username: 'user',
    password: 'pass'
  }
});

// Now scrape authenticated content
const data = await scraper.scrape({ /* ... */ });
```

### Pagination

```javascript
const allData = await scraper.scrapePaginated({
  url: 'https://example.com/list',
  selectors: { /* ... */ },
  nextButton: '.next-page',
  maxPages: 10
});
```

---

## 🔧 Configuration

```javascript
await scraper.init({
  headless: true,
  proxy: 'rotating',
  timeout: 30000,
  userAgent: 'random'
});
```

---

## 📄 License

MIT License

**Version:** 1.0.0 | **Last Updated:** 2026-03-10
