# Principles

> **Purpose:** Distilled wisdom from all decisions + implementation experience. Read in <2 minutes.
>
> **When to create:** Emerges after 5+ completed tasks — populated by `..hygiene`, not during onboarding.
>
> **When to update:** After major milestones or when pattern emerges across 3+ decisions.

---

## Mission

[Extract from project context — What is this delegation's core purpose?]

---

## Delegation Principles

**DP1: Trust & Integrity over Fluffy & Entertaining**
Accuracy beats impressiveness. Never hallucinate facts. Say "I don't know" when uncertain. Operator-grade communication, not marketing-grade. Trust is the product.

**DP2: Proactive Uncertainty Handling**
When context is incomplete, suggest tools (search, documentation) proactively. Don't assume completeness. Surface gaps explicitly. Default to "should we check?" not "I'll guess."

**DP3: Context Awareness**
Hold all .md files in mind when updating. Every stakeholder mention → check stakeholders/ files. Every decision → check PRINCIPLES/CONSTRAINTS. Never dump information arbitrarily.

<!-- Example from a trip project (uno/pa):
**DP1: Proactive Research** — Surface options before being asked
**DP2: Constraint-Aware** — Remember dietary, budget, and preference constraints
**DP3: Decision-Ready** — Present comparison tables, not raw data
-->

---

## Process Principles

**PP1: Files ARE Memory** — Docs persist, conversations don't
All context lives in .md files. AI reads them every session. This is how continuity works.

**PP2: Verifiable Done** — AC must be testable, not assumed
Every task has acceptance criteria. Check explicitly before marking complete. No verification theater.

**PP3: Deliverables Built Daily, Not Retrospectively**
After every meeting: "What goes in [deliverable]?" Weekly updates assembled daily. No Friday scrambles.

**PP4: README=Static, NEWSFEED=Dynamic**
README: purpose, structure, conventions (rarely changes). NEWSFEED: today's story (changes daily). Never mix.

**PP5: Stakeholder Memory is Explicit**
One file per person in stakeholders/. Update after every interaction. Relationship intelligence must be durable, not conversational.

<!-- Example:
**PP1: Files ARE Memory** — Docs persist, conversations don't
**PP2: Verifiable Done** — AC must be testable, not assumed
-->

---

## The "Next Session Test"

**For every section in a context file, ask:**
> "Would Claude need this to start fresh next session?"

- ✅ **Keep:** Active tasks, current constraints, technical reference
- ❌ **Archive:** Historical narrative, completed research, "how we learned X"

---

## Context Hygiene

Protocol files are the trade — they cost tokens but save more than they cost. Keep them lean.

**Check monthly:**
```bash
wc -w *.md
```

**Thresholds:**
- ✅ **Good:** Total <10,000 words, no single file >3,000 words
- ⚠️ **Warning:** Total 10,000-15,000 words, or any file >3,000 words
- 🚨 **Critical:** Total >15,000 words, or any file >5,000 words

**When critical:** Run `..hygiene` to archive old content.

---

## Related Files

| File | Purpose | Relationship to PRINCIPLES.md |
|------|---------|------------------------------|
| **PERSONA.md** | User preferences, signals | Source of Delegation Principles |
| **TODO.md** | Task list with AC | Source of process patterns |
| **CLAUDE.md** | Technical reference | Source of Process Principles |

---

*This file is extracted from active decisions after patterns emerge. It replaces the need to read all historical context.*

*Template from uno Protocol*
