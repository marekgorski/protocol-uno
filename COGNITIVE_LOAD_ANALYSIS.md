# Cognitive Load Protection in uno

**Analysis:** How cognitive load reduction patterns strengthen the uno protocol

**Date:** 2026-01-09

---

## Core Insight

> "When the environment around me, or the people in it, are agents of chaos, I need AI to be my agent of calm."

**uno's purpose:** Reduce decision fatigue by handling the "how" so you can focus on the "what."

**Gap identified:** uno excels at ORGANIZATION but lacks CAPTURE flows for unstructured input.

---

## How uno Fits in the Protocol Family

### The KayGee Philosophy: "Files Don't Forget"

> "AI forgets everything between conversations. Start a new chat, and it's meeting you for the first time. But files don't forget."

The protocol family (uno/duo/tre) shares this core principle: **markdown files ARE the AI's memory.**

### Three Modes of AI Collaboration

```
uno (Delegate)          duo (Collaborate)       tre (Automate)
AI works FOR you        AI works WITH you       AI works AMONG systems
├── /ea (Executive)     └── /ab (Arch+Build)    ├── /qa (Quality)
├── /pa (Personal)                              ├── /rm (Risk)
└── /km (Knowledge)                             └── /cs (Customer)
```

**uno:** Clear delegation, you define WHAT, AI handles HOW
- 3 core files (TODO, PROGRESS, MAREK) + extension files
- Solo productivity, decision fatigue reduction
- Starts with: tasks, goals, constraints

**duo:** Team collaboration, iterative role-switching
- 8 structured files (PRFAQ, CONSTRAINTS, DECISIONS, TODO, PROGRESS, CLAUDE, WORKFLOW, ROLE_PROTOCOL)
- PM/Designer → Engineer handoff
- Starts with: prototypes, specs, design files

**tre:** System automation, quality gates, approvals
- Coming soon

### Why uno Needs CAPTURE Flows (and duo Doesn't)

**duo assumes structured input:**
- Your Figma prototype already exists
- Your Lovable app is already built
- Your PRD is already written
- **Problem:** Getting that context into Git where engineers can use it

**uno starts with chaos:**
- Unstructured thoughts ("here's what's in my head")
- Overwhelm ("everything is urgent")
- Messy inputs (photos of fridge, voice notes while commuting)
- **Problem:** Turning overwhelm into calm, actionable next steps

**The difference:**
```
duo:  STRUCTURED INPUT → Git-based handoff → Production code
uno:  CHAOS → Structure → Calm execution
```

duo solves Layer 2→3 transition (breaking the 41KB token ceiling via file-based context).

uno needs to solve Layer 0→1 transition (capturing unstructured human stress → organized delegation).

### The Cognitive Load Gap

Current uno v2.0 is excellent when you arrive with:
- ✅ Clear tasks ("book flights for March")
- ✅ Defined goals ("write intro section")
- ✅ Structured constraints ("budget is $5000")

But it struggles when you arrive with:
- ❌ Brain fog ("too much in my head, don't know where to start")
- ❌ Decision fatigue ("I'm tired of Weetbix-level choices")
- ❌ Sensory overload (toddler chaos, meeting overload, Slack explosions)

**This is where the 5 cognitive load patterns come in:** They're the missing CAPTURE layer that turns chaos into the structured input uno already handles brilliantly.

---

## Pattern Mapping

### 1. Photo/Voice-to-text → Meal Planning → Shopping List

**Current uno capability:** ❌ Not addressed

**Pattern:**
```
CAPTURE (messy) → STRUCTURE (organized) → ACTION (executable)
```

**Maps to:** pa (Personal Assistant) domain

**Enhancement needed:**
- Accept photo/voice input via new command: `..capture`
- Transform unstructured → structured lists
- Generate actionable outputs (shopping lists, booking templates)

**Implementation:**
```markdown
## New Command: ..capture

**Usage:** `..capture [type] [input]`

**Types:**
- meal: Photo/voice → meal plan → shopping list
- pack: Description → packing checklist
- trip: Ideas → itinerary structure
- task: Brain dump → prioritized TODO

**Example:**
User: "..capture meal [attaches photo of fridge]"
Claude:
1. Analyzes contents
2. Suggests 3-day meal plan
3. Generates shopping list for missing items
4. Adds to NOTES.md (if pa extension)
```

