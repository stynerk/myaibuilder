---
name: retro
description: Run a sprint or launch retrospective with templates/retro.md, judge hypotheses against metrics, measure TTFU, and turn learnings into concrete Builder OS changes (playbook, skills, agents, templates, CLAUDE.md). Use at the end of a sprint, after a launch, or when the user says 회고 or /retro.
argument-hint: "<service-name> [sprint-NN]"
---

# /retro

회고를 작성하고, 배운 점을 Builder OS 변경으로 연결한다.
**Builder OS 개선 항목이 없는 회고는 완료가 아니다.**

## 절차

1. **사실 수집**
   - Sprint 문서
   - 기간 내 머지된 PR과 닫힌 Issue (`git log`, GitHub)
   - PRD 성공 지표의 실제 값 (Owner에게 묻는다)
2. **TTFU 계산**: `os/vision.md` 정의대로 Idea Issue(Backlog) 등록일부터 첫 실사용자 날짜까지.
3. **가설 판정**: PRD의 H1, H2…를 검증 / 기각 / 보류로 판정하고 근거를 쓴다.
4. **Keep / Problem / Try** 작성.
5. **Builder OS 개선 도출**
   - 반복된 수작업 → 새 skill 후보
   - agent가 헤맨 지점 → agent 정의나 `CLAUDE.md` 수정
   - 쓰지 않은 템플릿 항목 → 삭제
   - Gate가 너무 무겁거나 가벼웠던 지점 → `os/playbook.md` 수정
6. **반영**: Owner 승인 후 개선 항목을 실제 파일에 반영한다. 구조 변경이면 ADR(`templates/decision.md`)을 추가한다.
7. **ADR Review**: Review Date가 지난 ADR의 Result와 Lessons Learned를 채운다.

## 출력

- `services/<name>/sprints/retro-NN.md` (`templates/retro.md` 기준)
- Builder OS 변경 diff (PR)
- 다음 Sprint 추천 목표 1개
