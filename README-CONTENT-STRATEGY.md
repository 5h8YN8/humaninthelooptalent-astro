# Human in the Loop Talent: AEO Content Strategy Delivery

## What You're Getting

A complete, production-ready AEO (Answer Engine Optimization) content strategy for Human in the Loop Talent. This package includes all 120 unique buyer journey questions mapped to your 3 ICPs, 6 topic clusters, and full Astro implementation.

### Files Included

**1. `src/data/content-strategy.json` (Primary Data File)**
- 120 unique questions for all ICPs and buyer journey stages
- Ready to import into Astro content collection
- Fields: id, question, slug, icp, buyerIntent, pageType, subpath, questionType
- Use this to generate dynamic pages

**2. `CONTENT-STRATEGY-SUMMARY.md` (Strategy Guide)**
- Executive overview and buyer journey analysis
- ICP distribution and pain point alignment
- Page type strategy and URL structure
- Implementation roadmap

**3. `SUBPATH-TAXONOMY.md` (Architecture & Linking)**
- Visual map of /insights/ structure
- Internal linking strategy
- Content calendar by priority (4 phases)
- Success metrics and measurement

**4. `QUICK-REFERENCE.md` (Lookup Guide)**
- Quick statistics and distribution
- The 120 questions at a glance
- How to use each file
- Next steps and checklist

---

## Key Numbers

| Metric | Count |
|--------|-------|
| Total Unique Questions | 120 |
| Topic Clusters (Subpaths) | 6 |
| Pillar Pages | 8 |
| Blog Posts | 42 |
| FAQ Pages | 28 |
| Comparison Pages | 9 |
| Case Studies | 3 |
| Buyer Journey Stages | 6 |
| ICPs Covered | 3 + Cross-ICP |

---

## The 6 Topic Clusters

```
/insights/
├── workforce-architecture/         (14 questions) - ICP-1 primary
├── startup-recruiting/            (30 questions) - ICP-1 primary
├── post-funding-hiring/           (21 questions) - ICP-2 primary
├── ai-native-org-design/          (15 questions) - ICP-3 primary
├── hire-automate-or-super-ic/     (12 questions) - Cross-ICP
└── super-ic/                      (13 questions) - Cross-ICP
```

---

## How to Implement

### Step 1: Import into Astro (5 minutes)

Create content collection in `src/content/config.ts`:

```typescript
import { defineCollection, z } from 'astro:content';

const strategyCollection = defineCollection({
  schema: z.object({
    id: z.string(),
    question: z.string(),
    slug: z.string(),
    icp: z.enum(['1', '2', '3', 'cross-icp']),
    buyerIntent: z.enum(['unaware', 'problem_aware', 'solution_aware', 'product_aware', 'decision', 'retention']),
    pageType: z.enum(['pillar', 'cluster', 'faq', 'blog', 'comparison', 'landing', 'glossary', 'case_study']),
    subpath: z.string(),
    questionType: z.string(),
  }),
});

export const collections = { strategy: strategyCollection };
```

Place `content-strategy.json` in `src/content/strategy/`.

### Step 2: Create Dynamic Route (10 minutes)

Create `src/pages/insights/[subpath]/[slug].astro`:

```astro
---
import { getCollection } from 'astro:content';

const allQuestions = await getCollection('strategy');

export async function getStaticPaths() {
  return allQuestions.map(q => ({
    params: {
      subpath: q.data.subpath,
      slug: q.data.slug
    },
    props: q.data
  }));
}

const { question, icp, buyerIntent, pageType } = Astro.props;
---

<Layout title={question}>
  <h1>{question}</h1>
  {/* Render content based on pageType and ICP */}
</Layout>
```

### Step 3: Generate Content (2-12 weeks)

Use content-strategy.json to drive your content production:

**Phase 1 (Weeks 1-4):** Build 16 pages
- 2 pillar pages (startup-recruiting, workforce-architecture)
- 8 supporting FAQ pages
- Internal linking between pillars and clusters

**Phase 2 (Weeks 5-8):** Build 17 pages
- 2 pillar pages (post-funding-hiring, hire-automate-or-super-ic)
- 12 blog pages
- 3 comparison pages

**Phase 3 (Weeks 9-12):** Build 15 pages
- 2 pillar pages (ai-native-org-design, super-ic)
- 8 blog pages
- 3 case studies

**Phase 4 (Weeks 13+):** Optimize & Expand
- Internal link optimization
- FAQ schema markup
- Video/visual content expansion
- Email nurture sequence

---

## SEO Quick-Start

### Before Building Content

1. **Export all 120 questions** from content-strategy.json
2. **Run SEO analysis** (Ahrefs, SEMrush, or Moz):
   - Search volume for each question
   - Competition level
   - Ranking difficulty
3. **Prioritize by:**
   - High volume + Low competition = Quick wins
   - High volume + Medium competition = Authority builder
   - Low volume = ICP-specific niche content

### Content Strategy

