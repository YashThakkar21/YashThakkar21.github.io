---
layout: page
title: TigerHelp
description: The office-hours platform Princeton's intro CS course staff runs on — live SSE queue, CAS auth, and analytics that inform staffing.
permalink: /projects/tigerhelp/
importance: 6
category: software
github: https://github.com/YashThakkar21/tiger-help
---

**Next.js · TypeScript · PostgreSQL** — 2026 · [Code]({{ page.github }})

Running office hours for 300+ students a semester across three courses is a queueing problem, and we were solving it with a spreadsheet. As Head TA I had the data on how badly that worked — students waiting without knowing their position, TAs double-claiming the same question, and no record afterward of where the time actually went. TigerHelp is what replaced it.

### Features

- **Live queue over Server-Sent Events.** Students see their position update in real time without polling; TAs see claims propagate instantly, which is what eliminated double-claiming.
- **CAS authentication.** Integrated with Princeton's central auth, so there are no separate accounts and course rosters map directly to access.
- **TA analytics view.** Aggregates wait times, question volume by assignment, and per-session load — the numbers that inform how many TAs to staff for which hours.

The analytics view is the part I care most about. Staffing decisions used to be made on intuition about which weeks were "the hard ones"; now they're made on the actual distribution of demand.
