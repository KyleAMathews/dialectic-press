# Phase 1: Inventory Dialectic Outputs

## Goal

Survey the dialectic outputs and identify what you have to work with. Extract the key elements that will become essay components.

## Check for Multiple Rounds

First, list files in the dialectic directory to check for multiple rounds. Look for `round1_*.md`, `round2_*.md`, etc.

**Multiple rounds don't necessarily build on each other.** Each round may be a separate argument that could become its own essay. Don't assume you're writing about the final round.

If multiple rounds exist:
1. Briefly read each round's `round{N}_sublation.md` (just the key insight, not full analysis)
2. Present a summary of what each round produced
3. Ask the user which round(s) to focus on before diving deeper

> "This dialectic has [N] rounds:
> - **Round 1:** [one-sentence summary of the sublation]
> - **Round 2:** [one-sentence summary]
> - **Round 3:** [one-sentence summary]
> 
> Which round should the essay focus on? Or should we combine insights from multiple rounds?"

Only after the user picks should you do the full read-through below.

---

## What to Read

Dialectic files follow this naming convention: `round{N}_{type}.md`

**Read in this order** — it matters:

| Order | File Pattern | Why This Order |
|-------|--------------|----------------|
| 1 | `round{N}_sublation.md` | **Start here.** This is the synthesis — what got cancelled/preserved/elevated. |
| 2 | `round{N}_determinate_negation.md` | The specific failures that make the argument interesting. Often the best material. |
| 3 | `round{N}_monk_a.md`, `round{N}_monk_b.md` | **Skim for evidence and examples**, not their framing. The essay won't reproduce the monks' arguments. |
| 4 | `misfit_register.md` | Honest limits — what tensions remain unresolved. (Lives at dialectic root, not per-round.) |
| 5 | `round{N}_context.md` | Only if you need background for the hook. Don't read this first — you'll get lost in details. |

**Do not read randomly.** The sublation is where you learn what the essay is actually about. The monks are source material, not the structure.

## Extract Key Elements

As you read, identify:

### 1. The Hook
What concrete phenomenon will draw readers in? Look for:
- A paradox or surprising fact from the context briefing
- A real-world example that crystallizes the tension
- Something readers will recognize from their own experience

### 2. The Surprising Turn
What did the dialectic reveal that wasn't obvious at the start?
- Check the "hidden question" in determinate negation
- What assumption did both monks share that neither noticed?
- What reframing transformed the debate?

### 3. The New Concept
What term or framework emerges from the synthesis?
- What got "elevated" in the Aufhebung?
- Is there a name for it yet, or does it need coining?

### 4. The Honest Limits
What tensions remain unresolved?
- Check the misfit register
- What did the validation agents critique?
- What's queued for future rounds?

### 5. The Best Material
Flag the most quotable/usable passages:
- Strongest formulations from monk essays
- The specific failure diagnoses from determinate negation (often the most interesting material)
- Concrete evidence and examples

---

## Exploratory 2×2s

Before checkpointing, **draw 2-3 candidate 2×2 diagrams** to map the space of possible framings. This helps you be precise about what the essay is actually about, and makes it easier for the user to evaluate your read.

### How to Draw a 2×2

**Start from the tension, not the dimensions.** Don't hunt for "the two most important dimensions." Start from the argument the 2×2 needs to resolve.

1. **Axis 1** = the surface tension from the dialectic (what the monks were arguing about)
2. **Axis 2** = an orthogonal dimension that turns "opposing positions on one line" into "different quadrants"
3. Label all four quadrants — each must name a real, distinct thing
4. Place the monks/positions
5. Read the **empty or under-occupied quadrant** — often where the synthesis or essay's insight lives

### ASCII Template

```
                       axis-2: [POLE B]
        ┌──────────────────────┬──────────────────────┐
        │ [quadrant label]     │ [quadrant label]     │
        │ — [who/what here]    │ — [who/what here]    │
 axis-1 ├──────────────────────┼──────────────────────┤  axis-1
[POLE A]│ [quadrant label]     │ [quadrant label]     │ [POLE B]
        │ — [who/what here]    │ — [who/what here]    │
        └──────────────────────┴──────────────────────┘
                       axis-2: [POLE A]
```

### Judging Tests

- **Orthogonality** — are the axes actually independent, or secretly correlated (a diagonal in disguise)?
- **All four meaningful** — does each quadrant name a real, distinct thing?
- **The telling empty quadrant** — empty for an interesting reason = payoff. Empty because axis was forced = defect.
- **Does it resolve the argument?** — does placing positions in quadrants actually clarify something?

### The Honesty Rule

Generate multiple 2×2s with different axis pairs — you're exploring, not committing. A legitimate output is also:

> "No second axis earns its place here — these positions genuinely sit on one line."

That's a finding, not a failure. Don't force a diagram.

---

## Checkpoint

Present your inventory to the user, including the exploratory 2×2s:

> "Here's what I found in the dialectic outputs:
> 
> **Hook candidates:** [list 2-3 concrete phenomena that could open the essay]
> 
> **The surprising turn:** [the hidden question or shared assumption both monks missed]
> 
> **Emerging concept:** [what the synthesis produced — named or unnamed]
> 
> **Honest limits:** [what remains unresolved]
> 
> **Best material:** [2-3 passages worth building around]
> 
> ---
> 
> **Exploratory 2×2s:**
> 
> [Draw 2-3 candidate diagrams with different axis pairs. For each, note what it clarifies and what's in the empty quadrant.]
> 
> ---
> 
> Does this capture the dialectic correctly? Which 2×2 (if any) feels like the right frame for the essay? Is there something I missed or misread?"

---

## HARD STOP

**You CANNOT proceed to Phase 2 until the user explicitly says to continue.**

Do not read the next phase file. Do not start working on analogies. Stay here.

If the user has questions, wants to discuss, or asks you to revise — do that. Say something like:

> "Happy to keep discussing until you give me the go-ahead to move to Phase 2."

Only when the user explicitly confirms (e.g., "continue," "next phase," "let's move on") should you read `phases/2-analogy.md`.

If the user identifies gaps or corrections, update your inventory. If a particular 2×2 resonates, note it — the second axis often becomes the analogical domain or key concept. If they want to revisit the dialectic itself, pause the sloptractions process.
