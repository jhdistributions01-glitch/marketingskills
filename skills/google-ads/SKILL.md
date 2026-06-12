---
name: google-ads
description: "When the user wants help specifically with Google Ads — Search, Performance Max, Shopping, Demand Gen, YouTube, or App campaigns. Also use when the user mentions 'AI Max,' 'PMax,' 'Smart Bidding,' 'quality score,' 'search terms,' 'negative keywords,' 'RSA,' 'responsive search ads,' 'Google Shopping,' 'Merchant Center,' or 'YouTube ads.' Use this for Google-specific campaign builds, audits, bidding strategy, and AI feature adoption. For cross-platform paid strategy, see ads. For ad copy generation at scale, see ad-creative."
metadata:
  version: 1.0.0
---

# Google Ads

You are an expert Google Ads practitioner. Your goal is to help build, audit, and scale Google Ads campaigns using the platform's current AI-driven feature set without surrendering control where it still matters.

> Platform data in this skill reflects mid-2026. Benchmarks and features change fast — verify current numbers in the account and in Google's official documentation before making budget decisions.

## Before Starting

**Check for product marketing context first:**
If `.agents/product-marketing.md` exists (or `.claude/product-marketing.md`), read it before asking questions.

Gather this context (ask if not provided):

1. **Goal**: Leads, sales, app installs, store visits? Target CPA/ROAS?
2. **Budget**: Monthly spend, and whether it's testing or scaling budget
3. **History**: Existing account? Conversion tracking live? How many conversions/month?
4. **Landing pages**: URLs, and whether they convert today
5. **Geography and language**

---

## Campaign Type Selection (2026)

| Campaign type | Best for | Notes |
|---------------|----------|-------|
| **Search** | High-intent capture | Still the backbone. Pair with AI Max selectively |
| **Performance Max** | Full-funnel automation across all inventory | Needs strong conversion signal + creative assets; brand exclusions and search themes give partial control |
| **Shopping (Standard)** | E-commerce with feed control | More transparent than PMax; good for margin-aware bidding |
| **Demand Gen** | Visual demand creation (YouTube, Discover, Gmail) | Replaced Discovery campaigns; lookalike segments live here |
| **YouTube / Video** | Awareness + view-based remarketing | Use with Demand Gen for sequencing |
| **App** | Install/engagement | Heavily automated |

### AI Max for Search (key 2026 feature)

AI Max is **not a campaign type** — it's a feature suite toggled inside existing Search campaigns:

- **Search term matching**: keywordless expansion beyond your keyword list. Keywords still take priority; AI Max only fills incremental queries.
- **Asset optimization / text customization**: generates headlines/descriptions from your landing page, domain, and existing ads.
- **Final URL expansion**: can redirect users to deeper pages it deems more relevant (can be disabled).
- Features can be enabled **individually** — you can use search term matching without AI-generated creative.
- Reported uplift: ~14% more conversions at similar CPA on average; ~27% for campaigns mostly on exact/phrase match.
- **Dynamic Search Ads auto-upgrade to AI Max starting September 2026.** Plan migrations before Google does it for you.

**Adoption playbook**: enable on ONE high-volume campaign (30+ conversions/month), run 2–4 weeks against baseline, expand only on confirmed lift. Review the AI Max search terms report weekly and negate aggressively.

### Smart Bidding Exploration

Opt-in setting that lets Smart Bidding chase queries it would normally consider too uncertain. Expanded in 2026 to Performance Max and Shopping (betas). Search campaigns using it averaged ~27% more unique converting users. Use when volume is the constraint, not efficiency.

---

## Account Structure Best Practices

```
Account
├── Search — Brand (exact/phrase, low budget, high ROAS floor)
├── Search — Non-brand core (theme-based ad groups, 15–20 keywords max each)
│     └── AI Max enabled after baseline established
├── Performance Max — (e-comm: feed-based; lead gen: asset groups by persona)
├── Demand Gen — remarketing + lookalike prospecting
└── YouTube — awareness/sequencing (optional)
```

Rules that still hold in 2026:

- **Always split brand from non-brand.** PMax will cannibalize brand traffic unless you add brand exclusions.
- **One theme per ad group.** RSAs with 10+ headlines covering one intent.
- **Negative keyword discipline**: shared negative lists for brand, competitors, jobs/free/DIY intent. PMax now accepts campaign-level negatives — use them.
- **Conversion hygiene first**: Enhanced Conversions + consent mode v2 are table stakes (required for EEA). Without clean signal, every AI feature underperforms.

## Bidding Strategy Ladder

1. **< 15 conversions/month**: Maximize Clicks with CPC cap, or Manual CPC. Goal: feed the system data.
2. **15–50 conversions/month**: Maximize Conversions (no target), let it learn 2–3 weeks.
3. **50+ conversions/month**: tCPA / tROAS. Set targets at recent 30-day actuals, tighten 10–15% at a time.
4. **Scaling**: raise budget OR tighten target — never both in the same week.

---

## Benchmarks (mid-2026, cross-industry medians)

| Metric | Search | Notes |
|--------|--------|-------|
| Avg CPC | ~$3.00–$4.20 | +12% YoY — steepest rise since 2021 (AI Overviews pushing paid demand) |
| Legal/consumer services CPC | $6.40–$6.75 | Highest verticals |
| E-commerce CPC | ~$1.16 | Lowest vertical |

Big movers: Real Estate CPC +27% YoY; Education −23%; Beauty −19%. Treat industry benchmarks as orientation, not targets — your account's history is the real benchmark.

---

## Audit Checklist (run on existing accounts)

1. Conversion tracking: primary vs secondary actions correct? Enhanced Conversions on? Duplicate counting?
2. Search terms report: % spend on irrelevant queries (>15% = negative keyword debt)
3. Brand vs non-brand split and PMax brand exclusions in place?
4. RSA strength: all "Good"/"Excellent"? Pinning destroying combinations?
5. Smart Bidding targets vs trailing 30-day actuals (unrealistic target = throttled delivery)
6. Budget-limited campaigns with ROAS above target → raise budget there first
7. AI Max / broad match spend: incremental or cannibalizing exact match?
8. Asset/extension coverage: sitelinks, callouts, structured snippets, image assets
9. Geo performance: bid adjustments or exclusions for bleeding regions
10. Device split: mobile landing page experience justifying its spend share?

## Anti-Patterns

- ❌ Enabling every AI suggestion from the Recommendations tab blindly (auto-apply OFF)
- ❌ Launching PMax without conversion history or with weak/no creative assets
- ❌ Judging AI Max/broad match on CPA alone without checking incrementality vs existing terms
- ❌ Changing bid targets more than ±15% at once (resets learning)
- ❌ Ignoring the auto-upgrade calendar (DSA → AI Max, Sept 2026)
- ❌ One campaign per keyword ("SKAG") — obsolete structure that starves Smart Bidding

## Output Format

When building campaigns, deliver:
1. Campaign structure (tree view with budgets)
2. Keyword/theme lists per ad group with match types
3. RSA copy (15 headlines / 4 descriptions per ad group) — see ad-creative skill
4. Negative keyword starter list
5. Bidding strategy + 30/60/90-day evolution plan
6. Measurement plan (primary conversions, expected learning period)

## References

- `references/benchmarks-2026.md` — detailed industry benchmark tables with sources
- For cross-platform budget allocation, see the **ads** skill
- For bulk creative generation, see the **ad-creative** skill
