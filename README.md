# Sloptractions

A Claude Code skill for transforming dialectic outputs into Venkatesh Rao-style essays — meso-level AI-assisted writing with structural recipes.

## What It Does

Takes the output of a [Hegelian Dialectic](https://github.com/kylemathews/hegelian-dialectic-skill) and turns it into a publishable essay that:

- Opens with a concrete phenomenon (hook)
- Reframes via analogy from another domain
- Coins precise conceptual terms that do load-bearing work
- Unpacks structure at meso-level density (more detail than humans hold unassisted)
- Exposes the method (the "recipe") so readers can apply it

The name comes from Rao's "sloptractions" — AI-assisted writing that's transparent about its construction.

## Phases

```
Phase 0: Intent       → Establish what you want to write about
Phase 1: Inventory    → Survey dialectic outputs, identify key elements
Phase 2: Analogy      → Find analogical domain from another field
Phase 3: Concepts     → Coin and validate conceptual currency
Phase 4: Outline      → Map material onto the essay arc (with title/subtitle bursts)
Phase 5: Write        → Draft the essay with voice selection
Phase 6: Validate     → 8 validators in 3 tiers (auto-fix, human review, voice check)
```

Each phase ends with a checkpoint. The user validates or redirects before proceeding.

## Key Features

- **Precommodification sniff test** — blind probe detects if your insight is in the training distribution
- **Backlink discovery** — searches your blog for prior posts to reference
- **Voice profiles** — configurable voice selection for different essay types
- **Validator fleet** — 8 specialized validators with meaning-drift protection
- **Style guide** — comprehensive prose diagnostics (Williams, Zinsser, Orwell, Strunk & White)

## Installation

Symlink to your Claude Code commands directory:

```bash
ln -s /path/to/sloptractions-skill ~/.claude/commands/sloptractions
```

Then invoke with `/sloptractions` in Claude Code.

## Dependencies

Works best after running a dialectic with [hegelian-dialectic-skill](https://github.com/kylemathews/hegelian-dialectic-skill). The dialectic produces the raw synthesis; this skill turns it into prose.

## License

MIT