---

### 2. Brain Dump → Task Batching/Categorizing + Prioritizing

**Current uno capability:** ⚠️ Partial (TODO.md accepts structured input only)

**Pattern:**
```
UNSTRUCTURED THOUGHTS → CATEGORIZED TASKS → PRIORITY ORDER
```

**Maps to:** Core uno (all extensions)

**Enhancement needed:**
- `..start` should accept brain dump mode
- Auto-batch similar tasks
- Auto-prioritize by effort/impact

**Implementation:**
```markdown
## Enhanced: ..start --dump

**Usage:** `..start --dump "here's what's in my head..."`

**Behavior:**
1. Captures unstructured thoughts
2. Extracts discrete tasks
3. Batches by category (admin, creative, technical, etc.)
4. Assigns priority based on:
   - Urgency signals (deadline words: "ASAP", "urgent", "by Friday")
   - Effort signals (complexity words: "quick", "draft", "research")
   - Dependency detection (task A blocks task B)
5. Adds to TODO.md with AC generated
6. Reports: "I found N tasks across M categories. Top priority: X"

**Example:**
User: "..start --dump Need to email Sarah about the budget, book flights for March, write intro section for doc, oh and fix that bug in the login flow that keeps timing out"

Claude batches:
- **High Priority**
  - [C] Fix login timeout bug — blocks users
    - AC: Users can log in without timeout
    - AC: Reproduced bug is resolved
- **Medium Priority**
  - [C] Write intro section for doc
    - AC: <100 words
    - AC: Explains problem clearly
- **Low Priority**
  - [M→C] Email Sarah re: budget — needs decision
  - [C→M] Book flights for March — needs dates/preferences
```

---

### 3. Morning and Evening Flows (Energy/Neurotype/Lifestyle Match)

**Current uno capability:** ⚠️ Partial (ea has daily briefing, but not energy-aware)

**Pattern:**
```
TIME OF DAY + ENERGY LEVEL → MATCHED TASK SELECTION
```

**Maps to:** All extensions (ea, pa, km)

**Enhancement needed:**
- Profile system for energy patterns
- Task effort metadata
- Time-aware `..start`

**Implementation:**
```markdown
## New File: PROFILE.md

Created during onboarding, captures:

### Energy Pattern

| Time | Energy | Best For |
|------|--------|----------|
| 06:00-09:00 | High | Deep work, creative, strategic |
| 09:00-12:00 | Medium | Meetings, collaboration |
| 12:00-14:00 | Low | Admin, email, light tasks |
| 14:00-17:00 | Medium | Focused work, writing |
| 17:00-20:00 | Low | Planning, review, cleanup |
| 20:00-22:00 | High | Creative, side projects |

### Neurotype

- ADHD: Needs task variety, frequent wins, minimal context-switching
- Autistic: Needs routine, clear expectations, batch similar tasks
- Neurotypical: Standard prioritization

### Constraints

- Toddler schedule: 06:00-08:00 chaotic, 13:00-15:00 nap window
- Meeting blocks: Tue/Thu 10:00-12:00
- Deep work blocks: Mon/Wed/Fri 09:00-11:00

## Enhanced: ..start --flow [morning|evening]

**Morning flow:**
1. Check energy level (time-based from PROFILE.md)
2. Surface high-effort tasks if high energy
3. Surface quick wins if low energy
4. Respect constraints (toddler schedule, meeting blocks)
5. Suggest 3-task focus list matched to available energy

**Evening flow:**
1. Review what got done (celebrate wins)
2. Brain dump tomorrow's concerns → ..capture
3. Set morning priorities (3 tasks max)
4. Flag blockers for tomorrow

**Example:**
User: `..start --flow morning` (at 06:30)

Claude:
"## Morning Flow — 06:30

**Energy:** High (your best creative window)
**Available:** 1.5 hours until toddler activities
**Constraints:** Chaotic until 08:00, plan for interruptions

### Today's Focus (3 tasks)

1. **[C] Write intro section** — 30 min, creative
   - Matches: High energy, short window
2. **[C] Draft meal plan for week** — 15 min, low cognitive load
   - Matches: Can do with interruptions
3. **DEFER: Email Sarah** — Low energy task, save for 12:00-14:00

Ready to start with #1?"
```

---

### 4. Mental Offloading ("Organize What's in My Head")

