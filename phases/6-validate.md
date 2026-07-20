# Phase 6: Validate & Polish

## Goal

Review the draft against quality criteria using specialized validators. Revise as needed. Finalize.

## Validator Fleet

Split validation across focused subagents. Each validator has a small, coherent job — this prevents dropped checks.

**Spawn all validators in parallel.** Each reads the essay fresh with no writing-phase context.

---

### Validator 1: Prose Mechanics

**Focus:** Sentence-level craft, AI-isms, padding

**Subagent prompt:**

> You are validating prose mechanics. Read `reference/style-guide.md` first, then read [essay path].
>
> Check for:
> 1. **Sentence length variance** — std dev should be > 8 words. Flag if monotonous.
> 2. **First 7-8 words test** — can you find subject and verb? Flag buried subjects.
> 3. **Nominalizations** — circle -tion/-ment/-ness words. Flag verbs hiding as nouns.
> 4. **AI-isms** — search for: "delve," "crucial," "tapestry," "multifaceted," "nestled," "it's important to note," "actually," "really," "literally" (unless genuinely correcting). Flag all.
> 5. **Padding** — "the fact that," "there is/are," "in order to," "it's worth noting." Flag all.
> 6. **Em-dash usage** — 1-3 per 1000 words is good. Flag if overused or absent.
>
> **CRITICAL: Preserve meaning.** Every suggested fix must say the same thing as the original. Cleaner ≠ different. If removing padding loses information, keep the original or flag for human review.
>
> Return: list of issues with line references and suggested fixes.

---

### Validator 2: Voice & Tone

**Focus:** Teacher mode, fellow-traveler register, throat-clearing

**Subagent prompt:**

> You are validating voice and tone. Read `reference/style-guide.md` (especially "Us vs. Them / Teacher Mode" and "Throat-Clearing" sections) first, then read [essay path].
>
> Check for:
> 1. **Teacher mode** — "They're making the same mistake," "You think you're standing," "They're not wrong that X, they're wrong about..." Flag us-vs-them postures.
> 2. **Throat-clearing** — sentences that sound important but convey nothing. "When X spoke, people listened." "Few topics are as important as..." Flag ambient credentialing.
> 3. **Protesting too much** — "An honest acknowledgement," "To be frank," "The truth is..." Flag insecurity markers.
> 4. **First person in first 100 words** — should have "I" early. Flag if missing.
> 5. **Fellow-traveler register** — is the essay "we're figuring this out together" or "let me explain what you're missing"? Note overall posture.
>
> Return: list of issues with line references and suggested rewrites.

---

### Validator 3: Clichés & Stale Metaphors

**Focus:** Dying metaphors, wallpaper phrases, dead images

**Subagent prompt:**

> You are hunting stale language. Read `reference/style-guide.md` (especially "Cliche Avoidance" section) first, then read [essay path].
>
> Check for:
> 1. **Dying metaphors** — stand shoulder to shoulder, toe the line, Achilles' heel, play into the hands of, run roughshod over, take up the cudgels for. Flag any.
> 2. **Tech/business clichés** — move the needle, boil the ocean, low-hanging fruit, deep dive, double down, at the end of the day, the reality is, it goes without saying. Flag any.
> 3. **Wallpaper phrases** — any phrase so familiar it no longer creates a picture. Test: does this evoke an image, or do readers' eyes slide past? Flag suspects.
> 4. **Mixed metaphors** — two incompatible images colliding. Flag any.
> 5. **Freshness test** — for each metaphor/simile, ask: have I seen this exact phrase before? If yes, flag it.
>
> **CRITICAL: Preserve meaning.** Replacements must convey the same claim. "Move the needle on retention" → "increase retention" is fine. "Move the needle on retention" → "create impact" loses specificity — flag for human instead.
>
> Return: list of stale phrases with line references. For each, suggest either plain language or a fresh image.

---

### Validator 4: Structural Integrity

**Focus:** Does the analogy work? Does the synthesis add? Is the recipe usable?

**Subagent prompt:**

> You are validating essay structure. Read [essay path] only — no style guide needed.
>
> Check for:
> 1. **Analogy load-bearing test** — mentally remove the analogical vocabulary. Does the argument still work? If yes, the analogy is decorative. Note your finding.
> 2. **Synthesis test** — is there a genuine reframing? Could you summarize the insight in one non-obvious sentence? Note whether this passes.
> 3. **Conceptual currency test** — for each coined term, ask: "In situation X, is this [term A] or [term B]?" If the distinction doesn't help with new cases, note which terms are weak.
> 4. **Recipe usability** — could you apply this recipe to a different topic? Is it too specific (only works for this essay) or too generic ("think carefully")? Note your assessment.
>
> Return: structural assessment for each test. Note what works and what needs revision.

