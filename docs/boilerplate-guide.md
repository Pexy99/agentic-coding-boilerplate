# Boilerplate Guide

이 저장소는 가능한 한 스킬 중심으로 사용합니다. 사람이 처음부터 문서를 하나씩 수동 작성하는 흐름을 기본값으로 두지 않습니다.

## 기본 원칙

- 새 프로젝트 시작은 `/init-project`
- 작은 수정은 `/quick-change`
- 기능, 버그, 구조 변경은 `/start-track`
- 구현은 `/implement-track`
- 검증은 `/validate-change`
- PR 준비는 `/prepare-pr`

각 스킬은 한 단계만 담당합니다. 다음 단계는 제안만 하고 자동으로 이어서 수행하지 않습니다.

## 프로젝트 초기화

초기화는 가능한 한 `/init-project` 하나로 끝내는 것을 기본값으로 둡니다.

`/init-project`는 최소한 아래 항목을 한 번에 초안화하거나 갱신해야 합니다.

- 루트 `README.md`
- `docs/product.md`
- `docs/tech-stack.md`
- 구조 규칙과 스캐폴딩 결정
- 기본 검증 기준
- 사람이 직접 해야 하는 설정이 있으면 `docs/project-setup.md`의 TODO
- 배포 대상이 정해져 있으면 `docs/deployment.md`의 초안 또는 TODO

초기화 이후 기본 동작은 "문서를 추가로 많이 작성"하는 것이 아니라 "생성된 초안을 검토하고 필요한 부분만 고치는 것"입니다.

초기 흐름:

1. `/init-project` 실행
2. 생성된 초안 검토
3. 사실과 다른 부분만 수정
4. 바로 `quick-change` 또는 `start-track`으로 진행

즉, 기본 흐름은 `init-project -> 검토 -> 작업 시작`입니다.

## 프로젝트 구조

구조 규칙은 자유방임으로 두지 않습니다.

- 기술 선택은 `docs/tech-stack.md`
- 작업 규칙은 `docs/workflow.md`
- 가능한 경우 공식 CLI 또는 스캐폴더를 우선 사용
- 앱 코드는 문서화된 위치에만 둠. 예: `src/`
- 루트에는 문서, 설정 파일, 전역 엔트리만 둠

## 문서 사용 방식

문서는 스킬이 먼저 초안을 만들고, 사람이 사실 여부를 검토하는 방식으로 유지합니다.

- 전역 문서 초안: `/init-project`
- 트랙 문서 초안: `/start-track`
- ADR 문서 초안: `/write-adr`

사람이 직접 해야 하는 설정이나 운영 정보는 문서에 TODO로 남기고, 가능한 한 스킬이 먼저 뼈대를 만듭니다.

## 검증 원칙

검증도 가능한 한 스킬 중심으로 진행합니다.

- 구현 후 검증은 `/validate-change`
- UI는 전체 E2E 남발보다 핵심 경로와 수동 검증 체크리스트를 우선
- 결정론적인 테스트는 자동화를 우선
- PR 준비 전에는 기본적으로 `/validate-change`를 먼저 수행

## GitHub 설정과 운영

GitHub 설정, 권한, 브랜치 보호처럼 사람이 직접 적용해야 하는 항목은 [project-setup.md](/Users/ahyun/work/ai-dev/agentic-coding-boilerplate/docs/project-setup.md)에 둡니다.

배포 환경, 시크릿, 롤백 기준처럼 프로젝트별로 달라지는 운영 정보는 [deployment.md](/Users/ahyun/work/ai-dev/agentic-coding-boilerplate/docs/deployment.md)에 둡니다.

즉, 보일러플레이트의 기본 철학은 다음과 같습니다.

- 가능한 한 스킬이 초안을 만든다
- 문서는 스킬 결과를 검토하는 용도로 쓴다
- 사람이 직접 해야 하는 설정만 별도 문서에 남긴다
