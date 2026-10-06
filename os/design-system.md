# Design System

## Philosophy

- Mobile First
- Responsive by Default
- Component First
- Accessibility
- Content First

## UI References

새로운 Component를 만들기 전에 아래 순서로 기존 패턴을 먼저 검토한다.

1. [component.gallery](https://component.gallery)
2. [shadcn/ui](https://ui.shadcn.com)
3. [Radix UI](https://www.radix-ui.com)

## Responsive

| Breakpoint | 기준 |
|---|---|
| Mobile | 기본 설계 대상 |
| Tablet | Mobile 확장 |
| Desktop | Mobile 확장 |

Desktop은 Mobile을 확장하는 방식으로 설계한다.

## Core Rules

- Primary CTA는 화면당 하나이며 명확해야 한다.
- Touch Target은 44px 이상이다.
- Responsive는 필수다.
- 새로운 UI보다 검증된 Component를 재사용한다.
