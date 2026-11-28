---
name: contract-management
description: 공식 요구사항·계약 변경의 영향과 사용자 승인을 같은 Jira Task에서 관리한다.
---

# 공식 계약 변경 관리

[공통 규칙](../../../AGENTS.md), [통합 조정](../../../docs/workflows/orchestrator.md), [Jira](../../../docs/providers/jira.md), [리뷰 기준](../../../docs/review/orchestrator.md)을 읽는다. 해당 Jira Task와 루트 설정의 공식 경로·기본 브랜치 SHA를 확인한다.

1. 실제 명세·구현·소비자와 호환성을 대조한다. 영향·대안·전환 순서·복구 제약과 검증 방법을 정리한다.
2. 해당 Task에 변경안과 결정·출처를 기록한다. 필요한 Confluence 협의는 기존 페이지와 Jira 링크를 재사용한다. 공식 파일을 수정하기 전에 사용자 승인 또는 유효한 사이클 위임을 확인한다.
3. 승인된 명세 변경은 [공통 개발 절차](../../../docs/workflows/development.md)에 따라 해당 Task의 브랜치와 PR에서 필요한 구현 및 검증과 함께 처리한다. 명세 자체가 독립된 완료 결과인 경우에도 동일한 Task 착수·PR·마무리 절차를 적용한다.
