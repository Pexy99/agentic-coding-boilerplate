# Contributing Guide

이 문서는 팀원이 작업할 때 어떤 에이전트 스킬을 쓰면 되는지 안내합니다. 자세한 절차는 각 스킬과 `AGENTS.md`를 따릅니다.

## TL;DR

- 새 프로젝트 시작: `/init-project`
- 작은 수정: `/quick-change`
- 기능/버그/구조 변경: `/start-track`
- 작업 중간 저장: `/save-work`
- PR 전 점검: `/validate-change`
- PR 준비: `/prepare-pr`
- PR 병합 후 로컬 브랜치 정리: `/cleanup-branches`
- 큰 기술 결정: 필요할 때 `/write-adr`

## 기본 원칙

- 작업을 맡길 때는 에이전트에게 먼저 `AGENTS.md`를 읽게 합니다.
- 새 프로젝트의 첫 작업은 `init-project`로 전역 문맥을 먼저 채웁니다.
- 작은 수정은 `quick-change`로 처리합니다.
- 기능, 버그, API, 화면, 구조 변경처럼 맥락 공유가 필요한 작업은 `start-track`으로 시작합니다.
- 에이전트가 만든 변경은 사람이 리뷰하고 최종 책임을 집니다.
- `main`에는 직접 push하지 않습니다. 모든 변경은 PR로 병합합니다.
- 문서나 코드를 수정하기 전에 먼저 작업 브랜치로 분리합니다.
- 주요 작업 시작 전과 PR 생성 전에는 원격 `main` 상태를 확인합니다.
- 코드 변경은 자동화 테스트를 우선합니다. 어렵다면 이유와 수동 검증 결과를 남깁니다.
- 구조 규칙은 문서로만 권고하지 않고, 가능하면 공식 스캐폴더와 팀 규칙으로 맞춥니다.
- UI E2E는 최소화하고, 사람이 따라할 수 있는 검증 체크리스트를 남깁니다.
- 트랙 작업 완료 시 `plan.md`와 `spec.md` 체크 상태를 함께 맞춥니다.

## 권장 도구

- GitHub CLI(`gh`)를 설치하면 `prepare-pr` 스킬이 PR 생성을 도와줄 수 있습니다.
- `gh`가 없으면 `prepare-pr`이 PR 제목과 본문을 만들어주고, 사용자가 GitHub 웹에서 직접 PR을 생성합니다.

## AI에게 작업을 맡길 때

작업을 맡기면 에이전트는 파일을 수정하기 전에 먼저 아래 내용을 말해야 합니다.

- 사용할 흐름: `init-project`, `quick-change`, 또는 `start-track`
- 작업 브랜치 생성 여부
- `origin/main` 확인 여부
- 예상 검증 방법
- 다음에 따를 스킬 순서

에이전트가 이 내용을 말하지 않고 바로 수정하려고 하면 먼저 `AGENTS.md`와 이 문서를 읽고 작업 시작 선언을 하라고 요청합니다.

예:

```text
AGENTS.md와 CONTRIBUTING.md를 읽고, 작업 시작 전에 사용할 흐름과 브랜치/검증 계획을 먼저 말해줘.
```

여러 단계를 한 번에 진행하는 것은 허용하지만, PR 전에는 반드시 `validate-change` 결과를 요약해야 합니다.

## 앞으로 쓸 절차

작업 종류에 따라 아래 순서로 요청합니다.

- 새 프로젝트 초기화: `/init-project`
- 작은 수정: `/quick-change` -> `/save-work` -> `/validate-change` -> `/prepare-pr`
- 기능/버그/화면/구조 변경: `/start-track` -> `/implement-track` -> `/save-work` -> `/validate-change` -> `/prepare-pr`
- 큰 기술 결정: 필요한 시점에 `/write-adr`
- PR 병합 후 로컬 브랜치 정리: `/cleanup-branches`

## 작은 수정과 트랙 작업의 차이

`quick-change`를 쓰는 경우:

- 오타 수정
- 문서 문구 정리
- 작은 UI 조정
- 원인이 명확한 작은 버그 수정
- 작은 설정 수정
- 변경 범위가 작고 `spec.md`/`plan.md`가 필요 없는 작업

`start-track`을 쓰는 경우:

- 새 기능 추가
- 사용자 흐름 변경
- API, DB, 인증, 배포 관련 변경
- 원인 분석이 필요한 버그 수정
- QA나 디자인 리뷰가 필요한 UI 변경
- 여러 파일이나 모듈에 걸친 변경
- 완료 기준을 팀과 맞춰야 하는 작업

작은 수정으로 시작했더라도 변경 범위가 커지면 `start-track`으로 전환합니다.

## 스킬 사용 순서

