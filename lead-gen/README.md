# Arsilix Lead Generation Workflow

Target client: **startup and SaaS founders, CTOs and heads of product** (seed to Series B, 5–200 people) who need AI features, a web or SaaS app, or a mobile app.

```
 INBOUND                         OUTBOUND
 Website form / newsletter       Prospect list (ICP filters)
          │                               │
          ▼                               ▼
   HubSpot contact  ◄──── enrich + import ┘
   (fit score + tier, UTM source)
          │
          ├── Tier A (Hot)   → alert + personal reply < 2h → book discovery call
          ├── Tier B (Warm)  → personal reply < 1 business day + nurture
          └── Tier C (Nurture) → automated 5-email nurture sequence
          │
          ▼
   Deal pipeline: Discovery → Qualified → Proposal → Negotiation → Won / Lost
```

| File | What it covers |
|---|---|
| `README.md` (this file) | Inbound setup, lead scoring, pipeline, weekly routine, KPIs |
| [`nurture-sequence.md`](nurture-sequence.md) | Auto-reply and 5-email nurture copy, plus HubSpot workflow settings |
| [`outbound-playbook.md`](outbound-playbook.md) | ICP filters, prospect sourcing, 4-touch cold sequence, LinkedIn steps |

---

## 1. Inbound: website → HubSpot (one-time setup, ~20 min)

The site form (`arsilix-studio_1.html`, `#lead-form`) and the footer newsletter now send submissions to the HubSpot Forms API. Until the form IDs below are filled in, each submission opens a pre-filled email to `hello@arsilixstudio.com`, so no lead is lost in the meantime.

### 1a. Create the contact properties
In HubSpot, go to **Settings → Properties → Contact properties → Create property** (group: *Contact information*):

| Internal name | Label | Type |
|---|---|---|
| `project_type` | Project Type | Single-line text |
| `budget_range` | Budget Range | Single-line text |
| `project_timeline` | Project Timeline | Single-line text |
| `lead_fit_score` | Lead Fit Score | Number |
| `lead_tier` | Lead Tier | Dropdown: `A – Hot`, `B – Warm`, `C – Nurture` |

`utm_source`, `utm_medium`, `utm_campaign`, `landing_page` and `referrer` are optional. Create them the same way if you want first-touch attribution on each contact.

### 1b. Create two forms
In HubSpot, go to **Marketing → Forms → Create form → Embedded**:

1. **Website – Project Inquiry** with fields: First name, Last name, Email, Company name, Message, plus every property from 1a, added as *hidden* fields.
2. **Website – Newsletter** with the Email field only (plus the UTM fields if you created them).

Copy each form's ID (the GUID in the form editor URL, e.g. `…/forms/247639719/`**`a1b2c3d4-…`**).

### 1c. Paste the IDs into the site
In `arsilix-studio_1.html`, find `LEAD_CONFIG`:

```js
contactFormGuid: 'PASTE-PROJECT-INQUIRY-FORM-ID',
newsletterFormGuid: 'PASTE-NEWSLETTER-FORM-ID',
hubspotRegion: 'na1',   // change to 'eu1' if your HubSpot URL contains app-eu1
```

The portal ID (`247639719`) is already set. If a property from 1a is missing on the form, HubSpot rejects the submission. The script then resends it with name, email, company and message only, so the lead still arrives, but you should fix the form.

### 1d. Turn on notifications
Under **Forms → Website – Project Inquiry → Options → Notifications**, send to `info@arsilixsolution.com` (plus anyone else on sales).

---

## 2. Lead scoring (calculated in the browser on submit)

| Signal | Points |
|---|---|
| Budget: $5–15k / $15–50k / $50–150k / $150k+ | 5 / 15 / 25 / 30 |
| Timeline: ASAP / 1–3 mo / 3–6 mo / Flexible | 20 / 15 / 8 / 3 |
| Project: AI or SaaS app / Mobile / Website / Branding | 20 / 15 / 10 / 5 |
| Company name provided | +10 |
| Work email (not Gmail, Yahoo, Outlook, etc.) | +10 |
| Details longer than 80 characters | +10 |

**Tiers:** score of 70 or more = **A – Hot**, 45–69 = **B – Warm**, below 45 = **C – Nurture**.
Example: AI project, $50–150k, ASAP, company name and work email give 25 + 20 + 20 + 10 + 10 = 85, so it's an **A**.

The score is also written into the message body, so you can see it even before the custom properties exist. To change the weights, edit `scoreLead()` in the site's lead capture script.

---

## 3. Pipeline and response rules

Use the existing HubSpot **Sales Pipeline**, mapped as follows:

| HubSpot stage | Meaning for Arsilix | Exit criteria | Owner SLA |
|---|---|---|---|
| Appointment Scheduled | Discovery call booked | Call happened | Confirm within 2h |
| Qualified To Buy | Budget, timeline and decision-maker confirmed | Scope agreed enough to quote | Send recap within 24h |
| Presentation Scheduled | Proposal walkthrough booked | Proposal presented | Proposal within 3 business days of qualification |
| Decision Maker Bought-In | Verbal yes, negotiating scope or price | Terms agreed | Follow up every 2–3 days |
| Contract Sent | SOW / contract out | Signed | Nudge at day 2 and day 5 |
| Closed Won / Lost | — | Log the lost reason every time | — |

Response rules by tier:
- **A – Hot:** personal reply within 2 business hours, with a booking link and 2–3 sharp questions about their project. Create a deal right away.
- **B – Warm:** personal reply within 1 business day, then enroll in the nurture sequence if there's no reply in 3 days.
- **C – Nurture:** automatic enrollment in the nurture sequence. Review weekly for anything that warmed up (replies, pricing page visits).

---

## 4. Weekly routine (about 3 hours a week)

| Day | Task | Time |
|---|---|---|
| Mon | Pull 25–50 new outbound prospects (see `outbound-playbook.md`), import them to HubSpot, start the sequence | 60 min |
| Daily | Reply to inbound A/B leads, work the outbound reply inbox, move deals between stages | 15 min |
| Wed | Publish 1 LinkedIn post (case study, build log or AI teardown) to feed inbound | 30 min |
| Fri | Review KPIs, re-score stale leads, log lost reasons | 30 min |

## 5. KPIs to track (HubSpot dashboard)

| Metric | Healthy target |
|---|---|
| Inbound form submissions / month | Grow month over month |
| Form → discovery call rate | ≥ 30% (A and B tiers) |
| Outbound reply rate | 5–10% |
| Outbound positive-reply → call | ≥ 50% |
| Discovery → proposal | ≥ 50% |
| Proposal → won | 25–35% |
| Median first-response time (A tier) | < 2h |
| Pipeline value created / month | ≥ 3× monthly revenue goal |
