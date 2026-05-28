---
version: alpha
name: Phorest
description: >
  Operational design system for Phorest, the salon, spa, and clinic SaaS.
  Tablet-landscape primary form factor (~1024px), desktop secondary.
  Light theme only. Restrained color, brutalist signature on interactive
  controls, operational density over breathing room.

colors:
  # Primary — brand accent, dominant CTA
  primary: "#FBBF24"
  primary-hover: "#F59E0B"

  # Ink — text, borders, icons. Pure black.
  ink: "#000000"
  ink-muted: "#6B7280"
  ink-subtle: "#9CA3AF"
  ink-inverted: "#FFFFFF"

  # Surfaces — light theme only
  canvas: "#F9FAFB"
  surface: "#FFFFFF"
  surface-muted: "#F3F4F6"

  # Borders
  border: "#E5E7EB"
  border-strong: "#9CA3AF"
  divider: "#E0E0E0"

  # Brand teal — wordmark only
  brand: "#134E4A"

  # Status
  success: "#059669"
  success-bg: "#D1FAE5"
  success-ink: "#065F46"
  warning: "#D97706"
  warning-bg: "#FEF3C7"
  warning-ink: "#92400E"
  danger: "#DC2626"
  danger-bg: "#FEE2E2"
  danger-ink: "#991B1B"
  info: "#2563EB"
  info-bg: "#DBEAFE"
  info-ink: "#1E40AF"

  # Theme — modal and slideover footers only
  theme: "#7DD3FC"
  theme-bg: "#F0F9FF"
  theme-ink: "#0C4A6E"

typography:
  stat:
    fontFamily: InterVariable
    fontSize: 30px
    fontWeight: 700
    lineHeight: 1.1
    fontVariation: "'numerals' tabular"
  h1:
    fontFamily: InterVariable
    fontSize: 24px
    fontWeight: 700
    lineHeight: 1.25
    letterSpacing: -0.01em
  h2:
    fontFamily: InterVariable
    fontSize: 20px
    fontWeight: 700
    lineHeight: 1.25
  h3:
    fontFamily: InterVariable
    fontSize: 18px
    fontWeight: 700
    lineHeight: 1.25
  body:
    fontFamily: InterVariable
    fontSize: 16px
    fontWeight: 400
    lineHeight: 1.5
  body-sm:
    fontFamily: InterVariable
    fontSize: 14px
    fontWeight: 400
    lineHeight: 1.5
  meta:
    fontFamily: InterVariable
    fontSize: 12px
    fontWeight: 400
    lineHeight: 1.5
  label-micro:
    fontFamily: InterVariable
    fontSize: 12px
    fontWeight: 500
    lineHeight: 1.5
    letterSpacing: 0.05em
  numeric:
    fontFamily: InterVariable
    fontWeight: 500
    fontVariation: "'numerals' tabular"
  code:
    fontFamily: "ui-monospace, SFMono-Regular, Menlo, Consolas, monospace"
    fontSize: 15px
    fontWeight: 400

spacing:
  "0": 0px
  "0.5": 2px
  "1": 4px
  "2": 8px
  "3": 12px
  "4": 16px
  "5": 20px
  "6": 24px
  "8": 32px
  "10": 40px
  "12": 48px
  "16": 64px
  "20": 80px

rounded:
  DEFAULT: 4px
  lg: 8px
  full: 9999px

