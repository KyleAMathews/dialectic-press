# Phase 2: Find the Analogical Domain

## Goal

Decide whether the essay needs an outside analogy at all, and if so, which one. Often the dialectic's native frame is stronger than any import.

## Start with the Dialectic's Native Analogies

**Check what's already there before inventing.** The dialectic often contains analogies that emerged organically from the argument:

1. **List analogies already in the dialectic** — historical examples, comparisons the monks used, frames from research
2. **Check if the synthesis already has a frame** — tetrads, phase models, structural diagrams
3. **Ask: does the native frame carry the argument?**

**If the dialectic has a strong native frame** (like McLuhan's tetrad, a historical parallel, or a structural model), the right answer is often: *use that, don't import a new one*.

Outside analogies are for when:
- The dialectic's native frame is too technical or narrow
- The synthesis needs a more familiar domain to land
- No strong native frame emerged

**The failure mode:** inventing elaborate outside analogies that compete with or distort the dialectic's actual insight. If you find yourself proposing three new frameworks when the dialectic already has one, stop.

---

## When Outside Analogies Help

Good analogies:
- Are **structural, not superficial** — the systems actually work similarly
- **Do work** — removing the analogy would collapse the argument
- **Import vocabulary** — terms from the analogical domain become conceptual currency

Examples:
- **LLMs as index funds** — both converge to mean, suppress variance, offer cheap exposure to average
- **Prompting as managing** — both involve delegation, oversight, quality control

But note: these work because the original frame was thin. If the dialectic already produced a rich frame, adding another layer creates confusion.

---

## Finding Candidates (When Needed)

Look at the dialectic's structure (not just its content). Ask:

1. **What kind of system is this?**
   - A tradeoff between two resources? → Thermodynamics, economics
   - A tension between control and emergence? → Ecology, gardening
   - A conflict between local and global optima? → Evolution, game theory
   - A timing/sequencing problem? → Music, cooking, construction

2. **What's the shape of the synthesis?**
   - Did it reveal a hidden third thing? → Look for domains with similar "hidden variables"
   - Did it dissolve a false binary? → Look for domains where a similar binary was dissolved
   - Did it introduce a temporal dimension? → Look for domains with phase transitions

3. **What domains does the user know well?**
   - The analogy works best when it imports *their* expertise into the essay
   - Ask if there's a field they'd like to draw from

## Candidate Domains by Dialectic Type

| Dialectic Structure | Candidate Analogies |
|--------------------|---------------------|
| **Tech choices** (frameworks, tools) | Financial instruments, evolutionary niches, arms races |
| **Organizational design** | Biological systems, game theory, thermodynamics |
| **Personal decisions** | Navigation, gardening, investment, cooking |
| **Creative work** | Sculpture, architecture, jazz improvisation |
| **Epistemic questions** | Legal reasoning, debugging, scientific method |
| **Behavioral/habit** | Control systems, ecology, cultivation |

## Test Each Candidate

For each candidate analogy, check:

1. **Structural match** — Do the dynamics actually map?
2. **Vocabulary import** — What terms come with it?
3. **Surprise value** — Will readers see the original domain differently?
4. **Explanatory power** — Does it resolve the original tension or just redescribe it?

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

---

## Checkpoint

First, present what the dialectic already has. Then offer outside options only if needed.

**If the dialectic has a strong native frame:**

> "The dialectic already has a strong frame: [the tetrad / the historical parallel / the structural model].
>
> **Native frame:** [describe it]
> - What it explains: [its strengths]
> - What vocabulary it provides: [terms]
>
> I don't think we need an outside analogy — the native frame can carry the essay. We could use [specific example from dialectic] as the concrete illustration of [concept].
>
> Do you agree, or would you like to explore outside analogies anyway?"

**If the dialectic needs an outside analogy:**

> "The dialectic's synthesis is strong but the native frame is [too technical / too narrow / absent]. Here are candidate analogies:
> 
> **Option A: [Domain]**
> - How it maps: [explain the structural correspondence]
> - What it imports: [vocabulary, concepts]
> - Why it might work: [what it would illuminate]
> - Limits: [what it doesn't explain well]
> 
> **Option B: [Domain]**
> - How it maps: ...
> - What it imports: ...
> - Why it might work: ...
> - Limits: ...
> 
> Which resonates? Or should we stick closer to the dialectic's native examples?"

**If testing reveals no analogy carries the full argument:**

> "I tested several analogies against the dialectic's structure. None carries all parts well — each explains one aspect and distorts others.
>
> **Recommendation:** Let [the native frame] organize the essay. Use [analogy X] locally to explain [specific point], and [analogy Y] lightly for [other point]. Don't ask the reader to hold multiple competing frameworks.
>
> Does that feel right?"

---

## HARD STOP

**You CANNOT proceed to Phase 3 until the user explicitly says to continue.**

Do not read the next phase file. Do not start coining concepts. Stay here.

If the user has questions, wants to explore other domains, or asks you to develop an option further — do that. Say something like:

> "Happy to keep exploring until you give me the go-ahead to move to Phase 3."

Only when the user explicitly confirms (e.g., "continue," "next phase," "let's go with Option A") should you read `phases/3-concepts.md`.

If the user picks a domain, confirm and note which vocabulary/concepts you'll import. If they propose a different domain, explore its structural fit before committing.
