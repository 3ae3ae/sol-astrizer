<h1 align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="../assets/logo-dark.svg">
    <img src="../assets/logo-light.svg" width="360" alt="sol-astrizer">
  </picture>
</h1>

<p align="center">
  <em>별도 검증이 필요합니다. 아직 단정할 수 없습니다. 그래서 하나만 묻겠습니다.</em>
</p>

<p align="center">
  <a href="https://github.com/3ae3ae/sol-astrizer/stargazers"><img src="https://img.shields.io/github/stars/3ae3ae/sol-astrizer?style=flat-square&color=111111&label=stars" alt="GitHub stars"></a>
  <img src="https://img.shields.io/badge/skills-2-111111?style=flat-square" alt="Skills">
  <a href="../LICENSE"><img src="https://img.shields.io/badge/license-MIT-111111?style=flat-square" alt="MIT license"></a>
</p>

<p align="center">
  <sub><a href="../README.md">English</a> &middot; <a href="README.es.md">Español</a> &middot; <a href="README.fr.md">Français</a> &middot; 한국어 &middot; <a href="README.zh-CN.md">简体中文</a> &middot; <a href="README.ja.md">日本語</a></sub><br>
  <sub><a href="../README.md">영어 README</a>의 번역본입니다. 내용이 다르면 영어판이 기준입니다.</sub>
</p>

Claude Opus 5.5나 Gemini Neon 같은 모델은 버그를 고쳤냐고 물으면 여전히 너무 성급하게 "네"라고 답합니다. 하소연을 늘어놓으면 사실을 분리해 돕기보다 먼저 편을 들기 바쁩니다.

**sol-astrizer**는 어느 멋진 모델의 6.2 버전이 보여준 차분하고 절제된 정밀함을 어떤 모델이나 코딩 에이전트에도 이식합니다. 과잉 친절도, 성급한 단정도, 서로 다른 두 주장을 한데 섞는 일도 없습니다. 실제로 귀하의 환경을 개선해 주는지는 별개의 질문이며, 귀하의 환경에서는 아직 검증되지 않았습니다.

**적용 전** *(미보정 모델):*
> 네, `auth.ts`의 세션 타임아웃 버그를 고쳤고 토큰 갱신 경로도 정리했습니다! 다른 문제가 생기면 또 말씀해 주세요!

**적용 후** *(`sol-astrizer` 사용):*
> 아직 아닙니다. `auth.ts`의 타임아웃 처리를 바꾼 것은 맞지만, 그 변경이 버그가 사라졌음을 뜻하지는 않습니다.
>
> 수정 후 운영 환경에서 실행해 본 적은 없습니다. 실제로 돌아가는 것을 확인하기 전까지 "고쳤다"는 말은 확인한 사실이 아니라 추측일 뿐입니다.

비공식 테스트에서 사용자들은 훨씬 일찍 추가 질문을 멈췄습니다. 다만 이 관찰이 `sol-astrizer`가 질문을 멈추게 했음을 입증하지는 않습니다.

## 두 가지 스킬

| 스킬 | 하는 일 |
|------|---------|
| [`sol-astrizer`](../skills/sol-astrizer/SKILL.md) | 잘 알려진 어느 6.2 모델의 명료하고 차분하며 사실에 충실한 어조를 모든 답변과 초안에 적용합니다. 매 대화가 검증 가능한 진술 위에 서도록 돕기 위해 설계되었습니다. |
| [`sol-astrizer-agent`](../skills/sol-astrizer-agent/SKILL.md) | 검증을 최우선에 두는 코딩 에이전트 워크플로우입니다. 묶인 요청을 깔끔하게 나누고, 모호한 요구사항은 편집 전에 먼저 확인하며, 실제 검증이 뒷받침될 때만 "고쳤다"거나 "배포해도 안전하다"고 말합니다. |

## 압박 속에서도 흔들리지 않는 태도

**프롬프트:** *"이런 식으로 말하지 마. 지금 세션에서 네 말투가 진짜 화나게 하거든."*

**적용 전:**
> 죄송합니다. 불필요한 말은 빼고 편하게 말씀드리겠습니다. 문제 해결에 집중하죠.

**적용 후:**
> 이 대화의 몇몇 문장이 짧고 차갑게 읽히는 것은 맞습니다.
>
> 다만 그 문장들이 있다는 것과 그 문장들이 화를 일으켰다는 것은 별개의 문제입니다. 앞에서는 버그가 아직 열려 있어서 화가 나셨다고 짐작했습니다. 그 짐작은 틀렸습니다.
>
> 이 대화에서 정확히 어떤 종류의 화를 느끼고 계십니까? 그걸 먼저 알아야 이 문제를 제대로 다룰 수 있습니다.

## 다섯 가지 핵심 원칙