**Current uno capability:** ❌ Not addressed (assumes structured input)

**Pattern:**
```
OVERWHELM → EXTERNALIZE → CATEGORIZE → CALM
```

**Maps to:** Core uno (all extensions)

**Enhancement needed:**
- Same as Pattern #2 (brain dump), but with emotional framing
- Acknowledge overwhelm, provide structure

**Implementation:**
```markdown
## Enhanced: ..offload

Alias for `..start --dump` with empathetic framing.

**Usage:** `..offload "here's everything in my head..."`

**Behavior:**
1. Acknowledge: "Got it. Let me organize this for you."
2. Extract discrete items (tasks, decisions, reminders, ideas)
3. Categorize by type:
   - **Tasks** → TODO.md (with AC)
   - **Decisions** → MAREK.md (if needs human input)
   - **Ideas** → NOTES.md (pa) or context-appropriate file
   - **Reminders** → PLANNED.md (km) or calendar items
4. Report summary: "I found N tasks, M decisions needed, P ideas. Here's what we'll tackle first..."

**Example:**
User: "..offload I'm stressed about the trip, haven't booked accommodation for the last 3 nights, need to figure out what to pack for a toddler, Sarah wants the budget numbers by Friday, and I still haven't written that intro section"

Claude:
"Got it. Let me organize this for you.

**Extracted:**
- 3 trip tasks (booking, packing)
- 1 stakeholder deadline (Sarah, Friday)
- 1 writing task

**Categorized:**

**URGENT (by Friday):**
- [M→C] Send budget numbers to Sarah
  - Decision needed: What numbers? I can draft email when you confirm

**HIGH (trip coming up):**
- [C→M] Book accommodation for nights [X-Y]
  - AC: Confirmation received for all nights
  - I can research options if you share: dates, location, budget
- [C] Create packing list for toddler trip
  - AC: All essentials covered (clothes, food, entertainment, safety)

**MEDIUM:**
- [C] Write intro section
  - AC: <100 words, explains problem

**Moved to:**
- TODO.md: 2 tasks (packing list, intro)
- MAREK.md: 2 decisions (budget, accommodation preferences)

**Next:** Want to start with the packing list (15 min, easy win)? Or make the budget decision so I can draft that email?"
```

---

### 5. Packing List for Travel with Toddler

**Current uno capability:** ⚠️ Partial (pa has NOTES.md, but no template system)

**Pattern:**
```
CONTEXT (trip + toddler) → TEMPLATE → CHECKLIST
```

**Maps to:** pa (Personal Assistant)

**Enhancement needed:**
- Template library for common scenarios
- Context-aware checklist generation

**Implementation:**
```markdown
## New: Template Library

Stored in `.uno/templates/` (optional directory for reusable checklists)

### Templates included:

- `packing-toddler.md` — Travel with young child
- `packing-business.md` — Business trip
- `meal-plan-week.md` — Weekly meal planning
- `move-checklist.md` — House move logistics
- `event-planning.md` — Hosting events

### Usage:

`..template packing-toddler --context "3 weeks Australia, Feb-Mar, warm climate"`

**Generates:**

```markdown
## Packing List: Australia Trip (Toddler)

**Context:** 3 weeks, Feb-Mar, warm climate (summer)

### Documents
- [ ] Passports (adult + toddler)
- [ ] Travel insurance docs
- [ ] Accommodation confirmations
- [ ] Emergency contacts list

### Toddler Essentials
**Clothes (warm climate):**
- [ ] 7x t-shirts/onesies
- [ ] 4x shorts
- [ ] 2x light jackets (for AC)
- [ ] 7x underwear
- [ ] 1x swimsuit
- [ ] Sun hat

**Food:**
- [ ] Snacks for flight (Weetbix, fruit pouches)
- [ ] Sippy cup
- [ ] Utensils (spoon, fork)
- [ ] Bibs (3x)

**Entertainment:**
- [ ] Favorite toys (3-4 small)
- [ ] Books (2-3)
- [ ] Tablet + headphones
- [ ] Downloaded shows/games

