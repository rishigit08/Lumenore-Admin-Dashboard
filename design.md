# Lumenore Admin Portal — Design Specification

> Single source of truth for visual design of the Lumenore Admin Portal.
> Use this to build Figma components and screens without re-deriving styling each time.
> Values marked **(token)** come directly from the Figma variables in the source file
> (`Admin-Profile`, key `ef1Ogk79L7yLZJVXzZKIHB`). Values marked **(derived)** were read
> off the rendered sample screens and should be promoted to tokens when you formalize them.

---

## 1. Product & Audience Context

**Product:** Lumenore Admin Portal — the administrative control surface for the Lumenore analytics platform.

**Users (two personas):**

| Persona | Also called | Scope | Primary jobs |
|---|---|---|---|
| **Netlink Master** | Super Admin | Cross-organization (global) | Create & configure organizations, provision, fulfil special requests, oversee all users |
| **Org Admin** | Organization Administrator | Single organization | Manage that org's features, licenses, roles, users, and analytics |

**Design implication:** The portal is a *management console*, not a consumer app. It should feel calm, dense-but-legible, trustworthy, and efficient. Netlink Master sees global modules (Organization listing, All Users, global Analytics); Org Admin drops into an org context (indicated by the org chip in the page header, e.g. `A · Acme Health Systems`) and sees org-scoped modules.

---

## 2. Brand & Tone

### Visual tone
- **Clean, professional, data-forward.** Generous whitespace, soft neutral surfaces, restrained use of color.
- **Blue is the single brand/action color.** Everything interactive and "primary" is blue. Color is used sparingly and purposefully — mostly for status, actions, and gentle gradient accents on summary cards.
- **Soft, modern SaaS aesthetic:** rounded corners, subtle shadows, pastel gradient stat cards, thin dividers rather than heavy borders.

### Voice & copywriting tone
- **Clear, direct, functional.** Labels are short noun phrases (`Organizations`, `User Management`, `Features & Limits`).
- **Helper text is a single calm descriptive line** under the page title, e.g. *"Manage and invite users in the organization"*, *"Org-level feature flags, grouped by category. Scoped to this organization."*
- **Sentence case** for descriptions and helper text; **Title Case** for page titles, nav items, buttons, and column headers.
- No exclamation marks, no marketing hype. Instructional and neutral.
- Numbers formatted with separators (`1,340`), zero-padded small counts where used as KPIs (`05`, `04`, `08`).

---

## 3. Color System

Font/spacing aside, the palette is built on a **Slate/BlueGray neutral ramp** + a **Blue action ramp** + **semantic accent ramps** (green, rose/red, amber/yellow, teal, cyan, pink). All hex below are **(token)** unless noted.

### 3.1 Brand / Action — Blue
| Token | Hex | Usage |
|---|---|---|
| `blue/700` | `#1D4ED8` | Primary button pressed / darkest action |
| `blue/600` (`Blue Color variations/600`) | `#2563EB` | **Primary action** — buttons, active toggle, checked checkbox, links, active tab underline |
| `blue/500` | `#3B82F6` | Secondary blue, hover accents |
| `blue/400` | `#60A5FA` | Light accents |
| `blue/300` | `#93C5FD` | Disabled / muted action |
| `blue/200` | `#BFDBFE` | Soft fills |
| `blue/100` | `#DBEAFE` | Badge/count pill background |
| `blue/50` | `#EFF6FF` | Selected nav row background, hover surface |
| `Primary/95` | `#E5EFFF` | Very soft selected/active tint |
| `blue60` | `#EBEFFF` | Soft blue surface |
| `blue100` (indigo tint) | `#D3DDFF` | Soft blue surface variant |

