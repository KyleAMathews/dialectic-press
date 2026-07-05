# Style Guide

This guide draws on:

- **Strunk & White** (*The Elements of Style*) — omit needless words, use active voice, put statements in positive form
- **George Orwell** ("Politics and the English Language") — never use a familiar metaphor, prefer short words, cut ruthlessly
- **William Zinsser** (*On Writing Well*) — clarity, unity, anticipate what the reader will ask next
- **Joseph Williams** (*Style: Lessons in Clarity and Grace*) — characters as subjects, actions as verbs, old before new
- **Venkatesh Rao** — meso-level density, structural transparency, conceptual handles, dense blocks → single-sentence reset

---

## Audience

You're writing for smart friends who already get most of what you're saying. They know the domain, they've thought about these problems, they don't need basics explained. 

This means:
- Skip the explainers. Don't define terms your audience already knows.
- Assume shared context. Reference ideas without preamble.
- Get to the interesting part fast. The hook isn't "here's why this matters" — it's the insight itself.
- Trust them to follow. Dense is fine. Jargon is fine if it's the right word.

You're not writing for a mass audience. You're not trying to onboard newcomers. You're offering a lens to people who are already looking at the same thing.

---

## Voice

- **Conversational but substantive.** Writing like explaining something interesting to a smart friend.
- **Confident without hedging.** Direct statements. "The real difference is..." not "One might argue that..."
- **First person welcome.** "I realized," "I've been thinking" — this is personal writing.
- **Enthusiastic where genuine.** If you're excited about an idea, say so.

---

## Sentence-Level

- **Vary length.** Short declaratives for emphasis. Longer ones for explanation. Punchy resets after dense passages.
- **Front-load.** Put conclusions first, then explain. Don't bury the point.
- **Active voice default.** Say who does what.
- **Positive form.** Say what something IS, not what it ISN'T.
- **Em-dashes encouraged** — vary with commas and parentheses. One per sentence max.

### Characters and Actions (Williams)

Make actors the subjects of sentences. Make their actions verbs.

- **Bad:** "The implementation of the system by the team resulted in improvements."
- **Good:** "The team implemented the system and improved performance."

Watch for **nominalizations** — verbs hiding as nouns. "Made a decision" → "decided." "The analysis of" → "analyzing."

### Sentence Flow (Williams + Zinsser)

- **Old before new.** Start sentences with familiar info, end with new/complex. The end carries emphasis.
- **Get to the verb fast.** Within 7-10 words of starting. Don't front-load with long introductory phrases.
- **Consistent subjects.** Keep grammatical subjects consistent across related sentences. Jumping subjects makes readers work.
- **Anticipate reader questions.** After each sentence, ask: "What will the reader wonder now?" Answer that in your next sentence. Don't repeat — move forward.

---

## Cliche Avoidance (The Load-Bearing Rule)

**Never use a metaphor, simile, or figure of speech you are used to seeing in print.**

Cliches fail because they no longer evoke images — readers' eyes slide past them. The test: does this phrase create a picture, or has it become wallpaper?

**Dying metaphors:**
- stand shoulder to shoulder, toe the line, Achilles' heel, ring the changes, play into the hands of, run roughshod over, take up the cudgels for

**Dying phrases in tech/business writing:**
- move the needle, boil the ocean, low-hanging fruit, deep dive, double down, at the end of the day, the reality is, it goes without saying, needless to say

**The fix:** When you reach for a familiar phrase, stop. Either say it plainly or invent a fresh image. If you can't make it fresh, plain is better than stale.

---

## Padding to Cut

- "The fact that" → rephrase
- "There is / There are" → start with the subject
- "In order to" → "to"
- "It's worth noting that" → just note it
- Qualifiers that hedge without adding: "very," "quite," "rather," "somewhat," "basically," "essentially"
- Emphasis words that have lost their meaning: "actually," "really," "literally," "truly" — these imply correction or surprise, but AI overuses them as filler. Delete unless you're genuinely correcting a misconception.

---

## Throat-Clearing and False Gravitas

Watch for sentences that sound important but convey nothing:
- "When Brooks spoke about what made software hard, people listened."
- "This question has occupied thinkers for centuries."
- "Few topics are as important as..."

These are **ambient credentialing** — establishing authority or importance without showing it. The fix: state the idea. If Brooks matters, quote him or describe his specific claim. If the question is important, show why with a concrete stake.

Test: Delete the sentence. Does the argument lose anything? If not, cut it.

---

## Us vs. Them / Teacher Mode

AI defaults to didactic posture — the author as analyst explaining a pattern to "other" people who aren't getting it. This creates implicit superiority: the writer understands; the subjects don't.

