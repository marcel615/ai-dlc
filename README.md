# AI-DLC 공통 운영 저장소

프로젝트와 요청에 따라 Orchestrator, Backend, Frontend, Analytics 작업을 선택하는 공통 운영 루트다. 프로젝트별 설정과 명세, 소스, 작업 기록과 상태는 각 대상 저장소에 남는다. 공통 저장소는 기존 AI-DLC 저장소의 파일이나 Skill을 실행 중에 불러오지 않는다.

## 프로젝트 등록과 요청

1. `projects.example.yaml`을 루트의 `projects.local.yaml`로 복사한다.
2. 사용자에게 확인된 프로젝트 이름, 별칭과 필요한 대상의 절대 경로를 입력한다. 사용하지 않는 대상은 생략할 수 있다. 비밀값을 넣지 않는다.
3. 이 저장소를 운영 루트로 열고 프로젝트와 작업을 명시한다. 예: `Example Project 백엔드 작업 시작하자`, `Example Project 분석 작업 시작하자`, `Example Project 백로그 정제해`.

로컬 등록은 Git에서 제외된다. 이름·역할·대상 경로와 원격을 확인하는 방법 및 중단 조건은 [AGENTS.md](AGENTS.md)를 따른다. 공식 명세가 필요한 작업에서는 실제 설정된 원본을 확인해야 한다.

`Example Project 사이클 시작`, `Example Project 사이클 3회 시작`, `Example Project 사이클 재개`로 후보 하나씩 정제·상세화·구현·마무리까지 진행할 수 있다. 회차에 연결된 PR의 머지와 환경 변수 대기·재개 기준은 [프로젝트 사이클 절차](docs/workflows/project-cycle.md)를 따른다.

## 새 프로젝트 설정

새 프로젝트에서는 대상 역할에 맞는 `templates/orchestrator/`, `templates/backend/`, `templates/frontend/`, `templates/analytics/` 폴더의 `ai-dlc.example.yaml`을 대상 저장소 루트에 `ai-dlc.yaml`로 직접 복사하고 실제 환경에 맞게 수정한다. 역할별 설정 예시는 각각 독립적이며 비밀값을 넣지 않는다.

같은 역할 폴더의 문서와 Issue·PR 양식은 필요한 경우 참고한다. 대상 저장소의 기존 설정·양식·작업 기록을 우선하며 자동으로 복사하거나 덮어쓰지 않는다. Backend·Frontend·Analytics의 작업 기록 초기 양식은 각각 해당 폴더의 `docs/current-work-log.md`에 있다.

Analytics는 데이터 수집·전처리·분석·리포팅·모델 평가 등에 사용하는 선택 역할이다. 프로젝트 등록 예시에서 사용하는 대상만 남긴다.

프로젝트에서 공식 분석 기준을 관리할 때는 Specs 저장소의 `docs/analytics-spec.md`에 합의한 입력 범위, 계산 규칙, 지표 정의와 수용 기준을 기록한다. [분석 명세 양식](templates/orchestrator/docs/analytics-spec.md)을 참고하고 Specs와 Analytics의 설정에서 `contracts.analytics`가 같은 원본을 가리키도록 한다. 분석 코드, 실행 환경, 테스트 데이터와 재현 명령은 Analytics 저장소에 둔다.

Specs를 함께 운영하는 프로젝트에서 Analytics 작업을 계획한다면 Specs 설정의 `repositories.analytics`를 실제 Analytics 저장소에 연결한다. Jira에서는 그 설정과 Analytics 개발 설정의 `jira.role_labels.analytics`를 일치시킨다. GitHub Projects에서 공통 Parent/Sub-issue를 사용하면 구현 저장소 역할 목록에 `analytics`를 추가한다.

## 검증과 PR 준비

실행 가능한 검증과 필수 수정을 마치면 환경·외부 의존성으로 남은 미검증을 PR 본문에 기록하고 commit·push·PR·리뷰·devlog까지 마무리한다. 미검증의 이유·위험·후속 검증 방법과 머지 전 필수 여부를 명시하며, 확인된 버그나 테스트 실패를 이 방식으로 넘기지 않는다. 머지 시 필수 검증·리뷰·보호 조건을 확인한다. 독립 실행에서는 사용자가 직접 머지하고, 명시적인 사이클 요청에서는 해당 회차에 연결된 PR의 머지를 위임한다. 상세 기준은 [공통 개발 절차](docs/workflows/development.md#품질-게이트)를 따른다.

## 저장소 구조

```text
ai-dlc/
├── AGENTS.md                 # 프로젝트·역할 선택과 공통 권한
├── projects.example.yaml     # 로컬 등록 양식
├── .agents/skills/           # 역할별 Skill
├── .codex/agents/            # 공통 개발 Agent
├── docs/workflows/           # 공통·Orchestrator 절차
├── docs/providers/           # Jira·GitHub Projects 절차
├── docs/review/              # 공통·역할별 리뷰 기준
└── templates/
    ├── orchestrator/         # Orchestrator 설정 예시와 초기 양식
    ├── backend/              # Backend 설정 예시와 초기 양식
    ├── frontend/             # Frontend 설정 예시와 초기 양식
    └── analytics/            # Analytics 설정 예시와 초기 양식
```

## 이관 기준 이력

- [Orchestrator — 5723e65](https://github.com/marcel615/ai-dlc-orchestrator/tree/5723e651b73e2e76466b28526b973ce1f8d2cb01)
- [Backend — 013be82](https://github.com/marcel615/ai-dlc-backend/tree/013be82159c0ce1d9926e1208c8b180cd2a2660c)
- [Frontend — e6a9bf9](https://github.com/marcel615/ai-dlc-frontend/tree/e6a9bf9e15e22de2f9e3dc74cd284d9e707ab6e6)