components:
  # Buttons
  button-primary:
    backgroundColor: "{colors.primary}"
    textColor: "{colors.ink}"
    typography: "{typography.body-sm}"
    rounded: "{rounded.DEFAULT}"
    height: 40px
    padding: "0 12px"
  button-primary-hover:
    backgroundColor: "{colors.primary-hover}"

  button-secondary:
    backgroundColor: "{colors.surface}"
    textColor: "{colors.ink}"
    typography: "{typography.body-sm}"
    rounded: "{rounded.DEFAULT}"
    height: 40px
    padding: "0 12px"
  button-secondary-hover:
    backgroundColor: "{colors.surface-muted}"

  button-tertiary:
    backgroundColor: "{colors.surface}"
    textColor: "{colors.ink}"
    typography: "{typography.body-sm}"
    rounded: "{rounded.DEFAULT}"
    height: 40px
    padding: "0 12px"
  button-tertiary-hover:
    backgroundColor: "{colors.surface-muted}"

  # Input
  input:
    backgroundColor: "{colors.surface}"
    textColor: "{colors.ink}"
    typography: "{typography.body}"
    rounded: "{rounded.DEFAULT}"
    height: 40px
    padding: "0 12px"

  # Toggle
  toggle:
    backgroundColor: "{colors.surface-muted}"
    rounded: "{rounded.full}"
    width: 40px
    height: 24px
  toggle-on:
    backgroundColor: "{colors.success}"

  # Card
  card:
    backgroundColor: "{colors.surface}"
    rounded: "{rounded.lg}"
    padding: "16px"

  # Slideover
  slideover:
    backgroundColor: "{colors.surface}"
    rounded: "0px"
    padding: "16px"
  slideover-narrow:
    width: "520px"
  slideover-wide:
    width: "680px"
  slideover-footer:
    backgroundColor: "{colors.theme}"
    padding: "16px 24px"
---

## Overview

Phorest is operational software for salon staff who use it dozens of times
per shift. The visual character is deliberately restrained: pure black
ink on white, with crisp black strokes on interactive elements giving
the system its signature brutalist clarity. Color is sparse — an amber
accent on the dominant CTA, brand teal reserved for the wordmark,
status colors inside chips. At the frequency staff use the product,
anything louder becomes noise.

### Key Characteristics

- The white-stroked secondary button is the workhorse. The amber primary
  is reserved for one CTA per view, and not every view has one.
- Primary and secondary buttons carry a 1px black stroke on three sides
  plus a 2px stroke on the bottom edge. On press, the bottom edge
  collapses to 1px and the button nudges 1px down.
- Tertiary buttons: white background with a 1px light-gray border. No
  2px bottom edge. Lower visual weight than secondary.
- Destructive buttons: flat red fill, no stroke. Reserved for moments
  when data is being deleted or destroyed. Rarer than the amber primary.
- Inputs and selects: 1px black stroke at rest. On focus, the stroke
  thickens to 2px on all sides without layout shift (implemented via
  inset shadow).
