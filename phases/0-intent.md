# Phase 0: Establish Intent

## Goal

Read the dialectic to understand what's there, then establish what you actually want to write about. The dialectic is source material, not the assignment.

## Step 1: Survey the Dialectic

First, read the dialectic outputs to understand what you have to work with.

**Read in this order:**

| Order | File Pattern | What You're Looking For |
|-------|--------------|------------------------|
| 1 | `round{N}_synthesis.md` | The synthesis — what got elevated |
| 2 | `round{N}_determinate_negation.md` | The specific failures, hidden questions |
| 3 | `round{N}_monk_a.md`, `round{N}_monk_b.md` | Skim for interesting threads, tangents |
| 4 | `misfit_register.md` | Unresolved tensions, queued ideas |

**If multiple rounds exist:** Briefly read each round's synthesis to see what different threads emerged.

After reading, present a brief summary:

> "Here's what I found in the dialectic:
>
> **Main synthesis:** [one sentence]
>
> **Interesting threads:** 
> - [thread 1]
> - [thread 2]
> - [thread 3]
>
> **Unresolved tensions:** [from misfits]
>
> **Rounds available:** [if multiple]"

---

## Step 2: The Intent Interview

Now that you both know what's in the dialectic, ask what they want to write:

> "What's the essay you want to write?
> 
> This could be:
> - The main synthesis
> - One of the threads that emerged
> - Something the dialectic made you think about but didn't directly address
> - A reaction to or extension of what you discovered
>
> What's the piece you're imagining?"

**Wait for answer before proceeding.**

---

## Clarifying the Intent

Once you have a topic direction, dig into the "why":

| Question | What It Reveals |
|----------|-----------------|
| "Why are you writing this particular piece?" | Dominant motive |
| "Who is your intended reader? What do they already know/believe?" | Audience, assumptions |
| "What do you want to happen after someone reads it?" | Desired effect |
| "Is this entering an existing conversation or starting a new one?" | Novelty level |
| "What would failure look like for this piece?" | What success actually is |

Don't ask all five at once — conversational flow. But by the end of Phase 0, you should know:

1. **Topic:** What the essay is actually about (may differ from dialectic focus)
2. **Motive:** Why you're writing it (Orwell's four: egoism, aesthetic, historical, political)
3. **Audience:** Who you're writing for and what they already know
4. **Desired effect:** What should change in the reader

---

## Mapping to Frameworks (Internal Use)

Use these frameworks to understand the user's intent, but don't force them on the user:

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

---

## Precommodification Sniff Test

Once you have a topic direction, test whether it's precommodified territory.

**The goal:** Never write what's expected. If a blind agent can predict your essay's argument, you're not in the sweet spot. The value is in the *understory* — the meso-level detail that's more than humans hold unassisted (>7±2 chunks) but less than AI handles autonomously. Overstory claims are already in distribution.

**The mechanism:** LLMs compress training data into a latent space. Multiple people querying similar problems "pull forward the same sticky ideas along the same gradients" — arriving at roughly the same conclusions independently. Ideas arrive pre-packaged, no clear originator, no attribution value.

**The test question:** Can the probe *summarize* your essay accurately from just the topic? If yes, the essay is too predictable — it has no unsummarizable load-bearing content. The goal is writing that's pleasurable, not summarizable.

**The problem with self-assessment:** An agent can't reliably judge whether its own elaboration "flows easily" — it always produces fluent text. Instead, use a **blind-expectation probe**.

### The Blind Probe

Spawn a fresh subagent that sees **only the topic** — not the dialectic materials, not the synthesis, not any of the work done.

**Subagent prompt:**

