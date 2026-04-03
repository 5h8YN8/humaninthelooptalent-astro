# HITL AEO Content Strategy - Quick Reference

## What You Have

**3 Complete Documents:**

1. **content-strategy.json** (37KB, 120 questions)
   - Location: `/src/data/content-strategy.json`
   - Format: Ready for Astro collection
   - Fields: id, question, slug, icp, buyerIntent, pageType, subpath, questionType
   - Use this to: Generate dynamic Astro pages, populate CMS, plan content calendar

2. **CONTENT-STRATEGY-SUMMARY.md**
   - High-level overview and strategy
   - Buyer journey stage breakdown
   - Page type distribution
   - ICP distribution
   - Implementation roadmap

3. **SUBPATH-TAXONOMY.md**
   - Visual map of /insights/ structure
   - Internal linking strategy
   - Content calendar by priority
   - Success metrics and phases

---

## The 120 Questions at a Glance

### Distribution by ICP

```
Seed/Series A Founders (ICP-1):    26 questions
Series B/C CEOs (ICP-2):           29 questions
COO/Head of Ops (ICP-3):           19 questions
Cross-ICP (All 3):                 27 questions
Multi-ICP variants:                19 questions
───────────────────────────────────────────────
TOTAL:                            120 questions
```

### Distribution by Buyer Journey Stage

```
Unaware:           15 questions   (problems discovered)
Problem Aware:     22 questions   (root cause understood)
Solution Aware:    38 questions   (categories explored)
Product Aware:     20 questions   (features evaluated)
Decision:          16 questions   (confidence built)
Retention:          9 questions   (ongoing success)
───────────────────────────────────────────
TOTAL:            120 questions
```

### Distribution by Page Type

```
Blog:              42 questions   (long-form, SEO-friendly)
Pillar:             8 questions   (high-authority hubs)
FAQ:               28 questions   (quick answers)
Comparison:         9 questions   (head-to-head analysis)
Cluster:            4 questions   (detailed supporting)
Case Study:         3 questions   (proof and validation)
Landing:            3 questions   (product-specific)
Glossary:          15 questions   (future expansion)
───────────────────────────────────────────
TOTAL:            120 questions
```

---

## The 6 Topic Clusters (Subpaths)

### 1. Startup Recruiting (30 questions)
Primary ICP: Seed/Series A Founders
Authority: End-to-end hiring playbook for early-stage teams
Example Questions:
- How do I stop hiring reactively and start hiring strategically?
- How do I hire my first engineer as a founder?
- How do I recruit when I can't offer top market salary?

### 2. Post-Funding Hiring (21 questions)
Primary ICP: Series B/C CEOs
Authority: Scaling org structure after capital injections
Example Questions:
- How do I scale from a founder-led team to a structured org?
- What does a healthy org structure look like at Series B?
- How do I build a management layer without killing speed?

### 3. Workforce Architecture (14 questions)
Primary ICP: Seed/Series A Founders
Authority: Foundational framework for team scaling
Example Questions:
- What is workforce architecture and why does it matter for startups?
- What roles create the most leverage in a small startup?
- How many people do I actually need to build a product?

### 4. AI-Native Org Design (15 questions)
Primary ICP: COO/Head of Operations
Authority: Structuring teams for AI leverage
Example Questions:
- How do AI-native companies structure their teams differently?
- How should I structure teams for maximum AI leverage?
- What team composition makes an AI-native startup actually AI-native?

### 5. Hire vs Automate vs Super IC (12 questions)
Primary ICP: Cross-ICP (all 3)
Authority: THE core decision framework
Example Questions:
- How do I decide between hiring, automating, or finding a super IC?
- When should I automate vs. hire?
- Can I really run a startup with just three people and a lot of automation?

### 6. Super IC Archetype (13 questions)
Primary ICP: Cross-ICP (all 3)
Authority: Defining the super IC and when to build around them
Example Questions:
- What is a super IC and should I hire one?
- How much should I pay a super IC?
- What happens when your super IC leaves?

---

## How to Use This

### For Content Development
1. Open `content-strategy.json`
2. Filter by `subpath` to see all questions in a cluster
3. Filter by `buyerIntent` stage to plan content calendar
4. Use `slug` as your Astro page filename
5. Use `question` as your page title/H1

### For SEO/SEM
1. Take all 120 questions
2. Run through SEO tools (Ahrefs, SEMrush, Moz) to get search volume
3. Prioritize high-intent, high-volume questions first
4. Use clusters with highest aggregate volume as Phase 1

### For Internal Linking
1. Use `icp` field to identify cross-ICP variants
2. Link variant pages to each other ("See how this applies to Series B CEOs" → link)
3. Link cluster pages back to pillar pages
4. Link related pages across clusters (workforce-architecture ↔ hire-automate-or-super-ic)

### For Astro Integration
```astro
// Example: /src/pages/insights/[subpath]/[slug].astro
import { getCollection } from 'astro:content';

export async function getStaticPaths() {
  const questions = await getCollection('content-strategy');
  return questions.map(q => ({
    params: {
      subpath: q.data.subpath,
      slug: q.data.slug
    },
    props: { question: q }
  }));
}

const { question } = Astro.props;
```

---

