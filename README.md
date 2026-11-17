# AI-DLC 공통 운영 저장소

프로젝트와 요청에 따라 Orchestrator, Backend, Frontend 작업을 선택하는 공통 운영 루트다. 프로젝트별 설정과 명세, 소스, 작업 기록과 상태는 각 대상 저장소에 남는다. 공통 저장소는 기존 AI-DLC 저장소의 파일이나 Skill을 실행 중에 불러오지 않는다.

## 현재 단계

프로젝트 등록과 역할 선택 규칙을 구성했다. Skill, 공통 워크플로, 리뷰 기준, Agent, 역할별 설정 예시와 템플릿은 다음 통합 단계에서 이관할 예정이다. 해당 파일이 준비되기 전에는 선택된 작업을 실행하지 않는다. 실제 프로젝트의 `ai-dlc.yaml`은 공통 저장소 통합 후 전환 단계에서 필요한 부분만 갱신한다.

## 프로젝트 등록과 요청

1. `projects.example.yaml`을 루트의 `projects.local.yaml`로 복사한다.
2. 사용자에게 확인된 프로젝트 이름, 별칭과 필요한 대상의 절대 경로를 입력한다. 사용하지 않는 대상은 생략할 수 있다. 비밀값을 넣지 않는다.
3. 이 저장소를 운영 루트로 열고 프로젝트와 작업을 명시한다. 예: `Example Project 백엔드 작업 시작하자`, `Example Project 백로그 정제해`.

로컬 등록은 Git에서 제외된다. 이름·역할·대상 경로와 원격을 확인하는 방법 및 중단 조건은 [AGENTS.md](AGENTS.md)를 따른다. 공식 명세가 필요한 작업에서는 실제 설정된 원본을 확인해야 한다.

## 예정 구조

```text
ai-dlc/
├── AGENTS.md                 # 프로젝트·역할 선택과 공통 권한
├── projects.example.yaml     # 로컬 등록 양식
├── .agents/skills/           # 역할별 Skill (통합 예정)
├── .codex/agents/            # 공통 개발 Agent (통합 예정)
├── docs/workflows/           # 공통·Orchestrator 절차 (통합 예정)
├── docs/providers/           # Jira·GitHub Projects 절차 (통합 예정)
├── docs/review/              # 공통·역할별 리뷰 기준 (통합 예정)
├── examples/                 # 역할별 ai-dlc.yaml 예시 (통합 예정)
└── templates/                # 역할별·공통 초기 양식 (통합 예정)
```

최종 전환과 검증은 공통 저장소 통합 이후 진행한다. 기존 프로젝트의 설정·계약·기록·상태를 공통 저장소로 옮기거나 초기화하지 않는다.

## 이관 기준 이력

- [Orchestrator — 5723e65](https://github.com/marcel615/ai-dlc-orchestrator/tree/5723e651b73e2e76466b28526b973ce1f8d2cb01)
- [Backend — 013be82](https://github.com/marcel615/ai-dlc-backend/tree/013be82159c0ce1d9926e1208c8b180cd2a2660c)
- [Frontend — e6a9bf9](https://github.com/marcel615/ai-dlc-frontend/tree/e6a9bf9e15e22de2f9e3dc74cd284d9e707ab6e6)
