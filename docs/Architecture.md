# Architecture

## Purpose

Architecture는 AI Builder OS를 구성하는 시스템과 각 도구의 역할을 정의한다.

모든 구성 요소는 하나의 책임(Single Responsibility)을 가지며, 역할이 중복되지 않도록 설계한다.

---

## System Overview

                    User
                      │
                      ▼
                  ChatGPT
          (Planning & Decision)
          ┌────────────┴────────────┐
          ▼                         ▼
      Notion                    GitHub
(Project Management)      (Knowledge & Source)
          └────────────┬────────────┘
                       ▼
                    Codex
             (AI Software Engineer)
                       ▼
               Git Repository
                       ▼
           Preview / Production

---

## Responsibilities

User

Responsibility

* 비즈니스 목표 설정
* 우선순위 결정
* 최종 의사결정

Owns

* Vision
* Business Direction

---

ChatGPT

Responsibility

Builder OS의 AI Project Manager

Owns

* 아이디어 구체화
* 시장 조사
* PRD
* 전략
* Architecture
* Workflow
* Decision Support

Never Owns

* Source Code
* Project Status

---

Notion

Responsibility

Project Management Hub

Owns

* Service Backlog
* Builder Backlog
* Sprint
* PRD
* Decision Log
* Meeting Notes
* Dashboard

Never Owns

* Source Code
* Workflow 정의

---

GitHub

Responsibility

Knowledge Base + Source Code Repository

Owns

* Vision
* Roadmap
* Workflow
* Playbook
* Agents
* Templates
* Standards
* Prompt Rules
* Source Code

Never Owns

* Sprint
* Project Schedule

---

Codex

Responsibility

AI Software Engineer

Owns

* Development
* Refactoring
* Testing
* Code Review
* Bug Fix

Never Owns

* Product Strategy
* Priority

---

## Information Flow

Idea
↓
Notion Backlog
↓
Research
↓
PRD
↓
GitHub Documentation
↓
Codex Development
↓
QA
↓
Deploy
↓
Analytics
↓
Builder OS Update

---

## Single Source of Truth

Item	Source
Vision	GitHub
Workflow	GitHub
Playbook	GitHub
Source Code	GitHub
Backlog	Notion
Sprint	Notion
Project Status	Notion
Decisions	Notion
Development	Codex

---

## Design Principles

Single Responsibility

각 시스템은 하나의 역할만 수행한다.

---

Documentation First

프로젝트보다 문서가 먼저 존재해야 한다.

---

AI First

AI가 수행 가능한 업무는 사람이 하지 않는다.

---

Automation by Default

반복되는 작업은 반드시 자동화 후보로 등록한다.

---

Reuse Before Build

새로운 것을 만들기 전에 기존 Workflow와 Template을 재사용한다.

---

## Future Architecture

Builder OS는 아래 방향으로 발전한다.

Idea
↓
AI Evaluation
↓
Notion Registration
↓
PRD Generation
↓
GitHub Issue
↓
Codex Development
↓
QA Agent
↓
Deploy
↓
Analytics
↓
Builder OS Learning

---

## Long-term Vision

Builder OS의 최종 목표는 AI Native Software Company의 운영체제가 되는 것이다.

사람은 방향을 결정하고,

AI는 제품을 만든다.

---

## References

* README.md
* Vision.md
* BuilderWorkflow.md
* Playbook.md
* Agents.md
