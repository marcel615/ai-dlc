# GitHub Projects 작업 추적

`work_tracking.provider`가 생략되거나 `github_projects`일 때 적용한다. 접근·권한·Project 필드·승인 및 공식 관계를 확인하고 실패를 부재로 판단하지 않는다. Jira에 Draft 또는 GitHub Sub-issue 관계를 적용하지 않는다.

사용자가 요청한 프로젝트 사이클의 후보 승인·착수 전환·머지 권한은 [사이클 위임 규칙](../workflows/project-cycle.md#실행-범위와-위임)을 따른다. 실제 필드 상태와 관계는 아래 절차로 검증한다.

후보 발굴·정제, Draft 전환과 Parent/Sub-issue 관계·부분 실패는 `docs/workflows/orchestrator.md`의 GitHub Projects 절차를 따른다. 개발 Issue 선정·상태·기술 후속 Issue와 재개는 `docs/workflows/development.md`의 GitHub Projects 절차를 따른다. 사용자 승인과 개발 착수는 별개다.
