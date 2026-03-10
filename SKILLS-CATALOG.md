# 📚 Skills Catalog - Top 20 Hybrid Labs Skills

**Complete documentation of the 20 curated skills in this collection**

---

## 🤖 Agent Architecture (4 skills)

### 1. **multi-agent-coordinator**
**Category:** Agent Architecture  
**Complexity:** ⭐⭐⭐⭐  
**Use Case:** Orchestrate multiple AI agents working on different tasks

**Description:**
Coordinates multiple AI agents with defined roles, task routing, and handoff protocols. Perfect for complex workflows requiring specialization.

**Key Features:**
- Role-based agent assignment
- Task lifecycle management (inbox → spec → build → review → done)
- Async communication between agents
- Artifact sharing and versioning

**Installation:**
```bash
npm install @hybrid-labs/multi-agent-coordinator
```

**Example:**
```javascript
const coordinator = require('@hybrid-labs/multi-agent-coordinator');

// Define agent roles
const team = {
  researcher: { model: 'qwen3.5:397b', specialty: 'research' },
  writer: { model: 'qwen3:8b', specialty: 'content' },
  reviewer: { model: 'qwen3:8b', specialty: 'quality' }
};

// Assign task
await coordinator.assignTask({
  task: 'Write blog post about AI trends',
  team: team,
  workflow: ['research', 'write', 'review']
});
```

**Docs:** [skills/multi-agent-coordinator/README.md](./skills/multi-agent-coordinator/README.md)

---

### 2. **agent-memory-store**
**Category:** Agent Architecture  
**Complexity:** ⭐⭐⭐  
**Use Case:** Shared semantic memory across agents

**Description:**
SQLite-backed semantic memory store that persists across agent sessions. Enables agents to remember context, learnings, and user preferences.

**Key Features:**
- Vector similarity search
- TTL-based memory decay
- Cross-agent memory sharing
- Automatic compaction

**Installation:**
```bash
npm install @hybrid-labs/agent-memory-store
```

**Example:**
```javascript
const memory = require('@hybrid-labs/agent-memory-store');

// Store memory
await memory.store({
  type: 'USER_PREFERENCE',
  content: 'User prefers concise responses',
  ttl: 86400000 // 24 hours
});

// Search memories
const results = await memory.search('response style', { limit: 5 });
```

**Docs:** [skills/agent-memory-store/README.md](./skills/agent-memory-store/README.md)

---

### 3. **memory-tiering**
**Category:** Agent Architecture  
**Complexity:** ⭐⭐⭐  
**Use Case:** Automatic memory tiering (HOT/WARM/COLD)

**Description:**
Automatically tiers memories based on access frequency and recency. Optimizes context window usage and reduces token costs.

**Key Features:**
- HOT: Frequently accessed (always in context)
- WARM: Occasionally accessed (loaded on demand)
- COLD: Rarely accessed (archived, searchable)
- Automatic tier migration

**Installation:**
```bash
npm install @hybrid-labs/memory-tiering
```

**Example:**
```javascript
const tiering = require('@hybrid-labs/memory-tiering');

// Configure tiers
await tiering.configure({
  hotThreshold: 10,      // Last 10 accesses
  warmThreshold: 100,    // Last 100 accesses
  coldAfter: 86400000    // 24 hours without access
});

// Auto-tier memories
await tiering.optimize();
```

**Docs:** [skills/memory-tiering/README.md](./skills/memory-tiering/README.md)

---

### 4. **token-manager**
**Category:** Agent Architecture  
**Complexity:** ⭐⭐  
**Use Case:** Real-time context window monitoring

**Description:**
Monitors token usage in real-time and provides alerts before hitting context limits. Prevents context truncation and optimizes model routing.

**Key Features:**
- Real-time token counting
- Alerts at 50%/80% capacity
- Automatic context summarization
- Model routing recommendations

**Installation:**
```bash
npm install @hybrid-labs/token-manager
```

