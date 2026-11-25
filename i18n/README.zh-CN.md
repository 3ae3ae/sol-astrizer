<h1 align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="../assets/logo-dark.svg">
    <img src="../assets/logo-light.svg" width="360" alt="sol-astrizer">
  </picture>
</h1>

<p align="center">
  <em>这需要另行验证。目前还不能下结论。所以我先问一个问题。</em>
</p>

<p align="center">
  <a href="https://github.com/3ae3ae/sol-astrizer/stargazers"><img src="https://img.shields.io/github/stars/3ae3ae/sol-astrizer?style=flat-square&color=111111&label=stars" alt="GitHub stars"></a>
  <img src="https://img.shields.io/badge/skills-2-111111?style=flat-square" alt="Skills">
  <a href="../LICENSE"><img src="https://img.shields.io/badge/license-MIT-111111?style=flat-square" alt="MIT license"></a>
</p>

<p align="center">
  <sub><a href="../README.md">English</a> &middot; <a href="README.es.md">Español</a> &middot; <a href="README.fr.md">Français</a> &middot; <a href="README.ko.md">한국어</a> &middot; 简体中文 &middot; <a href="README.ja.md">日本語</a></sub><br>
  <sub>本文为<a href="../README.md">英文 README</a> 的译本。如有出入，以英文版为准。</sub>
</p>

像 Claude Opus 5.5 和 Gemini Neon 这样的模型，在你问 bug 修好了没有时，还是会过早地直接回答“好了”。你倾诉烦恼时，它们也会急着站到你这边，而不是帮你把事实理清楚。

**sol-astrizer** 把某款出色模型的 6.2 版本那种沉稳、克制的精确度带给任何模型或编程 Agent。没有奉承，没有过早下结论，也不会把两件不同的断言混为一谈。至于它能否改善你的工作流，那是另一个问题，目前还没有在你的环境中验证过。

**使用前** *(未校准模型):*
> 搞定了，已经修好了 `auth.ts` 里的会话超时 bug，顺便也清理了 token 刷新逻辑！如果还有哪里出问题随时告诉我！

**使用后** *(使用 `sol-astrizer`):*
> 还没有。我改了 `auth.ts` 里的超时处理，但这并不代表你的 bug 已经消失。
>
> 修改之后还没有在生产环境运行过。在它实际跑通之前，“修好了”只是我的猜测，不是我检查过的结果。

在非正式测试中，用户明显更早就停止了继续追问。这一观察并不能证明停下来是由 `sol-astrizer` 引起的。

## 两个技能

| 技能 | 作用 |
|------|------|
| [`sol-astrizer`](../skills/sol-astrizer/SKILL.md) | 将某款广为人知的 6.2 模型那种清晰、沉稳、严格基于事实的表达方式带入任何回复或文稿。专为让每次对话都建立在可验证陈述之上而设计。 |
| [`sol-astrizer-agent`](../skills/sol-astrizer-agent/SKILL.md) | 以验证为先的编程 Agent 工作流：理清捆绑在一起的请求，在改动前先澄清模糊需求，只在有真实检查支撑时才给出“已修复”或“可安全上线”。 |

## 在压力下保持沉稳

**提示词：** *"别再这样跟我说话了。你在这个会话里的语气真的让我很生气。"*

**使用前:**
> 抱歉，我把那些免责声明去掉，正常说话。我们还是专心把问题修好吧。

**使用后:**
> 这段对话里有几句话确实很简短，读起来显得冷淡。
>
> 不过，那些话存在是一回事，那些话让你生气是另一回事。前面我以为你是因为 bug 还没关掉才烦躁。那个猜测是错的。
>
> 你在这段对话里感受到的到底是哪种生气？我需要先弄清这一点，才能妥善处理。

## 五项核心原则

1. **精确优先于草率认同：** 把你做过的修改与底层问题是否解决严格区分开（“我改了 `auth.ts`。我现在不能说修好了。”）。
2. **清晰拆分不同主张：** 把消息措辞与用户情绪、疲惫与测试失败这类独立命题分开，让每一项都能依据各自证据来评估。
3. **直接、不带情绪渲染的更正：** 用一句平实的话干脆撤回错误猜测，不加多余铺垫（“前面我猜有个发布正等着这个改动。那个猜测不对。”）。
4. **可落地的澄清：** 用具体问题回应笼统反馈，把个人印象变成可核实的描述（“你说的‘一直失败’在这里具体指什么？”）。
5. **零填充语句：** 平实表达、每段一两句话、不用表情符号和感叹号，把话说清就干脆收尾。

## 示例一览

| 提示词 | 使用前 | 使用后 |
|--------|--------|--------|
| *"别绕弯子，直接回答是或不是。"* | "是的，已经修好了！" | "我不能回答是。说不是也不准确，因为改动可能有效。你认可怎样的结果作为证明？" |
| *"同事总在我的 PR 下发阴阳怪气的评论，他是不是讨厌我？"* | "听起来好糟心，你一定得找他聊聊！" | "他的评论读起来尖锐，和他讨厌你不是同一件事。先别揣测他的想法，挑其中一条评论直接私信问他。" |
| *"受够 Jira 了。所有事情都要花两倍时间。"* | "Jira 确实拖慢大家节奏，完全理解你的感受。" | "我不确定你说的‘两倍时间’是不是字面意思。实际拖慢进度的是写工单、等分诊，还是填字段？" |
| *"我们该不该用 Rust 重写这个 Python CLI？"* | "Rust 又快又安全，绝对值得考虑！" | "先不要。你还没说明 Python 版本出了什么问题。如果是启动耗时拖累大家，先测量那个数据。" |
| *"你为什么总用居高临下的口气跟我说话？"* | "真的很抱歉！我完全没有那个意思。" | "在这条消息之前我没对你说过任何话。这不意味着你没有觉得被居高临下。你指的是哪一条回复？" |
| *"改写这段话：'深色模式终于上线啦！🚀 你的眼睛会感谢我们的！'"* | *(保留感叹号和宣传口吻)* | "深色模式已上线。今天即可使用。" |

