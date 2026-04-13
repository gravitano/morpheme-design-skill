# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## About This Repository

This repository contains the **Morpheme UI Design System** reference documentation — a token-based design system by gits.id. It is used as the authoritative source of truth for design tokens, component specs, and visual guidelines when building UIs.

## Design System Reference

All design decisions should follow **@DESIGN.md**, which documents:

- **Color system** — 3-layer token architecture: Foundation → Brand → Semantic
- **Typography** — Poppins font family, type scale (12px–72px), weight usage rules
- **Spacing** — 4px base unit grid (spacing-1 through spacing-24)
- **Border radius, shadows, blur/opacity** — elevation and surface tokens
- **Component specs** — Buttons, inputs, cards, badges, alerts, modals, navigation
- **Layout & grid** — 12-column, 1280px max-width, breakpoints (xs→2xl)
- **Motion** — Duration and easing tokens for micro-interactions to page transitions
- **Accessibility** — 4.5:1 contrast ratio, focus ring spec, semantic color usage

## Key Design Constraints

- Always use **semantic tokens** in components (e.g. `--color-primary`, `--shadow-md`), never raw foundation values, to preserve theming capability.
- Primary brand color: `#1D6EEB` (colorPrimary500). Secondary: `#E55B05` (colorSecondary500).
- Font stack: `"Poppins", -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif`.
- All spacing must be multiples of 4px.
- Animations must use only `opacity` and `transform` (no layout-triggering properties). Respect `prefers-reduced-motion`.
- Focus ring: `outline: 2px solid #1D6EEB; outline-offset: 2px`.
- Copy style: sentence case, action-first button labels, explicit error messages with solutions.

## CSS Variables

The full CSS custom property definitions are in `DESIGN.md § 14`. Always prefer these variables over hardcoded values:

```css
/* Primary entry points */
--color-primary: #1D6EEB;
--color-error:   #F04438;
--color-success: #12B76A;
--color-warning: #F79009;
--color-info:    #28A0F8;
--font-family:   "Poppins", -apple-system, sans-serif;
```

## Skills

- **`/morpheme-design`** — Invoke this skill when building any web page, app, or UI component. It enforces all Morpheme Design System tokens, component specs, and accessibility guidelines automatically. Trigger: any frontend/UI creation or modification task.
