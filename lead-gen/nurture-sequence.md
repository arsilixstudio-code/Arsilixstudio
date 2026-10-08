# Nurture Sequence

Build this in HubSpot under **Automation → Workflows → Contact-based**. Sequences or workflows with delays need Marketing Hub or Sales Hub Starter or higher. On the free plan, send the same emails manually as Gmail templates.

**Enrollment trigger:** form submission on *Website – Project Inquiry* **OR** *Website – Newsletter*
**Suppress / unenroll when:** contact replies, a meeting is booked, a deal is created, or lifecycle stage becomes Opportunity

Tokens in `{{double braces}}` map to HubSpot personalization tokens. Replace `[BOOKING LINK]` with your calendar link (HubSpot Meetings or Google Calendar appointment schedule). Replace `[CASE STUDY LINK]` with a real case study page; only cite results you can back up.

---

## Email 0: instant auto-reply (all form leads, sent immediately)

**Subject:** Got it, {{contact.firstname}}: next steps on your project

> Hi {{contact.firstname}},
>
> Thanks for reaching out about your {{contact.project_type}} project. A real person from our team (not a bot) will reply within one business day.
>
> To move faster, grab a 30-minute discovery call here: [BOOKING LINK]
>
> On the call we'll cover what you're building, what "done" looks like, and a rough timeline and budget range. You'll leave with a clear next step whether or not we work together.
>
> — Arsilix Studio
> hello@arsilixstudio.com

---

## Email 1: day 2 · proof

**Subject:** How we ship AI features in weeks, not quarters

> Hi {{contact.firstname}},
>
> Most startups we talk to have the same problem: the AI feature is "on the roadmap", but the team is heads-down on the core product.
>
> Here's how we handled that for a SaaS team: [CASE STUDY LINK]. Scope, timeline, and what changed after launch.
>
> If something similar is on your plate, reply with one line about it and I'll tell you honestly whether we're a fit.

## Email 2: day 5 · process and de-risking

**Subject:** What a first 2 weeks with Arsilix looks like

> {{contact.firstname}}, a quick look at how we start:
>
> **Week 1:** discovery workshop, technical audit, and a clickable prototype of the riskiest flow.
> **Week 2:** a fixed-scope plan with milestones and a fixed price, so you know exactly what you're getting before the build starts.
>
> Starter engagements begin at $4,900 and Professional at $14,900 per project.
>
> Want a scoped plan for your idea? [BOOKING LINK]

## Email 3: day 9 · objection handling

**Subject:** "We'll just hire in-house"

> Fair. It's often the right call long-term.
>
> Where we help: getting v1 shipped while you hire, or handling specialist work (LLM integration, design systems, mobile) your team doesn't do every day. We document everything so your hires can take over cleanly.
>
> Happy to sanity-check your build-vs-hire plan on a short call, no pitch: [BOOKING LINK]

## Email 4: day 14 · value asset

**Subject:** A checklist for your next launch

> {{contact.firstname}}, here's the pre-launch checklist we run on every SaaS and AI project: performance, onboarding, analytics, LLM cost guardrails and more. [CHECKLIST LINK]
>
> Steal it. And if you want a second pair of eyes on your product, reply "audit" and we'll send back a short, free teardown.

## Email 5: day 21 · breakup

**Subject:** Should I close your file?

> Hi {{contact.firstname}},
>
> I haven't heard back, so I'll assume the timing isn't right. No problem.
>
> I'll stop emailing about this project. If things change, just reply to this thread and it comes straight to me.
>
> Good luck with the build!

**After email 5:** if there's no engagement, set lifecycle stage to *Lead* and keep the contact on the newsletter list only. If they opened or clicked 3 or more times, create a task: "Manual check-in — engaged but silent".

---

## Internal alert workflow (separate, for A-tier leads)

**Trigger:** `lead_tier` is `A – Hot`
**Actions:**
1. Send an internal email or Slack notification: "🔥 Hot lead: {{contact.firstname}} {{contact.lastname}}, {{contact.company}}, {{contact.budget_range}}, {{contact.project_timeline}}"
2. Create a deal in *Sales Pipeline → Appointment Scheduled*, named `{{contact.company}} — {{contact.project_type}}`
3. Create a task due in 2 hours: "Personal reply + booking link"
4. Unenroll the contact from the generic nurture so they get a human reply instead
