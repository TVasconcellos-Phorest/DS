# Phorest Design System (DESIGN.md)

A description of the visual language used by the Phorest salon software web client. Distilled from the in-app living styleguide and the Tailwind theme used in production. Intended for consumption by Claude Design.

---

## 1. Visual Theme & Atmosphere

Phorest is a salon, spa, and clinic SaaS used daily by front-desk staff, stylists, therapists, and owners. The interface is **dense, calm, and operational** — not flashy. People live in it for full shifts, so screens prioritize legibility, scanability, and confidence over decoration.

**Tone**
- Warm and friendly, but never playful at the expense of clarity.
- Professional. Errors and money values must read as authoritative.
- Light theme is the default and dominant surface; dark theme is not a primary concern.

**Density**
- Comfortably packed. Lists, tables, calendars, and slideovers carry a lot of information. White space exists to group, not to breathe for its own sake.
- Default text size is `text-sm` / `text-base`; supporting metadata sits at `text-xs` or the custom `text-tiny` (0.6rem).

**Atmosphere**
- A warm amber-yellow primary signals key actions and selection.
- A cool sky-blue **theme** scale signals informational accents, calendar surfaces, and navigational chrome.
- Neutral grays carry structure. Brand "Phorest teal" (`teal-900`) only appears on the corporate mark, not as functional UI color.

---

## 2. Color Palette & Roles

All colors are exposed as Tailwind utility classes (`bg-*`, `text-*`, `border-*`, `ring-*`). Use the **semantic name**, never the hex.

### Brand
| Token | Hex | Role |
|---|---|---|
| `phorest` | `#134E4A` (teal-900) | Wordmark, marketing surfaces |
| `phorest-light` | `#115E59` (teal-800) | Hover/secondary brand surface |

### Primary — amber/yellow (calls-to-action, selection, focus)
| Token | Hex |
|---|---|
| `primary-lightest` | `#FFFBEB` |
| `primary-lighter` | `#FEEDA9` |
| `primary-light` | `#FCD34D` |
| `primary` (DEFAULT) | `#FBBF24` |
| `primary-dark` | `#F59E0B` |
| `primary-darker` | `#D97706` |
| `primary-darkest` | `#92400E` |

### Secondary — gray (default neutrals, dividers, muted UI)
| Token | Hex |
|---|---|
| `secondary-lightest` | `#9CA3AF` (gray-400) |
| `secondary-lighter` | `#6B7280` (gray-500) |
| `secondary-light` | `#4B5563` (gray-600) |
| `secondary` (DEFAULT) | `#111827` (gray-900) |

### Status — success / danger / warning / info
| Role | Lighter | Light | DEFAULT | Dark | Darker |
|---|---|---|---|---|---|
| success | `#ECFDF5` | `#A7F3D0` | `#34D399` | `#059669` | `#065F46` |
| danger | `#FEF2F2` | `#FECACA` | `#F87171` | `#DC2626` | `#991B1B` |
| warning | `#FFFBEB` | `#FEEDA9` | `#FBBF24` | `#D97706` | `#92400E` |
| info | `#EFF6FF` | `#BFDBFE` | `#60A5FA` | `#2563EB` | `#1E40AF` |

Notes:
- `warning` and `primary` share their amber palette. Treat `primary` as "this is the action" and `warning` as "be careful with this action."
- Success greens and danger reds are deliberately muted at `DEFAULT` — saturated jewel tones are reserved for `dark` variants used on filled chips/buttons.

### Text colors (use as `text-*`)
| Token | Resolved |
|---|---|
| `text-primary` | black (default body text) |
| `text-primary-light` | gray-500 (secondary text) |
| `text-primary-lighter` | gray-400 (placeholder, meta) |
| `text-primary-lightest` | gray-300 (disabled) |
| `text-theme-light` | yellow-400 |
| `text-theme-neutral` | sky-400 |
| `text-theme-dark` | sky-900 |

