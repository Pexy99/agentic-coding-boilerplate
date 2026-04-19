---
name: validate-change
description: Check whether a code or documentation change is ready for PR or merge by validating workflow fit, track status, docs, tests, and review readiness.
---

# Skill: Validate Change

이 스킬은 변경사항이 PR 또는 병합 준비 상태인지 확인합니다.

## Workflow
1. 변경 범위를 확인합니다.
2. 작업 크기가 Level 1/2/3 중 어디에 해당하는지 판단합니다.
3. Level 2 이상이면 관련 트랙의 `spec.md`와 `plan.md`가 있는지 확인합니다.
4. `plan.md`의 진행 상태가 실제 변경과 맞는지 확인합니다.
5. 테스트 또는 수동 검증 기록이 있는지 확인합니다.
6. 필요한 문서가 업데이트됐는지 확인합니다.
7. 브랜치, 커밋, 트랙 ID의 type이 맞는지 확인합니다.
8. PR 템플릿에 채울 요약과 검증 내용을 정리합니다.

## Output
- 통과한 항목
- 수정이 필요한 항목
- PR 전에 반드시 처리할 항목
- 선택 개선 사항
