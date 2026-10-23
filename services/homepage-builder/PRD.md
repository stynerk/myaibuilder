# Homepage Builder PRD

| 항목 | 내용 |
|---|---|
| Owner | HJ |
| Status | Draft (Owner 검토 필요) |
| Priority | P0 |
| Issue | 등록 예정 |
| Last Updated | 2026-10-06 |

> **포지셔닝 제안 (확인 필요)**: 기존 문서의 목표는 "기업 홈페이지를 빠르게 생성하는 Builder"였다.
> 이 초안은 v0의 첫 고객을 **Builder OS 자신**으로 좁혔다. 즉 "다음 서비스의 수요를 검증할 랜딩페이지를 하루 안에 띄우는 도구"로 정의했다.
> 이유는 세 가지다.
>
> 1. 다음에 만들 모든 서비스(Diet AI 등)가 출시 전 수요 검증용 랜딩페이지를 필요로 한다. 그래서 North Star(TTFU) 단축에 바로 기여한다.
> 2. 외부 고객(기업 홈페이지 시장)은 경쟁이 치열하다 (Wix, Framer, 각종 AI 사이트 빌더). 차별점 가설이 아직 없다.
> 3. 내부에서 먼저 반복 사용하며 검증한 Workflow가 외부 제품화의 근거가 된다.
>
> 외부 판매용으로 바로 가려면 Problem과 Target을 다시 정의해야 한다 (Open Questions Q1).

## 1. Problem

- **누구의**: 아이디어를 빠르게 검증하려는 1인 빌더 (v0: Builder OS Owner)
- **어떤**: 서비스마다 랜딩페이지(소개, CTA, 대기자 수집, 분석)를 매번 새로 만드느라 검증 착수가 늦어진다. 이 시간이 TTFU의 상당 부분을 차지한다.
- **현재 우회 방법**: 노코드 빌더를 수작업으로 쓰거나, 매번 코드로 새로 만든다. 카피, SEO, 분석 설정을 매번 반복한다.
- **왜 지금**: Roadmap Phase 2–4에서 서비스 3개를 연속으로 검증해야 한다. 지금 만들면 세 번 모두 재사용할 수 있다.

### JTBD

> When 새 서비스 아이디어가 Go 판정을 받으면,
> I want to 한 페이지 브리프만 써서 수요 검증용 랜딩페이지를 바로 배포하고,
> so I can 개발 전에 실제 사용자 반응(대기자 수, 전환율)을 확인할 수 있다.

## 2. Hypotheses & Risks

| ID | 가설 | 틀렸을 때 영향 | 검증 방법 |
|---|---|---|---|
| H1 | 브리프(마크다운 1장)만으로 AI가 출시 가능한 품질의 랜딩페이지를 만든다 | 수작업 수정이 길어져 시간 단축 효과가 사라진다 | 브리프 → 배포까지 걸린 시간, 사람이 수정한 횟수 |
| H2 | 같은 Workflow를 다른 서비스에도 수정 없이 재사용할 수 있다 | 서비스마다 다시 만들어야 한다 | Service #1 적용 시 코드·프롬프트 변경량 |
| H3 | 랜딩페이지 대기자 수집으로 서비스 수요를 판단할 수 있다 | 검증 신호로 쓸 수 없다 | Service #1에서 방문자 대비 가입률 측정 가능 여부 |

| Risk | 유형 | Mitigation |
|---|---|---|
| AI가 생성한 카피·디자인 품질이 낮다 | Value | 검증된 섹션 Component 세트 + 카피 프롬프트를 고정 (Design System) |
| 배포·폼·분석 연동에 시간을 빼앗긴다 | Feasibility | 매니지드 서비스 사용, 첫 1회 셋업 후 템플릿화 |
| 범위가 "범용 홈페이지 빌더"로 커진다 | Business | 단일 페이지 + 대기자 수집으로 범위 고정 (Stop Rule) |

## 3. Success Metrics

| 구분 | 지표 | 목표 | 측정 방법 |
|---|---|---|---|
| North Star | 브리프 작성 완료 → Live URL까지 걸린 시간 | ≤ 4시간 (최대 1일) | 브리프 커밋 시각과 배포 시각 비교 |
| 재사용성 | Service #1 적용 시 템플릿 코드 수정 라인 | ≤ 50줄 | PR diff |
| Guardrail | 모바일 Lighthouse (Performance, Accessibility) | 각 90 이상 | Lighthouse |
| Guardrail | 폼 제출부터 데이터 저장까지 성공률 | 100% (QA 기준) | QA 테스트 |

