---
name: prd
description: Write or refine a service PRD using templates/prd.md, working backward from hypotheses and success metrics to the minimal MVP scope. Use when the user asks for a PRD, MVP scope, success metrics, or says /prd <service>.
---

# /prd

`services/<name>/PRD.md`를 작성하거나 개선한다. `pm` agent 원칙을 따른다.

## 절차 (순서를 지킨다)

1. **컨텍스트 수집**: 서비스 README, 기존 PRD, 관련 Issue, `os/vision.md`(North Star와의 연결)를 읽는다.
2. **Problem**: 누구의 / 어떤 문제 / 현재 우회 방법 / 왜 지금. JTBD 한 문장. 경쟁·대체 서비스를 조사하고, 차별화 포인트가 우리 컨텍스트에 맞는지 근거를 쓴다.
3. **Hypotheses & Risks**: 가치 가설(H1)과 도달 가설(H2)을 최소 1개씩 쓰고, 각각의 검증 방법을 적는다.
4. **Success Metrics**: North Star 1개, Guardrail 1–2개, Kill Criteria를 쓴다. 목표 수치와 측정 방법도 함께 쓴다.
5. **MVP Scope 역산**: 지표 검증에 꼭 필요한 기능만 포함하고, 각 기능이 어느 가설을 검증하는지 연결한다. 제외 항목과 그 이유도 적는다.
6. **Requirements**: FR마다 테스트 가능한 수용 기준을 붙인다.
7. **Open Questions**: 추측으로 채운 부분은 모두 여기에 올린다.

## 품질 체크 (저장 전 자체 점검)

- [ ] 기능이 아니라 문제로 시작하는가?
- [ ] 모든 MVP 기능이 가설과 연결되는가? (연결되지 않으면 제외)
- [ ] 2주 안에 만들 수 있는가? (Two Week Rule)
- [ ] 수용 기준을 QA가 그대로 테스트할 수 있는가?
- [ ] 측정 방법이 실제로 구현 가능한가?

## 출력

PRD 파일을 갱신한다 (Status는 Draft 또는 Review로 둔다). Owner에게 확인이 필요한 결정 사항을 선택지와 추천안으로 요약한다.
Approved 전환은 Owner 승인 후에만 한다.
