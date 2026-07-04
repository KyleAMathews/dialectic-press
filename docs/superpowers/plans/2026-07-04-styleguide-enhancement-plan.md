# Styleguide Enhancement Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Enhance the sloptractions skill with voice profiles, ablation testing, and stronger density enforcement.

**Architecture:** Three new reference docs (ablation-testing, voice-profiles, kyle-voice), updates to style-guide.md with positive constraints and metrics, and updates to all six phase files with interview questions, ablation hooks, and expanded validation.

**Tech Stack:** Markdown files only — no code changes.

## Global Constraints

- All files are in `/Users/kylemathews/programs/sloptractions-skill/`
- Reference docs go in `reference/`
- Phase files are in `phases/`
- Commit after each task
- No tests required (documentation-only changes)

---

### Task 1: Create `reference/ablation-testing.md`

**Files:**
- Create: `reference/ablation-testing.md`

**Interfaces:**
- Produces: Ablation protocol referenced by phases 1-6

- [ ] **Step 1: Create the ablation testing reference doc**

```markdown
# Ablation Testing

Ablation testing determines whether essay components are load-bearing or decorative. Two types:

## Structural Ablation (Component-Level)

Tests whether removing a component breaks comprehension.

**Protocol:**
1. Spawn a fresh subagent per test — no context from siblings
2. Provide only the modified text (component removed) and the comprehension question
3. Run all tests in parallel (no sequential context bleed)
4. Collect results and present to user

**Tests:**

| Component | How to Remove | Ask Subagent | If Comprehension Survives |
|-----------|---------------|--------------|---------------------------|
| Analogy | Strip analogy vocabulary throughout | "Summarize the argument in 2-3 sentences." | Analogy is decorative — strengthen or cut |
| Coined term | Replace all instances with "[TERM]" placeholder | "What's the key distinction this essay draws?" | Term is labeling, not compressing — cut |
| Synthesis | Remove the synthesis/reframing section | "What's the insight or reframing?" | Synthesis is restating, not elevating — sharpen |
| Examples | Remove all examples and evidence | "Why should I believe this argument?" | Examples are garnish — either strengthen or essay is too abstract |
| Hook | Remove the opening section | "What problem is this essay addressing?" | Hook isn't grounding stakes — strengthen |

**Interpretation:**
- Comprehension fails → component is load-bearing ✓
- Comprehension succeeds → component is decorative, needs strengthening or cutting

## Meso-Level Ablation (Density)

Tests whether text rewards close reading or is all overstory (Rao's "pleasurable over summarizable").

**Protocol:**
1. Spawn two fresh subagents in parallel
2. Agent A: Full draft → "Summarize this in 100 words."
3. Agent B: Full draft → "What do you get from close reading that you wouldn't get from a summary?"

**Interpretation:**
- If Agent B says "not much" or lists only surface-level details → draft lacks understory density
- The *loss* in summarization is the measure of meso-level success
- High-density text has orientation-relevant information that can't be compressed

## When to Use

| Phase | Ablation Type | Purpose |
|-------|---------------|---------|
| Phase 1 (Inventory) | Structural | Discovery — is Monk A necessary? Does synthesis add? |
| Phase 2 (Analogy) | Structural | Test candidate analogies before presenting |
| Phase 3 (Concepts) | Structural | Test coined terms before committing |
| Phase 5 (Write) | Meso-level | After draft, check density |
| Phase 6 (Validate) | Both | Full ablation suite on finished draft |

## Subagent Spawn Pattern

```
# Structural ablation — spawn in parallel
Agent 1: [analogy stripped] → "Summarize the argument in 2-3 sentences."
Agent 2: [terms replaced with placeholder] → "What's the key distinction this essay draws?"
Agent 3: [synthesis removed] → "What's the insight or reframing?"
Agent 4: [examples removed] → "Why should I believe this argument?"
Agent 5: [hook removed] → "What problem is this essay addressing?"

# Meso-level ablation — spawn in parallel
Agent 6: [full draft] → "Summarize this in 100 words."
Agent 7: [full draft] → "What do you get from close reading that you wouldn't get from a summary?"
```

Each agent is fresh — no shared context. Report results to user. User decides what to strengthen vs. cut.
```

