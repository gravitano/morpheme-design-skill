# DESIGN.md — Morpheme UI Design System
> Based on Morpheme UI by gits.id (Morpheme UI • k6a9jw2v)
> The ultimate Figma UI kit and design system

---

## 1. Design Philosophy

Morpheme UI is a **universal and accessible** design system — built for projects of any scale. Its core principles:

- **Consistent** — The same tokens and components are used consistently across the entire interface.
- **Accessible** — Semantic colors follow real-world associations (red = danger, yellow = warning, green = positive) to reduce cognitive load.
- **Scalable** — A layered token system (foundation → brand → semantic) makes theming and customization straightforward.
- **Clean & Light** — The default visual style is light mode with crisp typography, subtle shadows, and generous whitespace.

---

## 2. Color System

Morpheme uses a **3-layer** color system:

```
Foundation Colors  →  Brand Colors  →  Semantic Colors
(primitives)          (product)        (contextual UI)
```

---

### 2.1 Foundation Colors

Base colors that remain constant regardless of theme.

| Token     | Hex       | RGB                | Usage                          |
|-----------|-----------|--------------------|--------------------------------|
| `white`   | `#FFFFFF` | rgb(255, 255, 255) | Backgrounds, light surfaces    |
| `black`   | `#000000` | rgb(0, 0, 0)       | Base typography color tokens   |
| `info`    | `#28A0F8` | rgb(40, 160, 248)  | Informational states           |
| `warning` | `#F79009` | rgb(247, 144, 9)   | Caution, warnings              |
| `success` | `#12B76A` | rgb(18, 183, 106)  | Positive feedback, completion  |
| `error`   | `#F04438` | rgb(240, 68, 56)   | Danger, errors, destructive    |

---

### 2.2 Brand Colors

The default brand colors are **blue** (primary) and **orange** (secondary). Both should be replaced to match the product's brand.

#### Primary Colors (Blue Scale)

| Token              | Value | Hex       | RGB                  |
|--------------------|-------|-----------|----------------------|
| `colorPrimary25`   | 25    | `#F5F8FF` | rgb(245, 248, 255)   |
| `colorPrimary50`   | 50    | `#EBF3FF` | rgb(235, 243, 255) *(approx)* |
| `colorPrimary100`  | 100   | `#BFDBFE` | rgb(191, 219, 254) *(approx)* |
| `colorPrimary200`  | 200   | `#93C5FD` | rgb(147, 197, 253) *(approx)* |
| `colorPrimary300`  | 300   | `#60A5FA` | rgb(96, 165, 250)  *(approx)* |
| `colorPrimary400`  | 400   | `#3B82F6` | rgb(59, 130, 246)  *(approx)* |
| `colorPrimary500`  | 500   | `#1D6EEB` | rgb(29, 110, 235)            |
| `colorPrimary600`  | 600   | `#1B69C2` | rgb(27, 105, 194) *(approx)* |
| `colorPrimary700`  | 700   | `#1554A1` | rgb(21, 84, 161)  *(approx)* |
| `colorPrimary800`  | 800   | `#0D4487` | rgb(13, 68, 135)  *(approx)* |
| `colorPrimary900`  | 900   | `#072D60` | rgb(7, 45, 96)               |

**Primary brand color: `#1D6EEB` (colorPrimary500)**
Used on all interactive elements: buttons, links, input focus, etc.

#### Secondary Colors (Orange/Red Scale)

| Token               | Value | Hex (approx) |
|---------------------|-------|--------------|
| `colorSecondary25`  | 25    | `#FFF9F5`    |
| `colorSecondary50`  | 50    | `#FFF3EB`    |
| `colorSecondary100` | 100   | `#FFE0C2`    |
| `colorSecondary200` | 200   | `#FFBC87`    |
| `colorSecondary300` | 300   | `#FF9855`    |
| `colorSecondary400` | 400   | `#FF7320`    |
| `colorSecondary500` | 500   | `#E55B05`    |
| `colorSecondary600` | 600   | `#CC4E00`    |
| `colorSecondary700` | 700   | `#A33E00`    |
| `colorSecondary800` | 800   | `#7A2E00`    |
| `colorSecondary900` | 900   | `#4A1C00`    |

Secondary is used sparingly — pills, alerts, accents, non-primary badges.

---

### 2.3 Semantic Colors

Semantic colors are mapped from foundation colors to specific UI contexts. Available in a 25–900 scale for each category:

- **Info** (based on blue `#28A0F8`) — informational notifications, tooltips
- **Warning** (based on yellow-orange `#F79009`) — caution, at-risk states
- **Success** (based on green `#12B76A`) — completion, valid, positive
- **Error** (based on red `#F04438`) — errors, destructive, blocked

