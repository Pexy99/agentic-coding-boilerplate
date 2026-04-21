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

`docs/product.md` 또는 `docs/tech-stack.md`가 템플릿 상태라면 기능 작업을 시작하지 말고 먼저 `init-project` 흐름으로 전역 문맥을 초기화하십시오.
루트 `README.md`가 여전히 보일러플레이트 소개 상태라면 실제 프로젝트 초기화가 끝난 것으로 보지 마십시오.

## 에이전트 의무
- 새 프로젝트에서 첫 작업을 시작하기 전 `docs/product.md`와 `docs/tech-stack.md`가 실제 프로젝트 내용으로 채워졌는지 확인하십시오.
- 파일을 수정하기 전에 사용할 흐름(`init-project`, `quick-change`, 또는 `start-track`)을 사용자에게 짧게 알리십시오.
- 스킬은 원자적 단계로 다루십시오. 한 스킬의 책임 범위를 넘어서 다음 스킬의 본 작업까지 진행하지 마십시오.
- 파일을 수정하기 전에 `main`이 아닌 작업 브랜치에 있는지 확인하고, 필요하면 먼저 작업 브랜치를 만드십시오.
- 주요 작업 시작 전과 PR 생성 전 `git fetch origin main`으로 원격 상태를 확인하십시오.
- 파일을 수정하기 전에 이번 작업의 검증 방법을 말하십시오. 코드 변경은 자동화 테스트를 우선합니다.
- 여러 단계를 한 번에 진행하더라도 `validate-change` 전에는 변경 요약, 검증 결과, 남은 이슈를 정리하십시오.
- 구현 전 `spec.md`와 `plan.md`를 동기화하고 확인하십시오.
- 구조 규칙이 정해진 프로젝트에서는 임의로 루트 구조를 만들지 말고 공식 스캐폴더와 문서화된 규칙을 따르십시오.
- 기술 선택이나 제약이 바뀌는 경우 `docs/tech-stack.md`를 업데이트하십시오.
- 코드 변경 시 관련 `docs/code_styleguides/` 문서를 확인하고 규칙을 따라야 합니다.
- UI 검증은 전체 E2E 자동화보다 핵심 경로 자동화와 사람용 검증 체크리스트를 우선하십시오.

## 작업 시작 선언
에이전트는 파일을 수정하기 전에 아래 내용을 먼저 사용자에게 알립니다:

- 사용할 흐름: `init-project`, `quick-change`, 또는 `start-track`
- 작업 브랜치 생성 여부
- `origin/main` 확인 여부
- 예상 검증 방법
- 다음에 따를 스킬 순서

## 단계 경계

- `start-track`은 트랙 시작 준비까지만 담당합니다.
- `implement-track`은 구현과 로컬 검증까지만 담당합니다.
- `validate-change`는 독립된 검증 단계로서 검증 결과와 리스크 정리까지만 담당합니다.
- `prepare-pr`는 PR 초안과 리뷰 준비까지만 담당합니다.
- 다음 단계는 `Recommended next step`으로만 제안하고, 사용자가 명시적으로 요청하지 않으면 자동 실행하지 않습니다.
