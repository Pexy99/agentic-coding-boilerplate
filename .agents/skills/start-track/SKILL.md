---
name: start-track
description: Create a new work track by copying docs/tracks/_template, initializing spec.md and plan.md, and registering it in docs/tracks.md.
---

# Skill: Start New Track

이 스킬은 새로운 개발 트랙을 초기화하는 과정을 자동화합니다.

## Workflow
1. `git fetch origin main`으로 원격 `main` 상태를 확인합니다.
2. 현재 브랜치가 `main`이면 코드를 수정하기 전에 작업 브랜치를 만듭니다. 예: `git checkout -b feat/login_20260419`.
3. 현재 브랜치가 이미 작업 브랜치라면 브랜치명이 트랙 ID의 type과 맞는지 확인합니다.
4. `docs/tracks.md`에 새 엔트리 추가.
5. `docs/tracks/<track_id>/` 디렉터리 생성 (ID 형식: `<type>_<short_name>_<YYYYMMDD>`, 예: `feat_login_20260419`).
6. `docs/tracks/_template/`의 파일들을 새 디렉터리로 복사.
7. `spec.md`, `plan.md`를 요청된 내용에 맞게 초기화.

## Branch Rules
- 트랙 파일이나 코드를 수정하기 전에 반드시 `main`이 아닌 작업 브랜치에 있어야 합니다.
- 로컬 `main`에서 바로 문서나 코드를 수정하지 않습니다.
- 원격 `main`이 없거나 fetch가 실패하면 작업을 계속하기 전에 사용자에게 상태를 알립니다.

## Interactive Fill
요청에 트랙 목표, 범위, 완료 기준, 검증 방법이 부족하면 빈 템플릿을 그대로 만들지 말고 먼저 짧게 질문합니다.

질문은 최대 4개로 제한합니다:
1. 이 트랙의 목표는 무엇인가요?
2. 이번에 포함할 것과 제외할 것은 무엇인가요?
3. 완료됐다고 판단할 기준은 무엇인가요?
4. 어떤 자동화 테스트로 확인할까요? 어렵다면 수동 검증이 필요한 이유는 무엇인가요?

사용자가 답한 내용으로 `spec.md`와 `plan.md`를 채웁니다. 사용자가 답을 모르면 `TODO:`로 표시하되, `plan.md`에 "TODO 정리" 항목을 추가합니다.

## Prompt Template
"새로운 트랙 '<description>'을(를) 생성해줘. ID는 <track_id>로 해줘."