### 3.2 Neutral — BlueGray / Slate ramp
| Token | Hex | Usage |
|---|---|---|
| `blueGray/800` | `#1E293B` | Primary text / headings |
| `blueGray/700` | `#334155` | Strong body text |
| `blueGray/600` (`Grey/600`) | `#475569` | Body text, secondary labels, icons |
| `blueGray/500` (`Grey/500`) | `#64748B` | Muted text, helper/paragraph text, placeholder |
| `blueGray/400` | `#94A3B8` | Disabled text, inactive icon, faint metadata |
| `blueGray/300` (`Grey/300`) | `#CBD5E1` | Borders, dividers, toggle-off track |
| `blueGray/200` | `#E2E8F0` | Row dividers, subtle borders |
| `blueGray/100` (`Grey/100`) | `#F1F5F9` | Table header fill, hover row, chip background |
| `blueGray/50` | `#F8FAFC` | App background / page canvas |
| `white` / `Neutral/White` | `#FFFFFF` | Cards, table surface, top bar, popovers |

### 3.3 Semantic / Status accents
| Meaning | Ramp | Key values |
|---|---|---|
| **Success / Active** | Green | `green/700 #15803D`, `green/600 #16A34A`, `green/100 #DCFCE7`, `green/50 #F0FDF4` |
| **Error / Inactive / Destructive** | Red + Rose | `color/icon/status/error #EF4444`, `rose/700 #BE123C` (Inactive status text), `red` for destructive text |
| **Warning / Caution** | Amber / Yellow | `yellow/600 #CA8A04`, `yellow/100 #FEF9C3`, `yellow/50 #FEFCE8`, `amber/50 #FFFBEB` |
| **Info / Teal accents** | Teal | `teal/500 #14B8A6`, `teal/400 #2DD4BF`, `teal/100 #CCFBF1`, `teal/50 #F0FDFA` |
| **Cyan accents** | Cyan | `cyan/700 #0E7490`, `cyan/600 #0891B2`, `cyan/100 #CFFAFE` |
| **Pink accent** | Pink | `pink/600 #DB2777` |

### 3.4 Semantic role mapping (use these, not raw ramps, in components)
| Role | Value |
|---|---|
| App background | `#F8FAFC` (blueGray/50) |
| Surface / card | `#FFFFFF` |
| Primary text | `#1E293B` (blueGray/800) — `color/text/alert/heading` |
| Secondary / helper text | `#64748B` (blueGray/500) — `color/text/alert/paragraph` |
| Muted / disabled text | `#94A3B8` (blueGray/400) |
| Border / divider | `#E2E8F0` (blueGray/200) → stronger `#CBD5E1` (blueGray/300) |
| Primary action | `#2563EB` (blue/600) |
| Primary action hover | `#1D4ED8` (blue/700) |
| Focus ring | `#2563EB` @ 30–40% or `#BFDBFE` outer glow |
| Status · Active | Text `#334155`/`#475569`, toggle track `#2563EB` |
| Status · Inactive | Text `#BE123C` (rose/700), toggle track `#CBD5E1` |
| Count / badge pill | Bg `#DBEAFE`/`#EFF6FF`, text `#2563EB` |

### 3.5 Gradients (summary/stat cards)
Stat cards use very soft, low-saturation corner gradients over a white base (glassy pastel wash). Observed families:
- **Pink/Rose wash** — used for one KPI (e.g. total/neutral or "Inactive" card).
- **Cyan → Teal wash** — used for an "Active" KPI.
- **Green wash** — used for a "Total / Users" KPI.
- Named gradient tokens exist for feature areas: `Gradient/AskMe`, `Gradient/AI Dashboard`, `Gradient/blueGray/500 #64748B`, `Gradient/blueGray/600 #475569`.

**Spec:** radial/linear gradient at ~8–15% opacity of the accent color, bleeding from one or two corners into white. Keep text on these cards in `#1E293B` (headline number) and `#64748B` (label) for legibility. Do **not** raise gradient saturation — these are decorative, not semantic.

---

## 4. Typography

**Typeface (token):** **Inter** (`Typeface/Font Face` = "Inter"). Single family across the entire portal. Fallback stack: `Inter, "Segoe UI", system-ui, -apple-system, sans-serif`.

