# Tech Stack

이 문서는 프로젝트의 기술 선택, 제약 사항 및 도입 근거를 관리합니다. 기술 선택이 바뀌는 작업에서는 이 문서를 함께 업데이트합니다.

## Language
- [예: Python 3.10+]

## Core Frameworks
- [예: Fast API, Typer]

## Data Persistence
- [예: PostgreSQL, Redis]

## Tooling & Infrastructure
- [예: uv, Pytest, Ruff]
- **CI/CD**: GitHub Actions
- **Deployment**: [예: Vercel, Render, Railway, AWS, GitHub Pages]

## Code Style Guides
- [예: `docs/code_styleguides/python.md`]
- 새 언어나 프레임워크를 도입하면 `docs/code_styleguides/README.md`를 따라 스타일가이드를 추가합니다.

## Architecture Principles
- **Modular Monolith**: 관심사 분리를 위한 모듈화된 모놀리스 구조 지향.
- **Strict Typing**: 모든 인터페이스와 데이터 모델에 정적 타입 적용.
