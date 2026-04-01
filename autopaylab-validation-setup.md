# How I Built a Production Validation Environment as a PM — and Got Security to Sign Off

At Autopay, I needed a way to validate product ideas quickly. Not in staging. Not in Figma.
In a real, public environment — with real analytics, real URLs, and real user behavior.

Here's how I built it, got it through security and compliance, and why it changed how I work.

## The Problem

As a Product Discovery Director, I kept hitting the same wall: by the time a concept
reached a real environment, too many decisions had already been made. Prototypes in Figma
are great for flows, but they don't tell you if people actually engage, click, or understand
what you're offering.

I wanted something in between. A real URL. Real analytics. Fast to spin up. Zero risk
to Autopay's core infrastructure.

## The Stack

- **Lovable** — for building interfaces fast, without writing code
- **Vercel** — for hosting and deployment
- **Matomo** — for analytics (self-hosted, privacy-first)
- **autopaylab.com** — the umbrella domain, currently showing a coming soon page

The key insight on the domain setup: DNS is configured so I can create new subdomains
directly in Vercel. Every smoke test or validation gets its own subdomain — spun up in
minutes, no IT ticket required.

## Getting Security and Compliance On Board

This was the part I was most worried about. Autopay is a fintech. Security is not a
checkbox — it's a culture.

The argument that worked was simple: **isolation**.

I made it clear that autopaylab.com has zero connection to Autopay's systems, data,
or infrastructure. No shared databases. No internal APIs. No customer data. It's a
completely separate environment that happens to live under a related domain.

Framing it as a sandbox — not a product extension — changed the conversation. Security
didn't need to audit a new surface of Autopay. They needed to confirm that this thing
was genuinely disconnected from it. Once that was established, the path was clear.

**The lesson:** in regulated environments, the question isn't "can we do this?" —
it's "what would make this safe enough to do?" Come with the answer, not just the ask.

## The Analytics Setup

I didn't want to deal with GDPR friction on every new experiment, and I didn't want
analytics living in a third-party cloud. Matomo was the obvious choice.

The integration lives inside Lovable's knowledge base — a design system file that
includes the Matomo tracking snippet. Every new interface I build in Lovable inherits
the analytics automatically. No copy-pasting. No forgetting to add tracking.

This means from day one of any new validation, I have:
- Pageviews and session data
- Click and engagement tracking
- A clean dashboard to review before making a go/no-go call

## How I Use It for Product Validation

The workflow is straightforward:

1. I identify a hypothesis worth testing — usually something that would take weeks
   to validate through normal product development
2. I build a rough interface in Lovable (hours, not days)
3. I deploy to a new subdomain on Vercel (minutes)
4. I drive traffic to it — through internal stakeholders, targeted outreach, or small
   paid campaigns
5. I read the Matomo data and make a call

It's not A/B testing at scale. It's smoke testing: does anyone care enough to click?
Does the concept land without explanation? Is the CTA clear?

That signal, even from a small sample, is worth more than three weeks of internal debate.

## What This Changes for PMs

Most product managers treat "production" as someone else's domain. You design, you
specify, you hand off — and then you wait.

This setup removes that dependency for early-stage validation. You're not shipping
a feature. You're testing whether a feature is worth shipping at all.

The tools exist. Lovable handles the interface. Vercel handles the infrastructure.
Matomo handles the data. The only thing left is the judgment call on what to test —
and that's exactly what PMs are supposed to be good at.

## TL;DR

- Built a public production validation environment as a non-technical PM
- Got security sign-off by framing it as a fully isolated sandbox
- DNS setup on autopaylab.com allows instant subdomain creation via Vercel
- Matomo is embedded in a Lovable knowledge base — analytics come for free on every build
- Used for smoke tests and early hypothesis validation before committing to development
