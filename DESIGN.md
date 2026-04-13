# DESIGN.md — Morpheme UI Design System
> Based on Morpheme UI by gits.id (Morpheme UI • k6a9jw2v)
> The ultimate Figma UI kit and design system

---

## 1. Design Philosophy

Morpheme UI adalah design system yang bersifat **universal dan accessible** — dirancang untuk digunakan di berbagai proyek dengan skala apapun. Prinsip utamanya:

- **Consistent** — Token dan komponen yang sama digunakan secara konsisten di seluruh antarmuka.
- **Accessible** — Warna semantic mengikuti asosiasi dunia nyata (merah = bahaya, kuning = peringatan, hijau = positif) untuk menurunkan cognitive load.
- **Scalable** — Sistem token berlapis (foundation → brand → semantic) memudahkan theming dan kustomisasi.
- **Clean & Light** — Visual default adalah light mode dengan tipografi tegas, shadow halus, dan whitespace yang lapang.

---

## 2. Color System

Morpheme menggunakan sistem warna **3 lapisan**:

```
Foundation Colors  →  Brand Colors  →  Semantic Colors
(primitif)            (produk)          (kontekstual UI)
```

---

### 2.1 Foundation Colors

Warna dasar yang tidak berubah terlepas dari tema.

| Token     | Hex       | RGB                | Usage                          |
|-----------|-----------|--------------------|--------------------------------|
| `white`   | `#FFFFFF` | rgb(255, 255, 255) | Background, surface terang     |
| `black`   | `#000000` | rgb(0, 0, 0)       | Base typography color tokens   |
| `info`    | `#28A0F8` | rgb(40, 160, 248)  | Informational states           |
| `warning` | `#F79009` | rgb(247, 144, 9)   | Caution, peringatan            |
| `success` | `#12B76A` | rgb(18, 183, 106)  | Positive feedback, selesai     |
| `error`   | `#F04438` | rgb(240, 68, 56)   | Danger, error, destruktif      |

---

### 2.2 Brand Colors

Brand color default adalah **biru** (primary) dan **oranye** (secondary). Kedua warna ini harus diganti sesuai brand produk.

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

**Primary brand color utama: `#1D6EEB` (colorPrimary500)**
Digunakan pada semua elemen interaktif: tombol, link, input focus, dll.

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

Secondary digunakan sparingly — pills, alerts, aksen, badge non-primary.

---

### 2.3 Semantic Colors

Semantic colors dipetakan dari foundation colors ke konteks UI yang spesifik. Tersedia dalam skala 25–900 untuk setiap kategori:

- **Info** (berbasis biru `#28A0F8`) — notifikasi informatif, tooltip
- **Warning** (berbasis kuning-oranye `#F79009`) — peringatan, at-risk
- **Success** (berbasis hijau `#12B76A`) — selesai, valid, positif
- **Error** (berbasis merah `#F04438`) — error, destruktif, blocked

Setiap kategori semantic memiliki skala warna 25–900:
```
{category}25   → tint paling terang, untuk background/surface
{category}100  → background ringan (alert, badge bg)
{category}300  → border, outline
{category}500  → warna utama (icon, text bold)
{category}700  → warna gelap (hover state)
{category}900  → tint paling gelap
```

---

## 3. Typography

### Font Family
```
Font utama: Poppins
Fallback:   -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif
```

Morpheme menggunakan **Poppins** — geometric sans-serif dengan karakter yang bersih dan modern. Tersedia dalam Regular (400), Medium (500), Semibold (600), dan Bold (700).

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
- Display sizes selalu gunakan tracking `-2%` (letter-spacing negatif) untuk keterbacaan di ukuran besar.
- Body text default: **Text md (16px)**, line height 24px.
- Jangan mix lebih dari 2 weight dalam satu komponen.
- Gunakan Poppins Semibold untuk semua heading h1–h3.

---

## 4. Spacing System

Berbasis **4px base unit**. Semua spacing adalah kelipatan 4.

```
4px   — spacing-1  (hairline)
8px   — spacing-2  (xs)
12px  — spacing-3  (sm)
16px  — spacing-4  (md — default padding)
20px  — spacing-5
24px  — spacing-6  (card inner padding)
32px  — spacing-8  (section gap kecil)
40px  — spacing-10
48px  — spacing-12 (section gap)
64px  — spacing-16
80px  — spacing-20
96px  — spacing-24 (large section)
```