### Theme (sky) — informational chrome, calendar surfaces
| Token | Resolved |
|---|---|
| `bg-theme-lighter` / `border-theme-lighter` | sky-50 |
| `bg-theme-light` / `border-theme-light` | blue-200 |
| `bg-theme` (DEFAULT) | sky-300 |
| `bg-theme-dark` | sky-400 |
| `bg-theme-darker` | sky-900 |

### Surface grays
| Token | Resolved |
|---|---|
| `bg-gray-lightest` | gray-50 |
| `bg-gray-lighter` | gray-100 (panel surfaces) |
| `bg-gray-light` | gray-200 |
| `bg-gray` (DEFAULT) | `#E0E0E0` (divider) |
| `bg-gray-dark` | gray-400 |
| `bg-gray-darker` | gray-600 |

---

## 3. Typography Rules

### Font families
- **Primary:** `InterVariable` (variable-axis Inter). Fallback: system-ui sans stack.
- **Secondary / display:** `Gilroy`. Used sparingly for marketing-adjacent headings.
- **Mono:** system mono stack (code, IDs, ticket numbers).

### Type scale (Tailwind names; rem)
| Token | Size | Line height | Typical use |
|---|---|---|---|
| `text-tiny` | 0.6rem | — | dense metadata, calendar pills |
| `text-xs` | 0.75rem | 1rem | timestamps, helper text |
| `text-sm` | 0.875rem | 1.25rem | body in dense views |
| `text-base` | 1rem | 1.5rem | default body |
| `text-lg` | 1.125rem | 1.75rem | section titles |
| `text-xl` | 1.25rem | 1.75rem | page subtitles |
| `text-2xl` | 1.5rem | 2rem | page titles |
| `text-3xl` | 1.875rem | 2.25rem | dashboard stat figures |
| `text-4xl`+ | 2.25rem+ | — | marketing / empty-state only |

### Weights
- `font-normal` (400) — body.
- `font-medium` (500) — emphasis, list item names, button labels.
- `font-semibold` (600) — section headings inside cards/slideovers.
- `font-bold` (700) — page titles, currency totals.

### Rules
- Numbers (currencies, durations, counts) should be tabular when stacked. Prefer `font-medium` and lining figures.
- Avoid uppercase for body content. Allowed for short badge labels at `text-xs`.
- Never combine more than two weights in a single dense view.

---

## 4. Component Stylings

Phorest's component vocabulary, mirrored from the in-app styleguide. Components are exposed through a `Ui::` namespace internally; what matters here is the *visual contract*.

### Buttons
- **Stroke system** — **Primary** and **Secondary** carry a **1px `#111827` (ink) stroke on all four sides PLUS a thicker 2px stroke on the bottom edge**. On press, the bottom edge collapses to 1px and the button nudges 1px down. **Danger** and **Disabled** are completely flat — no stroke, no rail.
- **Primary** — solid amber (`bg-primary` text-black), used once per view as the dominant action. Stroke system as above. Hover darkens to `bg-primary-dark`. Radius `rounded` (4px, the control radius — not `rounded-md`).
- **Secondary** — white background, 1px ink stroke + 2px bottom rail, `text-primary`. Same height/padding as primary. Hover darkens to a visibly grey `bg-gray-light` (`#E5E7EB`) — not a near-white tint.
- **Tertiary** — text-only, `text-primary-darker` or `text-info-dark` for links inside content.
- **Danger** — solid red (`bg-danger-dark`, white text) for destructive confirmations. Flat — no stroke.
- **Disabled** — `bg-gray-light text-primary-lightest`, no hover, no stroke, `cursor-not-allowed`.
- **Loading** — preserve width, swap label for inline spinner (Tailwind `animate-spin`).
- **Focus** — 3px amber halo outside the stroke (`box-shadow: 0 0 0 3px rgba(251, 191, 36, 0.45)`). Always visible on keyboard.
- **Sizes** — Phorest ships a **single button size**: `h-10` (40px tall, 18px horizontal padding, `text-sm`/`text-base`). There is no `sm` or `md` variant in the product.
- **Button groups** — segmented controls share the same 1px ink stroke + 2px bottom rail as buttons. Selected segment uses `bg-primary` with `text-black`.

