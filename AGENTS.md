# AGENTS.md

Instructions for coding agents working inside the `sol-astrizer` repository.

## Structure

- `skills/sol-astrizer/SKILL.md` — Voice calibration and text-rewriting skill.
- `skills/sol-astrizer-agent/SKILL.md` — Verification-gated coding agent workflow skill.
- `assets/logo-light.svg`, `assets/logo-dark.svg` — Monochrome wordmarks used in `README.md`.
- Do **not** create a `SKILL.md` at the repository root (doing so hides `skills/*/` from `npx skills` discovery without `--full-depth`).
- Do **not** edit or remove `.gitignore` entries protecting local workspace assets such as `assets/icon.svg`.

## Conventions

- Keep all primary repository docs and skills in English.
- Keep `SKILL.md` YAML frontmatter `name` identical to its parent directory name (`sol-astrizer`, `sol-astrizer-agent`).
- Use vendor-neutral descriptors (`sol`, `astra`, `6.2`) in prose, examples, and commit messages; avoid trademarked model or vendor names.
- Keep skill rules concise and realistic—avoid bloated rubrics, repetitive catchphrases, or cartoon robot clichés.

## Checks Before Committing

```bash
npx skills add . --list
git status
```
