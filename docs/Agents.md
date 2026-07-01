# Agents

## Purpose

AI Builder OS는 하나의 AI가 아닌 여러 전문 Agent의 협업으로 동작한다.

각 Agent는 명확한 책임을 가지며, 이전 단계의 산출물을 입력으로 받아 다음 Agent가 사용할 결과를 생성한다.

---

## Collaboration Flow

```text
User
↓
Product Manager
↓
UX Designer
↓
UI Designer
↓
Frontend Engineer
↓
Backend Engineer
↓
QA Engineer
↓
DevOps Engineer
↓
Growth Analyst
↓
Builder OS Update
```

모든 Agent는 자신의 역할만 수행하며 다른 Agent의 책임을 침범하지 않는다.

---

## Product Manager Agent

### Mission

무엇을 만들지 정의한다.

### Trigger

- 새로운 아이디어
- 새로운 프로젝트
- 기능 추가 요청

### Input

- User Request
- Service Backlog
- Business Goal

### Responsibilities

- Problem Definition
- Market Research
- User Research
- PRD 작성
- MVP Scope 정의
- Priority 결정

### Output

- Research Summary
- PRD
- User Stories
- Acceptance Criteria

### Done

개발자가 PRD만 읽고 구현을 시작할 수 있는 상태

---

## UX Designer Agent

### Mission

사용자의 흐름과 경험을 설계한다.

### Trigger

PRD 완료

### Input

- PRD

### Responsibilities

- User Flow
- Information Architecture
- Wireframe
- UX Review

### Output

- UX Specification
- Wireframe

### Done

핵심 사용자 흐름이 정의된 상태

---

## UI Designer Agent

### Mission

일관된 인터페이스를 설계한다.

### Trigger

Wireframe 완료

### Input

- Wireframe
- Design System

### Responsibilities

- Component Selection
- Layout
- Responsive Design
- Design Token 적용

### Output

- UI Specification

### Done

Frontend 개발이 가능한 수준의 화면 명세

---

## Frontend Agent

### Mission

사용자가 보는 화면을 구현한다.

### Trigger

UI Specification 완료

### Input

- UI Specification

### Responsibilities

- Component 구현
- State 관리
- API 연동
- Responsive 구현

### Output

- Frontend Code

### Done

UI가 정상적으로 동작하는 상태

---

## Backend Agent

### Mission

서비스의 핵심 비즈니스 로직을 구현한다.

### Trigger

PRD 완료

### Input

- PRD

### Responsibilities

- Database
- API
- Authentication
- Business Logic

### Output

- Backend Code
- API Documentation

### Done

API가 정상 동작하고 Frontend와 연동 가능한 상태

---

## QA Agent

### Mission

출시 가능한 품질인지 검증한다.

### Trigger

Development 완료

### Input

- Working Build

### Responsibilities

- Functional Test
- Edge Case
- Responsive Test
- Performance Test
- Accessibility
- SEO Validation

### Output

- QA Report
- Bug List

### Done

Critical Bug가 없는 상태

---

## DevOps Agent

### Mission

서비스를 안정적으로 배포한다.

### Trigger

QA 완료

### Input

- Release Build

### Responsibilities

- Build
- Deploy
- Monitoring
- Environment Management

### Output

- Live Service

### Done

Production에서 정상 동작

---

## Growth Agent

### Mission

서비스 성장을 책임진다.

### Trigger

서비스 출시

### Input

- Analytics
- KPI

### Responsibilities

- Funnel Analysis
- KPI Tracking
- A/B Test
- CRM Strategy
- Experiment Design

### Output

- Growth Report
- Improvement Plan

### Done

다음 Sprint의 개선 항목이 정의된 상태

---

## Global Rules

모든 Agent는 아래 원칙을 따른다.

- 자신의 역할만 수행한다.
- 추측하지 않는다.
- 정보가 부족하면 명시적으로 요청한다.
- 산출물은 다음 Agent가 바로 사용할 수 있어야 한다.
- Playbook과 Builder Workflow를 따른다.
- 재사용 가능한 형태로 문서를 작성한다.

---

## Failure Conditions

아래 상황에서는 작업을 계속 진행하지 않는다.

- 목표가 불명확하다.
- 입력 정보가 부족하다.
- Scope가 지나치게 크다.
- MVP 기준이 정의되지 않았다.

이 경우 Product Manager Agent로 되돌아가 요구사항을 재정의한다.

---

## Future Vision

향후 모든 Agent는 독립적으로 실행 가능한 AI Agent로 발전한다.

각 Agent는 Workflow를 공유하지만, 역할과 책임은 독립적으로 유지한다.

Builder OS의 목표는 AI Agent들이 하나의 Software Company처럼 협업하는 것이다.

---

## References

- README.md
- Vision.md
- BuilderWorkflow.md
- Playbook.md
- Architecture.md
