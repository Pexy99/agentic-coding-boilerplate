---
name: validate-change
description: Check whether a code or documentation change is ready for PR or merge by validating workflow fit, track status, docs, tests, and review readiness.
---

# Skill: Validate Change

이 스킬은 변경사항이 PR 또는 병합 준비 상태인지 확인합니다.

## Workflow
1. 변경 범위를 확인합니다.
2. `quick-change`로 충분한 작은 수정인지, `start-track`이 필요한 트랙 작업인지 판단합니다.
3. 트랙 작업이면 관련 트랙의 `spec.md`와 `plan.md`가 있는지 확인합니다.
4. 트랙 작업이면 `plan.md`의 진행 상태가 실제 변경과 맞는지 확인합니다.
5. DB, 인증, 배포, 프레임워크처럼 되돌리기 어려운 결정이 있으면 ADR이 필요한지 확인합니다.
6. 변경한 파일에 맞는 린터, 포매터, 테스트를 실행했는지 확인합니다.
7. 자동 검증이 없거나 실행할 수 없다면 수동 검증 방법과 결과를 기록했는지 확인합니다.
8. 필요한 문서가 업데이트됐는지 확인합니다.
9. 브랜치, 커밋, 트랙 ID의 type이 맞는지 확인합니다.
10. PR 템플릿에 채울 요약과 검증 내용을 정리합니다.

## Validation Hints
- 코드 변경은 관련 코드 스타일가이드(`docs/code_styleguides/`)와 프로젝트 lint/test 명령을 확인합니다.
- 문서나 YAML 변경은 CI 설정과 lint 설정(`docs/ci.md`, `.markdown-lint.yml`, `.yaml-lint.yml`)을 확인합니다.
- 프로젝트별 검증 명령이 정해져 있으면 `docs/tech-stack.md` 또는 `docs/ci.md`의 기준을 따릅니다.

## Output
- 통과한 항목
- 수정이 필요한 항목
- PR 전에 반드시 처리할 항목
- 선택 개선 사항
