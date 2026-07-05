# Phase 5: Write the Draft

## Goal

Produce the essay draft using the validated outline, analogy, and concepts.

## Voice Selection

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

## Style Reference

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

## Meso-Level Density

- Hold many threads — reference earlier points, connect across sections
- Be specific — names, dates, mechanisms, not just abstractions
- But don't drown — if a paragraph has 5+ distinct claims, break it up

## Integrating Dialectic Material

### From Monk Essays
- Don't reproduce — compress to strongest single-paragraph form
- Quote sparingly — the best formulations, not everything
- Each side should sound genuinely compelling before the turn

### From Determinate Negation
- This is often the most interesting material
- The specific failures are often the best sentences in the piece
- "Position A fails because [specific failure], which reveals [specific missing thing]"

### From Synthesis
- Should feel like arrival — "oh, *that's* what this is really about"
- Deploy conceptual currency here
- Don't over-explain — let the reframing land

### From Misfits/Queue
- Honest limits go in Stakes section
- Acknowledging what you didn't resolve builds trust

## Writing Process

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

## Section-by-Section Guidance

### Hook
- Open with the concrete phenomenon
- Make readers nod — they recognize this
- Create slight dissonance — something doesn't add up
- Don't frame as "the debate" — just show the phenomenon

### The New Frame
- The analogy enters here
- Introduce it directly, not as "but actually..."
- Show the structural correspondence
- Deploy your key terms
- Let readers notice what your frame displaces — don't spell it out

### Structural Unpacking
- This is where meso-level density lives
- Decompose into layers, phases, or tensions
- Use concrete evidence from the monk essays (their examples, not their framing)
- Connect back to earlier points
- This section earns the right to the length

### Stakes & Implications
- What changes if readers accept this?
- What should they do/think differently?
- Name the open questions — don't pretend to have solved everything

### Recipe

The recipe section needs an introduction that frames it. Put it in italics. Something like:

> *This essay was written with AI assistance. Here's the recipe — the structural moves that produced it, in case you want to apply them to your own thinking.*

Or:

> *What follows is the recipe — the method behind this essay. These are the moves that produced it.*

The point: acknowledge the AI collaboration, explain what the recipe is for, then give the steps.

**The steps themselves:**
- Imperative verbs: Start with..., Reframe..., Identify..., Trace...
- Generalizable — someone should be able to apply this to their own problems
- Honest about the process — if it was messy, say so

---

## Iterative Improvement Loop

After completing the first draft, run one improvement pass before presenting to user.

**The loop:**

1. **Re-read the draft cold** — as if you didn't write it
2. **Run style diagnostics** (from `reference/style-guide.md`):
   - First 7-8 words test: Can you find subject and verb?
   - Nominalization detector: Circle -tion/-ment/-ness words
   - AI-ism scan: Check for "delve," "crucial," "tapestry," etc.
3. **Run voice check** (from `reference/kyle-voice.md`):
   - "I" in first 100 words?
   - At least one question as transition?
   - Any teacher-mode passages?
   - Em-dashes present but not overused?
4. **Fix the top 3-5 issues you find** — don't over-polish, just catch the obvious
5. **Note what you fixed** — this becomes part of the draft summary

**When to loop again:**
- If you find more than 5 significant issues, fix and loop once more
- Maximum 2 passes before presenting to user
- Note in summary if more revision is recommended

**What this is NOT:**
- Not a substitute for Phase 6 validation
- Not user review
- Just catching obvious issues before wasting the user's attention on fixable problems

---

## Output

Save the draft to the dialectic directory:
- Filename: `essay_[topic].md` or similar
- Include the recipe as a marked section at the end

Do not present the full draft inline — it's too long. Instead, confirm:

> "Draft complete: [filename]
> 
> Length: [X words]
> Sections: [list with word counts]
> 
> Happy to discuss or revise until you give me the go-ahead to move to Phase 6."

---

## HARD STOP

**You CANNOT proceed to Phase 6 until the user explicitly says to continue.**

Do not read the next phase file. Do not start validation. Stay here.

If the user wants to read the draft, discuss it, or request changes — do that. Say something like:

> "Happy to keep revising until you give me the go-ahead to move to Phase 6."

Only when the user explicitly confirms (e.g., "continue," "validate it," "move to review") should you read `phases/6-validate.md`.

The user may want to read the draft before validation, request revisions, or proceed directly.
