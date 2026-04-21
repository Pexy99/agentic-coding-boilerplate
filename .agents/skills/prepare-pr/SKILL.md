---
name: prepare-pr
description: Prepare a PR draft, change summary, validation summary, and review context, then stop without adding more implementation or re-validation by default.
---

# Skill: Prepare PR

## Purpose

이 스킬은 PR 본문 초안, 변경 요약, 검증 요약, 리뷰 준비까지만 담당합니다. 추가 구현, 재검증, 추가 수정은 기본 책임이 아닙니다.

## Inputs

- 커밋되었거나 PR 직전 상태인 변경 사항
- `validate-change` 결과 요약
- 관련 트랙과 검증 기록
- 현재 브랜치 상태

## Workflow

1. 현재 브랜치가 `main`이 아닌지 확인합니다.
2. `git fetch origin main`으로 PR 기준 브랜치의 최신 상태를 확인합니다.
3. 현재 브랜치가 `origin/main` 기준으로 뒤처져 있으면 사용자에게 알리고 최신 `main` 반영이 필요하다고 안내합니다.
4. `git status`로 커밋되지 않은 변경이 있는지 확인합니다.
5. 커밋되지 않은 변경이 있으면 `save-work` 사용을 제안합니다.
6. `validate-change` 결과가 있는지 확인합니다. 없다면 먼저 검증이 필요하다고 알립니다.
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
- PR 전 `validate-change`를 기본 전제 조건으로 둡니다.
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

## Outputs

- PR 제목 초안
- PR 본문 초안
- 검증 요약
- 리뷰어가 확인해야 할 항목
- 생성된 PR 링크, 생성한 경우

## Stop Condition

PR 초안과 리뷰 준비 정보가 정리되면 멈춥니다. 추가 구현, 재검증, 후속 수정을 기본 단계로 수행하지 않습니다.

## Recommended Next Step

일반적으로 다음 단계는 사람의 리뷰 요청 또는 PR 생성 확인입니다. PR이 병합된 뒤에는 `cleanup-branches`를 제안할 수 있습니다. 단, 자동으로 실행하지 않습니다.

## Non-goals

- 추가 구현을 하지 않습니다.
- `validate-change`를 대신 다시 수행하지 않습니다.
- 자동으로 merge하지 않습니다.
- 사용자가 명시적으로 요청하지 않으면 다음 스킬을 자동 호출하지 않습니다.
