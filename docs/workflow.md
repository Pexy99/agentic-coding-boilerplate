# Conductor Protocol (Agent-Agnostic Workflow)

## 1. 개요
이 프로젝트는 **Conductor 방법론**을 따릅니다. 이 워크플로우는 특정 AI 에이전트(Gemini, Claude, GPT 등)에 종속되지 않으며, 모든 협업자(인간 및 AI)가 동일한 규칙에 따라 코드를 작성하고 관리하는 것을 목표로 합니다.

## 2. 핵심 원칙 (Core Principles)
1. **Plan as Source of Truth:** 모든 작업의 시작과 끝은 `conductor/tracks/<id>/plan.md`에 기록됩니다.
2. **Standardized Hand-over:** AI 모델을 교체하거나 인간이 이어받을 때, `plan.md`의 상태와 `git notes`를 통해 즉시 맥락을 동기화합니다.
3. **TDD (Test-Driven Development):** 기능 구현 전 반드시 실패하는 테스트를 먼저 작성합니다.
4. **Git-Centric Documentation:** 작업 요약(Summary)은 커밋 메시지나 Git Notes에 저장하여 히스토리를 코드와 함께 관리합니다.

## 3. 작업 프로세스 (Task Lifecycle)

모든 작업자는 다음 단계를 엄격히 준수합니다:

### [Step 1] 맥락 파악 및 작업 선택
- `conductor/index.md`를 읽어 프로젝트 전체 구조를 파악합니다.
- `conductor/tracks.md`에서 활성화된 트랙을 확인하고, 해당 트랙의 `plan.md`에서 다음 작업(`[ ]`)을 선택합니다.

### [Step 2] 작업 시작 표시
- `plan.md`에서 해당 항목을 `[~]` (In Progress)로 변경합니다.

### [Step 3] TDD Cycle
- **Red:** 요청된 기능을 검증하는 실패하는 테스트를 작성합니다.
- **Green:** 테스트를 통과시키는 최소한의 코드를 작성합니다.
- **Refactor:** 코드 품질을 개선하고 테스트 재실행을 통해 무결성을 확인합니다.

### [Step 4] 작업 완료 및 기록
1. **코드 커밋:** 원자적 단위로 커밋합니다. (예: `feat(core): ...`)
2. **작업 요약 기록:** `git notes add -m "<Summary>"`를 사용하여 해당 커밋에 상세 구현 내용, 변경 파일, 결정 사유를 기록합니다.
3. **Plan 업데이트:** `plan.md`의 상태를 `[x]`로 변경하고 옆에 커밋 해시(Short SHA)를 기록합니다.

## 4. 에이전트 간 협업 (Cross-Agent Collaboration)

다른 AI 모델(Claude, ChatGPT 등)에게 작업을 요청할 때는 다음 프롬프트를 함께 제공하십시오:

> "이 프로젝트는 `conductor/` 폴더에 정의된 워크플로우를 따릅니다. 
> 1. `conductor/index.md`를 먼저 분석해줘.
> 2. `plan.md`의 규칙에 따라 작업을 진행하고, 완료 후에는 `git notes`에 요약을 남겨줘.
> 3. 모든 코드 변경은 테스트가 동반되어야 해."

## 5. 단계별 검증 프로토콜 (Phase Verification)
각 단계(Phase)가 끝날 때마다 다음을 수행합니다:
1. 전체 테스트 실행 및 커버리지 확인 (>80%).
2. `conductor/workflow.md`의 'Quality Gates' 체크리스트 확인.
3. 체크포인트 커밋 생성 (`conductor(checkpoint): ...`).
