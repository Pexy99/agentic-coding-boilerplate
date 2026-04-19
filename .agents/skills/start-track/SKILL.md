---
name: start-track
description: Create a new work track by copying docs/tracks/_template, initializing spec.md and plan.md, and registering it in docs/tracks.md.
---

# Skill: Start New Track

이 스킬은 새로운 개발 트랙을 초기화하는 과정을 자동화합니다.

## Workflow
1. `docs/tracks.md`에 새 엔트리 추가.
2. `docs/tracks/<track_id>/` 디렉터리 생성 (ID 형식: `<type>_<short_name>_<YYYYMMDD>`, 예: `feat_login_20260419`).
3. `docs/tracks/_template/`의 파일들을 새 디렉터리로 복사.
4. `spec.md`, `plan.md`를 요청된 내용에 맞게 초기화.

## Interactive Fill
요청에 트랙 목표, 범위, 완료 기준, 검증 방법이 부족하면 빈 템플릿을 그대로 만들지 말고 먼저 짧게 질문합니다.

질문은 최대 4개로 제한합니다:
1. 이 트랙의 목표는 무엇인가요?
2. 이번에 포함할 것과 제외할 것은 무엇인가요?
3. 완료됐다고 판단할 기준은 무엇인가요?
4. 테스트 또는 수동 검증은 어떻게 확인할까요?

사용자가 답한 내용으로 `spec.md`와 `plan.md`를 채웁니다. 사용자가 답을 모르면 `TODO:`로 표시하되, `plan.md`에 "TODO 정리" 항목을 추가합니다.

## Prompt Template
"새로운 트랙 '<description>'을(를) 생성해줘. ID는 <track_id>로 해줘."