**Example:**
```javascript
const tokenManager = require('@hybrid-labs/token-manager');

// Monitor context
tokenManager.on('warning', (usage) => {
  console.log(`Context usage: ${usage.percentage}%`);
});

// Get optimization suggestions
const suggestions = await tokenManager.getOptimizations();
```

**Docs:** [skills/token-manager/README.md](./skills/token-manager/README.md)

---

## 💰 Crypto & Trading (4 skills)

### 5. **binance-pro**
**Category:** Crypto & Trading  
**Complexity:** ⭐⭐⭐⭐⭐  
**Use Case:** Complete Binance trading integration

**Description:**
Full-featured Binance integration for spot and futures trading. Supports market/limit orders, position management, stop-loss/take-profit, and real-time data.

**Key Features:**
- Spot & futures trading
- Up to 125x leverage
- Real-time price streams
- Position & PnL tracking
- Stop-loss & take-profit

**Installation:**
```bash
npm install @hybrid-labs/binance-pro
```

**Example:**
```javascript
const binance = require('@hybrid-labs/binance-pro');

// Get price
const btcPrice = await binance.getPrice('BTCUSDT');

// Place order
const order = await binance.placeOrder({
  symbol: 'BTCUSDT',
  side: 'BUY',
  type: 'MARKET',
  quantity: 0.001
});

// Open futures position
const position = await binance.futuresOpen({
  symbol: 'BTCUSDT',
  side: 'LONG',
  leverage: 10,
  quantity: 0.01
});
```

**Docs:** [skills/binance-pro/README.md](./skills/binance-pro/README.md)

---

### 6. **defi-yield-optimizer**
**Category:** Crypto & Trading  
**Complexity:** ⭐⭐⭐⭐  
**Use Case:** Cross-protocol yield optimization

**Description:**
Scans multiple DeFi protocols to find the best yield opportunities. Automatically rebalances positions for maximum APY.

**Key Features:**
- Multi-protocol scanning (Aave, Compound, Curve, Yearn)
- APY vs risk analysis
- Auto-rebalancing
- TVL change tracking

**Installation:**
```bash
npm install @hybrid-labs/defi-yield-optimizer
```

**Example:**
```javascript
const optimizer = require('@hybrid-labs/defi-yield-optimizer');

// Find best yield for USDC
const opportunities = await optimizer.findBestYield({
  token: 'USDC',
  minAPY: 5,
  maxRisk: 'medium'
});

// Auto-rebalance
await optimizer.rebalance({
  from: 'Aave',
  to: 'Curve',
  amount: 1000
});
```

**Docs:** [skills/defi-yield-optimizer/README.md](./skills/defi-yield-optimizer/README.md)

---

### 7. **crypto-arbitrage-scanner**
**Category:** Crypto & Trading  
**Complexity:** ⭐⭐⭐⭐  
**Use Case:** Cross-exchange arbitrage detection

**Description:**
Real-time scanner for arbitrage opportunities across multiple exchanges. Detects price differences and triangular arbitrage.

**Key Features:**
- Multi-exchange price comparison
- Triangular arbitrage detection
- Real-time alerts
- Profit calculation (fees included)

**Installation:**
```bash
npm install @hybrid-labs/crypto-arbitrage-scanner
```

**Example:**
```javascript
const scanner = require('@hybrid-labs/crypto-arbitrage-scanner');

// Scan for opportunities
const opportunities = await scanner.scan({
  exchanges: ['Binance', 'Coinbase', 'Kraken'],
  minProfit: 0.5 // 0.5% minimum profit
});

// Get triangular arbitrage
const triangular = await scanner.findTriangular({
  base: 'USDT',
  path: ['BTC', 'ETH', 'USDT']
});
```

**Docs:** [skills/crypto-arbitrage-scanner/README.md](./skills/crypto-arbitrage-scanner/README.md)

---

### 8. **crypto-market-data**
**Category:** Crypto & Trading  
**Complexity:** ⭐⭐  
**Use Case:** Real-time crypto market data

**Description:**
Professional-grade cryptocurrency and stock market data. No API key needed for free tier. Zero external dependencies.

