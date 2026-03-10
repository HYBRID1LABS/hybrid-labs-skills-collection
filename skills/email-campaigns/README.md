# Email Campaigns

**Write high-converting email campaigns for any business**

---

## 🎯 Overview

Generate high-converting email campaigns including newsletters, re-engagement sequences, B2B cold outreach, and automated drip campaigns. Includes subject line formulas and segmentation strategies.

---

## ✨ Features

- **Multiple Campaign Types** - Newsletters, cold outreach, drip campaigns
- **Subject Line Generator** - Proven formulas for higher open rates
- **Segmentation Strategies** - Target the right audience
- **Deliverability Best Practices** - Avoid spam filters
- **A/B Testing Templates** - Optimize performance

---

## 📦 Installation

```bash
npm install @hybrid-labs/email-campaigns
```

---

## 🚀 Quick Start

```javascript
const emailCampaigns = require('@hybrid-labs/email-campaigns');

// Generate cold outreach campaign
const campaign = await emailCampaigns.create({
  type: 'cold-outreach',
  industry: 'SaaS',
  goal: 'demo-bookings',
  tone: 'professional',
  length: 'short'
});

console.log(campaign.subject);
// "Quick question about [Company]'s automation"

console.log(campaign.body);
// Full email body with personalization tokens

// Generate subject lines
const subjects = await emailCampaigns.generateSubjectLines({
  topic: 'AI automation',
  urgency: 'medium',
  style: 'curiosity'
});
```

---

## 📊 Campaign Types

| Type | Use Case | Avg Open Rate |
|------|----------|---------------|
| Cold Outreach | First contact | 15-25% |
| Newsletter | Regular updates | 20-30% |
| Re-engagement | Win back inactive | 10-20% |
| Drip Campaign | Nurture sequence | 25-40% |
| Promotional | Sales/offers | 15-25% |

---

## 🎨 Advanced Usage

### Drip Campaign Sequence

```javascript
const dripSequence = await emailCampaigns.createDrip({
  name: 'SaaS Onboarding',
  emails: [
    { day: 0, goal: 'welcome' },
    { day: 2, goal: 'education' },
    { day: 5, goal: 'social-proof' },
    { day: 10, goal: 'call-to-action' }
  ]
});
```

### Personalization

```javascript
const email = await emailCampaigns.personalize({
  template: campaign,
  recipient: {
    name: 'John',
    company: 'Acme Inc',
    industry: 'E-commerce'
  }
});
```

---

## 🔧 Configuration

```javascript
await emailCampaigns.init({
  defaultTone: 'professional',
  includeUnsubscribe: true,
  trackLinks: true,
  maxSubjectLength: 60
});
```

---

## 📄 License

MIT License

**Version:** 1.0.0 | **Last Updated:** 2026-03-10
