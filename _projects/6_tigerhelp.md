---
layout: page
title: TigerHelp
description: An office-hours platform I'm building for Princeton's intro CS course staff, with a live SSE queue, CAS auth, and analytics that inform staffing.
permalink: /projects/tigerhelp/
importance: 6
category: software
github: https://github.com/YashThakkar21/tiger-help
---

**Next.js · TypeScript · PostgreSQL** · In development (started July 2026) · [Code]({{ page.github }})

Running office hours for 300+ students a semester across three courses is a queueing problem, and we've been solving it with a spreadsheet. As Head TA I have the data on how badly that works: students waiting without knowing their position, TAs double-claiming the same question, and no record afterward of where the time actually went. TigerHelp is what I'm building to replace it.

### Features

- **Live queue over Server-Sent Events.** Students see their position update in real time without polling; TAs see claims propagate instantly, which eliminates double-claiming.
- **CAS authentication.** Integrated with Princeton's central auth, so there are no separate accounts and course rosters map directly to access.
- **TA analytics view.** Aggregates wait times, question volume by assignment, and per-session load: the numbers that inform how many TAs to staff for which hours.

The analytics view is the part I care most about. Staffing decisions are usually made on intuition about which weeks are "the hard ones"; the goal is to make them on the actual distribution of demand instead.