- Toggles and checkboxes flip to brand green (#059669) when on. Amber
  is for action; green signals state.
- Brand teal (#134E4A) is wordmark-only. Never appears in functional UI.
- Light theme only. No dark surfaces.
- No gradients, no glassmorphism, no purple, no pink.

## Colors

Phorest's palette is built around restraint. Most visual weight is carried
by pure black ink on near-white surfaces. Color appears only in deliberate
roles.

### Primary

- **`{colors.primary}` — Amber (#FBBF24):** Brand accent. Reserved for the
  dominant CTA — one per view. Most operational surfaces have no amber
  button at all; work gets done by the white-stroked secondary.
- **`{colors.primary-hover}` (#F59E0B):** Press/hover state of the amber
  primary button.
- **`{colors.brand}` — Brand teal (#134E4A):** Wordmark only. Never a
  button, never a fill, never a stroke in functional UI.

### Ink

Default ink is pure black (#000000), not near-black. Applies to text,
icons, and borders on interactive elements. The brutalist character of
the system is built on this choice.

- **`{colors.ink}` (#000000):** Default text, default icon, default
  border on buttons and inputs.
- **`{colors.ink-muted}` (#6B7280):** Secondary text, captions, metadata.
- **`{colors.ink-subtle}` (#9CA3AF):** Tertiary text, fine print,
  placeholder text.
- **`{colors.ink-inverted}` (#FFFFFF):** Text on dark surfaces (rare).

### Surfaces

Light theme only. No dark mode.

- **`{colors.canvas}` (#F9FAFB):** Default page background.
- **`{colors.surface}` (#FFFFFF):** Cards, panels, default content surface.
- **`{colors.surface-muted}` (#F3F4F6):** Subtle elevation, secondary
  surfaces.

### Borders

- **`{colors.border}` (#E5E7EB):** Default 1px border on cards, dividers
  within cards, tertiary button outline.
- **`{colors.border-strong}` (#9CA3AF):** Heavier dividers, used against
  denser content.
- **`{colors.divider}` (#E0E0E0):** Heavier hairline at page-section
  boundaries.

### Status

Status colors live inside content (chip backgrounds, icon fills, error
text), not on chrome. Each status pairs a saturated value, a light
background, and darker text from the same family.

- **`{colors.success}` (#059669):** Toggle and checkbox "on" state, status
  chips, confirmation icons. Not used as a primary action color — amber
  owns action; green signals state.
- **`{colors.warning}` (#D97706):** Cautionary chips and inline warnings.
- **`{colors.danger}` (#DC2626):** Destructive button fill, error icons,
  error text. Rare.
- **`{colors.info}` (#2563EB):** Informational chips and neutral notices.

### Theme

`{colors.theme}` (#7DD3FC) is reserved for **modal and slideover footers
only**. It does not appear in primary UI chrome, navigation, calendars,
info banners, or anywhere else. Most narrowly scoped color in the system.

## Typography

Inter Variable for all product UI. One family, one scale, three weights.

### Hierarchy

- **`{typography.stat}` (30/700/1.1, tabular-nums):** Dashboard numbers,
  key metrics.
- **`{typography.h1}` (24/700/1.25):** Page titles. One per view.
- **`{typography.h2}` (20/700/1.25):** Section heads within a page.
- **`{typography.h3}` (18/700/1.25):** Sub-section heads, card titles.
- **`{typography.body}` (16/400/1.5):** Default running text.
- **`{typography.body-sm}` (14/400/1.5):** Dense metadata, table content.
- **`{typography.meta}` (12/400/1.5):** Captions, fine print, timestamps.
- **`{typography.label-micro}` (12/500/1.5, 0.05em, uppercase):** Small
  badges, table column headers, short pill labels. The single uppercase
  exception in the system.

### Numerics

Numbers carrying information (money, counts, durations, percentages) use
`{typography.numeric}` — tabular numerics with `font-weight: 500`.
Tabular ensures digits align vertically in tables and lists.

### Code

Ticket numbers, IDs, and inline code use `{typography.code}` — system
monospace stack.

### Casing

Sentence case everywhere. Title Case only for proper nouns (client names,
service names, brand names). The single uppercase exception is
`label-micro` for small badges and table column headers.

### Weights

Phorest uses three weights from Inter Variable: 400 (regular), 500
(medium), 700 (bold). Lighter and heavier weights are not used.

- **400:** Body, running text.
- **500:** Numeric data, micro-labels.
- **700:** Section heads, page titles, statistics.

Italic available for inline emphasis in body copy. Not used in headings,
buttons, or labels.

## Layout

Phorest is operational software for tablets in landscape (primary, ~1024px)
and desktops (≥1280px). Phones are not a supported product surface. The
layout system prioritizes density over breathing room.

### Grid

All spacing values are multiples of 4. The base grid step is 8px. When
choosing a spacing value, use the tokens defined in the front matter; do
not introduce off-grid values (6px, 10px, 14px).

Pages use a 12-column grid for desktop layouts (≥1024px) and a fluid
stack for narrower viewports. Common column splits: 6/6 for two-pane
layouts, 8/4 for content-with-sidebar, 9/3 for content with a slim
secondary column.

### Spacing Rules

Choose spacing values by the *relationship* between elements:

- **Tightly related** (icon + label, label + value): `{spacing.2}` (8px)
- **Related items in a row** (form fields side-by-side): `{spacing.3}` (12px)
- **Default padding inside cards:** `{spacing.4}` (16px)
- **Generous card padding:** `{spacing.6}` (24px)
- **Sections within a page:** `{spacing.6}` (24px) or `{spacing.8}` (32px)
- **Major page divisions:** `{spacing.8}` (32px) or larger

Whitespace in Phorest groups elements; it does not separate them. Tight
gaps signal "these belong together." Larger gaps signal "these are
distinct concerns." When choosing between two spacing values, prefer
the tighter one.

### Container Padding

Page horizontal padding scales with the viewport:

| Viewport | Page padding |
|----------|--------------|
| ≤768px (narrow) | 16px |
| ~1024px (tablet landscape, primary) | 24px |
| ~1280px (small desktop) | 32px |
| ≥1440px (wide desktop) | 64px |
| ≥1920px (extra-wide) | 80px |

### Fixed Layout Elements

- **Sidebar:** Fixed-left on desktop (~240px wide), full page height,
  white surface, no shadow. Collapses to a drawer below 1024px.
- **Page header:** Sits inside the page column. Not a separately-shadowed
  bar across the viewport. Page title at left, secondary actions at right.
- **Action bar:** Bottom-fixed bar; appears only when multi-select is
  active on a list view. White surface, `shadow-lg`.
- **Slideovers:** Slide in from the right. `bg-black/50` backdrop. Use
  the theme-blue footer treatment for the bottom action bar (see Colors
  → Theme).
- **Modals:** Fade in, center-screen. `bg-black/50` backdrop. Same
  theme-blue footer treatment as slideovers.

## Elevation & Depth

Phorest is flat. Static UI sits at zero elevation. Borders, not shadows,
distinguish surfaces.

### Shadow

A single shadow value is used in the system:

`shadow: 0 4px 6px -1px rgb(0 0 0 / 0.10), 0 2px 4px -2px rgb(0 0 0 / 0.10)`

Applied to: dropdown menus, date pickers.

Not applied to: cards, modals, slideovers, popovers, alerts, toasts, or
any static UI.

### Elevation Without Shadow

Surfaces are differentiated by borders, not by shadow:

- **Cards:** 1px `border` (#E5E7EB) on white surface. No shadow at rest
  or on hover.
- **Modals:** 1px border on white panel. `bg-black/50` backdrop behind.
  The backdrop alone communicates that the modal is above the page.
- **Slideovers:** 1px border on white panel. `bg-black/50` backdrop behind.
  Same elevation logic as modals.

### Forbidden

- No gradient backgrounds.
- No glassmorphism, no backdrop-blur.
- No bordered "left-accent-rail" cards (status indication lives inside
  the card, not on its frame).
- No purple, no pink, no off-brand decorative colors.

## Shapes

Two radii plus a fully-round value for the toggle thumb. No exceptions.

- **`{rounded.DEFAULT}` (4px):** Controls — buttons, inputs, selects,
  segmented controls.
- **`{rounded.lg}` (8px):** Surfaces — cards, panels, modals, slideovers.
- **`{rounded.full}` (9999px):** Toggle thumb. The only round element
  in the system.

Do not introduce new radii. If a design feels like it needs a 6px or
12px corner, the answer is to use 4 or 8, not to add a new value.

## Icons

Phorest uses **Heroicons** as the icon library. Outline style is the
default; solid is used only for filled status chips and rare emphasis
moments.

### Sizing

- **16px (`h-4 w-4`):** Inside dense lists and buttons.
- **20px (`h-5 w-5`):** Default size everywhere else.
- **24px (`h-6 w-6`):** Sidebar navigation and empty-state hero icons.

Avatars and decorative marks aside, no icon exceeds 24px.

### Stroke and Color

Heroicons default stroke weight (1.5px). No mixing with thinner or
heavier icon sets. Icons inherit text color via `currentColor`; muted
icons take `{colors.ink-muted}`, actionable icons take `{colors.ink}`.

### Format

Icons are consumed as inline SVG, not an icon font. Emoji and unicode
glyphs are not used as icons in product UI.

## Components

### Buttons

One size: 40px tall. One radius: 4px. 12px horizontal padding. Three
variants in regular use (primary, secondary, tertiary). Destructive is
not documented in this version (see Known Gaps).

#### Common Behavior

Primary and secondary buttons share the system's signature stroke
convention: **1px black border on three sides (top, left, right), plus
a 2px black border on the bottom edge**. On press, the bottom edge
collapses to 1px and the button translates 1px downward. This is the
system-wide click feedback — the button visibly "depresses" into the
surface.

Tertiary buttons drop the brutalist signature. They use a 1px
`{colors.border-strong}` border on all four sides — no 2px bottom edge,
no press nudge.

Disabled state for all variants: 50% opacity on the existing fill plus
`cursor: not-allowed`. No special disabled fill color.

#### Primary

`{component.button-primary}` — Amber background with black text, 1px
black stroke on three sides plus 2px bottom edge. Reserved for the
dominant CTA on a view. **One per view, and not every view has one.**
Most operational surfaces do not surface a primary button.

#### Secondary

`{component.button-secondary}` — White background with black text, same
stroke convention as primary (1px on three sides, 2px on the bottom).
**The workhorse of the system.** The brutalist signature lives here,
not on the primary. Used for the majority of action buttons across the
product.

Hover state: background shifts to `{colors.surface-muted}` (#F3F4F6) —
a visible mid-gray rather than a near-white tint. The contrast on hover
is deliberate, not subtle.

#### Tertiary

`{component.button-tertiary}` — White background with black text, 1px
`{colors.border-strong}` (#9CA3AF) border on all four sides. No 2px
bottom edge. No press nudge. Lower visual weight than secondary.

Used as a third action option when secondary is too heavy — typically in
forms with multiple optional actions, or in dialogs where the cancel
action needs to be present but visually subordinate.

#### Icon Buttons

When a button shows only an icon (no text label), it becomes a 40×40
square. The 1px+2px stroke convention applies to primary and secondary
icon buttons. Tertiary icon buttons follow the tertiary border
convention.

### Input

One size: 40px tall. 12px horizontal padding. 4px radius. Covers text
inputs, selects, segmented controls, and textareas.

#### Default

`{component.input}` — White background, body text, **1px black stroke**
on all four sides. The same pure black (#000000) used for ink, applied
as the input's border. This matches the brutalist treatment of buttons
but without the 2px bottom edge.

#### Focus

On focus, the stroke thickens to 2px on all four sides — **without
layout shift**. The implementation uses an inset box-shadow rather than
a wider border:

`box-shadow: inset 0 0 0 2px {colors.ink}`

The 1px outer border remains; the inset shadow paints over it to give
the appearance of a 2px stroke. This prevents the input from "jumping"
1px when focus enters or leaves. Critical in dense forms where every
field is adjacent — any layout shift propagates visually.

No focus ring, no outer outline, no color change. The thickened black
stroke alone signals focus.

#### Disabled

50% opacity on the existing background and text. The stroke remains 1px
black. Cursor: `not-allowed`.

#### Error

When an input is in an error state, the stroke shifts from black to
`{colors.danger}` (#DC2626). Same 1px thickness at rest, same inset
shadow treatment for the 2px on focus, but in red rather than black.
Error messages appear inline beneath the field in `{colors.danger-ink}`
(#991B1B).

### Toggle

Pill-shaped track with a round white thumb. **1px black stroke** around
the track. Two states: off and on.

#### Off

`{component.toggle}` — Gray track (`{colors.surface-muted}`, #F3F4F6),
40px wide × 24px tall, fully rounded, 1px black border. White thumb
(20×20, `{rounded.full}`) sits at the left of the track.

#### On

`{component.toggle-on}` — Same dimensions and 1px black stroke; the
track fill shifts to brand green (`{colors.success}`). The white thumb
slides to the right of the track. **Brand green, not amber.** Amber is
reserved for action; green signals state.

#### Checkboxes

Checkboxes follow the same on/off color logic: the unchecked state is
white with a 1px black border, the checked state fills with
`{colors.success}` and shows a white checkmark. Same principle — green
signals state.

### Card

The default content container. White surface, 8px radius, 1px border,
flat by default.

#### Structure

`{component.card}` — `{colors.surface}` (white) background,
`{rounded.lg}` (8px) radius, 1px `{colors.border}` (#E5E7EB) border on
all sides. Default padding: 16px. Generous padding: 24px for cards with
substantial content.

#### Elevation

Cards do not have shadow at rest. The 1px border alone defines the
card's edge. Cards do not have a hover state in static contexts — when
a card is itself interactive (clickable, draggable), the parent control
governs the interaction style, not the card's surface.

#### Title and Content

When a card has a title, it sits at the top-left in `{typography.h3}`
(18px, weight 700, line-height 1.25). Optional tertiary actions sit
at the top-right. The body content area uses `{typography.body}`
(16px regular) for prose or table content.

No colored left-border accent rail. No top-border color stripe. Status
indication, when needed, lives inside the card (chips, leading icons)
— never on the card's frame.

### Slideover

Right-sliding panel for forms, detail views, and multi-step flows. The
most common contextual surface in the product after cards.

#### Structure

`{component.slideover}` — White panel, slides in from the right, full
viewport height, no shadow, no rounded corners. 16px padding throughout
the panel.

Two width variants:

- **`{component.slideover-narrow}` (520px):** Default width. Used for
  forms, detail views, single-step flows.
- **`{component.slideover-wide}` (680px):** Used when content requires
  more horizontal room — tables, or flows where keeping critical
  information above the fold matters.

The page behind the slideover dims to `bg-black/50`. Clicking the
dimmed area closes the slideover.

#### Header

Always present. Contains:

- **Title** (`{typography.h2}`) at the top-left.
- **Close button** (tertiary icon button) at the top-right. Always
  present.
- **Back button** (tertiary icon button) at the top-left, before the
  title. Present only when the slideover is inside a flow with a
  previous step. First slideover in a flow has no back button;
  subsequent slideovers do.

The header has no background fill — it sits on the white panel surface.

#### Footer

`{component.slideover-footer}` — Theme-blue (`{colors.theme}`, #7DD3FC)
background. Contains the primary action button(s) for the slideover.

**Not always present.** Slideovers without a primary action (read-only
detail views, informational displays) have no footer. When a footer is
present, theme blue marks it as the action bar.

**Theme blue appears here and in the matching modal footer. Nowhere
else.** This is the entire scope of theme blue in the system.

#### Content

The content area between header and footer scrolls when content exceeds
viewport height. 16px padding throughout, matching the panel's overall
padding rhythm.

## Do's and Don'ts

### Do

- Use `{colors.primary}` (amber #FBBF24) for **one CTA per view, maximum**.
  Many views have no amber button at all.
- Pair amber primary fills with `{colors.ink}` (black) text, not white.
- Use the white-stroked secondary button as the default action button.
  It is the workhorse.
- Apply the 1px black stroke convention to all interactive controls
  (buttons, inputs, toggles, checkboxes) at rest.
- Apply the 2px bottom edge stroke to primary and secondary buttons
  only. On press, the bottom edge collapses to 1px and the button
  nudges 1px down.
- Use `{colors.success}` (#059669) for toggle/checkbox on-state and
  status chips. **Green signals state.**
- Use `{colors.primary}` (amber) for the dominant action button.
  **Amber signals action.**
- Use `{colors.brand}` (teal #134E4A) for the Phorest wordmark only.
- Use `{colors.theme}` (sky #7DD3FC) for slideover and modal footers
  only.
- Use tabular numerics (`{typography.numeric}`) for all numbers that
  carry information (money, counts, durations, percentages).
- Use sentence case for all UI text. Title Case only for proper nouns
  (client names, service names, brand names).
- Use the two-radius vocabulary: 4px for controls, 8px for surfaces.
- Use borders, not shadows, to differentiate surfaces. Shadow is for
  dropdowns and date pickers only.

### Don't

- Don't use two amber primary buttons on the same view.
- Don't paint primary buttons green or secondary buttons amber. Green
  signals state; amber signals action.
- Don't use brand teal (`{colors.brand}`) anywhere except the wordmark.
- Don't use theme blue (`{colors.theme}`) anywhere except slideover
  and modal footers.
- Don't add shadow to cards, alerts, toasts, or static UI. Phorest is
  flat by default.
- Don't use gradient backgrounds, glassmorphism, or backdrop-blur.
- Don't use a colored left-border or top-stripe on cards. Status
  indication lives inside the card, not on its frame.
- Don't use purple, pink, or any decorative color not defined in the
  Colors section.
- Don't introduce new radii (6px, 10px, 12px, 16px). Use 4 or 8.
- Don't introduce off-grid spacing values. Use multiples of 4.
- Don't use uppercase for body text or headings. The single exception
  is `{typography.label-micro}` for small badges and table column
  headers.
- Don't use Inter weights other than 400, 500, or 700.
- Don't use shadow as a "more important" signal. Shadow indicates
  float, not importance.
- Don't apply the 2px bottom edge to tertiary buttons, inputs, or any
  control other than primary/secondary buttons.
- Don't apply hover backgrounds on cards or non-button surfaces. Cards
  are flat across all states.
- Don't introduce dark mode. Phorest is light theme only.
- Don't use emoji as icons. Phorest uses Heroicons (outline by default).

## Known Gaps

This DESIGN.md is the first version of Phorest's design system
articulated for AI tool consumption. The following are not documented
in this version. They may be added in subsequent versions.

### Components Not Documented

- **Destructive button.** Used so rarely (only for genuine data
  destruction) that v1 omits it from the component token surface.
  Visual: flat `{colors.danger}` (#DC2626) fill, white text, no stroke.
  Behavior matches the press/disabled rules of other buttons.
- **Alert / banner system.** A real structural pattern in the product
  but not yet articulated as a system-level component. Two distinct
  classes exist (system/compliance vs. marketing/promotional) and the
  taxonomy is still being decided.
- **Dropdown menus.** Use the system's single shadow token and follow
  the input/select stroke convention, but specific dimensions and
  positioning rules are not articulated here.
- **Tooltips.** Not documented.
- **Status chips and badges.** Referenced in Colors and Typography
  but not given a component token entry.

### States Not Documented

- **Focus states (buttons).** Intentionally omitted from v1 because they
  are rarely engaged with directly in Phorest's primary form factor
  (tablet, touch). The inset-shadow focus mechanism for inputs is
  documented in Components; other focus states are not.
- **Animation tokens.** Phorest's toast, alert, and slideover
  animations are calibrated (Apple-inspired motion language with
  asymmetric easing) but not surfaced here as motion tokens.

### Surface-Specific Patterns Not Documented

- **Appointment screen color coding.** Each appointment on the
  appointment diary uses a loud, vibrant color identifying the assigned
  stylist or service. These are operational data colors, not design
  system colors. They are out of scope for the chrome palette
  documented in Colors.
- **Calendar component patterns.** The appointment diary is a
  Phorest-signature surface with its own typographic and color rules
  (including the use of SF Pro Display for appointment cards, which is
  the system's one font exception). Not documented at component level
  in v1.

### Known Drift

- **Stale button tokens in CSS.** The button component tokens in the
  upstream `colors_and_type.css` file are flagged as out of date
  relative to the actual rendered buttons (specifically the secondary
  hover and disabled states). The values documented in Components
  reflect actual rendered behavior, not the stale CSS tokens.

### Out of Scope

- **Marketing surfaces.** Phorest's marketing website uses Gilroy as a
  display face and follows a different visual register than product UI.
  Out of scope for this DESIGN.md.
- **Phorest Go (mobile companion).** A separate product surface with
  its own design language. Out of scope.
- **Dark theme.** Phorest is light-theme only. No dark variants exist.