**Key Features:**
- Real-time prices
- Historical data
- Market cap & volume
- Company profiles (stocks)

**Installation:**
```bash
npm install @hybrid-labs/crypto-market-data
```

**Example:**
```javascript
const marketData = require('@hybrid-labs/crypto-market-data');

// Get current price
const btc = await marketData.getPrice('BTC');

// Get market cap
const stats = await marketData.getStats('ETH');

// Get top 100 coins
const top100 = await marketData.getTopCoins(100);
```

**Docs:** [skills/crypto-market-data/README.md](./skills/crypto-market-data/README.md)

---

## 📈 Marketing & Outreach (4 skills)

### 9. **linkedin-lead-generation**
**Category:** Marketing & Outreach  
**Complexity:** ⭐⭐⭐⭐  
**Use Case:** Automated B2B lead generation

**Description:**
Searches, researches, and verifies non-tech founders on LinkedIn. Generates professional PDF reports with high-value prospects.

**Key Features:**
- Advanced LinkedIn search
- Profile verification
- Company research
- PDF report generation

**Installation:**
```bash
npm install @hybrid-labs/linkedin-lead-generation
```

**Example:**
```javascript
const leadGen = require('@hybrid-labs/linkedin-lead-generation');

// Search for leads
const leads = await leadGen.search({
  title: 'Founder',
  industry: 'E-commerce',
  location: 'Spain',
  companySize: '11-50'
});

// Generate report
await leadGen.generateReport(leads, {
  format: 'pdf',
  includeContactInfo: true
});
```

**Docs:** [skills/linkedin-lead-generation/README.md](./skills/linkedin-lead-generation/README.md)

---

### 10. **email-campaigns**
**Category:** Marketing & Outreach  
**Complexity:** ⭐⭐⭐  
**Use Case:** High-converting email campaign writing

**Description:**
Writes high-converting email campaigns for newsletters, re-engagement, B2B cold outreach, and automated drip campaigns.

**Key Features:**
- Subject line formulas
- Segmentation strategies
- Deliverability best practices
- A/B testing templates

**Installation:**
```bash
npm install @hybrid-labs/email-campaigns
```

**Example:**
```javascript
const emailCampaigns = require('@hybrid-labs/email-campaigns');

// Generate campaign
const campaign = await emailCampaigns.create({
  type: 'cold-outreach',
  industry: 'SaaS',
  goal: 'demo-bookings',
  tone: 'professional'
});

// Get subject lines
const subjects = await emailCampaigns.generateSubjectLines({
  topic: 'AI automation',
  urgency: 'medium'
});
```

**Docs:** [skills/email-campaigns/README.md](./skills/email-campaigns/README.md)

---

### 11. **seo-content-writer**
**Category:** Marketing & Outreach  
**Complexity:** ⭐⭐⭐⭐  
**Use Case:** SEO-optimized content generation

**Description:**
Generates SEO-optimized blog posts, articles, and web content. Includes keyword research, competitor analysis, and on-page optimization.

**Key Features:**
- Keyword research integration
- Competitor content analysis
- On-page SEO optimization
- Readability scoring

**Installation:**
```bash
npm install @hybrid-labs/seo-content-writer
```

**Example:**
```javascript
const seoWriter = require('@hybrid-labs/seo-content-writer');

// Generate article
const article = await seoWriter.write({
  keyword: 'AI automation tools',
  wordCount: 2500,
  tone: 'professional',
  includeFAQ: true
});

// Optimize for SEO
const optimized = await seoWriter.optimize(article, {
  targetScore: 90,
  keywords: ['automation', 'AI', 'productivity']
});
```

**Docs:** [skills/seo-content-writer/README.md](./skills/seo-content-writer/README.md)

---

### 12. **outreach-sequencer**
**Category:** Marketing & Outreach  
**Complexity:** ⭐⭐⭐  
**Use Case:** Multi-step outreach automation

**Description:**
Creates and manages multi-step outreach sequences across LinkedIn, email, and follow-ups with personalization.

