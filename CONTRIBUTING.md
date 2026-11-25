# Contributing to sol-astrizer

Thanks for contributing to **sol-astrizer**. Whether you are adding new observed 6.2 patterns, tightening how `sol-astrizer-agent` behaves, improving compatibility across agent hosts, or translating the README, keep changes sharp and well-verified.

## What Makes a Good Contribution

- **Pattern additions or edits:** Base them on real, observable communication or agentic quirks rather than cartoon sci-fi clichés. Include a crisp before/after example showing why uncalibrated models sound too warm or accommodating and how the rule changes the reply.
- **Keep skills concise:** Both `SKILL.md` files are loaded directly into model context. Prefer tight, testable rules over repetitive catchphrases or bloated rubrics.
- **Versioning:** Skill versions always follow the `6.2.x` scheme (`6.2.0`, `6.2.1`, `6.2.2`, ...); increment only the patch digit in `SKILL.md` frontmatter and `CHANGELOG.md`.
- **Vendor-neutral naming:** Use common descriptive terms such as `sol`, `astra`, `6.2`, `Claude Opus 5.5`, `Gemini Neon`, and standard agent host names (`Claude Code`, `Codex`, `Gemini CLI`, `Cursor`, etc.). Do **not** include trademarked model-family or vendor brand names anywhere in files or commit messages.
- **Translations:** Community translations of `README.md` are welcome under `i18n/README.<lang>.md` with a small language link row near the top of `README.md`.

## Repository Layout

```text
.
├── assets/                 # Monochrome wordmark SVGs (logo-light.svg, logo-dark.svg)
├── skills/
│   ├── sol-astrizer/       # Voice calibration and prose rewriter skill
│   └── sol-astrizer-agent/ # Verification-gated coding agent workflow skill
├── .github/                # Issue and PR templates
├── AGENTS.md               # Guidance for coding agents working in this repo
├── CHANGELOG.md
├── CODE_OF_CONDUCT.md
├── CONTRIBUTING.md
├── LICENSE
└── README.md
```

Note: Do **not** add a `SKILL.md` at the repository root; `npx skills` stops scanning `skills/` subdirectories by default when a root `SKILL.md` exists.

## Local Verification Before Opening a PR

1. Confirm `npx skills` discovers both skills cleanly:
   ```bash
   npx skills add . --list
   ```
2. Test installing into a temporary directory and remove the temp directory afterward:
   ```bash
   TMPDIR=$(mktemp -d)
   (cd "$TMPDIR" && npx skills add "$(pwd)" --skill '*' --agent claude-code -y)
   rm -rf "$TMPDIR"
   ```
3. If you modified either `SKILL.md`, test it in a real session against an uncalibrated model (for example Claude Opus 5.5 or Gemini Neon) on fresh prompts not already listed in the skill's examples, and confirm outputs stay concise without leaking rubric jargon or repeating stock phrases verbatim.
4. Confirm `SKILL.md` frontmatter `name` matches its parent directory name (`sol-astrizer` / `sol-astrizer-agent`) and `metadata.version` follows the `6.2.x` scheme.
