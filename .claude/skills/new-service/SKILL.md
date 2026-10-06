---
name: new-service
description: Evaluate a new service idea with the Builder OS 5-criteria scorecard and, if it passes, scaffold services/<name>/ with README, PRD draft, and sprints folder. Use when the user brings a new idea or says "새 서비스", "아이디어 평가", or /new-service.
---

# /new-service

아이디어를 평가하고, Go 판정이 나면 서비스 폴더를 만든다.

## 입력

아이디어 설명, 또는 GitHub Issue 번호. 정보가 부족하면 아래 세 가지를 먼저 묻는다.

- 누구의 문제인가?
- 지금은 그 문제를 어떻게 해결하고 있는가?
- 왜 지금인가?

## 절차

1. **Reuse 확인**: `services/`와 Issue에서 유사한 서비스나 아이디어를 찾는다.
2. **평가**: `pm` agent 관점에서 `os/playbook.md`의 5개 항목(Problem, Market, AI Leverage, MVP Speed, Reusability)을 각 1–5점으로 매기고, 항목마다 근거를 한 줄씩 쓴다.
3. **핵심 가정과 리스크**: 이 아이디어가 성립하려면 참이어야 하는 가정 상위 3개를 쓴다.
4. **판정**: 15점 이상이면 Go 추천, 미만이면 No-go 추천. **최종 판단은 Owner에게 묻는다.**
5. **Go 승인 시 Scaffold**:
   - `services/<kebab-name>/README.md`: 아래 형식
   - `services/<kebab-name>/PRD.md`: `templates/prd.md`를 복사하고 Problem 섹션과 가설 초안만 채운다 (Status: Draft)
   - `services/<kebab-name>/sprints/`: 비워 둔다
6. 다음 단계로 `/prd`를 안내한다.

## README 형식

```markdown
# {Service Name}

| 항목 | 내용 |
|---|---|
| One-liner | 누구의 어떤 문제를 어떻게 |
| Status | Define |
| Issue | #번호 |
| Score | NN/25 |

- [PRD](PRD.md)
- [Sprints](sprints/)
```

## 출력

평가표(마크다운 표), 핵심 가정 3개, Go/No-go 추천, (승인 시) 생성한 파일 목록.
