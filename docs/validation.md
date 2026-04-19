# Validation Strategy

## 검증 원칙
- 모든 코드는 자동화된 테스트에 의해 검증되어야 합니다.
- 수동 검증(Manual Verification)은 자동화가 어려운 UI/UX 영역에 집중합니다.

## 테스트 기준
1. **Unit Tests**: 개별 함수 및 클래스 단위 검증 (커버리지 >80% 목표).
2. **Integration Tests**: 컴포넌트 간 상호작용 검증.
3. **E2E Tests**: 주요 사용자 시나리오 전체 흐름 검증.

## 품질 게이트
- `ruff`를 통한 린트 및 포맷팅 검사 통과.
- `pytest`를 통한 모든 테스트 통과.
- PR 리뷰 시 `docs/workflow.md` 준수 여부 확인.