Each semantic category has a 25–900 color scale:
```
{category}25   → lightest tint, for backgrounds/surfaces
{category}100  → light background (alert, badge bg)
{category}300  → border, outline
{category}500  → primary color (icon, bold text)
{category}700  → dark shade (hover state)
{category}900  → darkest tint
```

---

## 3. Typography

### Font Family
```
Primary font: Poppins
Fallback:     -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif
```

Morpheme uses **Poppins** — a geometric sans-serif with clean, modern character. Available in Regular (400), Medium (500), Semibold (600), and Bold (700).

### Type Scale

| Token        | Font Size | Line Height | Tracking  | Notes          |
|--------------|-----------|-------------|-----------|----------------|
| Display 2xl  | 72px      | 90px        | -2%       | Hero, splash   |
| Display xl   | 60px      | 72px        | -2%       | Page hero      |
| Display lg   | 48px      | 60px        | -2%       | Section hero   |
| Display md   | 36px      | 44px        | -2%       | Large heading  |
| Display sm   | 30px      | 38px        | —         | Heading        |
| Display xs   | 24px      | 32px        | —         | Sub-heading    |
| Text xl      | 20px      | 30px        | —         | Large body     |
| Text lg      | 18px      | 28px        | —         | Body large     |
| Text md      | 16px      | 24px        | —         | Body default   |
| Text sm      | 14px      | 20px        | —         | Body small     |
| Text xs      | 12px      | 18px        | —         | Caption, label |

### Weight Usage
```
Regular   (400) — body text, descriptions
Medium    (500) — labels, nav items, secondary headings
Semibold  (600) — headings, subheadings, important labels
Bold      (700) — display text, CTAs, emphasis
```

### Typography Rules
- Display sizes must always use `-2%` tracking (negative letter-spacing) for readability at large sizes.
- Default body text: **Text md (16px)**, line height 24px.
- Do not mix more than 2 weights in a single component.
- Use Poppins Semibold for all headings h1–h3.

---

## 4. Spacing System

Based on a **4px base unit**. All spacing is a multiple of 4.

```
4px   — spacing-1  (hairline)
8px   — spacing-2  (xs)
12px  — spacing-3  (sm)
16px  — spacing-4  (md — default padding)
20px  — spacing-5
24px  — spacing-6  (card inner padding)
32px  — spacing-8  (small section gap)
40px  — spacing-10
48px  — spacing-12 (section gap)
64px  — spacing-16
80px  — spacing-20
96px  — spacing-24 (large section)
```

---

## 5. Border Radius

```
0px   — radius-none  (sharp, tables)
2px   — radius-xs    (small badges)
4px   — radius-sm    (input, button sm)
6px   — radius-md    (default button, small card)
8px   — radius-lg    (default card)
12px  — radius-xl    (large card, modal)
16px  — radius-2xl   (feature card)
9999px— radius-full  (pill, avatar, chip)
```

---

## 6. Shadows

Morpheme uses shadows as elevation indicators on white and colored backgrounds.

### White Background (Light Surface)

```css
/* shadow-inner */
box-shadow: inset 0 2px 4px rgba(0,0,0,0.06);

/* shadow-none */
box-shadow: none;

/* shadow-sm */
box-shadow: 0 1px 2px rgba(16,24,40,0.05);

/* shadow (default) */
box-shadow: 0 1px 3px rgba(16,24,40,0.10), 0 1px 2px rgba(16,24,40,0.06);

/* shadow-md */
box-shadow: 0 4px 8px -2px rgba(16,24,40,0.10), 0 2px 4px -2px rgba(16,24,40,0.06);

/* shadow-lg */
box-shadow: 0 12px 16px -4px rgba(16,24,40,0.08), 0 4px 6px -2px rgba(16,24,40,0.03);

/* shadow-xl */
box-shadow: 0 20px 24px -4px rgba(16,24,40,0.08), 0 8px 8px -4px rgba(16,24,40,0.03);

/* shadow-2xl */
box-shadow: 0 24px 48px -12px rgba(16,24,40,0.18);
```

### Colored Background

Use the same shadow values but with slightly higher opacity due to different contrast on colored backgrounds.

---

## 7. Blur & Opacity

### Blur Scale (Backdrop / Glassmorphism)

