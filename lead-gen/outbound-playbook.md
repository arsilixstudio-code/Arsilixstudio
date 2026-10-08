# Outbound Prospecting Playbook: Startups & SaaS

## 1. Ideal Customer Profile (ICP)

| Filter | Value |
|---|---|
| Industry | Software development, SaaS, internet, fintech, healthtech, AI/ML |
| Company size | 5–200 employees |
| Company age | 0–6 years |
| Location | US, UK, Canada, EU, Australia (adjust to your time zones) |
| Buying signals (any one) | New funding round in the last 90 days · hiring engineers or designers · new product launch · growing engineering headcount |
| Personas | Founder / CEO, CTO / VP Engineering, Head of Product |

**Best-fit trigger:** freshly funded startups (seed to Series B). They have budget and pressure to ship, and their hiring can't keep up.

## 2. Sourcing (weekly, 25–50 prospects)

Use the connected **Vibe Prospecting** tool. Ask Claude something like *"pull 30 founders/CTOs at software startups, 11–200 employees, US/UK, that raised funding in the last 90 days, with emails"*.

1. Free exploration fetch: check the count and preview rows
2. `show-sample` (≈5 credits): full rows
3. Contact enrichment, then export (cost shown first; **always confirm before spending credits**)
4. Import the CSV into HubSpot (**Contacts → Import**) and set *Lead source = Outbound – Vibe*, *Lifecycle = Lead*
5. Enroll in the cold sequence below. Skip anyone already in HubSpot.

Other free sources: Crunchbase or Dealroom funding news, YC launches, Product Hunt launches, "we're hiring" posts on LinkedIn, and Wellfound job listings for frontend, mobile or ML roles.

## 3. Personalization (2 minutes per prospect)

Find **one** specific hook before sending:
- Recent funding: "Congrats on the $Xm seed"
- Job post: "Saw you're hiring a senior React Native dev"
- Product: a concrete observation about their app or site (slow load, missing AI feature, onboarding gap)

No hook means the prospect isn't ready; skip them.

## 4. Cold email sequence (4 touches over 14 days)

Send from a warmed-up mailbox. Keep it under 30–50 cold emails a day per inbox, plain text, with no images or tracking pixels on touch 1. Add an opt-out line and your business address to comply with CAN-SPAM, GDPR and PECR.

**Touch 1 · Day 0**
**Subject:** {{company}} + {{trigger_short}}

> Hi {{firstname}},
>
> {{personal_hook}}.
>
> Teams at your stage usually hit the same wall: the roadmap needs {{AI features / a mobile app / a rebuilt web app}}, but the core team is already at capacity.
>
> Arsilix is a small senior studio that ships those projects in 4–10 weeks at a fixed scope and price, then hands everything to your team cleanly.
>
> Worth a 20-minute call to see if there's a fit?
>
> — {{sender}}, Arsilix Studio
> *Not relevant? Reply "no" and I won't follow up.*

**Touch 2 · Day 3** (reply in the same thread)

> {{firstname}}, one idea specific to {{company}}: {{1-sentence concrete idea, e.g. "an AI onboarding assistant could cut your setup steps from 6 to 2"}}.
>
> Happy to sketch it out. No charge, no obligation.

**Touch 3 · Day 7** (new thread)
**Subject:** quick teardown of {{company}}'s {{onboarding / app / site}}

> Hi {{firstname}}, I put together 3 quick wins I'd make to {{product area}}:
> 1. …
> 2. …
> 3. …
>
> If useful, I can walk you through them in 15 minutes: [BOOKING LINK]

**Touch 4 · Day 14** (same thread)

> Closing the loop. Sounds like the timing's off. If {{AI / mobile / web}} work moves up the roadmap, just reply here.

**Replies:**
- **Positive:** book the call and create a HubSpot deal at *Appointment Scheduled*
- **"Not now":** set a task for 90 days out and move them to the newsletter
- **"No" or unsubscribe:** mark as unsubscribed, never contact again

## 5. LinkedIn in parallel

| Day | Action |
|---|---|
| −2 | View profile, like or comment on a recent post |
| 1 | Connection request, no note or a one-line note referencing the hook |
| 5 (if accepted) | "Thanks for connecting. Shared a quick idea for {{company}} by email; happy to send it here instead." |

## 6. Benchmarks and when to change course

- Reply rate below 3% after 100 sends: rewrite the touch 1 hook and subject line; the targeting may be off.
- Replies but no calls: the offer is unclear; lead with the free teardown.
- Calls but no proposals: qualify harder on budget and timeline before the call.
