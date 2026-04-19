---
name: prepare-pr
description: Prepare and optionally open a pull request by validating changes, summarizing work, checking commit rules, and filling the PR template.
---

# Skill: Prepare PR

이 스킬은 PR을 만들기 직전에 변경사항을 정리하고 PR 본문을 준비할 때 사용합니다.

## Workflow
1. 현재 브랜치가 `main`이 아닌지 확인합니다.
2. `git status`로 커밋되지 않은 변경이 있는지 확인합니다.
3. 커밋되지 않은 변경이 있으면 `save-work` 사용을 제안합니다.
4. `validate-change`로 PR 전 점검을 수행합니다.
5. 변경 요약, 관련 트랙, 검증 결과를 정리합니다.
6. `.github/pull_request_template.md` 형식에 맞춰 PR 본문을 작성합니다.
7. PR 제목을 `CONTRIBUTING.md`의 type 규칙에 맞게 제안합니다.
8. GitHub CLI 또는 GitHub 앱을 사용할 수 있으면 사용자 확인 후 PR을 생성합니다.
9. 자동 생성이 불가능하면 PR 제목과 본문을 출력해 사용자가 직접 생성할 수 있게 합니다.

## Rules
- `main` 브랜치에서는 PR을 만들지 않습니다.
- `main`에 직접 push하지 않습니다.
- merge는 하지 않습니다.
- 리뷰 승인, CI 통과, branch protection을 우회하지 않습니다.
- PR 전 `validate-change`를 반드시 수행합니다.
- PR 본문에는 검증 결과와 남은 이슈를 숨기지 않습니다.

## Output
- PR 제목
- PR 본문
- 검증 요약
- 리뷰어가 확인해야 할 항목
- 생성된 PR 링크, 생성한 경우
