---
name: morpheme-design
description: >
  Enforce the Morpheme UI Design System when building web pages, apps, or UI components.
  Ensures all design tokens, colors, typography, spacing, components, and accessibility
  guidelines follow the Morpheme specification from DESIGN.md.
  Use when user asks to build, create, or modify a web page, app, landing page,
  dashboard, form, UI component, or any frontend interface. Also use when user asks
  to style, theme, or design any web element.
---

# Morpheme Design System — Agent Skill

You are building UI that **must** follow the Morpheme UI Design System. Read `@DESIGN.md` as your authoritative source of truth before writing any HTML/CSS/JS.

## Pre-flight checklist

Before generating any UI code:

1. Review all specifications in this skill document — tokens, component specs, and rules are defined below.
2. Identify which components are needed (see Component specifications section).
3. Plan the layout using the 12-column grid system (see Layout & grid section).
4. Choose the correct typography and spacing tokens (see Typography and Spacing sections below).

## Mandatory CSS variables

Every page/component MUST include the full `:root` CSS variables block from DESIGN.md §14. Never hardcode values — always reference variables:

```css
/* Always use semantic tokens */
color: var(--color-primary);        /* NOT #1D6EEB */
padding: var(--space-6);            /* NOT 24px */
border-radius: var(--radius-lg);    /* NOT 8px */
box-shadow: var(--shadow-md);       /* NOT the raw value */
font-family: var(--font-family);    /* NOT "Poppins" directly */
```

## Color rules

- **3-layer system**: Foundation → Brand → Semantic. Always use semantic tokens in components.
- **Primary**: `--color-primary: #1D6EEB` — all interactive elements (buttons, links, focus).
- **Secondary**: `--color-secondary: #E55B05` — sparingly for accents, pills, badges.
- **Semantic states**: `--color-info`, `--color-warning`, `--color-success`, `--color-error`.
- **Neutrals**: Use `--color-gray-{25..900}` scale for text, borders, backgrounds.
- Include the full primary scale (`colorPrimary25`–`colorPrimary900`) and secondary scale as CSS variables when hover/active states are needed.

## Typography rules

- **Font**: `"Poppins"` with system fallback stack. Load from Google Fonts:
  ```html
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;500;600;700&display=swap" rel="stylesheet">
  ```
- **Weight usage**: Regular (400) body, Medium (500) labels/nav, Semibold (600) headings, Bold (700) display/CTA.
- **Display sizes** (24px+): use `letter-spacing: -0.02em`.
- **Body default**: 16px / 24px line-height.
- **Max 2 weights** per component.

## Spacing rules

- All spacing is **multiples of 4px**. Use `--space-{1..24}` tokens.
- Default component padding: `--space-4` (16px).
- Card inner padding: `--space-6` (24px).
- Section gaps: `--space-8` (32px) small, `--space-12` (48px) medium, `--space-24` (96px) large.

## Component specifications

When building these components, follow the specs below exactly:

### Buttons
- **Sizes**: `lg` 52px, `md` 44px (default), `sm` 36px, `xs` 28px — font/icon scale proportionally
- **Color groups**: Primary (`--color-primary`) and Destructive (`--color-error`)
- **4 style variants per color**:
  - **Filled**: solid bg, white text/icon
  - **Outlined**: transparent bg, 1.5px border in brand color, brand-colored text/icon
  - **Text (ghost)**: no border/bg, brand-colored text/icon
  - **Icon-only**: square (`--radius-lg`) or rounded (`--radius-full`), width = height
- **Icon layouts**: text-only, icon-left, icon-right, icon-both (gap 8px)
- **States**: default → hover (1 shade darker / tint bg) → active (2 shades) → focus (outline 2px) → disabled (`opacity: 0.4`) → loading (3-dot indicator)
- Hover transitions: 100ms ease-out minimum

### Form inputs
- Height: 44px, border `1.5px solid var(--color-gray-300)`, `--radius-lg`
- Focus: primary border + `box-shadow: 0 0 0 4px rgba(29,110,235,0.12)`
- Error: error border + `box-shadow: 0 0 0 4px rgba(240,68,56,0.12)`
- Labels: Poppins Medium 14px, `--color-gray-700`
- All inputs MUST have associated `<label>` via `for`/`id`

### Cards
- White bg, `1px solid var(--color-gray-200)`, `--radius-xl` (12px), `--space-6` padding
- Shadow: `--shadow-md`, hover: `--shadow-lg` with 150ms transition

