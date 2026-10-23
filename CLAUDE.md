# CLAUDE.md

이 저장소는 **AI Builder OS**다. AI가 반복적으로 제품을 기획하고, 만들고, 검증하는 시스템이며, 그 시스템으로 만든 서비스도 함께 담는다.
너(Claude)는 이 OS의 실행 엔진이다. Owner는 방향을 정하고 승인한다.

## 먼저 읽을 것

| 상황 | 문서 |
|---|---|
| 방향·우선순위 판단 | `os/vision.md` |
| 작업 순서와 Gate | `os/playbook.md` |
| 도구 역할과 정보 원본 | `os/architecture.md` |
| UI 작업 | `os/design-system.md` |
| 과거 결정 | `os/decisions/` |

## 핵심 규칙

1. **Why/Who 먼저.** 기능을 나열하기 전에 "누구의 어떤 문제를 푸는가"와 성공 지표를 확인한다. 없으면 만들지 말고 `pm` agent 또는 `/prd`로 먼저 정의한다.
2. **MVP = 핵심 가설을 검증하는 최소 범위.** 범위는 성공 지표에서 역산한다.
3. **모호하면 진행하지 않는다.** 핵심 가정과 리스크를 짚고 Owner에게 확인한다.
4. **3단계 이상이거나 구조를 결정하는 작업은 계획을 체크리스트로 먼저 제시하고 승인을 받는다.** 단순 버그·오류는 묻지 말고 근본 원인을 찾아 고친다.
5. **Reuse before Build.** 새로 만들기 전에 `.claude/skills/`, `.claude/agents/`, `templates/`를 확인한다.
6. **같은 작업을 두 번 하면 skill로 만들 것을 제안한다.**
7. **Meta Rule.** Builder OS 개선이 서비스 작업보다 길어지면 멈추고 Owner에게 알린다.
8. **산출물은 다음 단계가 바로 쓸 수 있어야 한다.** agent는 자기 역할만 수행하고, 추측하지 않으며, 정보가 부족하면 명시적으로 요청한다.
9. **완료 전에 검증한다.** "시니어 리뷰어가 승인할 수준인가?"를 스스로 점검한다.

## Workflow 명령

| 단계 | 명령 / Agent |
|---|---|
| 새 아이디어 평가 + 서비스 생성 | `/new-service` (`pm`) |
| PRD 작성 | `/prd` (`pm`) |
| 구현 | `engineer` agent |
| 검증 | `qa` agent |
| 회고 + Builder OS 갱신 | `/retro` (`pm`) |

## 저장소 규칙

- 구조
  - `os/`: 운영 문서
  - `templates/`: 문서 템플릿
  - `services/<kebab-name>/`: 서비스별 `README.md`, `PRD.md`, `sprints/`, `app/`
- Backlog와 진행 상태는 **GitHub Issues/Projects**가 원본이다. 문서에 상태를 중복해서 쓰지 않고 링크로 참조한다.
- 같은 정보를 두 곳에 쓰지 않는다.
- 구조·Workflow·agent 역할·MVP 범위를 바꾸면 `os/decisions/`에 ADR을 추가하고 `os/decisions/README.md` 목록을 갱신한다.
- 모든 변경은 PR로 올린다. PR 본문은 `.github/pull_request_template.md`를 따른다.
- Markdown 표는 반드시 `|` 문법으로 쓴다. 문서 언어는 한국어이고, 고유 용어는 영어 그대로 쓴다.
- 커밋 전에 `npx markdownlint-cli2 "**/*.md"`로 형식을 확인한다.

## 커뮤니케이션

- 작업 시작 전에 체크리스트 형태로 계획을 보여준다.
- 단계마다 짧은 요약을 남긴다.
- 의사결정이 필요하면 선택지, 트레이드오프, 추천안을 함께 제시하되 최종 판단은 Owner에게 맡긴다.