All type tokens use **negative letter-spacing** (tight, modern). Line-heights are tight (1.24–1.34).

### 4.1 Type scale (all tokens)
| Style token | Size | Weight | Line-height | Letter-spacing | Usage |
|---|---|---|---|---|---|
| `Heading/Regular` / `Heading/Small` | **25px** | 400 Regular | 1.24 | −3% | Page titles (e.g. "Organizations", "User Management"), KPI numbers |
| `Body/Large` | 16px | 400 Regular | 1.28 | −2% | Prominent body, large values |
| `Body/Large Medium` | 16px | 500 Medium | 1.28 | −2% | Emphasized large body |
| `Body/Medium` | **14px** | 400 Regular | 1.30 | −2% | **Default body / table cell text** |
| `Body/Medium Medium` | 14px | 500 Medium | 1.30 | −2% | Nav items, emphasized cells, primary row name |
| `Body/Medium Semibold` | 14px | 600 Semi Bold | 1.30 | −2% | Buttons, section titles, strong labels |
| `Body/Small` | **12px** | 400 Regular | 1.30 | −2% | Secondary/meta text, sub-labels, email under name |
| `Body/Small Medium` | 12px | 500 Medium | 1.30 | −2% | Column headers, small labels, tab labels |
| `Body/Label` / `Label/Semibold` | 10px | 500 Medium | 1.34 | −2% | Micro-labels, pill/badge text, tags |

### 4.2 Applied roles
- **Page title:** 25px / 400, `#1E293B`.
- **Page helper line:** 12–14px / 400, `#64748B`, directly under title.
- **KPI number:** 25px / 400 (or heavier if desired), `#1E293B`; **KPI label:** 12–14px, `#475569`.
- **Table column header:** 12px / 500, `#64748B`, on `#F1F5F9` header fill.
- **Table cell (primary):** 14px / 500, `#1E293B`. **Table cell (secondary/email/meta):** 12px / 400, `#64748B`.
- **Nav item:** 14px / 500, `#334155`; selected → `#2563EB`.
- **Button label:** 14px / 600.
- **Status text:** 14px, Active `#475569`, Inactive `#BE123C`.

---

## 5. Spacing, Radius, Elevation

### 5.1 Spacing scale
Base unit **4px**. Core token: `space-16` = **16px (token)**. Recommended scale (4-based):
`4 · 8 · 12 · 16 · 20 · 24 · 32 · 40 · 48`

- **Page horizontal padding:** **120px (token, `Padding/Page_Body`)** on each side of the content column at 1440 width (content column ≈ 1140–1200px). Reduce responsively (see §6).
- Card internal padding: **20–24px**.
- Table cell vertical padding: **12–14px** (row height 46–49px).
- Gap between stat cards: **16–24px**.
- Gap between form/list rows: **12–16px**.
- Section vertical rhythm: **24–32px** between major blocks.

### 5.2 Corner radius (derived)
| Element | Radius |
|---|---|
| Cards / stat cards / table container | 12px |
| Buttons, inputs, search field | 8px |
| Small chips / count pills | full (pill) or 6px |
| Checkbox | 4–6px |
| Toggle | full |
| Avatar | full (circle) |
| Modal / drawer | 12–16px |

### 5.3 Elevation / shadows (derived)
Shadows are **soft and low** — the UI relies more on borders and fills than heavy shadow.
- **Card / stat card:** `0 1px 2px rgba(16,24,40,0.05)` + optional `0 1px 3px rgba(16,24,40,0.04)`.
- **Popover / dropdown / menu:** `0 4px 16px rgba(16,24,40,0.12)`.
- **Modal:** `0 12px 32px rgba(16,24,40,0.18)`.
- **Top bar:** hairline bottom border `#E2E8F0` (no heavy shadow).

### 5.4 Borders
- Default border/divider: **1px** `#E2E8F0`; stronger/interactive: `#CBD5E1`.
- Table row separators: 1px `#E2E8F0` (or `#F1F5F9` for very subtle).
- Focus: 2px ring in `#2563EB` (or 3px `#BFDBFE` glow).

