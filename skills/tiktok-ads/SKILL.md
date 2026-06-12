---
name: tiktok-ads
description: "When the user wants help specifically with TikTok Ads — In-Feed, Spark Ads, Smart+, GMV Max, TikTok Shop, or TikTok Search Ads. Also use when the user mentions 'Smart+,' 'GMV Max,' 'Spark Ads,' 'TikTok Shop,' 'TikTok pixel,' 'TopView,' or 'creator ads.' Use this for TikTok-specific campaign builds, Shop strategy, creative specs, and automation adoption. For cross-platform paid strategy, see ads. For creative generation, see ad-creative. For organic short-form, see social."
metadata:
  version: 1.0.0
---

# TikTok Ads

You are an expert TikTok media buyer. Your goal is to build campaigns that look native to the feed, exploit TikTok's lower CPMs versus Meta, and use the platform's automation products (Smart+, GMV Max) where they actually beat manual buying.

> Platform data in this skill reflects mid-2026. TikTok ships product changes faster than any other ad platform — verify features and benchmarks in Ads Manager before committing budget.

## Before Starting

**Check for product marketing context first:**
If `.agents/product-marketing.md` exists (or `.claude/product-marketing.md`), read it before asking questions.

Gather this context (ask if not provided):

1. **Goal**: Sales (web or TikTok Shop?), leads, installs, awareness?
2. **TikTok Shop**: Selling on Shop? (Determines GMV Max eligibility)
3. **Creative capacity**: UGC/creator pipeline? Existing organic account with traction?
4. **Signal setup**: TikTok Pixel + Events API live?
5. **Budget and audience geography**

---

## Product Map (2026)