| Token      | blur value | Opacity bg (light) | Opacity bg (dark) |
|------------|------------|--------------------|--------------------|
| `blur-sm`  | 4px        | rgba(255,255,255,0.4) | rgba(30,40,60,0.4) |
| `blur-md`  | 8px        | rgba(255,255,255,0.6) | rgba(30,40,60,0.6) |
| `blur-lg`  | 16px       | rgba(255,255,255,0.75)| rgba(30,40,60,0.75)|
| `blur-xl`  | 32px       | rgba(255,255,255,0.9) | rgba(30,40,60,0.9) |

```css
/* Example usage */
backdrop-filter: blur(8px);
background: rgba(255, 255, 255, 0.6);
```

### Opacity Scale

| Token       | Value  | Use case                            |
|-------------|--------|-------------------------------------|
| `opacity-sm`| ~0.20  | Very transparent overlay            |
| `opacity-md`| ~0.40  | Medium overlay                      |
| `opacity-lg`| ~0.65  | Heavy overlay, modal backdrop       |
| `opacity-xl`| ~0.90  | Nearly solid, glassmorphism max     |

Light variants use a white base, dark variants use a dark navy base.

---

## 8. Components (Guidelines)

### 8.1 Buttons

Buttons are available in **two color groups** (Primary, Destructive) × **four style variants** (Filled, Outlined, Text, Icon-only) × **four sizes** × **five states**.

#### Sizes

| Size | Height | Padding (h) | Font size | Icon size | Icon-only width |
|------|--------|-------------|-----------|-----------|-----------------|
| `lg` | 52px   | 0 24px      | 18px      | 24px      | 52px            |
| `md` | 44px   | 0 18px      | 16px      | 20px      | 44px            |
| `sm` | 36px   | 0 14px      | 14px      | 16px      | 36px            |
| `xs` | 28px   | 0 10px      | 12px      | 14px      | 28px            |

- Font weight: Medium (500) for all sizes.
- Default size is `md` (44px).

#### Icon placement

Every non-icon-only button supports these content layouts:

| Layout | Description |
|--------|-------------|
| Text only | Label centered, no icon |
| Icon left | Icon before label, gap 8px |
| Icon right | Icon after label, gap 8px |
| Icon both | Icons on both sides of label, gap 8px |

Icon-only buttons come in two shapes:
- **Square** — `border-radius: 8px` (radius-lg)
- **Rounded** — `border-radius: 9999px` (radius-full)

#### Style variants

##### Filled

```
Primary Filled:
  Background: colorPrimary500 (#1D6EEB)
  Text: #FFFFFF
  Icon: #FFFFFF
  Border: none
  Border-radius: 8px (radius-lg)
  Hover: colorPrimary600 (#1B69C2)
  Focus: outline 2px solid colorPrimary500, offset 2px
  Active: colorPrimary700 (#1554A1)
  Disabled: opacity 0.4, cursor not-allowed

Destructive Filled:
  Background: error500 (#F04438)
  Text: #FFFFFF
  Icon: #FFFFFF
  Hover: #D92D20
  Active: #B42318
  Disabled: opacity 0.4
```

##### Outlined

```
Primary Outlined:
  Background: transparent
  Border: 1.5px solid colorPrimary500 (#1D6EEB)
  Text: colorPrimary500
  Icon: colorPrimary500
  Border-radius: 8px
  Hover: background colorPrimary25 (#F5F8FF)
  Active: background colorPrimary50 (#EBF3FF)
  Disabled: opacity 0.4

Destructive Outlined:
  Background: transparent
  Border: 1.5px solid error500 (#F04438)
  Text: #F04438
  Icon: #F04438
  Hover: background #FEF3F2
  Active: background #FEE4E2
  Disabled: opacity 0.4
```

##### Text (Ghost)

```
Primary Text:
  Background: transparent
  Border: none
  Text: colorPrimary500 (#1D6EEB)
  Icon: colorPrimary500
  Hover: background colorPrimary25 (#F5F8FF)
  Active: background colorPrimary50 (#EBF3FF)
  Disabled: opacity 0.4

Destructive Text:
  Background: transparent
  Border: none
  Text: #F04438
  Icon: #F04438
  Hover: background #FEF3F2
  Active: background #FEE4E2
  Disabled: opacity 0.4
```

##### Icon-only

Same color/state rules as the corresponding style (filled, outlined, or text).
Width equals height (square aspect ratio). Two shapes available:

```
Icon-only (square):  border-radius: 8px (radius-lg)
Icon-only (rounded): border-radius: 9999px (radius-full)
```

#### Loading state

When loading, the button label and icon are replaced by a **3-dot animated indicator** (centered). The button retains its size, variant, and color. `pointer-events: none` during loading.

```css
.btn-loading {
  pointer-events: none;
  position: relative;
}
/* 3 dots: 6px circles, gap 4px, opacity pulse animation */
```

#### States summary

