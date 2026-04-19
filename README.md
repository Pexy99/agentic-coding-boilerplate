# Agentic Coding Boilerplate

이 프로젝트는 사람과 다양한 AI 에이전트(Claude, GPT, Gemini 등)가 협업하여 소프트웨어를 개발하기 위한 **문서 주도 개발(Document-Driven Development)** 보일러플레이트입니다.

## 핵심 철학
- **Source of Truth**: 모든 의사결정과 계획은 `docs/` 아래의 마크다운 문서에 기록됩니다.
- **Agent-Agnostic**: 특정 도구에 종속되지 않으며, 어떤 AI 모델과도 협업 가능한 어댑터 레이어를 제공합니다.
- **Track-Based**: 모든 작업은 '트랙(Track)'이라는 단위로 관리되어 문맥의 파편화를 방지합니다.

## 빠른 시작
1. `docs/workflow.md`를 읽고 작업 프로토콜을 이해합니다.
2. `docs/tech-stack.md`에서 기술 제약을 확인합니다.
3. 새로운 작업을 시작하려면 `CONTRIBUTING.md`를 참조하십시오.

## 협업 가이드
자세한 운영 규칙과 작업 프로세스는 [CONTRIBUTING.md](./CONTRIBUTING.md)를 확인해 주세요. 에이전트를 위한 안내는 [AGENTS.md](./AGENTS.md)에 별도로 정리되어 있습니다.