## The 8 Pillar Pages (Content Hubs to Build First)

These are your highest-authority pages. Build these first:

1. **Workforce Architecture** — What framework should every startup use to scale teams?
2. **AI-Native Org Design** — How do you structure teams for AI leverage?
3. **Super IC Archetype** — What is the super IC and how is it different?
4. **Hire vs Automate vs Super IC** — The core decision framework
5. **Post-Funding Org Design** — How do you scale from founder-led to structured?
6. **Startup Recruiting 101** — The playbook for building early teams
7. **Leverage in Org Design** (Cross-ICP) — Core framework tying it together
8. **AI-Era Team Building** (Cross-ICP) — The future of team structure

---

## Content Calendar (Recommended Priority)

### Phase 1: Weeks 1-4 (Foundation)
- ✅ Build pillar pages: `startup-recruiting`, `workforce-architecture`
- ✅ Create 8 supporting FAQ pages
- ✅ Internal linking between pillar ↔ cluster

### Phase 2: Weeks 5-8 (Authority)
- ✅ Build pillar pages: `post-funding-hiring`, `hire-automate-or-super-ic`
- ✅ Create 6 blog pages per pillar
- ✅ Add comparison pages

### Phase 3: Weeks 9-12 (Specialization)
- ✅ Build pillar pages: `ai-native-org-design`, `super-ic`
- ✅ Create case studies and proof pages
- ✅ Add video/visual content

### Phase 4: Weeks 13-16 (Optimization)
- ✅ Internal linking optimization across all clusters
- ✅ Add FAQ schema markup
- ✅ Create FAQ index page
- ✅ Launch email nurture sequence based on content

---

## Key Insights from This Strategy

### Why This Works for HITL

1. **Pain Point Alignment** (120 questions mapped to 5 cross-ICP pain points)
   - "I don't know which roles create maximum leverage" → 16 questions
   - "Hiring reactively rather than architecturally" → 22 questions
   - "No framework for hire vs automate vs super-IC" → 12 questions
   - "Being benchmarked against leaner AI-native peers" → 15 questions
   - "Legacy HR isn't equipped for AI-native team design" → 18 questions

2. **ICP-Specific Authority** (Each subpath targets a primary ICP)
   - Seed/Series A sees talent acquisition as core problem → startup-recruiting, workforce-architecture
   - Series B/C sees scaling/management as core problem → post-funding-hiring
   - COO/Ops sees AI integration as core problem → ai-native-org-design

3. **Cross-ICP Differentiation** (27 shared questions create variants)
   - "When should I hire my first manager?" has 3 variants:
     - Seed founder asking: "Should I hire a manager at 5 people?"
     - Series B CEO asking: "When do I hire my second layer of managers?"
     - COO asking: "How do I build management without losing ops velocity?"
   - All 3 link to each other, multiplying authority

4. **Buyer Journey Depth** (6 stages ensure full coverage)
   - Awareness: "Why am I hiring reactively?" → Blog
   - Problem: "How do I identify root cause?" → Blog + FAQ
   - Solution: "What are my options?" → Comparison page
   - Product: "How does HITL's framework work?" → Pillar page
   - Decision: "How do I implement this?" → How-to + Case study
   - Retention: "How do I sustain this?" → Blog + ongoing content

---

## Next Steps

1. **Get Executive Buy-In**
   - Share this doc with HITL leadership
   - Get agreement on subpath taxonomy
   - Confirm Phase 1 priorities

2. **Set Up Astro Collection**
   - Import `content-strategy.json` into Astro
   - Create dynamic page template: `/src/pages/insights/[subpath]/[slug].astro`
   - Set up collection schema in `astro.config.ts`

3. **Create Content Brief Template**
   - Use JSON data to auto-generate content briefs
   - Each brief includes: question, icp, buyer intent, page type, target word count
   - Assign writers based on cluster specialization

4. **Plan Content Production**
   - Estimate: 1-2 pages per writer per week
   - Phase 1: ~20 pages (startup-recruiting + workforce-architecture pillars + FAQs)
   - Timeline: 10-15 weeks for all 120 pages at 2 pages/week

5. **Set Up Measurement**
   - Google Search Console tracking by subpath
   - Organic traffic dashboard
   - Lead source attribution
   - Content-to-demo conversion rate

---

## Files Reference

| File | Size | Purpose |
|------|------|---------|
| `content-strategy.json` | 37KB | Master data (use in Astro) |
| `CONTENT-STRATEGY-SUMMARY.md` | 13KB | Strategy & buyer journey overview |
| `SUBPATH-TAXONOMY.md` | 12KB | Visual structure & linking strategy |
| `QUICK-REFERENCE.md` | This file | Quick lookup guide |

---

## Questions? Check These Sections

**"How many pages should I make?"** → 120 (you have them all)

**"Which should I make first?"** → See Content Calendar section

**"How do I decide the order?"** → By search volume (use SEO tool on 120 questions)

**"How do ICP variants work?"** → See "Cross-ICP Differentiation" section

**"How should pages link to each other?"** → See SUBPATH-TAXONOMY.md Internal Linking Strategy

**"What's the tone/voice?"** → Each question should sound like how someone would ask ChatGPT/Perplexity
