---
name: start-track
description: Start a new track by creating its branch and initializing spec.md, plan.md, and the active track entry, then stop before implementation.
---

# Skill: Start New Track

## Purpose

이 스킬은 새 트랙을 시작하는 준비 단계까지만 담당합니다. 작업 브랜치를 준비하고, `docs/tracks.md`에 활성 트랙을 등록하고, `spec.md`와 `plan.md`를 초기화한 뒤 멈춥니다.

## Inputs

- `AGENTS.md`, `docs/product.md`, `docs/tech-stack.md`, `docs/workflow.md`를 읽은 상태
- 새 기능, 버그, 구조 변경처럼 트랙이 필요한 작업 요청
- 사용할 `track_id` 또는 트랙 설명

## Workflow

1. `git fetch origin main`으로 원격 `main` 상태를 확인합니다.
2. 현재 브랜치가 `main`이면 코드를 수정하기 전에 작업 브랜치를 만듭니다. 예: `git checkout -b feat/login_20260419`.
3. 현재 브랜치가 이미 작업 브랜치라면 브랜치명이 트랙 ID의 type과 맞는지 확인합니다.
4. `docs/tracks.md`에 새 엔트리를 추가합니다.
5. `docs/tracks/<track_id>/` 디렉터리를 만듭니다. ID 형식은 `<type>_<short_name>_<YYYYMMDD>`입니다.
6. `docs/tracks/_template/`의 파일들을 새 디렉터리로 복사합니다.
7. `spec.md`, `plan.md`를 요청된 내용에 맞게 초기화합니다.

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

## Outputs

- 생성된 작업 브랜치
- `docs/tracks.md`의 새 Active Track 엔트리
- 초기화된 `docs/tracks/<track_id>/spec.md`
- 초기화된 `docs/tracks/<track_id>/plan.md`

## Stop Condition

트랙 브랜치와 문서가 준비되면 멈춥니다. 구현, 검증, PR 준비는 이 스킬의 범위가 아닙니다.

## Recommended Next Step

일반적으로 다음 단계는 `implement-track`입니다. 단, 자동으로 실행하지 않고 다음 단계로만 제안합니다.

## Non-goals

- 코드를 구현하지 않습니다.
- `validate-change`를 실행하지 않습니다.
- `prepare-pr`를 수행하지 않습니다.
- 다음 스킬을 자동 호출하지 않습니다.