**Key Features:**
- Multi-channel sequences
- Personalization at scale
- Follow-up automation
- Response tracking

**Installation:**
```bash
npm install @hybrid-labs/outreach-sequencer
```

**Example:**
```javascript
const sequencer = require('@hybrid-labs/outreach-sequencer');

// Create sequence
const sequence = await sequencer.create({
  name: 'SaaS Founders Outreach',
  steps: [
    { channel: 'linkedin', delay: 0, template: 'connection' },
    { channel: 'email', delay: 2, template: 'followup-1' },
    { channel: 'email', delay: 5, template: 'followup-2' }
  ]
});

// Start sequence
await sequencer.start(sequence, {
  leads: leadList,
  personalize: true
});
```

**Docs:** [skills/outreach-sequencer/README.md](./skills/outreach-sequencer/README.md)

---

## 🛠️ Development & Deployment (4 skills)

### 13. **github-actions-generator**
**Category:** Development & Deployment  
**Complexity:** ⭐⭐⭐  
**Use Case:** Automated CI/CD workflow generation

**Description:**
Generates GitHub Actions workflows for CI/CD, testing, deployment, and automation. Supports multiple languages and frameworks.

**Key Features:**
- Multi-language support (Node, Python, Go, etc.)
- Pre-built templates
- Custom workflow generation
- Security scanning integration

**Installation:**
```bash
npm install @hybrid-labs/github-actions-generator
```

**Example:**
```javascript
const generator = require('@hybrid-labs/github-actions-generator');

// Generate CI workflow
const workflow = await generator.generate({
  language: 'node',
  tasks: ['install', 'test', 'build'],
  deploy: 'vercel'
});

// Save to repo
await generator.save(workflow, {
  repo: 'my-project',
  path: '.github/workflows/ci.yml'
});
```

**Docs:** [skills/github-actions-generator/README.md](./skills/github-actions-generator/README.md)

---

### 14. **railway-deploy**
**Category:** Development & Deployment  
**Complexity:** ⭐⭐⭐  
**Use Case:** One-command deployment to Railway

**Description:**
Deploy applications to Railway with a single command. Supports Docker, Node.js, Python, and more.

**Key Features:**
- One-command deploy
- Environment variable management
- Database provisioning
- Custom domain setup

**Installation:**
```bash
npm install @hybrid-labs/railway-deploy
```

**Example:**
```javascript
const railway = require('@hybrid-labs/railway-deploy');

// Deploy project
await railway.deploy({
  path: './my-app',
  name: 'my-awesome-app',
  env: {
    NODE_ENV: 'production',
    API_KEY: 'secret'
  }
});

// Provision database
await railway.provisionDatabase({
  type: 'postgresql',
  name: 'my-app-db'
});
```

**Docs:** [skills/railway-deploy/README.md](./skills/railway-deploy/README.md)

---

### 15. **playwright-scraper-skill**
**Category:** Development & Deployment  
**Complexity:** ⭐⭐⭐⭐  
**Use Case:** Advanced web scraping with anti-bot protection

**Description:**
Playwright-based web scraping with anti-detection, proxy rotation, and session management. Successfully tested on complex sites.

**Key Features:**
- Anti-bot protection bypass
- Proxy rotation
- Session management
- Screenshot capture

**Installation:**
```bash
npm install @hybrid-labs/playwright-scraper-skill
```

**Example:**
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
  proxy: 'rotating'
});

// Take screenshot
await scraper.screenshot({
  url: 'https://example.com',
  path: './screenshot.png',
  fullPage: true
});
```

**Docs:** [skills/playwright-scraper-skill/README.md](./skills/playwright-scraper-skill/README.md)

---

### 16. **vercel**
**Category:** Development & Deployment  
**Complexity:** ⭐⭐  
**Use Case:** Deployment to Vercel platform

**Description:**
Deploy static sites and serverless functions to Vercel. Includes preview deployments and production management.

**Key Features:**
- Instant deployments
- Preview URLs
- Environment variables
- Custom domains

**Installation:**
```bash
npm install @hybrid-labs/vercel
```

**Example:**
```javascript
const vercel = require('@hybrid-labs/vercel');

