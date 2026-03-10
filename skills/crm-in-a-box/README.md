# CRM In A Box

**File-based CRM with zero SaaS dependency**

---

## 🎯 Overview

Bootstrap and manage a complete CRM using NDJSON files. Track contacts, pipeline deals, and interactions without any SaaS dependency. Perfect for solopreneurs and small teams.

---

## ✨ Features

- **Zero SaaS** - Complete file-based storage
- **NDJSON Format** - Easy to parse and version control
- **Pipeline Management** - Track deals through stages
- **Interaction Logging** - Record calls, emails, meetings
- **Search & Filter** - Fast queries on large datasets

---

## 📦 Installation

```bash
npm install @hybrid-labs/crm-in-a-box
```

---

## 🚀 Quick Start

```javascript
const crm = require('@hybrid-labs/crm-in-a-box');

// Initialize
await crm.init({
  dataPath: './crm-data'
});

// Add contact
const contact = await crm.addContact({
  name: 'John Doe',
  email: 'john@example.com',
  company: 'Acme Inc',
  stage: 'lead',
  tags: ['warm', 'enterprise']
});

// Create deal
const deal = await crm.createDeal({
  title: 'Acme Inc - Enterprise Plan',
  value: 5000,
  stage: 'negotiation',
  contactId: contact.id,
  closeDate: '2026-04-01'
});

// Update deal stage
await crm.updateDeal(deal.id, {
  stage: 'closed-won',
  closedAt: new Date()
});

// Log interaction
await crm.logInteraction({
  contactId: contact.id,
  type: 'call',
  notes: 'Discussed pricing, interested in annual plan',
  duration: 30 // minutes
});

// Search contacts
const contacts = await crm.searchContacts({
  stage: 'lead',
  tags: ['warm']
});
```

---

## 📊 Data Structure

### Contacts
```json
{
  "id": "contact-123",
  "name": "John Doe",
  "email": "john@example.com",
  "company": "Acme Inc",
  "stage": "lead",
  "tags": ["warm"],
  "createdAt": "2026-03-10T10:00:00Z"
}
```

### Deals
```json
{
  "id": "deal-456",
  "title": "Acme Inc - Enterprise Plan",
  "value": 5000,
  "stage": "negotiation",
  "contactId": "contact-123",
  "closeDate": "2026-04-01"
}
```

### Interactions
```json
{
  "id": "interaction-789",
  "contactId": "contact-123",
  "type": "call",
  "notes": "Discussed pricing",
  "timestamp": "2026-03-10T14:00:00Z"
}
```

---

## 🎨 Advanced Usage

### Pipeline Report

```javascript
const report = await crm.getPipelineReport();
console.log(report);
// {
//   total: 50000,
//   byStage: {
//     'lead': 20000,
//     'negotiation': 15000,
//     'closed-won': 15000
//   }
// }
```

### Export Data

```javascript
await crm.export({
  format: 'csv',
  path: './backup.csv',
  entities: ['contacts', 'deals']
});
```

---

## 🔧 Configuration

```javascript
await crm.init({
  dataPath: './crm-data',
  autoBackup: true,
  backupInterval: 86400000 // daily
});
```

---

## 📄 License

MIT License

**Version:** 1.0.0 | **Last Updated:** 2026-03-10
