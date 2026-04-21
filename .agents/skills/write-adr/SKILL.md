---
name: write-adr
description: Create or update one ADR for a significant decision and stop without implementing or validating the change itself.
---

# Skill: Write ADR

## Purpose

이 스킬은 되돌리기 어려운 결정이나 팀 합의가 필요한 결정을 ADR 문서로 기록하는 단계까지만 담당합니다.

## Inputs

- ADR이 필요할 정도의 결정
- 관련 트랙 또는 배경 정보
- 기존 ADR 목록

## When to Use

- DB, 인증, 배포, 프레임워크 변경
- 외부 서비스 또는 주요 라이브러리 도입
- 데이터 모델이나 API 계약 변경
- 팀 작업 방식에 영향을 주는 결정

작은 구현 세부사항이나 쉽게 되돌릴 수 있는 선택에는 ADR을 만들지 않습니다.

## Workflow

1. 결정이 ADR이 필요한 수준인지 확인합니다.
2. 기존 `docs/adr/` 문서를 확인해 중복 결정을 피합니다.
3. `docs/adr/0001-template.md`를 복사해 새 ADR 파일을 만듭니다.
4. 파일 이름은 `NNNN-short-title.md` 형식을 사용합니다. 예: `0002-use-postgresql.md`
5. Status, Date, Deciders를 채웁니다.
6. Context에는 왜 결정이 필요한지 적습니다.
7. Decision에는 선택한 결정을 짧고 명확하게 적습니다.
8. Consequences에는 장점, 단점, 후속 작업을 적습니다.
9. 관련 트랙이 있다면 `spec.md` 또는 `plan.md`에 ADR 링크를 남깁니다.

## Outputs

- 생성 또는 수정한 ADR 경로
- 결정 요약
- 남은 후속 작업

## Stop Condition

ADR 문서가 작성 또는 갱신되면 멈춥니다. 구현과 검증은 이 스킬의 범위가 아닙니다.

## Recommended Next Step

일반적으로 다음 단계는 관련 구현 스킬 또는 검증 스킬입니다. 단, 자동으로 실행하지 않고 다음 단계로만 제안합니다.

## Non-goals

- 구현을 하지 않습니다.
- 검증을 수행하지 않습니다.
- 다음 스킬을 자동 호출하지 않습니다.
