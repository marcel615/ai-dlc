---
name: frontend-issue-driven-dev
description: 모노레포의 Frontend 영역에서 설정된 작업을 설계·구현·검증하고 PR과 기록을 준비한다.
---

# Frontend 작업

공통 루트의 `AGENTS.md`, `docs/workflows/development.md`, `docs/providers/jira.md`, `docs/review/shared.md`와 아래 역할별 리뷰 기준을 실행 전에 읽는다. Git·설정·기록은 프로젝트 루트에서 확인하고 검증은 영역 경로에서 실행한다. Main은 한 번에 한 작업의 설계 확인·구현·검증·자체 리뷰·기록과 PR 준비를 직접 수행한다. 독립 리뷰가 필요한 경우 공통 개발 절차에 따라 Architect를 호출하고 머지 준비 게이트를 확인한다.

기능 후보 발굴·등록과 백로그 정제는 Orchestrator의 `feature-discovery`와 `backlog-refinement`에서 별도 요청으로 수행한다. 개발 중 확인된 기술 후속 Issue는 공통 개발 절차의 기존 권한과 제한을 따른다. 공식 계약과 운영 파일 수정 권한은 루트 규칙과 공통 개발 절차를 따른다.

## Frontend 기준

대상은 루트 설정의 `areas.frontend`이며 역할 리뷰는 `docs/review/frontend.md`다. UI·API·인증 등 필요한 공식 원본을 설정에서 확인해 URL·SHA를 기록하고 별도 인증 계약이 설정되면 API와 함께 확인하고, 없을 때만 API 문서의 공식 인증 참조를 따른다. 확인 실패나 계약 충돌은 보류한다.

대상 설정의 `areas.frontend.development.build_command`와 `areas.frontend.development.lint_command`, 실제 package scripts와 테스트 도구를 확인한다. 빌드·린트 성공을 기능 테스트나 전체 타입 검사 성공으로 대신 보고하지 않는다. 화면·API 변경은 주요 흐름과 로딩·빈 상태·오류·권한을 검증하고, 브라우저 검증이 필요한 경우 실제 실행 주소와 Network의 URL·Payload·Response, Console을 확인한다. 실행한 검증과 미검증 사항을 구분한다. 세부 기준은 `docs/review/frontend.md`를 따른다.

## React 구현 기준

- `package.json`, lockfile과 현재 코드를 확인해 스택·버전과 언어·타입 패턴을 파악하고 기존 구조를 따른다.
- 조회는 `useQuery`, 사용자 변경 요청은 `useMutation`과 이벤트 핸들러로 관리한다. query key·무효화·삭제 캐시 정리는 관련 코드와 현재 구현을 확인한다.
- 공식 API 응답·인증 계약을 우선 확인한다. 기존 응답 처리와 타입을 실제 코드에서 확인하되 공식 계약의 규칙으로 일반화하지 않는다. 기존 불일치는 범위 밖에서 임의 수정하지 않고 보고한다.
- React Hook Form 검증 실패 시 요청을 보내지 않고 오류 시 입력을 유지한다. 조회·mutation의 로딩/실패/빈 상태와 중복 제출 방지를 확인한다. 에러 응답 메시지를 우선 사용하고 서버 응답이 없으면 기본 메시지를 사용한다.
- API 함수의 위치와 기존 Page·Component·CSS 구조를 실제 코드에서 확인하고 따른다. 사용하지 않는 import와 불필요한 console.log를 추가하지 않는다.
