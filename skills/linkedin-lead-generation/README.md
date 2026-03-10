# LinkedIn Lead Generation

**Automated B2B lead generation with profile verification and PDF reports**

---

## 🎯 Overview

Search, research, and verify high-value prospects on LinkedIn. Automatically generates professional PDF reports with qualified leads for your target market.

---

## ✨ Features

- **Advanced Search** - Filter by title, industry, location, company size
- **Profile Verification** - Ensure leads are active and relevant
- **Company Research** - Enrich with company data
- **PDF Reports** - Professional, ready-to-share reports
- **Bulk Processing** - Handle hundreds of leads

---

## 📦 Installation

```bash
npm install @hybrid-labs/linkedin-lead-generation
```

### Prerequisites

- LinkedIn account
- Browser with LinkedIn session (or cookies)
- Node.js 18+

---

## 🚀 Quick Start

```javascript
const leadGen = require('@hybrid-labs/linkedin-lead-generation');

// Search for leads
const leads = await leadGen.search({
  title: 'Founder',
  industry: 'E-commerce',
  location: 'Spain',
  companySize: '11-50',
  limit: 50
});

// Enrich with company data
const enriched = await leadGen.enrich(leads);

// Generate PDF report
await leadGen.generateReport(enriched, {
  format: 'pdf',
  includeContactInfo: true,
  outputPath: './leads-report.pdf'
});

console.log(`Found ${leads.length} qualified leads`);
```

---

## 📊 Search Filters

| Filter | Options | Example |
|--------|---------|---------|
| Title | Any | 'Founder', 'CEO', 'CTO' |
| Industry | Any | 'E-commerce', 'SaaS', 'Healthcare' |
| Location | Any | 'Spain', 'United States', 'Remote' |
| Company Size | 1-10, 11-50, 51-200, 201-500, 500+ | '11-50' |
| Keywords | Any | 'AI', 'automation', 'crypto' |

---

## 🎨 Advanced Usage

### Save to CSV

```javascript
await leadGen.saveToCSV(leads, {
  path: './leads.csv',
  fields: ['name', 'title', 'company', 'location', 'linkedinUrl']
});
```

### Automated Outreach List

```javascript
const qualifiedLeads = leads.filter(lead => {
  return lead.companySize === '11-50' && 
         lead.industry.includes('Tech');
});

await leadGen.prepareForOutreach(qualifiedLeads);
```

---

## 🔧 Configuration

```javascript
await leadGen.init({
  session: 'linkedin-session-cookie',
  maxResults: 100,
  delay: 2000, // ms between requests
  proxy: false
});
```

---

## 📄 License

MIT License

**Version:** 1.0.0 | **Last Updated:** 2026-03-10