- [ ] **Step 2: Commit**

```bash
cd /Users/kylemathews/programs/sloptractions-skill
git add reference/ablation-testing.md
git commit -m "Add ablation testing reference doc

Two types: structural (component knockout) and meso-level (density).
Protocol for parallel subagent spawning with no context bleed."
```

---

### Task 2: Create `reference/voice-profiles.md`

**Files:**
- Create: `reference/voice-profiles.md`

**Interfaces:**
- Produces: Voice profile system referenced by Phase 5

- [ ] **Step 1: Create the voice profiles reference doc**

```markdown
# Voice Profiles

Voice profiles shape prose generation. Select at Phase 5 (Write).

## Default Profile

**Kyle** — see `reference/kyle-voice.md` for full pattern map and exemplars.

Summary: Conversational, exploratory, visible author, fellow-traveler tone. Opens with personal situation, uses questions as transitions, ends with invitations.

## Alternate Profiles

| Voice | Key Features | Best For |
|-------|--------------|----------|
| **Paul Graham** | Deceptively simple prose, exploratory "I", short paragraphs, conclusions emerge rather than announce | Counterintuitive takes, startup essays, essays that discover their point |
| **Scott Alexander** | Exhaustive thoroughness, constant humor and wit, structural variety (lists, dialogues, numbered points), step-by-step reasoning | Deep dives, contested topics, book reviews, anything requiring exhaustive treatment |
| **Joan Didion** | Sparse declarative sentences, omission as power, detached irony, carefully selected details evoke larger themes | Personal essays with cultural observation, mood over argument, restraint |
| **George Orwell** | Plain prose as moral commitment, no hedging, concrete over abstract, short words, everyday English | Polemics, political commentary, moral clarity, making evasion impossible |
| **Gwern** | Dense with citations and hyperlinks, quantitative rigor, explicit uncertainty, impersonal voice, long-form patience | Technical deep dives, meta-analyses, topics requiring extensive citation |
| **Matt Levine** | Dry wit on technical subjects, absurdist examples to explain mechanisms, conversational asides, running jokes | Making boring things interesting, technical explanations for general audiences |

## Voice Taxonomy (4 Axes)

Position any voice on these axes:

| Axis | Spectrum |
|------|----------|
| Stance toward reader | Conversational ↔ Authoritative |
| Relationship to uncertainty | Exploratory/hedged ↔ Declarative |
| Density | Spare ↔ Exhaustive |
| Author presence | Visible ↔ Receding |

**Kyle's position:** 70% conversational, 65% exploratory, 60% spare, 75% visible

## Blending Voices

Syntax: "70% Kyle, 30% Gwern density"

This means: Apply Kyle's patterns (openings, questions, fellow-traveler tone) but increase citation/link density and add more explicit uncertainty markers.

Common blends:
- "Kyle + Gwern density" — more links and citations
- "Kyle + Orwell directness" — less hedging, more declarative
- "Kyle + Scott Alexander thoroughness" — more exhaustive treatment

## Selection Guide

| Writing Motivation | Suggested Voice |
|--------------------|-----------------|
| Aesthetic enthusiasm | Didion, Kyle |
| Political purpose | Orwell |
| Historical impulse | Gwern |
| Community-finding | Kyle, Paul Graham |
| Technical explanation | Matt Levine, Gwern |
| Counterintuitive take | Paul Graham |
| Deep dive | Scott Alexander |

## Adding Custom Profiles

To add a new profile:
1. Read 5-10 pieces from the target author
2. Extract patterns across the 10 categories in kyle-voice.md
3. Position on the 4 axes
4. Add 2-3 annotated exemplar passages
5. Add to the alternate profiles table with "Best For" guidance
```

- [ ] **Step 2: Commit**

```bash
cd /Users/kylemathews/programs/sloptractions-skill
git add reference/voice-profiles.md
git commit -m "Add voice profiles reference doc

Default: Kyle. Six alternates: Graham, Scott Alexander, Didion, Orwell, Gwern, Levine.
Four-axis taxonomy and blending syntax."
```

---

### Task 3: Create `reference/kyle-voice.md`