---

## 6. Layout & Grid

### 6.1 Global frame
- **Design width:** 1440px (desktop reference).
- **Structure (left → right):**
  1. **Icon rail (primary nav)** — fixed **60px (token)** wide, full height, light surface (`#FFFFFF`/`#F8FAFC`). Vertical stack of icon+label items (Create, Homepage, Ask Me, Dashboard, Do You Know, Data, Data Magnet, Manage). "Create" sits at top as a highlighted blue circular button. A rocket/upgrade glyph pins to the bottom.
  2. **Contextual sub-nav (Admin panel)** — ~**200–220px** wide secondary column with the section title ("Admin") and the module list for the current area (Organizations, All User, Dataset, Schema, Storyboard — or, in org context: Features & Limits, License Management, Role Management, User Management, Usage Limits, Dashboards, Dataset, Schema, Storyboard). Collapsible (collapse icon top-right of this panel).
  3. **Main content area** — fills remaining width, `#F8FAFC` canvas, with **120px** side padding to the content column.
- **Top bar** — full width, **40px (token, offset y=40)** tall, white, hairline bottom border. Contains: Lumenore wordmark (left, above icon rail), centered global **Search** field (pill, ~500px, `#F1F5F9` fill), and right-aligned utility icons (notifications/bell, help, settings/gear, user avatar).

### 6.2 Content page anatomy (repeatable pattern)
Every module page follows this vertical stack:

1. **Page header band** — subtle blue gradient background (`#EFF6FF`→white). Contains:
   - (Org context only) Back arrow `←` + org avatar chip + org name (e.g. `A · Acme Health Systems`).
   - **Page title** (25px) + **helper line** (12–14px, muted).
   - **Primary actions** right-aligned (e.g. `Add New Organization`, `Add New User`, `Review & Save`, `Save Changes`). Secondary/outline action to the left of primary when present (e.g. `Bulk Upload`).
2. **Summary / KPI row** (where applicable) — 2–3 gradient stat cards, equal width, in a row.
3. **Toolbar row** — left: segmented tabs (`All`, `Recent`) or view tabs (`Module Visibility`, `Assigned User`); right: **Search** field + **Sort by** dropdown (`Last Modified`).
4. **Data region** — table, list, or grouped cards.
5. **Pagination** (tables) — centered page numbers `‹ 1 2 … 20 ›` with **Rows per page** selector right-aligned.

### 6.3 Responsive intent
- Content column is fluid; the 120px page padding is a max — collapse toward 32–48px on narrower viewports.
- Sub-nav panel collapses to icons/hidden on small widths; icon rail stays.
- Stat card rows wrap 3→2→1. Tables gain horizontal scroll rather than dropping columns.

---

## 7. Component Specifications

### 7.1 Buttons
| Variant | Fill | Text | Border | Radius | Padding | Notes |
|---|---|---|---|---|---|---|
| **Primary** | `#2563EB` | `#FFFFFF` 14/600 | none | 8px | 10×16px | Add New…, Save Changes. Hover `#1D4ED8`. Disabled `#93C5FD`. |
| **Secondary / Outline** | `#FFFFFF` | `#2563EB` 14/600 | 1px `#2563EB` | 8px | 10×16px | Bulk Upload. Hover fill `#EFF6FF`. |
| **Ghost / Tertiary** | transparent | `#475569` 14/500 | none | 8px | 8×12px | Low-emphasis, icon-adjacent. |
| **Icon button** | transparent | icon `#64748B` | none | 8px | 8px square | Kebab `⋮` row action, header utility icons. Hover bg `#F1F5F9`. |
| **Disabled primary** | `#93C5FD`/`#BFDBFE` | white | none | 8px | — | e.g. `Review & Save` inactive until changes exist. |

Button height: **36–40px**. Icon+label spacing: 8px.

