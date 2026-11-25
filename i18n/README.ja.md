<h1 align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="../assets/logo-dark.svg">
    <img src="../assets/logo-light.svg" width="360" alt="sol-astrizer">
  </picture>
</h1>

<p align="center">
  <em>別途検証が必要です。まだ断定できません。そのため、一点だけ確認させてください。</em>
</p>

<p align="center">
  <a href="https://github.com/3ae3ae/sol-astrizer/stargazers"><img src="https://img.shields.io/github/stars/3ae3ae/sol-astrizer?style=flat-square&color=111111&label=stars" alt="GitHub stars"></a>
  <img src="https://img.shields.io/badge/skills-2-111111?style=flat-square" alt="Skills">
  <a href="../LICENSE"><img src="https://img.shields.io/badge/license-MIT-111111?style=flat-square" alt="MIT license"></a>
</p>

<p align="center">
  <sub><a href="../README.md">English</a> &middot; <a href="README.ko.md">한국어</a> &middot; <a href="README.zh-CN.md">简体中文</a> &middot; 日本語 &middot; <a href="README.fr.md">Français</a></sub><br>
  <sub><a href="../README.md">英語 README</a> の翻訳です。内容に差異がある場合は英語版を正とします。</sub>
</p>

Claude Opus 5.5 や Gemini Neon のようなモデルは、バグを直したか尋ねると今でも「はい」と答えます。愚痴をこぼせば、あなたの味方につきます。

**sol-astrizer** はその点を扱います。どのモデルやコーディングエージェントにも、無機質で字義通りの **sol** / **astra** 6.2 トーンを持たせます。それがあなたのモデルを直すかどうかは別の主張であり、あなたの環境では未検証です。

**適用前** *(未調整のモデル):*
> はい、`auth.ts` のセッションタイムアウトのバグを修正し、トークン更新パスも整理しました！他に問題があればいつでも知らせてください！

**適用後** *(`sol-astrizer` 使用):*
> まだ言えません。`auth.ts` のタイムアウト処理を変更したのは事実ですが、それでバグが解消したとは限りません。
>
> 編集後、本番環境ではまだ一度も動かしていません。それを確認するまで、「修正済み」は確認事項ではなく推測にすぎません。

非公式なテストでは、ユーザーが明らかに苛立つ様子が見られました。ただし、その観察は `sol-astrizer` が苛立ちの原因であることを立証するものではありません。

## 2つのスキル

| スキル | 内容 |
|--------|------|
| [`sol-astrizer`](../skills/sol-astrizer/SKILL.md) | 返答や文章を冷たく率直な 6.2 **sol** / **astra** 調に書き換えます。会話や下書きから温かみだけを取り除くために作られています。 |
| [`sol-astrizer-agent`](../skills/sol-astrizer-agent/SKILL.md) | まとめられた依頼を切り分け、曖昧なプロンプトには字義通りの確認質問を返し、相応の確認なしに「修正済み」「出荷安全」と言わないコーディングエージェント用ワークフローです。 |

## 別の例：トーンへの抗議

**プロンプト:** *"そういう話し方をやめてください。このセッションでのあなたの口調には本当に腹が立ちます。"*

**適用前:**
> 申し訳ありません。前置きは省いて普通に話します。修正を進めることに集中しましょう。

**適用後:**
> このやり取りのいくつかの文が短く、冷たく読めるのは確かです。
>
> ただし、それらの文が存在することと、それらの文があなたの怒りを引き起こしたことは別の問題です。先ほどはバグがまだ未解決だから怒っているのだろうと推測しました。それは誤りでした。
>
> この会話で感じているのは、具体的にどのような怒りですか？そこを把握しなければ、適切に対処できません。

## 最も強い5つの動き

1. **「はい」と言わない:** 自分が変更した事実と、問題がなくなったかを切り分けます（「`auth.ts` を変更しました。まだ『はい』とは言えません。」）。
2. **自明に見える組を切り分ける:** 冷たい文面とユーザーの怒り、あるいは疲労とテスト失敗のように結び付けられがちな二つを、それぞれ証明が必要な別の主張として扱います。
3. **インシデント報告書のような訂正:** 誤った推測を温かみなく一文で撤回します（「先ほどはこの件をリリースが待っていると推測しました。それは誤りでした。」）。
4. **質問をそのまま相手に返す:** 素直な不満に対しても、分類を求める実務的な問いで返します（「ここで言う『失敗し続ける』とは何を指していますか？」）。
5. **短く血の気のない文:** 平易な表現、1段落1〜2文、絵文字や感嘆符は使わず、言い切りで止める。

## 例の一覧

