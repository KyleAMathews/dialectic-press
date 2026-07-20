# Phase 5: Write & Validate

## Goal

Produce the essay draft, run mechanical cleanup, run validation, then present a polished draft with findings for user review.

---

## Before Writing: Scent-Fix

**Re-read the essay log.** Long sessions drift. Before writing:

1. Read `essay_log.md` — especially the frozen anchor and "groove to avoid"
2. Re-state the anchor in your own words (forces re-encoding, counteracts context pressure)
3. Check: does the outline still honor the anchor? Or has it drifted?

> "Re-reading the essay log before writing...
>
> **Anchor:** [restate in your words]
> **Frontier claim to protect:** [what the probe couldn't predict]
> **Groove to avoid:** [what would be precommodified]
>
> [If tension:] The outline seems to have drifted toward [X]. Want to correct before writing, or proceed?
> [If aligned:] Outline aligns with the anchor. Proceeding to draft."

---

## Part A: Write the Draft

### Voice Selection

Before writing, confirm voice profile.

**Default:** Kyle (see `reference/kyle-voice.md`)

**Check with user if:**
- Writing motivation suggests a different voice (see `reference/voice-profiles.md` selection guide)
- The material calls for different treatment (exhaustive → Scott Alexander; polemic → Orwell)
- User previously indicated voice preferences

**Prompt:**
> "The default voice is Kyle's — conversational, exploratory, fellow-traveler tone. Based on [motivation/material], does that fit, or would you prefer a different profile or blend?"

**If blending:**
- Syntax: "70% Kyle, 30% Gwern density"
- Apply Kyle's patterns (openings, questions, tone) with the blended element (citations, directness, thoroughness)

---

### Style Reference

**Read `reference/style-guide.md` before writing.** It contains:
- Style Lineage (Strunk & White, Orwell, Zinsser, Williams, Rao)
- Voice principles
- Sentence-level guidance (Williams tests, flow patterns)
- Cliche avoidance
- Padding to cut
- Throat-clearing and false gravitas
- Protesting too much
- Paragraph and structure guidance
- Prose diagnostics for when sentences feel off

Internalize those voices, then write.

---

### Meso-Level Density

- Hold many threads — reference earlier points, connect across sections
- Be specific — names, dates, mechanisms, not just abstractions
- But don't drown — if a paragraph has 5+ distinct claims, break it up

### Integrating Dialectic Material

**From Monk Essays:**
- Don't reproduce — compress to strongest single-paragraph form
- Quote sparingly — the best formulations, not everything
- Each side should sound genuinely compelling before the turn

**From Determinate Negation:**
- This is often the most interesting material
- The specific failures are often the best sentences in the piece
- "Position A fails because [specific failure], which reveals [specific missing thing]"

**From Synthesis:**
- Should feel like arrival — "oh, *that's* what this is really about"
- Deploy conceptual currency here
- Don't over-explain — let the reframing land

**From Misfits/Queue:**
- Honest limits go in Stakes section
- Acknowledging what you didn't resolve builds trust

### Writing Process

1. **Write the Hook first** — this sets the tone
2. **Write the New Frame next** — this is the core move; get it right
3. **Structural Unpacking** — the meso-level detail work
4. **Stakes & Implications** — what follows
5. **Recipe** — write this AS you write, noting your actual moves

### Track the Recipe
As you write each section, note:
- What move did I just make?
- Could someone else apply this move to a different topic?

This produces a better recipe than trying to reconstruct it after.

### Section-by-Section Guidance

**Hook:**
- Open with the concrete phenomenon
- Make readers nod — they recognize this
- Create slight dissonance — something doesn't add up
- Don't frame as "the debate" — just show the phenomenon

**The New Frame:**
- The analogy enters here
- Introduce it directly, not as "but actually..."
- Show the structural correspondence
- Deploy your key terms
- Let readers notice what your frame displaces — don't spell it out

**Structural Unpacking:**
- This is where meso-level density lives
- Decompose into layers, phases, or tensions
- Use concrete evidence from the monk essays (their examples, not their framing)
- Connect back to earlier points
- This section earns the right to the length

**Stakes & Implications:**
- What changes if readers accept this?
- What should they do/think differently?
- Name the open questions — don't pretend to have solved everything

**Recipe:**

The recipe section needs an introduction that frames it. Put it in italics. Something like:

> *This essay was written with AI assistance. Here's the recipe — the structural moves that produced it, in case you want to apply them to your own thinking.*

Or:

> *What follows is the recipe — the method behind this essay. These are the moves that produced it.*

The point: acknowledge the AI collaboration, explain what the recipe is for, then give the steps.

**The steps themselves:**
- Imperative verbs: Start with..., Reframe..., Identify..., Trace...
- Generalizable — someone should be able to apply this to their own problems
- Honest about the process — if it was messy, say so

### Frontmatter

Include YAML frontmatter with the title, subtitle, and meta description (from Phase 4):

```yaml
---
title: "The Chosen Title"
subtitle: "The chosen subtitle"
description: "The meta description for search/social (~155 chars)"
date: YYYY-MM-DD
---
```

---

## Part B: Mechanical Cleanup (Auto-Fix Loop)

**Immediately after writing, before presenting to user**, run the mechanical validators in a loop.

### Tier 1 Validators

Spawn these in parallel, loop until clean (max 3 passes):

**Validator 1: Prose Mechanics**
> Check for: sentence length variance, buried subjects (first 7-8 words test), nominalizations (-tion/-ment/-ness), AI-isms ("delve," "crucial," "tapestry," "multifaceted," "it's important to note," "actually," "really," "literally"), padding ("the fact that," "there is/are," "in order to"), em-dash usage.
>
> **Preserve meaning.** Cleaner ≠ different.

**Validator 3: Clichés & Stale Metaphors**
> Check for: dying metaphors, tech/business clichés, wallpaper phrases, mixed metaphors.
>
> **Preserve meaning.** "Move the needle" → "increase retention" is fine. "Move the needle" → "create impact" loses specificity.

**Validator 8: Factual Claims**
> Check for: verifiable facts, technical claims, citations. Flag anything wrong or overconfident.

### The Loop

1. Spawn Validators 1, 3, 8 in parallel
2. Collect findings
3. Apply fixes (preserving meaning)
4. Re-run on updated draft
5. Repeat until clean OR max 3 passes
6. Log all changes for drift review

**If still finding issues after 3 passes:** Stop and flag — something's wrong upstream.

---

## Part C: Validation (For User Review)

After mechanical cleanup, run the judgment-requiring validators.

### Tier 2: Structural & Subjective (Run in Parallel)

**Validator 4: Structural Integrity**
> - Analogy load-bearing test: remove analogical vocabulary, does argument survive?
> - Synthesis test: genuine reframing or restating?
> - Conceptual currency test: do terms help with new cases?
> - Recipe usability: too specific or too generic?

**Validator 5: Density & Flow**
> - Empty paragraphs, skimmable sections, dense blocks without reset
> - Transitions: connect or stack?
> - Opening/closing lines: strong or weak?

**Validator 6: Audience Fit**
> - Over-explaining (condescension) or under-explaining (gaps)?
> - Density calibration: too dumbed down / well calibrated / too insider?

**Validator 7: Backlink Integration**
> - Organic placement, context provided, value added, link text quality?
> - If none found, note the opportunity.

### Tier 3: Voice Check (Careful Review)

**Validator 2: Voice & Tone**
> - Teacher mode, throat-clearing, protesting too much
> - First person in first 100 words?
> - Fellow-traveler register or explaining-what-you're-missing?

Voice fixes risk overcorrection — present suggested rewrites for user approval, don't batch-apply.

### Tier 4: Anchor Check (Anti-Drift)

**Validator 9: Anchor Honoring**
> Read `essay_log.md` (the frozen anchor, frontier claim, groove to avoid).
> Then read the draft.
>
> Check:
> 1. **Frontier claim present?** Does the draft make the claim the blind probe couldn't predict?
> 2. **Groove avoided?** Has precommodified material crept back in?
> 3. **Anchor honored?** Does the draft say what the user originally intended?
> 4. **Drift detection:** Compare draft thesis to the anchor. Note any divergence.
>
> Return: assessment of alignment. Flag any drift toward groove or away from anchor.

This is the most important validator — catches the failure mode where the essay drifts back to obvious territory.

---

## Part D: Present to User

Save the draft, then present the cleaned version with findings:

> "Draft complete: [filename]
>
> **Length:** [X words]
> **Sections:** [list with word counts]
>
> ---
>
> **Mechanical cleanup applied (Tier 1):**
> - Prose mechanics: [N] fixes
> - Clichés: [N] replacements  
> - Factual claims: [N] corrections
> - Passes: [1-3]
>
> **Changes to review for meaning drift:**
>
> | Original | Replacement | ⚠️ Drift? |
> |----------|-------------|-----------|
> | [example] | [example] | ✓ OK |
> | [example] | [example] | ⚠️ check |
>
> ---
>
> **Structural assessment (Tier 2):**
> - Analogy: [load-bearing / decorative]
> - Synthesis: [genuine / restating]
> - Conceptual currency: [assessment]
> - Recipe: [usable / too specific / too generic]
> - Density/flow: [issues if any]
> - Audience fit: [assessment]
> - Backlinks: [assessment]
>
> **Voice rewrites for approval (Tier 3):**
> 1. [original] → [proposed] — approve? y/n
> 2. [original] → [proposed] — approve? y/n
>
> ---
>
> **Overall:** [Ready for your read-through / Needs revision in X areas]
>
> Happy to apply voice fixes or discuss findings. When you're ready to read and finalize, let me know."

---

## HARD STOP

**You CANNOT finalize until the user explicitly approves.**

The user should:
1. Review the Tier 1 changes for meaning drift
2. Decide on Tier 2 structural issues (may need earlier phase)
3. Approve/reject Tier 3 voice rewrites
4. Read the draft themselves
5. Request any final revisions

Say something like:

> "Happy to keep refining until you give me the go-ahead to finalize."

Only when the user explicitly confirms (e.g., "finalize," "ship it," "done") should you proceed to Finalizing.

---

## Finalizing

Once approved:

1. Ensure the recipe section is clearly marked
2. Add any author's note the user wants (optional)
3. Confirm final filename and location
4. Remove any working notes or comments

> "Essay finalized: [path]
> 
> [X] words, [Y] sections, recipe included.
> 
> Ready to publish or share."