// Deploy project
const deployment = await vercel.deploy({
  path: './my-site',
  project: 'my-awesome-site',
  env: 'production'
});

// Get preview URL
console.log(deployment.url);
```

**Docs:** [skills/vercel/README.md](./skills/vercel/README.md)

---

## 📊 Business Operations (4 skills)

### 17. **crm-in-a-box**
**Category:** Business Operations  
**Complexity:** ⭐⭐⭐  
**Use Case:** File-based CRM (no SaaS dependency)

**Description:**
Bootstrap and manage a complete CRM using NDJSON files. Contacts, pipeline, and interactions tracked without any SaaS dependency.

**Key Features:**
- Zero SaaS dependency
- NDJSON storage
- Pipeline management
- Interaction tracking

**Installation:**
```bash
npm install @hybrid-labs/crm-in-a-box
```

**Example:**
```javascript
const crm = require('@hybrid-labs/crm-in-a-box');

// Add contact
await crm.addContact({
  name: 'John Doe',
  email: 'john@example.com',
  company: 'Acme Inc',
  stage: 'lead'
});

// Update deal stage
await crm.updateDeal('deal-123', {
  stage: 'negotiation',
  value: 5000
});

// Log interaction
await crm.logInteraction({
  contactId: 'contact-456',
  type: 'call',
  notes: 'Discussed pricing'
});
```

**Docs:** [skills/crm-in-a-box/README.md](./skills/crm-in-a-box/README.md)

---

### 18. **revenue-operations**
**Category:** Business Operations  
**Complexity:** ⭐⭐⭐⭐  
**Use Case:** SaaS revenue optimization & metrics

**Description:**
Analyzes pipeline coverage, tracks forecast accuracy with MAPE, and calculates GTM efficiency metrics for SaaS revenue optimization.

**Key Features:**
- Pipeline coverage analysis
- Forecast accuracy (MAPE)
- GTM efficiency metrics
- Revenue attribution

**Installation:**
```bash
npm install @hybrid-labs/revenue-operations
```

**Example:**
```javascript
const revOps = require('@hybrid-labs/revenue-operations');

// Calculate pipeline coverage
const coverage = await revOps.calculateCoverage({
  quota: 100000,
  pipeline: 350000
});

// Get forecast accuracy
const accuracy = await revOps.getForecastAccuracy({
  actuals: [90, 95, 100],
  forecasts: [85, 90, 98]
});

// GTM efficiency metrics
const metrics = await revOps.getGTMMetrics({
  revenue: 500000,
  spend: 200000
});
```

**Docs:** [skills/revenue-operations/README.md](./skills/revenue-operations/README.md)

---

### 19. **contract-review**
**Category:** Business Operations  
**Complexity:** ⭐⭐⭐⭐  
**Use Case:** Legal contract analysis

**Description:**
Legal contract analysis using CUAD dataset (41 risk categories). Supports NDA, SaaS, M&A, employment, and payment agreements.

**Key Features:**
- 41 risk category detection
- Red flag identification
- Redline suggestions
- Market standard comparison

**Installation:**
```bash
npm install @hybrid-labs/contract-review
```

**Example:**
```javascript
const contractReview = require('@hybrid-labs/contract-review');

// Analyze contract
const analysis = await contractReview.analyze({
  text: contractText,
  type: 'SaaS'
});

// Get red flags
const redFlags = analysis.getRedFlags();

// Get suggested redlines
const redlines = await contractReview.suggestRedlines({
  clause: 'Indemnification',
  riskLevel: 'high'
});
```

**Docs:** [skills/contract-review/README.md](./skills/contract-review/README.md)

---

### 20. **appointment-booking-system**
**Category:** Business Operations  
**Complexity:** ⭐⭐⭐  
**Use Case:** Complete appointment booking & management

**Description:**
Generic appointment booking system for service businesses. Includes booking intake, confirmation, automated reminders, no-show followup, and daily reports.

**Key Features:**
- Booking intake forms
- Automated reminders (24h, 2h)
- No-show tracking
- Daily schedule reports

**Installation:**
```bash
npm install @hybrid-labs/appointment-booking-system
```

**Example:**
```javascript
const booking = require('@hybrid-labs/appointment-booking-system');

