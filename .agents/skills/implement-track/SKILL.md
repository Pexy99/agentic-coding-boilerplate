---
name: implement-track
description: Implement a task from an active track by reading the track spec and plan, updating task status, verifying changes, and preparing the result for PR.
---

# Skill: Implement Track Task

이 스킬은 활성 트랙의 특정 태스크를 구현할 때 사용합니다.

## Read First
1. `AGENTS.md`
2. `docs/product.md`
3. `docs/tech-stack.md`
4. `docs/workflow.md`
5. `docs/tracks.md`
6. 해당 트랙의 `spec.md`
7. 해당 트랙의 `plan.md`
8. 관련 `docs/code_styleguides/`

## Workflow
1. `git fetch origin main`으로 원격 `main` 상태를 확인합니다.
2. 현재 브랜치가 `main`이면 코드를 수정하기 전에 트랙에 맞는 작업 브랜치를 만듭니다.
3. 구현할 태스크가 `plan.md`에 있는지 확인합니다.
4. `spec.md`의 목표, 범위, 완료 기준을 확인합니다.
5. 시작한 태스크를 `plan.md`에서 `[~]`로 변경합니다.
6. 자동화 테스트 방법을 먼저 정합니다. 자동화가 어렵다면 이유와 수동 확인 방법을 정합니다.
7. 구현합니다.
8. 관련 테스트, lint, format 등 자동 검증을 실행합니다.
9. 필요한 문서가 있으면 업데이트합니다.
10. 자동 검증이 어렵다면 수동 검증 결과와 자동화하지 못한 이유를 `plan.md` 또는 PR 설명에 남깁니다.
11. 완료한 태스크를 `plan.md`에서 `[x]`로 변경합니다.
12. 충족된 완료 기준을 `spec.md`에서 `[x]`로 변경합니다.
13. 가능하면 완료 항목 옆에 커밋 해시를 남깁니다.
14. PR 전 `validate-change` 스킬로 변경사항을 점검합니다.

## Rules
- 구현 전 반드시 `main`이 아닌 작업 브랜치에 있어야 합니다.
- 원격 `main`이 없거나 fetch가 실패하면 작업을 계속하기 전에 사용자에게 상태를 알립니다.
- `spec.md`와 충돌하는 구현은 하지 않습니다. 범위 변경이 필요하면 먼저 `spec.md`를 업데이트합니다.
- 테스트 파일을 추가하거나 기존 테스트를 업데이트하는 것을 기본값으로 삼습니다.
- 자동화 테스트가 어렵다면 그 이유와 수동 검증 방법을 `plan.md` 또는 PR 설명에 남깁니다.
- 작업 완료 시 `plan.md` 진행 상태와 `spec.md` 완료 기준 체크 상태를 함께 동기화합니다.
- 기술 선택이나 제약이 바뀌면 `docs/tech-stack.md`를 업데이트합니다.
- 코드 변경 시 관련 `docs/code_styleguides/` 문서를 따릅니다.
- `git notes`는 선택 사항입니다. PR 설명과 `plan.md`로 충분하면 사용하지 않아도 됩니다.

## Output
- 변경 요약
- 검증 결과
- 업데이트한 문서
- 남은 이슈
