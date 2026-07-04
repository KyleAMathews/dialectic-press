# Sloptractions Skill Enhancement: Styleguide, Voice Profiles, and Ablation Testing

**Date:** 2026-07-04  
**Status:** Design approved, pending implementation

## Problem

The sloptractions skill produces essays from dialectic outputs, but has several gaps:

1. **Positive constraints are vague and unenforced** — style guide says "be conversational" but doesn't specify concrete patterns or test for them
2. **Author voice not captured** — generic good-prose advice exists, but Kyle's specific voice patterns are not documented or enforced
3. **No ablation testing** — components aren't tested for whether they're load-bearing
4. **Single-shot generation** — Phase 5 writes once, Phase 6 validates; no iterative refinement
5. **Meso-level density not measured** — Rao's "pleasurable over summarizable" criterion isn't tested
6. **High-value dialectic material leaks** — personal grounding and misfits don't have explicit preservation mechanisms

## Solution Overview

Three-layer architecture:

1. **Reference docs** — voice profiles, ablation protocol, Kyle's pattern map (stable, rarely change)
2. **Phase files** — embed key constraints, point to reference docs for depth
3. **Validation checklist** — comprehensive, tests everything the style guide describes

## New Files

### 1. `reference/ablation-testing.md`

Two types of ablation testing:

**Structural Ablation (component-level)**

Tests whether components do work or are decorative. For each test:
- Spawn a fresh subagent with no context from siblings
- Provide only the modified text (component removed) and the comprehension question
- Run all tests in parallel (no sequential context bleed)

| Component | Remove | Ask Subagent | If Comprehension Survives |
|-----------|--------|--------------|---------------------------|
| Analogy | Strip analogy vocabulary | "Summarize the argument" | Analogy is decorative |
| Coined term | Replace with placeholder | "What's the key distinction?" | Term isn't compressing |
| Synthesis | Remove synthesis section | "What's the insight?" | Synthesis is restating |
| Examples | Remove examples | "Why should I believe this?" | Examples are garnish |
| Hook | Remove opening | "What problem is being solved?" | Hook isn't grounding stakes |

**Meso-Level Ablation (density)**

Tests whether text rewards close reading or is all overstory.

| Test | Method | Interpretation |
|------|--------|----------------|
| Summarize-and-compare | Subagent summarizes in 100 words | What orientation-relevant info is lost? |
| Pleasurability | "What do you get from close reading that you wouldn't get from a summary?" | If "not much" → lacks understory |

