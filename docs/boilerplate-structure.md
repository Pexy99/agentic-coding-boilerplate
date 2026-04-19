# Boilerplate Structure

이 저장소의 디렉터리 및 파일 역할 정의입니다.

## 1. Root Layer
- `README.md`: 프로젝트 소개.
- `CONTRIBUTING.md`: 사람을 위한 운영 및 협업 가이드.
- `AGENTS.md`, `CLAUDE.md`, `GEMINI.md`: 에이전트용 로더 (Adapter Layer).

## 2. Docs Layer (Source of Truth)
- `product.md`: 제품 비전 및 비즈니스 목표.
- `tech-stack.md`: 기술 스택, 라이브러리 제약, 아키텍처 원칙.
- `workflow.md`: TDD, 커밋 컨벤션, 검증 프로토콜 등 실제 작업 규칙.
- `tracks.md`: 전체 작업 목록 및 상태 관리.
- `tracks/`: 각 개별 트랙(기능/버그)의 명세와 플랜이 담긴 공간.
- `architecture.md`: 고수준 시스템 설계도.
- `validation.md`: 테스트 및 품질 검증 기준.
- `adr/`: 아키텍처 결정 기록 (Architecture Decision Records).

## 3. Agent Layer
- `.agents/skills/`: 에이전트가 반복적으로 수행하는 작업(예: 트랙 생성, ADR 작성 등)을 위한 자동화 스크립트 및 스킬 정의 공간.

## 4. Source Code Layer
- `src/`: 실제 애플리케이션 코드.
- `tests/`: 테스트 코드.