// Create booking
const appointment = await booking.create({
  customerName: 'Jane Smith',
  service: 'Consultation',
  dateTime: '2026-03-15T10:00:00Z',
  duration: 60
});

// Send reminders
await booking.sendReminders({
  appointmentId: 'apt-123',
  times: ['24h', '2h']
});

// Get daily schedule
const schedule = await booking.getDailySchedule({
  date: '2026-03-15'
});
```

**Docs:** [skills/appointment-booking-system/README.md](./skills/appointment-booking-system/README.md)

---

## 📊 Summary Table

| # | Skill | Category | Complexity | Installation |
|---|-------|----------|------------|--------------|
| 1 | multi-agent-coordinator | Agent Architecture | ⭐⭐⭐⭐ | `npm install @hybrid-labs/multi-agent-coordinator` |
| 2 | agent-memory-store | Agent Architecture | ⭐⭐⭐ | `npm install @hybrid-labs/agent-memory-store` |
| 3 | memory-tiering | Agent Architecture | ⭐⭐⭐ | `npm install @hybrid-labs/memory-tiering` |
| 4 | token-manager | Agent Architecture | ⭐⭐ | `npm install @hybrid-labs/token-manager` |
| 5 | binance-pro | Crypto & Trading | ⭐⭐⭐⭐⭐ | `npm install @hybrid-labs/binance-pro` |
| 6 | defi-yield-optimizer | Crypto & Trading | ⭐⭐⭐⭐ | `npm install @hybrid-labs/defi-yield-optimizer` |
| 7 | crypto-arbitrage-scanner | Crypto & Trading | ⭐⭐⭐⭐ | `npm install @hybrid-labs/crypto-arbitrage-scanner` |
| 8 | crypto-market-data | Crypto & Trading | ⭐⭐ | `npm install @hybrid-labs/crypto-market-data` |
| 9 | linkedin-lead-generation | Marketing & Outreach | ⭐⭐⭐⭐ | `npm install @hybrid-labs/linkedin-lead-generation` |
| 10 | email-campaigns | Marketing & Outreach | ⭐⭐⭐ | `npm install @hybrid-labs/email-campaigns` |
| 11 | seo-content-writer | Marketing & Outreach | ⭐⭐⭐⭐ | `npm install @hybrid-labs/seo-content-writer` |
| 12 | outreach-sequencer | Marketing & Outreach | ⭐⭐⭐ | `npm install @hybrid-labs/outreach-sequencer` |
| 13 | github-actions-generator | Development & Deployment | ⭐⭐⭐ | `npm install @hybrid-labs/github-actions-generator` |
| 14 | railway-deploy | Development & Deployment | ⭐⭐⭐ | `npm install @hybrid-labs/railway-deploy` |
| 15 | playwright-scraper-skill | Development & Deployment | ⭐⭐⭐⭐ | `npm install @hybrid-labs/playwright-scraper-skill` |
| 16 | vercel | Development & Deployment | ⭐⭐ | `npm install @hybrid-labs/vercel` |
| 17 | crm-in-a-box | Business Operations | ⭐⭐⭐ | `npm install @hybrid-labs/crm-in-a-box` |
| 18 | revenue-operations | Business Operations | ⭐⭐⭐⭐ | `npm install @hybrid-labs/revenue-operations` |
| 19 | contract-review | Business Operations | ⭐⭐⭐⭐ | `npm install @hybrid-labs/contract-review` |
| 20 | appointment-booking-system | Business Operations | ⭐⭐⭐ | `npm install @hybrid-labs/appointment-booking-system` |

---

**Total Skills:** 20  
**Categories:** 5  
**Average Complexity:** ⭐⭐⭐  
**Last Updated:** 2026-03-10
