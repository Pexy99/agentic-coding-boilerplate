# Agent Loader

이 저장소는 **문서 주도(Document-Driven) 워크플로우**를 사용합니다. 작업 전 `docs/`의 공통 문맥을 읽고, 트랙 작업은 해당 `spec.md`와 `plan.md`를 기준으로 진행합니다.

## Source of Truth
- **Project Knowledge**: `docs/` 디렉터리 내의 모든 문서.
- **Task Status**: 활성화된 트랙의 `plan.md` (예: `docs/tracks/<track_id>/plan.md`).

## 필수 확인 순서 (Read First)
작업 시작 전 다음 순서대로 파일을 읽으십시오:
1. `docs/product.md`: 제품 목적, 사용자, 범위, 성공 기준
2. `docs/tech-stack.md`: 기술 스택 및 제약 사항
3. `docs/workflow.md`: 작업 프로토콜 및 검증 규칙
4. 활성 트랙 정보: `docs/tracks.md` 및 해당 트랙의 `spec.md`, `plan.md`

## 에이전트 의무
- 파일을 수정하기 전에 사용할 흐름(`quick-change` 또는 `start-track`)을 사용자에게 짧게 알리십시오.
- 파일을 수정하기 전에 `main`이 아닌 작업 브랜치에 있는지 확인하고, 필요하면 먼저 작업 브랜치를 만드십시오.
- 주요 작업 시작 전과 PR 생성 전 `git fetch origin main`으로 원격 상태를 확인하십시오.
- 파일을 수정하기 전에 이번 작업의 검증 방법을 말하십시오. 코드 변경은 자동화 테스트를 우선합니다.
- 여러 단계를 한 번에 진행하더라도 `validate-change` 전에는 변경 요약, 검증 결과, 남은 이슈를 정리하십시오.
- 구현 전 `spec.md`와 `plan.md`를 동기화하고 확인하십시오.
- 기술 선택이나 제약이 바뀌는 경우 `docs/tech-stack.md`를 업데이트하십시오.
- 코드 변경 시 관련 `docs/code_styleguides/` 문서를 확인하고 규칙을 따라야 합니다.

## 작업 시작 선언
에이전트는 파일을 수정하기 전에 아래 내용을 먼저 사용자에게 알립니다:

- 사용할 흐름: `quick-change` 또는 `start-track`
- 작업 브랜치 생성 여부
- `origin/main` 확인 여부
- 예상 검증 방법
- 다음에 따를 스킬 순서