작은 수정은 아래 순서로 진행합니다.

1. `quick-change`
   - 트랙 없이 작은 수정을 진행할 때 사용합니다.
   - `main`이 아닌 작업 브랜치에서 수정하고 PR로 병합합니다.
2. `save-work`
   - 개발 브랜치에서 중간 커밋이 필요할 때 사용합니다.
3. `validate-change`
   - PR 전 또는 AI 작업 후 점검할 때 사용합니다.
4. `prepare-pr`
   - PR 제목과 본문을 준비하고, 가능하면 PR을 생성할 때 사용합니다.

일반 작업은 아래 순서로 진행합니다.

1. `start-track`
   - 새 기능, 버그 수정, 구조 변경을 시작할 때 사용합니다.
   - 트랙 ID, `spec.md`, `plan.md`를 만듭니다.
   - 정보가 부족하면 에이전트가 목표, 범위, 완료 기준, 검증 방법을 먼저 질문합니다.
2. `implement-track`
   - 트랙의 작업을 구현할 때 사용합니다.
   - `spec.md`와 `plan.md`를 확인하고 진행 상태를 업데이트합니다.
3. `save-work`
   - 개발 브랜치에서 중간 커밋이 필요할 때 사용합니다.
4. `validate-change`
   - PR 전 또는 AI 작업 후 점검할 때 사용합니다.
   - 트랙 상태, 문서 업데이트, 검증 기록, 브랜치/커밋 규칙을 확인합니다.
5. `prepare-pr`
   - PR 제목과 본문을 준비하고, 가능하면 PR을 생성할 때 사용합니다.
   - 트랙이 완료됐다면 `docs/tracks.md`에서 Active Tracks 항목을 History로 이동하는 변경을 PR에 포함합니다.
   - merge는 하지 않습니다. 리뷰와 CI는 GitHub 보호 규칙에 맡깁니다.

## 필요할 때만 쓰는 스킬

- `cleanup-branches`
  - PR이 병합된 뒤 로컬 브랜치를 정리할 때 사용합니다.
  - 병합 여부가 확실한 로컬 브랜치만 사용자 확인 후 삭제합니다.
- `write-adr`
  - DB, 인증, 배포, 프레임워크처럼 되돌리기 어려운 결정을 기록할 때 사용합니다.
  - 작은 구현 세부사항에는 사용하지 않습니다.

## 도구별 스킬 호출

Claude Code, Codex, Antigravity 모두 채팅 입력창에 `/`와 스킬 이름을 입력하여 즉시 실행할 수 있습니다. (Claude Code용 커스텀 명령어는 이미 `.claude/commands/` 아래에 세팅되어 있습니다.)

예:
```text
/init-project
/quick-change
/start-track
/implement-track
/save-work
/validate-change
/prepare-pr
/cleanup-branches
/write-adr
```

## 이름 규칙

트랙 ID, 브랜치, 커밋 메시지는 같은 type을 사용합니다.

- 사용 가능한 type: `feat`, `fix`, `docs`, `refactor`, `test`, `chore`
- 트랙 ID: `feat_login_20260419`
- 브랜치: `feat/login_20260419`
- 커밋: `feat: add login form`

## GitHub 규칙

- `main` 브랜치는 항상 배포 가능한 상태를 유지합니다.
- `main` 직접 push는 금지합니다.
- 작업 시작 전 `git fetch origin main`으로 원격 상태를 확인합니다.
- `main`에서 바로 수정하지 말고 `feat/...`, `fix/...`, `docs/...` 같은 작업 브랜치를 먼저 만듭니다.
- PR에는 최소 1명 리뷰가 필요합니다.
- 병합 전 관련 테스트와 린트를 확인합니다.
- PR conversation은 병합 전 모두 resolve합니다.
- `main` 보호 규칙 우회는 허용하지 않습니다.
- GitHub 브랜치 보호와 required check 설정은 `docs/project-setup.md`를 따릅니다.

## 브랜치 정리

- PR이 병합된 브랜치는 삭제합니다.
- GitHub의 `Automatically delete head branches` 설정을 켜두는 것을 권장합니다.
- 로컬 브랜치는 필요할 때 `cleanup-branches` 스킬로 정리합니다.
- 병합되지 않은 오래된 브랜치는 작성자가 정리합니다.
- 보류 중인 작업 브랜치는 PR 설명이나 팀 채널에 남은 이유를 짧게 남깁니다.

## 충돌 처리

- `docs/tracks.md`, `docs/workflow.md`처럼 여러 사람이 자주 수정하는 문서에서 충돌이 나면 혼자 덮어쓰지 않습니다.
- 팀 채널에 충돌 파일과 수정 의도를 공유한 뒤, 최신 `main` 기준으로 다시 정리합니다.