**When to use:**
- Phases 1-4: Ablation as discovery (learn what you're actually saying)
- Phase 6: Ablation as validation (verify components are load-bearing)

### 2. `reference/voice-profiles.md`

**Default Profile:** Kyle (see `reference/kyle-voice.md`)

**Alternate Profiles:**

| Voice | Key Features | Best For |
|-------|--------------|----------|
| Paul Graham | Deceptively simple, exploratory "I", short paragraphs | Counterintuitive takes, startup essays |
| Scott Alexander | Exhaustive thoroughness, constant humor, structural variety | Deep dives, contested topics |
| Joan Didion | Sparse declarative sentences, omission as power, detached irony | Personal essays, mood over argument |
| George Orwell | Plain prose, no hedging, concrete over abstract | Polemics, moral clarity |
| Gwern | Dense citations, quantitative rigor, impersonal, long-form | Technical deep dives, meta-analyses |
| Matt Levine | Dry wit on technical subjects, absurdist examples | Making boring things interesting |

**Voice Taxonomy (4 axes):**
- Conversational ↔ Authoritative
- Exploratory ↔ Declarative
- Spare ↔ Exhaustive
- Visible author ↔ Receding author

**Blending Syntax:** "70% Kyle, 30% Gwern density" — apply Kyle's patterns but increase citation/link density

**Selection:** Default is Kyle. Override at Phase 5 if essay content suits different voice.

### 3. `reference/kyle-voice.md`

**Pattern Map:**

| Pattern | What Kyle Does | Example |
|---------|----------------|---------|
| Openings | Personal situation → broader significance. Never thesis-first. | "My wife and I often talk about the difficulty of making friends as adults." |
| Paragraphs | Short-to-medium, liberal subheadings, lists break density | |
| First person | Frequent natural "I" and "we", author always visibly present | "I've been loosely involved...", "I realized that..." |
| Questions | Structural transitions, genuine invitations, asks then answers | "Why is this happening now? My general model..." |
| Hedging | Confident but not arrogant. "My preferred theory atm is..." | |
| Reader relationship | Fellow traveler thinking out loud, not teacher | |
| Sentences | Clean, direct, occasional em-dashes, sparing parentheticals | |
| Technical | Assumes technical reader, explains briefly, links out liberally | |
| Endings | Questions, invitations to engage, forward-looking — no tidy summaries | "If you're interested, please reach out" |
| Absent patterns | No throat-clearing, no listicle bookends, no jargon peacocking | |

**Axis Positioning:**
- 70% conversational
- 65% exploratory
- 60% spare
- 75% visible author

**Annotated Exemplars:** 3-5 passages with margin notes showing patterns in action. (To be extracted from blog corpus during implementation.)

## Updates to Existing Files

### `reference/style-guide.md`

**Add: Positive Constraints Section**

| Pattern | Concrete Constraint |
|---------|---------------------|
| Opening | Start 40%+ of essays with personal situation or concrete observation |
| Questions | Include at least one genuine question you don't know the answer to |
| First person | "I" should appear in first 100 words |
| Paragraphs | No paragraph over 5 sentences; at least one 1-2 sentence paragraph per 500 words |
| Endings | End with question, invitation, or forward-looking statement — not summary |
| Hedging | Use "I think" / "my sense is" to mark opinion; be declarative on observations |

**Add: Measurable Metrics Section**

| Metric | Target |
|--------|--------|
| Sentence length variance | Std dev > 8 words |
| Em-dash usage | 1-3 per 1000 words |
| First-person in first 100 words | Yes |
| Cliché count | 0 from banned list |
| "Delve/crucial/important to note" | 0 |

**Add: AI-ism Detection Section**

Patterns to scan for and remove:
- "quiet" as emotional filler
- Unsolicited validation ("You're not alone")
- "Bold Header: explanation" list format
- Excessive internal coherence (too smooth)
- Neutral emotional temperature on topics that warrant stance

### `phases/1-inventory.md`

**Add: Personal Material Extraction**

The dialectic produces structural insight but not personal grounding. Extract or ask:

| Constraint | Source |
|------------|--------|
| Personal situation opening | Ask: "What's your personal connection to this topic?" |
| Concrete observation | Look in context briefing; if abstract, ask for specific example |
| Genuine question | Check misfit register; ask: "What's still genuinely unclear to you?" |
| Lived experience details | Ask: "Any specific names, dates, places, projects?" |

Present at checkpoint alongside hook candidates, surprising turn, etc.

**Add: Ablation-as-Discovery**

Before checkpoint:
- Remove Monk A's material → is Monk B sufficient alone?
- Remove synthesis → is hook + monks still interesting?

### `phases/2-analogy.md`

**Add: Ablation Test for Analogies**

For each candidate, sketch argument without analogy vocabulary. If argument still makes sense → analogy is decorative. Only present analogies that fail this test.

### `phases/3-concepts.md`

**Add: Ablation Test for Terms**

For each coined term, explain key distinction without using the term. If still clear → term is labeling, not compressing. Keep only terms where removal causes loss.

### `phases/4-outline.md`

**Add: Personal Material Placement**

Map personal material from Phase 1 into arc:
- Personal situation → Hook
- Concrete observation → Hook or Structural Unpacking
- Genuine question → Stakes or throughout
- Lived experience details → wherever they ground abstraction

If Phase 1 didn't surface enough, pause and ask.

### `phases/5-write.md`

**Add: Voice Profile Selection**

Before writing, confirm voice:
- Default: Kyle voice (see `reference/kyle-voice.md`)
- Override: Select alternate or blend (see `reference/voice-profiles.md`)
- Blend syntax: "70% Kyle, 30% Gwern density"

**Replace single-shot with: Iterative Refinement Loop**

1. Write draft
2. Self-critique: "Where would I skim? Where am I hedging? Where is this generic?"
3. Revise those sections
4. Meso-level ablation: summarize → compare → identify understory loss
5. If loss is low, add density to thin sections
6. Proceed to Phase 6

### `phases/6-validate.md`

**Add to Validation Checklist:**

| Test | Method | Fail Action |
|------|--------|-------------|
| Voice fidelity | Compare against `kyle-voice.md` | Line-edit for voice |
| Cliché scan | Check banned list | Remove/replace |
| Throat-clearing | Check first paragraph of each section | Cut |
| AI-ism detection | Scan for known patterns | Add grit |
| First/last line strength | Read in isolation | Strengthen |
| Positive constraints | First-person in 100 words? Genuine question? Invitation ending? | Add if missing |
| Meso-level density | Summarize → compare → measure loss | Add understory if low loss |

**Add: Structural Ablation Suite**

Spawn 5+ parallel fresh subagents, each with one component removed:

```
Agent 1: [analogy stripped] → "Summarize the argument"
Agent 2: [terms replaced] → "What's the key distinction?"
Agent 3: [synthesis removed] → "What's the insight?"
Agent 4: [examples removed] → "Why should I believe this?"
Agent 5: [hook removed] → "What problem is being solved?"
Agent 6: [full draft] → "Summarize in 100 words"
Agent 7: [full draft] → "What do you get from close reading vs summary?"
```

Report results to user. User decides what to strengthen vs. cut.

## Architecture Principles

1. **Density through constraint accumulation** — each phase adds tests that eliminate lazy writing modes
2. **Voice as selectable profile** — default (Kyle) with optional overrides/blends at Phase 5
3. **Ablation as discovery and validation** — early phases learn what you're saying; Phase 6 verifies
4. **Decorrelation** — ablation tests use parallel fresh subagents, no context bleed
5. **Meso-level density** — summarize-and-compare test; loss = success
6. **Personal material is required input** — Phase 1 extracts/asks; constraints enforce

## Implementation Order

1. Create `reference/ablation-testing.md`
2. Create `reference/voice-profiles.md`
3. Create `reference/kyle-voice.md` (extract exemplars from blog)
4. Update `reference/style-guide.md` (positive constraints, metrics, AI-isms)
5. Update phases 1-4 (personal material, ablation hooks)
6. Update phase 5 (voice selection, iterative loop)
7. Update phase 6 (expanded checklist, ablation suite)

## Open Questions

None — design approved.
