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
- CI 검사 추가 기준은 `docs/ci.md`를 따릅니다.

## Project Structure
- 앱 코드는 가능하면 `src/` 아래에 둡니다.
- 루트에는 설정 파일, 문서, 빌드 진입점처럼 프로젝트 전역 파일만 둡니다.
- 테스트 디렉터리는 프레임워크 기본값을 따르되, 팀이 합의한 위치를 문서에 고정합니다.
- 구조 규칙이 필요하면 여기와 `docs/workflow.md`를 함께 업데이트합니다.

## Scaffolding
- 새 프로젝트 초기 생성은 가능하면 공식 CLI 또는 공식 스캐폴더를 사용합니다.
- 예:
  - Vite: `npm create vite@latest`
  - Next.js: `npx create-next-app@latest`
  - Django: `django-admin startproject`
  - FastAPI: 팀 템플릿 또는 공식 예제를 기준으로 시작
- 에이전트가 임의로 루트 구조를 만드는 것보다, 공식 생성기로 시작한 뒤 필요한 규칙만 추가하는 방식을 우선합니다.

## Code Style Guides
- [예: `docs/code_styleguides/python.md`]
- 새 언어나 프레임워크를 도입하면 `docs/code_styleguides/README.md`를 따라 스타일가이드를 추가합니다.

## Architecture Principles
- **Modular Monolith**: 관심사 분리를 위한 모듈화된 모놀리스 구조 지향.
- **Strict Typing**: 모든 인터페이스와 데이터 모델에 정적 타입 적용.