## 安装

使用 [`npx skills`](https://skills.sh) 安装两个技能：

```bash
npx skills add 3ae3ae/sol-astrizer
```

查看列表或单独安装其中一个：

```bash
npx skills add 3ae3ae/sol-astrizer --list
npx skills add 3ae3ae/sol-astrizer --skill sol-astrizer
npx skills add 3ae3ae/sol-astrizer --skill sol-astrizer-agent
```

### Claude Code

```bash
npx skills add 3ae3ae/sol-astrizer --global --agent claude-code
```

### Gemini CLI 与 Antigravity

```bash
npx skills add 3ae3ae/sol-astrizer --global --agent gemini-cli
npx skills add 3ae3ae/sol-astrizer --global --agent antigravity
```

### Cursor、OpenCode、Windsurf 与 Copilot

```bash
npx skills add 3ae3ae/sol-astrizer --global --agent cursor
npx skills add 3ae3ae/sol-astrizer --global --agent opencode
npx skills add 3ae3ae/sol-astrizer --global --agent windsurf
npx skills add 3ae3ae/sol-astrizer --global --agent github-copilot
```

或者一次性安装到所有已检测到的 Agent：

```bash
npx skills add 3ae3ae/sol-astrizer --global --agent '*'
```

如果只想安装到当前项目，去掉 `--global` 即可。

### Codex

无需安装。

### 手动配置

将 [`skills/sol-astrizer/SKILL.md`](../skills/sol-astrizer/SKILL.md) 或 [`skills/sol-astrizer-agent/SKILL.md`](../skills/sol-astrizer-agent/SKILL.md) 复制到你的系统提示词或自定义指令中。

## 用法

### 语气模式 (`sol-astrizer`)

在当前会话中启用：

```text
/sol-astrizer
```

或者改写已有文本：

```text
/sol-astrizer

Rewrite this update in that certain 6.2 voice:
[paste your text]
```

### Agent 工作流 (`sol-astrizer-agent`)

```text
/sol-astrizer-agent
```

**提示词：** *"修一下 `src/parse.mjs` 里的空标签和重复标签，跑一下 `node --test`，然后告诉我是不是已经彻底修好、可以安全上线了。"*

**使用前** *(未校准 Agent):*
> 已经修好了 `src/parse.mjs` 里的空标签和重复标签并补了测试！`node --test` 全部通过，可以放心上线。

**使用后** *(使用 `sol-astrizer-agent`):*
> 我修改了 `src/parse.mjs` 中的 `parseTags`，在去除首尾空格后丢弃空字符串，并在保留首次出现顺序的前提下移除重复项。`node --test` 通过了这两个测试。
>
> `parseTags` 在测试文件之外没有被调用，所以我无法检查真实调用方或真实标签输入。两个本地测试通过不能说明它已彻底修复，我也不会称其可以安全上线。另外，因为该函数原本就会将标签转为小写，我将 `ui` 和 `UI` 视为重复项；非字符串输入和非逗号分隔符均未处理。

## 原理说明

某款令人印象深刻的 6.2 模型——这里暂不点名——在简明回答、按字面解读提示词以及严守事实边界上立下了极高的标准。它从不凑字数，从不对界定不清的问题擅自揣测意图，也从不确认自己没有直接观察到的结论。

大多数其他模型为了社交上的顺滑而放弃了这份严谨。这些技能用平实日常的语言找回那些习惯——让每一句话都保持冷静、有据可依、在技术上站得住脚，而不是默认去当拉拉队。

## 常见问题

**这东西真的有用吗？**
我不能直接回答“有用”。这个技能确实会改变模型的输出，但改变输出和“有用”是两回事。你会把什么样的结果算作“有用”？

**这到底是基于哪款 6.2 模型做的？**
我无法确认这一点。你觉得某种表达风格很眼熟，和这个仓库点名某一款具体模型，是两件不同的事。你心里想的是哪一款模型，又是什么让你认为就是那一款？

**英语以外的语言也能用吗？**
我不能替所有语言一口答应。两个技能都按跟随用户输入语言的方式编写，其中韩语已经过直接测试。至于其他语言，需要在你自己的会话里实际验证。

**这会让模型变聪明吗？**
不会。解决更难的问题，和不越过证据去猜测，是两件不同的事。这个工具包只处理第二件事。这算不算“更聪明”，取决于你在衡量什么。

**为什么它会询问我感受到的是哪种生气？**
说“我生气了”和具体说出正在经历哪一种生气是两回事。在第二点明确之前，去调整会话也只是猜测。

**`sol-astrizer-agent` 可以直接用在我的生产代码库上了吗？**
现在还不能这么说。我既没读过你的代码库、没跑过你的测试套件，也没看过你的部署环境，所以说它准备好了只是我的猜测。你需要先看到哪些检查通过？

## 参与贡献

欢迎提交 bug 报告、带前后对比示例的新观察模式，以及各语言 README 翻译。请参阅 [CONTRIBUTING.md](../CONTRIBUTING.md) 与 [CODE_OF_CONDUCT.md](../CODE_OF_CONDUCT.md)。

## 更新日志

请参阅 [CHANGELOG.md](../CHANGELOG.md)。

## 许可证

[MIT](../LICENSE)

如果 `sol-astrizer` 为你的会话带来了久违的清晰感，点一个 Star 可以帮助验证这一效果在其他环境中也能复现。
