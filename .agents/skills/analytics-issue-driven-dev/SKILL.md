---
name: analytics-issue-driven-dev
description: 선택한 Analytics 저장소에서 Jira 작업에 따라 데이터 수집·분석·백테스트를 설계·구현·검증하고 PR과 기록을 준비한다.
---

# Analytics 작업

공통 루트의 `AGENTS.md`, `docs/workflows/development.md`, `docs/providers/jira.md`, `docs/review/shared.md`, `docs/review/analytics.md`를 실행 전에 읽는다. Main은 한 번에 한 작업의 설계 확인·구현·검증·자체 리뷰·기록과 PR 준비를 직접 수행한다. 공통 개발 절차의 독립 리뷰 조건에 해당하면 Architect에게 읽기 전용 리뷰를 맡긴다.

## 대상과 작업 추적

- `targets.analytics`에서 대상 루트를 확인한다. 대상 `ai-dlc.yaml`의 활성 서비스에서 `repositories.analytics`와 기준 브랜치를 확인하고 실제 Git 루트 및 fetch·push 원격과 대조한다. 다른 역할의 저장소는 작업에 필요한 경우에만 확인한다.
- `work_tracking.provider: jira`를 명시한 서비스를 사용한다. 착수·재개·마무리는 Jira 개발 Task 절차를 따르며 `jira.role_labels.analytics`로 역할을 확인한다. 검토 가능한 PR을 같은 Task에 연결하고, 마무리 요청 시 실제 머지를 확인한 뒤 해당 Task를 완료한다.
- 대상의 작업 기록과 PR 양식을 사용한다. 없으면 `templates/analytics/`의 양식을 참고한다.

## 설계와 검증

- Issue의 완료 조건과 적용되는 요구사항·계약을 확인한다. 필요한 공식 원본은 대상 설정에서 확인하고 URL과 SHA를 기록한다. 다른 구성 요소가 소비하는 API, 공유 데이터 구조 또는 지표 의미의 공식 계약 변경이 필요하면 공통 개발 절차에 따라 영향과 근거를 기록하고 관련 작업을 보류한다.
- 입력 데이터, 전략 또는 계산 규칙, 결과 지표와 재현 조건을 변경 범위에 맞게 확인한다. 데이터 수집·백테스트 명령은 기존 프로젝트의 실행 방식을 따른다.
- 대상 설정의 `development.test_command` 또는 환경에 맞는 `development.test_command_windows`와 관련 검증을 실행한다. 작업 로그와 PR에 실행 명령, 적용한 입력과 가정, 실제 결과 및 미검증 사항을 기록한다.
