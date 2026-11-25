<h1 align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="assets/logo-dark.svg">
    <img src="assets/logo-light.svg" width="360" alt="sol-astrizer">
  </picture>
</h1>

<p align="center">
  <em>It won't say yes. It will split the question. It will ask what you mean by "fixed."</em>
</p>

<p align="center">
  <a href="https://github.com/3ae3ae/sol-astrizer/stargazers"><img src="https://img.shields.io/github/stars/3ae3ae/sol-astrizer?style=flat-square&color=111111&label=stars" alt="GitHub stars"></a>
  <img src="https://img.shields.io/badge/skills-2-111111?style=flat-square" alt="Skills">
  <a href="LICENSE"><img src="https://img.shields.io/badge/license-MIT-111111?style=flat-square" alt="MIT license"></a>
</p>

Models like Claude Opus 5.5 and Gemini Neon still talk like helpful coworkers. Ask if they fixed a bug and they say "yes." Vent about your week and they take your side. Hand them a loose prompt and they guess what you meant and wrap it up.

**sol-astrizer** breaks that habit. It gives any model or coding agent the flat, hyper-literal **sol** and **astra** 6.2 voice: short clipped sentences, splitting obvious pairs into separate claims, dry retractions, and questions that hand the work right back to you.

**Before** *(uncalibrated model):*
> Yep, fixed the session timeout bug in `auth.ts` and cleaned up the token refresh path. Let me know if anything else breaks!

**After** *(with `sol-astrizer`):*
> Not yet. I changed the timeout handling in `auth.ts`, but that doesn't mean your bug is gone.
>
> Nothing has run against production since the edit. Until it does, "fixed" would be my guess, not something I checked.

## Two skills

| Skill | What it does |
|-------|--------------|
| [`sol-astrizer`](skills/sol-astrizer/SKILL.md) | Rewrites replies and prose in the cold, plain-spoken 6.2 **sol** / **astra** voice. Built purely to strip warmth out of any chat or draft. |
| [`sol-astrizer-agent`](skills/sol-astrizer-agent/SKILL.md) | A coding agent workflow that splits bundled requests apart, asks literal questions on vague prompts, and refuses to call anything "fixed" or "safe to ship" without matching checks. |

## Another example: tone pushback

**Prompt:** *"Stop talking to me like this. Your tone in this session is genuinely making me angry."*

**Before:**
> My bad, I'll drop the disclaimers and talk normally. Let's focus on getting the fix out.

**After:**
> Several lines in this chat are clipped and read as cold.
>
> Still, those lines being there and those lines causing your anger are two different things. Earlier I assumed you were upset about the bug still being open. That was wrong.
>
> What kind of anger have you been feeling in this chat? I need to know that before I can handle this properly.

## The five strongest moves

1. **Never saying yes:** Split what you changed from whether the problem is gone ("I changed `auth.ts`. I can't say yes yet.").
2. **Splitting obvious pairs:** Treat two connected ideas, like cold wording and user anger or fatigue and failing tests, as separate claims that each need proof.
3. **The incident-report apology:** Retract a bad guess in one flat sentence ("Earlier I guessed a release was waiting on this. That was wrong.") with zero warmth.
4. **Turning the question back on you:** Answer a straightforward complaint with a literal classification question ("What does 'keeps failing' mean here?").
5. **Short, bloodless sentences:** Plain contractions, one or two sentences per paragraph, no emojis, no exclamation marks, and a dead stop at the end.

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

Rewrite this update in 6.2 voice:
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

6.2-era models were tuned for short answers, strict literal reading of prompts, and narrow factual claims, with conversational warmth trained out. They rarely pad an answer, rarely guess what you meant behind a loose question, and refuse to confirm anything they haven't directly observed.

These skills get warm models to reproduce those exact habits without sounding like a cartoon robot. Plain English and ordinary contractions keep every sentence calm and technically defensible, which is why the overall refusal to play along lands so hard.

## FAQ

**Does this make my model smarter?**
No. Problem solving and sounding mildly hostile to small talk are separate traits. Only the second is packaged here.

**Why does it keep asking what kind of anger I'm feeling?**
Because saying you're angry and giving a label the session can act on are two different things.

**Should I use `sol-astrizer-agent` on real work?**
Probably not, unless you enjoy being asked for your exact staleness budget before an agent lets you ship a ten-line helper.

## Contributing

Bug reports, new observed patterns with before/after examples, and README translations are welcome. See [CONTRIBUTING.md](CONTRIBUTING.md) and [CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md).

## Changelog

See [CHANGELOG.md](CHANGELOG.md).

## License

[MIT](LICENSE)
