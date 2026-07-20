# Dialectic Press

An agent skill for transforming dialectic outputs into essays — meso-level AI-assisted writing with structural recipes.

## What It Does

Takes the output of a [Hegelian Dialectic](https://github.com/KyleAMathews/hegelian-dialectic-skill) and turns it into a publishable essay that:

- Opens with a concrete phenomenon (hook)
- Reframes via analogy from another domain
- Coins precise conceptual terms that do load-bearing work
- Unpacks structure at meso-level density (more detail than humans hold unassisted)
- Exposes the method (the "recipe") so readers can apply it

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

- **Interactive workshop** — each phase ends with a checkpoint; you validate or redirect before proceeding
- **Intent-first** — establishes what you want to write before touching the dialectic materials
- **Precommodification detection** — blind probe tests if your insight is already in the training distribution
- **Idea bursts** — generates 8-12 candidates for titles, subtitles, and descriptions before selecting
- **Style guide** — comprehensive prose diagnostics drawing on Williams, Zinsser, Orwell, Strunk & White
- **Validator fleet** — 8 specialized reviewers catch different failure modes (clichés, voice drift, structural issues)

## Installation

Symlink to your agent's commands/skills directory. For Claude Code:

```bash
ln -s /path/to/dialectic-press ~/.claude/commands/dialectic-press
```

Then invoke with `/dialectic-press`.

## Dependencies

Works best after running a dialectic with [hegelian-dialectic-skill](https://github.com/KyleAMathews/hegelian-dialectic-skill). The dialectic produces the raw synthesis; this skill turns it into prose.

## Inspirations

- [Sloptractions](https://substack.com/@contraptions/note/c-271675689) — Venkatesh Rao's AI-assisted essay format
- [LLMs Pre-Commodify Ideas](https://summerlightning.substack.com/p/llms-pre-commodify-ideas) — the precommodification concept

## License

MIT
