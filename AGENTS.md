# AI-DLC 공통 운영 규칙

## 프로젝트와 작업 영역

1. 공통 운영 루트의 `projects.local.yaml`을 파싱한다. `projects`의 이름과 별칭은 공백 제거와 대소문자 무시 후 프로젝트 간 충돌이 없어야 한다. 요청의 전체 이름 또는 별칭으로 프로젝트 하나를 선택한다. `projects.example.yaml`은 예시다. YAML 파서가 없으면 설치된 도구나 JDK·Gradle 캐시의 SnakeYAML을 확인한다.
2. 선택 항목의 `root`는 프로젝트 Git 루트의 절대 경로다. 명시 경로, 실제 경로, `git rev-parse --show-toplevel`을 대조하고 별도 worktree를 쓰면 동일 저장소인지 확인한다. `root`가 없는 항목은 이 운영 방식의 대상에서 제외된다. 이름·경로·역할이 모호하거나 확인에 실패하면 중단하고 확인한다.
3. 프로젝트의 루트 `ai-dlc.yaml`에서 `schema_version: 3`, `repository`, `default_branch`, `areas`와 작업에 필요한 설정을 확인한다. 실제 fetch·push 원격과 각각의 URL을 같은 `owner/repo`로 대조하고 원격 기본 브랜치가 설정과 일치하는지 확인한다. Git 명령과 설정은 프로젝트 루트, 검증 명령은 설정된 해당 영역 디렉터리를 기준으로 실행한다.
4. `areas`의 키는 `specs`, `backend`, `frontend`, `analytics` 중 필요한 영역으로 한정한다. `path`는 프로젝트 루트를 기준으로 서로 중첩되지 않는 하위 디렉터리이며 실제 경로도 같은 Git 루트 안이어야 한다. 경로 이탈, 중첩 Git 루트, 미등록 영역 또는 적용되는 로컬 지시와 충돌이 있으면 해당 작업을 보류한다. 공식 명세와 실제 코드를 대조해 Task의 완료에 필요한 변경·검증 영역을 판단하고 `docs/current-task.md`에 기록한다. 승인된 범위의 모든 변경은 하나의 Task·브랜치·PR에서 처리한다. 공통 경로도 필요한 승인 범위에 포함한다.
5. 공식 원본은 루트 설정의 `requirements` 및 `contracts`가 지정한 `specs` 영역 내 파일이다. 원격 기본 브랜치의 SHA를 먼저 확인하고 같은 SHA에서 관련 파일을 읽는다. 명세 사본과 템플릿은 공식 원본으로 사용하지 않는다. 확인하지 못한 원본이 필요한 작업은 보류한다.

| 요청 | Skill |
|---|---|
| 프로젝트 사이클 시작·재개 | `project-cycle` |
| 프로젝트 Jira Task 시작·재개·마무리 | [공통 개발 절차](docs/workflows/development.md)와 해당 영역의 `*-issue-driven-dev` 전문 기준 |
| 기능 아이디어 제안, 백로그 정제, 기존 작업 상세화 | 각각 `feature-discovery`, `backlog-refinement`, `issue-refinement` |
| Confluence 프로젝트 논의 기록 | `discussion-log` |
| 공식 계약 변경 관리 | `contract-management` |

선택 Skill, 공통·해당 영역 워크플로, Jira 절차와 리뷰 기준을 실행 전에 읽는다. 각 Skill은 요청 범위에서 독립 실행한다. 후보 발굴이 후속 단계의 승인이나 실행으로 이어지지 않는다.

## 승인과 기록

- `development.protected_branches`에서 보호할 브랜치 이름을 확인한다. 기본 브랜치와 이 목록에 있는 브랜치에서는 직접 구현·커밋·push·삭제하지 않는다. 변경은 작업 브랜치와 PR을 거친다. 이 목록은 로컬 운영 규칙이며 실제 GitHub 보호 규칙도 별도로 확인한다.

- 사용자가 PM이자 최종 승인자다. 독립 실행에서 후보 승인, 중요한 요구사항·계약·인증·DB·배포 결정과 PR 머지는 사용자가 담당한다. 명시적인 [프로젝트 사이클](docs/workflows/project-cycle.md)은 해당 회차의 권한 위임과 단계 연결을 적용한다. 실제 저장소 보호·실행 권한도 확인한다.
- 공식 명세는 사용자 승인 또는 유효한 사이클 위임을 확인한 뒤 같은 Task의 PR에 반영한다. AI-DLC 운영 설정 변경은 별도로 승인된 유지보수 범위를 따른다. PR은 준비 조건을 충족한 뒤 제출한다.
- 작업 범위와 설계 근거는 프로젝트의 `docs/current-task.md`, 재개·게이트 단서는 `docs/current-work-log.md`에 기록한다. Jira에서 작업 범위와 상태, GitHub에서 PR·리뷰·실행 결과를 확인한다. Confluence에서 프로젝트 논의 및 연결 후보 상태를 관리한다. 기존 개발 기록을 보존하고 비밀값은 기록하지 않는다.
- Main은 개발과 자체 리뷰를 수행한다. [공통 개발 절차](docs/workflows/development.md#독립-리뷰가-필요한-경우)에 해당하면 Architect에게 읽기 전용 독립 리뷰를 맡기고 공통 루트·프로젝트 루트·설정 파일의 절대 경로, 기준 SHA, 역할별 경로, 승인 범위와 금지 작업을 전달한다. Orchestrator 작업은 Main이 수행한다.