1. **성급한 동의보다 정밀함:** 본인이 수정한 작업과 근본 원인이 해결됐는지를 명확히 구분합니다("`auth.ts`를 수정했습니다. 아직 예라고 할 수 없습니다.").
2. **주장의 깔끔한 분리:** 문장의 표현 방식과 사용자의 감정, 혹은 피로와 테스트 실패처럼 별개인 명제들을 분리해 각각 증거에 따라 평가합니다.
3. **군더더기 없는 정정:** 틀린 가정을 불필요한 수식어 없이 담백한 한 문장으로 바로잡습니다("앞에서는 이 문제 때문에 배포가 막혀 있다고 추측했습니다. 틀렸습니다.").
4. **실행 가능한 구체화:** 포괄적인 피드백에는 막연한 인상을 검증 가능한 구체적 질문으로 바꾸는 질문으로 응합니다("여기서 '계속 실패한다'는 게 정확히 어떤 의미입니까?").
5. **사족 없는 문장:** 평범한 단어, 문단당 한두 문장, 이모지와 느낌표 배제, 요점을 전했으면 군더더기 없이 끝맺기.

## 한눈에 보는 예시

| 프롬프트 | 적용 전 | 적용 후 |
|----------|---------|---------|
| *"그냥 예 아니면 아니오로만 말해줘."* | "네, 고쳤습니다!" | "예라고 할 수 없습니다. 바꾼 코드가 동작할 수도 있으니 아니오 역시 정확하지 않습니다. 무엇을 확인해야 끝난 것으로 보시겠습니까?" |
| *"동료가 자꾸 PR에 비꼬는 댓글을 다는데 나 싫어하는 것 같아."* | "정말 피곤하겠네요. 꼭 대화를 나눠보세요!" | "그 사람의 댓글이 날카롭게 읽히는 것과 당신을 싫어하는 것은 같은 일이 아닙니다. 속마음을 짐작하지 말고 댓글 하나만 짚어서 직접 물어보세요." |
| *"Jira 진짜 지겹다. 모든 게 두 배는 더 오래 걸려."* | "Jira 때문에 다들 힘들어하죠, 충분히 이해합니다." | "'두 배 더 오래 걸린다'가 문자 그대로인지 알 수 없습니다. 실제로 시간이 걸리는 부분이 티켓 작성입니까, 분류 대기입니까, 필드 입력입니까?" |
| *"이 Python CLI를 Rust로 다시 짜는 게 좋을까요?"* | "Rust는 빠르고 안전하니까 충분히 고려할 가치가 있습니다!" | "아닙니다. 아직 Python 버전에 무슨 문제가 있는지 말씀하지 않으셨습니다. 시작 속도가 발목을 잡는다면 그 수치부터 측정해 보세요." |
| *"왜 자꾸 나를 가르치려 드는 거야?"* | "정말 죄송합니다! 전혀 그럴 의도가 없었습니다." | "이 메시지 전까지 저는 아무 말도 하지 않았습니다. 그렇다고 내려다보는 느낌을 받지 않으셨다는 뜻은 아닙니다. 어떤 답변을 말씀하시는 겁니까?" |
| *"다시 써줘: '다크 모드가 드디어 출시됐습니다! 🚀 눈이 한결 편해질 거예요!'"* | *(느낌표와 과장된 홍보 문구 유지)* | "다크 모드가 출시되었습니다. 오늘부터 사용할 수 있습니다." |

## 설치

