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

You are building UI that **must** follow the Morpheme UI Design System. The full design specification is in [references/DESIGN.md](references/DESIGN.md) — consult it for detailed token values, component specs, and guidelines.

## Pre-flight checklist

Before generating any UI code:

1. Review all specifications in this skill document. For the full authoritative reference, see [references/DESIGN.md](references/DESIGN.md).
2. **If modifying an existing component** — read the file first, then change only what is needed. Do not rewrite the whole component.
3. Identify which components are needed (see Component specifications section).
4. Plan the layout using the 12-column grid system (see Layout & grid section).
5. Choose the correct typography and spacing tokens (see Typography and Spacing sections below).
6. Detect the framework, CSS tooling, and TypeScript usage from the project before writing a single line of code (see Output structure section).

## Mandatory CSS variables

**Skip this section if Tailwind CSS is detected** — use the Tailwind config approach instead (see Output structure → Tailwind CSS).

For all other setups, every page/component MUST include the full `:root` CSS variables block in the global stylesheet. Never hardcode values — always reference variables:

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
- Include the full primary scale (`--color-primary-25`–`--color-primary-900`) and secondary scale as CSS variables when hover/active states are needed.

## Typography rules

- **Font**: `"Poppins"` with system fallback stack. Load method depends on framework — see Output structure section for the correct approach per framework. For plain HTML only:
  ```html
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;500;600;700&display=swap" rel="stylesheet">
  ```
- **Weight usage**: Regular (400) body, Medium (500) labels/nav, Semibold (600) headings, Bold (700) display/CTA.
- **Display sizes** (24px+): use `letter-spacing: -0.02em`.
- **Body default**: 16px / 24px line-height.
- **Max 2 weights** per component.

## Spacing rules

- All spacing is **multiples of 4px**.
- **Plain CSS / CSS Modules**: use `--space-{1..24}` tokens (e.g. `var(--space-6)` for 24px).
- **Tailwind (v3 or v4)**: use utility classes (`p-6`, `gap-4`, `mt-8`) — do NOT mix with `var(--space-*)`.
- Default component padding: 16px (`--space-4` / `p-4`).
- Card inner padding: 24px (`--space-6` / `p-6`).
- Section gaps: 32px small, 48px medium, 96px large.

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
- Focus: primary border + `box-shadow: 0 0 0 4px var(--color-primary-focus-ring, rgba(29,110,235,0.12))`
- Error: error border + `box-shadow: 0 0 0 4px var(--color-error-focus-ring, rgba(240,68,56,0.12))`
- Labels: Poppins Medium 14px, `--color-gray-700`
- All inputs MUST have associated `<label>` via `for`/`id`

### Cards
- White bg, `1px solid var(--color-gray-200)`, `--radius-xl` (12px), `--space-6` padding
- Shadow: `--shadow-md`, hover: `--shadow-lg` with 150ms transition

### Badges/Chips
- Pill shape (`--radius-full`), Poppins Medium 12px, 22px height
- Info: `background: var(--color-info-bg, #EFF8FF); color: var(--color-info-text, #175CD3)`
- Success: `background: var(--color-success-bg, #ECFDF3); color: var(--color-success-text, #027A48)`
- Warning: `background: var(--color-warning-bg, #FFFAEB); color: var(--color-warning-text, #B54708)`
- Error: `background: var(--color-error-bg, #FEF3F2); color: var(--color-error-text, #B42318)`

### Alerts
- 16px padding, `--radius-lg`
- Info: `background: var(--color-info-bg, #EFF8FF); border-left: 4px solid var(--color-info, #28A0F8)`
- Success: `background: var(--color-success-bg, #ECFDF3); border-left: 4px solid var(--color-success, #12B76A)`
- Warning: `background: var(--color-warning-bg, #FFFAEB); border-left: 4px solid var(--color-warning, #F79009)`
- Error: `background: var(--color-error-bg, #FEF3F2); border-left: 4px solid var(--color-error, #F04438)`

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

**Follow this priority order when determining output format:**

