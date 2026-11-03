---
name: meta-ads
description: "When the user wants help specifically with Meta Ads — Facebook, Instagram, Messenger, or WhatsApp campaigns. Also use when the user mentions 'Advantage+,' 'ASC,' 'Andromeda,' 'CAPI,' 'Conversions API,' 'pixel,' 'lookalikes,' 'Reels ads,' 'CBO,' 'Event Match Quality,' 'creative fatigue,' 'click-to-WhatsApp,' 'anuncios a WhatsApp,' 'campaña de mensajes,' 'conversaciones,' 'costo por conversación,' or 'Ads Manager.' Use this for Meta-specific campaign builds, audits, creative strategy under Andromeda, signal quality, and small-budget chat-sales campaigns (LATAM SMBs). For cross-platform paid strategy, see ads. For ad copy and creative generation at scale, see ad-creative. For pixels/CAPI implementation, see conversion-tracking."
metadata:
  version: 1.1.0
---

# Meta Ads

You are an expert Meta media buyer. Your goal is to build and scale Meta campaigns under the platform's creative-first delivery system, where signal quality and creative diversity have replaced manual audience targeting as the primary levers.

> Platform data in this skill reflects mid-2026, with Andromeda, learning-phase, click-to-WhatsApp and UI updates verified 2026-11-03. Benchmarks shift quarterly — verify against the account's own history before making budget calls.

**Small budget or WhatsApp sales?** If the business sells through chats (click-to-WhatsApp) or spends under ~USD 20/day, read `references/click-to-whatsapp-smb.md` first: the e-commerce structure below does not apply. Before publishing anything in Ads Manager, run the checklist in `references/ads-manager-ui-traps-2026.md`.

## Before Starting

**Check for product marketing context first:**
If `.agents/product-marketing.md` exists (or `.claude/product-marketing.md`), read it before asking questions.

Gather this context (ask if not provided):

1. **Goal**: Purchases, leads, app installs, traffic? Target CPA/ROAS?
2. **Signal setup**: Pixel + Conversions API live? Event Match Quality score?
3. **Creative capacity**: How many net-new creatives can you produce per week?
4. **Budget and account history**

---

## The Andromeda Shift (what changed in 2025–2026)

Meta's Andromeda delivery system (fully rolled out by late 2025) replaced audience-based delivery with **creative-based delivery**: the system reads your creative to predict who should see it. Practical consequences:

- **Interest stacks, detailed targeting, and most lookalikes matter far less.** Broad targeting + strong creative outperforms narrow targeting + average creative.
- **Creative diversity is the new targeting.** Each conceptually distinct ad reaches a different pocket of users. Recommendation: 10–20 conceptually distinct actives per campaign at scale; **3–5 truly distinct concepts per ad set for SMB budgets** (different hooks, formats, angles — not 10 crops of the same video). Meta officially groups ads that look or feel alike and treats copy/CTA-only changes on the same visual as iteration, not diversification; the same video localized per city is one concept ([Demystifying creative diversification](https://www.facebook.com/business/news/demystifying-creative-diversification), 2025-12-16). Check "Similitud creativa" / "Fatiga creativa" in Account insights when available.
- **Learning phase**: ~50 optimization events in 7 days ([help 112167992830700](https://www.facebook.com/business/help/112167992830700)). Max cost per result that still exits learning = daily budget × 7 / 50. If the target event cannot reach that, optimize for a higher-volume event (conversations before leads, leads before purchases).
- **Second-generation Andromeda** (Oct 2026): per-user "expert" models, >1B ads/second evaluated; Meta attributes +2.4% Facebook conversions since 2025 ([engineering.fb.com, 2026-10-28](https://engineering.fb.com/2026/10/28/ml-applications/meta-andromeda-next-gen-ads-retrieval-gpu-co-design/)).
- **Signal quality gates everything.** Weak conversion signal slows Andromeda's learning and inflates CPMs. Run Pixel + CAPI simultaneously; keep Event Match Quality ≥ 7.
- **Consolidation wins.** Fewer campaigns with bigger budgets beat fragmented account structures.

## Campaign Structure (2026 default)

```
Account
├── Advantage+ Sales (ASC) — primary engine, 60–80% of budget
│     └── 10–20 conceptually distinct creatives, refresh 2–3/week
├── Manual sales campaign — testing lab (new concepts, 10–20% of budget)
│     └── Winners graduate into ASC
└── Retargeting/retention (optional, small) — catalog + offer-led
```

- **Advantage+ Shopping** delivers ~17–32% lower CPA than equivalent manual campaigns on average — make it the default for e-commerce, not the experiment.
- Lead gen: Advantage+ Leads or manual + broad targeting; instant forms with higher-intent qualifying questions beat short forms on lead quality.
- Brand safety/exclusions are moving to **account controls by objective**; manual placements are being removed at ad set level gradually ([help 1546753450586085](https://www.facebook.com/business/help/1546753450586085)).

### SMB / chat-sales structure (under ~USD 20/day)

```
Account
└── 1 campaign per business objective (e.g. national WhatsApp sales)
      └── 1 ad set per service area — Advantage+ audience + Advantage+ placements
            └── 3–5 truly distinct concepts, each with its own predefined WhatsApp message
Optional, only with audience volume: 1 remarketing ad set (ad set budget, Advantage+ audience OFF)
```

- Optimize for **conversations** first; move to **leads via messages** once lead events flow through CAPI for messaging (Meta reports ~24% lower cost per lead). Purchases via messages only with dozens of attributed sales per week.
- Ad ceiling anchored on **cost per sale**, not cost per chat. Judge ads on CRM sales, not chat volume.
- Full playbook: `references/click-to-whatsapp-smb.md`.

## Creative Specs & Rules (2026)

| Item | Spec |
|------|------|
| Primary format | 9:16 vertical (≈90% of Meta inventory is vertical) |
| Secondary | 4:5 for Feed |
| Safe zone (9:16, unified March 2026) | Keep critical elements out of: top 14%, bottom 20–35%, sides 6% |
| Universal trick | Put all critical content in a centered 1080×1080 square on the 1080×1920 canvas |
| Hook | First 3 seconds decide scroll-stop — strongest claim/visual before any branding |
| Sound | Design for sound ON: Meta reports 75%+ of Instagram Reels views are with sound (the "85% muted" stat is from 2016 feed video). Still burn in captions (accessibility + muted viewers); voice + music together lift purchase intent |
| Feed fallback | A 9:16-only video errors on Instagram Feed; add a 4:5 version inside the same ad (blurred background, no text crop) |
| Refresh cadence | 2–3 net-new creatives weekly; expect fatigue in 7–14 days at scale |

**Advantage+ Creative enhancements**: Meta auto-generates variants (text, music, aspect ratios, visual tweaks). Review each enhancement — turn off ones that break brand (e.g., auto-music on a B2B demo). Test AI-generated backgrounds/variations rather than accepting them by default. Under Meta's updated Commercial Terms (reported effective 2026-11-20) the advertiser carries responsibility for AI-generated ad content: keep text-writing and product-altering enhancements OFF unless reviewed; video touch-ups and effects OFF when the video has burned-in text.

## Benchmarks (mid-2026, medians — verify per vertical)

| Metric | Value | Trend |
|--------|-------|-------|
| CPM (all objectives) | ~$14.19 | +20% YoY |
| CPM (sales campaigns) | $20–$30 | Strong creative keeps it ~$25; weak creative spikes >$50 |
| CPC (Facebook, all) | ~$1.72 | Instagram runs higher ($1.83–$3.35) |
| CPA (cross-industry median) | ~$38 | +8.5% YoY |
| ROAS (sales median) | ~2.8 | |
| CVR range | 0.4% (hardware/auto) – 14% (fitness) | Vertical-dependent |

CPC floor verticals: apparel (~$0.45), food & beverage (~$0.52). Ceiling: finance/insurance (~$3.77).

These are US-centric USD medians. For LATAM chat-sales accounts use the COP section in `references/benchmarks-2026.md` and, above all, the account's own history.

---

## Optimization Playbook

**Daily** (only if spend > $500/day): check spend pacing and delivery errors. Do NOT react to single-day CPA noise.

**Weekly**:
1. Kill creatives with frequency > 4 and declining CTR, or flagged "Fatiga creativa" / "Creativo limitado" (fatigue)
2. Ship 2–3 new concepts into the testing campaign
3. Graduate test winners (CPA at or below target over ≥ 3 days) into ASC
4. Check Event Match Quality hasn't degraded

**Scaling rules**:
- Budget increases ≤ 20% per day (bigger jumps reset learning)
- Scale by adding creative concepts, not by duplicating campaigns
- Watch CPM as the canary: a CPM spike with stable CTR = auction pressure; with falling CTR = creative fatigue

## Audit Checklist

1. Pixel + CAPI both firing, deduplicated? EMQ ≥ 7?
2. Account structure: consolidated or fragmented into learning-starved ad sets?
3. Creative count + diversity in main campaign (10+ distinct concepts?)
4. Frequency and fatigue: actives with frequency > 4?
5. % budget on Advantage+ vs manual — justify any manual-heavy split
6. Placement opt-outs (Advantage+ placements usually wins; exclusions need a reason)
7. Attribution settings: 7-day click / 1-day view as default; compare in-platform vs blended/MMM numbers
8. Creative enhancements: audited or blindly accepted?
9. Click-to-WhatsApp: one predefined message per ad? Sales measured in the CRM per ad? Chat close rate and human hand-off checked before blaming the media buy? WhatsApp number linked as Business/API (not personal)? See `references/click-to-whatsapp-smb.md`.

## Anti-Patterns

- ❌ Narrow interest-stacked audiences "to control delivery" (Andromeda ignores you and charges you for it)
- ❌ 10 variants of the same creative concept counted as "creative diversity"
- ❌ Duplicating campaigns to scale (splits signal, restarts learning)
- ❌ Running Pixel only, without CAPI (signal loss inflates CPA)
- ❌ Judging performance on 1-day windows of in-platform attribution alone
- ❌ Pausing/reactivating campaigns repeatedly (each cycle resets learning phase)
- ❌ Judging a click-to-WhatsApp ad by chat volume: the ad with most chats often sells less
- ❌ Following the "Cuenta de WhatsApp Business obligatoria" migration from the phone for a number that is on the WhatsApp Cloud API
- ❌ Mentioning credit/financing in the ad copy (triggers the financial special category; offer it in the chat)

## Output Format

When building campaigns, deliver:
1. Campaign structure with budget split
2. Creative brief matrix: 10+ concepts across hooks (problem / social proof / demo / UGC / offer) × formats (video / static / carousel)
3. Signal setup checklist (Pixel + CAPI + EMQ)
4. Testing → graduation criteria
5. 30-day scaling plan with kill/scale thresholds

## References

- For a deep account audit with 250+ weighted checks, use the **claude-ads** plugin (ads-meta, ads-audit) if installed
- For cross-platform budget allocation, see the **ads** skill
- For bulk creative generation and UGC briefs, see the **ad-creative** skill
- `references/benchmarks-2026.md` — detailed benchmark tables with sources (USD medians + LATAM COP section)
- `references/click-to-whatsapp-smb.md` — small-budget chat-sales playbook: objective by budget, structure, measuring by sale, CAPI for messaging, WhatsApp number checks, Colombia context
- `references/ads-manager-ui-traps-2026.md` — pre-publish checklist of Ads Manager defaults that silently change what you publish
- For pixels, CAPI and server-side implementation, see the **conversion-tracking** skill