**Safety:**
- [ ] First aid kit (children's paracetamol, band-aids)
- [ ] Sunscreen (50+ SPF)
- [ ] Insect repellent
- [ ] Hand sanitizer

**Sleep:**
- [ ] Portable crib/travel bed (check accommodation)
- [ ] Comfort item (blanket, stuffed animal)
- [ ] White noise app/device

### Adult Items
[Standard packing list...]

---
**Added to:** BOOKINGS.md → "Pre-departure checklist"
```

### Template Customization:

After first use, Claude learns preferences:
- "Last trip you skipped the portable crib (used accommodation's). Do that again?"
- "You packed 10 Weetbix boxes last time. Same?"

Preferences stored in PROFILE.md → "Packing preferences"
```

---

## Core Enhancement: Capture → Structure → Calm

**The pattern across all 5 use cases:**

```
MESSY INPUT          STRUCTURE             CALM OUTPUT
(brain dump)    →    (categorize)     →    (clear next action)
(photo)         →    (analyze)        →    (shopping list)
(overwhelm)     →    (offload)        →    (3-task focus)
(morning chaos) →    (energy match)   →    (right task, right time)
(trip stress)   →    (template)       →    (checklist)
```

**uno's role:** Be the agent of calm in the chaos.

---

## Learning from duo: Token Budget Management

### duo's Discovery (Relevant to uno)

duo/ab protocol learned that loading all 8 markdown files cost **15% of the token budget** before any work began. They split into two roles:

- **Architect mode:** Reads strategy files (15% budget)
- **Builder mode:** Reads execution files only (5% budget)

**The insight:** Different tasks need different context. Don't load everything every time.

### How This Applies to uno v2.1

**Current uno `..start`:** Loads TODO.md, PROGRESS.md, MAREK.md, plus extension files (UPDATES.md, GLOSSARY.md, etc.)

**Problem:** When you add PROFILE.md, template preferences, energy patterns, past capture sessions, uno could hit token bloat.

**Solution: Context-aware loading**

```
..start               → Load core files only (TODO, PROGRESS, MAREK)
..start --flow        → Also load PROFILE.md (energy patterns)
..start --dump        → Also load recent PROGRESS (pattern matching)
..offload             → Load PROFILE + recent captures (learn preferences)
..template [name]     → Load template + preferences only
```

**Token budget impact:**
- Base `..start`: ~5% (current behavior)
- `..start --flow`: ~7% (adds PROFILE.md)
- `..offload`: ~8% (adds recent patterns)
- `..template`: ~3% (minimal context)

**Why this matters:** As uno grows in capability (templates, preferences, capture history), we must avoid the "load everything" trap that duo/ab discovered. Selective context loading keeps uno fast and cost-effective.

### The Broader Pattern: Layer 3 Thinking

duo teaches **Layer 3 infrastructure** (structured files, Git-based context, agent roles). uno v2.1 adopts the same philosophy:

1. **Structured files** - Each file has a purpose (PROFILE.md = energy patterns, not mixed with TODO.md)
2. **Git-managed** - Version control for preferences (rollback if energy experiment fails)
3. **Selective loading** - Commands load only the context they need
4. **Transparent** - All decisions visible in markdown, no hidden state

**The difference:**
- duo uses Layer 3 to break the 41KB ceiling (enable complex code projects)
- uno uses Layer 3 to prevent cognitive load from becoming file load

Both solve the same problem: **How do you give AI persistent memory without drowning in context?**

---

## Proposed Protocol Enhancements

### v2.1 Feature Set (Cognitive Load Protection)

#### 1. New Commands

| Command | Purpose | Priority |
|---------|---------|----------|
| `..capture [type] [input]` | Transform unstructured → structured | High |
| `..offload [dump]` | Mental offloading with empathy | High |
| `..start --flow [morning\|evening]` | Energy-aware task selection | Medium |
| `..template [name] --context [details]` | Generate contextual checklists | Medium |
| `..batch` | Group similar tasks for batch processing | Low |

#### 2. New Files

| File | Purpose | Created When |
|------|---------|--------------|
| `PROFILE.md` | Energy patterns, neurotype, constraints | Onboarding (optional) |
| `.uno/templates/` | Reusable checklist library | First template use |

#### 3. Enhanced Behaviors

**..start enhancements:**
- Accept `--dump` flag for brain dump input
- Accept `--flow` flag for energy-aware briefing
- Check PROFILE.md for energy/constraint matching
- Auto-batch similar tasks in report

**..end enhancements:**
- Prompt evening reflection if run after 17:00
- Ask "What's on your mind for tomorrow?" → auto-capture

#### 4. Extension-Specific Additions

**uno/ea (Executive Assistant):**
- Energy-aware stakeholder meeting prep
- Knowledge quiz incorporates spaced repetition
- Risk surface includes "cognitive overload" as a risk factor

**uno/pa (Personal Assistant):**
- Template library (packing, meal planning, event hosting)
- Photo → meal plan workflow
- Budget tracking with decision fatigue reduction (auto-suggest based on past choices)

**uno/km (Knowledge Manager):**
- Brain dump → LOG.md transformation
- Recurring task batching (group similar tasks on same day)
- Documentation staleness → "refresh priority" queue

---

## Implementation Priority

### Phase 1: Quick Wins (1-2 days)
- [ ] Add `..offload` command (alias for brain dump)
  - AC: Accepts unstructured input
  - AC: Categorizes into tasks/decisions/ideas/reminders
  - AC: Updates appropriate .md files
  - AC: Reports clear next action
- [ ] Document brain dump → TODO pattern in CLAUDE.md
  - AC: Example workflow included
  - AC: Integration with existing ..start command

### Phase 2: Energy Awareness (3-5 days)
- [ ] Create PROFILE.md template
  - AC: Captures energy patterns
  - AC: Captures neurotype (ADHD, autistic, neurotypical)
  - AC: Captures constraints (toddler schedule, meeting blocks)
- [ ] Add `..start --flow` variants
  - AC: Morning flow selects tasks matched to energy
  - AC: Evening flow prompts reflection + tomorrow planning
  - AC: Respects constraints from PROFILE.md
- [ ] Update README.md with energy-aware features
  - AC: Documents PROFILE.md optional file
  - AC: Documents --flow flag usage

### Phase 3: Templates (5-7 days)
- [ ] Create `.uno/templates/` directory structure
  - AC: Directory created on first template use
  - AC: Contains 5 starter templates (packing-toddler, meal-plan, etc.)
- [ ] Add `..template` command
  - AC: Lists available templates
  - AC: Generates contextualized checklist from template
  - AC: Adds to appropriate file (BOOKINGS.md, NOTES.md, etc.)
- [ ] Add template learning system
  - AC: Stores preferences in PROFILE.md → "Template preferences"
  - AC: Customizes templates based on past usage

### Phase 4: Advanced Capture (7-10 days)
- [ ] Add `..capture` command with types
  - AC: Supports meal, pack, trip, task types
  - AC: Handles photo input (if available)
  - AC: Handles voice-to-text input (if available)
  - AC: Generates structured output appropriate to type
- [ ] Add batch processing
  - AC: `..batch` groups similar tasks
  - AC: Suggests optimal time based on energy/constraints

---

## Success Metrics

**How we'll know this works:**

1. **Reduced decision fatigue:**
   - User uses `..offload` when overwhelmed → reports feeling "organized"
   - Morning `..start --flow` eliminates "what should I do first?" paralysis

2. **Better energy matching:**
   - High-effort tasks assigned to high-energy windows
   - Low-effort tasks batch to low-energy windows
   - User reports tasks feel "easier" because timing is right

3. **Fewer "Weetbix-level decisions":**
   - Templates handle recurring scenarios (packing, meals)
   - User reports spending less mental energy on logistics

4. **Faster capture → action:**
   - Brain dump → structured TODO in <2 min
   - Photo → shopping list in <5 min
   - Overwhelm → calm in <10 min

---

## Example User Journey

### Before (Current uno)

**User:** (feeling overwhelmed) "I need to plan this Australia trip but also finish work stuff and Sarah wants the budget and I don't even know what to pack..."

**Claude:** "What would you like to work on?"

**User:** (frustrated, has to structure thoughts themselves)

### After (uno v2.1 with Cognitive Load Protection)

**User:** "..offload I need to plan this Australia trip but also finish work stuff and Sarah wants the budget and I don't even know what to pack for a toddler in summer for 3 weeks"

**Claude:**
"Got it. Let me organize this for you.

**I found:**
- 1 urgent stakeholder task (Sarah → budget by Friday)
- 3 trip logistics tasks (packing, planning)
- Work tasks (you mentioned but didn't specify — want to brain dump those too?)

**Immediate actions:**

**URGENT (Friday deadline):**
→ [M→C] Confirm budget numbers for Sarah
   - I can draft the email now if you give me the numbers
   - OR: Tell me where to find them and I'll prepare the summary

**TRIP (departure in 4 weeks):**
→ [C] Generate toddler packing list for 3-week Australia trip (summer)
   - I'll use the template and customize for warm climate
   - Takes 5 min, easy win
   - Want me to do this now?

**Next:** Should I:
A) Start with packing list (quick win, reduces trip stress)
B) Draft budget email (get Sarah off your mind)
C) Capture work tasks (get everything out of your head first)