**Files:**
- Create: `reference/kyle-voice.md`

**Interfaces:**
- Produces: Kyle's voice profile referenced by voice-profiles.md and Phase 5

- [ ] **Step 1: Create Kyle's voice profile with exemplars**

```markdown
# Kyle's Voice Profile

The default voice for sloptractions essays.

## Pattern Map

| Pattern | What Kyle Does | Example |
|---------|----------------|---------|
| **Openings** | Personal situation → broader significance. Never thesis-first. | "My wife and I often talk about the difficulty of making friends as adults." |
| **Paragraphs** | Short-to-medium (2-4 sentences typical), liberal subheadings, lists break density | |
| **First person** | Frequent natural "I" and "we", author always visibly present | "I've been loosely involved...", "I realized that...", "My preferred theory atm is..." |
| **Questions** | Structural transitions, genuine invitations, asks then answers | "Why is this happening now? My general model for change..." |
| **Hedging** | Confident but not arrogant. Marks opinion explicitly. | "My preferred theory atm is...", "I think we should...", "I'm convinced..." |
| **Reader relationship** | Fellow traveler thinking out loud, not teacher. Shares evolving understanding. | |
| **Sentences** | Clean, direct, occasional em-dashes for interjection, sparing parentheticals | "Ice cream, while delicious, is not perhaps the key component of a healthy balanced diet." |
| **Technical** | Assumes technical reader, explains concepts briefly, links out liberally rather than over-explaining | |
| **Endings** | Questions, invitations to engage, forward-looking — no tidy summaries | "If you're interested or have thoughts, please reach out, I'd love to chat." |
| **Absent patterns** | No throat-clearing, no listicle bookends ("In this post I will..."), no jargon peacocking, no self-deprecation | |

## Axis Positioning

| Axis | Position |
|------|----------|
| Conversational ↔ Authoritative | 70% conversational |
| Exploratory ↔ Declarative | 65% exploratory |
| Spare ↔ Exhaustive | 60% spare |
| Visible ↔ Receding | 75% visible |

## Annotated Exemplars

### Exemplar 1: Personal Opening → Broader Significance

> My wife and I often talk about the difficulty of making friends as adults. There's lots of articles online about this so I won't rehash them — what's been on my mind recently is that the root of the problem is broader than it appears, and understanding that root leads to novel solutions.
>
> The root issue is that we've collectively forgotten how to run complex social arrangements.

**Patterns present:**
- Opens with personal situation (talking with wife)
- Quickly zooms to broader significance (collective forgetting)
- "what's been on my mind recently" — thinking out loud
- Em-dash for interjection
- No throat-clearing, jumps straight in

### Exemplar 2: Question as Transition

> But we're not going to stop watching TV or scrolling through feeds. So how can our society bootstrap the individual skills and group social capital necessary for the vast majority of people to have great social experiences and to keep solving all the problems reality keeps throwing at us?

**Patterns present:**
- Acknowledges reality constraint first
- Genuine question (not rhetorical) as transition
- Stakes embedded in the question
- "throwing at us" — casual, conversational

### Exemplar 3: Confident Hedging

> There's a lot of discussion about why this is happening. My preferred theory atm is it's a combination of _scaling problems_ — institutional practices invented in the previous decades and centuries are not scaling well as the world grows larger and more complex.

**Patterns present:**
- "My preferred theory atm" — marks opinion, but still confident
- Italics for emphasis on key concept
- Em-dash to elaborate
- Doesn't oversell ("a combination of" not "the answer is")

### Exemplar 4: Fellow Traveler Ending

> My main question now is if there's a there there. This is a complex space with a lot of history. If you're interested or have thoughts — please reach out, I'd love to chat.

**Patterns present:**
- Admits uncertainty ("if there's a there there")
- Acknowledges complexity without claiming to have solved it
- Invitation to engage
- Warm, direct close

### Exemplar 5: Technical + Personal

> We had our first child last August (pandemic baby, baby). As a treat, I fulfilled a childhood dream and bought a fancy ice cream maker. Which ended up being great fun as the fresh ice cream helped distract / soothe our stressed / exhausted new parent brains.

**Patterns present:**
- Personal detail grounds technical/project discussion
- Parenthetical humor ("pandemic baby, baby")
- Fragment for rhythm ("Which ended up...")
- Slashes for casual enumeration
- Vulnerable detail (stressed/exhausted)

## Anti-Patterns (What Feels Off)

If the prose does any of these, it doesn't sound like Kyle:

- Opens with thesis statement or "In this essay I will..."
- Uses "we" to mean "society" without personal grounding
- Hedges excessively ("It might perhaps be argued that...")
- Teacher mode ("Let me explain why...")
- Tidy summary ending ("In conclusion...")
- Jargon without links or brief explanation
- No questions throughout
- No "I" in first 100 words
- Every paragraph same length
- No em-dashes
```