| State | Change |
|-------|--------|
| Default | Base appearance |
| Hover | Background shifts one shade darker (filled) or adds tint bg (outlined/text) |
| Focus | `outline: 2px solid currentColor; outline-offset: 2px` |
| Active | Background shifts two shades darker (filled) or deeper tint (outlined/text) |
| Disabled | `opacity: 0.4; cursor: not-allowed; pointer-events: none` |
| Loading | Content replaced by 3-dot indicator, pointer-events none |

#### Transition

All state changes: `100ms ease-out` minimum. Only animate `background`, `opacity`, `box-shadow` — no layout-triggering properties.

### 8.2 Form Inputs

```
Height: 44px (default)
Background: #FFFFFF
Border: 1.5px solid #D0D5DD
Border-radius: 8px
Padding: 0 14px
Font: Poppins Regular 16px
Color: #101828

Focus:
  Border: 1.5px solid #1D6EEB
  Box-shadow: 0 0 0 4px rgba(29,110,235,0.12)

Error:
  Border: 1.5px solid #F04438
  Box-shadow: 0 0 0 4px rgba(240,68,56,0.12)

Placeholder: #667085
Label: Poppins Medium 14px, #344054
Helper text: Poppins Regular 14px, #667085
```

### 8.3 Cards

```
Background: #FFFFFF
Border: 1px solid #EAECF0
Border-radius: 12px
Padding: 24px
Shadow: shadow-md

Hover (interactive card):
  Shadow: shadow-lg
  transition: 150ms ease-out
```

### 8.4 Badges / Chips

```
Height: 22px
Padding: 2px 8px
Font: Poppins Medium 12px
Border-radius: 9999px (pill)

Info:    bg #EFF8FF, text #175CD3
Success: bg #ECFDF3, text #027A48
Warning: bg #FFFAEB, text #B54708
Error:   bg #FEF3F2, text #B42318
```

### 8.5 Alerts

```
Padding: 16px
Border-radius: 8px
Border-left: 4px solid {semantic color}
Font: Poppins Regular 14px

Info:    bg #EFF8FF, border #1D6EEB
Success: bg #ECFDF3, border #12B76A
Warning: bg #FFFAEB, border #F79009
Error:   bg #FEF3F2, border #F04438
```

### 8.6 Modals

```
Background: #FFFFFF
Border-radius: 16px
Padding: 24px
Shadow: shadow-2xl
Backdrop: rgba(16,24,40,0.6)
Max-width: 560px (default)

Header:
  Font: Poppins Semibold 18px
  Border-bottom: 1px solid #EAECF0
  Padding-bottom: 16px

Footer:
  Border-top: 1px solid #EAECF0
  Padding-top: 16px
  Display: flex, justify-content: flex-end, gap: 12px
```

### 8.7 Navigation / Sidebar

```
Background: #FFFFFF
Border-right: 1px solid #EAECF0
Width: 260px

Nav Item:
  Height: 40px
  Padding: 0 12px
  Font: Poppins Medium 14px
  Color: #667085
  Border-radius: 6px
  Hover: background #F9FAFB, color #344054
  Active: background #EFF8FF, color #1D6EEB, font-weight 600

Section label:
  Font: Poppins Semibold 12px
  Color: #98A2B3
  Letter-spacing: 0.05em
  Text-transform: uppercase
```

---

## 9. Iconography

- Style: **Outline** icons, 1.5–2px stroke
- Recommended libraries: Heroicons, Phosphor Icons, or Feather Icons
- Standard sizes: 16px (inline), 20px (default), 24px (feature/header)
- Icon color follows the parent text hierarchy
- Icon-only elements must always include `aria-label`

---

## 10. Motion & Animation

```
Micro interactions:  100–150ms  ease-out
Hover transitions:   100ms      ease-out
Modal open:          200ms      ease-out (scale 0.95→1, opacity 0→1)
Modal close:         150ms      ease-in
Drawer / sidebar:    250ms      ease-in-out
Toast / notification: 200ms     slide + fade
Page transitions:    300ms      ease-in-out
```

**Principles:**
- Only use `opacity` and `transform` for animations (avoid layout-triggering properties).
- All interactive elements must have a hover transition of at least 100ms — never instant.
- `prefers-reduced-motion`: disable all transitions; state changes still occur.

---

## 11. Layout & Grid

```
Max content width: 1280px
Page horizontal padding: 16px (mobile), 24px (tablet), 40px (desktop)
Column grid: 12 columns
Gutter: 24px
```

### Breakpoints

