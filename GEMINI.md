# Gemini CLI Adapter

이 저장소는 `docs/` 기반의 워크플로우와 `.agents/skills/`의 자동화 스킬을 지원합니다.

## 핵심 컨텍스트
구현 전 다음 문서를 순서대로 로드하십시오:
- `docs/workflow.md`
- `docs/tech-stack.md`
- `docs/product.md`

## 작업 진행
- 활성 트랙 정보는 `docs/tracks.md` 및 `docs/tracks/<track_id>/`에서 확인하십시오.
- 반복적인 작업(트랙 생성, 구현 등)을 위한 워크스페이스 스킬은 `.agents/skills/`에 정의되어 있습니다.

## 주의 사항
- `docs/`가 유일한 Source of Truth입니다. 루트의 어댑터 파일에 새로운 규칙을 추가하지 마십시오.