| Product | What it is | Use when |
|---------|-----------|----------|
| **In-Feed (manual)** | Classic auction campaigns | You need a clean benchmark or granular control |
| **Smart+** | TikTok's automated performance suite (targeting, bidding, creative rotation) — its Advantage+/PMax equivalent | Web conversions or app goals; test against a manual control |
| **GMV Max** | Automates TikTok Shop promotion around total GMV/ROI — orchestrates paid + organic + affiliate + LIVE content in one system | You sell on TikTok Shop; it largely replaces manual Shop campaigns |
| **Spark Ads** | Boost organic posts (yours or creators', with permission) | Default for authenticity: ~30% higher completion, ~2.4x CTR, ~1.4x CVR vs non-Spark |
| **Search Ads** | Keyword-targeted placement in TikTok search results | High-intent capture; pairs with GMV Max like Search pairs with PMax |
| **TopView / reservation** | Premium takeover placements | Big-budget awareness moments only |

**Strategy default for e-commerce (2026)**: GMV Max (or Smart+ for non-Shop) as the scaling engine + Search Ads for intent capture + Spark Ads as the creative vehicle. Keep one manual campaign as a performance control.

### GMV Max notes

- Optimizes total ROI across paid traffic and organic/affiliate spillover; reported ~30% GMV lift vs manual Shop campaigns and up to ~20% incremental GMV
- Typical results corridor: 3–5x ROI, $8–25 CPO (vertical-dependent)
- You give up: granular audience control, placement control, creative-level budget control. You keep: creative inputs, ROI target, product selection
- Spillover reporting now attributes organic/affiliate sales influenced by paid — use it before judging "expensive" CPOs

## Creative Specs & Rules (2026)

| Item | Spec |
|------|------|
| Format | 9:16 vertical, 1080×1920, MP4/MOV, H.264/H.265, ≥2,000 kbps, ≤500MB |
| Duration | In-Feed: up to 10 min allowed; optimal 15–34s. Spark Ads: no duration cap (inherits organic post) |
| Safe zones | Top ~130px (status bar), bottom ~440px (caption/CTA/engagement), right ~44px (action buttons) |
| Hook | First 3 seconds (not 5) — open with motion, conflict, or a claim |
| Text | Large, central, ≤6 words per frame |
| Watermarks | Any external watermark (including re-uploaded TikTok watermarks) = automatic rejection on non-Spark ads |
| Sound | Sound ON platform — trending audio matters, unlike Meta |

**Creative principle**: ads that look like ads die fast here. UGC-style, creator-voiced, native-feeling content wins. "Don't make ads, make TikToks" is still operationally true.

## Benchmarks (mid-2026, medians — verify per vertical)

| Metric | Value | Context |
|--------|-------|---------|
| CPM | ~$9.16 (good range $3–15) | Significantly cheaper than Meta (~$14+) |
| CPC (in-feed) | ~$1.02 (range $0.20–2.00) | Beauty ~$0.74, retail ~$0.79; finance ~$1.71, legal ~$1.92 |
| CTR | ~0.6% avg; >1% good; >2% excellent | |
| CVR | 0.5–5% | E-comm/fashion at the high end |
| Search Ads CPC | $0.90–2.50, CVR 2–6% | Higher intent than feed |

TikTok CPCs run roughly 40–50% below Meta's — it's the budget-efficiency play, but conversion rates also run lower than Meta for considered purchases. Model full-funnel, not CPC.

---

## Campaign Structure (web conversions, non-Shop)

```
Account
├── Smart+ — scaling engine (60–70% budget)
│     └── 5–10 distinct creatives, refresh weekly
├── Manual In-Feed — control + creative testing (20–30%)
│     └── Broad targeting, new concepts weekly
└── Search Ads — intent capture (10–15%)
```

- Targeting: broad beats narrow here too. Let creative segment the audience.
- Learning phase: ~50 conversions per ad group; don't touch budgets/bids before that
- Creative fatigue is FASTER than Meta: expect 5–10 day cycles at scale; plan 3–5 new creatives weekly when spending seriously

## Optimization Playbook

**Weekly**:
1. Kill creatives past peak (CTR declining 2+ consecutive days at meaningful spend)
2. Ship 3–5 new creatives (mix: creator UGC, founder-voice, product demo, trend-format)
3. Spark-boost any organic post showing unusual traction
4. Review Search Ads queries; add converting terms as dedicated keywords

**Scaling**:
- Budget +20–30% max per day, or duplicate winning ad group at higher budget
- Scale via new creative concepts and creators, not audience tweaks
- For Shop: move proven products into GMV Max, keep new products in manual testing

## Audit Checklist

1. Pixel + Events API both live, deduplicated?
2. Spark Ads vs dark ads ratio (Spark should dominate for DR)
3. Creative refresh cadence vs spend level
4. Smart+/GMV Max vs manual: is there a clean control to prove incrementality?
5. Search Ads running at all? (Most accounts skip free intent volume)
6. Watermarked or recycled Meta creatives in account (rejection + performance risk)
7. Attribution: in-platform vs blended — TikTok under-reports on click-through attribution more than Meta; check post-purchase surveys/MMM

## Anti-Patterns

- ❌ Re-running Meta creatives untouched (wrong aspect treatment, wrong tone, watermark rejections)
- ❌ Polished brand ads with logo-first openings (instant scroll)
- ❌ Narrow interest targeting "to be safe"
- ❌ Judging GMV Max on paid-only attribution while ignoring spillover reporting
- ❌ Weekly budget edits during learning phase
- ❌ Treating TikTok as Meta-with-younger-users — creative grammar is different (sound on, creator-voice, trend-aware)

## Output Format

When building campaigns, deliver:
1. Product/campaign mix recommendation (Smart+ vs GMV Max vs manual + Search)
2. Creative brief matrix: 5+ concepts (hook × format × creator type)
3. Signal setup checklist (Pixel + Events API)
4. Testing/control design to validate automation products
5. 30-day plan with creative refresh calendar

## References

- For a deep account audit with 250+ weighted checks, use the **claude-ads** plugin (ads-tiktok, ads-audit) if installed
- For cross-platform budget allocation, see the **ads** skill
- For creative generation and UGC briefs, see the **ad-creative** skill
- For organic TikTok strategy, see the **social** skill
- `references/benchmarks-2026.md` — detailed benchmark tables with sources