1. **Explicit user request** — if the user specifies a framework or format (e.g. "build in HTML", "make a Vue component", "use plain CSS"), always follow that instruction regardless of what the project uses.
2. **Auto-detect from project** — if no explicit request, check `package.json` dependencies and config files to determine the framework.
3. **Plain HTML fallback** — only if no framework is detected and the user hasn't specified otherwise.

Never default to plain HTML when a framework is present in the project and the user hasn't explicitly asked for HTML.

### Detection signals

#### Framework

| Framework | Signal files / deps |
|-----------|-------------------|
| Next.js | `next` in deps, `next.config.*` |
| React (Vite/CRA) | `react` in deps, `vite.config.*`, no `next` |
| TanStack Start | `@tanstack/react-start` or `@tanstack/start` (legacy) in deps, `app/routes/` directory |
| Nuxt 4 | `nuxt@^4` in `package.json`, or `compatibilityVersion: 4` in `nuxt.config.*`, or `app/` dir with `components/`/`pages/` inside |
| Nuxt 3 | `nuxt@^3` in `package.json`, no signals above |
| Vue (Vite) | `vue` in deps, `vite.config.*`, no `nuxt.config.*` |
| Svelte / SvelteKit | `svelte` in deps, `svelte.config.*`, `.svelte` files |
| Analog.js | `@analogjs/platform` in deps, `vite.config.ts` with analog plugin |
| Solid.js | `solid-js` in deps, `.tsx` with `solid` imports |
| Plain HTML | No framework detected |

#### CSS tooling

| Tooling | Signal | How to apply Morpheme tokens |
|---------|--------|------------------------------|
| Tailwind CSS v4 | `tailwindcss@^4` in deps, `@import "tailwindcss"` in CSS, no `tailwind.config.*` | Define Morpheme tokens in `@theme` block in CSS |
| Tailwind CSS v3 | `tailwindcss@^3` in deps, `tailwind.config.*` present | Extend config with Morpheme tokens via `theme.extend` |
| CSS Modules | `*.module.css` files in project | Write CSS vars in a shared `tokens.module.css`, import per component |
| styled-components / Emotion | `styled-components` or `@emotion/react` in deps | Use a `ThemeProvider` with Morpheme tokens as theme values |
| Plain CSS | No tooling detected | Add `:root` CSS variables block to global stylesheet |

#### TypeScript vs JavaScript

| Signal | Output |
|--------|--------|
| `typescript` in deps, `tsconfig.json` present | `.tsx` / `.ts` files |
| No TypeScript detected | `.jsx` / `.js` files |

#### Dark mode

| Signal | Behavior |
|--------|----------|
| Tailwind v3: `darkMode` in `tailwind.config.*` | Follow existing strategy (`class` or `media`) — add `dark:` variants to utility classes |
| Tailwind v4: `@variant dark` or `@custom-variant dark` in CSS | Follow existing dark mode variant — add `dark:` variants to utility classes |
| `prefers-color-scheme` used in existing CSS | Add `@media (prefers-color-scheme: dark)` overrides |
| No dark mode detected | Light mode only — do not add dark mode unless explicitly asked |

---

### Tailwind CSS (any framework)

Detect Tailwind version before writing any token config.

#### Tailwind v4

No `tailwind.config.*` — tokens are defined in CSS using `@theme`:

