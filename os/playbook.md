# Playbook

> AI Builder OS의 표준 운영 매뉴얼이자 개발 Workflow다.
> 모든 프로젝트는 이 Playbook을 따르며, 예외가 생기면 [Decision](decisions/README.md)으로 기록하고 Playbook을 개선한다.

## Operating Principles

- **Validate before Build**: 만들기 전에 "누구의 어떤 문제인가"와 성공 지표를 먼저 정한다.
- **MVP = 핵심 가설을 검증하는 최소 범위**: 기능이 가장 적은 버전이 아니라, 가설을 검증할 수 있는 가장 작은 범위다.
- **Launch > Perfection**: 핵심 가치가 동작하면 출시한다.
- **AI First**: AI가 할 수 있는 일은 사람이 하지 않는다.
- **Reuse before Build**: 새로 만들기 전에 기존 skill·template·agent를 확인한다.
- **Workflow is Asset**: 같은 작업을 두 번 하면 skill로 만든다.

## Workflow

```text
Capture → Evaluate → Define → Build → Verify → Launch → Measure → Retro
```

각 단계는 **통과 조건(Gate)**을 만족해야 다음으로 넘어간다.
단계는 건너뛰지 않되, 작은 서비스는 여러 단계를 한 세션에서 처리해도 된다.

| # | Phase | 담당 | 실행 수단 | 산출물 | Gate (통과 조건) |
|---|---|---|---|---|---|
| 1 | Capture | 사람 | GitHub Issue `idea` 템플릿 | Idea Issue | 한 줄 문제 정의가 있다 |
| 2 | Evaluate | `pm` agent | `/new-service` | 평가 점수, Go/No-go | 15점 이상 + Owner 승인 |
| 3 | Define | `pm` agent | `/prd` | PRD (가설·지표·MVP 범위) | PRD Status = Approved |
| 4 | Build | `engineer` agent | Claude Code 세션 | 동작하는 코드 (PR) | 수용 기준을 로컬에서 충족 |
| 5 | Verify | `qa` agent | PR 리뷰 | QA Report | Critical 버그 0건 |
| 6 | Launch | `engineer` agent | 배포 | Live URL, Analytics | 지표 수집 시작 |
| 7 | Measure | 사람 + `pm` | 지표 확인 | 가설 검증 결과 | 가설 판정 (검증/기각/보류) |
| 8 | Retro | `pm` agent | `/retro` | Retro, Builder OS 갱신 PR | 개선 항목이 PR로 반영됨 |

### 1. Capture

아이디어를 잃지 않고 즉시 기록한다. GitHub Issue(`idea` 템플릿)로 등록한다.

### 2. Evaluate

개발 여부를 판단한다. 아래 5개 항목을 각 1–5점으로 평가한다 (총 25점).

| 항목 | 질문 |
|---|---|
| Problem | 실제로 존재하고, 충분히 아픈 문제인가? |
| Market | 이 문제를 가진 사용자가 충분히 많고 도달 가능한가? |
| AI Leverage | AI가 해결의 핵심인가, 장식인가? |
| MVP Speed | 2주 안에 핵심 가설을 검증할 수 있는가? |
| Reusability | 기존 Builder OS 자산을 재사용하고, 새 자산을 남기는가? |

- 15점 이상 → Define 진행
- 15점 미만 → `archived` 라벨 (삭제하지 않는다)

### 3. Define

[PRD 템플릿](../templates/prd.md)으로 작성한다. 순서가 중요하다.

1. 문제와 사용자 (Why / Who)
2. 핵심 가설과 리스크
3. 성공 지표 (먼저 정한다)
4. 지표를 검증할 수 있는 최소 MVP 범위 (지표에서 역산한다)
5. 수용 기준

### 4. Build

- 작은 단위로 구현하고, 모든 변경은 PR로 올린다.
- 기능보다 완료를 우선한다.
- [Design System](design-system.md)을 따른다.

### 5. Verify

PRD의 수용 기준을 기준으로 검증한다. 기능, Edge Case, 모바일, 성능, 접근성, SEO를 점검한다.

### 6. Launch

Production 배포, Analytics 연결, Error Tracking을 확인한다.

### 7. Measure

PRD의 성공 지표와 비교해 가설을 판정한다. 핵심 지표: Activation, Retention, Conversion, Error Rate.

### 8. Retro

`/retro`로 회고하고, 개선 항목을 Builder OS(Playbook, skills, agents, templates)에 PR로 반영한다.
**Builder OS 갱신이 없으면 프로젝트는 끝나지 않은 것이다.**

## Decision Rules

| Rule | 내용 |
|---|---|
| Two Week Rule | MVP가 2주를 넘기면 범위를 줄인다 |
| Workflow Rule | 같은 작업을 두 번 하면 skill로 만든다 |
| Stop Rule | 사용자 검증 없이 기능을 계속 추가하지 않는다 |
| Meta Rule | Builder OS 작업이 서비스 작업보다 길어지면 멈추고 서비스로 돌아간다 |
| Decision Rule | 구조·Workflow·agent 역할·MVP 범위 변경은 ADR로 기록한다 |

## Definition of Done

- [ ] MVP 출시 (Live URL)
- [ ] 수용 기준 충족, Critical 버그 0건
- [ ] 성공 지표 수집 중
- [ ] 핵심 가설 판정 완료
- [ ] Retro 작성, Builder OS 갱신 PR 머지
- [ ] 주요 결정 ADR 기록

## Daily Routine

1. Issue/Project 보드 확인
2. 오늘의 한 가지 목표 결정
3. Claude Code와 작업 → PR
4. 막힌 점과 배운 점을 Sprint 문서에 기록

## Philosophy

서비스는 일회성 결과물이고, Workflow는 반복 가능한 시스템이다.
단, Workflow는 서비스를 출시하면서만 검증된다.
