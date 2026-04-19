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
- 구현 전 `spec.md`와 `plan.md`를 동기화하고 확인하십시오.
- 기술 선택이나 제약이 바뀌는 경우 `docs/tech-stack.md`를 업데이트하십시오.
- 코드 변경 시 관련 `docs/code_styleguides/` 문서를 확인하고 규칙을 따라야 합니다.
