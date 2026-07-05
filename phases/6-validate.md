# Phase 6: Validate & Polish

## Goal

Review the draft against quality criteria. Revise as needed. Finalize.

## Spawn a Fresh Reviewer

**Important:** The agent that wrote the draft will be biased toward its own choices. Spawn a fresh subagent to do the validation. The reviewer should:

1. Read the essay file (not the conversation context)
2. Read `reference/style-guide.md` for prose diagnostics
3. Apply the validation checklist below
4. Return specific findings with line references
5. Not see the earlier phases or decision-making process

**Subagent prompt — use this verbatim:**

> You are reviewing an essay for quality. You have not seen the writing process — approach it fresh.
>
> **Step 1:** Read `reference/style-guide.md` — this contains the prose diagnostics you'll apply (Williams tests, Zinsser tests, Orwell's questions, Strunk & White patterns, cliche lists, padding to cut)
>
> **Step 2:** Read [essay path]
>
> **Step 3:** Apply the validation checklist below. For each issue found, cite the specific passage and explain the problem.
>
> [Paste the validation checklist from this file]

The orchestrator receives the findings and presents them to the user. The user decides what to revise.

---

## Validation Checklist

Work through these questions. Be honest — if the answer is "no," the essay needs revision.

### 0. Measurable Metrics (Run First)

Run these quantitative checks before subjective review. They catch mechanical issues quickly.

| Metric | Target | How to Check |
|--------|--------|--------------|
| Sentence length variance | Std dev > 8 words | Count words per sentence, compute std dev |
| Em-dash usage | 1-3 per 1000 words | Count "—" occurrences |
| First-person in first 100 words | Yes | Check first 100 words for "I" |
| Cliché count | 0 from banned list | Scan against style-guide.md cliché lists |
| AI-ism count | 0 | Search: "delve," "crucial," "tapestry," "multifaceted," "nestled," "it's important to note" |
| "Actually/really/literally" | ≤1 per 1000 words | These imply correction; overuse is filler |

**If metrics fail:** Fix mechanically before continuing to subjective review.

### 1. Does the analogy do work?
- If you removed the analogy, would the essay collapse or survive?
- It should *need* the analogy — not just use it as decoration
- Test: Can you state the argument without the analogical vocabulary? If yes, the analogy isn't load-bearing.

**If no:** Return to Phase 2 or strengthen the analogy's role in the Turn section.

### 2. Does the essay have a genuine insight?
- Is there a reframing that changes how you see the topic?
- Test: Does the essay make it hard to go back to thinking in the old terms?
- Test: Could you summarize the insight in one sentence that sounds non-obvious?

**If no:** The problem is upstream — return to the dialectic.

Note: This is an essay, not a dialectic synthesis. You don't need to "elevate both monks" — the essay uses the dialectic's insight to make an argument. It's fine to take a side or dismiss a position if the argument supports it.

### 3. Can readers use the conceptual currency?
- Test: "In situation X, is this [term A] or [term B]?"
- If the distinction doesn't help with new cases, the term isn't doing work
- Test: Will readers remember and reuse these terms?

**If no:** Revise or remove weak terms. Less is better than hollow.

### 4. Is the recipe usable?
- Test: Apply it to a different topic in your head
- If it's too specific to this essay, generalize
- If it's too generic ("think carefully, then write"), add specificity

**If no:** Revise the recipe to be both honest and transferable.

### 5. Is it pleasurable to read?
- Read it aloud (or have the user read it)
- Where do you find yourself skimming? Tighten or cut there.
- Does the prose have rhythm? Vary sentence lengths.
- Any cliches that slipped through? (dying metaphors, familiar phrases that no longer evoke images)

**If no:** Line-edit for voice. Cut 10-20%.

### 6. Information Density Check
- Any paragraphs that assert much but specify nothing?
- Any sections that could be cut without losing substance?
- Is there enough concrete detail to reward close reading?

**If no:** Either add specifics or cut the vague material.

---

## Structural Ablation Suite

After subjective checklist, run structural tests. These use fresh subagents with no context from writing — see `reference/ablation-testing.md` for full protocol.

### Test 1: Analogy Knockout

**Setup:** Generate a version with analogical vocabulary replaced by literal descriptions.

**Fresh subagent prompt:**
> Read this essay. Does the argument still work? Rate comprehension 1-5 and note where confusion begins.

**Interpretation:**
- Comprehension 4-5 → analogy is decorative, not load-bearing
- Comprehension 2-3 → analogy does some work
- Comprehension 1-2 → analogy is essential (good)

### Test 2: Synthesis Section Removal

**Setup:** Remove the "New Frame" section entirely.

**Fresh subagent prompt:**
> Read this essay (missing one section). What is the main argument? What's missing?

**Interpretation:**
- If subagent reconstructs the synthesis → section was restating, not adding
- If subagent is confused → synthesis does real work (good)

### Test 3: Meso-Level Density Test

**Setup:** Summarize the essay to 50% length.

**Fresh subagent prompt:**
> Read both versions. What was lost? Rate the loss 1-5 (1 = nothing important, 5 = gutted).

**Interpretation:**
- Loss rating 1-2 → original was padded
- Loss rating 3-4 → appropriate density
- Loss rating 5 → may be too dense (reader can't absorb)

### Running the Suite

1. Each test uses a **separate fresh subagent** — no shared context
2. Subagents read only the essay (or modified version) — no dialectic materials
3. Results inform revision priority, not pass/fail

**Present to user:**
> "Ablation results:
> - Analogy knockout: [score] — [interpretation]
> - Synthesis removal: [reconstruction/confused]
> - Density test: [loss rating] — [interpretation]
> 
> [Recommendations if any tests suggest issues]"

---

## Revision Process

If validation surfaces issues:

1. **Minor issues (voice, AI-isms, density):** Edit the draft directly
2. **Structural issues (analogy doesn't work, synthesis is weak):** Return to the relevant phase
3. **Fundamental issues (dialectic was shallow):** Pause sloptractions, return to dialectic

After revisions, re-run the validation checklist on changed sections.

## Final Polish

Once validation passes:

1. **Check the opening line** — is it strong enough to earn the reader's attention?
2. **Check the closing line** — does it land, or trail off?
3. **Check transitions** — do sections connect, or just stack?
4. **Check the recipe** — does it match what you actually did?

## Output

Present validation results to the user:

> "Validation complete:
> 
> **Analogy:** [pass/needs work — brief note]
> **Synthesis:** [pass/needs work]
> **Conceptual currency:** [pass/needs work]
> **Recipe:** [pass/needs work]
> **Readability:** [pass/needs work]
> **Density:** [pass/needs work]
> 
> [If all pass:] Ready to finalize.
> [If issues:] Recommend revising [X, Y] before finalizing."

---

## HARD STOP

**You CANNOT finalize until the user explicitly approves.**

Do not finalize. Do not declare the essay complete. Stay here.

If the user has questions, wants revisions, or needs to discuss findings — do that. Say something like:

> "Happy to keep refining until you give me the go-ahead to finalize."

Only when the user explicitly confirms (e.g., "finalize," "ship it," "done") should you proceed to Finalizing.

The user may:
- Approve and finalize
- Request specific revisions
- Want to read the draft themselves before deciding
- Decide the essay isn't working and abandon or restart

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
