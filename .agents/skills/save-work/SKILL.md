---
name: save-work
description: Safely create an intermediate commit on a non-main development branch after checking changed files and commit message rules.
---

# Skill: Save Work

이 스킬은 현재 개발 브랜치에서 작업 중간 저장용 커밋을 만들 때 사용합니다.

## Workflow
1. 현재 브랜치가 `main`이 아닌지 확인합니다.
2. `git status`로 변경 파일을 확인합니다.
3. 변경 범위를 요약합니다.
4. 커밋에 포함할 파일을 확인합니다.
5. `CONTRIBUTING.md`의 type 규칙에 맞는 커밋 메시지를 제안합니다.
6. 사용자가 동의하면 커밋합니다.
7. 원격 브랜치 push가 필요하면 사용자 확인 후 push합니다.

## Rules
- `main` 브랜치에서는 커밋하지 않습니다.
- `main`에 직접 push하지 않습니다.
- force push는 하지 않습니다.
- 커밋 메시지는 `feat`, `fix`, `docs`, `refactor`, `test`, `chore` 중 하나로 시작합니다.
- 관련 트랙이 있으면 커밋 type을 트랙 ID의 type과 맞춥니다.
- WIP 커밋이 필요하면 `chore: save work in progress`처럼 명확히 작성합니다.
- PR 전에는 `validate-change`를 실행합니다.

## Output
- 커밋 해시
- 커밋 메시지
- 포함된 파일 요약
- 남은 작업