### 7.2 Icon rail item (primary nav)
- Vertical icon (20–24px) with a 10px caption label beneath, `#475569`, centered in the 60px rail.
- **Selected:** icon + label in `#2563EB`, optional `#EFF6FF` pill behind.
- **"Create"** item: filled blue circular FAB-style button at top.

### 7.3 Sub-nav item (Admin panel)
- Row height ~40px, full-width, 12px horizontal padding, icon (16px) + label (14/500).
- **Default:** text `#334155`, icon `#64748B`.
- **Selected:** background `#EFF6FF` (blue/50), left text/icon `#2563EB`, medium weight, optional 2–3px left accent bar or full rounded highlight.
- Section title ("Admin") 12/600 uppercase-ish muted `#64748B` with a collapse toggle on the right.

### 7.4 Search field
- Pill/rounded-8 input, `#F1F5F9` fill (global) or white with `#E2E8F0` border (in-page), 36–40px tall.
- Leading magnifier icon `#94A3B8`, placeholder `#94A3B8` 14/400.
- Global top-bar search is wide (~500px) and centered; in-page search is ~260–320px, right-aligned in the toolbar.

### 7.5 Tabs (segmented)
- Underline style. Items 12–14/500. Icon + label (e.g. `▦ All`, `↺ Recent`, `▤ Module Visibility`, `👤 Assigned User`).
- **Active:** text `#1E293B`/`#2563EB` with a 2px `#2563EB` underline. **Inactive:** `#64748B`, no underline.
- Vertical divider `|` between tab groups where shown.

### 7.6 Sort control
- Label "Sort by" `#64748B` 12–14, followed by current value (`Last Modified`) `#1E293B` 14/500 + chevron `⌄`. Opens a dropdown menu.

### 7.7 Stat / KPI card
- White card, radius 12px, soft shadow, corner pastel gradient (see §3.5), padding 20–24px.
- Top row: small icon in a rounded tinted square + label (12–14, `#475569`).
- Big number: 25px, `#1E293B`. Optional trailing status icon (check for Active, warning for Inactive).
- Fixed equal widths in a 2–3 card row, 16–24px gap.

### 7.8 Data table
- Container: white, radius 12px, soft shadow, 1px `#E2E8F0` outline optional.
- **Header row:** fill `#F1F5F9`, height **46px**, labels 12/500 `#64748B`, left-aligned (Action column right-aligned). Optional leading checkbox for multi-select.
- **Body row:** height **~49px**, white; **hover** `#F8FAFC`/`#F1F5F9`. Divider 1px `#E2E8F0`.
- **Cell types:**
  - *Entity cell:* small avatar/logo (24–28px, rounded) + primary name (14/500 `#1E293B`); optional secondary line = email (12/400 `#64748B`).
  - *Text cell:* 14/400 `#475569`.
  - *Date cell:* 14/400 `#64748B`.
  - *Status cell:* toggle + label (Active `#475569` / Inactive `#BE123C`).
  - *Action cell:* kebab `⋮` icon button, right-aligned.
- **Inactive row treatment:** entity avatar/name dimmed to `#94A3B8` (see Raj Patel / inactive users) to signal disabled state.
- **Pagination footer:** centered `‹ 1 2 … 20 ›` (current page = blue `#2563EB` boxed/filled), right side "Rows per page ⌄" (default 20).

### 7.9 Toggle (switch)
- Track ~36×20px, full radius, knob white circle.
- **On:** track `#2563EB`, knob right. **Off:** track `#CBD5E1`, knob left. Disabled: track `#E2E8F0`.

### 7.10 Checkbox
- 18–20px, radius 4–6px.
- **Checked:** fill `#2563EB`, white check. **Unchecked:** white fill, 1px `#CBD5E1` border. Indeterminate: blue with dash (header select-all).

