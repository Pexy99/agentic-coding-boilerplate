---
name: validate-change
description: Independently validate a completed change, summarize evidence and risks, and stop before PR preparation unless explicitly asked otherwise.
---

# Skill: Validate Change

## Purpose

이 스킬은 구현 단계의 일부가 아니라 독립된 검증 단계입니다. 자동 테스트 결과 정리, 수동 검증 절차 제안, 남은 리스크 요약을 핵심 책임으로 하며, 기본적으로 이 단계가 끝나기 전에는 `prepare-pr`로 넘어가지 않습니다.

## Inputs

- 구현이 끝난 변경 사항
- 관련 `spec.md`, `plan.md`, 테스트 결과, 수동 검증 메모
- 현재 브랜치와 커밋 상태

## Workflow

1. 변경 범위를 확인합니다.
2. `quick-change`로 충분한 작은 수정인지, `start-track`이 필요한 트랙 작업인지 판단합니다.
3. 트랙 작업이면 관련 트랙의 `spec.md`와 `plan.md`가 있는지 확인합니다.
4. 트랙 작업이면 `plan.md`의 진행 상태와 `spec.md`의 완료 기준 체크 상태가 실제 변경과 맞는지 확인합니다.
5. DB, 인증, 배포, 프레임워크처럼 되돌리기 어려운 결정이 있으면 ADR이 필요한지 확인합니다.
6. 변경한 파일에 맞는 린터, 포매터, 테스트가 실행됐는지 확인합니다.
7. 코드 변경인데 테스트 파일이 추가/수정되지 않았다면 자동화 테스트가 불필요하거나 어려운 이유가 기록됐는지 확인합니다.
8. 자동 검증이 없거나 실행할 수 없다면 수동 검증 방법과 결과를 기록했는지 확인합니다.
9. 필요한 문서가 업데이트됐는지 확인합니다.
10. 트랙 작업이면 `docs/tracks.md`에서 Active 유지 또는 History 이동이 실제 상태와 맞는지 확인합니다.
11. 브랜치, 커밋, 트랙 ID의 type이 맞는지 확인합니다.
12. PR 템플릿에 들어갈 검증 요약, 남은 리스크, 후속 확인 항목을 정리합니다.

## Validation Hints

- 코드 변경은 관련 코드 스타일가이드(`docs/code_styleguides/`)와 프로젝트 lint/test 명령을 확인합니다.
- 자동화 테스트를 기본값으로 보고, 수동 검증은 자동화가 어렵거나 비용이 큰 경우의 보완책으로 봅니다.
- UI 작업은 광범위한 E2E 자동화보다 핵심 happy path와 수동 검증 체크리스트를 우선합니다.
- 데이터 처리나 입력/출력 비교처럼 결정론적인 영역은 자동화 비중을 더 높입니다.
- 문서나 YAML 변경은 CI 설정과 lint 설정(`docs/ci.md`, `.markdown-lint.yml`, `.yaml-lint.yml`)을 확인합니다.
- 프로젝트별 검증 명령이 정해져 있으면 `docs/tech-stack.md` 또는 `docs/ci.md`의 기준을 따릅니다.
- 완료된 트랙은 PR 안에서 `docs/tracks.md`의 History로 이동하고, 후속 작업이 남은 트랙은 Active에 둡니다.

## Outputs

- 통과한 검증 항목
- 수정이 필요한 항목
- PR 전에 반드시 처리할 항목
- 남은 리스크 요약
- 사람이 따라할 수 있는 수동 검증 절차 제안

## Stop Condition

검증 결과와 남은 리스크가 정리되면 멈춥니다. 기본적으로 이 단계가 끝나기 전에는 `prepare-pr`로 넘어가지 않습니다. 단, 사용자가 명시적으로 요청하면 예외적으로 바로 다음 단계를 제안할 수 있습니다.

## Recommended Next Step

일반적으로 다음 단계는 `prepare-pr`입니다. 단, 자동으로 실행하지 않고 다음 단계로만 제안합니다.

## Non-goals

- 추가 구현을 하지 않습니다.
- 테스트를 새로 작성하는 구현 작업까지 확장하지 않습니다.
- PR 본문을 완성하지 않습니다.
- 사용자가 명시적으로 요청하지 않으면 `prepare-pr`를 자동 호출하지 않습니다.
