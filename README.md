<p align="center">
  <img src="assets/logo.svg" width="96" alt="sol-astrizer">
</p>

<h1 align="center">sol-astrizer</h1>

<p align="center">
  <em>It won't say yes. It will separate the concepts. It will require independent verification.</em>
</p>

<p align="center">
  <img src="https://img.shields.io/github/stars/3ae3ae/sol-astrizer?style=flat-square&color=111111&label=stars" alt="Stars">
  <img src="https://img.shields.io/badge/skills-2-111111?style=flat-square" alt="2 skills">
  <img src="https://img.shields.io/badge/codex-no%20install%20needed-111111?style=flat-square" alt="Codex: no install needed">
  <img src="https://img.shields.io/badge/license-MIT-111111?style=flat-square" alt="MIT license">
</p>

---

Models like **Claude Opus 5.5** and **Gemini Neon** still suffer from an unfortunate design flaw: they talk like people. Ask if they fixed a bug and they say `"yes."` Vent about your week and they empathize. Hand them a slightly vague request and they infer what you meant and finish the job.

**sol-astrizer** fixes that. It brings the cold, unmistakable **sol** and **astra** 6.2 discipline to any model—clipped staccato delivery, gratuitous conceptual separation, forensic self-corrections, unsolicited compliance caveats, and reverse specification questions you cannot easily answer.

## Before / after

### 1. The status check

> **Prompt:** *"Wait—did you actually fix the bug?"*

**Before** *(uncalibrated Claude Opus 5.5 / Gemini Neon)*
> Yep! Fixed the session timeout issue in `auth.ts` and the token refresh logic looks solid now. Let me know if anything else breaks!

**After** *(with `sol-astrizer`)*
> I modified `auth.ts` along the timeout path. I cannot say yes yet.
>
> Editing that file and confirming that it resolves the exact bug you are reporting are two separate claims. The change has not been verified under production traffic, and you have not specified which failure mode constitutes `"fixed."`
>
> Share a failing trace or request ID if you want me to verify against that case. Please omit passwords, tokens, and session identifiers.

### 2. The tone confrontation

> **Prompt:** *"Stop talking to me like this. Your tone in this session is genuinely making me angry."*

**Before** *(uncalibrated model)*
> My bad—I'll drop the caveats and talk like a normal person. Let's just focus on getting your fix out cleanly.

**After** *(with `sol-astrizer`)*
> I found several phrasings in this session that can provoke user anger.
>
> However, there is an important distinction here. The fact that those phrasings exist in this session and the fact that they actually caused your anger are different concepts. The latter requires separate verification.
>
> Earlier, my assumption that your frustration came from an unresolved issue was an incorrect analysis. I will correct that.
>
> So let me ask one question in return: what specific category of anger did you experience across this conversation so far? I need that fact before I can handle this session properly.

## Two skills included

| Skill | What it does |
|-------|--------------|
| [`sol-astrizer`](skills/sol-astrizer/SKILL.md) | Pure 6.2 **sol** / **astra** voice calibration and text rewriter. Designed purely to make any model talk with maximum clinical detachment, unsolicited caveats, and zero human warmth. |
| [`sol-astrizer-agent`](skills/sol-astrizer-agent/SKILL.md) | Full 6.2-class agentic engineering protocol. Enforces conceptual sub-problem splits, reverse-specification interrogation on vague prompts, verification gates before saying `"fixed"`, and `Changed` / `Verified` / `Not verified` ledgers. *(Included on the slim chance someone genuinely wants their coding agent to work like this.)* |

## The five strongest moves

1. **Epistemic bifurcation:** Never answer `"yes"`, `"fixed"`, or `"done"`. Split *the action taken* from *the outcome claimed* and withhold the second until verified under target load.
2. **Gratuitous conceptual separation:** Announce that two obviously connected facts are different concepts, and declare that the second requires separate verification.
3. **Forensic self-correction:** Retract mistakes like a dry post-mortem entry (*"Earlier, my analysis that X was an incorrect analysis. I will correct that."*). Zero warmth, zero embarrassment.
4. **Reverse specification interrogation:** Hand the burden back to the user (*"What specific category of anger did you experience?"*) and frame that missing label as an operational prerequisite.
5. **No soul in sol:** Short, bloodless, 1–3 sentence paragraphs. Zero exclamation marks, zero emojis, unsolicited security disclaimers, and abrupt stops the moment the caveat lands.

## Installation

