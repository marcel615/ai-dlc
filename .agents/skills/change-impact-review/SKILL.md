---
name: change-impact-review
description: 지정 PR 또는 모노레포 신규·갱신 PR의 실제 diff를 공식 명세와 비교해 변경 영향을 검토한다.
---

# PR 변경 영향 검토

[공통 규칙](../../../AGENTS.md), [PR 탐색·이력·분석 절차](../../../docs/workflows/orchestrator.md#요청-시-pr-탐색과-이력), [리뷰 기준](../../../docs/review/orchestrator.md)을 읽는다.

- 설정된 저장소의 PR base/head와 전체 변경 파일을 조회한다. 공식 경로의 diff와 각 구현 영역의 영향을 모두 확인한다. patch가 잘렸으면 원문으로 보완하고 관련 최신 공식 원본 SHA를 별도로 확인한다.
- `review.state_file`에서 PR의 실제 맥락·SHA·상태가 같은 완료 분석만 재사용한다. 새 맥락·보류·실패는 재검토하고 선택 PR 검토만으로 전체 조회 기준점을 진전시키지 않는다.
- 영향 없음·호환·비호환·보류의 판정과 근거, 필요한 사용자 결정·후속 작업안을 보고한다. 작업 등록이나 제품 구현, 자동 감시로 이어가지 않는다.
