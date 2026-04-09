# EverydayAI: Travel Planner Offline App

**Series:** EverydayAI — practical AI use cases that don't scale. And that's the point.


## The pitch nobody gives at conferences

Most AI narratives follow a familiar arc. A team identifies a problem affecting thousands of users. They train a model, instrument a pipeline, ship to production, measure retention uplift. The story ends with a deck slide showing hockey-stick adoption.

This is not that story.

This is about a five-day family trip to the Świętokrzyskie Mountains in Poland over Easter 2026. Six people, children included, one car, a lot of medieval ruins and one very useful offline HTML file that I built with Claude over the course of a few evenings.

No pipeline. No users. No scale. Just one artifact that made one trip meaningfully better.

I think that matters more than we admit.

## The problem, stated plainly

Group travel with children has a specific failure mode: information collapse. You have a hotel confirmation in one app, attraction tickets in another, a shared notes doc nobody checks, a WhatsApp thread that's been overtaken by memes, and at least one person who will ask "wait, what time was the reservation?" at the exact moment you're trying to navigate a roundabout.

We had six people going to a region none of us knew well. We had pre-bought tickets with specific entry times. We had opening hours that varied by holiday. We had a local contact (Sebastian) whose recommendations were scattered across a voice note. We had weather that would determine which days were best for outdoor attractions.

What I wanted was a single offline-capable screen I could hand to anyone in the car and they'd know exactly what was happening, when, and what to do next. No signal required.

What I didn't want was to spend three hours in Figma or wrestle with a no-code tool to get there.


## What I actually built

A single HTML file. Fully offline. Optimized for mobile. Dark mode with a warm parchment-and-gold aesthetic that felt appropriate for medieval castles and Neolithic mines.

The app had three tabs:

**Plan** — a day-by-day timeline for all six days of the trip. Each attraction was a card you could tap to expand. Inside: address, phone number (tap-to-call), entry time, ticket status, and any tips from our local contact. Weather forecast embedded per day. A sticky navigation bar at the top let you jump between days.

**Checklist** — all pre-bought tickets with confirmation numbers, things still to arrange, and practical reminders (bring a jacket — caves are 9°C year-round; cash only at several sites; change of clothes mandatory on Easter Monday for obvious reasons involving children and water pistols).

**Info** — contacts, parking coordinates, ticket codes, cost summary per day.

The whole thing was built iteratively across multiple conversations with Claude. I'd describe what I needed, Claude would generate the HTML and CSS, I'd test it on my phone, and we'd refine. No framework. No build step. One file, open in any browser, works with airplane mode on.


## How AI actually helped

Not by doing the research for me. By helping me structure what I already knew and present it usefully.

The process looked like this:

I had raw information from multiple sources — official attraction websites, a local guide's recommendations, my own ticket emails, weather forecasts, a planned route. Claude helped me turn that into a navigable interface without me having to write a line of CSS from scratch or remember how to make a sticky tab bar behave on iOS Safari.

When I confirmed opening hours by phone (yes, I still called attractions — AI can't replace that), I'd come back and update the app. "The castle is open Monday but confirm it's not Easter Sunday specifically" became a real conversation thread that affected the final itinerary.

When our plans changed during the trip — we added two spontaneous stops, moved an attraction from one day to another — I updated the app in under ten minutes per change. The format was flexible enough to absorb reality.

When the trip was over, I asked Claude to update the app to reflect what actually happened, as a record. Every card got a ✅ Done tag. Two spontaneous bonuses (a baroque castle ruin that rivalled Versailles in its day, a bison safari at a 14th-century palace) got marked as happy accidents.


## What this is not

It's not a product. It served exactly one trip, for exactly one group of people, and will never be used again in this form.

It's not a validated use case. I didn't A/B test "trip app vs. WhatsApp thread." I didn't measure how many fewer times someone asked "where are we going next?"

It's not scalable. I can't turn this into a SaaS. The value was entirely in the specificity — the exact entry time for Krzemionki UNESCO mines, the note that the ECN PGE science center is on the second floor of a building called SKYE INC (not the address that was in the original plan), the GPS coordinates for a parking lot at the foot of Łysa Góra that costs 30 PLN for the day.

Generic tools can't do this. A travel app doesn't know that our local contact Sebastian said the Muzeum Orła Białego is the most underrated thing in the region and that kids can literally climb on the military equipment. A template can't capture that a specific cave is closed Easter Sunday but confirmed open Easter Monday after a phone call.

The specificity was the product. And AI was the tool that made the specificity usable.



## The actual insight

We're in a period where most AI discourse is structured around scale. How many users? What's the retention? Does it generalize?

These are the right questions for products. They're the wrong questions for tools.

A hammer doesn't scale. A spreadsheet doesn't scale. A well-structured HTML file that your travel group can open offline on their phones doesn't scale.

What it does is solve a specific problem for specific people in a specific moment. And if that problem is real and the solution works, that's enough. It doesn't need to be more than that to be valuable.

As product managers, we're trained to think in user segments and use cases that aggregate. That training is right for what we build professionally. But it can become a blind spot for how we think about tools — including AI — in our own lives.

The question isn't always "how does this scale?" Sometimes the question is just "does this help?" And sometimes the answer is a single HTML file that a six-year-old can look at and understand that tomorrow we're going to a cave where a Neanderthal lived 50,000 years ago.


## What I'd do differently

Almost nothing about the output. A few things about the process.

I'd start the app earlier — ideally two weeks before the trip, not five days. The iterative back-and-forth to verify information takes time that shouldn't be compressed into the last few evenings before departure.

I'd involve the group from the start. I built the app and then shared it. It would have been better to ask "what information do you actually want at your fingertips?" before building. Classic product mistake, even on a personal scale.

I'd add a simple audio layer earlier. We ended up with five podcast-style audio briefings — five to fifteen minutes each, one per day — covering the history of each attraction. These were great in the car. But they were written as text and read aloud from the screen, which is clunky. Next time I'd budget time to generate proper audio via ElevenLabs and share MP3s through WhatsApp before departure.


## The stack, for the technically curious

Single HTML file with embedded CSS and vanilla JavaScript. Google Fonts loaded from CDN (with fallback to system fonts for offline). LocalStorage for checklist persistence. No framework. No build step. No deployment. Shared as a file attachment.

Claude (Sonnet) for iteration across multiple sessions — interface design, content structuring, day-by-day logic, and post-trip archiving. Web search for verifying opening hours and finding current ticket prices. My own phone calls for anything where the stakes were high enough to require a human confirmation.

Total time investment: roughly six to eight hours spread across a week, including research, phone verification, and iterative refinement.


## On the EverydayAI framing

I'm planning to write more of these. Not about AI that disrupts industries. About AI that helps one person do one thing better than they would have otherwise.

The travel planner is one example. There are others: a coaching framework I built to structure mentor sessions, a competitive analysis template that made a product review three times faster, a communication audit that helped me give better feedback to a junior colleague.

None of these scale. All of them worked.

I think that's worth documenting.

