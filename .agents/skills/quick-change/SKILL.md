---
name: quick-change
description: Make one small non-track change, verify it locally, and stop without automatically continuing into commit, validation, or PR preparation.
---

# Skill: Quick Change

## Purpose

이 스킬은 트랙이 필요 없는 작은 수정의 변경 단계까지만 담당합니다. 작은 변경을 만들고 로컬 검증까지 수행한 뒤 멈춥니다.

## Inputs

- 작은 수정 요청
- 트랙이 필요 없다고 판단할 수 있는 범위
- `main`이 아닌 작업 브랜치 또는 브랜치를 만들 수 있는 상태

## When to Use

- 오타 수정
- 문서 문구 정리
- 작은 UI 조정
- 원인이 명확한 작은 버그 수정
- 작은 설정 수정
- 영향 범위가 작고 `spec.md`/`plan.md`가 필요 없는 변경

## Workflow

1. 변경이 정말 작은 수정인지 확인합니다.
2. 변경 범위가 커지거나 완료 기준을 팀과 맞춰야 하면 `start-track`으로 전환합니다.
3. `git fetch origin main`으로 원격 `main` 상태를 확인합니다.
4. 현재 브랜치가 `main`이면 수정하기 전에 작업 브랜치를 만듭니다.
5. 브랜치 이름은 `<type>/<short-name>` 형식을 사용합니다. 예: `docs/fix-typo`
6. 수정합니다.
7. 변경에 맞는 자동 검증을 수행합니다.
8. 자동 검증이 어렵다면 수동 확인 방법과 결과를 기록합니다.

## Rules

- 트랙을 만들지 않습니다.
- `main`에 직접 커밋하거나 push하지 않습니다.
- 문서나 코드를 수정하기 전에 반드시 `main`이 아닌 작업 브랜치에 있어야 합니다.
- 원격 `main`이 없거나 fetch가 실패하면 작업을 계속하기 전에 사용자에게 상태를 알립니다.
- 변경 범위가 커지면 `start-track`으로 전환합니다.
- 큰 기술 결정이 생기면 `write-adr`을 사용합니다.
- 커밋 type은 변경 성격에 맞게 `docs`, `fix`, `chore`, `refactor`, `test` 중에서 고릅니다.

## Outputs

- 생성한 브랜치
- 변경 요약
- 로컬 검증 결과

## Stop Condition

작은 변경과 로컬 검증이 끝나면 멈춥니다. 커밋, 공식 검증 단계, PR 준비는 이 스킬의 범위가 아닙니다.

## Recommended Next Step

일반적으로 다음 단계는 `save-work` 또는 `validate-change`입니다. 단, 자동으로 실행하지 않고 다음 단계로만 제안합니다.

## Non-goals

- 트랙을 생성하지 않습니다.
- `save-work`를 대신 수행하지 않습니다.
- `validate-change`를 대신 수행하지 않습니다.
- `prepare-pr`를 수행하지 않습니다.
- 다음 스킬을 자동 호출하지 않습니다.
