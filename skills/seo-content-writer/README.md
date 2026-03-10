# SEO Content Writer

**AI-powered SEO-optimized content generation**

---

## 🎯 Overview

Generate SEO-optimized blog posts, articles, and web content with built-in keyword research, competitor analysis, and on-page optimization. Achieve SEO scores of 80-100.

---

## ✨ Features

- **Keyword Research** - Find high-value keywords
- **Competitor Analysis** - Analyze top-ranking content
- **On-Page SEO** - Optimize headings, meta, density
- **Readability Scoring** - Flesch-Kincaid, grade level
- **Content Briefs** - Structured outlines before writing

---

## 📦 Installation

```bash
npm install @hybrid-labs/seo-content-writer
```

---

## 🚀 Quick Start

```javascript
const seoWriter = require('@hybrid-labs/seo-content-writer');

// Generate article
const article = await seoWriter.write({
  keyword: 'AI automation tools',
  wordCount: 2500,
  tone: 'professional',
  includeFAQ: true,
  includeTableOfContents: true
});

// Optimize for SEO
const optimized = await seoWriter.optimize(article, {
  targetScore: 90,
  keywords: ['automation', 'AI', 'productivity'],
  density: 1.5 // keyword density %
});

console.log(`SEO Score: ${optimized.score}`);
// SEO Score: 92
```

---

## 📊 SEO Factors Optimized

- ✅ Keyword density (1-2%)
- ✅ Heading structure (H1, H2, H3)
- ✅ Meta title & description
- ✅ Internal linking suggestions
- ✅ Image alt text
- ✅ Readability (grade 8-10)
- ✅ Content length (2000+ words)
- ✅ FAQ schema

---

## 🎨 Advanced Usage

### Competitor Analysis

```javascript
const analysis = await seoWriter.analyzeCompetitors({
  keyword: 'best CRM software',
  topN: 10
});

console.log(analysis);
// { avgWordCount: 3500, commonKeywords: [...], gaps: [...] }
```

### Content Brief

```javascript
const brief = await seoWriter.createBrief({
  keyword: 'email marketing automation',
  intent: 'informational',
  audience: 'small business owners'
});
```

---

## 🔧 Configuration

```javascript
await seoWriter.init({
  defaultTone: 'professional',
  minWordCount: 2000,
  targetSEOScore: 85,
  language: 'en'
});
```

---

## 📄 License

MIT License

**Version:** 1.0.0 | **Last Updated:** 2026-03-10
