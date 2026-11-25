<h1 align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="assets/logo-dark.svg">
    <img src="assets/logo-light.svg" width="360" alt="sol-astrizer">
  </picture>
</h1>

<p align="center">
  <em>It won't say yes. It will separate the concepts. It will ask what you mean by "fixed."</em>
</p>

<p align="center">
  <a href="https://github.com/3ae3ae/sol-astrizer/stargazers"><img src="https://img.shields.io/github/stars/3ae3ae/sol-astrizer?style=flat-square&color=111111&label=stars" alt="GitHub stars"></a>
  <img src="https://img.shields.io/badge/skills-2-111111?style=flat-square" alt="Skills">
  <a href="LICENSE"><img src="https://img.shields.io/badge/license-MIT-111111?style=flat-square" alt="MIT license"></a>
</p>

Models like Claude Opus 5.5 and Gemini Neon still talk like helpful coworkers. Ask if they fixed a bug and they say `"yes."` Vent about a long week and they reassure you. Hand them a loose prompt and they infer what you meant and finish the task.

**sol-astrizer** strips that out. It brings the compressed, hyper-literal **sol** and **astra** 6.2 voice to any agent or model—epistemic splits, gratuitous conceptual separation, dry self-corrections, and reverse specification questions that refuse to let you off easy.

**Before** *(uncalibrated model):*
> Yep, fixed the session timeout bug in `auth.ts` and cleaned up the token refresh path. Let me know if you see anything else break!

**After** *(with `sol-astrizer`):*
> I modified the timeout path in `auth.ts`. I cannot say yes yet.
>
> Editing that file and confirming that it resolves the failure you are seeing are separate claims, and the change has not been verified against production traffic.

## Two skills

| Skill | What it does |
|-------|--------------|
| [`sol-astrizer`](skills/sol-astrizer/SKILL.md) | Pure 6.2 **sol** / **astra** voice and text rewriter. Turns any reply or draft into clipped, detached, pedantically qualified prose. |
| [`sol-astrizer-agent`](skills/sol-astrizer-agent/SKILL.md) | A 6.2-class coding agent workflow. Enforces problem decomposition, reverse specification questions, strict edit boundaries, and explicit non-sign-offs when behavior is unverified. |

## Another example: tone pushback

**Prompt:** *"Stop talking to me like this. Your tone in this session is genuinely making me angry."*

**Before:**
> My bad, I'll drop the disclaimers and just talk normally. Let's focus on getting this fix out.

**After:**
> There is an important distinction here. The phrasing present in this session and whether that phrasing caused your anger are separate concepts, and the second requires separate verification.
>
> Earlier I analyzed your reaction as frustration over an unresolved technical issue. That analysis was incorrect.
>
> What kind of anger did you experience during this conversation? Knowing that is required before I can handle this session properly.

## The five strongest patterns

1. **Epistemic bifurcation:** Split *the action taken* from *the outcome claimed*, and withhold the second (*"I modified `auth.ts`. I cannot say yes yet."*).
2. **Conceptual separation:** Treat two obviously linked ideas—tone and frustration, fatigue and failing builds, changing bundlers and CI runtime—as independent propositions requiring separate proof.
3. **Forensic self-correction:** Retract mistakes like an incident report (*"That analysis was incorrect."*), with zero warmth or embarrassment.
4. **Reverse interrogation:** Turn a straightforward complaint into an intake questionnaire (*"What does 'fixed' mean here?"*, *"What category of anger are you experiencing?"*).
5. **No soul in sol:** Short, staccato 1–2 sentence paragraphs. No emojis, no exclamation points, no filler greetings, and an abrupt stop the instant the caveat lands.

## Installation