> You are predicting what an essay on this topic would likely argue.
>
> **Topic:** [the user's stated topic/question, one sentence]
>
> Without any other context, predict:
> 1. The 2-3 most likely arguments or conclusions an essay on this topic would reach
> 2. The standard framing or angle you'd expect
> 3. The usual examples or evidence that would appear
>
> Be specific. What would the *expected* essay say?

**Then compare:** The orchestrator (you) compares the blind prediction to what the dialectic actually produced.

### Interpreting Results

| Comparison | Reading | What It Means |
|------------|---------|---------------|
| Dialectic matches blind prediction | **Groove** | The synthesis landed where any competent analysis would. Precommodified territory. |
| Dialectic diverges from prediction | **Frontier** | The synthesis reached somewhere unexpected. Potentially novel. |
| Partial match | **Mixed** | Some elements are standard, some are novel. |

**The collapse signal:** If the dialectic *reached* (monks strained, needed external research, invented new framing) but the synthesis still matches the blind prediction — that's the failure mode. Frontier work that got smoothed back to groove.

**The inversion trap:** Don't treat a match as validation. If the blind probe predicts your claim almost verbatim, that's evidence of precommodification — not confirmation you're right. "The probe agrees with me" means you're in the groove, not on the frontier.

### Response Strategies

**If groove (matches prediction):**

**Do not proceed.** Writing what's expected is not worth writing. Instead:

1. **Cut or demote:** Anything the probe predicts verbatim gets cut or reduced to connective tissue
2. **Find the level-up:** Is there a *combination* or tangent that's novel even if the main argument isn't?
3. **Protect the frontier:** Your live claim is whatever the probe *couldn't* predict — build around that
4. **Go deeper into understory:** The probe predicts overstory. What's the meso-level detail beneath it that the probe can't reconstruct?
5. **Lean on provenance:** Your backlinks, your history, your specific angle — these establish attribution

**If still groove after trying these:** Consider abandoning this essay. Not everything is worth writing. The dialectic may have landed on a well-worn path. Return to the dialectic and look for frontier material.

**If frontier (diverges):**
Good sign. The dialectic produced something the LLM wouldn't predict from the topic alone. The argument has understory the probe can't summarize. Proceed with confidence.

**If collapse (reached but grooved):**
Warning. The hard work got flattened. Look at where the dialectic reached — can you recover that frontier material? Or find a different angle?

### Present to User

> "Precommodification check:
>
> **Blind prediction:** [what the probe expected]
>
> **Dialectic produced:** [what actually emerged]
>
> **Reading:** [groove/frontier/mixed] — [one-line interpretation]
>
> [If collapse:] ⚠ The dialectic reached on [X] but landed back in expected territory. Worth looking at the frontier material that got smoothed over."

---

## Re-Running the Probe

The thesis evolves through discussion. **Re-run the blind probe when:**

- The topic/angle shifts meaningfully during Phase 0 discussion
- Phase 1 inventory reveals a different focus than initially stated
- Phase 2 analogy reframes the argument
- Phase 3 coins concepts that change what you're actually claiming
- Phase 4 outline crystallizes a thesis that differs from Phase 0 intent

**The probe is cheap — when in doubt, re-run.** A thesis that started frontier can drift to groove through refinement (you converged on the obvious version). Catching this early saves a wasted draft.

**How to re-run:**

1. Spawn a fresh blind agent with the *current* thesis (not the original)
2. Compare to what you're actually proposing now
3. Report the new reading alongside the old one

> "The thesis has shifted since our last check. Re-running precommodification probe...
>
> **Original thesis:** [what we started with] → [original reading]
> **Current thesis:** [what we're proposing now] → [new reading]
>
> [If drift toward groove:] The refined version is more obvious than where we started. Did we lose the frontier edge, or clarify something that was always there?
>
> [If still frontier:] The refinement held. Still diverges from what a blind agent would predict."

---

## The Essay Log (Anti-Drift)

Long sessions drift. The agent forgets motivations, softens frontier claims, reintroduces precommodified ideas. The essay log prevents this.

### Create the Log File

At the end of Phase 0, create `essay_log.md` in the dialectic directory:

```markdown
# Essay Log

## Anchor (frozen — do not edit)

**What I'm trying to say:** [user's stated intent, verbatim]

**Frontier claim:** [what the blind probe couldn't predict]

**Groove to avoid:** [what the probe DID predict — cut or demote this]

**Motivation:** [why writing this, in user's words]

---

## Working Thesis (living — explicit diffs only)

[Current thesis. When this changes, record the delta below.]

---

## Thesis Ledger (append-only)

| Phase | Thesis at this point | Delta from previous | Probe reading |
|-------|---------------------|---------------------|---------------|
| 0 | [initial] | — | [frontier/groove/mixed] |

---

## Decisions Ledger (append-only)

| Phase | Decision | Rationale |
|-------|----------|-----------|
| 0 | [e.g., "focus on community fission, not broken apprenticeship"] | [why] |

---
```

### Using the Log

**At phase boundaries:** Re-read the anchor. Compare current work to the frozen intent. If drifting, flag it.

**When thesis evolves:** Don't silently update the working thesis. Record the delta explicitly:
- What changed
- Why
- Re-run probe if significant

**When tempted by a groove idea:** Check the "Groove to avoid" section. If it matches, cut it.

**At validation (Phase 5):** One validator checks: does the draft honor the anchor? Or has it drifted to the groove?

### The Scent-Fix

At the top of each phase:
1. Read the essay log
2. Re-state the anchor in your own words (forces re-encoding)
3. Note any tension between current work and frozen intent

This counteracts context-window pressure. Writing the anchor without re-reading it builds the anchor and never looks at it.

---

## How This Shapes the Process

The intent established here determines:

- **Which parts of the dialectic matter** — maybe just one round, one monk's evidence, one tangent
- **Voice selection** — aesthetic motive → different voice than political motive
- **Density requirements** — action requires density; making can be sparser
- **Personal material weight** — egoism → more grounding; referential → less
- **Stakes section** — political → strong implications; historical → honest limits

---

## Checkpoint

Present your understanding back to the user:

> "Here's what I'm hearing:
>
> **Topic:** [the essay subject — may differ from dialectic]
>
> **Motive:** [why you're writing this]
>
> **Audience:** [who, what they know]
>
> **Desired effect:** [what should change]
>
> **Relationship to dialectic:** [using the whole synthesis / one thread / tangential inspiration]
>
> Does this capture it? Anything to adjust before we inventory the dialectic materials?"

---

## HARD STOP

**You CANNOT proceed to Phase 1 until the user confirms the intent.**

Do not read the dialectic files. Do not start inventorying. Stay here.

If the user is still figuring out what they want to write, help them explore. Ask follow-up questions. This is the foundation — get it right.

Only when the user explicitly confirms (e.g., "yes that's it," "let's proceed," "move on") should you read `phases/1-inventory.md`.
