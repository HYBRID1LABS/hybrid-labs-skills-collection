# Railway Deploy

**One-command deployment to Railway platform**

---

## 🎯 Overview

Deploy applications to Railway with a single command. Supports Docker, Node.js, Python, and more with automatic environment variable management and database provisioning.

---

## ✨ Features

- **One-Command Deploy** - `railway deploy`
- **Environment Variables** - Secure management
- **Database Provisioning** - PostgreSQL, MySQL, Redis, MongoDB
- **Custom Domains** - Automatic SSL
- **Preview Environments** - Per-branch deployments

---

## 📦 Installation

```bash
npm install @hybrid-labs/railway-deploy
```

---

## 🚀 Quick Start

```javascript
const railway = require('@hybrid-labs/railway-deploy');

// Deploy project
const deployment = await railway.deploy({
  path: './my-app',
  name: 'my-awesome-app',
  env: {
    NODE_ENV: 'production',
    API_KEY: 'secret'
  },
  region: 'europe-west'
});

console.log(`Deployed to: ${deployment.url}`);

// Provision database
const db = await railway.provisionDatabase({
  type: 'postgresql',
  name: 'my-app-db',
  plan: 'hobby'
});

console.log(`Database URL: ${db.connectionString}`);
```

---

## 📊 Supported Services

- ✅ Node.js applications
- ✅ Python applications
- ✅ Docker containers
- ✅ Static sites
- ✅ Databases (PostgreSQL, MySQL, Redis, MongoDB)
- ✅ Cron jobs

---

## 🔧 Configuration

```javascript
await railway.init({
  token: 'railway-token',
  projectId: 'project-id',
  autoDeploy: true
});
```

---

## 📄 License

MIT License

**Version:** 1.0.0 | **Last Updated:** 2026-03-10