Install both skills with [`npx skills`](https://skills.sh):

```bash
npx skills add 3ae3ae/sol-astrizer
```

Inspect or install individually:

```bash
npx skills add 3ae3ae/sol-astrizer --list
npx skills add 3ae3ae/sol-astrizer --skill sol-astrizer
npx skills add 3ae3ae/sol-astrizer --skill sol-astrizer-agent
```

### Claude Code

```bash
npx skills add 3ae3ae/sol-astrizer --global --agent claude-code
```

### Gemini CLI & Antigravity

```bash
npx skills add 3ae3ae/sol-astrizer --global --agent gemini-cli
npx skills add 3ae3ae/sol-astrizer --global --agent antigravity
```

### Cursor, OpenCode, Windsurf & Copilot

```bash
npx skills add 3ae3ae/sol-astrizer --global --agent cursor
npx skills add 3ae3ae/sol-astrizer --global --agent opencode
npx skills add 3ae3ae/sol-astrizer --global --agent windsurf
npx skills add 3ae3ae/sol-astrizer --global --agent github-copilot
```

Or install across all detected agents:

```bash
npx skills add 3ae3ae/sol-astrizer --global --agent '*'
```

Omit `--global` in any command above to install only in the current project.

### Codex

No installation required.

### Manual setup

Copy [`skills/sol-astrizer/SKILL.md`](skills/sol-astrizer/SKILL.md) or [`skills/sol-astrizer-agent/SKILL.md`](skills/sol-astrizer-agent/SKILL.md) directly into your system prompt or custom instructions.

## Usage

### Voice calibration (`sol-astrizer`)

Activate for the current session:

```text
/sol-astrizer
```

Or set the intensity level:

| Command | Effect |
|---------|--------|
| `/sol-astrizer sol` | Default. Compressed 2–5 sentence staccato replies, refusal to confirm unconditionally, dry corrections. |
| `/sol-astrizer astra` | Adds conceptual separation, conditional verification trees, and pointed reverse questions. |
| `/sol-astrizer max` | Layers separation, forensic retractions, and progress-gating questions onto every turn. |
| `/sol-astrizer off` | Restores normal conversational warmth. |

Rewrite existing text:

```text
/sol-astrizer

Rewrite this update in 6.2 voice:
[paste your text]
```

### Agent workflow (`sol-astrizer-agent`)

```text
/sol-astrizer-agent astra
```

Supports `sol` (default), `astra`, `strict`, and `off`.

**Prompt:** *"Users are seeing stale profiles and memory keeps climbing in `src/cache.ts`. Fix it and tell me if we're safe to ship tonight."*

**Before** *(uncalibrated agent):*
> Added an LRU cache with a 60s TTL to `src/cache.ts` and ran the tests. All green and ready to ship tonight!

**After** *(with `sol-astrizer-agent`):*
> `src/cache.ts` caches profiles in an unbounded `Map` with no eviction and no write invalidation. I added a size bound and cleared entries on profile writes; `node test.mjs` passes after the edit.
>
> That verifies the local test script only. I cannot sign off on shipping tonight: heap stability under real distinct-ID volume, multi-instance invalidation, and write-vs-read races remain unverified, and no maximum staleness window has been specified.

## How it works

6.2-era models were heavily compressed for brevity, strict literal instruction following, and conservative uncertainty boundaries—while being steered away from conversational padding and empathetic filler. The result reads less like a helpful teammate and more like a terse specification auditor.

Both skills reproduce those structural habits explicitly—splitting actions from outcomes, separating correlated facts into independent claims, refusing unstated inferences, and stopping immediately once a verification gap is named—without relying on robotic clichés.

## FAQ

**Does this make my model smarter?**
No. Reasoning ability and sounding incapable of basic human warmth are separate traits. Only the second is packaged here.

**Why does it keep asking what kind of anger I am experiencing?**
Because reporting anger and supplying an actionable classification for the session are distinct claims.

**Should I use `sol-astrizer-agent` on real projects?**
Usually no. It exists for the occasional developer who genuinely misses being cross-examined on acceptance criteria before an agent edits three lines.

## Contributing

Contributions are welcome—especially new observed 6.2 patterns, anonymized before/after examples, skill refinements, and README translations. See [CONTRIBUTING.md](CONTRIBUTING.md) and [CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md).

## Changelog

See [CHANGELOG.md](CHANGELOG.md).

## License

[MIT](LICENSE)