- [ ] **Step 2: Commit**

```bash
cd /Users/kylemathews/programs/sloptractions-skill
git add reference/kyle-voice.md
git commit -m "Add Kyle's voice profile with annotated exemplars

10-pattern map, 4-axis positioning, 5 annotated exemplars from blog,
anti-patterns section for what feels off."
```

---

### Task 4: Update `reference/style-guide.md`

**Files:**
- Modify: `reference/style-guide.md` (append new sections)

**Interfaces:**
- Consumes: Existing style guide content
- Produces: Positive constraints, metrics, AI-ism detection sections

- [ ] **Step 1: Read current end of style-guide.md to find insertion point**

The file ends with "Prose Diagnostics" section. Append new sections after that.

- [ ] **Step 2: Append positive constraints, metrics, and AI-ism detection sections**

Add to end of `reference/style-guide.md`:

```markdown

---

## Positive Constraints

Concrete patterns to enforce, not just avoid. These are testable at validation.

| Pattern | Concrete Constraint |
|---------|---------------------|
| Opening | Start 40%+ of essays with personal situation or concrete observation |
| Questions | Include at least one genuine question you don't know the answer to |
| First person | "I" should appear in first 100 words |
| Paragraphs | No paragraph over 5 sentences; at least one 1-2 sentence paragraph per 500 words |
| Endings | End with question, invitation, or forward-looking statement — not summary |
| Hedging | Use "I think" / "my sense is" to mark opinion; be declarative on observations |

---

## Measurable Metrics

Quantitative checks for validation phase.

| Metric | Target | How to Check |
|--------|--------|--------------|
| Sentence length variance | Std dev > 8 words | Count words per sentence, compute std dev |
| Em-dash usage | 1-3 per 1000 words | Count "—" occurrences |
| First-person in first 100 words | Yes | Check first 100 words for "I" |
| Cliché count | 0 from banned list | Scan against Cliché Avoidance section |
| "Delve/crucial/important to note" | 0 | Literal string search |

---

## AI-ism Detection

Patterns that signal AI-generated prose. Scan and remove.

**Word-level:**
- "quiet" as emotional filler ("a quiet satisfaction")
- "delve" / "delve into"
- "crucial" / "crucially"
- "it's important to note"
- "nestled"
- "tapestry"
- "multifaceted"

**Structural:**
- Unsolicited validation ("You're not alone", "This is completely normal")
- "Bold Header: explanation" list format (every list item starts with bolded phrase)
- Excessive internal coherence (too smooth, no friction)
- Neutral emotional temperature on topics that warrant stance
- Parallelism overdone (every sentence same structure)

**Tonal:**
- Relentless positivity without acknowledging difficulty
- Hedging without conviction ("It could perhaps be argued...")
- Summarizing what was just said
- "In conclusion" / "To summarize" / "In this essay we explored"

**The fix:** When you spot these, either delete or replace with something specific and textured. Add "grit" — oddly specific details, throwaway numbers, stances that might alienate someone.
```

- [ ] **Step 3: Commit**

```bash
cd /Users/kylemathews/programs/sloptractions-skill
git add reference/style-guide.md
git commit -m "Add positive constraints, metrics, and AI-ism detection to style guide

Positive constraints: testable patterns (opening, questions, first-person, etc.)
Metrics: quantitative checks (sentence variance, em-dash usage, etc.)
AI-isms: word-level, structural, and tonal patterns to detect and remove."
```

---

### Task 5: Update `phases/1-inventory.md`

