# Agent Loader

이 저장소는 **문서 주도(Document-Driven) 워크플로우**를 사용합니다. 모든 작업은 `docs/` 아래의 문서를 기준으로 수행되어야 합니다.

## Source of Truth
- 모든 프로젝트 문맥과 실행 계획은 `docs/`에 있습니다. 루트 파일들은 진입점 역할만 합니다.

## 필수 확인 순서 (Read First)
작업 시작 전 다음 순서대로 파일을 읽으십시오:
1. `docs/workflow.md`: 작업 프로토콜 및 TDD 규칙
2. `docs/tech-stack.md`: 기술 스택 및 제약 사항
3. `docs/product.md`: 제품 비전
4. 현재 활성화된 트랙의 `spec.md` 및 `plan.md`

## 에이전트 의무
- 구현 전 `spec.md`와 `plan.md`를 동기화하고 확인하십시오.
- 기술적 변경 시 `docs/tech-stack.md`를 먼저 업데이트하십시오.
- 작업 완료 후 `git notes`를 통해 요약을 남기십시오 (상세 내용은 `workflow.md` 참조).
- 모든 코드는 `docs/code_styleguides/`의 규칙을 따라야 합니다.