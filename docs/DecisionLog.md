# Decision Log

## Purpose

Decision Log는 AI Builder OS에서 이루어진 중요한 의사결정과 그 이유를 기록하는 문서이다.

좋은 시스템은 좋은 결정을 반복하는 시스템이다.

모든 주요 결정은 기록하고, 이후 회고와 개선의 근거로 사용한다.

---

## Principles

Decision Log는 다음 목적을 가진다.

* 같은 논의를 반복하지 않는다.
* 의사결정의 배경을 남긴다.
* 잘못된 결정도 기록한다.
* Builder OS 개선에 활용한다.

---

## Decision Template

## Decision ID
## DEC-001
### Date
YYYY-MM-DD
### Status
Accepted / Rejected / Changed
### Category
Product
## Workflow
Architecture
Prompt
Automation
Business
### Context
왜 이 결정이 필요했는가?
### Decision
무엇을 결정했는가?
### Alternatives
고려했던 다른 선택지는 무엇인가?
### Reason
왜 이 결정을 선택했는가?
### Expected Impact
기대 효과
### Risks
예상되는 리스크
### Review Date
언제 다시 검토할 것인가?
### Result
실제 결과
### Lessons Learned
배운 점

---

## Decision Categories

Product

제품 방향

예)

* MVP 범위
* 기능 제거
* 기능 추가

---

## Workflow

프로세스

예)

* Workflow 변경
* Playbook 수정

---

Architecture

시스템 구조

예)

* GitHub 구조 변경
* Notion 변경
* Codex 적용

---

Prompt

Prompt 개선

예)

* Prompt 수정
* Prompt 삭제

---

Automation

자동화

예)

* Workflow 자동화
* GitHub Actions
* MCP

---

Business

비즈니스

예)

* 새로운 서비스
* Pivot
* Pricing

---

## Decision Rules

아래 사항은 반드시 Decision Log에 기록한다.

* Builder OS 구조 변경
* Workflow 변경
* Prompt 변경
* Agent 역할 변경
* Architecture 변경
* MVP 범위 변경
* 서비스 방향 변경

---

## Example

## DEC-001

Date

2026-06-29

Category

Architecture

Context

Agent를 각각의 파일로 분리할 것인가?

Decision

현재는 하나의 Agents.md에서 관리한다.

Alternatives

PM-Agent.md

QA-Agent.md

UX-Agent.md

…

Reason

아직 Agent가 충분히 성숙하지 않았다.

MVP 단계에서는 하나의 문서가 유지보수가 쉽다.

Expected Impact

문서 수 감소

관리 단순화

Review

첫 번째 서비스 출시 이후 다시 검토한다.

---

## Review Process

매 Sprint 종료 후

Decision Log를 검토한다.

아래 질문을 한다.

* 유지할 것인가?
* 수정할 것인가?
* 삭제할 것인가?

---

## Philosophy

좋은 시스템은

좋은 코드를 많이 만드는 시스템이 아니다.

좋은 결정을 반복하는 시스템이다.

Decision Log는

Builder OS의 기억(Memory)이다.

프로젝트가 늘어날수록

Builder OS는 더 좋은 결정을 내릴 수 있어야 한다.

---

## References

* Vision.md
* Playbook.md
* BuilderWorkflow.md
* Architecture.md