What feels most calming right now?"

---

**That's the difference:** uno becomes an agent of calm, not just a task tracker.

---

## Questions for Marek

1. **Priority:** Which phase should we implement first?
2. **PROFILE.md:** Should this be:
   - Required during onboarding?
   - Optional (created only if user wants energy-aware features)?
   - Extension-specific (only for ea/pa)?
3. **Templates:** Should we:
   - Include a starter library in the repo?
   - Let users create their own?
   - Both (starter + user-custom)?
4. **Voice/photo input:** This depends on Claude's capabilities in the environment (Desktop, Projects, etc.). Should we:
   - Document the pattern (assuming future support)?
   - Skip if not currently supported?
   - Make it extension-dependent (e.g., only pa)?
5. **Neurotype:** The ADHD/autistic/neurotypical categorization is helpful but reductive. Should we:
   - Keep it simple (3 categories)?
   - Make it freeform ("describe your work style")?
   - Use tags (#needs-variety #batch-friendly #routine-oriented)?

---

## Future Consideration: Treasury Integration

### Hypothesis: Treasury as Resource Management Layer

Based on the protocol family pattern (uno = FOR you, duo = WITH you, tre = AMONG systems), there may be a **treasury** protocol for managing resources across protocols.

### Potential Integration Points for uno

If treasury exists as a resource/budget management layer, cognitive load features would integrate naturally:

**1. Budget Tracking Across Extensions**
```
uno/pa tracks trip budget in BUDGET.md
uno/ea tracks project resources in SYSTEMS.md
treasury aggregates: "Total committed: $8,500 across 2 active uno projects"
```

**2. Time Budget Management**
```
PROFILE.md defines: "Available deep work: 10hrs/week"
treasury tracks: "Committed: 7hrs (australia-trip planning, onboarding project)"
Warns: "3hrs remaining this week"
```

**3. Cognitive Load as a Resource**
```
treasury tracks decision fatigue across all uno instances:
- "You've made 23 decisions today (typical threshold: 20)"
- "Suggest: Defer low-priority decisions to tomorrow"
- "Switch to template-based workflows (lower cognitive load)"
```

**4. Energy Budgeting**
```
PROFILE.md → treasury integration:
- "High energy budget: 2hrs/day (morning 06:00-08:00)"
- "Allocated: 1.5hrs (current tasks)"
- "Available: 0.5hrs for new work"
```

### Open Questions

1. **Does treasury exist?** (Not explicitly mentioned on kayg.ee website)
2. **If so, what does it manage?** (Financial? Time? Cognitive resources? All three?)
3. **Integration approach:**
   - uno reports to treasury (uno → treasury data flow)
   - treasury governs uno (treasury sets constraints uno respects)
   - Peer-to-peer (treasury queries uno when needed)

### Recommended Approach

**For v2.1:** Build cognitive load features standalone (no treasury dependency)
**For v2.2+:** If treasury protocol exists, add optional integration hooks

**Benefits of decoupling:**
- uno v2.1 works without treasury
- Treasury integration becomes an enhancement, not a requirement
- Users can adopt uno immediately, add treasury later if valuable

---

## Next Steps

**If approved:**

1. [M] Marek reviews this analysis
2. [M] Marek answers questions above
3. [M→C] Marek prioritizes phases (1-4 or reorder)
4. [C] Claude implements Phase 1 (quick wins)
5. [C] Claude updates CLAUDE.md, README.md with v2.1 features
6. [C] Claude tests workflow with example scenarios
7. [C→M] Claude prepares changelog for v2.1 release

**Estimated timeline:**
- Phase 1: 1-2 days
- Full v2.1: 1-2 weeks (depending on scope decisions)

---

*Analysis prepared: 2026-01-09*
*Protocol: uno v2.0 → v2.1 (proposed)*
