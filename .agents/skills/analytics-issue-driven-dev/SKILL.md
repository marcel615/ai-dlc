---
name: analytics-issue-driven-dev
description: 선택한 Analytics 저장소에서 설정된 작업에 따라 데이터 처리·분석 산출물을 설계·구현·검증하고 PR과 기록을 준비한다.
---

# Analytics 작업

공통 루트의 `AGENTS.md`, `docs/workflows/development.md`, `docs/review/shared.md`, `docs/review/analytics.md`와 선택한 추적 도구의 `docs/providers/jira.md` 또는 `docs/providers/github-projects.md`를 실행 전에 읽는다. Main은 한 번에 한 작업의 설계 확인·구현·검증·자체 리뷰·기록과 PR 준비를 직접 수행한다. 공통 개발 절차의 독립 리뷰 조건에 해당하면 Architect에게 읽기 전용 리뷰를 맡긴다.

## 대상과 작업 추적

- `targets.analytics`에서 대상 루트를 확인한다. 대상 `ai-dlc.yaml`의 활성 서비스에서 `repositories.analytics`와 기준 브랜치를 확인하고 실제 Git 루트 및 fetch·push 원격과 대조한다. 다른 역할의 저장소는 작업에 필요한 경우에만 확인한다.
- `work_tracking.provider`가 `jira`이면 Jira 개발 절차를 따르고 `jira.role_labels.analytics`로 작업 영역을 확인한다. `github_projects`이거나 생략되면 GitHub Projects 절차를 따르고 Analytics 저장소의 Issue와 설정된 Project를 확인한다. 두 경로 모두 착수·재개·마무리 시 해당 작업과 PR의 실제 상태를 확인한다.
- 대상의 작업 기록과 PR 양식을 사용한다. 없으면 `templates/analytics/`의 양식을 참고한다.

## 설계와 검증

- Issue의 완료 조건과 적용되는 요구사항·계약을 확인한다. 공식 분석 명세가 필요한 작업은 `contracts.analytics`에 설정된 Specs 원본을 확인하고 URL과 SHA를 기록한다. 분석 기준이나 연동 계약의 변경이 필요하면 공통 개발 절차에 따라 영향과 근거를 기록하고 관련 작업을 보류한다.
- 변경 범위에 맞춰 입력, 처리 규칙, 출력 형태와 검증 기준을 확인한다. Python 환경·의존성 관리·실행 진입점은 대상 저장소의 기존 방식을 따르고, 새 프로젝트에서는 합의한 실행 방식과 검증 명령을 대상 저장소에 기록한다.
- 대상 설정의 `development.test_command` 또는 환경에 맞는 `development.test_command_windows`와 관련 검증을 실행한다. 작업 로그와 PR에 실행 명령, 적용한 입력과 가정, 실제 결과 및 미검증 사항을 기록한다.
