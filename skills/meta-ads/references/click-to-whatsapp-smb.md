# Click-to-WhatsApp for SMBs (low budget, LATAM)

Last verified: 2026-11-03. Review by: 2027-02-01 (Meta changes this surface often).
Applies to: physical stores and service businesses that sell through WhatsApp chats,
with roughly USD 5-20/day (COP 20.000-80.000/day). Written from Zentra's own accounts
(Equipos360, TechBridge, Zeni clients) plus Meta's official docs. Evidence labels:
**[Oficial]** Meta says it, **[Tercero]** reputable third party, **[Propio]** measured in
our own accounts, **[Inferencia]** our reasoning.

## 1. Objective and optimization by budget

The learning phase needs ~50 optimization events in 7 days **[Oficial]**
(facebook.com/business/help/112167992830700). Max cost per result that still exits learning:

```
max_cost_per_result = daily_budget × 7 / 50
COP 20.000/day → ~COP 2.800 per result      COP 60.000/day → ~COP 8.400
```

| Situation | Objective → performance goal |
|---|---|
| Starting, no messaging CAPI | Engagement (Interacción) → **Maximize conversations** (conversaciones), WhatsApp destination |
| Business sends lead events through CAPI for messaging | Leads → **leads via messages**. Meta reports ~24% lower cost per lead vs optimizing for conversations **[Oficial]** (help 575610661605746, 1214599109289826) |
| Purchases via messages | Only with dozens of attributed sales per week. 26 purchases/month did NOT exit learning **[Propio, Equipos360 2026-11]** |

Do not take the "Maximize purchases through messages" recommendation that Ads Manager pre-selects
unless the volume above exists.

## 2. Structure for small budgets

- **One campaign, one ad set per business objective and service area.** Do not split by age,
  interest, placement or language **[Oficial]** (help 2720085414702598; Performance 5).
- **3 to 5 truly different concepts** per ad set (different persona, problem or format). Meta groups
  ads that look or feel alike and treats copy/CTA changes on the same visual as iteration, not
  diversification **[Oficial]** ("Demystifying creative diversification", 2025-12-16). The
  same video localized per city counts as ONE concept **[Oficial principle]**.
- Add new concepts as new ads inside the ad set that already works; do not change budget or
  audience the same day (edits restart learning) **[Oficial]**.
- Separate remarketing ad set: only when the custom audience has volume. With very small budgets
  let Advantage+ audience cover it **[Inferencia]**. If you do separate it (example: B2 remarketing,
  COP 8.000/day, ~30-35k people), review after 7 days and merge if it does not exit learning.
- Change creatives when Ads Manager shows "Fatiga creativa" / "Creativo limitado" or cost per
  conversation rises for several days, not at a fixed frequency **[Oficial]** (help 1346816142327858).
  Real case: one ad alone for 30 days, cost per conversation went from COP 235 to 301 **[Propio]**.
- Let it run 7+ days before judging **[Oficial]** (help 269324800441478).

## 3. Measure by sale, not by chat

The ad with the most chats is often not the one that sells most **[Propio, Equipos360]**:

| Ad | Chats | Sales |
|---|---|---|
| "Todo para casa" v1 | 3.488 | 9 |
| "Todo para casa" v2 | 1.184 | 12 |

