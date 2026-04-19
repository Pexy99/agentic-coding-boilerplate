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
1. 구현할 태스크가 `plan.md`에 있는지 확인합니다.
2. `spec.md`의 목표, 범위, 완료 기준을 확인합니다.
3. 시작한 태스크를 `plan.md`에서 `[~]`로 변경합니다.
4. 테스트 또는 수동 확인 방법을 먼저 정합니다.
5. 구현합니다.
6. 관련 테스트 또는 수동 검증을 실행합니다.
7. 필요한 문서가 있으면 업데이트합니다.
8. 완료한 태스크를 `plan.md`에서 `[x]`로 변경합니다.
9. 가능하면 완료 항목 옆에 커밋 해시를 남깁니다.
10. PR 전 `validate-change` 스킬로 변경사항을 점검합니다.

## Rules
- `spec.md`와 충돌하는 구현은 하지 않습니다. 범위 변경이 필요하면 먼저 `spec.md`를 업데이트합니다.
- 테스트가 없으면 수동 검증 방법을 `plan.md` 또는 PR 설명에 남깁니다.
- 기술 선택이나 제약이 바뀌면 `docs/tech-stack.md`를 업데이트합니다.
- 코드 변경 시 관련 `docs/code_styleguides/` 문서를 따릅니다.
- `git notes`는 선택 사항입니다. PR 설명과 `plan.md`로 충분하면 사용하지 않아도 됩니다.

## Output
- 변경 요약
- 검증 결과
- 업데이트한 문서
- 남은 이슈