---

### Validator 5: Density & Flow

**Focus:** Information density, pacing, transitions

**Subagent prompt:**

> You are validating density and flow. Read [essay path] only.
>
> Check for:
> 1. **Empty paragraphs** — any paragraph that asserts much but specifies nothing? Flag vague sections.
> 2. **Skimmable sections** — where would a reader's attention drift? Flag boring stretches.
> 3. **Dense blocks without reset** — after complexity, is there a punchy single-sentence verdict? Flag unrelieved density.
> 4. **Transitions** — do sections connect or just stack? Note weak joints.
> 5. **Opening line** — strong enough to earn attention? Note if weak.
> 6. **Closing line** — does it land or trail off? Note if weak.
>
> Return: list of density/flow issues with locations. Note overall pacing assessment.

---

### Validator 6: Audience Fit

**Focus:** Assumed knowledge level, over-explaining, under-explaining

**Subagent prompt:**

> You are validating audience fit. Read `reference/style-guide.md` (especially "Audience" section) first, then read [essay path].
>
> The target audience is smart friends who already know the domain. They don't need basics explained.
>
> Check for:
> 1. **Over-explaining** — definitions of terms the audience already knows. "X, which means Y." Flag condescension.
> 2. **Unnecessary preamble** — "Before we dive in, let's establish..." "To understand this, we first need to..." Flag onboarding for people who don't need it.
> 3. **Under-explaining** — jargon or references that even smart friends wouldn't know without context. Flag gaps.
> 4. **Assumed context** — does the essay assume shared experiences that match the likely audience? Note mismatches.
> 5. **Density calibration** — is this dense enough to reward close reading, or padded for a mass audience? Note overall calibration.
>
> Return: list of audience fit issues with line references. Note overall assessment: too dumbed down / well calibrated / too insider.

---

### Validator 7: Backlink Integration

**Focus:** Are referenced posts woven in naturally?

**Subagent prompt:**

> You are validating backlink integration. Read [essay path].
>
> Find all links to the author's other posts (internal links to the blog).
>
> For each backlink, check:
> 1. **Organic placement** — does the link arise naturally from the argument, or feel shoehorned in?
> 2. **Context provided** — would a reader understand why this link matters without clicking? Or is it a bare "as I wrote before"?
> 3. **Value added** — does referencing this post strengthen the current essay, or is it just self-promotion?
> 4. **Link text quality** — is the anchor text descriptive, or generic ("this post," "here")?
>
> Return: assessment for each backlink. Note any that feel forced or undercontextualized.
>
> If no backlinks found, note that — may be an opportunity to add connections.

---

### Validator 8: Factual Claims

**Focus:** Checkable claims that might be wrong

**Subagent prompt:**

> You are fact-checking. Read [essay path].
>
> Identify claims that are:
> 1. **Verifiable facts** — dates, names, statistics, historical events, attributions ("X said Y")
> 2. **Technical claims** — how systems work, definitions of terms, cause-effect relationships
> 3. **Citations** — references to specific works, papers, posts
>
> For each, assess:
> - Is this claim accurate to your knowledge?
> - Is it stated with appropriate confidence (fact vs. speculation)?
> - Could it be easily checked? If so, note the check.
>
> **Do not flag:**
> - Opinions or interpretations
> - Analogies or metaphors (even if imperfect)
> - Speculative claims clearly marked as such
>
> Return: list of factual claims with confidence assessment. Flag any that seem wrong or unverifiable. Note claims that should be softened ("X is true" → "X appears to be true").

---

## Running the Fleet

Validators are split into three tiers based on how safely they can auto-fix.

### Tier 1: Auto-Fix Loop (Validators 1, 3, 8)

These find mechanical issues with clear fixes. Run in a loop until clean.

**Process:**
1. Spawn Validators 1 (Prose Mechanics), 3 (Clichés), 8 (Factual Claims) in parallel
2. Collect findings
3. Apply all suggested fixes
4. Re-run the same validators on the updated draft
5. Repeat until no issues found OR max 3 passes
6. **After loop completes:** Orchestrator reviews all changes for meaning drift (see below)

**Why these are safe to loop:**
- Prose Mechanics: AI-isms, padding, nominalizations have unambiguous fixes
- Clichés: stale phrase → plain language or fresh image
- Factual Claims: wrong → correct, or overconfident → soften

**Max 3 passes** — if still finding issues after 3, something's wrong upstream. Stop and flag for human.

