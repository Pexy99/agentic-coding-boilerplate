# Project Setup Checklist

이 문서는 새 프로젝트에서 사람이 직접 설정해야 하는 항목을 정리합니다. 저장소 문서와 템플릿만으로 자동 적용되지 않는 GitHub 설정을 포함합니다.

## Related Guides

- 보일러플레이트 사용법: `docs/boilerplate-guide.md`
- 팀 작업 흐름: `CONTRIBUTING.md`
- 제품 문맥: `docs/product.md`
- 기술 스택: `docs/tech-stack.md`
- CI 기준: `docs/ci.md`
- 배포 절차: `docs/deployment.md`
- 코드 스타일가이드 추가: `docs/code_styleguides/README.md`

## 1. Project Context

먼저 프로젝트의 공통 문맥을 채웁니다. 이 단계가 끝나기 전에는 기능 구현을 시작하지 않습니다.

- `docs/product.md`: 제품 목적, 사용자, 범위, 성공 기준
- `docs/tech-stack.md`: 사용할 언어, 프레임워크, 데이터 저장소, 도구
- `docs/code_styleguides/`: 선택한 언어와 프레임워크의 코드 스타일 규칙
- `docs/deployment.md`: 배포 대상, 환경 변수, 배포/롤백 절차

## 2. GitHub Branch Protection

`main` 브랜치에 보호 규칙을 설정합니다.

- `main` 직접 push 금지
- PR을 통한 병합 필수
- 최소 1명 리뷰 승인 필수
- GitHub Actions `CI` 통과 필수
- force push 금지
- branch 삭제 금지

초기 팀에서는 리뷰 승인 1명으로 시작하고, 병목이 생기지 않는지 확인합니다.

## 3. Required Status Check

GitHub 저장소 설정에서 `.github/workflows/ci.yml`의 `CI` 체크를 required status check로 등록합니다.

현재 CI는 필수 문서 존재 여부만 확인합니다. 실제 코드가 생기면 프로젝트 기술 스택에 맞춰 테스트와 린트를 추가합니다.

예:
- Python: `ruff check .`, `ruff format --check .`, `pytest`
- Node.js: `npm run lint`, `npm test`

CI에 어떤 검사를 추가할지는 `docs/ci.md`를 기준으로 결정합니다.

## 4. Repository Access

팀원 권한은 최소 권한으로 시작합니다.

- 일반 팀원: Write
- 병합/설정 담당자: Maintain 이상
- 외부 협력자: 필요 시 제한된 권한 부여

## 5. GitHub Recommended Settings

GitHub 저장소를 만든 뒤 아래 설정을 확인합니다.

### Branch Protection for `main`
- [ ] Require a pull request before merging
- [ ] Require at least 1 approval
- [ ] Dismiss stale pull request approvals when new commits are pushed
- [ ] Require status checks to pass before merging
- [ ] Required check: `CI`
- [ ] Block force pushes
- [ ] Block branch deletion

### Merge Settings
- [ ] Enable squash merge
- [ ] Set squash merge as default
- [ ] Disable merge commits, if the team wants a cleaner `main` history
- [ ] Rebase merge is optional

### Automation
- [ ] Keep `.github/workflows/ci.yml` required on PRs
- [ ] Add real lint/test commands when project code is added
- [ ] Keep `.github/pull_request_template.md` enabled
- [ ] Review `docs/ci.md` when adding a new language or framework

### Secrets and Environments
- [ ] Store secrets only in the deployment platform or GitHub Secrets
- [ ] Do not commit `.env` files or real credentials
- [ ] Document required environment variables in `docs/deployment.md`
- [ ] Give production secret access only to maintainers

## 6. Team Communication Rule

문서 충돌이나 작업 범위 충돌이 나면 혼자 덮어쓰지 않습니다.

- 충돌 파일
- 본인이 하려던 변경
- 최신 `main` 기준 재정리 계획

위 내용을 팀 채널에 공유한 뒤 정리합니다.

## 7. Before First Feature Work

첫 기능 작업 전에 다음을 확인합니다.

- `docs/product.md`가 실제 프로젝트 목적에 맞게 수정됨
- `docs/tech-stack.md`가 실제 기술 스택에 맞게 수정됨
- 필요한 코드 스타일가이드가 `docs/code_styleguides/`에 추가됨
- 배포 대상이 정해졌다면 `docs/deployment.md`가 수정됨
- `docs/tracks.md`에 활성 트랙이 등록됨
- 필요 시 `.github/workflows/ci.yml`에 실제 테스트/린트 명령 추가
