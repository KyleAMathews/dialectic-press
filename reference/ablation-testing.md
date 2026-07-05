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