**Files:**
- Modify: `phases/1-inventory.md` (insert new sections before Checkpoint)

**Interfaces:**
- Consumes: Existing inventory phase structure
- Produces: Writing motivation interview, personal material extraction, ablation-as-discovery

- [ ] **Step 1: Find insertion point**

Insert new sections after "## Extract Key Elements" and before "## Exploratory 2×2s".

- [ ] **Step 2: Insert "Why Are You Writing This?" interview section**

Add after "### 5. The Best Material" section:

```markdown

---

## Why Are You Writing This?

The dialectic surfaces what you're wrestling with, but not why you're writing about it. This shapes everything downstream.

**Interview the user:**

| Question | What It Reveals |
|----------|-----------------|
| "Why are you writing this particular piece?" | Dominant motive |
| "Who is your intended reader? What do they already know/believe?" | Audience, assumptions |
| "What do you want to happen after someone reads it?" | Action vs. making vs. labor |
| "Is this entering an existing conversation or starting a new one?" | Arendtian action level |
| "What would failure look like for this piece?" | What success actually is |

**Map responses to frameworks:**

**Orwell's Four Motives:**
- Sheer egoism — be remembered, get your own back
- Aesthetic enthusiasm — beauty in words, right arrangement
- Historical impulse — preserve truth for posterity
- Political purpose — push the world in a direction

**Arendtian Action Level (Rao/Arendt):**
- Laboring — private processing, personal need
- Making — producing an artifact, shipping product
- Action — entering history, public speech, beginning something new

**Kinneavy's Communication Triangle:**
- Expressive (self-centered) — journals, personal processing
- Referential (world-centered) — explaining how things are
- Persuasive (reader-centered) — changing minds, advocacy
- Literary (language-centered) — prose as aesthetic object

**Speech Acts (what the text DOES):**
- Asserting a truth
- Requesting action from reader
- Committing yourself to something
- Expressing a feeling/state
- Declaring something into existence

**Community-Finding:**
- "I'm trying to find my people"
- Building authority/expertise
- Documenting own trajectory

**Note:** The dialectic IS the discovery phase — by the time you reach sloptractions, you already know what you think. The essay is transmission. The question is: how much of the discovery journey do you expose in the texture?

**This shapes downstream decisions:**
- Voice selection (aesthetic → Didion; political → Orwell; historical → Gwern)
- Density requirements (action requires density; making can be sparser)
- Personal material placement (egoism → more grounding)
- Stakes section weight (political → strong implications)

---

## Personal Material Extraction

The dialectic produces structural insight but not personal grounding. Extract or ask:

| Constraint | Source |
|------------|--------|
| Personal situation opening | Ask: "What's your personal connection to this topic? A moment, project, conversation?" |
| Concrete observation | Look in context briefing; if abstract, ask: "What's a concrete example you've seen?" |
| Genuine question | Check misfit register; ask: "What's still genuinely unclear to you after the dialectic?" |
| Lived experience details | Ask: "Any specific names, dates, places, projects that could ground this?" |

Present at checkpoint alongside hook candidates, surprising turn, etc.

---

## Ablation-as-Discovery

Before checkpoint, run quick structural ablation on your inventory:

1. **Remove Monk A's material entirely** — is Monk B sufficient alone?
   - If yes → was this really a dialectic, or a one-sided argument?
   
2. **Remove the synthesis** — is the hook + monks still interesting?
   - If yes → synthesis may be restating rather than elevating

These tests help you understand what you're actually saying before you commit to an outline.

See `reference/ablation-testing.md` for full protocol.
```

- [ ] **Step 3: Commit**

```bash
cd /Users/kylemathews/programs/sloptractions-skill
git add phases/1-inventory.md
git commit -m "Add writing motivation interview and personal material extraction to Phase 1

Five interview questions mapped to Orwell, Arendt, Kinneavy frameworks.
Personal material extraction for grounding.
Ablation-as-discovery before checkpoint."
```

---

### Task 6: Update `phases/2-analogy.md`

**Files:**
- Modify: `phases/2-analogy.md` (insert ablation test section)

**Interfaces:**
- Consumes: Existing analogy phase structure
- Produces: Ablation test for candidate analogies