- **Kill Criteria**: 두 번째 페이지를 만들 때도 4시간을 넘고, 수작업 수정이 주요 원인이면 자체 빌더를 중단한다. 대신 기존 노코드 툴 + 프롬프트 Workflow로 전환한다.

## 4. MVP Scope

| 포함 | 검증하는 가설 |
|---|---|
| 브리프 템플릿 (서비스명, 문제, 타깃, 핵심 가치, CTA) | H1 |
| 브리프 → 페이지 생성 skill (`/landing`) | H1, H2 |
| 고정 섹션 세트: Hero, Problem, Solution, How it works, FAQ, CTA | H1 |
| 대기자 이메일 수집 폼 | H3 |
| 기본 SEO (title, description, OG 이미지) + Analytics (방문, 전환) | H3 |
| 정적 사이트 배포 (서비스별 서브도메인 또는 경로) | H1 |

| 제외 | 이유 |
|---|---|
| 다중 페이지 기업 홈페이지, CMS | 핵심 가설과 무관하며 2주를 넘는다 |
| 비주얼 에디터 UI | 사용자가 Owner 1명이면 브리프 수정으로 충분하다 |
| 결제, 회원가입, 다국어 | 수요 검증 단계에서는 불필요하다 |
| 외부 고객용 멀티 테넌시 | H1–H3 검증 이후에 결정한다 (Q1) |

## 5. User Flow

```text
/new-service Go 판정
  → brief.md 작성 (10분)
  → /landing 실행 → 로컬 Preview
  → 수정 지시 (선택)
  → PR → qa 검증 → 배포
  → 대기자 수와 전환율 확인
```

## 6. Requirements

| ID | Requirement | Priority | 수용 기준 |
|---|---|---|---|
| FR-001 | 브리프 1개로 랜딩페이지 생성 | Must | 브리프 필수 필드만으로 6개 섹션이 모두 채워진 페이지가 생성된다 |
| FR-002 | 대기자 이메일 수집 | Must | 유효한 이메일 제출 시 저장되고 완료 메시지가 보인다. 잘못된 형식은 거부한다 |
| FR-003 | Analytics | Must | 페이지 방문과 폼 제출 이벤트가 대시보드에 기록된다 |
| FR-004 | SEO 메타 | Must | title, description, OG 태그가 브리프 값으로 채워진다 |
| FR-005 | 서비스별 독립 배포 | Must | 두 번째 브리프로 첫 페이지에 영향 없이 별도 URL을 배포할 수 있다 |
| FR-006 | 반응형 | Must | 360px, 768px, 1280px에서 레이아웃이 깨지지 않고, CTA Touch Target이 44px 이상이다 |

### Non-functional

- Performance: 모바일 Lighthouse Performance 90 이상
- Accessibility: Lighthouse Accessibility 90 이상, 키보드로 폼 제출 가능
- Security: 폼 스팸 방지 (honeypot 이상), 시크릿 커밋 금지

## 7. Technical Notes

> `engineer` agent가 확정한다. 아래는 검토할 후보다.

| 결정 | 후보 | 고려 사항 |
|---|---|---|
| 프레임워크 | Astro / Next.js (static export) | 정적 페이지라면 Astro가 가볍다. 이후 앱으로 확장하려면 Next.js |
| UI | Tailwind + shadcn/ui 스타일 Component | Design System 우선순위와 맞춘다 |
| 배포 | Vercel / Cloudflare Pages | 무료 플랜, Preview URL, 서브도메인 |
| 폼 저장 | 매니지드 폼 서비스 / Serverless + DB | 셋업 시간 대비 데이터 소유권 |
| Analytics | Plausible / GA4 / Vercel Analytics | 프라이버시, 전환 이벤트 지원 |

## 8. Open Questions

- [ ] **Q1.** v0 첫 고객을 "Builder OS 내부(수요 검증용)"로 좁히는 데 동의하는가? 아니면 외부 기업 고객이 목표인가?
- [ ] **Q2.** 첫 실전 적용 대상(Service #1)은 무엇인가? (후보: Diet AI, Medicine AI)
- [ ] **Q3.** 도메인 보유 여부, 그리고 서비스별 서브도메인 사용 가능 여부
- [ ] **Q4.** 폼·분석 도구 비용 상한 (무료 플랜만 쓸 것인가?)

## Related

- [Vision](../../os/vision.md) · [Playbook](../../os/playbook.md) · [Design System](../../os/design-system.md) · [ADR-0001](../../os/decisions/0001-restructure.md)
