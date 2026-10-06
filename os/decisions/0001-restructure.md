# 0001. Builder OS를 Claude Code 중심 실행 구조로 재구성

| 항목 | 내용 |
|---|---|
| Date | 2026-10-06 |
| Status | Accepted |
| Category | Architecture, Workflow |
| Supersedes | DEC-001 (2026-06-29, "Agent를 하나의 Agents.md에서 관리") |
| Review Date | Homepage Builder MVP 출시 후 Retro |

## Context

2026-06-29에서 07-01 사이 Builder OS 문서 약 2,000줄을 작성했지만, 이후 3개월 동안 서비스 산출물은 없었다.

- **메타 작업의 함정**: 성공 지표가 산출물 개수(Prompt 100개 이상, Workflow 10개 이상)라서 문서를 쓰는 것 자체가 진척처럼 보였다.
- **문서와 도구의 불일치**: 문서는 ChatGPT + Notion + Codex를 전제로 했지만, 실제 도구는 Claude Code다. Agent·Prompt·Workflow가 설명 문서로만 존재해 AI가 자동으로 읽거나 실행하지 못했다.
- **중복과 충돌**: Playbook과 BuilderWorkflow가 같은 흐름을 두 번 정의했고, 빈 파일 3개가 있었다. Backlog·Decision의 원본이 Notion인지 GitHub인지도 충돌했다.
- **형식 오류**: 탭으로 구분한 표가 GitHub에서 표로 보이지 않았고, 헤딩이 깨졌으며, Vision 문서가 중간에 끊겨 있었다.

## Decision

1. **중심 도구는 Claude Code다.**
   - Agent → `.claude/agents/`
   - Prompt / Workflow Library → `.claude/skills/`
   - 운영 규칙 → `CLAUDE.md`
2. **Backlog와 Sprint 진행 상태의 원본은 GitHub Issues + Projects다.** Notion은 사용하지 않는다.
3. **Agent는 8개에서 3개로 줄인다** (`pm` / `engineer` / `qa`). 분리 기준은 [Architecture](../architecture.md)의 Evolution 표를 따른다.
4. **문서를 통합한다.**
   - Playbook + BuilderWorkflow → `os/playbook.md`
   - Vision + Roadmap → `os/vision.md`
   - DecisionLog → `os/decisions/` (ADR)
5. **North Star Metric을 Time-to-First-User로 바꾼다.**
6. **Roadmap은 2026-10-06 기준으로 다시 잡는다.**

## Alternatives

| 대안 | 기각 이유 |
|---|---|
| 기존 구조 유지, 형식만 수정 | 문서가 실행되지 않는 근본 문제가 남는다 |
| Notion을 Backlog 원본으로 유지 | AI가 직접 읽고 쓰기 어렵고 도구가 하나 늘어난다. PM 대시보드 측면에서는 Notion이 더 낫지만, 1인 빌더 단계에서는 단순함이 우선이다 |
| Agent 8개 유지 | 1인 빌더 단계에서는 인계 비용이 전문화 이득보다 크다 |

## Expected Impact

- 매 세션마다 AI가 운영 규칙을 자동으로 따른다 (CLAUDE.md).
- `/new-service` → `/prd` → 구현 → `/retro`가 명령 하나씩으로 실행된다.
- 문서 수가 줄어 유지 비용이 감소한다 (12개에서 6개 + 실행 파일).

## Risks

| Risk | Mitigation |
|---|---|
| 기존 문서의 뉘앙스 손실 | 원문은 git 이력에 보존되어 있다 (commit `1edc7fc`) |
| GitHub Projects의 PM 뷰가 부족함 | 불편이 두 번 이상 반복되면 ADR로 재검토한다 |
| 재구성 자체가 또 하나의 메타 작업이 됨 | 이번 재구성은 이 ADR로 종료하고, 다음 작업은 Homepage Builder MVP다 |

## Result

(Review Date에 작성)

## Lessons Learned

(Review Date에 작성)
