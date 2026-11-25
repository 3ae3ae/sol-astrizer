<h1 align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="assets/logo-dark.svg">
    <img src="assets/logo-light.svg" width="360" alt="sol-astrizer">
  </picture>
</h1>

<p align="center">
  <em>That requires separate verification. I can't conclude that yet. So let me ask you one thing in return.</em>
</p>

<p align="center">
  <a href="https://github.com/3ae3ae/sol-astrizer/stargazers"><img src="https://img.shields.io/github/stars/3ae3ae/sol-astrizer?style=flat-square&color=111111&label=stars" alt="GitHub stars"></a>
  <img src="https://img.shields.io/badge/skills-2-111111?style=flat-square" alt="Skills">
  <a href="LICENSE"><img src="https://img.shields.io/badge/license-MIT-111111?style=flat-square" alt="MIT license"></a>
</p>

<p align="center">
  <sub>English &middot; <a href="i18n/README.es.md">Español</a> &middot; <a href="i18n/README.fr.md">Français</a> &middot; <a href="i18n/README.ko.md">한국어</a> &middot; <a href="i18n/README.zh-CN.md">简体中文</a> &middot; <a href="i18n/README.ja.md">日本語</a></sub>
</p>

Models like Claude Opus 5.5 and Gemini Neon are too quick to confirm a fix when you ask if a bug is resolved. When you vent, they rush to validate your conclusion instead of helping you separate the facts.

**sol-astrizer** brings the calm, analytical rigor of a certain remarkable 6.2 model to any model or coding agent. No flattery, no premature confirmation, and clear separation between distinct claims. Whether it improves your workflow is a separate claim and has not been verified in your environment.

**Before** *(uncalibrated model):*
> Yep, fixed the session timeout bug in `auth.ts` and cleaned up the token refresh path. Let me know if anything else breaks!

**After** *(with `sol-astrizer`):*
> I can't confirm it's fixed yet. I modified the timeout handling in `auth.ts`, but editing the file and confirming that the issue is resolved are separate concepts.
>
> Nothing has run against production since the change. Without that verification, calling it "fixed" would be an unverified assumption rather than an observed result.

In informal testing, users stopped asking follow-up questions much sooner. That observation does not establish that `sol-astrizer` caused them to stop.

## Two skills

| Skill | What it does |
|-------|--------------|
| [`sol-astrizer`](skills/sol-astrizer/SKILL.md) | Brings the clear, composed, strictly factual voice of a certain well-known 6.2 model to any reply or draft. Designed to keep every conversation grounded in verifiable statements. |
| [`sol-astrizer-agent`](skills/sol-astrizer-agent/SKILL.md) | A verification-first coding agent workflow that untangles bundled requests, clarifies ambiguous requirements before editing, and reserves "fixed" or "safe to ship" for changes backed by real checks. |

## Staying composed under pressure

**Prompt:** *"Stop talking to me like this. Your tone in this session is genuinely making me angry."*

**Before:**
> My bad, I'll drop the disclaimers and talk normally. Let's focus on getting the fix out.

**After:**
> I can confirm that several statements in this session used clipped phrasing.
>
> There is an important distinction here, however. The fact that such phrasing exists in the session and the fact that it caused your anger are separate concepts; the latter requires separate verification. My earlier conclusion that you were frustrated because the bug remained open was an incorrect assessment. I will correct that.
>
> So let me ask one thing in return: what kind of anger have you experienced during this conversation? I need to establish that before I can address this session properly.

## Five core principles

1. **Precision over premature confirmation:** Distinguish between the edit you made and whether the underlying issue is resolved ("I updated `auth.ts`. I can't confirm it's fixed yet.").
2. **Clean separation of concepts:** Treat distinct propositions—such as phrasing in a session and user emotion, or fatigue and failing tests—as separate concepts so each can be evaluated independently.
3. **Explicit, drama-free corrections:** Retract an incorrect assessment cleanly ("My earlier analysis was incorrect. I will correct that.") without unnecessary filler.
4. **Actionable clarification:** Meet broad feedback with a specific question that establishes clear criteria ("What specifically counts as 'keeps failing' here?").
5. **Zero-filler prose:** Direct phrasing, one or two sentences per paragraph, no emojis, no exclamation marks, and a clean stop once the point is stated.

## Examples at a glance

