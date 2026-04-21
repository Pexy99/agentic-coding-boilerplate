# Agentic Coding Boilerplate

이 프로젝트는 사람과 다양한 AI 에이전트(Claude, GPT, Gemini 등)가 협업하여 소프트웨어를 개발하기 위한 **문서 주도 개발(Document-Driven Development)** 보일러플레이트입니다.

실제 프로젝트를 시작하면 이 README는 프로젝트 소개와 실행 방법으로 교체하십시오. 보일러플레이트 사용법은 [docs/boilerplate-guide.md](./docs/boilerplate-guide.md)에 보관되어 있습니다.

## 핵심 철학
- **Shared Context**: 제품 맥락, 기술 선택, 작업 규칙은 `docs/` 아래의 마크다운 문서에 기록됩니다.
- **Agent-Agnostic**: 특정 도구에 종속되지 않으며, 어떤 AI 모델과도 협업 가능한 어댑터 레이어를 제공합니다.
- **Track-Based When Useful**: 기능, 버그, 구조 변경처럼 맥락 공유가 필요한 작업은 트랙(Track)으로 관리합니다.

## 프로젝트 초기화
새 프로젝트를 시작할 때 가장 먼저 공통 문맥을 채웁니다.

1. `/init-project`로 전역 문맥을 초기화합니다.
2. `docs/product.md`에 제품 목적, 사용자, 범위, 성공 기준을 작성합니다.
3. `docs/tech-stack.md`에 사용할 기술과 제약을 작성합니다.
4. `docs/project-setup.md`를 따라 GitHub 브랜치 보호와 required check를 설정합니다.
5. 개발은 `CONTRIBUTING.md`의 스킬 흐름에 따라 진행합니다.
6. 배포 대상이 정해졌다면 `docs/deployment.md`에 배포 환경과 절차를 작성합니다.

## 작업 시작
이미 초기화된 프로젝트에서 작업을 시작할 때는 다음 문서를 확인합니다.

1. `docs/workflow.md`에서 작업 크기와 검증 규칙을 확인합니다.
2. `docs/tracks.md`에서 활성 트랙을 확인합니다.
3. 새 작업, 구현, 중간 커밋, 검증, PR 준비는 `CONTRIBUTING.md`의 스킬 사용 순서를 따릅니다.

## 협업 가이드
자세한 운영 규칙과 작업 프로세스는 [CONTRIBUTING.md](./CONTRIBUTING.md)를 확인해 주세요. 에이전트를 위한 안내는 [AGENTS.md](./AGENTS.md)에 별도로 정리되어 있습니다.

프로젝트 생성 후 GitHub 브랜치 보호, required check, 팀 권한 설정은 [docs/project-setup.md](./docs/project-setup.md)를 따라 적용합니다.
