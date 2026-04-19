# Code Style Guides

이 디렉터리는 팀과 AI 에이전트가 같은 코드 스타일을 따르도록 언어별 규칙을 모아두는 곳입니다.

## 언제 추가하나요?

새 언어, 프레임워크, 주요 코드 영역을 도입할 때 추가합니다.

예:
- Python 코드를 작성한다면 `python.md`
- TypeScript/React 코드를 작성한다면 `typescript.md` 또는 `react.md`
- SQL 규칙이 필요하다면 `sql.md`

## 파일 이름

파일 이름은 소문자와 `-`를 사용합니다.

예:
- `python.md`
- `typescript.md`
- `react.md`
- `sql.md`

## 작성 기준

스타일가이드는 짧고 실행 가능해야 합니다. 팀원이 외우기 어려운 긴 원문을 복사하지 말고, 이 프로젝트에서 꼭 지킬 규칙만 적습니다.

권장 구성:

```md
# [Language or Area] Style Guide

## Formatting
- [들여쓰기, 줄 길이, formatter 등]

## Naming
- [파일, 함수, 클래스, 변수 이름 규칙]

## Project Rules
- [이 프로젝트에서만 지킬 규칙]

## Verification
- [lint, format, test 명령]
```

## 운영 규칙

- `docs/tech-stack.md`에 적힌 언어나 프레임워크와 맞는 스타일가이드를 둡니다.
- 자동화 가능한 규칙은 formatter/linter에 맡깁니다.
- 문서에는 자동화하기 어려운 판단 기준만 짧게 남깁니다.
- 에이전트에게 코드 작업을 맡길 때는 관련 스타일가이드를 함께 읽게 합니다.