Rules:
- **One predefined message per ad** ("Hola, vi que tienen tienda física...", "Hola, me interesa la
  guadaña"). It is free and lets the CRM/bot attribute each chat and each sale to its ad. Save each
  one as a named message template (e.g. "T03 Guadaña Nov 2026").
- Report per ad: conversations, cost per conversation, **sales and cost per sale from the CRM/ERP**,
  frequency, CTR.
- Before blaming the media buy, ask for the **chat close rate** and **hand-off to a human**:
  Equipos360 closed 0,53% of conversations; with hand-off to an advisor 3,3% bought vs 0,17%
  without it **[Propio]**. Fixing the chat often beats any targeting change.
- One greeting only: if the bot greets, turn off the WhatsApp Business app greeting (the ad's
  welcome message replaces app greetings for ad-started chats) **[Oficial + Propio]**.

## 4. Conversions API for Business Messaging

Without signals Meta optimizes toward people who chat, not people who buy **[Oficial mechanics]**.
Docs: developers.facebook.com/docs/marketing-api/conversions-api/business-messaging (updated 2026-09-28).

- `action_source: business_messaging`, `messaging_channel: whatsapp`.
- Send `ctwa_clid` (from the referral object of the first inbound message of an ad-started chat)
  plus `whatsapp_business_account_id`. **Since 2026-09-28: without `ctwa_clid`, `page_id` is required.**
- The dataset must be linked to the WhatsApp Business account.
- Known failure modes **[Propio]**: event dropped when `page_id` missing (error 2804116);
  expired/invalid token (190) fails silently if nobody reads the response; the sale should come from
  the ERP/CRM "won" state, not from the bot guessing.
- Start with a lead event (qualified conversation) before purchase: it reaches 50/week sooner.
- For implementation details see the `conversion-tracking` skill.

## 5. The WhatsApp number behind the ads

- **Error/notice "Cuenta de WhatsApp Business obligatoria ... los chats, el contenido multimedia y
  los contactos se moverán de forma automática (#2923012)"**: this is Meta's migration of *personal*
  WhatsApp accounts to WhatsApp Business (help 447934475640650). No public doc names the code.
  - Seen in Ads Manager on NEW ad sets (or ad sets whose locations were changed) for a number that
    is on the WhatsApp Cloud API through a CRM. Older ad sets did not show it **[Propio]**.
  - Publishing with "Intentar publicar elementos con errores" was accepted and ads went to review **[Propio]**.
  - **Do not follow the migration from the phone for a number that is on the Cloud API.** A number
    registered on the API cannot be used in the WhatsApp app; registering it in the app likely
    takes it off the API and breaks the CRM **[Oficial + Inferencia]**
    (developers.facebook.com/docs/whatsapp/cloud-api/phone-numbers; help 4631406400243963 is the
    flow for API numbers).
  - What to check instead: Page > Settings > Linked accounts > WhatsApp; confirm the number is
    linked as a Business/API number in the same business portfolio as the Page and ad account.
- After any ad goes live: **click the real ad until the chat appears in the CRM** with the ad's
  predefined message and referral data.
- Personal WhatsApp numbers are being retired for ads; before advertising a client's number,
  verify it is WhatsApp Business app or API **[Oficial]** (help 447934475640650, 1583303048513172).

## 6. Colombia / LATAM context

- Fear of scams is the main objection to buying online (93% fear scams, CNC 2023). The proof
  points that last: **physical store**, **"revísalo al recibir"** (inspect on delivery), deliveries
  by municipality, real staff on camera **[Tercero + Propio]**.
- Cash on delivery (contraentrega) is now table stakes (88 of 111 competing advertisers say it):
  use it as a fixed strip, not as the main message **[Propio, Ad Library research 2026-10-29]**.
- **Credit in ads** (Sistecrédito, ACR, financing) forces the **financial products special ad
  category**, which removes age and radius targeting (≥ ~24 km). Offer credit inside the chat,
  not in the ad **[Oficial category rules + Propio]**. Never imply the viewer's financial situation.
- No brand logos of manufacturers in ads or catalogs for resellers: Google suspended Equipos360
  for "counterfeit goods" after prominent brand use (2026-08) **[Propio]**. Keep catalog/Products
  extensions off unless the client owns the brand.
- Local store campaigns: pin radius ≥ 17 km in Ads Manager (minimum allowed), add nearby
  municipalities as **"Solo ciudad actual"** (city only) so the default +40 km radius does not
  blow up the area, and turn off "Llegar a más personas con probabilidades de responder"
  (it shows ads outside the selected places).

## 7. Creative formats that work cheaply for chat sales

See `ad-creative/references/hook-system.md` (Local and offer hooks) for templates:
- "¿Estás en [lugar] y buscas [solución]?" + 3 reasons (2 benefits + 1 differentiator, ≤ 7 words each).
- One objection per ad, taken from the bot's chats (contraentrega, city coverage, price), not from comments.
- Price in the hook to filter curiosity seekers (fewer chats, better chats).
- Physical store walkthrough, product working in real terrain, unboxing at the counter.
- 9:16 video plus a 4:5 version inside the same ad (see ads-manager-ui-traps-2026.md, item 1).

## 8. Weekly routine (15 minutes)

1. Per ad: conversations, cost per conversation, CRM sales, cost per sale, frequency, fatigue status.
2. Kill or replace ads in fatigue; add 1-2 new concepts if any ad set has < 3 distinct concepts.
3. Read 20 random chats from the week: objections, cities, products asked → next week's hooks.
4. Do not touch budgets more than ±20% at a time; no edits in the first 7 days of a new ad set.