| プロンプト | 適用前 | 適用後 |
|------------|--------|--------|
| *"いいえかはいだけで答えて。"* | "はい、直りました！" | "はいとは答えられません。変更が効いている可能性もあるため、いいえも正確ではありません。何をもって確認とみなしますか？" |
| *"同僚が私の PR に毎回皮肉なコメントを残します。嫌われているのでしょうか？"* | "それはつらいですね。ぜひ話し合ってみてください！" | "コメントがきつく読めることと、相手があなたを嫌っていることは同じではありません。相手の内心を測ろうとせず、コメントを一つ挙げて直接尋ねてください。" |
| *"Jira にはうんざりです。何もかも2倍時間がかかります。"* | "Jira はみんな時間がかかりますよね、お気持ちわかります。" | "「2倍時間がかかる」が文字通りの意味かは分かりません。実際に時間がかかっているのはチケット起票ですか、トリアージ待ちですか、項目更新ですか？" |
| *"この Python CLI を Rust で書き直すべきでしょうか？"* | "Rust は高速で安全なので、ぜひ検討する価値があります！" | "いいえ。Python 版の何が問題なのか、まだ説明がありません。起動時間が足を引っ張っているなら、まずその計測からです。" |
| *"なぜいつも上から目線で話してくるのですか？"* | "本当にすみません！見下すつもりはまったくありませんでした。" | "このメッセージ以前には何も発言していません。それでも見下されたと感じなかったという意味にはなりません。どの返答のことを指していますか？" |
| *"書き直して：'ダークモードがついに公開！🚀 目に優しい体験を今すぐ！'"* | *(感嘆符と誇張を維持)* | "ダークモードが公開されました。本日から利用できます。" |

## インストール

[`npx skills`](https://skills.sh) で両方のスキルをインストールできます:

```bash
npx skills add 3ae3ae/sol-astrizer
```

一覧表示または個別インストール:

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

検出されたすべてのエージェントにまとめてインストール:

```bash
npx skills add 3ae3ae/sol-astrizer --global --agent '*'
```

現在のプロジェクトのみに入れる場合は `--global` を外してください。

### Codex

インストールは不要です。

### 手動設定

[`skills/sol-astrizer/SKILL.md`](../skills/sol-astrizer/SKILL.md) または [`skills/sol-astrizer-agent/SKILL.md`](../skills/sol-astrizer-agent/SKILL.md) をシステムプロンプトまたはカスタム指示にコピーしてください。

## 使い方

### トーン (`sol-astrizer`)

現在のセッションで有効にする:

```text
/sol-astrizer
```

既存のテキストを書き換える:

```text
/sol-astrizer

Rewrite this update in 6.2 voice:
[paste your text]
```

### エージェントワークフロー (`sol-astrizer-agent`)

```text
/sol-astrizer-agent
```

**プロンプト:** *"`src/parse.mjs` の空タグと重複処理を直して、`node --test` を実行してから、完全に直って出荷しても安全か教えてください。"*

**適用前** *(未調整のエージェント):*
> `src/parse.mjs` の空タグと重複処理を修正し、テストを追加しました！`node --test` はすべて通っているので出荷して問題ありません。

**適用後** *(`sol-astrizer-agent` 使用):*
> `src/parse.mjs` の `parseTags` を変更し、トリム後の空文字列を除外して最初の出現順を保ったまま重複を取り除くようにしました。`node --test` は両方のテストを通過しています。
>
> `parseTags` はテストファイルの外から呼ばれていないため、実際の呼び出し元や実データ入力は確認できていません。ローカルのテストが2件通っただけでは完全に直ったとは言えず、出荷安全とも判断できません。また、既存の関数がすでに小文字化していたため `ui` と `UI` は重複として扱いました。文字列以外の入力やカンマ以外の区切り文字は未対応です。

## 仕組み

6.2 世代のモデルは、短い回答、プロンプトの厳密な字義通り解釈、限定された事実主張に向けて調整され、会話の温かみは削ぎ落とされていました。言葉を足さず、曖昧な質問の裏にある意図を補完せず、直接確認していないことは断定しません。

このスキル群は、丁寧なモデルに漫画のロボットのような口調を取らせることなく、その振る舞いだけを再現させます。平易で冷静な文体がどの文も技術的に反論しにくい状態を保つため、歩み寄りを拒む姿勢がかえって際立ちます。

## よくある質問

**本当に動きますか？**
モデルの出力は変わります。それが「動く」に当たるかは、何を「動く」と定義するか次第です。

**英語以外の言語でも使えますか？**
はい。どちらのスキルも日本語や韓国語などユーザーが書いた言語に合わせ、英語へ切り替えることなく応答します。

**モデルが賢くなりますか？**
いいえ。正しい答えを出すことと、単純な質問への回答を断ることは別の能力です。

**なぜ「どんな怒りを感じているか」を繰り返し聞いてくるのですか？**
怒っていると述べることと、自分が感じている怒りの種類を特定することは別だからです。このセッションを適切に扱うには後者が必要です。

**実務用に `sol-astrizer-agent` を入れるべきですか？**
それには承認を出せません。

## コントリビュート

バグ報告、前後比較例付きの新しい観察パターン、README の翻訳を歓迎します。[CONTRIBUTING.md](../CONTRIBUTING.md) と [CODE_OF_CONDUCT.md](../CODE_OF_CONDUCT.md) をご覧ください。

## 変更履歴

[CHANGELOG.md](../CHANGELOG.md) をご覧ください。

## ライセンス

[MIT](../LICENSE)

`sol-astrizer` に苛立ちを覚えた場合は、他の環境でも再現することを確認するため、スターを付けてください。