### Inputs & forms
- Inputs use `@tailwindcss/forms` reset, then a **1px solid `#111827` (ink) stroke**, `rounded` (4px control radius — not `rounded-md`), `text-sm`. Focus adds a **3px amber halo** outside the stroke (`rgba(251, 191, 36, 0.45)`); the stroke itself stays ink, no border-color shift.
- **InputGroup** is the canonical wrapper: label above, input, helper text below, error in `text-danger-dark`.
- **Checkbox / Radio** — square (checkbox) and circle (radio), 1px ink stroke. Checked state flips to **brand green `#059669`** (not amber), matching the Switch.
- **Switch** — pill toggle with a 1px ink stroke. `bg-gray-light` off, **`bg-success-dark` (`#059669` brand green) on — not amber**. The on-color is shared with Checkbox/Radio.
- **Fieldsets** group related toggles with a light heading and stacked items.
- **Combobox / Select Menu** — dropdown surfaces use `bg-white shadow-lg ring-1 ring-black/5 rounded-md`. Selected item: `bg-primary-lightest text-primary-darkest`.
- **Keypad inputs** (currency, time) — large, finger-friendly numeric pads for tablet/POS use.

### Lists
- **Basic list** — single column, `divide-y divide-gray-light`, item padding `py-3 px-4`.
- **Stacked list** — two-line items: name (`text-sm font-medium`) over meta (`text-xs text-primary-light`), often with a leading `Ui::Avatar`.
- **Stacked list with sticky headings** — group header `bg-gray-lightest text-xs uppercase tracking-wide font-medium text-primary-light`, sticky at top of scroll container.

### Cards & panels
- White background, `rounded-lg`, `shadow` or `shadow-md`, padding `p-4` to `p-6`.
- Panel headers: bold title + optional `Ui::Button @variant="tertiary"` action on the right.
- Empty-state cards center their content vertically with a muted icon and a short instruction.

### Avatars & badges
- **Avatar** — circular, sizes `xs` (h-6), `sm` (h-8), `md` (h-10), `lg` (h-12), `xl` (h-14). Initials fallback is **neutral gray by default** — `bg-gray-dark` with white text, or a lighter gray-100 / gray-600 pairing on darker surfaces. **No deterministic coloring from the name.** Callers can override the background colour explicitly.
- **Badge** — pill, `text-xs font-medium`, status-colored: e.g. `bg-success-lighter text-success-darker`. Always pair lighter background with darker text.
- **Tag** — like badge but with a close button; user-removable.

### Navigation
- **Tabs** — horizontal, underline style, active tab `border-b-2 border-primary text-primary-darker`.
- **Vertical navigation** — sidebar list, active item `bg-primary-lightest text-primary-darker font-medium`.
- **Stepper** — numbered circles, completed steps filled `bg-primary`, current step ringed, future steps `bg-gray-light`.

### Overlays
- **Dialog / Modal** — centered, max-width `max-w-md` (confirm) to `max-w-3xl` (form). Backdrop `bg-black/50`. Close button top-right.
- **Slideover** — right-edge sheet, full height, `w-screen max-w-md` or wider. Used heavily for appointment editing.
- **Notification (toast)** — top-right stack, white background, status-tinted left border, auto-dismiss.
- **Action bar** — bottom-fixed bar that appears on multi-select to expose batch actions.

### Domain components (Phorest-specific)
These are unique to the salon domain and should be referenced explicitly when generating screens in that context:

- **Appointment Calendar / Event Content** — colored slot cards in a day-grid calendar. Each slot has a **2px solid `#111827` stroke around all four sides** (no leading-edge stripe). The fill carries the status colour; text is **black on light fills and white on dark fills**, chosen by contrast. Service name on top, time below — never side-by-side on the same row.
- **Appointment Slideover / Insights** — a right slideover that surfaces "flag" insight cards (e.g. no-show risk, rebook reminder). 11 individual flag types.
- **Calendar navigation / view selector** — top bar combining date picker, day/week toggle, and staff filter.
- **Client profile** — header card with avatar, contact, and recent visit stats.
- **Side Bar / Branch Selector** — switches the active salon location.
- **Side Bar / Profile Actions** — bottom-of-sidebar staff menu (logout, settings).
- **Modals / Discard Changes** — danger-styled confirm before navigating away from a dirty form.
- **Modals / Appointment Issues Report** — surfaces validation issues blocking an appointment save.

### Feedback
- **Alerts** — inline banners, status-tinted background + status-darker text, optional icon and close.
- **No connection** — full-width offline banner, sticky at top.
- **Animation** — restrained: `animate-spin` for loading, `animate-pulse` for skeletons. No bounce/ping in product UI.

### Data display
- **Stats** — large `text-3xl font-bold` figure over `text-xs uppercase` label.
- **Charts** — embedded via Vega; muted palette aligning to status colors.
- **Tables** — `text-sm`, `divide-y divide-gray-light`, header row `bg-gray-lightest text-xs uppercase tracking-wide font-medium text-primary-light`.

---

## 5. Layout Principles

### Spacing scale
Standard Tailwind scale (`0`, `px`, `0.5`, `1` … `96`) plus a custom `160 = 40rem` for very wide fixed panels.

- **4px (`-1`)** — icon-to-text gap, tight chip padding.
- **8px (`-2`)** — list item vertical rhythm.
- **12–16px (`-3` to `-4`)** — default form field gap, card inner padding base.
- **24px (`-6`)** — section-to-section spacing inside a card.
- **32–48px (`-8` to `-12`)** — page-level section dividers.

### Grid
- 12-column grid available via `grid-cols-12`; most forms use 6/6 or 8/4 splits.
- Custom `grid-cols-products` (`minmax(0, 1fr) auto auto`) for product line items (name / qty / price).

### Container
Centered, with responsive horizontal padding:
- DEFAULT `px-4`
- `sm` `px-6`
- `lg` `px-8`
- `xl` `px-16`
- `2xl` `px-20`

### Whitespace rhythm
Information density first; aerate only across logical boundaries. Within a list/table, keep row padding consistent and predictable. Between blocks of unrelated information, use a `-6` or `-8` gap, not a heavier divider.

---

## 6. Depth & Elevation

Phorest uses **shadow sparingly**, primarily to lift floating surfaces above content. Most static UI sits flat on the page.

| Token | Shadow | Use |
|---|---|---|
| `shadow-none` | — | flat cards on a tinted background |
| `shadow-sm` | very subtle | dense cards in a grid |
| `shadow` (DEFAULT) | light | standard card surface |
| `shadow-md` | medium | hovered card, primary card on dashboard |
| `shadow-lg` | strong | dropdown menus, popovers, comboboxes |
| `shadow-xl` | stronger | modals, slideovers (paired with backdrop) |
| `shadow-2xl` | dramatic | onboarding spotlights only |
| `shadow-inner` | inset | scroll containers, keypads |

Surface hierarchy (front to back):
1. Toasts / notifications
2. Modals + slideovers (with `bg-black/50` backdrop)
3. Dropdowns, popovers, tooltips
4. Page content cards
5. Page background (`bg-gray-lightest` or white)

Never stack two `shadow-xl` surfaces directly on top of each other — promote the lower surface to flat or use a backdrop.

---

## 7. Do's and Don'ts