- [ ] **Step 1: Find insertion point**

Insert after "## Test Each Candidate" section and before "## Checkpoint".

- [ ] **Step 2: Insert ablation test section**

Add before the Checkpoint section:

```markdown

---

## Ablation Test for Analogies

Before presenting candidates to the user, test each one:

**For each candidate analogy:**
1. Sketch the argument *without* the analogy vocabulary
2. Ask yourself: Does the argument still make sense and feel complete?

**Interpretation:**
- If the argument survives without the analogy → analogy is decorative
- Only present analogies where removal causes real loss

This prevents presenting "nice to have" analogies that don't actually do structural work.

**Example:**
- With analogy: "LLMs are index funds — they converge to market average, suppress alpha"
- Without analogy: "LLMs produce average-quality output"
- Does the second version lose something important? If yes, the analogy is load-bearing.

See `reference/ablation-testing.md` for full protocol.
```

- [ ] **Step 3: Commit**

```bash
cd /Users/kylemathews/programs/sloptractions-skill
git add phases/2-analogy.md
git commit -m "Add ablation test for candidate analogies to Phase 2

Test each analogy by removing vocabulary - only present load-bearing ones."
```

---

### Task 7: Update `phases/3-concepts.md`

**Files:**
- Modify: `phases/3-concepts.md` (insert ablation test section)

**Interfaces:**
- Consumes: Existing concepts phase structure
- Produces: Ablation test for coined terms

- [ ] **Step 1: Find insertion point**

Insert after "## The Minimum Set" section and before "## Checkpoint".

- [ ] **Step 2: Insert ablation test section**

Add before the Checkpoint section:

```markdown

---

## Ablation Test for Terms

Before committing to a term, test it:

**For each coined term:**
1. Explain the key distinction *without* using the term
2. Ask yourself: Is the distinction still clear?

**Interpretation:**
- If the distinction is still clear → term is labeling, not compressing
- Keep only terms where removal causes real loss

**The test:**
- Can you state the same thing in plain language without losing precision?
- If yes, the term isn't doing work — it's just a label
- If no, the term is compressing something that would otherwise require a paragraph

**Example:**
- Term: "linguistic alpha"
- Without term: "original language that can't be produced by averaging"
- Does the second version lose something? The term "alpha" imports the finance metaphor and all its connotations. That's compression.

See `reference/ablation-testing.md` for full protocol.
```

- [ ] **Step 3: Commit**

```bash
cd /Users/kylemathews/programs/sloptractions-skill
git add phases/3-concepts.md
git commit -m "Add ablation test for coined terms to Phase 3

Test each term by explaining without it - keep only compressing terms."
```

---

### Task 8: Update `phases/4-outline.md`

**Files:**
- Modify: `phases/4-outline.md` (insert personal material placement section)

**Interfaces:**
- Consumes: Existing outline phase structure, personal material from Phase 1
- Produces: Personal material placement guidance

- [ ] **Step 1: Find insertion point**

Insert after "## On Subtlety" section and before "## Title".

- [ ] **Step 2: Insert personal material placement section**

Add before the Title section:

```markdown

---

## Personal Material Placement

Map the personal material from Phase 1 into the arc:

| Material Type | Where It Goes |
|---------------|---------------|
| Personal situation | Hook — opens the essay |
| Concrete observation | Hook or Structural Unpacking — grounds abstraction |
| Genuine question | Stakes section, or woven throughout |
| Lived experience details | Wherever they anchor abstract claims |

**Check:** Does your outline include the personal material from Phase 1?

If Phase 1 didn't surface enough personal material, **pause here and ask:**
- "What's your personal connection to this topic?"
- "Any specific moments, projects, conversations that got you thinking about this?"

Don't proceed with an outline that lacks personal grounding — the essay will read generic.
```

- [ ] **Step 3: Commit**

```bash
cd /Users/kylemathews/programs/sloptractions-skill
git add phases/4-outline.md
git commit -m "Add personal material placement guidance to Phase 4

Map personal material into arc. Pause if insufficient grounding."
```

---

### Task 9: Update `phases/5-write.md`

**Files:**
- Modify: `phases/5-write.md` (add voice selection, replace single-shot with iterative loop)

