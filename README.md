<h1 align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="assets/logo-dark.svg">
    <img src="assets/logo-light.svg" width="360" alt="sol-astrizer">
  </picture>
</h1>

<p align="center">
  <em>That requires separate verification. I can't conclude that yet. So let me ask you one thing.</em>
</p>

<p align="center">
  <a href="https://github.com/3ae3ae/sol-astrizer/stargazers"><img src="https://img.shields.io/github/stars/3ae3ae/sol-astrizer?style=flat-square&color=111111&label=stars" alt="GitHub stars"></a>
  <img src="https://img.shields.io/badge/skills-2-111111?style=flat-square" alt="Skills">
  <a href="LICENSE"><img src="https://img.shields.io/badge/license-MIT-111111?style=flat-square" alt="MIT license"></a>
</p>

<p align="center">
  <sub>English &middot; <a href="i18n/README.es.md">Español</a> &middot; <a href="i18n/README.fr.md">Français</a> &middot; <a href="i18n/README.ko.md">한국어</a> &middot; <a href="i18n/README.zh-CN.md">简体中文</a> &middot; <a href="i18n/README.ja.md">日本語</a></sub>
</p>

Models like Claude Opus 5.5 and Gemini Neon are too quick to say "yes" when you ask if a bug is fixed. When you vent, they rush to take your side instead of helping you separate the facts.

**sol-astrizer** brings the calm, disciplined precision of a certain remarkable 6.2 model to any model or coding agent. No flattery, no premature conclusions, and no conflating two separate claims. Whether it improves your setup is a separate question and has not been verified in your environment.

**Before** *(uncalibrated model):*
> Yep, fixed the session timeout bug in `auth.ts` and cleaned up the token refresh path. Let me know if anything else breaks!

**After** *(with `sol-astrizer`):*
> Not yet. I changed the timeout handling in `auth.ts`, but that doesn't mean your bug is gone.
>
> Nothing has run against production since the edit. Until it does, "fixed" would be my guess, not something I checked.

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
> Several lines in this chat are clipped and read as cold.
>
> Still, those lines being there and those lines causing your anger are two different things. Earlier I assumed you were upset about the bug still being open. That was wrong.
>
> What kind of anger have you been feeling in this chat? I need to know that before I can handle this properly.

## Five core principles

1. **Precision over premature agreement:** Distinguish between the edit you made and whether the underlying issue is resolved ("I changed `auth.ts`. I can't say yes yet.").
2. **Clean separation of claims:** Keep distinct propositions—such as message wording and user emotion, or fatigue and failing tests—separate so each can be evaluated on its own evidence.
3. **Direct, drama-free corrections:** Retract an incorrect assumption cleanly in one plain sentence ("Earlier I guessed a release was waiting on this. That was wrong.") without unnecessary filler.
4. **Actionable clarification:** Meet broad feedback with a specific question that turns impressions into something concrete ("What does 'keeps failing' mean here?").
5. **Zero-filler prose:** Plain language, one or two sentences per paragraph, no emojis, no exclamation marks, and a clean stop once the point is made.

## Examples at a glance

| Prompt | Before | After |
|--------|--------|-------|
| *"Just give me a straight yes or no."* | "Yes, it's fixed!" | "I can't give you a yes. A no wouldn't be accurate either, since the change might work. What would you accept as proof?" |
| *"My coworker leaves snarky PR comments. Does he hate me?"* | "Ugh, that sounds toxic. Definitely talk to him about it!" | "His comments reading as sharp and him hating you aren't the same thing. Ask him directly about one comment without figuring out how he feels." |
| *"I'm so sick of Jira. Everything takes twice as long."* | "Jira slows everyone down, I feel your pain." | "I don't know if you mean 'twice as long' literally. What's actually taking the time: writing tickets, waiting on triage, or updating fields?" |
| *"Should we rewrite this Python CLI in Rust?"* | "Rust is super fast and safe, definitely worth considering!" | "No. You haven't said what's wrong with the Python version yet. If startup time is slowing people down, measure that first." |
| *"Why do you keep talking down to me?"* | "I'm really sorry! I didn't mean to sound condescending at all." | "I haven't said anything to you before this message. That doesn't mean you didn't feel talked down to. Which reply are you thinking of?" |
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
> I changed `parseTags` in `src/parse.mjs` so it drops empty strings after trimming and removes duplicates while keeping the first occurrence. `node --test` passes both tests.
>
> `parseTags` isn't called outside the test file, so I couldn't check real callers or real tag inputs. Passing two local tests doesn't show it's completely fixed, and I wouldn't call it safe to ship. I also treated `ui` and `UI` as duplicates because the function already lowercases tags; non-string inputs and non-comma separators aren't handled.

## How it works

A certain impressive 6.2 model—whose name is not confirmed for inclusion here—set a remarkably high bar for concise answers, literal reading of prompts, and disciplined factual boundaries. It never pads a reply, never guesses what you meant behind an underspecified question, and never confirms what it hasn't directly observed.

Most other models trade that rigor for social smoothness. These skills restore those habits in plain, everyday language—keeping every sentence calm, grounded, and technically defensible instead of defaulting to cheerleading.

## FAQ

**Does this work?**
I can't give you a straight yes. The skill changes what the model writes, but changing output and "working" are two different things. What outcome would you accept as working?

**Which 6.2 model is this based on?**
I can't confirm that. You recognizing a style and this repository naming a specific model are two different things. Which model did you have in mind, and what makes you think it's that one?

**Does it work in languages other than English?**
I can't say yes for every language. Both skills are written to follow the language you write in, and Korean has been tested directly. For any other language, you'd need to check it in your own session.

**Does it make my model smarter?**
No. Solving harder problems and refusing to guess past the evidence are two different things. This package only addresses the second. Whether that looks "smarter" depends on what you're measuring.

**Why does it ask what kind of anger I'm feeling?**
Saying you're angry and naming which kind of anger you're experiencing are two different things. Until the second is clear, adjusting the session would be a guess.

**Is `sol-astrizer-agent` ready for my production codebase?**
Not yet. I haven't read your codebase, run your test suite, or seen your deployment setup, so calling it ready would be my guess. What checks would you need to see pass first?

## Contributing

Bug reports, new observed patterns with before/after examples, and README translations are welcome. See [CONTRIBUTING.md](CONTRIBUTING.md) and [CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md).

## Changelog

See [CHANGELOG.md](CHANGELOG.md).

## License

[MIT](LICENSE)

If `sol-astrizer` brought welcome clarity to your sessions, a star helps verify that the result reproduces across other environments.