- **Pillar pages** should target primary keywords (high volume, high difficulty)
- **Cluster pages** should target long-tail variants (medium volume, medium difficulty)
- **FAQ pages** should target "People Also Ask" queries (high intent, lower volume)

---

## ICP Targeting Quick Reference

**ICP-1: Seed/Series A Founders**
- Primary: `startup-recruiting`, `workforce-architecture`
- Pain: "I'm hiring reactively and drowning"
- Questions: 26 total
- Key searches: "how to hire first engineer", "early-stage hiring mistakes"

**ICP-2: Series B/C CEOs**
- Primary: `post-funding-hiring`
- Pain: "My org is slowing down as I scale"
- Questions: 29 total
- Key searches: "scaling team structure", "when to hire managers"

**ICP-3: COO/Head of Ops**
- Primary: `ai-native-org-design`
- Pain: "My competitors are leaner because of AI"
- Questions: 19 total
- Key searches: "AI-native org structure", "team automation"

**All ICPs:**
- Shared: `hire-automate-or-super-ic`, `super-ic`
- Core framework questions (27 shared)
- Multi-variant opportunities (19 questions with ICP-specific angles)

---

## Internal Linking Strategy

### Hierarchy
1. Pillar pages (hub authority)
2. Cluster pages (spoke pages)
3. FAQ pages (long-tail capture)

### Cross-Cluster Linking
Link related pages across clusters:
- workforce-architecture ↔ hire-automate-or-super-ic
- ai-native-org-design ↔ post-funding-hiring
- startup-recruiting ↔ workforce-architecture

### ICP Variant Linking
When a question has 2-3 ICP variants:
- Link each variant to the others
- Add context: "See how this applies to Series B CEOs" → link
- Multiply authority across ICPs

---

## Measurement & Success Criteria

### Phase 1 (Weeks 1-4)
- All 120 questions indexed in Google
- Organic impressions > 0 in GSC
- At least 1 pillar page ranking top 20

### Phase 2 (Weeks 5-12)
- Pillar pages ranking top 10 for primary keywords
- FAQ pages appearing in "People Also Ask"
- Organic click-through rate increasing

### Phase 3 (Months 4-6)
- HITL branded searches increasing
- Return visitor rate increasing
- Content pages getting internal links from other sections

### Phase 4 (Months 6-12)
- Qualified leads from `/insights/` pages
- Content cited in cold outreach
- Organic traffic sustaining month-over-month

---

## Frequently Asked Questions

**Q: Should I build all 120 pages at once?**
No. Build in phases: pillar pages first (authority), then clusters (depth), then FAQs (conversion).

**Q: How long should each article be?**
- Pillar: 3,000-5,000 words
- Blog: 1,500-2,500 words
- FAQ: 500-800 words
- Comparison: 1,500-2,000 words

**Q: Should I publish every question as its own page?**
Yes. Each question is a unique search intent. Some questions can be answered together (similar topics), but they deserve separate URLs for SEO.

**Q: How do I know which questions to prioritize?**
1. Run SEO analysis on all 120
2. Look for high volume + low competition
3. Prioritize ICP pain points (pain point alignment = better conversions)
4. Build in phases (quick wins first, then authority, then niche)

**Q: Can I use AI to write these?**
Partially. AI can draft from the question, but every page needs:
- HITL-specific methodology/framework
- Case study examples or customer proof
- ICP-specific context and language
- Original research or unique insight

**Q: What about video content?**
Treat videos as supplementary (not replacement):
- Use for pillar pages (embed YouTube)
- Create short-form content for social
- Build list of "content clips" to repurpose

---

## Support & Next Steps

### You Have Everything You Need To:
1. ✅ Map all buyer journey questions for your ICPs
2. ✅ Structure an Astro content collection
3. ✅ Prioritize content production by impact
4. ✅ Build internal linking strategy
5. ✅ Set up measurement and success criteria

### To Get Started:
1. **Week 1:** Get executive alignment on subpath taxonomy
2. **Week 2:** Import content-strategy.json into Astro
3. **Week 3:** Create content production template
4. **Week 4:** Hire/assign first content author for Phase 1

---

## File Locations

```
/mnt/human-in-the-loop/hitl-astro/
├── src/data/content-strategy.json          ← Primary data file
├── CONTENT-STRATEGY-SUMMARY.md             ← Strategy overview
├── SUBPATH-TAXONOMY.md                     ← Architecture & linking
├── QUICK-REFERENCE.md                      ← Quick lookup
├── README-CONTENT-STRATEGY.md              ← This file
└── [Astro project files...]
```

---

## Contact & Questions

For questions about this strategy or implementation, refer to:
- `QUICK-REFERENCE.md` for quick lookups
- `SUBPATH-TAXONOMY.md` for architecture decisions
- `CONTENT-STRATEGY-SUMMARY.md` for buyer journey analysis

---

**Generated:** April 3, 2026
**For:** Human in the Loop Talent
**Strategy:** AEO (Answer Engine Optimization) Content Taxonomy
**Questions:** 120 unique pages across 6 clusters and 3 ICPs