```css
/* globals.css / app.css */
@import "tailwindcss";

@theme {
  /* Colors */
  --color-primary:           #1D6EEB;
  --color-primary-25:        #F5F8FF;
  --color-primary-50:        #EBF3FF;
  --color-primary-100:       #BFDBFE;
  --color-primary-500:       #1D6EEB;
  --color-primary-600:       #1B69C2;
  --color-primary-700:       #1554A1;
  --color-primary-900:       #072D60;
  --color-secondary:         #E55B05;
  --color-secondary-500:     #E55B05;
  --color-error:             #F04438;
  --color-success:           #12B76A;
  --color-warning:           #F79009;
  --color-info:              #28A0F8;
  --color-gray-25:           #FCFCFD;
  --color-gray-50:           #F9FAFB;
  --color-gray-100:          #F2F4F7;
  --color-gray-200:          #EAECF0;
  --color-gray-300:          #D0D5DD;
  --color-gray-400:          #98A2B3;
  --color-gray-500:          #667085;
  --color-gray-600:          #475467;
  --color-gray-700:          #344054;
  --color-gray-800:          #1D2939;
  --color-gray-900:          #101828;

  /* Typography */
  --font-sans: "Poppins", system-ui, sans-serif;

  /* Border radius */
  --radius-sm:   4px;
  --radius-md:   6px;
  --radius-lg:   8px;
  --radius-xl:   12px;
  --radius-2xl:  16px;

  /* Shadows */
  --shadow-sm:  0 1px 2px rgba(16,24,40,0.05);
  --shadow:     0 1px 3px rgba(16,24,40,0.10), 0 1px 2px rgba(16,24,40,0.06);
  --shadow-md:  0 4px 8px -2px rgba(16,24,40,0.10), 0 2px 4px -2px rgba(16,24,40,0.06);
  --shadow-lg:  0 12px 16px -4px rgba(16,24,40,0.08), 0 4px 6px -2px rgba(16,24,40,0.03);
  --shadow-xl:  0 20px 24px -4px rgba(16,24,40,0.08), 0 8px 8px -4px rgba(16,24,40,0.03);
  --shadow-2xl: 0 24px 48px -12px rgba(16,24,40,0.18);

  /* Spacing — no override needed. Tailwind v4 default spacing unit is 0.25rem (4px),
     so p-4=16px, p-6=24px, p-8=32px etc. already match the Morpheme 4px grid exactly. */

  /* Motion */
  --duration-fast:   100ms;
  --duration-base:   150ms;
  --duration-slow:   200ms;
  --duration-slower: 300ms;
  --ease-out:    cubic-bezier(0.0, 0.0, 0.2, 1);
  --ease-in-out: cubic-bezier(0.4, 0.0, 0.2, 1);
}
```

Use utility classes: `bg-primary`, `text-gray-700`, `rounded-lg`, `shadow-md`, `p-6`, etc.

#### Tailwind v3

Extend `tailwind.config.ts` — do NOT add a separate `:root` block:

```ts
// tailwind.config.ts
export default {
  theme: {
    extend: {
      colors: {
        primary: {
          DEFAULT: '#1D6EEB',
          25: '#F5F8FF', 50: '#EBF3FF', 100: '#BFDBFE',
          500: '#1D6EEB', 600: '#1B69C2', 700: '#1554A1', 900: '#072D60',
        },
        secondary: { DEFAULT: '#E55B05', 500: '#E55B05' },
        error:   '#F04438',
        success: '#12B76A',
        warning: '#F79009',
        info:    '#28A0F8',
        gray: {
          25: '#FCFCFD', 50: '#F9FAFB', 100: '#F2F4F7', 200: '#EAECF0',
          300: '#D0D5DD', 400: '#98A2B3', 500: '#667085', 600: '#475467',
          700: '#344054', 800: '#1D2939', 900: '#101828',
        },
      },
      fontFamily: { sans: ['Poppins', 'system-ui', 'sans-serif'] },
      borderRadius: {
        sm: '4px', md: '6px', lg: '8px', xl: '12px', '2xl': '16px',
      },
      boxShadow: {
        sm:      '0 1px 2px rgba(16,24,40,0.05)',
        DEFAULT: '0 1px 3px rgba(16,24,40,0.10), 0 1px 2px rgba(16,24,40,0.06)',
        md:      '0 4px 8px -2px rgba(16,24,40,0.10), 0 2px 4px -2px rgba(16,24,40,0.06)',
        lg:      '0 12px 16px -4px rgba(16,24,40,0.08), 0 4px 6px -2px rgba(16,24,40,0.03)',
        xl:      '0 20px 24px -4px rgba(16,24,40,0.08), 0 8px 8px -4px rgba(16,24,40,0.03)',
        '2xl':   '0 24px 48px -12px rgba(16,24,40,0.18)',
      },
      spacing: {
        1: '4px', 2: '8px', 3: '12px', 4: '16px', 5: '20px', 6: '24px',
        8: '32px', 10: '40px', 12: '48px', 16: '64px', 20: '80px', 24: '96px',
      },
      transitionDuration: {
        fast: '100ms', base: '150ms', slow: '200ms', slower: '300ms',
      },
      transitionTimingFunction: {
        'ease-out':    'cubic-bezier(0.0, 0.0, 0.2, 1)',
        'ease-in-out': 'cubic-bezier(0.4, 0.0, 0.2, 1)',
      },
    },
  },
}
```

