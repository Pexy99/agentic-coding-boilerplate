---
name: init-project
description: Initialize project-wide context documents and scaffolding decisions before any track starts, then stop before actual feature work.
---

# Skill: Init Project

## Purpose

이 스킬은 새 프로젝트의 전역 문맥, 루트 `README.md`, 구조 규칙을 초기화하는 단계까지만 담당합니다.

## Inputs

- 보일러플레이트를 실제 프로젝트로 쓰기 시작한 상태
- 루트 `README.md`가 아직 보일러플레이트 소개 상태이거나 미완성인 상태
- `docs/product.md` 또는 `docs/tech-stack.md`가 템플릿 상태이거나 미완성인 상태
- 프로젝트의 제품/기술/검증 정보

## When to Use

- 보일러플레이트를 실제 프로젝트로 처음 사용할 때
- `docs/product.md`나 `docs/tech-stack.md`가 템플릿 상태일 때
- 첫 트랙을 만들기 전에 제품 목적, 기술 스택, 검증 기준을 정해야 할 때

## Workflow

1. `AGENTS.md`, `README.md`, `docs/project-setup.md`를 읽습니다.
2. `docs/product.md`가 템플릿 상태인지 확인합니다.
3. `docs/tech-stack.md`가 템플릿 상태인지 확인합니다.
4. 루트 `README.md`가 아직 보일러플레이트 소개 상태인지 확인합니다.
5. 필요한 코드 스타일가이드가 `docs/code_styleguides/`에 있는지 확인합니다.
6. 사용할 공식 CLI 또는 스캐폴더가 있는지 확인합니다.
7. 프로젝트 구조 규칙을 `docs/tech-stack.md`와 `docs/workflow.md`에 맞게 정합니다.
8. CI 기준이 현재 기술 스택과 맞는지 `docs/ci.md`에서 확인합니다.
9. 배포 대상이 정해졌다면 `docs/deployment.md`를 확인합니다.
10. 정보가 부족하면 먼저 질문합니다.
11. 답변을 바탕으로 전역 문서를 짧게 채웁니다.
12. 루트 `README.md`를 프로젝트 소개와 실행 방법 중심으로 갱신합니다.
13. 공식 스캐폴더를 쓸 프로젝트라면 임의 구조 생성을 하기 전에 그 도구를 먼저 실행하도록 제안합니다.

## Questions

필요하면 아래 질문을 짧게 묻습니다.

1. 이 프로젝트가 해결하려는 문제는 무엇인가요?
2. 주요 사용자는 누구인가요?
3. 이번 버전에서 포함할 것과 제외할 것은 무엇인가요?
4. 사용할 언어, 프레임워크, 데이터 저장소는 무엇인가요?
5. 공식 CLI 또는 스캐폴더로 시작할 수 있나요? 가능하면 무엇을 쓰나요?
6. 앱 코드는 어디에 둘 건가요? 예: `src/`
7. lint, test, build 명령은 무엇인가요?
8. 배포 대상이 정해졌나요?
9. 루트 `README.md`에 가장 먼저 보여야 할 프로젝트 소개와 실행 방법은 무엇인가요?

## Rules

- `docs/product.md`와 `docs/tech-stack.md`가 템플릿 상태라면 기능 트랙을 시작하지 않습니다.
- 루트 `README.md`가 여전히 보일러플레이트 소개 상태라면 프로젝트 초기화가 끝났다고 보지 않습니다.
- 모르는 내용은 추측해서 확정하지 말고 `TODO:`로 남기거나 사용자에게 질문합니다.
- 전역 문서는 길게 쓰지 않고, 에이전트가 작업 판단에 필요한 만큼만 채웁니다.
- 루트 `README.md`는 실제 프로젝트 소개, 실행 방법, 핵심 링크를 우선 보여주도록 유지합니다.
- 기술 선택이 정해졌다면 관련 코드 스타일가이드를 추가하거나 TODO로 남깁니다.
- 공식 스캐폴더가 있는 프로젝트는 가능하면 그 도구를 우선 사용합니다.
- 구조 규칙이 정해지지 않은 상태에서 루트에 임의 파일을 만들지 않습니다.
- 코드가 생기기 전이라도 CI에서 무엇을 검사할지 `docs/ci.md` 기준으로 확인합니다.

## Outputs

- 초기화한 전역 문서
- 갱신한 루트 `README.md`
- 구조/스캐폴딩 결정
- 아직 TODO로 남은 결정

## Stop Condition

전역 문맥 문서와 구조 규칙이 초기화되면 멈춥니다. 기능 구현이나 트랙 생성은 다음 단계 책임입니다.

## Recommended Next Step

일반적으로 다음 단계는 `quick-change` 또는 `start-track`입니다. 단, 자동으로 실행하지 않고 다음 단계로만 제안합니다.

## Non-goals

- 기능 구현을 하지 않습니다.
- 트랙을 생성하지 않습니다.
- 다음 스킬을 자동 호출하지 않습니다.
