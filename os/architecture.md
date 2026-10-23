# Architecture

> Builder OS를 구성하는 도구와 각각의 책임, 정보의 원본(Single Source of Truth)을 정의한다.
> 변경 배경은 [ADR-0001](decisions/0001-restructure.md) 참고.

## System Overview

```text
                 Owner (사람)
        방향 · 우선순위 · 승인 · 최종 판단
                     │
                     ▼
               Claude Code
  CLAUDE.md(헌법) + agents(역할) + skills(Workflow)
                     │
                     ▼
                  GitHub
  Repo(지식·코드) · Issues/Projects(Backlog·Sprint) · PR(리뷰) · Actions(CI)
                     │
                     ▼
            Preview / Production
```

## Responsibilities

| 구성 요소 | 책임 | Owns | Never Owns |
|---|---|---|---|
| Owner | 방향 결정, 승인 | Vision, 우선순위, Go/No-go, PR 머지 | 반복 실행 작업 |
| Claude Code | AI 실행 엔진 | 기획 초안, 구현, QA, 회고 초안 | 최종 의사결정 |
| `pm` agent | 무엇을, 왜 | 평가, PRD, 가설, 지표, 회고 | 코드 |
| `engineer` agent | 어떻게 | 설계, 구현, 배포, 테스트 | 범위·우선순위 변경 |
| `qa` agent | 출시 가능한가 | 수용 기준 검증, QA Report | 기능 추가 |
| GitHub Repo | 지식 + 코드 | os/, templates/, .claude/, services/ | 일정·진행 상태 |
| GitHub Issues/Projects | 실행 관리 | Backlog, Sprint 보드, 버그 | 운영 규칙 |

## Single Source of Truth

| 항목 | 원본 위치 |
|---|---|
| 운영 규칙 (AI용) | `CLAUDE.md` |
| Vision, Roadmap, 지표 | `os/vision.md` |
| Workflow, Gate | `os/playbook.md` |
| 의사결정 | `os/decisions/` |
| Agent 정의 | `.claude/agents/` |
| 재사용 Workflow / Prompt | `.claude/skills/` |
| 문서 템플릿 | `templates/` |
| 서비스 PRD·Sprint·코드 | `services/<service>/` |
| Backlog, Sprint 진행 상태 | GitHub Issues + Projects |

같은 정보를 두 곳에 쓰지 않는다. 다른 곳에서는 링크로 참조한다.

## Design Principles

- **Executable over Descriptive**: Agent·Prompt·Workflow는 설명 문서가 아니라 Claude Code가 실행하는 파일로 관리한다.
- **Single Responsibility**: 각 구성 요소는 하나의 역할만 가진다.
- **PR-based**: 모든 변경은 PR로 리뷰한 뒤 머지한다.
- **Start Small**: Agent는 필요해질 때 분리한다 (현재 3개).

## Evolution

| 단계 | 변화 | 트리거 |
|---|---|---|
| 현재 | 3 agents (pm / engineer / qa) | — |
| 다음 | `engineer` → `designer` / `frontend` / `backend` 분리 | 서비스 2개 이상에서 역할 과부하 확인 |
| 이후 | GitHub Actions에서 Claude 자동 실행 (Issue → PRD → PR) | 수동 단계가 반복될 때 |
| 장기 | `growth` agent 추가 | 출시된 서비스에 지표 데이터가 쌓일 때 |