**Signs you're doing it:**
- "They're making the same mistake..."
- "They're not wrong that X. They're wrong about what it means."
- "You think you're standing on solid ground"
- "Every time this happens, you hear the same sound"
- Repeated "now" with a "can you believe it" energy

**Why it happens:** When synthesizing an argument from analysis, the natural posture is "let me explain what's really going on." This creates a false binary: enlightened readers vs. confused practitioners.

**The fix — shift from teacher to fellow traveler:**
- "They're making the same mistake" → "It's easy to believe this is the irreducible core. Every previous generation believed the same thing."
- "you hear the same sound" → "some of us say the same thing"
- "They're wrong about what it means" → "Something is being lost — that's real. But what's being lost is a particular adaptation, not the craft itself."
- "You think you're standing" → "We're all standing"

**The register you want:** "We're all experiencing this together — here's a lens that makes sense of it."

**Not:** "Let me explain what you're missing."

---

## Protesting Too Much

Watch for qualifiers that undermine by over-insisting:
- "An honest acknowledgement" — why would you say it's honest unless the rest might not be?
- "To be frank..." / "I'm not gonna lie..." — implies you were lying before
- "It's important to note that..." — if it's important, just note it
- "The truth is..." — as opposed to the lies you've been telling?

These are verbal tics that signal insecurity. Delete them — the statement is stronger without.

---

## Paragraphs

- **Short to medium.** Rarely more than 4-5 sentences. Often 1-2 for pacing.
- **One idea per paragraph.**
- **Whitespace is generous.** Let ideas breathe.

---

## Structure (Rao patterns)

- **Lead with a concrete phenomenon.** Not an abstract claim — something specific and recognizable.
- **Create cognitive handles.** Named concepts that anchor the argument.
- **Dense blocks → single-sentence reset.** After building complexity, punctuate with a verdict.
- **Loop back.** Close by returning to the opening image, transformed.

---

## The Test

1. What am I actually trying to say?
2. Does every phrase create a picture, or has it become wallpaper?
3. Would I say this out loud to a smart friend?

---

## Prose Diagnostics

When a sentence or paragraph feels off but you can't pinpoint why, use these tests:

### Sentence-Level (Williams)

**The First 7-8 Words Test**
- Underline the first 7-8 words. Can you find the main subject and verb?
- Is the subject a real actor, or an abstraction? ("The establishment of..." vs "We established...")
- Is the verb a strong action, or weak verb + nominalization? ("made a decision" vs "decided")

**Nominalization Detector**
- Circle words ending in -tion, -ment, -ness, -ity. These often hide the real action.
- Ask: what verb is buried here? Can I restore it?

**Subject-Verb Distance**
- More than 6-7 words between subject and verb? Reader loses the thread.

### Read-Aloud Tests (Zinsser)

**The Monotony Test**
- Read three consecutive sentences aloud. Same rhythm/length? Vary them.

**The Stumble Test**
- Where do you stumble or run out of breath? That's where structure is fighting you.

**The "What Am I Trying to Say?" Test**
- After reading a sentence, can you say it more directly in plain speech? If not, it's unclear.

### Paragraph-Level

**Topic Sentence Audit**
- Can you identify each paragraph's main claim in one sentence?
- Does that claim appear in the first 2 sentences? Buried topic sentences confuse readers.

**The "So What?" Chain**
- Read each sentence and ask "so what?" or "why does this follow?"
- If you can't answer, there's a coherence gap.

### Complex vs Unclear

A sentence is **complex but clear** if:
- Subject and verb are findable in the first 7-8 words
- Each clause has a clear agent doing something
- Subordinate clauses attach logically

A sentence is **unclear** if:
- You can't identify who is doing what
- Multiple readings produce different interpretations
- The main point only emerges after the sentence ends

### Orwell's Six Questions

For any sentence that feels off, ask:
1. What am I trying to say?
2. What words will express it?
3. What image or idiom will make it clearer?
4. Is this image fresh enough to have an effect?
5. Could I put it more shortly?
6. Have I said anything avoidably ugly?

### Strunk & White Pattern Hunt

Search the draft for these and revise:
- **"The fact that"** → always rephrase
- **"Who is / which was"** → usually delete ("his cousin, who is a member" → "his cousin, a member")
- **"There is / There are"** → start with the real subject
- **Lonely qualifiers:** "rather," "very," "little," "pretty," "quite" — cut if they add nothing
- **Separated pairs:** subject far from verb? modifier far from what it modifies? Move them together
- **Broken parallels:** "reading, writing, and to paint" → "reading, writing, and painting"
- **Buried emphasis:** the stress position is sentence-final. Important word stuck in the middle? Restructure

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