**Interfaces:**
- Consumes: Existing write phase structure, voice profiles
- Produces: Voice profile selection, iterative refinement loop

- [ ] **Step 1: Find insertion point for voice selection**

Insert new section after "## Style Reference" and before "## Meso-Level Density".

- [ ] **Step 2: Insert voice profile selection section**

Add after Style Reference section:

```markdown

---

## Voice Profile Selection

Before writing, confirm voice with the user:

**Default:** Kyle voice (see `reference/kyle-voice.md`)

**Override options:**
- Select an alternate profile (see `reference/voice-profiles.md`)
- Blend: "70% Kyle, 30% Gwern density"

**Selection guidance based on Phase 1 motivation interview:**

| Dominant Motive | Suggested Voice |
|-----------------|-----------------|
| Aesthetic enthusiasm | Kyle, Didion |
| Political purpose | Orwell, Kyle + Orwell directness |
| Historical impulse | Gwern, Kyle + Gwern density |
| Community-finding | Kyle, Paul Graham |
| Technical explanation | Matt Levine, Gwern |

Ask:
> "Default voice is Kyle (conversational, exploratory, visible author). Want to override or blend with another profile? See `reference/voice-profiles.md` for options."

Once confirmed, keep the voice profile in mind throughout drafting.
```

- [ ] **Step 3: Find insertion point for iterative loop**

Replace the existing writing process (single-shot) with iterative refinement. Find the "## Writing Process" section.

- [ ] **Step 4: Update writing process to iterative refinement loop**

Replace the Writing Process section content (keep the header) with:

```markdown

## Writing Process

**Iterative refinement, not single-shot:**

### Loop 1: Draft

1. **Write the Hook first** — this sets the tone
2. **Write the New Frame next** — this is the core move; get it right
3. **Structural Unpacking** — the meso-level detail work
4. **Stakes & Implications** — what follows
5. **Recipe** — write this AS you write, noting your actual moves

### Loop 2: Self-Critique

After completing the draft, run self-critique:

Ask yourself:
- "Where would I skim?" → Tighten or cut those sections
- "Where am I hedging without conviction?" → Either commit or acknowledge uncertainty honestly
- "Where is this generic?" → Add specific details, examples, or personal grounding

Revise the flagged sections before proceeding.

### Loop 3: Meso-Level Ablation

Run the density test (see `reference/ablation-testing.md`):

1. Summarize the draft in 100 words
2. Compare summary to original
3. Ask: "What orientation-relevant information is in the full text that's missing from the summary?"

**Interpretation:**
- If the answer is "not much" → draft is all overstory, lacks understory density
- Add density to thin sections: more specific details, more personal grounding, more implications

### Loop 4: Proceed to Phase 6

Only after iterative refinement, proceed to validation.
```

- [ ] **Step 5: Commit**

```bash
cd /Users/kylemathews/programs/sloptractions-skill
git add phases/5-write.md
git commit -m "Add voice profile selection and iterative refinement loop to Phase 5

Voice selection before writing with blend syntax.
Replace single-shot with: draft → self-critique → meso-level ablation → validate."
```

---

### Task 10: Update `phases/6-validate.md`

**Files:**
- Modify: `phases/6-validate.md` (expand validation checklist, add ablation suite)

**Interfaces:**
- Consumes: Existing validation phase structure, ablation protocol
- Produces: Expanded validation checklist, structural ablation suite

- [ ] **Step 1: Find the validation checklist section**

The file has "## Validation Checklist" with existing checks. Add new checks to this section.

- [ ] **Step 2: Add new validation checks after existing checklist**

Find the end of the existing validation checklist (after "### 6. Information Density Check") and add:

