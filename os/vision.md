# Vision & Roadmap

> AI Builder OS의 존재 이유, 성공 기준, 실행 계획을 정의한다.
> 모든 의사결정의 최상위 기준이며, 서비스나 기능을 추가할 때 이 문서와 비교한다.

## Mission

AI를 활용해 제품을 **반복적으로** 만들고 개선하는 시스템(Builder OS)을 구축한다.

서비스 하나를 만드는 것이 목표가 아니다. 서비스를 만들 때마다 다음 서비스가 더 빨라지는 구조를 만드는 것이 목표다.

## Vision

AI를 사용하는 사람이 아니라, AI가 일하는 회사를 만든다.

- 사람은 방향을 정하고 판단한다.
- AI는 기획·디자인·개발·QA·배포를 실행한다.

### Long-term Scope

```text
Service → Workflow → Automation → Builder Platform → AI Native Business
```

지금은 Service와 Workflow 단계다. 다음 단계로의 확장은 TTFU가 실제로 줄어든 뒤에 판단한다.

## Why

기존 제품 개발은 사람이 기획하고, 디자인하고, 개발하고, QA하는 구조다.
1인 빌더에게 이 구조는 곧 병목이다. Builder OS는 실행을 AI Workflow로 전환해 **아이디어 → 실사용자 검증**까지의 시간을 줄인다.

## North Star Metric

**Time-to-First-User (TTFU)**: 아이디어가 Backlog에 등록된 날부터 첫 실사용자가 서비스를 사용한 날까지의 일수

| 이유 | 설명 |
|---|---|
| 시스템 효과를 직접 측정 | 서비스가 늘수록 TTFU가 줄어야 Builder OS가 작동하는 것이다 |
| 메타 작업 방지 | 문서·프롬프트 개수는 늘려도 TTFU는 줄지 않는다 |
| 검증 우선 | "출시"가 아니라 "사용자"를 기준으로 삼는다 |

### 보조 지표

| 지표 | 정의 | 목표 |
|---|---|---|
| Reuse Rate | 새 서비스에서 기존 skill/template/agent를 그대로 쓴 비율 | 서비스마다 증가 |
| Manual Steps | Playbook 전체에서 사람이 직접 수행하는 단계 수 | 서비스마다 감소 |
| Validated Learnings | 서비스별로 검증(또는 기각)된 핵심 가설 수 | 서비스당 1개 이상 |

## Success Definition

> 초안: Owner 확인 필요 (원문이 "새로운…"에서 끊겨 있어 의도를 추정해 보완함)

Builder OS는 아래 조건을 만족하면 성공으로 간주한다.

- 새로운 아이디어를 **2주 이내**에 실사용자 검증 단계까지 가져갈 수 있다.
- 세 번째 서비스의 TTFU가 첫 번째 서비스보다 **30% 이상** 짧다.
- 프로젝트 종료 후 회고(`/retro`)를 거쳐 Builder OS가 실제로 갱신된다.

## Roadmap

> 재기준일: **2026-10-06**. 기존 계획(2026-06-29 시작)은 Phase 1 문서화 이후 정체되었다.
> 상세 배경은 [ADR-0001](decisions/0001-restructure.md) 참고.

Builder OS → Service → Learning → Builder OS 개선 → Next Service 순환을 반복한다.
모든 서비스는 Builder OS를 검증하기 위한 실험이다.

| Phase | 기간 | 목표 | 성공 기준 |
|---|---|---|---|
| 0. Foundation | 완료 | 운영 문서, 저장소, AI 협업 구조 | CLAUDE.md, agents, skills가 동작 |
| 1. Homepage Builder MVP | Week 1–2 | 검증용 랜딩페이지를 하루 안에 배포하는 Workflow | 브리프 → 배포 URL ≤ 1일 |
| 2. Service #1 | Week 3–4 | 첫 서비스 수요 검증 (Homepage Builder 재사용) | 첫 실사용자 확보, TTFU 측정 |
| 3. Service #2 | Week 5–6 | Builder OS 재사용성 검증 | TTFU가 Service #1 대비 감소 |
| 4. Service #3 | Week 7–8 | Builder OS만으로 출시 | TTFU 30% 이상 단축 |
| 5. Optimization | Week 9–10 | Playbook·skills·agents v2 정리 | Builder OS v1.0 |

### 서비스 후보

Backlog의 원본은 GitHub Issues(`idea` 라벨)다. 아래는 이전 문서에서 옮겨 온 후보이며, 각각 Issue로 등록해 관리한다.

| Service | Priority | Status |
|---|---|---|
| Homepage Builder | P0 | In Progress |
| Diet AI | P1 | Idea |
| Medicine AI | P1 | Idea |
| GPS Journal | P2 | Idea |

## Guiding Principle

서비스를 많이 만드는 것이 목표가 아니다.
새 서비스를 **더 빠르게, 더 확실하게 검증**할 수 있는 시스템을 만드는 것이 목표다.
