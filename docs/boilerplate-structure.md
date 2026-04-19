# Boilerplate Structure

본 보일러플레이트는 효율적인 **에이전트-인간 협업 워크플로우** 구축에 집중합니다.

## 1. Root Layer
- `README.md`, `CONTRIBUTING.md`: 사람을 위한 프로젝트 진입점.
- `AGENTS.md`, `CLAUDE.md`, `GEMINI.md`: AI 에이전트용 로더 (Adapter Layer).

## 2. Docs Layer (Source of Truth)
- `docs/product.md`, `tech-stack.md`, `workflow.md`: 프로젝트의 핵심 지식.
- `docs/tracks/`: 활성화된 작업(Track)별 명세와 플랜 관리.
- `docs/tracks/_template/`: 새 트랙 생성을 위한 표준 템플릿.

## 3. Agent Layer
- `.agents/skills/`: 에이전트 전용 반복 작업 스킬.

## 4. Source Code Layer (TBD)
*본 보일러플레이트에는 기본 소스 코드가 포함되어 있지 않습니다.*
- 트랙 구현이 시작되면 `src/` (애플리케이션) 및 `tests/` (테스트) 폴더가 생성됩니다.
- 초기 폴더 구조는 첫 번째 트랙의 실행 계획에 따라 결정됩니다.