---

## 5. Border Radius

```
0px   — radius-none  (sharp, tabel)
2px   — radius-xs    (badge kecil)
4px   — radius-sm    (input, button sm)
6px   — radius-md    (default button, card kecil)
8px   — radius-lg    (card default)
12px  — radius-xl    (card besar, modal)
16px  — radius-2xl   (feature card)
9999px— radius-full  (pill, avatar, chip)
```

---

## 6. Shadows

Morpheme menggunakan shadow sebagai indikator elevasi pada white dan colored background.

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

Gunakan shadow yang sama tapi dengan opacity sedikit lebih tinggi karena kontras berbeda pada background berwarna.

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
/* Contoh penggunaan */
backdrop-filter: blur(8px);
background: rgba(255, 255, 255, 0.6);
```

### Opacity Scale

| Token       | Value  | Use case                        |
|-------------|--------|---------------------------------|
| `opacity-sm`| ~0.20  | Overlay sangat transparan       |
| `opacity-md`| ~0.40  | Overlay sedang                  |
| `opacity-lg`| ~0.65  | Overlay tebal, modal backdrop   |
| `opacity-xl`| ~0.90  | Hampir solid, glassmorphism max |

Light variants menggunakan white base, dark variants menggunakan dark navy base.

---

## 8. Components (Guidelines)

### 8.1 Buttons

```
Primary Button:
  Background: #1D6EEB (colorPrimary500)
  Text: #FFFFFF
  Height: 44px (default), 36px (sm), 52px (lg)
  Padding: 0 18px
  Font: Poppins Medium 16px
  Border-radius: 8px
  Hover: colorPrimary600
  Disabled: opacity 0.4

Secondary Button:
  Background: transparent
  Border: 1.5px solid #1D6EEB
  Text: #1D6EEB
  Hover: colorPrimary25 background

Destructive Button:
  Background: #F04438
  Text: #FFFFFF
  Hover: darker error shade

Ghost / Link Button:
  No border, no background
  Text: #1D6EEB
  Hover: underline atau colorPrimary25 bg
```

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
- Recommended library: Heroicons, Phosphor Icons, atau Feather Icons
- Ukuran standar: 16px (inline), 20px (default), 24px (feature/header)
- Warna icon mengikuti hierarchy teks parent-nya
- Icon-only selalu sertakan `aria-label`

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

**Prinsip:**
- Gunakan hanya `opacity` dan `transform` untuk animasi (hindari animasi layout).
- Semua interaktif harus punya transisi hover minimal 100ms — jangan instant.
- `prefers-reduced-motion`: nonaktifkan semua transisi, perubahan state tetap terjadi.

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
lg:  1024px   (desktop kecil)
xl:  1280px   (desktop)
2xl: 1536px   (desktop besar)
```

---

## 12. Writing & Copy Style

- **Sentence case** — bukan Title Case, kecuali nama produk/brand
- **Langsung & jelas** — hindari kata-kata filler ("simply", "easily", "just")
- **Action-first** pada tombol: "Simpan perubahan", "Hapus akun", "Buat baru"
- **Error messages** selalu eksplisit dan memberikan solusi
- **Placeholder text** menggunakan contoh konkret, bukan instruksi generik

---

## 13. Accessibility

- Kontras minimum: **4.5:1** untuk body text, **3:1** untuk UI besar
- Focus ring: `outline: 2px solid #1D6EEB; outline-offset: 2px`
- Warna bukan satu-satunya pembeda — selalu kombinasikan dengan icon atau label
- Semua form input memiliki label yang terhubung via `for`/`id`
- Urutan tab logis dan konsisten

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

Morpheme menggunakan pola penamaan yang konsisten:

```
{category}{variant}{scale}

Contoh:
  colorPrimary500    → brand primary, shade 500
  colorSecondary100  → brand secondary, shade 100
  shadow-lg          → shadow, large
  text-md            → text size, medium
  radius-xl          → border radius, extra large
```

Tiga lapisan token:
1. **Foundation** — nilai primitif (`#F04438`)
2. **Brand** — alias brand (`colorPrimary500`)
3. **Semantic** — alias kontekstual (`color-error`, `color-success`)

Selalu gunakan **semantic token** di komponen, bukan foundation token langsung, agar theming mudah dilakukan.

---

*Design system extracted from Morpheme UI by gits.id — April 2026.*