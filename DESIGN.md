# Phorest Design System (DESIGN.md)

The visual language used by the Phorest salon software web client. Source of truth: the Phorest Design System Figma file (key `z3NnAwMyxonMiZUqyrzW8h`). Intended for consumption by Claude Design.

This document captures what is currently stable in the system. Components not listed are either pre-audit or work-in-progress and should not be generated until they land here.

---

## 1. Visual Theme & Atmosphere

Phorest is a salon, spa, and clinic SaaS used daily by front-desk staff, stylists, therapists, and owners. The interface is **dense, calm, and operational**, not flashy. People live in it for full shifts, so screens prioritise legibility, scanability, and confidence over decoration.

**Tone**
- Warm and professional. Numbers, money values, and errors must read as authoritative.
- Light theme only. There is no dark theme.

**Density**
- Comfortably packed. Lists, tables, calendars, and slideovers carry a lot of information.
- White space exists to group, not to breathe for its own sake.
- Default body text is 14-16px. Supporting metadata sits at 12px.

**Atmosphere**
- A warm amber-yellow primary (`#fbbf24`) signals key actions.
- A cool sky-blue **theme** scale signals informational accents and calendar surfaces (temporary tokens, pending product-wide direction).
- Neutral grays carry structure. Brand "Phorest teal" appears only on the corporate mark and is not a functional UI colour.
- A 1px black outline is the system's signature: it appears on buttons, tabs, toggles, inputs, and interactive nav items. See section 4 (The outlined control).

---

## 2. Color Palette & Roles

All colour values resolve to Tailwind v3 primitives. Bind via the semantic tokens listed below, not raw hex.

### Primitives (Tailwind v3, exact)

The system carries the full Tailwind v3 colour scale as primitives. Listing the families used by semantic tokens:

| Family | 50 | 100 | 200 | 300 | 400 | 500 | 600 | 700 | 800 | 900 |
|---|---|---|---|---|---|---|---|---|---|---|
| gray | `#f9fafb` | `#f3f4f6` | `#e5e7eb` | `#d1d5db` | `#9ca3af` | `#6b7280` | `#4b5563` | `#374151` | `#1f2937` | `#111827` |
| yellow | `#fffbeb` | `#fef3c7` | `#fde68a` | `#fcd34d` | `#fbbf24` | `#f59e0b` | `#d97706` | `#b45309` | `#92400e` | `#78350f` |
| green | `#ecfdf5` | `#d1fae5` | `#a7f3d0` | `#6ee7b7` | `#34d399` | `#10b981` | `#059669` | `#047857` | `#065f46` | `#064e3b` |
| red | `#fef2f2` | `#fee2e2` | `#fecaca` | `#fca5a5` | `#f87171` | `#ef4444` | `#dc2626` | `#b91c1c` | `#991b1b` | `#7f1d1d` |
| blue | `#eff6ff` | `#dbeafe` | `#bfdbfe` | `#93c5fd` | `#60a5fa` | `#3b82f6` | `#2563eb` | `#1d4ed8` | `#1e40af` | `#1e3a8a` |
| sky | `#f0f9ff` | `#e0f2fe` | `#bae6fd` | `#7dd3fc` | `#38bdf8` | `#0ea5e9` | `#0284c7` | `#0369a1` | `#075985` | `#0c4a6e` |
| teal | (brand mark only) | | | | | | | | `#115e59` | `#134e4a` |

### Semantic tokens (the binding layer)

These are the tokens components actually bind to. Names describe role, not value.

**Text**

| Token | Resolves to | Use |
|---|---|---|
| `text/primary` | `#000000` | Default body text, list item names, table cells |
| `text/secondary` | gray-500 `#6b7280` | Helper text, metadata, descriptions |
| `text/tertiary` | gray-400 `#9ca3af` | Placeholder, menu titles, de-emphasised labels |
| `text/inverted` | `#ffffff` | Text on dark surfaces |
| `text/status/error` | red-800 `#991b1b` | Error message text |
| `text/status/success` | green-800 `#065f46` | Success message text |
| `text/status/warning` | yellow-800 `#92400e` | Warning message text |
| `text/status/info` | blue-800 `#1e40af` | Info message text |

**Backgrounds**

| Token | Resolves to | Use |
|---|---|---|
| `bg/white` | `#ffffff` | Card surfaces, menu surfaces, table rows |
| `bg/neutral-light` | gray-50 `#f9fafb` | Page background, group headers |
| `bg/neutral` | gray-100 `#f3f4f6` | Hover backgrounds, panel surfaces |
| `bg/neutral-dark` | gray-200 `#e5e7eb` | Pressed/active neutral surfaces |
| `bg/neutral-darker` | gray-300 `#d1d5db` | (reserved) |
| `bg/banner` | yellow-400 `#fbbf24` | Actionbar background (multi-select feedback) |
| `bg/overlay/dark` | gray-600 at 75% opacity | Modal/slideover backdrop |
| `bg/overlay/light` | white at 90% opacity | (specialised use) |

Status bg family (success / error / warning / info, all five stops):

| Stop | success | error | warning | info |
|---|---|---|---|---|
| `-lighter` | green-50 | red-50 | yellow-50 | blue-50 |
| `-light` | green-100 | red-100 | yellow-100 | blue-100 |
| `(default)` | green-400 | red-400 | yellow-400 | blue-400 |
| `-dark` | green-600 | red-600 | yellow-600 | blue-600 |
| `-darker` | green-800 | red-800 | yellow-800 | blue-800 |

Pattern: light backgrounds (`-light`) pair with dark text (`-darker`) for inline status content (alerts, badges). The `-dark` and `-darker` stops are for filled status controls (checked boxes, radios, toggles, destructive buttons).

**Borders**

| Token | Resolves to | Use |
|---|---|---|
| `border/primary` | `#000000` | The signature black 1px outline. Buttons, inputs, tabs, toggles, sidebar items, secondary nav items |
| `border/light` | gray-400 `#9ca3af` | Standard neutral borders (tertiary buttons, tab underline, input dividers) |
| `border/lighter` | gray-100 `#f3f4f6` | Subtle borders (menu surface, card dividers, list dividers) |
| `border/darker` | gray-900 `#111827` | Strong borders (radio card hover) |
| `border/error` | red-600 `#dc2626` | Input error state |
| `border/status/{role}` | role-600 | Status borders (default) |
| `border/status/{role}-darker` | role-800 | Status borders (strong) |

**Icons**

| Token | Resolves to | Use |
|---|---|---|
| `icon/default` | `#000000` | Default icon colour |
| `icon/tertiary` | gray-400 `#9ca3af` | Muted icon (menu titles, banners) |
| `icon/inverted` | `#ffffff` | Icon on dark surfaces |
| `icon/status/{role}` | role-600 | Status icons |

