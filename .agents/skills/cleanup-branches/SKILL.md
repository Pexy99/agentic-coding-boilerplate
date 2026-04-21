---
name: cleanup-branches
description: Review and clean up merged local branches only, then stop without modifying tracks, validation, or PR state.
---

# Skill: Cleanup Branches

## Purpose

이 스킬은 PR 병합 후 로컬 브랜치를 안전하게 정리하는 단계까지만 담당합니다.

## Inputs

- 병합이 끝난 작업 브랜치들
- 로컬 git 상태
- 브랜치 삭제 전 사용자 확인

## When to Use

- PR이 병합된 뒤 로컬 브랜치를 정리할 때
- 원격에서 삭제된 브랜치를 로컬에도 반영하고 싶을 때
- 오래된 작업 브랜치를 확인하고 싶을 때

## Workflow

1. `git status`로 작업 중인 변경이 없는지 확인합니다.
2. 변경 중인 파일이 있으면 중단하고 사용자에게 먼저 저장 또는 커밋을 요청합니다.
3. 현재 브랜치가 `main`이면 그대로 진행합니다.
4. 현재 브랜치가 작업 브랜치이면 삭제 대상이 될 수 없으므로 `main`으로 이동할지 사용자에게 확인합니다.
5. `git fetch --prune`으로 원격 삭제 상태를 반영합니다.
6. 로컬 브랜치 목록을 확인합니다.
7. `main`에 병합된 로컬 브랜치만 삭제 후보로 분류합니다.
8. 삭제 후보와 제외한 브랜치를 사용자에게 보여줍니다.
9. 사용자 확인 후 병합된 로컬 브랜치만 삭제합니다.

## Rules

- `main`은 삭제하지 않습니다.
- 현재 체크아웃된 브랜치는 삭제하지 않습니다.
- 병합 여부가 불확실한 브랜치는 삭제하지 않습니다.
- 커밋되지 않은 변경이 있으면 삭제 작업을 하지 않습니다.
- 강제 삭제(`git branch -D`)는 사용하지 않습니다.
- 원격 브랜치 삭제는 GitHub의 `Automatically delete head branches` 설정에 맡깁니다.

## Outputs

- 삭제한 로컬 브랜치
- 삭제하지 않은 브랜치와 이유
- 추가 확인이 필요한 오래된 브랜치

## Stop Condition

로컬 브랜치 정리가 끝나면 멈춥니다. 문서 정리나 트랙 종료는 이 스킬의 범위가 아닙니다.

## Recommended Next Step

일반적으로 다음 단계는 없습니다. 필요하면 다른 변경 작업을 시작할 수 있다고만 제안합니다.

## Non-goals

- `docs/tracks.md`를 수정하지 않습니다.
- 트랙 종료를 수행하지 않습니다.
- `validate-change`나 `prepare-pr`를 수행하지 않습니다.
- 다음 스킬을 자동 호출하지 않습니다.