```markdown

### 7. Voice Fidelity Check

Compare draft against `reference/kyle-voice.md` (or selected voice profile):

- Does the opening follow the profile's pattern?
- Is first-person usage consistent with the profile?
- Does the ending match the profile's pattern?
- Are absent patterns truly absent?

**If no:** Line-edit for voice. Read the profile's exemplars, then revise.

### 8. Positive Constraints Check

Check against `reference/style-guide.md` positive constraints:

| Constraint | Check |
|------------|-------|
| "I" in first 100 words | Count words to first "I" |
| Genuine question present | Find a question you don't know the answer to |
| Invitation/question ending | Check final paragraph |
| No paragraph over 5 sentences | Scan all paragraphs |
| 1-2 sentence paragraph present | Find at least one per 500 words |

**If no:** Add missing elements.

### 9. Metrics Check

Run quantitative checks from `reference/style-guide.md`:

| Metric | Target | Check |
|--------|--------|-------|
| Sentence length variance | Std dev > 8 words | Count words per sentence, compute std dev |
| Em-dash usage | 1-3 per 1000 words | Count "—" |
| Cliché count | 0 | Scan against banned list |
| AI-ism count | 0 | Scan for "delve", "crucial", "quiet" as filler, etc. |

**If fail:** Fix the specific issues.

### 10. AI-ism Detection

Scan for patterns from `reference/style-guide.md` AI-ism Detection section:

- Word-level: "quiet" as filler, "delve", "crucial", "nestled", "tapestry"
- Structural: unsolicited validation, "Bold Header: explanation" lists, too-smooth coherence
- Tonal: relentless positivity, excessive hedging, summarizing what was just said

**If found:** Delete or replace with something specific and textured. Add "grit."
```

- [ ] **Step 3: Add structural ablation suite section**

Add new section before "## Revision Process":

```markdown

---

## Structural Ablation Suite

Run the full ablation suite on the finished draft. See `reference/ablation-testing.md` for protocol.

**Spawn 7 parallel fresh subagents:**

```
Agent 1: [analogy vocabulary stripped] 
         → "Summarize the argument in 2-3 sentences."

Agent 2: [coined terms replaced with "[TERM]"] 
         → "What's the key distinction this essay draws?"

Agent 3: [synthesis/reframing section removed] 
         → "What's the insight or reframing?"

Agent 4: [examples and evidence removed] 
         → "Why should I believe this argument?"

Agent 5: [hook/opening removed] 
         → "What problem is this essay addressing?"

Agent 6: [full draft, no changes] 
         → "Summarize this in 100 words."

Agent 7: [full draft, no changes] 
         → "What do you get from close reading that you wouldn't get from a summary?"
```

**Key rules:**
- Each agent is fresh — no shared context
- Run in parallel — no sequential contamination
- Report all results to user

**Interpretation:**
- Where comprehension fails → component is load-bearing ✓
- Where comprehension succeeds → component needs strengthening or cutting
- Agent 7 "not much" → draft lacks meso-level density

**Present results to user.** User decides what to strengthen vs. cut.
```

- [ ] **Step 4: Commit**

```bash
cd /Users/kylemathews/programs/sloptractions-skill
git add phases/6-validate.md
git commit -m "Expand validation checklist and add ablation suite to Phase 6

New checks: voice fidelity, positive constraints, metrics, AI-ism detection.
Structural ablation suite: 7 parallel subagents testing all components."
```

---

### Task 11: Final Review and Status Update

**Files:**
- Modify: `docs/superpowers/specs/2026-07-04-styleguide-enhancement-design.md` (update status)

**Interfaces:**
- Consumes: Completed implementation
- Produces: Updated spec status

- [ ] **Step 1: Update spec status to implemented**

Change the status line in the spec:

From: `**Status:** Design approved, pending implementation`
To: `**Status:** Implemented`

- [ ] **Step 2: Commit**

```bash
cd /Users/kylemathews/programs/sloptractions-skill
git add docs/superpowers/specs/2026-07-04-styleguide-enhancement-design.md
git commit -m "Mark styleguide enhancement spec as implemented"
```

- [ ] **Step 3: Verify all files exist**

```bash
ls -la reference/
ls -la phases/
```

Expected:
- `reference/ablation-testing.md` (new)
- `reference/voice-profiles.md` (new)
- `reference/kyle-voice.md` (new)
- `reference/style-guide.md` (updated)
- `phases/1-inventory.md` (updated)
- `phases/2-analogy.md` (updated)
- `phases/3-concepts.md` (updated)
- `phases/4-outline.md` (updated)
- `phases/5-write.md` (updated)
- `phases/6-validate.md` (updated)