### Do
- **Do** use semantic color tokens (`bg-primary`, `text-danger-dark`) — never raw hex in component code.
- **Do** keep the primary action **once per view**. Secondary/tertiary buttons surround it.
- **Do** pair light backgrounds with darker text from the same family (e.g. `bg-success-lighter` + `text-success-darker`) to keep contrast accessible.
- **Do** use `Ui::*` components rather than re-implementing buttons, inputs, lists, etc.
- **Do** prefer acceptance-test-friendly DOM (real labels, `data-test-*` hooks, semantic elements).
- **Do** treat numbers (money, counts, durations) with consistent alignment and `font-medium`.

### Don't
- **Don't** mix `primary` (amber) and `theme` (sky) as both primary calls-to-action — `primary` always wins.
- **Don't** introduce new shadows or border radii outside the Tailwind scale.
- **Don't** use Phorest brand teal as functional UI color (it is reserved for the wordmark).
- **Don't** use uppercase body text or letter-spacing tricks outside small badge/header micro-labels.
- **Don't** add animations beyond `animate-spin` (loading) and `animate-pulse` (skeleton) in product UI.
- **Don't** put two filled status buttons (e.g. `bg-success` *and* `bg-danger`) competing in the same row — one stays filled, the other goes tertiary.
- **Don't** use empty `''` as a fallback in conditional template expressions; prefer the inverse condition.

---

## 8. Responsive Behavior

### Breakpoints (standard Tailwind)
| Token | Min width | Typical context |
|---|---|---|
| (none) | < 640px | tablet portrait, POS, phone fallback |
| `sm` | 640px | tablet portrait |
| `md` | 768px | tablet landscape |
| `lg` | 1024px | laptop |
| `xl` | 1280px | desktop |
| `2xl` | 1536px | wide desktop |

### Targets
- Phorest's primary form factor is **tablet (landscape, ~1024px)** on the salon floor, with desktop secondary. Pure mobile is not a primary surface.
- Touch targets must be **≥ 40px** tall. Buttons default to `h-9`/`h-10`; numeric keypads use larger 56–64px keys.

### Collapse behavior
- **Sidebar** — fixed on `lg+`; becomes an overlay/drawer below.
- **Multi-column forms** — collapse from `lg:grid-cols-2` to single column below.
- **Tables** — preserve horizontal scroll rather than stack rows; we never reshape a row into cards.
- **Slideovers** — `max-w-md` on `md+`; full-screen on smaller widths.
- **Modals** — stay centered, shrink `max-w-*` step-wise.

---

## 9. Agent Prompt Guide

When generating new screens or components based on this design system, use the following framing:

### System prompt seed
> You are designing for **Phorest**, a salon and spa management SaaS used on tablets in landscape on the salon floor and on desktops in back office. The interface is dense, calm, professional, and warm. Light theme only. Use the semantic Tailwind tokens defined in this design system — never raw hex. The primary amber (`#FBBF24`) is reserved for the single dominant call-to-action per view; sky-blue `theme` tokens are for informational chrome and calendar surfaces. Default body text is `text-sm` / `text-base`; numbers are `font-medium`.

### Useful prompt fragments
- *"Generate a list view of upcoming appointments using `Ui::StackedList` styling: avatar + client name (`text-sm font-medium`) + appointment time/service (`text-xs text-primary-light`), dividers `divide-y divide-gray-light`."*
- *"Build a confirm dialog with a danger primary action — use `bg-danger-dark text-white` for the destructive button and a tertiary `text-primary-darker` cancel."*
- *"Design an empty state for a clients list: muted `HeroIcon` in `text-gray-dark`, `text-base` instruction line, and a single primary button to create a client."*
- *"Compose a stats card grid for the dashboard: 4 columns on `lg+`, 2 on `sm+`, 1 below. Each stat: `text-3xl font-bold` figure over `text-xs uppercase tracking-wide text-primary-light` label."*

### Output expectations
- Prefer **semantic Tailwind utility classes** over inline styles.
- Provide accessible markup: real `<label>` + `<input>` pairs, `aria-*` where appropriate, focus rings (`focus:ring-primary`).
- When introducing new patterns, justify them against the **Do's and Don'ts** above; if they don't fit, propose adding to the design system rather than freelancing.