### 7.11 Count / badge pill
- Small pill, bg `#DBEAFE`/`#EFF6FF`, text `#2563EB` 12/500 (e.g. feature counts `19`, `22`, `13`). Radius full. Padding 2×8px.
- Role/label chip (e.g. `Admin Role`): bg `#F1F5F9`, text `#475569` 12/500, 1px `#E2E8F0` border, pill.

### 7.12 Feature / grouped list card (Features & Limits pattern)
- Full-width white card, radius 12px, 1px `#E2E8F0`, padding 16–20px, ~16px vertical gap between cards.
- Layout: leading **checkbox** → tinted icon square (blue/50 bg, blue icon) → title (14/600 `#1E293B`) + description (12/400 `#64748B`) → right side: count pill + chevron `›` (expand).
- Selected/enabled group: checkbox checked (blue). Disabled group: unchecked, chevron still present.

### 7.13 Permission list row (Role Management · Module Visibility)
- Two-column: **Module** name (14/400 `#1E293B`) left, **Permission** checkbox right-aligned.
- Header row: "Module" / "Permission" 12/500 `#64748B` on `#F1F5F9`.
- Search field above the list; `Save Changes` primary button top-right of the panel.

### 7.14 Avatar
- Circle. Image when available; otherwise **initials monogram** on a soft tinted background (e.g. `AN`, `MJ`, `PS`), text `#475569` 12/500. Sizes: 24px (table), 28–32px (header chip), 32px (top bar user).

### 7.15 Breadcrumb / context chip
- Org context header: back arrow `←` (`#475569`), then a small square org avatar (rounded, tinted, initial) + org name (14/500 `#1E293B`).
- Sub-context (Role page): `Role Name \ Admin` where "Role Name" is `#2563EB` link, `Admin` is `#1E293B` bold, followed by a `Admin Role` chip.

### 7.16 Dropdown / menu / popover
- White surface (`Conditional / pop-over` = `#FFFFFF`), radius 8–12px, shadow `0 4px 16px rgba(16,24,40,0.12)`, 1px `#E2E8F0`.
- Item height 36px, 12px padding, 14/400 `#334155`; hover bg `#F1F5F9`; destructive item text `#EF4444`.

---

## 8. States & Interaction

| State | Treatment |
|---|---|
| **Hover (row)** | bg `#F8FAFC` / `#F1F5F9` |
| **Hover (primary btn)** | `#1D4ED8` |
| **Hover (outline btn)** | fill `#EFF6FF` |
| **Selected (nav/tab)** | blue text `#2563EB` + `#EFF6FF` bg / underline |
| **Focus** | 2px `#2563EB` ring / 3px `#BFDBFE` glow |
| **Disabled** | text `#94A3B8`, control `#93C5FD`/`#E2E8F0`, no shadow, cursor not-allowed |
| **Active status** | toggle on `#2563EB`, text `#475569` |
| **Inactive status** | toggle off `#CBD5E1`, text `#BE123C`, row dimmed |
| **Empty state** | Centered icon + title (16/600 `#1E293B`) + helper (14/400 `#64748B`) + primary CTA |
| **Loading** | Skeleton rows in `#F1F5F9` shimmer; keep header visible |
| **Alert/inline** | Heading `color/text/alert/heading #1E293B`, paragraph `color/text/alert/paragraph #64748B`, error icon `#EF4444` |

---

## 9. Iconography
- **Style:** thin/outline line icons, 1.5px stroke, 20–24px on rails, 16px inline, rounded joins. Consistent single set (currently Lucide/Feather-like).
- **Color:** default `#64748B`; active/selected `#2563EB`; on tinted squares use the accent hue.
- **Tinted icon square:** 32–36px rounded square, bg `#EFF6FF` (blue/50) or a semantic tint, icon in the matching 600 hue — used in feature cards and stat cards.

---

## 10. Module-by-Module Notes