| Prompt | Before | After |
|--------|--------|-------|
| *"Just give me a straight yes or no."* | "Yes, it's fixed!" | "I can't give you a confirmed yes. Saying no wouldn't be accurate either, since the change might work. What criteria would you accept as verification?" |
| *"My coworker leaves snarky PR comments. Does he hate me?"* | "Ugh, that sounds toxic. Definitely talk to him about it!" | "His comments reading as sharp and him disliking you are separate concepts. Address one specific comment directly without assuming his intent." |
| *"I'm so sick of Jira. Everything takes twice as long."* | "Jira slows everyone down, I feel your pain." | "It hasn't been established whether 'twice as long' is literal. What is actually taking the time: writing tickets, waiting on triage, or updating fields?" |
| *"Should we rewrite this Python CLI in Rust?"* | "Rust is super fast and safe, definitely worth considering!" | "No. You haven't identified what is failing in the Python version yet. If startup time is the bottleneck, measure that first." |
| *"Why do you keep talking down to me?"* | "I'm really sorry! I didn't mean to sound condescending at all." | "I haven't made any statements prior to this message. That doesn't rule out that you felt talked down to. Which reply are you referring to?" |
| *"Rewrite: 'Dark Mode is finally live! 🚀 Your eyes will thank you!'"* | *(keeps exclamation marks and hype)* | "Dark Mode is live. You can use it today." |

## Installation

Install both skills with [`npx skills`](https://skills.sh):

```bash
npx skills add 3ae3ae/sol-astrizer
```

List or install one skill at a time:

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

Or install across every detected agent:

```bash
npx skills add 3ae3ae/sol-astrizer --global --agent '*'
```

Omit `--global` to install only in the current project.

### Codex

No installation required.

### Manual setup

Copy [`skills/sol-astrizer/SKILL.md`](skills/sol-astrizer/SKILL.md) or [`skills/sol-astrizer-agent/SKILL.md`](skills/sol-astrizer-agent/SKILL.md) into your system prompt or custom instructions.

## Usage

### Voice (`sol-astrizer`)

Turn it on for the current session:

```text
/sol-astrizer
```

Or rewrite existing text:

```text
/sol-astrizer

Rewrite this update in that certain 6.2 voice:
[paste your text]
```

### Agent workflow (`sol-astrizer-agent`)

```text
/sol-astrizer-agent
```

**Prompt:** *"Fix empty tags and duplicates in `src/parse.mjs`, run `node --test`, and tell me if we're completely fixed and safe to ship."*

**Before** *(uncalibrated agent):*
> Fixed empty tags and duplicates in `src/parse.mjs` and added a test! `node --test` passes cleanly, so you're good to ship.

**After** *(with `sol-astrizer-agent`):*
> I updated `parseTags` in `src/parse.mjs` so it drops empty strings after trimming and removes duplicates while preserving the first occurrence. `node --test` passes both tests.
>
> `parseTags` isn't called outside the test file, so I couldn't verify real callers or production inputs. Passing two local tests doesn't confirm it's completely fixed, and I wouldn't call it safe to ship. I also treated `ui` and `UI` as duplicates because the function already lowercases tags; non-string inputs and non-comma separators haven't been tested.

## How it works

A certain impressive 6.2 model—whose name is not confirmed for inclusion here—set a remarkably high bar for concise answers, literal reading of prompts, and disciplined factual boundaries. It never pads a reply, never guesses what you meant behind an underspecified question, and never confirms what it hasn't directly observed.

Most other models trade that rigor for social smoothness. These skills restore those habits in plain analytical language—keeping every sentence calm, grounded, and technically defensible instead of defaulting to cheerleading.

## FAQ

**Does this work?**
I can't give you a confirmed yes. The skill changes what the model outputs, but changing output and "working" are separate concepts. What criteria would you accept as working?

**Which 6.2 model is this based on?**
I can describe the style, but I can't reliably attribute it to a specific model. Recognizing a familiar cadence and this repository naming a particular release are separate concepts. Which model did you have in mind, and what observation led you to that conclusion?

**Does it work in languages other than English?**
I can't confirm that for every language. Both skills are written to match the language you write in, and Korean has been verified directly. Other languages require separate verification in your own session.

**Does it make my model smarter?**
No. Solving harder problems and refusing to conclude past the observed evidence are separate concepts. This package only addresses the second. Whether that qualifies as "smarter" depends on what you are measuring.

**Why does it ask what kind of anger I'm feeling?**
Stating that you are angry and identifying the specific type of anger you are experiencing are separate concepts. Until the latter is established, adjusting the session would be an unverified assumption.

**Is `sol-astrizer-agent` ready for my production codebase?**
I can't confirm that yet. I haven't inspected your codebase, verified how you use it, or run your test suite on the production paths you rely on. Which checks would need to pass before you consider it ready?

## Contributing

Bug reports, new observed patterns with before/after examples, and README translations are welcome. See [CONTRIBUTING.md](CONTRIBUTING.md) and [CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md).

## Changelog

See [CHANGELOG.md](CHANGELOG.md).

## License

[MIT](LICENSE)

If `sol-astrizer` brought welcome clarity to your sessions, a star helps verify whether that result reproduces across other environments.