**CRITICAL: Preserve Meaning**

When fixing clichés, padding, or AI-isms, the replacement must say the same thing. Cleaner prose ≠ different prose.

- **Bad fix:** "move the needle" → "create impact" (vague, loses specificity)
- **Good fix:** "move the needle" → "increase conversion by 2%" (preserves the claim)
- **Bad fix:** "delve into the details" → "explore" (loses the depth implication)
- **Good fix:** "delve into the details" → "examine each component" (same meaning, no AI-ism)

If a cliché or padding phrase is load-bearing (removing it loses meaning), keep it or flag for human review rather than replacing with something vaguer.

---

### Tier 2: Human Review Required (Validators 4, 5, 6, 7)

These involve judgment calls. Present findings to user; they decide what to fix.

**Process:**
1. Spawn Validators 4 (Structural), 5 (Density/Flow), 6 (Audience), 7 (Backlinks) in parallel
2. Collect findings
3. Present to user with recommendations
4. User directs which fixes to apply
5. No auto-loop — one pass, then human decides

**Why these need human judgment:**
- Structural: if analogy is decorative, can't fix with edits — need earlier phase
- Density/Flow: over-tightening loses texture; subjective pacing
- Audience: calibration depends on intended readers
- Backlinks: can't invent connections; user knows their corpus

---

### Tier 3: Voice Check (Validator 2)

Voice fixes risk overcorrection. Teacher mode → wishy-washy is not an improvement.

**Process:**
1. Run Validator 2 (Voice & Tone)
2. Present findings with suggested rewrites
3. **User approves each rewrite before applying** — don't batch-apply
4. No loop — one pass, curated fixes

**Why this needs extra care:**
- Fixing "they're making a mistake" could become "perhaps some might consider..."
- Fellow-traveler register is a vibe, not a checklist
- Human ear needed to confirm rewrites preserve voice

---

## Execution Order

Run all three tiers, but handle results differently:

```
1. Spawn Tier 1 validators (1, 3, 8) — auto-fix loop, max 3 passes
   ↓
2. Spawn Tier 2 validators (4, 5, 6, 7) in parallel while Tier 1 loops
   ↓
3. Spawn Tier 3 validator (2) after Tier 1 completes
   ↓
4. Present combined results:
   - Tier 1: "Auto-fixed [N] issues across [M] passes"
   - Tier 2: findings for user decision
   - Tier 3: voice rewrites for user approval
```

---

## Presenting Results

After all tiers complete:

> "Validation complete.
>
> **Auto-fixed (Tier 1):**
> - Prose mechanics: [N] issues fixed
> - Clichés: [N] phrases replaced
> - Factual claims: [N] corrections/softenings
> - Passes required: [1-3]
>
> **Tier 1 changes for review (check for meaning drift):**
>
> | Original | Replacement | ⚠️ Drift? |
> |----------|-------------|-----------|
> | "move the needle on retention" | "increase retention" | ✓ OK |
> | "delve into the architecture" | "explore" | ⚠️ loses depth |
> | "the fact that users churn" | "users churn" | ✓ OK |
>
> [Flag any replacements where meaning may have shifted. User can revert or revise.]
>
> **Needs your decision (Tier 2):**
>
> *Structural:*
> - Analogy: [load-bearing / decorative — recommendation]
> - Synthesis: [genuine / restating — recommendation]
> - Conceptual currency: [which terms work, which are weak]
> - Recipe: [usable / too specific / too generic]
>
> *Density & Flow:*
> - [issue]: [location] — [recommendation]
>
> *Audience Fit:*
> - [overall assessment: too dumbed down / well calibrated / too insider]
> - [specific issues if any]
>
> *Backlinks:*
> - [assessment per link, or note if none found]
>
> **Voice rewrites for approval (Tier 3):**
> 1. [original] → [proposed rewrite] — approve? y/n
> 2. [original] → [proposed rewrite] — approve? y/n
> ...
>
> **Overall:** [Ready to finalize / Needs revision in X areas]"

---

## Ablation Suite (Optional)

If Validator 4 (Structural) flags problems, run deeper ablation tests. See `reference/ablation-testing.md` for protocol.

These are heavier — only run if structural issues surface.

---

## Revision Process

Based on tier results:

1. **Tier 1 auto-fixes:** Already applied. Review if curious.
2. **Tier 2 findings:** User directs which to fix. If structural issues, may need earlier phase.
3. **Tier 3 voice rewrites:** Apply only user-approved changes.

After user-directed revisions, re-run only affected validators if needed.

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