```
xs:  0px      (mobile portrait)
sm:  640px    (mobile landscape)
md:  768px    (tablet)
lg:  1024px   (small desktop)
xl:  1280px   (desktop)
2xl: 1536px   (large desktop)
```

---

## 12. Writing & Copy Style

- **Sentence case** — not Title Case, except for product/brand names
- **Direct & clear** — avoid filler words ("simply", "easily", "just")
- **Action-first** button labels: "Save changes", "Delete account", "Create new"
- **Error messages** must always be explicit and provide a solution
- **Placeholder text** should use concrete examples, not generic instructions

---

## 13. Accessibility

- Minimum contrast: **4.5:1** for body text, **3:1** for large UI elements
- Focus ring: `outline: 2px solid #1D6EEB; outline-offset: 2px`
- Color is never the sole differentiator — always combine with an icon or label
- All form inputs must have a linked label via `for`/`id`
- Tab order must be logical and consistent

---

## 14. CSS Variables — Quick Reference

```css
:root {
  /* Brand */
  --color-primary:         #1D6EEB;
  --color-primary-light:   #EFF8FF;
  --color-secondary:       #E55B05;
  --color-secondary-light: #FFF3EB;

  /* Foundation */
  --color-white:   #FFFFFF;
  --color-black:   #000000;
  --color-info:    #28A0F8;
  --color-warning: #F79009;
  --color-success: #12B76A;
  --color-error:   #F04438;

  /* Neutral */
  --color-gray-25:  #FCFCFD;
  --color-gray-50:  #F9FAFB;
  --color-gray-100: #F2F4F7;
  --color-gray-200: #EAECF0;
  --color-gray-300: #D0D5DD;
  --color-gray-400: #98A2B3;
  --color-gray-500: #667085;
  --color-gray-600: #475467;
  --color-gray-700: #344054;
  --color-gray-800: #1D2939;
  --color-gray-900: #101828;

  /* Typography */
  --font-family: "Poppins", -apple-system, sans-serif;
  --text-xs:   12px;
  --text-sm:   14px;
  --text-md:   16px;
  --text-lg:   18px;
  --text-xl:   20px;
  --text-2xl:  24px;
  --text-3xl:  30px;
  --text-4xl:  36px;
  --text-5xl:  48px;
  --text-6xl:  60px;
  --text-7xl:  72px;

  /* Spacing */
  --space-1:  4px;
  --space-2:  8px;
  --space-3:  12px;
  --space-4:  16px;
  --space-5:  20px;
  --space-6:  24px;
  --space-8:  32px;
  --space-10: 40px;
  --space-12: 48px;
  --space-16: 64px;
  --space-20: 80px;
  --space-24: 96px;

  /* Border Radius */
  --radius-sm:   4px;
  --radius-md:   6px;
  --radius-lg:   8px;
  --radius-xl:   12px;
  --radius-2xl:  16px;
  --radius-full: 9999px;

  /* Shadows */
  --shadow-sm:  0 1px 2px rgba(16,24,40,0.05);
  --shadow:     0 1px 3px rgba(16,24,40,0.10), 0 1px 2px rgba(16,24,40,0.06);
  --shadow-md:  0 4px 8px -2px rgba(16,24,40,0.10), 0 2px 4px -2px rgba(16,24,40,0.06);
  --shadow-lg:  0 12px 16px -4px rgba(16,24,40,0.08), 0 4px 6px -2px rgba(16,24,40,0.03);
  --shadow-xl:  0 20px 24px -4px rgba(16,24,40,0.08), 0 8px 8px -4px rgba(16,24,40,0.03);
  --shadow-2xl: 0 24px 48px -12px rgba(16,24,40,0.18);

  /* Motion */
  --duration-fast:   100ms;
  --duration-base:   150ms;
  --duration-slow:   200ms;
  --duration-slower: 300ms;
  --ease-out:    cubic-bezier(0.0, 0.0, 0.2, 1);
  --ease-in-out: cubic-bezier(0.4, 0.0, 0.2, 1);
}
```

---

## 15. Token Naming Convention

Morpheme uses a consistent naming pattern:

```
{category}{variant}{scale}

Examples:
  colorPrimary500    → brand primary, shade 500
  colorSecondary100  → brand secondary, shade 100
  shadow-lg          → shadow, large
  text-md            → text size, medium
  radius-xl          → border radius, extra large
```

Three token layers:
1. **Foundation** — primitive values (`#F04438`)
2. **Brand** — brand aliases (`colorPrimary500`)
3. **Semantic** — contextual aliases (`color-error`, `color-success`)

Always use **semantic tokens** in components, not foundation tokens directly, to keep theming easy.

---

*Design system extracted from Morpheme UI by gits.id — April 2026.*
