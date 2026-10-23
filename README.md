# My AI Builder OS

AI가 제품을 기획하고, 만들고, 검증하는 **AI-native product factory**다.
Claude Code를 실행 엔진으로 사용하며, 서비스를 하나 만들 때마다 시스템이 함께 개선된다.

- **North Star**: Time-to-First-User (아이디어 → 첫 실사용자까지 걸린 일수)
- **현재 집중**: [Homepage Builder MVP](services/homepage-builder/README.md)

## Rules

- 모든 변경은 PR로 올린다.
- AI가 먼저 만들고, 사람은 방향을 정하고 승인한다.
- MVP가 먼저다. MVP는 핵심 가설을 검증하는 최소 범위다.
- 같은 작업을 두 번 하면 skill로 만든다.

## Structure

```text
CLAUDE.md          AI 운영 헌법 (Claude Code가 매 세션 자동으로 읽음)
.claude/
  agents/          pm · engineer · qa 서브에이전트
  skills/          /new-service · /prd · /retro
os/
  vision.md        Vision, North Star, Roadmap
  playbook.md      Workflow, Gate, Decision Rules
  architecture.md  도구 역할, Single Source of Truth
  design-system.md UI 원칙
  decisions/       ADR (의사결정 기록)
templates/         prd · sprint · retro · decision
services/          서비스별 PRD, Sprint, 코드
.github/           PR/Issue 템플릿, 문서 lint CI
```

## How to Use

1. 아이디어가 생기면 Issue를 등록한다 (`💡 Idea` 템플릿).
2. Claude Code에서 `/new-service`로 평가하고 서비스 폴더를 만든다.
3. `/prd`로 가설, 지표, MVP 범위를 정의하고 승인한다.
4. `engineer` agent로 구현하고 PR을 올린다. `qa` agent가 검증한다.
5. 출시 후 `/retro`로 회고하고 Builder OS를 갱신한다.

자세한 내용은 [Playbook](os/playbook.md)을 참고한다.
