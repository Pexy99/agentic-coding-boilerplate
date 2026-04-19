# Conductor Protocol (Agent-Agnostic Workflow)

## 1. 개요
이 프로젝트는 **문서 주도 개발(Document-Driven Development)** 방법론을 따릅니다. 모든 협업자(인간 및 AI)는 본 문서의 규칙을 준수해야 합니다.

## 2. 핵심 원칙 (Core Principles)
1. **Plan as Source of Truth**: 모든 실행 상태는 `docs/tracks/<id>/plan.md`에 기록됩니다.
2. **Spec Before Code**: 구현 전 상세 명세(`spec.md`)가 반드시 확정되어야 합니다.
3. **Standardized Hand-over**: 에이전트 교체 시 `plan.md`와 `git notes`를 통해 맥락을 동기화합니다.
4. **TDD (Test-Driven Development)**: 기능 구현 전 실패하는 테스트 작성을 권장합니다.

## 3. 작업 프로세스 (Task Lifecycle)

### [Step 1] 맥락 파악 및 작업 선택
- `docs/tracks.md`에서 활성화된 트랙을 확인합니다.
- 해당 트랙의 `plan.md`에서 다음 작업(`[ ]`)을 선택합니다.

### [Step 2] 작업 시작 표시
- `plan.md`에서 해당 항목을 `[~]` (In Progress)로 변경합니다.

### [Step 3] TDD Cycle (Red-Green-Refactor)
- **Red**: 요청된 기능을 검증하는 실패하는 테스트를 작성합니다.
- **Green**: 테스트를 통과시키는 최소한의 코드를 작성합니다.
- **Refactor**: 코드 품질을 개선하고 테스트 재실행을 확인합니다.

### [Step 4] 작업 완료 및 기록
1. **커밋**: 원자적 단위로 커밋합니다. (예: `feat(core): ...`)
2. **Git Notes (선택)**: 상세 사유가 필요한 경우 `git notes add -m "<Summary>"`를 사용합니다.
3. **Plan 업데이트**: `plan.md`의 상태를 `[x]`로 변경하고 커밋 해시(Short SHA)를 병기합니다.

## 4. 품질 게이트 (Quality Gates)
태스크 완료 전 다음 사항을 자가 점검합니다:
- [ ] 모든 테스트 통과 여부
- [ ] 코드 커버리지 확인 (목표 >80%, 작은 팀의 경우 핵심 로직 우선)
- [ ] 관련 코드 스타일 가이드 준수 (`docs/code_styleguides/` 참조)
- [ ] `docs/` 내 관련 문서(Spec, Tech-stack 등) 업데이트 여부

## 5. 단계별 검증 프로토콜 (Phase Verification)
각 단계(Phase) 완료 시 전체 테스트를 실행하고 체크포인트 커밋(`conductor(checkpoint): ...`)을 생성합니다.
