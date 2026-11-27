---
name: analytics-issue-driven-dev
description: 프로젝트의 Analytics 영역에서 설정된 작업에 따라 데이터 처리·분석 산출물을 설계·구현·검증하고 PR과 기록을 준비한다.
---

# Analytics 작업

공통 루트의 `AGENTS.md`, `docs/workflows/development.md`, `docs/review/shared.md`, `docs/review/analytics.md`와 `docs/providers/jira.md`를 실행 전에 읽는다. Main은 한 번에 한 작업의 설계 확인·구현·검증·자체 리뷰·기록과 PR 준비를 직접 수행한다. 공통 개발 절차의 독립 리뷰 조건에 해당하면 Architect에게 읽기 전용 리뷰를 맡긴다.

## 대상과 작업 추적

- 루트 설정의 `areas.analytics`와 검증 디렉터리를 확인하고 기준 브랜치는 루트 `default_branch`를 따른다.
- Jira 개발 절차와 `jira.role_labels.analytics`로 작업 영역을 확인한다. 착수·재개·마무리 시 Jira 작업과 GitHub PR의 실제 상태를 재조회한다.
- 대상의 작업 기록과 PR 양식을 사용한다. 없으면 `templates/`의 양식을 참고한다.

## 설계와 검증

- Issue의 완료 조건과 적용되는 요구사항·계약을 확인한다. 공식 분석 명세가 필요한 작업은 `contracts.analytics`에 설정된 Specs 원본을 확인하고 URL과 SHA를 기록한다. 분석 기준이나 연동 계약의 변경이 필요하면 공통 개발 절차에 따라 영향과 근거를 기록하고 관련 작업을 보류한다.
- 변경 범위에 맞춰 입력, 처리 규칙, 출력 형태와 검증 기준을 확인한다. Python 환경·의존성 관리·실행 진입점은 대상 저장소의 기존 방식을 따르고, 새 프로젝트에서는 합의한 실행 방식과 검증 명령을 대상 저장소에 기록한다.
- 대상 설정의 `areas.analytics.development.test_command` 또는 환경에 맞는 `areas.analytics.development.test_command_windows`와 관련 검증을 실행한다. 작업 로그와 PR에 실행 명령, 적용한 입력과 가정, 실제 결과 및 미검증 사항을 기록한다.
