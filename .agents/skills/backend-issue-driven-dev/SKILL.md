---
name: backend-issue-driven-dev
description: 모노레포의 Backend 영역에서 설정된 작업을 설계·구현·검증하고 PR과 기록을 준비한다.
---

# Backend 작업

공통 루트의 `AGENTS.md`, `docs/workflows/development.md`, `docs/providers/jira.md`, `docs/review/shared.md`와 아래 역할별 리뷰 기준을 실행 전에 읽는다. Git·설정·기록은 프로젝트 루트에서 확인하고 검증은 영역 경로에서 실행한다. Main은 한 번에 한 작업의 설계 확인·구현·검증·자체 리뷰·기록과 PR 준비를 직접 수행한다. 독립 리뷰가 필요한 경우 공통 개발 절차에 따라 Architect를 호출하고 머지 준비 게이트를 확인한다.

기능 후보 발굴·등록과 백로그 정제는 Orchestrator의 `feature-discovery`와 `backlog-refinement`에서 별도 요청으로 수행한다. 개발 중 확인된 기술 후속 Issue는 공통 개발 절차의 기존 권한과 제한을 따른다. 공식 계약과 운영 파일 수정 권한은 루트 규칙과 공통 개발 절차를 따른다.

## Backend 기준

대상은 루트 설정의 `areas.backend`이며 역할 리뷰는 `docs/review/backend.md`다. 공식 요구사항·API·인증·ERD 등 필요한 계약을 설정된 원본에서 읽고 URL·SHA를 기록한다. 인증 계약이 별도로 설정된 경우 API와 함께 확인하고 미설정일 때만 공식 API 문서의 인증 참조를 따른다. 원본 확인 실패나 충돌은 보류한다.

Spring·Java의 기존 패키지, 계층과 프로젝트 패턴을 따르고 Controller·Service·Repository 책임, API DTO·오류·인가와 DB 트랜잭션을 승인된 설계 및 계약과 대조한다. 불필요한 추상화는 피하고 오류·보안·동시성 보장을 유지한다. 테스트 도구와 명령은 대상 설정의 `areas.backend.development.test_command` 또는 환경에 맞는 `areas.backend.development.test_command_windows`에서 확인한다. 변경 범위의 단위·통합·API 테스트와 설정된 검증을 실행하고, 실패·미실행은 통과로 보고하지 않는다. 세부 기준은 `docs/review/backend.md`를 따른다.
