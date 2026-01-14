# uno — Delegate Protocol

A template for AI-assisted delegation — AI works FOR you.

Part of the [KayGee Protocol Family](https://github.com/marekgorski/admin/tree/main/protocol).

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

## What's New in v2.1: Personas

uno now includes a **personalization layer**. During onboarding, AI asks what you care about, what signals matter, and what to filter out. This creates `PERSONA.md` — your AI's training data.

**Result:** Every briefing and summary is filtered through YOUR lens automatically.

| Extension | Persona Captures |
|-----------|------------------|
| **ea** | Decision style, signal watch, noise filter, key stakeholders |
| **pa** | Planning style, interests, constraints, avoid list |
| **km** | Learning style, depth preference, domain focus |

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
3. **Persona configuration** — What you care about, what to surface, what to filter (NEW)
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
├── PERSONA.md     # Your preferences and signals (NEW)
├── TODO.md        # Tasks with acceptance criteria
├── PROGRESS.md    # Session log
├── MAREK.md       # Human-only tasks
├── README.md      # Project description
└── _archive/      # Old entries
```

Extensions add domain-specific files (see above).

---

## Task Ownership

| Marker | Meaning | Lives In |
|--------|---------|----------|
| `[C]` | Claude can complete | TODO.md |
| `[M]` | Human must complete | MAREK.md |
| `[C→M]` | Claude prepares, human executes | TODO.md → MAREK.md |
| `[M→C]` | Human decides, Claude implements | MAREK.md → TODO.md |

**No marker = `[C]`**

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
| MAREK.md | What only you can do (so AI doesn't waste time) |
| PERSONA.md | Who you are, what you care about (NEW) |

Four files. That's all you need for persistent, personalized delegation.

---

## Key Rules

1. **AC is required** — Every TODO needs acceptance criteria
2. **Task ownership** — Use markers, don't let Claude spin on human tasks
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

| Project | Extension | Description |
|---------|-----------|-------------|
| [uno-ea](https://github.com/marekgorski/uno-ea) | ea | 90-day onboarding tracker |
| [australia-trip](https://github.com/marekgorski/australia-trip) | pa | Family trip planning Feb-Mar 2026 |
| [admin](https://github.com/marekgorski/admin) | km | KayGee operations |

---

## Changelog

- **v2.1** (Jan 14, 2026): Added persona layer — personalized briefings via PERSONA.md configuration
- **v2.0** (Jan 2, 2026): uno/pa validated with australia-trip implementation, refined NOTES.md template with research tables
- **v2.0** (Jan 1, 2026): Rebranded to uno, added extension system (ea, pa, km), extension-aware `..start`
- **v1.2** (Dec 28, 2025): Task ownership markers, handoff system
- **v1.1** (Dec 28, 2025): Acceptance criteria, verification
- **v1.0** (Dec 2024): Initial release

---

## License

MIT — Use freely, modify as needed.

---

*protocol-uno v2.1 — January 14, 2026*
