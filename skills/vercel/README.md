# Vercel Deploy

**Instant deployment to Vercel platform**

---

## 🎯 Overview

Deploy static sites and serverless functions to Vercel with instant preview URLs and production management. Perfect for Next.js, React, Vue, and static sites.

---

## ✨ Features

- **Instant Deployments** - Deploy in seconds
- **Preview URLs** - Auto-generated for every commit
- **Environment Variables** - Secure management
- **Custom Domains** - Automatic SSL certificates
- **Edge Functions** - Serverless at the edge

---

## 📦 Installation

```bash
npm install @hybrid-labs/vercel
```

---

## 🚀 Quick Start

```javascript
const vercel = require('@hybrid-labs/vercel');

// Deploy project
const deployment = await vercel.deploy({
  path: './my-site',
  project: 'my-awesome-site',
  env: 'production'
});

console.log(`Live at: ${deployment.url}`);

// Get preview URL for branch
const preview = await vercel.getPreviewUrl({
  project: 'my-site',
  branch: 'feature/new-design'
});
```

---

## 🎨 Advanced Usage

### Environment Variables

```javascript
await vercel.setEnvVars({
  project: 'my-site',
  env: {
    API_KEY: 'secret',
    DATABASE_URL: 'postgres://...'
  }
});
```

### Custom Domain

```javascript
await vercel.addDomain({
  project: 'my-site',
  domain: 'example.com'
});
```

---

## 🔧 Configuration

```javascript
await vercel.init({
  token: 'vercel-token',
  teamId: 'team-id' // optional
});
```

---

## 📄 License

MIT License

**Version:** 1.0.0 | **Last Updated:** 2026-03-10
