# CI Guide

이 문서는 CI에서 무엇을 검사할지 결정하는 기준을 정리합니다. 처음에는 가볍게 시작하고, 실제 코드가 생기면 프로젝트 기술 스택에 맞춰 점진적으로 추가합니다.

## 기본 원칙

- CI는 PR에서 빠르게 피드백을 주는 수준으로 시작합니다.
- `main` 브랜치 보호 규칙에서 CI 통과를 required check로 설정합니다.
- 자동화할 수 있는 검증은 CI로 옮기고, 사람이 판단해야 하는 내용은 PR 리뷰에 남깁니다.
- 새 언어나 프레임워크를 도입하면 `docs/tech-stack.md`와 관련 코드 스타일가이드를 함께 업데이트합니다.

## 현재 CI

현재 `.github/workflows/ci.yml`은 다음을 확인합니다.

1. 필수 문서 존재 여부
2. Markdown lint
3. YAML lint

문서 존재 확인 단계에는 `set -euo pipefail`을 사용합니다. 이후 shell 체크가 늘어나도 실패를 조기에 드러내기 위한 기본 설정입니다.

Markdown/YAML 검사는 Super-Linter를 사용합니다. 이 보일러플레이트는 코드가 없는 상태에서도 문서와 GitHub Actions 설정 품질을 먼저 잡는 것을 목표로 합니다.

Markdown과 YAML lint 설정은 아래 파일에서 관리합니다.

- `.markdown-lint.yml`
- `.yaml-lint.yml`

## 코드가 생기면 추가할 것

프로젝트 기술 스택이 정해지면 아래 중 필요한 항목을 CI에 추가합니다.

### Python
- `ruff check .`
- `ruff format --check .`
- `pytest`

### Node.js / TypeScript
- `npm run lint`
- `npm test`
- `npm run build`

### 기타
- Docker 이미지 빌드
- 데이터베이스 마이그레이션 검증
- 배포 preview 생성

## 추가 기준

다음 조건 중 하나에 해당하면 CI 검사를 추가합니다.

- 사람이 반복해서 확인하는 작업이다.
- 실패하면 PR 병합 전에 반드시 알아야 한다.
- 포맷, 린트, 테스트처럼 자동화가 쉽다.
- AI가 자주 실수하는 영역이다.

반대로 다음 항목은 CI보다 PR 리뷰나 문서 체크리스트에 둡니다.

- 제품 방향 판단
- UI/UX 선호도
- 팀 합의가 필요한 기술 선택
- 외부 서비스 비용이나 권한 결정
