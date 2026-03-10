# Outreach Sequencer

**Multi-step outreach automation across LinkedIn and email**

---

## 🎯 Overview

Create and manage multi-step outreach sequences with personalization at scale. Automate follow-ups across LinkedIn, email, and other channels with intelligent timing.

---

## ✨ Features

- **Multi-Channel Sequences** - LinkedIn, email, Twitter
- **Personalization** - Dynamic fields at scale
- **Follow-Up Automation** - Smart timing and triggers
- **Response Tracking** - Track replies and engagement
- **A/B Testing** - Test different messages

---

## 📦 Installation

```bash
npm install @hybrid-labs/outreach-sequencer
```

---

## 🚀 Quick Start

```javascript
const sequencer = require('@hybrid-labs/outreach-sequencer');

// Create sequence
const sequence = await sequencer.create({
  name: 'SaaS Founders Outreach',
  steps: [
    { 
      channel: 'linkedin', 
      delay: 0, 
      template: 'connection-request',
      message: 'Hi {{firstName}}, I noticed...'
    },
    { 
      channel: 'email', 
      delay: 2, // days
      template: 'followup-1',
      subject: 'Quick question about {{companyName}}'
    },
    { 
      channel: 'email', 
      delay: 5,
      template: 'followup-2',
      subject: 'Re: {{companyName}}'
    }
  ]
});

// Start sequence with leads
await sequencer.start(sequence, {
  leads: [
    { firstName: 'John', lastName: 'Doe', companyName: 'Acme', email: 'john@acme.com' },
    { firstName: 'Jane', lastName: 'Smith', companyName: 'TechCo', email: 'jane@techco.com' }
  ],
  personalize: true
});
```

---

## 📊 Sequence Templates

### Cold Outreach

```javascript
{
  name: 'B2B Cold Outreach',
  steps: [
    { day: 0, channel: 'email', type: 'initial' },
    { day: 3, channel: 'email', type: 'followup-1' },
    { day: 7, channel: 'email', type: 'followup-2' },
    { day: 14, channel: 'email', type: 'breakup' }
  ]
}
```

### LinkedIn + Email Combo

```javascript
{
  name: 'LinkedIn + Email',
  steps: [
    { day: 0, channel: 'linkedin', type: 'connection' },
    { day: 1, channel: 'linkedin', type: 'message-1' },
    { day: 3, channel: 'email', type: 'followup' }
  ]
}
```

---

## 🎨 Advanced Usage

### Personalization Rules

```javascript
await sequencer.setPersonalizationRules({
  firstName: 'required',
  companyName: 'required',
  industry: 'optional',
  customField: 'fallback-to-company'
});
```

### Response Handling

```javascript
sequencer.onResponse((response) => {
  if (response.positive) {
    sequencer.scheduleCall(response.lead);
  } else {
    sequencer.addToNurture(response.lead);
  }
});
```

---

## 🔧 Configuration

```javascript
await sequencer.init({
  maxLeadsPerDay: 50,
  workingHours: { start: 9, end: 17 },
  timezone: 'Europe/Madrid',
  trackLinks: true
});
```

---

## 📄 License

MIT License

**Version:** 1.0.0 | **Last Updated:** 2026-03-10