Use utility classes: `bg-primary`, `text-gray-700`, `rounded-lg`, `shadow-md`, `p-6`, etc.

---

### Next.js (App Router)

- `className` not `class`; `htmlFor` not `for`
- Load Poppins via `next/font/google`:
  ```tsx
  import { Poppins } from 'next/font/google'
  const poppins = Poppins({ subsets: ['latin'], weight: ['400','500','600','700'] })
  ```
- CSS variables go in `app/globals.css`, not inline `<style>` tags
- Add `'use client'` only when hooks or browser APIs are needed
- Prefer Server Components by default
- File placement: `components/ComponentName.tsx` (shared) or `app/(route)/components/ComponentName.tsx` (route-scoped)

### React (Vite / CRA)

- `className` not `class`; `htmlFor` not `for`
- Load Poppins via `<link>` in `index.html` or via a CSS `@import` in `index.css`
- CSS variables go in `index.css` or a dedicated `tokens.css`
- File placement: `src/components/ComponentName.tsx`

### TanStack Start

- Same JSX rules as React (`className`, `htmlFor`)
- Use `createFileRoute` for route files
- CSS variables in `app/styles/globals.css` or equivalent
- Load Poppins via `<link>` in root layout or CSS `@import`
- File placement: `app/routes/route-name.tsx` (routes) or `app/components/ComponentName.tsx` (shared)

### Vue / Nuxt

Generate `.vue` single-file components:

```vue
<template>
  <!-- semantic HTML -->
</template>

<script setup lang="ts">
// component logic
</script>

<style scoped>
/* component styles using var() tokens */
</style>
```

Detect Nuxt version before placing files:

| Signal | Version | Structure |
|--------|---------|-----------|
| `nuxt@^4` in `package.json` | Nuxt 4 | Source root is `app/` |
| `compatibilityVersion: 4` in `nuxt.config.ts` | Nuxt 4 | Source root is `app/` |
| `app/` directory exists with `components/`/`pages/` inside | Nuxt 4 | Source root is `app/` |
| `nuxt@^3` in `package.json`, no signals above | Nuxt 3 | Source root is project root |

**Nuxt 4** file placement:
- Components: `app/components/ComponentName.vue`
- Pages: `app/pages/page-name.vue`
- Composables: `app/composables/useHook.ts`
- Global CSS: `app/assets/css/tokens.css`
- Load Poppins via `@import url(...)` in `app/assets/css/main.css`

**Nuxt 3** file placement:
- Components: `components/ComponentName.vue` (auto-imported)
- Pages: `pages/page-name.vue`
- Composables: `composables/useHook.ts`
- Global CSS: `assets/css/tokens.css`
- Load Poppins via `@import url(...)` in `assets/css/main.css`

**Vue (Vite)** file placement: `src/components/ComponentName.vue`

### SvelteKit / Svelte

Generate `.svelte` components. Check which Svelte version is in use:

| Version | Signal | Event syntax |
|---------|--------|--------------|
| Svelte 5 (runes) | `svelte@^5`, uses `$state`, `$props` | `onclick={handler}` |
| Svelte 4 | `svelte@^4` | `on:click={handler}` |