Note: there is no `icon/secondary` token yet. Where a secondary-icon role is needed (Input's left icon, etc.), the component currently binds to `text/secondary`. Acceptable, but a known category mismatch.

### Component-layer tokens

Reserved for component-specific values that don't belong in the semantic layer.

| Token | Resolves to | Used by |
|---|---|---|
| `button/primary/bg-default` | yellow-400 | Primary button background |
| `button/primary/bg-hover` | yellow-500 | Primary button hover |
| `button/destructive/bg-default` | red-600 | Destructive button background |
| `button/destructive/bg-hover` | red-800 | Destructive button hover (200-step jump) |
| `theme/bg-default` | sky-300 | Numpad surface (temporary, pending review) |
| `theme/bg-accent` | sky-400 | Numpad header (temporary, pending review) |
| `table/header-bg-default` | sky-900 | Table column header |
| `table/header-bg-hover` | sky-800 | Table column header hover |
| `table/row-bg-hover` | blue-100 | Table row hover |
| `table/row-bg-totals` | blue-200 | Table totals row |
| `sidebar/item/bg-default-on-light` | white at 20% opacity | Sidebar item resting (light contrast) |
| `sidebar/item/bg-default-on-dark` | black at 5% opacity | Sidebar item resting (dark contrast) |
| `sidebar/item/bg-selected` | `#ffffff` | Sidebar item selected |
| `sidebar/item/border-hover-on-light` | `#ffffff` | Sidebar item hover (light contrast) |
| `sidebar/item/border-hover-on-dark` | `#000000` | Sidebar item hover (dark contrast) |
| `secondaryNav/item/bg-hover` | sky-50 | Secondary nav hover |
| `secondaryNav/item/bg-pressed` | sky-900 | Secondary nav pressed |
| `secondaryNav/item/text-default` | sky-900 | Secondary nav text |
| `secondaryNav/item/text-pressed` | `#ffffff` | Secondary nav pressed text |
| `secondaryNav/item/icon-default` | sky-900 | Secondary nav icon |
| `secondaryNav/item/icon-pressed` | `#ffffff` | Secondary nav pressed icon |

### Brand colour

Phorest teal `#134e4a` (teal-900) and `#115e59` (teal-800) appear on the corporate wordmark only. Do not use teal as a functional UI colour.

---

## 3. Typography

### Font family

`Inter` (single family). No display or secondary face. Mono is unused in the system today.

### Type scale

| Token | Size | Line height | Typical use |
|---|---|---|---|
| `font/size/xs` | 12px | 16px | Metadata, helper text, badge labels |
| `font/size/s` | 14px | 20px | Body in dense views (default for tables and lists) |
| `font/size/m` | 16px | 22px | Standard body |
| `font/size/l` | 18px | 24px | Section titles |
| `font/size/xl` | 20px | 30px | Page subtitles |
| `font/size/2xl` | 24px | 38px | Page titles |
| `font/size/3xl` | 30px | 46px | Dashboard stat figures |
| `font/size/4xl` | 36px | 60px | Display |
| `font/size/5xl` | 48px | 74px | Display (rare) |
| `font/size/6xl` | 60px | (custom) | Display (rare) |

### Weights

`regular` (400), `medium` (500), `semibold` (600), `bold` (700) are the working set. `light`, `extralight`, `thin`, `extrabold`, `black` exist as primitives but are not used in product UI.

Rules:
- Body: `regular`
- Labels, list item names, button labels: `medium`
- Section headings inside cards/slideovers: `semibold`
- Page titles, currency totals: `bold`
- Never combine more than two weights in a single dense view
- Numbers (currencies, durations, counts) are tabular when stacked, prefer `medium`
- Avoid uppercase for body content; allowed for short badge labels at 12px

---

## 4. The outlined control (system signature)

Phorest's interactive controls share a visual signature: a **1px black outline** (`border/primary`) on a coloured or white fill, with `radius/sm` (4px) corners and `strokeAlign: inside`. Several controls add a **2px bottom rail** on top of the 1px outline, which collapses or swaps on press for tactile feedback.

This is the most distinctive single pattern in the system. Generated UIs that miss it will not look like Phorest.

### Where the outline appears

| Component | 1px outline | 2px bottom rail | Press behaviour |
|---|---|---|---|
| Button (Primary, Secondary, Destructive) | yes | yes | Swap: 2px **top** rail, 1px bottom (pressed-down optical effect) |
| Button (Tertiary) | yes, gray-400 | no | No change |
| Tabs pill (`.pillsParts-item`) | yes | yes when selected | (no pressed state) |
| Toggle (`.toggle`, `Checked=true`) | yes | no | (no pressed state) |
| Secondary nav item (hover) | yes | yes on hover | No change |
| Input field | yes | no | No change |

### Press behaviour, in detail

For controls with the bottom rail:
- **Primary, Destructive button on press**: `strokeTopWeight: 2, strokeBottomWeight: 1` (the rail moves to the top, the bottom collapses). Optical "pressed down" effect.
- **Secondary button on press**: rail removed entirely, uniform `1px` all edges.
- **Tertiary button on press**: no change (never had a rail).

### Disabled

Disabled is universal: `opacity: 0.5` on the whole element. No separate disabled-coloured tokens. The outline and rail remain visible at half opacity.

### Stroke colour

- Filled and outlined controls: `border/primary` (black)
- Tertiary button: `border/light` (gray-400)
- Inputs in error state: `border/error` (red-600)

---

## 4b. Iconography

Phorest uses **Heroicons** (Tailwind Labs) as the primary icon library, supplemented by **Lucide** where Heroicons does not cover the case. All icons are flat single-path SVGs, designed to inherit colour from their parent.

### Library and CDN

- Heroicons v2.2.0 (current). Outline style is the default.
- CDN (jsDelivr): `https://cdn.jsdelivr.net/npm/heroicons@2.2.0/24/outline/{name}.svg`
- Browse and search: `https://heroicons.com`
- For names not in Heroicons, fall back to Lucide: `https://lucide.dev`

### Default size and stroke

- Default size: **24×24 px**. This matches the Figma icon components.
- Stroke width: as authored by Heroicons (1.5px outline, do not override).
- Colour: **inherits from parent text colour** via `stroke="currentColor"`. To recolour an icon, set the parent's text colour token.

### Sizing in context

- Inside buttons: 20×20 (slightly smaller than the 24px default, fits the 40px button height with 10px vertical padding).
- Inside list items, menu items, sidebar items: 24×24 (default).
- Inside badges: 16×16.
- Inside the Numpad and large inputs: 24×24.

### Colour binding

Icons inherit from the surrounding text colour. Concretely:

| Context | Token |
|---|---|
| Default icon on white surface | `icon/default` (black) |
| Muted icon (menu title, banner) | `icon/tertiary` (gray-400) |
| Status icons (alert, badge) | `icon/status/{role}` (role-600) |
| Icon on dark surface | `icon/inverted` (white) |
| Input left icon | currently binds to `text/secondary` (gray-500), a known category mismatch |

Do not set `fill` on icon SVGs. Heroicons outline icons use `stroke`, not `fill`.

### How to embed

Inline SVG, with the parent setting colour:

```html
<svg class="w-6 h-6" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor">
  <path stroke-linecap="round" stroke-linejoin="round" d="..." />
</svg>
```

Or img tag (less flexible for colour):

```html
<img src="https://cdn.jsdelivr.net/npm/heroicons@2.2.0/24/outline/calendar.svg" width="24" height="24" alt="" />
```

### Common icons by use

When the agent is unsure which icon to use, prefer these defaults:

| Use | Heroicon name |
|---|---|
| Calendar / appointments | `calendar` |
| Clients / users | `users`, `user` for single |
| Marketing | `megaphone` |
| Purchase / shopping | `shopping-bag` |
| Manager / dashboard | `chart-bar` |
| Settings | `cog-6-tooth` |
| Search | `magnifying-glass` |
| Close | `x-mark` |
| Confirm / check | `check` |
| More options | `ellipsis-horizontal` or `ellipsis-vertical` |
| Add | `plus` |
| Edit | `pencil` |
| Delete | `trash` |
| Next / forward | `chevron-right` |
| Back | `chevron-left` |
| Expand / collapse | `chevron-down` / `chevron-up` |
| Notification | `bell` |
| Help | `question-mark-circle` |
| Information (in Alerts) | `information-circle` |
| Warning (in Alerts) | `exclamation-triangle` |
| Error (in Alerts) | `x-circle` |
| Success (in Alerts) | `check-circle` |

### Avatar

Avatars are separate from icons but follow a similar simple rule. Phorest's avatar pattern:

- **Default colouring is neutral gray.** `bg/neutral-dark` (gray-200) surface, `text/primary` initials. There is **no deterministic colouring derived from the user's name** (no "Anna gets blue, Carlos gets red" rule).
- Callers may explicitly override the background colour when context calls for it.
- Sizes: 24×24 (xs), 32×32 (sm), 40×40 (md, the default in stacked lists), 48×48 (lg), 56×56 (xl).
- Shape: circle (`radius/full`).
- Initials fallback: first letter of first and last name, in `text/primary`, `medium` weight, font-size scaled to half the avatar height.

---

## 5. Component Stylings

Every component listed below is in the Figma file under a `✅` page and is stable for generation. Components not listed (Cards, Stepper, Combobox, IconButton, Modal primitive) are pre-audit or WIP - do not generate them.

### Button (`Button`)

Single size: **40px tall**, padding `0/12/0/12`, gap `4`, radius `4`, 32 variants.

Variant matrix: `Variant: primary | secondary | tertiary | destructive` × `State: default | hover | pressed | disabled` × `Icon only: No | Yes` (Icon only = Yes gives a 40×40 square button).

Boolean properties (`Show left icon`, `Show right icon`, `Show label`, `Left icon`, `Right icon`, `Label`) control content presence without expanding the variant matrix.

| Variant | Fill | Stroke | Text |
|---|---|---|---|
| primary | `button/primary/bg-default` (yellow-400) | `border/primary` (black) + 2px bottom rail | `text/primary` |
| secondary | `bg/white` | `border/primary` (black) + 2px bottom rail | `text/primary` |
| tertiary | transparent | `border/light` (gray-400), uniform 1px | `text/primary` |
| destructive | `button/destructive/bg-default` (red-600) | `border/primary` (black) + 2px bottom rail | `text/inverted` |

Hover: 200-step jump (`button/primary/bg-hover` = yellow-500, `button/destructive/bg-hover` = red-800). Disabled: `opacity: 0.5`. Press behaviour: see The outlined control above.

Use rule: **one Primary per view.** Secondary and Tertiary surround it. Destructive replaces Primary when the action is destructive.

### Input (`Input`)

24 variants. Axes: `Variant: field | area` × `State: default | hover | active | disabled` × `Error: true | false` × `Numpad: true | false` (Numpad applies only to `field`; `area` carries `Numpad=false` as a placeholder).

- Stroke: `border/primary` (black), 1px, no bottom rail
- Stroke in error state: `border/error` (red-600)
- Radius: 4px (`radius/sm`)
- Right icon stroke: `icon/status/default` (non-error) or `icon/status/error` (error). Asymmetric with left icon (`text/secondary`) - intentional, right icon is the primary affordance
- Resize indicator on Area variants: `border/light`
- Disabled: `opacity: 0.5`

`Numpad: true` adds a tappable affordance next to the input that summons an on-screen numpad (touch/POS surface). The `.numpad` keypad surface is its own component.

### Checkbox (page: Checkbox)

Three components: `.checkboxParts-Item` (the 20×20 box, 9 variants), `single` (box + label + help text), `list-checkbox` (group with group label/hint/description).

`.checkboxParts-Item` axes: `Checked: true | false` × `State: default | hover | disabled` × `Indeterminate: false | true`.

| State | Fill | Stroke |
|---|---|---|
| Checked, default | `bg/status/success-dark` (green-600) | (none, fill carries the colour) |
| Checked, hover | `bg/status/success-darker` (green-800) | `border/status/success-darker` |
| Unchecked, default | `bg/neutral-light` | `border/light` |
| Unchecked, hover | `bg/neutral-dark` | `border/light` |
| Disabled | per state above | per state above, at `opacity: 0.5` |

The check glyph itself is `bg/white` on the green fill. The 200-step hover jump (green-600 → green-800) is the system rule for status-bg hover states.

Radius: 4px (`radius/sm`). Size: 20×20.

### Radio (page: Radio)

Two patterns share the page:

**Inline radio** - `.radioParts-Item` (20×20 circle, 6 variants), `single`, `RadioList` (vertical or horizontal stack).

Axes: `Checked × State`. Same fill model as Checkbox: selected → `bg/status/success-dark/-darker`, selected stroke → `border/status/success-darker`, unselected fill → `bg/neutral-light` (default/disabled) or `bg/neutral-dark` (hover), unselected stroke → `border/light`. Inner indicator dot: `bg/white`. Radius: `radius/full` (circle).

**Radio card** - `.radioCardParts-Item` (bordered card with embedded radio + title + description, 4 variants), `RadioCardGroup`.

| State | Fill | Stroke |
|---|---|---|
| Default | `bg/white` | `border/light` |
| Hover | `bg/neutral-dark` | `border/darker` (gray-900) |
| Checked, default | (same as default with embedded radio checked) | `border/light` |
| Checked, hover | `bg/neutral-dark` | `border/darker` |

Card padding: 16px, gap 8px, radius 6px (`radius/md`). The two patterns are intentionally separate components - one is a form control, the other is a visual selection card.

### Toggle (page: Toggle)

`.toggle` (the switch primitive, 6 variants) and `Toggle` (switch + label composition).

Axes on `.toggle`: `Checked: true | false` × `State: default | hover | disabled`.

| Checked | Fill | Stroke |
|---|---|---|
| true | `bg/status/success-dark` (green-600) | `border/primary` (1px black) |
| false | `bg/neutral-dark` | `border/primary` (1px black) |

Hover on `Checked=true`: `bg/status/success-darker` (green-800), 200-step jump. Knob: 20×20 white circle, `bg/white`. Track: 44×24, `radius/full`. Disabled: `opacity: 0.5`.

The black 1px outline on a green fill is the outlined-control pattern in its filled-state form. Toggle and Checkbox share the same green-600 / green-800 fill semantics.

### Menu (page: Menu)

`Menu` (the surface) and `.parts/MenuItem` (the row).

**Menu surface**: vertical auto-layout, hug content, `bg/white` fill, `border/lighter` 2px stroke, `radius/lg` (8px) corners. Shadow: Tailwind `shadow-xl` (hardcoded, pending shadow token family).

**MenuItem axes**: `Type: Title | Item | Divider` × `State: Default | Hover`.

| Type | Layout | Fill | Text |
|---|---|---|---|
| Title | 8/16/8/16 padding, 12 gap | transparent | `text/tertiary` (gray-400) |
| Item | 8/16/8/16 padding, 12 gap | `bg/white` (default) / `bg/neutral` (hover) | `text/primary` |
| Divider | flat rectangle | `border/lighter` | - |

Booleans on Item: `Show checkbox`, `Show icon`, `Icon`, `Show label`, `Show alt label`, `Alt label`, `Show toggle`, `Show selected check`.

Icons in MenuItem use `text/primary` (black) by design - same emphasis as the label. Generation rule: a Menu component holds 10-15 rows by default; designers hide what they don't need rather than extending (per the "more children than needed" principle).

### Alert (`Alerts`)

8 variants. Axes: `Variant: error | info | success | warning` × `Layout: horizontal | vertical`.

| Element | Token |
|---|---|
| Fill | `bg/status/{role}-lighter` |
| Stroke | `border/status/{role}` (1px) |
| Radius | 6px (`radius/md`) |
| Padding | 12/12/12/12 |
| Gap | 8 |
| Title text | `text/status/{role}` |
| Description text | `text/status/{role}` |

Booleans: `Show title`, `Title`, `Show description`, `Description`, `Show actions`, `Show action icon`, `Action icon`, `Action label`.

### Badge (`Badge`)

10 variants. Axes: `Variant: info | error | neutral | success | warning` × `State: default | hover`.

| Element | Token |
|---|---|
| Fill | `bg/status/{role}-light` (default state) |
| Radius | `radius/full` (9999, pill shape) |
| Padding | 2/8/2/8 |
| Gap | 2 |
| Text | `text/status/{role}` |
| Font | 12px medium |

**Known regression** (flagged for follow-up): hover state currently renders at the same colour as default, because the old `-dark` 200-stop tokens were retired during the Checkbox audit. Badge hover is a tracked fix. Generated UIs should pair `Variant` with the correct status colour and not attempt to manually darken hover.

### System feedback (`Toast`, `Actionbar`)

**Toast** - 5 variants. Axes: `Variant: success | error | info | warning` × `Stacked: false | true`.

- Surface: `bg/white`, `radius/lg` (8px), `shadow-xl`
- Status-tinted left edge (status icon and accent inside the toast)
- Wrapper carries a `32/32/0/0` outer padding (intentional positioning offset for top-right placement, do not change)
- Booleans: `Show actions`, `Show icon`, `Title`, `Description`

**Actionbar** - appears at the bottom of the screen on multi-select.

- Fill: `bg/banner` (yellow-400)
- Padding: 16/12/16/12
- 2 variants: `Show actions: true | false`

### Sidebar (page: Sidebar)

Global left-rail navigation. Composed of `Sidebar` (the container, 8 variants), `.sidebarParts-Item` (each row, 6 variants), and a set of icon variants for each top-level destination (Appointments, Clients, Marketing, Purchase, Manager, Support, Lock, Clockin, Profile, Chat).

**Sidebar container axes**: `Contrast: dark | light` × `Collapsed: false | true` × `Platform: electron | web`.

`Contrast` controls which row treatment to use based on the chosen background colour (not a theme switch).

**Sidebar item axes**: `Selected: false | true` × `Contrast: dark | light | n-a` × `State: default | hover`.

- Padding: 8/12/8/12, gap 12, radius 8 (`radius/lg`)
- Hover adds the outlined-control treatment: `t1/r1/b2/l1` rail
- Selected: `sidebar/item/bg-selected` (white)
- Default fill: `sidebar/item/bg-default-on-light` (white @ 20%) or `sidebar/item/bg-default-on-dark` (black @ 5%) depending on Contrast
- Hover border: `sidebar/item/border-hover-on-light` (white) or `sidebar/item/border-hover-on-dark` (black)

### Secondary navigation (page: Secondary navigation)

A vertical nav panel used inside product surfaces (settings, admin areas), separate from the global Sidebar.

- Container: 240×variable, padding 16/20/16/20, gap 16, fill `bg/white`, border `border/light`
- Section header: `.secondaryNavParts-SectionHeader`, 8/16/8/16 padding
- Item: `.secondaryNavParts-Item`, 3 variants (`State: default | hover | pressed`)

| State | Fill | Text | Icon |
|---|---|---|---|
| default | transparent | `secondaryNav/item/text-default` (sky-900) | `secondaryNav/item/icon-default` (sky-900) |
| hover | `secondaryNav/item/bg-hover` (sky-50), `t1/r1/b2/l1` rail | as default | as default |
| pressed | `secondaryNav/item/bg-pressed` (sky-900) | `secondaryNav/item/text-pressed` (white) | `secondaryNav/item/icon-pressed` (white) |

Item dimensions: 16/4/16/4 padding for label, radius 4.

### Tabs (page: Tabs)

Two patterns: pills (`.pillsParts-item`) and underline (`.underlineParts-item`).

**Pills**: 4 variants. `isSelected: True | False` × `States: Default | Hover`. Selected = same treatment as a Primary button (`button/primary/bg-default` fill, `border/primary` stroke, `t1/r1/b2/l1` rail, 4px radius). Unselected = transparent fill, no stroke, `text/primary`. Padding 10/18/10/18.

**Underline**: 2 variants. `isSelected: True | False`. No fill, no full border. Selected adds a bottom-edge accent (per styleguide); unselected is plain text in `text/secondary`.

**Tabs container**: 2 variants. `isPills: False | True`. Underline-style container has a 1px bottom border in `border/light` and `bg/overlay/light` fill. Pills container has no border.

### Tables (page: Tables, tokens only - structural pass pending)

Composed of `columns` (column variants), `.cells` (31 cell variants), `.table footer` (Pagination / Totals), `.table topbar` (filter chrome), empty-state components, and a `Table template`.

| Surface | Token |
|---|---|
| Header background | `table/header-bg-default` (sky-900) |
| Header hover | `table/header-bg-hover` (sky-800) |
| Header text | white |
| Row background | `bg/white` (default) / `bg/neutral` (Grey rows) |
| Row hover | `table/row-bg-hover` (blue-100) |
| Totals row | `table/row-bg-totals` (blue-200) |
| Row border | `border/light` (gray-400) on bottom only |
| Cell text | `text/primary` |
| Cell muted text/icon | `text/secondary` / `text/tertiary` |
| Cell padding | 14/12/14/12 (default) |

The table palette uses sky/blue intentionally - distinct from the system-wide neutral surfaces - and is settled (not pending review like `theme/*`).

The `.cells` matrix is still mid-restructure (31 variants across `Type × Background × State`). For generation, treat the bound types as available: `Text only`, `Numbers only`, `Double Text + Avatar`, `Badge`, `Actions`, `Checkbox`, `Toggle`, `Header`, `Header-Checkbox`.

### Overlays (page: Overlays)

Five components on the page. The system has no generic Modal primitive - modal compositions live on the Templates page (off-limits for generation).

**Overlay** (the backdrop): full-bleed, `bg/overlay/dark` (gray-600 @ 75%). Used behind any modal/slideover.

**Numpad** (standalone): 368×456, `theme/bg-default` (sky-300) surface, `theme/bg-accent` (sky-400) header band, 6px radius, `shadow-xl`. Booleans: `Show input selector`, `Show banner`, `Show leading add-on`, `Show right icon`, `Show right text`.

**`.numpadParts-BigInput`**: the large value display at the top of the numpad. `bg/white` fill, `border/primary` 1px stroke, 4px radius, 0/12/0/12 padding.

**`.numpadParts-Banner`**: 4 variants (`Type: success | error | neutral | toggle`). Fill aliases to the matching `bg/status/{role}-lighter`. Used inside the numpad surface for inline messaging.

### Slideover (page: Slideover) - shell only

Slideover is a right-edge sheet, full height. The system spec covers the shell; product-specific slideover types (Appointment, Payment, Select Client, etc.) live as compositions in Figma but are not for generic generation.

**Shell parts**:
- `.parts/slideover-header`: 480×68, `bg/white`, 12 gap, `t0/r0/b1/l0` border (`border/lighter` divider on bottom)
- Body slot: scrollable content area, `bg/white`
- `.parts/slideover-footer`: 3 variants (`Type: Floating + | Single button | Multiple buttons`), 480×58, 0/16/0/16 padding, top border (`t1/r0/b0/l0`)

Compose: header + body + footer in a single vertical stack, full screen height, width `max-w-md` (or wider for specific use cases). Background is `bg/white`. Backdrop is `Overlay` (`bg/overlay/dark`).

### Lists (page: Lists)

`.listitem` (the row, 2 variants), `.listheader` (group header), `.listsupporting` (supporting content row), `Lists` (a stacked container).

**`.listitem`** axes: `State: Default | hover`. Booleans: `Avatar`, `Badge`, `Chevron`, `Main content`, `Description`, `Supporting icons`, `Checkbox`.

- Row: 512×80, padding 18/24/18/24, gap 12, `bg/white`
- Divider: `t0/r0/b1/l0` border in `border/lighter` (bottom-only)
- Hover: row fill becomes `bg/neutral`

**`.listheader`**: 376×28, fill `bg/neutral-light` (gray-50), divider in `border/lighter`. Used as sticky group headers in scrolling lists.

Stacked list pattern: avatar + main content (`text/primary`, 14px medium) over supporting text (`text/secondary`, 12px regular), with optional badge, chevron, or checkbox slots.

### Date picker (page: Date picker)

`Date picker` set with 2 variants: `Type: Day view | With Today button`. 376×268, 12/12/12/12 padding, 20 gap, 4 radius.

A standalone calendar surface for picking a date. No range/multi-select variant in the system yet.

### File upload (page: File upload)

`Upload file` set with 2 variants: `Upload type: Image | File`. Booleans: `Required`, `Title`. Used inside forms for attaching files or images.

### Chat (page: Chat)

The system contains only `Chat.typing` - a typing-input composition (740×112, padding 28/20/8/20). 2 variants: `State: Default | Disabled`. Boolean: `Attachment button`. No message-bubble component exists in the system.

### Manager screen card (page: Manager screen)

`Manager screen card` with 2 variants: `State: Default | Hover`. 216×64, 12/12/12/12 padding, 12 gap, 4 radius, `border/lighter`. A medium-sized card surface for the Manager dashboard.

---

## 6. States

Phorest's state vocabulary across interactive components:

- **default** - resting state
- **hover** - pointer over the element. On Buttons and other outlined controls, hover steps to the next colour in the family (200-step jump for status hovers like green-600 → green-800)
- **pressed** - transient feedback during mouse-down. Buttons swap the bottom rail to top. Also reused for sticky selection in button groups via `aria-pressed`
- **active** - persistent in-use state (Inputs: cursor is in the field, user is typing). Inputs use `active`, Buttons use `pressed`
- **disabled** - non-interactive. Universally `opacity: 0.5`. No separate disabled colour tokens

Components implement only the states they need. Inputs use `default / hover / active / disabled`. Buttons use `default / hover / pressed / disabled`. Selection components (Checkbox, Radio, Toggle) use `default / hover / disabled` with the selected/unselected axis carrying the rest of the variation.

---

## 7. Layout

### Spacing tokens

| Token | Pixels | Token | Pixels |
|---|---|---|---|
| `spacing/0` | 0 | `spacing/9` | 40 |
| `spacing/0-5` | 2 | `spacing/10` | 48 |
| `spacing/1` | 2 | `spacing/11` | 56 |
| `spacing/2` | 4 | `spacing/12` | 64 |
| `spacing/3` | 8 | `spacing/13` | 72 |
| `spacing/4` | 12 | `spacing/14` | 80 |
| `spacing/5` | 16 | `spacing/15` | 88 |
| `spacing/6` | 20 | `spacing/16` | 96 |
| `spacing/7` | 24 | `spacing/24` | 96 |
| `spacing/8` | 32 | `spacing/32` | 128 |

**Important**: Phorest's spacing scale does not match Tailwind's standard scale. `spacing/2` is 4px (Tailwind's `spacing-1`), `spacing/3` is 8px (Tailwind's `spacing-2`), `spacing/4` is 12px (Tailwind's `spacing-3`). Generation rule: bind to the **value** you want, not the token name. The mismatch is a known limitation pending future review.

Typical usage:
- 4px - icon-to-text gap, tight chip padding
- 8px - list item vertical rhythm
- 12-16px - default form field gap, card inner padding
- 24px - section-to-section spacing inside a card
- 32-48px - page-level section dividers

### Radius tokens

| Token | Pixels | Typical use |
|---|---|---|
| `radius/none` | 0 | (rare) |
| `radius/xs` | 2 | Inline badges, tight pills |
| `radius/sm` | 4 | Buttons, inputs, tabs, secondary nav items (the control radius) |
| `radius/md` | 6 | Cards, dropdowns, alerts, radio cards |
| `radius/lg` | 8 | Menu surface, toast, sidebar items |
| `radius/xl` | 12 | Large panels |
| `radius/2xl` | 16 | Featured cards |
| `radius/3xl` | 24 | (rare) |
| `radius/4xl` | 32 | (rare) |
| `radius/full` | 9999 | Pills, circles (badges, avatars, radio buttons, toggle track) |

### Border widths

`border/width/xs` 1px (default), `border/width/s` 2px (bottom rails, menu surface), `border/width/m` 4px, `border/width/l` 8px, `border/width/xl` 12px.

### Grid and container

Tablet-first (1024px). Multi-column forms collapse from 2-column to single column below `lg`. Tables maintain horizontal scroll rather than reshape rows.

### Phorest token → Tailwind class mapping

**Critical**: Phorest's token names look similar to Tailwind utility classes but **the names and the values do not always match**. Generate against the **resolved pixel value**, not against the matching-looking Tailwind class name.

Reference table (use this any time you would otherwise reach for a Tailwind utility based on a token name):

| Phorest token | Resolves to | Tailwind v3 class | Notes |
|---|---|---|---|
| `radius/xs` | 2px | `rounded-sm` | Tailwind `rounded-sm` happens to match |
| `radius/sm` | 4px | `rounded` | **Not `rounded-sm`** (which is 2px) |
| `radius/md` | 6px | `rounded-md` | Tailwind `rounded-md` happens to match |
| `radius/lg` | 8px | `rounded-lg` | Tailwind `rounded-lg` happens to match |
| `radius/xl` | 12px | `rounded-xl` | Tailwind `rounded-xl` happens to match |
| `radius/2xl` | 16px | `rounded-2xl` | Tailwind `rounded-2xl` happens to match |
| `radius/full` | 9999px | `rounded-full` | |
| `spacing/2` | 4px | `p-1`, `gap-1`, `m-1`, etc. | **Not Tailwind's `2`** (which is 8px) |
| `spacing/3` | 8px | `p-2`, `gap-2`, `m-2`, etc. | **Not Tailwind's `3`** (which is 12px) |
| `spacing/4` | 12px | `p-3`, `gap-3`, `m-3`, etc. | **Not Tailwind's `4`** (which is 16px) |
| `spacing/5` | 16px | `p-4`, `gap-4`, `m-4` | |
| `spacing/6` | 20px | `p-5`, `gap-5`, `m-5` | |
| `spacing/7` | 24px | `p-6`, `gap-6`, `m-6` | |
| `spacing/8` | 32px | `p-8`, `gap-8`, `m-8` | |
| `font/size/xs` | 12px | `text-xs` | |
| `font/size/s` | 14px | `text-sm` | |
| `font/size/m` | 16px | `text-base` | |
| `font/size/l` | 18px | `text-lg` | |
| `font/size/xl` | 20px | `text-xl` | |
| `font/size/2xl` | 24px | `text-2xl` | |
| `border/width/xs` | 1px | `border` | |
| `border/width/s` | 2px | `border-2` | (or `border-b-2` for the bottom rail) |

**Rule of thumb**: when the doc says `radius/sm`, write `rounded` in Tailwind, not `rounded-sm`. When the doc says `spacing/3`, write `p-2`/`gap-2` etc., not `p-3`. The Phorest scale shifted by one position relative to Tailwind's, so the names mislead.

When in doubt, use the **pixel value** as an arbitrary Tailwind utility: `rounded-[4px]`, `p-[8px]`. This is verbose but cannot be wrong.

---

## 8. Depth & Elevation

Phorest uses shadow sparingly, primarily to lift floating surfaces above content.

| Shadow | Use |
|---|---|
| (none) | Flat cards on a tinted background |
| `shadow-sm` | Dense cards in a grid |
| `shadow` | Standard card surface |
| `shadow-md` | Hovered card, primary card on dashboard |
| `shadow-lg` | Dropdown menus, popovers, comboboxes |
| `shadow-xl` | Menu, Toast, Numpad, Slideover, Modal (currently hardcoded - shadow tokens pending) |
| `shadow-inner` | Scroll containers, keypads |

Surface hierarchy (front to back):
1. Toasts
2. Modals + slideovers (with `bg/overlay/dark` backdrop)
3. Dropdowns, popovers, menus
4. Page content cards
5. Page background (`bg/neutral-light` or `bg/white`)

Never stack two `shadow-xl` surfaces directly on top of each other. Promote the lower surface to flat or use a backdrop.

---

## 9. Do's and Don'ts

### Do

- Use the **outlined control** signature on interactive surfaces (buttons, tabs, toggles, inputs, sidebar items, secondary nav items). The 1px black outline is the system's identity.
- Apply the **2px bottom rail** on Primary, Secondary, and Destructive buttons, Tabs pill selected, Secondary nav hover. Swap top/bottom on press for Primary and Destructive.
- Use **semantic tokens**: `text/primary`, `bg/status/success-dark`, `border/light`. Never raw hex in component code.
- Keep the Primary action **once per view**. Secondary and Tertiary surround it.
- Pair `bg/status/{role}-light` backgrounds with `text/status/{role}` text for inline status content.
- Use `opacity: 0.5` for all disabled states. No separate disabled colour tokens.
- For status hovers, use the **200-step jump** (e.g. green-600 → green-800). 100-step is too subtle.
- Use `radius/sm` (4px) for controls, `radius/md` (6px) for cards, `radius/lg` (8px) for floating surfaces, `radius/full` for pills and circles.
- Default to `bg/white` surfaces on a `bg/neutral-light` page background.
- Treat numbers (money, counts, durations) with `medium` weight and tabular alignment.

### Don't

- **Don't** drop the 1px black outline on outlined controls. Flat fills without the outline don't read as Phorest.
- **Don't** mix Primary (amber) and `theme/*` (sky-blue) as competing calls-to-action. Primary always wins.
- **Don't** use teal as a functional UI colour - it's reserved for the corporate wordmark.
- **Don't** introduce shadows or radii outside the token scales.
- **Don't** create per-component disabled colour tokens. Use `opacity: 0.5`.
- **Don't** use uppercase body text or letter-spacing tricks outside small badge labels.
- **Don't** generate components not listed in section 5. Cards, Stepper, Combobox, IconButton, and a generic Modal primitive are not yet stable in the system.
- **Don't** generate Slideover types (Appointment, Payment, Select Client, etc.) generically - those are product compositions. Use only the Slideover shell.
- **Don't** use animations beyond `animate-spin` (loading) and `animate-pulse` (skeletons).
- **Don't** put two filled status buttons (success + destructive) competing in the same row. One stays filled, the other goes tertiary.
- **Don't** extend the `theme/*` tokens beyond Numpad - they are temporary, pending product-wide direction.

---

## 10. Responsive

Phorest's primary form factor is **tablet (landscape, ~1024px)** on the salon floor, with desktop secondary. Pure mobile is not a primary surface.

| Breakpoint | Width | Context |
|---|---|---|
| (base) | < 640px | Phone fallback |
| `sm` | 640px | Tablet portrait |
| `md` | 768px | Tablet landscape (low end) |
| `lg` | 1024px | Tablet landscape (primary), laptop |
| `xl` | 1280px | Desktop |
| `2xl` | 1536px | Wide desktop |

Touch targets: ≥ 40px tall. Buttons default to `h-10` (40px). Numeric keypads use 56-64px keys.

Collapse rules:
- Sidebar: fixed on `lg+`, becomes overlay/drawer below
- Multi-column forms: 2-column above `lg`, single column below
- Tables: preserve horizontal scroll, never reshape rows into cards
- Slideovers: `max-w-md` on `md+`, full screen below
- Modals: shrink `max-w-*` step-wise, stay centred

---

## 11. Agent Prompt Guide

### System prompt seed

> You are generating UI for **Phorest**, a salon and spa management SaaS used on tablets (landscape, 1024px+) on the salon floor and on desktops in back office. The interface is dense, calm, and operational. Light theme only.
>
> Use **semantic tokens** from this design system, not raw hex. The signature visual mechanic is the **outlined control**: a 1px black outline on filled or white surfaces, with `radius/sm` (4px) corners, and a 2px bottom rail on Primary/Secondary/Destructive buttons (collapsing to 1px and swapping to the top edge on press).
>
> Primary amber (`bg/status/warning` / `button/primary/bg-default`, both yellow-400) is reserved for the single dominant call-to-action per view. Status colours follow the pattern: `bg/status/{role}-light` with `text/status/{role}` for inline content, `bg/status/{role}-dark` for filled selection controls. Disabled is universal: `opacity: 0.5`.
>
> Default body text is 14px (`font/size/s`). Numbers use `medium` weight.

### Example component prompts

- *"Generate a Primary button: 40px tall, padding 0/12/0/12, fill `button/primary/bg-default` (yellow-400), 1px `border/primary` outline with 2px bottom rail, 4px radius, `text/primary` label in medium weight. Hover: fill `button/primary/bg-hover` (yellow-500). Pressed: swap to 2px top, 1px bottom rail."*

- *"Build a Toast: white surface, 8px radius, `shadow-xl`, status-tinted icon and accent for `Variant: success`. Wrapper has 32/32/0/0 outer padding (positioning offset for top-right placement - keep). Show title in `text/primary` medium, description in `text/secondary` regular."*

- *"Compose a Slideover: right-edge sheet, full height, `max-w-md`, `bg/white` surface, `bg/overlay/dark` backdrop behind. Header at top with 480×68 frame, bottom divider in `border/lighter`. Body slot is scrollable. Footer at bottom with top divider, holds 1-2 buttons."*

- *"Generate a stacked list: `.listitem` rows in a column, each 80px tall with 18/24/18/24 padding, 12 gap, `bg/white` fill, bottom border in `border/lighter`. Each row: avatar (`spacing/4` gap), main content in `text/primary` 14px medium, supporting text in `text/secondary` 12px regular. Hover: fill changes to `bg/neutral`."*

- *"Build an Alert: variant `success`, layout horizontal. Fill `bg/status/success-lighter`, 1px stroke `border/status/success`, 6px radius, 12/12/12/12 padding, 8 gap. Title and description both in `text/status/success`. Icon left, optional close right."*

### Iteration guide

1. Every interactive control gets the **outlined-control treatment**. If the component doesn't have a 1px black outline, it's probably not a Phorest control.
2. Status hovers always step 200 (green-600 → green-800), never 100.
3. Filled status controls (checkbox, radio, toggle, destructive button) use the `-dark` stop of the bg/status family. Inline status content (alerts, badges) uses `-light` with `text/status/{role}`.
4. `radius/sm` (4px) is the control radius. `radius/md` (6px) is the card radius. `radius/lg` (8px) is the floating-surface radius. `radius/full` is for pills and circles.
5. Disabled is `opacity: 0.5`, applied uniformly. Don't create disabled-specific colours.
6. Tabs and Secondary nav items inherit the outlined-control treatment in their selected/hover states. Treat them as buttons-in-context.
7. Compose pages with `bg/neutral-light` page backgrounds and `bg/white` card surfaces. Use `bg/neutral` for hover states on white surfaces.
8. **Always check the token-to-Tailwind mapping table in section 7 before writing a Tailwind class.** `radius/sm` is `rounded`, not `rounded-sm`. `spacing/3` is `gap-2`, not `gap-3`.
9. **Use real Heroicons SVGs via the CDN listed in section 4b.** Do not use emoji or placeholder shapes.

### Worked example: full screen composition

This is what good looks like for a typical Phorest screen. Use as a structural reference for composing pages, not as a copy-paste template.

**Scene**: Today's appointment list, with two rows multi-selected. Three-column shell: global Sidebar (left), Secondary nav (middle), main content (right). Actionbar sticky at bottom when items are selected.

**Page structure (in order, top to bottom, left to right):**

1. **Global Sidebar** (220px wide, full height, dark sky-900 surface)
   - Logo at top (24px tall, white)
   - 8-12 nav items, each is a `.sidebarParts-Item`: 8/12/8/12 padding, `radius/lg` (8px) corners, gap 12, icon (24px) + label (14px medium)
   - Selected item: `sidebar/item/bg-selected` (white fill), sky-900 text
   - Default items: `sidebar/item/bg-default-on-light` (white at 20% opacity), white text
   - Profile/settings cluster at bottom (`mt-auto`)

2. **Secondary navigation** (240px wide, full height, white surface, `border/light` right edge)
   - Section header: `.secondaryNavParts-SectionHeader`, 8/16/8/16 padding, 12px uppercase tracking-wide font-medium text-tertiary
   - Items: `.secondaryNavParts-Item`, h-10, 0/16/0/16 padding, `radius/sm` (4px = Tailwind `rounded`)
   - Default item: transparent fill, sky-900 text/icon
   - Pressed item: sky-900 fill, white text/icon (the active route)
   - Hover: sky-50 fill + 2px bottom rail

3. **Main content** (flex-1, scrollable, `bg/neutral-light` background)
   - Page header: white surface, 32/24/32/24 padding, `border/lighter` bottom edge
     - Title: 24px bold (font/size/2xl)
     - Subtitle: gray-500, 16px regular (font/size/m)
     - Action buttons cluster on the right (Secondary "Export" + Primary "+ New appointment")
   - Tabs strip: underline pattern, `bg/overlay/light` surface, `border/light` bottom edge
   - List header: `.listheader`, gray-50 fill, 6/24/6/24 padding, 12px uppercase tracking-wide font-medium text-secondary
   - List body: stack of `.listitem` rows on white, each row 80px tall with `border/lighter` bottom divider

4. **Actionbar** (sticky bottom, appears on multi-select, 58px tall, `bg/banner` (yellow-400) fill, 16/12/16/12 padding)
   - Left: selection count in `text/primary` medium
   - Right: action buttons cluster
   - **Button choice inside Actionbar**: the yellow Actionbar surface conflicts with a yellow Primary button. Use **Secondary** (white) buttons for actions inside the Actionbar. Reserve Destructive (red) for genuinely destructive actions. The "confirm" / dominant action uses the Secondary treatment here, not Primary.

**Composition rhythm rules:**

- Page background is **`bg/neutral-light`** (gray-50). Surfaces that hold content (headers, list bodies, cards) are **`bg/white`**.
- Section dividers between major regions use `border/lighter` (gray-100), 1px, bottom-only. No box borders.
- Section internal padding: 24px horizontal. Vertical padding scales with content density (16px in dense list rows, 24px in headers, 32px between unrelated regions).
- Avatar in list rows: 40px circle, gray-200 fill, gray-900 initials. No name-derived colouring.
- Numbers (counts, times, money) right-align where stacked, `medium` weight.

**Reference HTML skeleton** (Tailwind, no inline styles where avoidable):

```html
<div class="flex h-screen">
  <!-- Sidebar -->
  <aside class="w-[220px] bg-sky-900 text-white flex flex-col p-2 gap-2">
    <div class="h-16 flex items-center px-3 font-bold">phorest</div>
    <a class="flex items-center gap-3 px-3 py-2 rounded-lg bg-white text-sky-900 font-medium">
      <svg class="w-6 h-6" ...><!-- heroicon: calendar --></svg>
      Appointments
    </a>
    <a class="flex items-center gap-3 px-3 py-2 rounded-lg text-white" style="background:rgba(255,255,255,0.20)">
      <svg class="w-6 h-6" ...><!-- heroicon: users --></svg>
      Clients
    </a>
    <!-- ... more items ... -->
  </aside>

  <!-- Secondary nav -->
  <nav class="w-[240px] bg-white border-r border-gray-400 px-5 py-4 flex flex-col gap-2">
    <div class="px-4 py-2 text-xs uppercase tracking-wide font-medium text-gray-400">Bookings</div>
    <a class="flex items-center gap-2 px-4 h-10 rounded bg-sky-900 text-white font-medium">
      <svg class="w-6 h-6" stroke="currentColor" ...><!-- heroicon --></svg>
      Today's appointments
    </a>
    <!-- ... more items ... -->
  </nav>

  <!-- Main -->
  <main class="flex-1 overflow-y-auto bg-gray-50">
    <header class="bg-white px-6 py-6 border-b border-gray-100 flex items-center justify-between">
      <div>
        <h1 class="text-2xl font-bold">Today's appointments</h1>
        <p class="text-gray-500 mt-1">Monday, May 18 - 24 bookings</p>
      </div>
      <div class="flex items-center gap-3">
        <button class="bg-white px-3 h-10 rounded font-medium" style="border:1px solid #000;border-bottom-width:2px">Export</button>
        <button class="px-3 h-10 rounded font-medium flex items-center gap-2" style="background:#fbbf24;border:1px solid #000;border-bottom-width:2px">
          <svg class="w-5 h-5" ...><!-- heroicon: plus --></svg>
          New appointment
        </button>
      </div>
    </header>

    <!-- Tabs (underline), list, etc. -->

    <!-- List body -->
    <div class="bg-white">
      <!-- Selected row -->
      <div class="flex items-center gap-3 px-6 py-[18px] border-b border-gray-100 bg-gray-100">
        <div class="w-5 h-5 rounded flex items-center justify-center" style="background:#059669">
          <svg class="w-3 h-3 text-white" ...><!-- heroicon: check --></svg>
        </div>
        <div class="w-10 h-10 rounded-full bg-gray-200 flex items-center justify-center font-medium text-gray-900">SM</div>
        <div class="flex-1">
          <div class="font-medium">Sarah Miller</div>
          <div class="text-xs text-gray-500 mt-0.5">Hair cut & colour - 90 min - with Anna</div>
        </div>
        <span class="px-2 py-0.5 rounded-full text-xs font-medium" style="background:#d1fae5;color:#065f46">Confirmed</span>
        <div class="font-medium w-16 text-right">9:00</div>
      </div>
      <!-- ... more rows ... -->
    </div>
  </main>
</div>

<!-- Actionbar -->
<div class="fixed bottom-0 left-[460px] right-0 px-3 py-4 flex items-center gap-3" style="background:#fbbf24">
  <span class="font-medium">2 appointments selected</span>
  <div class="ml-auto flex items-center gap-2">
    <!-- Tertiary - uniform 1px gray-400 -->
    <button class="bg-transparent px-3 h-10 rounded font-medium" style="border:1px solid #9ca3af">Cancel</button>
    <!-- Secondary - white surface with rail. The dominant action lives here, not in Primary,
         because Primary's yellow would clash with the Actionbar's yellow surface. -->
    <button class="bg-white px-3 h-10 rounded font-medium" style="border:1px solid #000;border-bottom-width:2px">Reschedule</button>
    <button class="bg-white px-3 h-10 rounded font-medium" style="border:1px solid #000;border-bottom-width:2px">Confirm</button>
    <!-- Destructive - red-600 fill -->
    <button class="px-3 h-10 rounded font-medium text-white" style="background:#dc2626;border:1px solid #000;border-bottom-width:2px">No-show</button>
  </div>
</div>
```

**What this example teaches the agent (and is hard to learn from component specs alone):**

- The default page background is `bg/neutral-light` (gray-50), with white surfaces stacked on top.
- The page header is its own white surface with a thin bottom divider, not a card.
- The Sidebar and Secondary nav are full-bleed (no rounded corners on the panels themselves).
- List rows stack flat against each other with bottom-only dividers, not as separate cards.
- **Inside the Actionbar, the button variant choice flips**: Secondary is the dominant action because Primary (yellow) would lose contrast on the yellow Actionbar surface.
- Numbers (times, counts) are right-aligned in a fixed-width slot.
- Avatars use neutral gray fills by default; no name-derived colours.

---

## 12. Source of truth

- **Figma file** (authoritative): `https://www.figma.com/design/z3NnAwMyxonMiZUqyrzW8h/Phorest-Design-System`
- **Variable collections**: Primitives (Tailwind v3 scale, 211 vars), Semantic (the binding layer, 57 vars), Components (component-specific tokens, 35 vars)
- **In-app styleguide**: `https://my-dev.phorest.com/styleguide` (production reference, may lag Figma)

When this document and Figma disagree, Figma wins. When Figma and the styleguide disagree, Figma wins.

Components not in section 5 are pre-audit or work-in-progress. Do not generate them. The current "do not generate yet" list: Cards, Stepper, Combobox, IconButton, Modal (generic primitive), Select / form-field dropdown, Templates, Appointments compositions.