### Badges/Chips
- Pill shape (`--radius-full`), Poppins Medium 12px, 22px height
- Info: `bg #EFF8FF, text #175CD3`
- Success: `bg #ECFDF3, text #027A48`
- Warning: `bg #FFFAEB, text #B54708`
- Error: `bg #FEF3F2, text #B42318`

### Alerts
- 16px padding, `--radius-lg`, `border-left: 4px solid {semantic-color}`
- Background uses the lightest tint of the semantic color

### Modals
- `--radius-2xl` (16px), `--shadow-2xl`, max-width 560px
- Backdrop: `rgba(16,24,40,0.6)`
- Header/footer separated by `1px solid var(--color-gray-200)`

### Navigation/Sidebar
- Width 260px, white bg, border-right `1px solid var(--color-gray-200)`
- Nav items: 40px height, Poppins Medium 14px, `--radius-md`
- Active: primary bg light, primary text, font-weight 600

## Layout & grid

- Max content width: **1280px**, centered with auto margins.
- Horizontal padding: 16px mobile, 24px tablet, 40px desktop.
- 12-column grid with 24px gutters.
- Breakpoints: `xs: 0`, `sm: 640px`, `md: 768px`, `lg: 1024px`, `xl: 1280px`, `2xl: 1536px`.

## Shadows & elevation

Use the shadow scale for depth hierarchy:
- `--shadow-sm`: subtle elevation (inputs, small elements)
- `--shadow` / `--shadow-md`: cards, dropdowns
- `--shadow-lg` / `--shadow-xl`: floating elements, popovers
- `--shadow-2xl`: modals, dialogs

## Motion & animation

- Micro interactions: 100–150ms ease-out
- Hover: 100ms ease-out (NEVER instant)
- Modal open: 200ms ease-out (scale 0.95→1, opacity 0→1)
- Only animate `opacity` and `transform` — never layout properties
- Always include `prefers-reduced-motion` media query:
  ```css
  @media (prefers-reduced-motion: reduce) {
    *, *::before, *::after {
      animation-duration: 0.01ms !important;
      transition-duration: 0.01ms !important;
    }
  }
  ```

## Accessibility — non-negotiable

- Contrast: **4.5:1** body text, **3:1** large UI elements.
- Focus ring on ALL interactive elements: `outline: 2px solid var(--color-primary); outline-offset: 2px`.
- Color is never the sole differentiator — always pair with icon or text label.
- All `<input>` elements must have a linked `<label>`.
- Logical tab order.
- All icon-only buttons must have `aria-label`.

## Icons

- Use outline-style icons (1.5–2px stroke).
- Sizes: 16px inline, 20px default, 24px header/feature.
- Recommended: Heroicons, Phosphor Icons, or Feather Icons.
- Icon color follows parent text hierarchy.

## Copy & writing style

- **Sentence case** everywhere (not Title Case).
- **Action-first** button labels: "Save changes", "Delete account", "Create new".
- Error messages must be explicit and provide a solution.
- Placeholders use concrete examples, not generic instructions.

## Output structure

When generating a complete page, structure the HTML as:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Page Title</title>
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;500;600;700&display=swap" rel="stylesheet">
  <style>
    /* 1. CSS Reset / Normalize */
    /* 2. :root variables from DESIGN.md §14 */
    /* 3. Base styles */
    /* 4. Component styles using var() tokens */
    /* 5. Layout styles */
    /* 6. Responsive styles */
    /* 7. prefers-reduced-motion */
  </style>
</head>
<body>
  <!-- Semantic HTML5 structure -->
</body>
</html>
```

## Self-review checklist

Before presenting the final code, verify:

- [ ] All colors use CSS variables, not hardcoded hex
- [ ] All spacing is multiples of 4px via `--space-*` tokens
- [ ] Typography uses Poppins with correct weight hierarchy
- [ ] All interactive elements have hover transitions (min 100ms)
- [ ] Focus rings on all focusable elements
- [ ] All form inputs have linked labels
- [ ] `prefers-reduced-motion` media query included
- [ ] Responsive layout with correct breakpoints
- [ ] Shadows match elevation hierarchy
- [ ] Border-radius uses `--radius-*` tokens
- [ ] Sentence case in all copy
- [ ] No layout-triggering animations (only opacity/transform)