```svelte
<script lang="ts">
  // Svelte 5: let { label } = $props()
  // Svelte 4: export let label: string
</script>

<main>
  <!-- semantic HTML -->
</main>

<style>
  /* component styles using var() tokens */
</style>
```

- CSS variables go in `src/app.css` or `src/lib/styles/tokens.css`
- Load Poppins via `@import url(...)` in `app.css`
- File placement: `src/lib/components/ComponentName.svelte`

### Analog.js (Angular)

Generate Angular components (`.component.ts` + `.component.html` + `.component.css`):

- Use `@Component` decorator with `standalone: true`
- Angular 17+: prefer `@if`, `@for` control flow over `*ngIf`, `*ngFor`
- Angular 16+: use Signals for reactive state (`signal()`, `computed()`, `effect()`) — not RxJS `BehaviorSubject` for simple local state
- Bindings: `[class]`, `(click)`
- CSS variables go in `src/styles.css`
- Load Poppins via `@import url(...)` in `styles.css`
- File placement: `src/app/components/component-name/component-name.component.ts`

```ts
import { Component, signal, computed } from '@angular/core'

@Component({
  selector: 'app-component-name',
  standalone: true,
  templateUrl: './component-name.component.html',
  styleUrl: './component-name.component.css',
})
export class ComponentNameComponent {
  // Use signals for reactive state
  count = signal(0)
  doubled = computed(() => this.count() * 2)
}
```

### Solid.js

Generate `.tsx` components using Solid primitives:

- Use `createSignal`, `createEffect` — not React hooks
- `class` not `className` (Solid uses `class`)
- CSS variables go in `src/index.css`
- Load Poppins via `@import url(...)` in global CSS
- File placement: `src/components/ComponentName.tsx`

```tsx
import { Component } from 'solid-js'

const ComponentName: Component = () => {
  return (
    <main>
      {/* semantic JSX */}
    </main>
  )
}

export default ComponentName
```

### Plain HTML (no framework detected)

Only fall back to full HTML when there is no framework in the project:

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
    /* 2. :root variables (§14) */
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

**Design tokens**
- [ ] All colors use tokens (CSS vars or Tailwind classes) — no hardcoded hex
- [ ] All spacing is multiples of 4px via `--space-*` or Tailwind spacing tokens
- [ ] Border-radius uses `--radius-*` tokens or equivalent Tailwind classes
- [ ] Shadows match elevation hierarchy (`--shadow-sm` → `--shadow-2xl`)

**Typography**
- [ ] Poppins loaded correctly for the framework (`next/font`, `@import`, etc.)
- [ ] Correct weight hierarchy: 400 body, 500 labels, 600 headings, 700 display/CTA
- [ ] Display sizes (24px+) have `letter-spacing: -0.02em`

**Interactions**
- [ ] All interactive elements have hover transitions (min 100ms ease-out)
- [ ] Focus rings on all focusable elements (`outline: 2px solid var(--color-primary); outline-offset: 2px`)
- [ ] Only `opacity` and `transform` animated — no layout-triggering properties
- [ ] `prefers-reduced-motion` media query included

**Accessibility**
- [ ] All form inputs have linked `<label>` via `for`/`id` (or `htmlFor` in JSX)
- [ ] All icon-only buttons have `aria-label`
- [ ] Color is not the sole differentiator — paired with icon or text

**Layout**
- [ ] Responsive layout with correct breakpoints (xs/sm/md/lg/xl/2xl)
- [ ] Max content width 1280px, centered

**Copy**
- [ ] Sentence case in all text
- [ ] Action-first button labels

**Framework-specific**
- [ ] Next.js: no React hooks in Server Components; `'use client'` added where needed
- [ ] Vue/Svelte: styles are scoped
- [ ] TypeScript: no untyped props or `any`
- [ ] Tailwind v3: tokens mapped in `tailwind.config.ts`, not inlined as arbitrary values like `bg-[#1D6EEB]`
- [ ] Tailwind v4: tokens defined in `@theme` block, not as raw CSS variables outside `@theme`
