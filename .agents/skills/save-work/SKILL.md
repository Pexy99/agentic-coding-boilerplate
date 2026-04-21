---
name: save-work
description: Create an intermediate commit on a non-main branch and stop without validating or preparing the PR.
---

# Skill: Save Work

## Purpose

이 스킬은 현재 변경을 개발 브랜치에 중간 저장용 커밋으로 남기는 단계까지만 담당합니다.

## Inputs

- `main`이 아닌 개발 브랜치
- 커밋할 변경 파일
- 커밋 메시지 규칙

## Workflow

1. 현재 브랜치가 `main`이 아닌지 확인합니다.
2. `git status`로 변경 파일을 확인합니다.
3. 변경 범위를 요약합니다.
4. 커밋에 포함할 파일을 확인합니다.
5. `CONTRIBUTING.md`의 type 규칙에 맞는 커밋 메시지를 제안합니다.
6. 사용자가 동의하면 커밋합니다.
7. 원격 브랜치 push가 필요하면 사용자 확인 후 push합니다.

## Rules

- `main` 브랜치에서는 커밋하지 않습니다.
- `main`에 직접 push하지 않습니다.
- force push는 하지 않습니다.
- 커밋 메시지는 `feat`, `fix`, `docs`, `refactor`, `test`, `chore` 중 하나로 시작합니다.
- 관련 트랙이 있으면 커밋 type을 트랙 ID의 type과 맞춥니다.
- WIP 커밋이 필요하면 `chore: save work in progress`처럼 명확히 작성합니다.

## Outputs

- 커밋 해시
- 커밋 메시지
- 포함된 파일 요약

## Stop Condition

커밋 또는 선택적 push가 끝나면 멈춥니다. 검증과 PR 준비는 이 스킬의 범위가 아닙니다.

## Recommended Next Step

일반적으로 다음 단계는 `validate-change`입니다. 단, 자동으로 실행하지 않고 다음 단계로만 제안합니다.

## Non-goals

- `validate-change`를 수행하지 않습니다.
- `prepare-pr`를 수행하지 않습니다.
- 다음 스킬을 자동 호출하지 않습니다.
