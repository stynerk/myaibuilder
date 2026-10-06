# Decisions (ADR)

> Decision Log는 Builder OS의 기억이다. 같은 논의를 반복하지 않고, 결정의 배경과 결과를 남긴다.

## Rules

- 결정 1건당 파일 1개: `NNNN-short-title.md` (예: `0002-backlog-tool.md`)
- 템플릿: [templates/decision.md](../../templates/decision.md)
- 결정을 뒤집을 때는 기존 파일을 수정하지 않고, 새 ADR을 만든 뒤 기존 ADR의 Status를 `Superseded by NNNN`으로 바꾼다.
- 잘못된 결정도 기록한다.

## 반드시 기록할 것

- Builder OS 구조 변경
- Workflow / Playbook 변경
- Agent 역할 변경
- 도구·아키텍처 변경
- MVP 범위 변경, 서비스 방향 변경 (Pivot)

## Review

Retro 때마다 Review Date가 지난 ADR을 확인한다. 질문은 세 가지다: 유지할 것인가? 수정할 것인가? 폐기할 것인가?

## Index

| ID | Title | Status | Date |
|---|---|---|---|
| DEC-001 | Agent를 하나의 문서에서 관리 | Superseded by 0001 | 2026-06-29 |
| [0001](0001-restructure.md) | Builder OS를 Claude Code 중심 실행 구조로 재구성 | Accepted | 2026-10-06 |
