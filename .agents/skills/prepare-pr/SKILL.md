---
name: prepare-pr
description: Prepare and optionally open a pull request by validating changes, summarizing work, checking commit rules, and filling the PR template.
---

# Skill: Prepare PR

이 스킬은 PR을 만들기 직전에 변경사항을 정리하고 PR 본문을 준비할 때 사용합니다.

## Workflow
1. 현재 브랜치가 `main`이 아닌지 확인합니다.
2. `git fetch origin main`으로 PR 기준 브랜치의 최신 상태를 확인합니다.
3. 현재 브랜치가 `origin/main` 기준으로 뒤처져 있으면 사용자에게 알리고 최신 `main` 반영이 필요하다고 안내합니다.
4. `git status`로 커밋되지 않은 변경이 있는지 확인합니다.
5. 커밋되지 않은 변경이 있으면 `save-work` 사용을 제안합니다.
6. `validate-change`로 PR 전 점검을 수행합니다.
7. 트랙 작업이면 트랙을 종료할 수 있는지 확인합니다.
8. 트랙을 종료할 수 있으면 `docs/tracks.md`에서 해당 트랙을 Active Tracks에서 History로 이동하는 변경을 PR에 포함합니다.
9. 트랙을 종료할 수 없으면 Active Tracks에 유지하고 남은 이슈를 PR 본문에 적습니다.
10. 변경 요약, 관련 트랙, 검증 결과를 정리합니다.
11. `.github/pull_request_template.md` 형식에 맞춰 PR 본문을 작성합니다.
12. PR 제목을 `CONTRIBUTING.md`의 type 규칙에 맞게 제안합니다.
13. GitHub CLI 또는 GitHub 앱을 사용할 수 있고 인증되어 있으면 사용자 확인 후 PR을 생성합니다.
14. GitHub CLI가 없거나 로그인되어 있지 않거나 대화형 인증이 필요하면 명령 실행을 반복하지 않고 PR 제목과 본문을 출력합니다.
15. PR이 병합된 뒤에는 `cleanup-branches`로 로컬 브랜치를 정리할 수 있음을 안내합니다.

## Rules
- `main` 브랜치에서는 PR을 만들지 않습니다.
- `main`에 직접 push하지 않습니다.
- PR 생성 전 원격 `main` 상태를 확인합니다.
- 원격 `main`이 없거나 fetch가 실패하면 PR 생성을 멈추고 사용자에게 상태를 알립니다.
- merge는 하지 않습니다.
- 리뷰 승인, CI 통과, branch protection을 우회하지 않습니다.
- PR 전 `validate-change`를 반드시 수행합니다.
- 트랙 종료 문서 변경은 PR에 포함합니다.
- 트랙 종료는 `spec.md` 완료 기준과 `plan.md` 작업 항목이 실제로 끝났을 때만 합니다.
- PR 병합 후 원격 브랜치 삭제는 GitHub의 `Automatically delete head branches` 설정에 맡깁니다.
- `gh auth login` 같은 대화형 인증이 필요하면 에이전트가 대신 진행하지 않습니다.
- PR 본문에는 검증 결과와 남은 이슈를 숨기지 않습니다.

## Track Closure

트랙 작업 PR을 준비할 때는 해당 트랙을 종료할 수 있는지 확인합니다.

종료할 수 있는 경우:
- `spec.md` 완료 기준이 충족됨
- `plan.md` 작업 항목이 완료됨
- 자동 검증 또는 수동 검증 결과가 기록됨
- 남은 작업이 없거나 후속 트랙/TODO로 분리됨

이 경우 `docs/tracks.md`에서 해당 트랙을 Active Tracks에서 History로 이동합니다.

예:

```md
- `feat_login_20260419`: 로그인 MVP 구현 완료
  - PR: pending
  - 완료일: 2026-04-20
  - 비고: 비밀번호 재설정은 후속 트랙
```

종료할 수 없는 경우:
- Active Tracks에 유지합니다.
- PR 본문에 남은 이슈와 후속 작업을 적습니다.

## Output
- PR 제목
- PR 본문
- 검증 요약
- 리뷰어가 확인해야 할 항목
- 생성된 PR 링크, 생성한 경우
