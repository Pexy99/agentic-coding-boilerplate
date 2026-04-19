# Contributing Guide

이 문서는 팀원이 작업할 때 어떤 에이전트 스킬을 쓰면 되는지 안내합니다. 자세한 절차는 각 스킬과 `AGENTS.md`를 따릅니다.

## 기본 원칙

- 작업을 맡길 때는 에이전트에게 먼저 `AGENTS.md`를 읽게 합니다.
- 작은 수정은 `quick-change`로 처리합니다.
- 기능, 버그, API, 화면, 구조 변경처럼 맥락 공유가 필요한 작업은 `start-track`으로 시작합니다.
- 에이전트가 만든 변경은 사람이 리뷰하고 최종 책임을 집니다.
- `main`에는 직접 push하지 않습니다. 모든 변경은 PR로 병합합니다.

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
   - merge는 하지 않습니다. 리뷰와 CI는 GitHub 보호 규칙에 맡깁니다.

## 필요할 때만 쓰는 스킬

- `write-adr`
  - DB, 인증, 배포, 프레임워크처럼 되돌리기 어려운 결정을 기록할 때 사용합니다.
  - 작은 구현 세부사항에는 사용하지 않습니다.

## 도구별 스킬 호출

Claude Code, Codex, Antigravity 모두 채팅 입력창에 `/`와 스킬 이름을 입력하여 즉시 실행할 수 있습니다. (Claude Code용 커스텀 명령어는 이미 `.claude/commands/` 아래에 세팅되어 있습니다.)

예:
```text
/quick-change
/start-track
/implement-track
/save-work
/validate-change
/prepare-pr
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
- PR에는 최소 1명 리뷰가 필요합니다.
- 병합 전 관련 테스트와 린트를 확인합니다.
- GitHub 브랜치 보호와 required check 설정은 `docs/project-setup.md`를 따릅니다.

## 충돌 처리

- `docs/tracks.md`, `docs/workflow.md`처럼 여러 사람이 자주 수정하는 문서에서 충돌이 나면 혼자 덮어쓰지 않습니다.
- 팀 채널에 충돌 파일과 수정 의도를 공유한 뒤, 최신 `main` 기준으로 다시 정리합니다.