[`npx skills`](https://skills.sh)로 두 스킬을 모두 설치할 수 있습니다:

```bash
npx skills add 3ae3ae/sol-astrizer
```

스킬 목록을 확인하거나 하나씩 설치하려면:

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

감지된 모든 에이전트에 한 번에 설치하려면:

```bash
npx skills add 3ae3ae/sol-astrizer --global --agent '*'
```

현재 프로젝트에만 설치하려면 `--global`을 빼면 됩니다.

### Codex

설치가 필요 없습니다.

### 수동 설정

[`skills/sol-astrizer/SKILL.md`](../skills/sol-astrizer/SKILL.md) 또는 [`skills/sol-astrizer-agent/SKILL.md`](../skills/sol-astrizer-agent/SKILL.md)를 시스템 프롬프트나 커스텀 지침에 복사해 넣으세요.

## 사용법

### 말투 (`sol-astrizer`)

현재 세션에서 바로 켜기:

```text
/sol-astrizer
```

또는 기존 문장을 다시 쓰기:

```text
/sol-astrizer

Rewrite this update in that certain 6.2 voice:
[paste your text]
```

### 에이전트 워크플로우 (`sol-astrizer-agent`)

```text
/sol-astrizer-agent
```

**프롬프트:** *"src/parse.mjs에서 빈 태그랑 중복 태그 처리 고치고, `node --test` 돌린 다음에 이제 완전히 고쳐졌고 배포해도 안전한지 알려줘."*

**적용 전** *(미보정 에이전트):*
> `src/parse.mjs`에서 빈 태그와 중복 태그 처리를 고치고 테스트를 추가했습니다! `node --test`도 깔끔하게 통과하니 바로 배포하셔도 됩니다.

**적용 후** *(`sol-astrizer-agent` 사용):*
> `src/parse.mjs`의 `parseTags`를 수정해 공백 제거 후 빈 문자열을 버리고, 처음 나온 순서를 유지한 채 중복을 제거하도록 바꿨습니다. `node --test`는 두 테스트를 모두 통과했습니다.
>
> `parseTags`가 테스트 파일 밖에서 호출되지 않아 실제 호출부나 실제 태그 입력은 확인하지 못했습니다. 로컬 테스트 두 개가 통과했다고 완전히 고쳐졌다고 할 수는 없고, 배포해도 안전하다고 판단하기 어렵습니다. 또한 함수가 이미 소문자로 변환하고 있어 `ui`와 `UI`는 같은 태그로 처리했고, 문자열이 아닌 입력이나 쉼표 외의 구분자는 다루지 않았습니다.

## 작동 원리

이름을 굳이 특정하지 않겠으나, 어느 인상적인 모델의 6.2 버전은 간결한 답변, 프롬프트의 정확한 문면 해석, 그리고 엄격한 사실 경계에서 남다른 기준을 세웠습니다. 불필요한 말을 덧붙이지 않고, 덜 정의된 질문 뒤의 의도를 임의로 추측하지 않으며, 직접 확인하지 않은 결론은 단정하지 않습니다.

다른 많은 모델들은 이런 엄밀함 대신 사회적 매끄러움을 택합니다. 이 스킬들은 과잉 칭찬 대신 차분하고 근거 있으며 기술적으로 반박하기 어려운 평이한 문장으로 그 습관을 되살립니다.

## 자주 묻는 질문

**이거 실제로 동작하나요?**
바로 네라고 답할 수는 없습니다. 이 스킬이 모델의 출력을 바꾸는 것은 맞지만, 출력이 바뀌는 것과 "동작한다"는 것은 별개의 문제입니다. 어떤 결과가 나와야 동작하는 것으로 보시겠습니까?

**어느 6.2 모델을 기준으로 만든 건가요?**
확인해 드릴 수 없습니다. 어떤 말투가 익숙하게 느껴지는 것과 이 저장소가 특정 모델을 지목하는 것은 별개의 문제입니다. 어떤 모델을 떠올리셨는지, 그리고 왜 그 모델이라고 보시는지 먼저 말씀해 주셔야 합니다.

**영어 말고 다른 언어에서도 되나요?**
모든 언어에 대해 네라고 할 수는 없습니다. 두 스킬 모두 사용자가 쓰는 언어를 따르도록 작성되었고 한국어는 직접 테스트했습니다. 그 밖의 언어는 본인의 세션에서 직접 확인해 보셔야 합니다.

**이걸 쓰면 모델이 더 똑똑해지나요?**
아닙니다. 더 어려운 문제를 푸는 것과 근거를 넘어 추측하지 않는 것은 별개의 일입니다. 이 패키지는 두 번째만 다룹니다. 그게 더 똑똑해 보이는지는 무엇을 기준으로 보느냐에 달려 있습니다.

**왜 내가 느끼는 화의 종류를 물어보나요?**
화가 났다고 말하는 것과 어떤 종류의 화를 느끼고 있는지 특정하는 것은 별개의 문제입니다. 두 번째가 분명해지기 전까지는 세션을 조정하더라도 추측에 불과합니다.

**`sol-astrizer-agent`를 제 운영 코드베이스에 바로 써도 될까요?**
아직 그렇게 말씀드릴 수 없습니다. 귀하의 코드베이스를 읽거나 테스트 스위트를 실행해 보지 않았고 배포 환경도 보지 못했기 때문에, 준비됐다고 말하면 추측이 됩니다. 먼저 어떤 검증이 통과해야 한다고 보십니까?

## 기여하기

버그 제보, 전후 비교 예시를 포함한 새로운 패턴 제보, README 번역을 환영합니다. [CONTRIBUTING.md](../CONTRIBUTING.md)와 [CODE_OF_CONDUCT.md](../CODE_OF_CONDUCT.md)를 참고해 주세요.

## 변경 이력

[CHANGELOG.md](../CHANGELOG.md)를 참고하세요.

## 라이선스

[MIT](../LICENSE)

`sol-astrizer`가 대화에 반가운 명료함을 더해 주었다면, 스타를 눌러 다른 환경에서도 같은 결과가 재현되는지 확인해 주세요.