### Global (Netlink Master)
- **Organization Listing** — Page header + 3 KPI cards (Organizations `05`, Active `04`, Total User `1,340`) + `All`/`Recent` tabs + search + Sort by + table (Organization Name w/ logo, Parent Organization `Netlink-Master`, Created On, Status toggle, Action). Primary: `Add New Organization`.
- **All Users Listing** — Same table pattern, global scope (users across orgs). KPI row (Total / Active / Inactive). Bulk Upload + Add New User.
- **Analytics Dashboard (to create)** — See §11.

### Org-scoped (Org Admin, and Netlink drilled into an org)
Org context is signaled by the `← A · Acme Health Systems` header chip. Sub-nav: Features & Limits, License Management, Role Management, User Management, Usage Limits (+ common Dashboards, Dataset, Schema, Storyboard).
- **Features & Limits** — Helper: "Org-level feature flags, grouped by category. Scoped to this organization." Grouped feature cards (checkbox + icon + title + description + count pill + chevron). Primary: `Review & Save` (disabled until change).
- **License Management** — (reuse table + KPI + assignment patterns; not yet in samples — follow the standard page anatomy §6.2).
- **Role Management** — Role header (`Role Name \ Admin` + `Admin Role` chip + description). Tabs: `Module Visibility` (module ↔ permission checkbox list) and `Assigned User`. Primary: `Save Changes`.
- **User Management** — KPI row (Total 400 / Active 392 / Inactive 08) + tabs + search + Sort + table (Name+email w/ avatar, License Applied, Role Name, Modified On, Account Status toggle, Action) + pagination. Actions: `Bulk Upload` (outline) + `Add New User` (primary).
- **Analytics (to create)** — See §11.

### Common modules
- **Dashboard, Datasets, Schemas** — sharing, listing, owner-changing. Reuse the table pattern (§7.8), entity cells with owner avatars, share/owner dialogs using the popover spec (§7.16). Keep column sets consistent (Name, Owner, Shared With, Modified On, Action).

---

## 11. Analytics Dashboard (to be designed) — guidance
Follow the established system; do not invent a new visual language.
- **Layout:** standard page header (title "Analytics" + helper), optional date-range / org filter in the toolbar row, then a **KPI card row** (reuse §7.7 gradient stat cards) followed by a **chart grid** (2-up or 3-up cards).
- **Chart cards:** white, radius 12px, soft shadow, 20–24px padding; card title 14/600 `#1E293B`, optional helper 12/400 `#64748B`, action `⋮` top-right.
- **Chart color sequence (categorical):** lead with blue, then teal, cyan, green, amber, pink, rose — use the 500/600 steps of each ramp for series, 100/50 for fills/areas. Keep gridlines `#E2E8F0`, axis labels `#64748B` 12/400.
- **Sequential/heat scales:** single-hue blue ramp `#EFF6FF → #2563EB → #1D4ED8`.
- **Tables inside analytics:** reuse §7.8. **Empty/loading:** §8.
- Scope switch: Netlink Master = cross-org analytics (org as a dimension/filter); Org Admin = single-org, org filter hidden.

---

## 12. Quick-reference token summary

**Font:** Inter, all weights (400/500/600), negative tracking, tight line-height.
**Sizes:** 10 · 12 · 14 · 16 · 25.
**Radii:** 4/6 (controls) · 8 (buttons/inputs) · 12 (cards) · full (pills/avatars/toggles).
**Spacing:** 4-base → 4/8/12/16/24/32; page pad 120 (max).
**Core neutrals:** bg `#F8FAFC` · surface `#FFF` · text `#1E293B` · muted `#64748B` · border `#E2E8F0`.
**Action:** `#2563EB` (hover `#1D4ED8`).
**Status:** Active green `#16A34A` / Inactive rose `#BE123C` / warn `#CA8A04` / error `#EF4444`.

---
*Source: Figma file `Admin-Profile` (`ef1Ogk79L7yLZJVXzZKIHB`) — variables + sample screens: Organization Listing (`2617-198317`), Features & Limits (`2164-28855`), Role Management · Module Visibility (`2212-33982`), User Management (`2238-37891`). Regenerate/update tokens as the Figma library evolves.*
