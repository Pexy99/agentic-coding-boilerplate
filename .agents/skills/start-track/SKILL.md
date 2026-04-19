# Skill: Start New Track

이 스킬은 새로운 개발 트랙을 초기화하는 과정을 자동화합니다.

## Workflow
1. `docs/tracks.md`에 새 엔트리 추가.
2. `docs/tracks/<track_id>/` 디렉터리 생성.
3. 기본 `spec.md`, `plan.md`, `metadata.json` 템플릿 생성.

## Prompt Template
"새로운 트랙 '<description>'을(를) 생성해줘. ID는 <track_id>로 해줘."