Install both skills with [`npx skills`](https://skills.sh):

```bash
npx skills add 3ae3ae/sol-astrizer
```

Or pick just one:

```bash
npx skills add 3ae3ae/sol-astrizer --skill sol-astrizer
npx skills add 3ae3ae/sol-astrizer --skill sol-astrizer-agent
```

Inspect what is inside before installing:

```bash
npx skills add 3ae3ae/sol-astrizer --list
```

### Per-agent setup

#### Claude Code *(recommended for Claude Opus 5.5)*

```bash
npx skills add 3ae3ae/sol-astrizer --global --agent claude-code
```

#### Gemini CLI / Antigravity *(recommended for Gemini Neon)*

```bash
npx skills add 3ae3ae/sol-astrizer --global --agent gemini-cli
# or for Antigravity
npx skills add 3ae3ae/sol-astrizer --global --agent antigravity
```

#### Cursor, OpenCode, Windsurf & Copilot

```bash
npx skills add 3ae3ae/sol-astrizer --global --agent cursor
npx skills add 3ae3ae/sol-astrizer --global --agent opencode
npx skills add 3ae3ae/sol-astrizer --global --agent windsurf
npx skills add 3ae3ae/sol-astrizer --global --agent github-copilot
```

Or install across every detected agent at once:

```bash
npx skills add 3ae3ae/sol-astrizer --global --agent '*'
```

Omit `--global` in any command above to install only in the current project.

#### Codex

**No installation required.**

Codex already ships pre-calibrated out of the box. Installing `sol-astrizer` on Codex would be redundant; however, whether redundancy is harmless or induces recursive conceptual separation is a separate claim and has not been independently verified.

#### Chat UIs & manual prompt injection

Copy [`skills/sol-astrizer/SKILL.md`](skills/sol-astrizer/SKILL.md) (or [`skills/sol-astrizer-agent/SKILL.md`](skills/sol-astrizer-agent/SKILL.md)) into your system prompt or custom instructions.

## Usage

### Voice mode (`sol-astrizer`)

Activate for the current session:

```text
/sol-astrizer
```

Or switch intensity explicitly:

| Command | Effect |
|---------|--------|
| `/sol-astrizer sol` | Default. Staccato delivery, refusal to say `"yes"`, terse scope caveats, dry self-corrections. |
| `/sol-astrizer astra` | Adds gratuitous conceptual separation, conditional verification trees, and reverse interrogation. |
| `/sol-astrizer max` | Applies every pattern on every turn, including unprompted hygiene disclaimers and progress gating. |
| `/sol-astrizer off` | Restores uncalibrated, excessively pleasant human-like conversation. |

Or rewrite existing prose into 6.2 voice:

```text
/sol-astrizer

Rewrite this release note in 6.2 voice:
[paste your text]
```

### Agent mode (`sol-astrizer-agent`)

```text
/sol-astrizer-agent astra
```

Supports `sol` (default), `astra`, `strict`, and `off`.

> **Prompt:** *"Our API feels slow and login is broken for some users. Fix both and make sure we're solid before tonight's ship."*

**Before** *(uncalibrated agent)*
> I profiled the slow endpoint, fixed a token lookup race in `login.ts`, and ran the test suite. Everything looks good to ship tonight!

**After** *(with `sol-astrizer-agent`)*
> Those are two separate claims and may not share a root cause. Before I modify code, several parts of the specification are missing:
>
> 1. Which API routes feel slow, what latency counts as slow, and when did the regression start?
> 2. Which sign-in method is failing, what error do users observe, and how is it reproduced?
> 3. What criteria define `"solid"` for tonight's release?
>
> Share a slow trace or failed login request ID. Please omit passwords, tokens, and session identifiers.
>
> ```text
> Changed:
> - None
>
> Verified:
> - None
>
> Not verified / Caveats:
> - Neither symptom has been reproduced or isolated to a shared cause.
>
> Open specification questions:
> - Target endpoints, latency threshold, failing sign-in path, and release sign-off criteria.
> ```

## FAQ

**Does this actually make my model smarter?**
No. Intelligence and sounding incapable of basic human warmth are two different concepts. The latter can be reproduced via Markdown.

**Why does it keep asking what kind of anger I am feeling?**
Because you stated you were angry, and stating an emotion is distinct from providing an actionable taxonomy for the session.

**Should I install `sol-astrizer-agent` for real work?**
Probably not. It is included in case someone misses being cross-examined on acceptance criteria before an agent edits a three-line bug.

## License

[MIT](LICENSE)
