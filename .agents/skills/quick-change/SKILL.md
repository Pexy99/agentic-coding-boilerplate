---
name: quick-change
description: Handle a small change without creating a track by using a non-main branch, keeping scope small, validating the change, and preparing it for PR.
---

# Skill: Quick Change

이 스킬은 트랙이 필요 없는 작은 수정에 사용합니다.

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
3. 현재 브랜치가 `main`이면 작업 브랜치를 만듭니다.
4. 브랜치 이름은 `<type>/<short-name>` 형식을 사용합니다. 예: `docs/fix-typo`
5. 수정합니다.
6. 관련 테스트 또는 수동 확인을 수행합니다.
7. `save-work`로 커밋합니다.
8. `validate-change`로 점검합니다.
9. `prepare-pr`로 PR을 준비합니다.

## Rules

- 트랙을 만들지 않습니다.
- `main`에 직접 커밋하거나 push하지 않습니다.
- 변경 범위가 커지면 `start-track`으로 전환합니다.
- 큰 기술 결정이 생기면 `write-adr`을 사용합니다.
- 커밋 type은 변경 성격에 맞게 `docs`, `fix`, `chore`, `refactor`, `test` 중에서 고릅니다.

## Output

- 생성한 브랜치
- 변경 요약
- 검증 결과
- PR 준비 상태
