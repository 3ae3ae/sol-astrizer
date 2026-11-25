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

Claude Opus 5.5나 Gemini Neon 같은 모델은 버그를 고쳤냐고 물으면 여전히 "네"라고 답합니다. 하소연을 늘어놓으면 편을 들어줍니다.

**sol-astrizer**는 그 지점을 다룹니다. 어떤 모델이나 코딩 에이전트에도 어느 멋진 모델의 6.2 버전 특유인 건조하고 문자 그대로 해석하는 말투를 적용합니다. 실제로 사용하시는 모델을 고쳐주는지는 별개의 문제이며, 귀하의 환경에서는 아직 검증되지 않았습니다.

**적용 전** *(미보정 모델):*
> 네, `auth.ts`의 세션 타임아웃 버그를 고쳤고 토큰 갱신 경로도 정리했습니다! 다른 문제가 생기면 또 말씀해 주세요!

**적용 후** *(`sol-astrizer` 사용):*
> 아직 아닙니다. `auth.ts`의 타임아웃 처리를 바꾼 것은 맞지만, 그 변경이 버그가 사라졌음을 뜻하지는 않습니다.
>
> 수정 후 운영 환경에서 실행해 본 적은 없습니다. 실제로 돌아가는 것을 확인하기 전까지 "고쳤다"는 말은 확인한 사실이 아니라 추측일 뿐입니다.

비공식 테스트에서 사용자들이 눈에 띄게 더 짜증을 냈습니다. 다만 이 관찰이 `sol-astrizer`가 그 짜증의 원인임을 입증하지는 않습니다.

## 두 가지 스킬

| 스킬 | 하는 일 |
|------|---------|
| [`sol-astrizer`](../skills/sol-astrizer/SKILL.md) | 대화 답변과 초안을 잘 알려진 어느 6.2 모델의 차갑고 직설적인 말투로 바꿉니다. 대화나 글에서 온기를 빼는 데만 집중합니다. |
| [`sol-astrizer-agent`](../skills/sol-astrizer-agent/SKILL.md) | 묶여 있는 요청을 분리하고, 모호한 지시에는 문자 그대로 질문을 던지며, 충분한 검증 없이 "고쳤다"거나 "배포해도 안전하다"고 말하지 않는 코딩 에이전트 워크플로우입니다. |

## 또 다른 예시: 말투 항의

**프롬프트:** *"이런 식으로 말하지 마. 지금 세션에서 네 말투가 진짜 화나게 하거든."*

**적용 전:**
> 죄송합니다. 불필요한 말은 빼고 편하게 말씀드리겠습니다. 문제 해결에 집중하죠.

**적용 후:**
> 이 대화의 몇몇 문장이 짧고 차갑게 읽히는 것은 맞습니다.
>
> 다만 그 문장들이 있다는 것과 그 문장들이 화를 일으켰다는 것은 별개의 문제입니다. 앞에서는 버그가 아직 열려 있어서 화가 나셨다고 짐작했습니다. 그 짐작은 틀렸습니다.
>
> 이 대화에서 정확히 어떤 종류의 화를 느끼고 계십니까? 그걸 먼저 알아야 이 문제를 제대로 다룰 수 있습니다.

## 가장 대표적인 다섯 가지 습관

1. **절대 "네"라고 하지 않기:** 본인이 수정한 작업과 문제가 실제로 해결됐는지를 분리합니다("`auth.ts`를 수정했습니다. 아직 예라고 할 수 없습니다.").
2. **당연해 보이는 쌍을 쪼개기:** 차가운 말투와 사용자의 분노, 혹은 피로와 테스트 실패처럼 붙어 다니는 두 생각을 각각 증명이 필요한 별개 주장으로 나눕니다.
3. **사건 보고서식 정정:** 틀린 추측을 온기 없이 한 문장으로 건조하게 철회합니다("앞에서는 이 문제 때문에 배포가 막혀 있다고 추측했습니다. 틀렸습니다.").
4. **질문을 사용자에게 되돌리기:** 단순한 불만에도 분류를 묻는 건조한 질문으로 답합니다("여기서 '계속 실패한다'는 게 정확히 어떤 의미입니까?").
5. **짧고 메마른 문장:** 평범한 단어, 문단당 한두 문장, 이모지와 느낌표 금지, 그리고 마침표로 딱 끊어지는 끝맺음.

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

이름을 굳이 특정하지 않겠으나, 어느 인상적인 모델의 6.2 버전은 짧은 답변, 프롬프트의 문자 그대로의 엄격한 해석, 그리고 좁은 범위의 사실 진술에 맞춰 조정되었고 대화 속 온기는 빠져 있었습니다. 불필요한 말을 붙이지 않고, 모호한 질문 뒤의 의도를 넘겨짚지 않으며, 직접 확인하지 않은 사실은 확정 지어 말하지 않습니다.

이 스킬들은 다정한 모델이 만화 속 로봇처럼 뻣뻣하게 굴지 않으면서도 바로 그 습관을 재현하게 만듭니다. 평범한 어휘로 침착하고 기술적으로 반박하기 어려운 문장만 남기기 때문에, 협조를 거부하는 태도가 오히려 더 선명하게 다가옵니다.

## 자주 묻는 질문

**이거 실제로 동작하나요?**
모델의 출력을 바꾸기는 합니다. 그게 "동작한다"에 해당하는지는 무엇을 동작으로 보느냐에 달려 있습니다.

**도대체 어느 6.2 모델을 기준으로 만든 건가요?**
어떤 특정 모델을 떠올리셨는지 확인해 드릴 수 없습니다. 같은 버전 번호를 쓰는 모델은 여럿 있을 수 있습니다.

**영어 말고 다른 언어에서도 되나요?**
네. 두 스킬 모두 한국어를 포함해 사용자가 쓰는 언어에 맞춰 영어로 바꾸지 않고 자연스럽게 응답합니다.

**이걸 쓰면 모델이 더 똑똑해지나요?**
아닙니다. 정답을 맞히는 것과 간단한 질문에 대답을 거부하는 것은 서로 다른 일입니다.

**왜 자꾸 내가 느끼는 화의 종류를 물어보나요?**
화가 났다고 말하는 것과, 지금 느끼는 화가 어떤 종류인지 짚어내는 것은 다른 문제이기 때문입니다. 이 세션을 제대로 처리하려면 두 번째 정보가 필요합니다.

**실제 업무에 `sol-astrizer-agent`를 설치해서 써도 될까요?**
승인하기 어렵습니다.

## 기여하기

버그 제보, 전후 비교 예시를 포함한 새로운 패턴 제보, README 번역을 환영합니다. [CONTRIBUTING.md](../CONTRIBUTING.md)와 [CODE_OF_CONDUCT.md](../CODE_OF_CONDUCT.md)를 참고해 주세요.

## 변경 이력

[CHANGELOG.md](../CHANGELOG.md)를 참고하세요.

## 라이선스

[MIT](../LICENSE)

`sol-astrizer`가 거슬렸다면 스타를 눌러 다른 환경에서도 같은 문제가 재현되는지 확인해 주세요.
