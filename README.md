# uno — Delegate Protocol

**Version 1.0** — AI works FOR you.

A template for AI-assisted delegation. Part of the [KayGee Protocol Family](https://kayg.ee/protocol).

---

## The Protocol Family

```
uno (Delegate)          duo (Collaborate)       tre (Automate)
AI works FOR you        AI works WITH you       AI works AMONG systems
├── /ea (Executive)     └── /ab (Arch+Build)    ├── /qa (Quality)
├── /pa (Personal)                              ├── /rm (Risk)
└── /km (Knowledge)                             └── /cs (Customer)
```

**uno** is for clear delegation: you define WHAT, AI handles HOW.

Use **duo** ([protocol-duo](https://github.com/marekgorski/protocol-duo)) for code projects needing architect/builder separation.

---

## What's in v1.0

**Commands:**
- `..start` — Load context, show priorities
- `..end` — Verify work, update logs, commit
- `..hygiene` — Token budget monitoring, health checks, automated thresholds
- `..gm` (Good Morning) — Morning briefing with priorities, risks, DMs to send
- `..gn` (Good Night) — Enhanced close with deliverables check, NEWSFEED prep

**File patterns:**
- **PERSONA.md** — Personalization layer (your AI's training data)
- **PRINCIPLES.md** — Distilled patterns from completed work
- **CONSTRAINTS.md** — What we avoid (learned from failures)
- **NEWSFEED.md** — Dynamic daily newspaper (ea extension)
- **stakeholders/** directory — One file per stakeholder (ea extension)

**Task ownership by location:**
- **TODO.md** — AI tasks (Claude's work)
- **TASKS/** — Human tasks (only a human can do)

**Trust & Integrity principles:**
- No lazy linking — inline narrative context required
- Proactive tool suggestions — admit uncertainty, suggest searches
- Deliverables discipline — build daily, not Friday scrambles
- Context awareness — check all .md files before updating

---

## Extensions

uno comes with domain-specific extensions that customize behavior:

| Extension | Mode | Use Case | Creates |
|-----------|------|----------|---------|
| **ea** | Executive Assistant | Onboarding, projects with deadlines, stakeholder management | UPDATES.md, GLOSSARY.md, KNOWLEDGE.md, SYSTEMS.md, PERSONA.md |
| **pa** | Personal Assistant | Trip planning, events, moves, personal finance | ITINERARY.md, BOOKINGS.md, BUDGET.md, NOTES.md, PERSONA.md |
| **km** | Knowledge Manager | Documentation, archives, reference material | LOG.md, PLANNED.md, PERSONA.md |
| **none** | Base uno | Simple delegation without domain tracking | (core files only) |

Extension is selected during onboarding — Claude will ask which fits your project.

---

## Quick Start

### 1. Use this template

**GitHub Template:** Click "Use this template" on GitHub to create a new repo.

Or clone directly:

```bash
git clone https://github.com/marekgorski/protocol-uno.git my-project
cd my-project
rm -rf .git && git init
```

### 2. Open in Claude

Claude will see the `[PLACEHOLDER]` markers and run the onboarding flow:

1. **Extension selection** — ea, pa, km, or none
2. **Discovery questions** — What, who, problem, success, constraints
3. **Persona configuration** — What you care about, what to surface, what to filter
4. **File creation** — Extension-specific files generated
5. **Ready to work**

### 3. Use session commands

| Command | Purpose |
|---------|---------|
| `..start` | Personalized briefing (persona-filtered), priorities, blockers |
| `..end` | Verify AC met, update docs, commit |
| `..hygiene` | Archive old entries |

---

## Core Files

All uno projects have:

```
my-project/
├── CLAUDE.md      # Protocol + project reference
├── PERSONA.md     # Your preferences and signals
├── TODO.md        # Tasks with acceptance criteria
├── PROGRESS.md    # Session log
├── TASKS/         # Human-only tasks (folder-based)
├── README.md      # Project description
└── _archive/      # Old entries
```

Extensions add domain-specific files (see above).

---

## Task Ownership

Location encodes ownership — no markers needed:

| Location | Owner | Purpose |
|----------|-------|---------|
| **TODO.md** | Claude | AI tasks — work Claude does |
| **TASKS/** | Human | Tasks only a human can do |

Handoffs flow naturally: Claude creates deliverables and adds task files in `TASKS/` for human execution. Humans add outcomes to task files in `TASKS/DONE/` and Claude picks up dependent work.

---

## Philosophy

### Why Files Work

AI forgets everything between conversations. Start a new chat, and it's meeting you for the first time.

But files don't forget.

When you write what you learned in a file, AI reads it next session. When you track what's done, AI knows where you left off. When you log what needs a human, AI doesn't spin on work it can't complete.

**Your markdown files ARE the AI's memory:**

| File | What It Remembers |
|------|-------------------|
| TODO.md | What needs doing (with clear "done" criteria) |
| PROGRESS.md | What happened (so the next session knows) |
| TASKS/ | What only you can do (so AI doesn't waste time) |
| PERSONA.md | Who you are, what you care about |

Four files. That's all you need for persistent, personalized delegation.

---

## Key Rules

1. **AC is required** — Every TODO needs acceptance criteria
2. **Task ownership** — TODO.md = AI work, TASKS/ = human work
3. **Verify before done** — `..end` checks AC explicitly
4. **Commit after each task** — Don't let work pile up
5. **Persona filters everything** — Briefings use your preferences automatically

---

## Extension Behaviors

### uno/ea — Executive Assistant

`..start` produces a persona-filtered daily briefing:
- **Signals detected** (matching your Signal Watch list)
- **Decisions needed** (structured per your Decision Style)
- Status calculation (Day N/90, T-N countdown)
- Pace check (meetings/day, deliverables vs targets)
- **Filtered out** (items matching your Noise Filter)
- Today's #1 priority

### uno/pa — Personal Assistant

`..start` produces a persona-filtered trip briefing:
- **Matches your interests** (from your Interest tags)
- Timeline check (next 7 days)
- **Constraints check** (verified against your stated constraints)
- Booking deadlines (expiring, needs confirmation)
- Budget status (spent vs planned)
- **Filtered out** (items matching your Avoid list)
- Today's logistics priority

### uno/km — Knowledge Manager

`..start` produces a persona-filtered documentation check:
- **Priority domains** (from your Domain Focus)
- Pending items in LOG.md
- **Learning queue** (structured per your Learning Style)
- Recurring tasks due in PLANNED.md
- Stale documentation (30+ days)
- Today's documentation priority

---

## Implementations

This protocol is actively used across multiple projects spanning all three extensions (ea, pa, km). Create your own by clicking "Use this template" on GitHub.

---

## Changelog

- **v1.0** (Jan 25, 2026): Official release of protocol-uno
  - Extension system: ea (Executive), pa (Personal), km (Knowledge)
  - Commands: `..start`, `..end`, `..hygiene`, `..gm`, `..gn`
  - File patterns: PERSONA.md, PRINCIPLES.md, CONSTRAINTS.md, NEWSFEED.md
  - Task ownership: TODO.md (AI work), TASKS/ folder (human work)
  - Trust & Integrity principles for transparent AI collaboration
  - Token budget monitoring and hygiene automation


---

## Graduation: From Jet Ski to Direct Intent

Most people start by building "jet skis" — exploring what AI can do, learning the rhythm of delegation. That's what this template is for.

At some point, you'll stop asking "what can I build?" and start asking "what should I build and why?" That's the graduation signal.

When you're ready, add `INITIATIVES.md` to your project root — a strategic layer above your existing files:

| Level | What | Files | When |
|-------|------|-------|------|
| **1. Initiative Tracker** | Why, what, who, when | INITIATIVES.md | After you've shipped something real |
| 2. Phase Tracker | Progress, priorities | TODO.md + TASKS/ | Day 1 |
| 3. Daily Work | Tasks, commits | TASKS/ + git | Day 1 |

The Level 1 template asks 6 questions per initiative: **Why**, **Which Models**, **What Revenue**, **How to Measure**, **Who's Building**, **When** (milestones + biggest risk).

Don't add it on day one — build first, direct later.

**Learn more:** [The 4 Levels](https://kayg.ee/learn/levels) — full guide with working example.

---

## Contributing

Evolved the protocol? We'd love to hear about it. See [CONTRIBUTING.md](CONTRIBUTING.md) or submit to [kayg.ee/protocol/upstream](https://kayg.ee/protocol/upstream).

---

## License

MIT — Use freely, modify as needed.

---

*protocol-uno v1.0 — January 25, 2026*
