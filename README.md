# Claude Code Skills

A public collection of Claude Code skills by Abraham Vallez — covering engineering management, product development, and team practices.

```bash
npx skills add abrahamvallez/skills
```

Uses [skills CLI](https://github.com/vercel-labs/skills) — supports Claude Code and 40+ other AI agents (Cursor, Copilot, Codex, etc.). The CLI will prompt you to select which skills to install.

---

## Skills

| Skill | Category | What it does | Key facts |
|---|---|---|---|
| [`1on1-coach`](#1on1-coach) | Management | Analyzes a 1on1 transcript and generates 3 output documents for the manager | Auto-detects language · 7 meeting types · Fathom / Otter / plain text |
| [`bokata-research`](#bokata-research) | Product Dev | Runs context research before mapping or slicing a feature | 3 research phases · outputs `feature-context.md` |
| [`bokata-feature-mapper`](#bokata-feature-mapper) | Product Dev | Maps actors, features, and user tasks from a PRD or description | User Story Mapping · bundling heuristics · Phase 0 discovery |
| [`bokata-ac-analyst`](#bokata-ac-analyst) | Product Dev | Generates Gherkin acceptance criteria from a Features Backbone | Rule-first · happy path + edge cases + permissions |
| [`bokata-feature-slicer`](#bokata-feature-slicer) | Product Dev | Decomposes a feature into a Walking Skeleton + Increments Backlog | 16+ slicing strategies · Walking Skeleton buildable in 1–3 days |
| [`product-discovery-ost`](#product-discovery-ost) | Product Dev | Turns specs, notes, transcripts or idea dumps into an Opportunity Solution Tree with ICE-scored solutions | Teresa Torres + Itamar Gilad · qualitative opportunity assessment · adapts to non-corporate contexts |
| [`the-mom-test`](#the-mom-test) | Product Dev | Writes, reviews and evaluates customer/user interviews, questions and discovery evidence using The Mom Test | 6 modes (prepare · review questions · evaluate interviews · evidence audit · live coach · batch review) · Spanish/English · based on Rob Fitzpatrick's book |

---

## 1on1-coach

**Category:** Management

Analyzes a 1on1 meeting transcript and produces three output documents:

| File | Audience | Contents |
|---|---|---|
| `outputs/shareable/{date}-{name}-summary.md` | Team member | Neutral recap, key points, verbatim quotes, action items |
| `outputs/coaching/{date}-{name}-analysis.md` | Manager (private) | Meeting effectiveness, Radical Candor quadrant, risks, improvement areas |
| `outputs/coaching/{date}-{name}-coaching.md` | Manager (private) | Socratic questions to reflect and prepare for the next meeting |

**Meeting types:** `check-in` · `career` · `unblocking` · `feedback` · `conflict` · `onboarding` · `mixed`

**Language:** auto-detected from the transcript. Override with `lang=es`, `lang=en`, etc.

**Compatible with:** Fathom, Otter.ai, and any plain-text transcript format.

**Usage:**
```
Analyze this 1on1: transcripts/2026-04-28-carlos.txt
```
```
Run 1on1-coach on my Fathom transcript from today's check-in with Alex
```
```
Process transcripts/2026-04-10-paula.txt lang=en
```

---

## bokata-research

**Category:** Product Dev · Bokata Framework

Runs three research phases to produce `feature-context.md` — a context document that enriches all downstream Bokata skills.

| Phase | What it produces |
|---|---|
| Feature Research | Domain vocabulary, actors, existing patterns |
| Criteria Research | Business rules, permissions, state transitions per task |
| Slicer Research | Tech stack, architecture constraints, available libraries |

Run this once per initiative, before `bokata-feature-mapper` or `bokata-feature-slicer`.

**Usage:**
```
Run bokata-research for this initiative:
[paste PRD or description]
```

---

## bokata-feature-mapper

**Category:** Product Dev · Bokata Framework

Maps a PRD or initiative description into a structured **Features Backbone** using User Story Mapping methodology.

- Features in `[Actor] [Verb] [Object]` format
- User Tasks in `[Verb] [Object]` format (actor inherited from feature)
- Phase 0 discovery: asks clarifying questions or documents assumptions
- Bundling heuristics: detects tasks merged into one that should be split

**Output:** `## Features Backbone` with features, user tasks, system tasks, and a dependency map.

**Usage:**
```
Run bokata-feature-mapper:
[paste PRD, description, or conversation context]
```
```
Run bokata-feature-mapper with this enriched context:
[paste PRD]

## Feature Research Summary
[paste bokata-research output]
```

---

## bokata-ac-analyst

**Category:** Product Dev · Bokata Framework

Generates Gherkin acceptance criteria (Given/When/Then) for a set of User Tasks using Feature Mapping and Example Mapping.

- Rule-first: defines business rules before writing scenarios
- Covers happy path, error states, edge cases, and permission boundaries
- Output scenarios are cross-linked to backbone IDs

**Usage:**
```
Run bokata-ac-analyst for these User Tasks:
- Create Match
- Join Match
- Leave Match
```
```
Run bokata-ac-analyst:
[paste ## Features Backbone section]

## Criteria Research Summary
[paste bokata-research output]
```

---

## bokata-feature-slicer

**Category:** Product Dev · Bokata Framework

Takes a single feature and decomposes it into a **Walking Skeleton** + **Increments Backlog** using Vertical Slicing (the Hamburger Method).

- **Walking Skeleton:** thinnest end-to-end slice that touches all layers — buildable in 1–3 days, ships to production
- **Increments Backlog:** prioritized list of follow-on slices building on top of the skeleton
- Uses 16+ breakdown strategies: Zero/One/Many, Dummy to Dynamic, SPIDR, Workflow Simplification, and more — see [`breakdown-strategies.md`](skills/bokata-feature-slicer/resources/breakdown-strategies.md)

**Usage:**
```
Run bokata-feature-slicer:
[paste Feature definition with User Tasks]
```
```
Run bokata-feature-slicer with --show-steps:
[paste Feature definition]

## Slicer Research Summary
[paste bokata-research output]
```

Use `--show-steps`, `--show-increments`, or `--show-all` to surface intermediate phases.

**Output structure:**
```
docs/<initiative>/slices/<FEAT-ID>-<name>.md   ← Walking Skeleton + Backlog
docs/<initiative>/walking-skeleton-plan.md      ← Consolidated plan across features
```

---

## product-discovery-ost

**Category:** Product Dev

Takes any raw material (spec, meeting notes, interview transcript, brainstorming dump, feature list) and produces a complete Opportunity Solution Tree analysis in markdown:

- Prioritized **opportunities**, assessed qualitatively by comparing siblings (Teresa Torres, *Continuous Discovery Habits*)
- **Solutions** scored with a simplified 1–4 ICE scale (Itamar Gilad)
- Detailed descriptions, assumptions, experiments, and summary tables with a roadmap

Language follows the input (Spanish, Catalan, English...). Torres criteria can be adapted to NGOs, unions, cooperatives and public sector (see `references/torres-adaptation.md`).

**Usage:**
```
Run product-discovery-ost on these meeting notes: notes/2026-09-30-discovery.md
```
```
Build an OST from this brainstorming list and score the solutions with ICE
```

---

## the-mom-test

**Category:** Product Dev

A discovery-conversation coach grounded in *The Mom Test* (Rob Fitzpatrick). It helps you ask questions people can't lie about, spot bad data (compliments, fluff, ideas), and decide the next step. Six modes:

| Mode | You provide | You get |
|---|---|---|
| **Prepare** | Segment / idea / stage | Big-3 learning goals (incl. a scary one), conversation flow with concrete questions, do-not-say list, commitment to ask for, framing message, note-taking setup |
| **Review questions** | A list of questions or a guide | Verdict per question (✅/⚠️/❌), rule broken, rewrite, missing questions |
| **Evaluate interview / communication** | Transcript, notes, email, message | Succeeded/failed verdict, facts vs compliments/fluff/ideas, interviewer errors with better lines, missed digs, commitments, next steps |
| **Evidence audit** | "Everyone loves it", survey results, discovery summary | What is validated / not / unknown, segment and risk checks, cheapest next conversations |
| **Live coach** | What the person just said | 3 exact follow-up lines (anchor · dig · scary/commitment) |
| **Batch review** | Notes from several conversations | Themes, consistency/segment check, beliefs updated, next Big 3 |

Replies in the user's language. Book content is paraphrased with chapter pointers in `references/`; skill-specific additions are marked **[skill heuristic]**. Pairs well with `product-discovery-ost` (evidence in, opportunities out).

**Usage:**
```
Prepare interviews for amateur basketball coaches to learn how they review games
```
```
Review these questions with the mom test: evals/the-mom-test/inputs/02-question-list.md
```
```
Evaluate this transcript: transcripts/2026-10-01-marta.txt
```
```
They said "seguro que lo compraría" — what do I ask now?
```

---

## Bokata Agents

Agents are orchestration wrappers that chain Bokata skills together and handle file I/O automatically. Skills can also be invoked standalone.

### `bokata-mapper-specialist`

Runs the full features pipeline for an initiative: scaffolds folders, invokes `bokata-research` → `bokata-feature-mapper` → `bokata-ac-analyst`, assigns deterministic IDs, writes `docs/<initiative>/features.md`.

```
Run bokata-mapper-specialist for initiative "basket-chess". The PRD is in docs/PRD.md.
```

### `bokata-slicer-specialist`

Slices a single feature: reads `features.md`, invokes `bokata-feature-slicer`, writes `docs/<initiative>/slices/<FEAT-ID>-<name>.md`, updates `walking-skeleton-plan.md`.

```
Run bokata-slicer-specialist. Slice "Player Executes Game Turn" from initiative basket-chess.
Slice BKC-FEAT-f16d from initiative basket-chess.
```

---

## Credits & Inspiration

Skills and agents architecture inspired by [eferro/skill-factory](https://github.com/eferro/skill-factory/tree/main).

`the-mom-test` is based on *The Mom Test* by [Rob Fitzpatrick](https://www.momtestbook.com/); the skill is an independent paraphrased working aid, not a substitute for the book.

## License

MIT — see [LICENSE](LICENSE).
