# Skill: Start New Track

이 스킬은 새로운 개발 트랙을 초기화하는 과정을 자동화합니다.

## Workflow
1. `docs/tracks.md`에 새 엔트리 추가.
2. `docs/tracks/<track_id>/` 디렉터리 생성 (ID 형식: `name_YYYYMMDD`).
3. `docs/tracks/_template/`의 파일들을 새 디렉터리로 복사.
4. `metadata.json`, `spec.md`, `plan.md`를 요청된 내용에 맞게 초기화.

## Prompt Template
"새로운 트랙 '<description>'을(를) 생성해줘. ID는 <track_id>로 해줘."
