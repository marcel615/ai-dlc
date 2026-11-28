# AI-DLC

하나의 Git 모노레포에서 Jira 작업, 공식 명세, 구현과 프로젝트 사이클을 운영하는 공통 Codex 지침입니다.

1. [등록 예시](projects.example.yaml)를 참고해 로컬 `projects.local.yaml`에 프로젝트 이름·별칭과 Git 루트를 등록합니다.
2. 프로젝트 루트의 `ai-dlc.yaml`을 [설정 예시](templates/ai-dlc.example.yaml)에 맞춰 작성하고 저장소·기준 브랜치·작업 영역·Jira 설정을 확인합니다.
3. [공통 규칙](AGENTS.md)과 [요청 예시](docs/prompts/quick.md)를 사용합니다.

프로젝트명과 Jira 작업 키로 개발을 시작하거나 재개합니다. 하나의 Task에 필요한 명세·구현·검증 변경은 같은 PR에 담습니다.

작업 범위와 상태는 Jira, 구현·리뷰·검증은 GitHub, 논의와 연결 후보 상태는 Confluence에서 확인합니다. 프로젝트의 `docs/current-task.md`와 `docs/current-work-log.md`는 설계 및 재개에 사용합니다. 월별 개발 일지는 기존 기록으로 보존합니다.

[개발 절차](docs/workflows/development.md) · [프로젝트 사이클](docs/workflows/project-cycle.md) · [Jira·Confluence 절차](docs/providers/jira.md)
