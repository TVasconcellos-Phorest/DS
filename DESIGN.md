---
version: alpha
name: Phorest
description: >
  Operational design system for Phorest Web, the salon, spa, and clinic SaaS.
  Tablet-landscape primary form factor (~1024px), desktop secondary.
  Light theme only. Restrained colour, black ink, crisp borders on
  interactive controls, operational density over breathing room.

colors:
  primary: "#FBBF24"
  primary-hover: "#F59E0B"
  primary-light: "#FCD34D"
  primary-lightest: "#FFFBEB"

  ink: "#000000"
  ink-muted: "#6B7280"
  ink-subtle: "#9CA3AF"
  ink-strong: "#111827"
  ink-inverted: "#FFFFFF"

  canvas: "#F3F4F6"
  canvas-lightest: "#F9FAFB"
  surface: "#FFFFFF"
  surface-muted: "#F3F4F6"

  border: "#E5E7EB"
  border-strong: "#9CA3AF"
  divider: "#E0E0E0"

  brand: "#134E4A"

  success: "#4ADE80"
  success-strong: "#16A34A"
  success-bg: "#F0FDF4"
  success-ink: "#166534"
  warning: "#FBBF24"
  warning-strong: "#D97706"
  warning-bg: "#FFFBEB"
  warning-ink: "#92400E"
  danger: "#F87171"
  danger-strong: "#DC2626"
  danger-bg: "#FEF2F2"
  danger-ink: "#991B1B"
  info: "#60A5FA"
  info-strong: "#2563EB"
  info-bg: "#EFF6FF"
  info-ink: "#1E40AF"

  theme: "#7DD3FC"
  theme-strong: "#38BDF8"
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
  title:
    fontFamily: InterVariable
    fontSize: 18px
    fontWeight: 500
    lineHeight: 1.5
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
  label:
    fontFamily: InterVariable
    fontSize: 14px
    fontWeight: 500
    lineHeight: 1.5
  meta:
    fontFamily: InterVariable
    fontSize: 12px
    fontWeight: 400
    lineHeight: 1.5
  numeric:
    fontFamily: InterVariable
    fontWeight: 500
    fontVariation: "'numerals' tabular"

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

rounded:
  DEFAULT: 4px
  md: 6px
  lg: 8px
  xl: 12px
  full: 9999px

components:
  button-primary:
    backgroundColor: "{colors.primary}"
    textColor: "{colors.ink}"
    typography: "{typography.label}"
    rounded: "{rounded.DEFAULT}"
    height: 40px
    padding: "8px 16px"
  button-primary-hover:
    backgroundColor: "{colors.primary-hover}"
  button-secondary:
    backgroundColor: "{colors.canvas-lightest}"
    textColor: "{colors.ink}"
    typography: "{typography.label}"
    rounded: "{rounded.DEFAULT}"
    height: 40px
    padding: "8px 16px"
  button-secondary-hover:
    backgroundColor: "{colors.surface-muted}"
  button-tertiary:
    backgroundColor: "{colors.surface}"
    textColor: "{colors.ink}"
    typography: "{typography.label}"
    rounded: "{rounded.DEFAULT}"
    height: 40px
    padding: "8px 16px"
  button-tertiary-hover:
    backgroundColor: "{colors.surface-muted}"
  button-danger:
    backgroundColor: "{colors.danger-strong}"
    textColor: "{colors.ink-inverted}"
    typography: "{typography.label}"
    rounded: "{rounded.DEFAULT}"
    height: 40px
    padding: "8px 16px"
  input:
    backgroundColor: "{colors.surface}"
    textColor: "{colors.ink}"
    typography: "{typography.body-sm}"
    rounded: "{rounded.DEFAULT}"
    height: 40px
    padding: "8px"
  switch:
    backgroundColor: "{colors.border}"
    rounded: "{rounded.full}"
    width: 44px
    height: 24px
  switch-on:
    backgroundColor: "{colors.success}"
  panel:
    backgroundColor: "{colors.surface}"
    rounded: "{rounded.lg}"
    padding: "16px"
  badge:
    backgroundColor: "{colors.border}"
    textColor: "{colors.ink}"
    typography: "{typography.meta}"
    rounded: "{rounded.full}"
    padding: "2px 10px"
  alert:
    backgroundColor: "{colors.info-bg}"
    textColor: "{colors.info-ink}"
    rounded: "{rounded.DEFAULT}"
    padding: "16px"
  modal:
    backgroundColor: "{colors.surface}"
    rounded: "{rounded.lg}"
    padding: "16px 24px"
  modal-footer:
    backgroundColor: "{colors.theme-strong}"
    padding: "12px 24px"
  slideover:
    backgroundColor: "{colors.surface}"
    rounded: "{rounded.xl}"
    padding: "16px"
  slideover-footer:
    backgroundColor: "{colors.theme-strong}"
    padding: "12px 16px"
---

## Overview

Phorest is operational software for salon staff who use it dozens of times
per shift. The look is deliberately restrained: black ink on white and light
grey, with crisp dark borders on interactive controls. Colour is sparse. Amber
marks the one dominant action, green marks state, and status colours live
inside content. At the frequency staff use the product, anything louder
becomes noise.

This file describes the live Ember product (`Ui::*` components and the
styleguide). When this file and the code disagree, the code wins.

### Key Characteristics

- Buttons are 40px tall with a 1px dark border and a 2px bottom edge. On press
  the button nudges 1px down.
- Amber primary is for the one dominant action of a view. Many views have none.
- Panels are bordered by default for new work: 1px grey stroke, 2px bottom
  edge, no shadow at rest, a shadow only on hover.
- Light theme only. No gradients, no glassmorphism, no purple, no pink.
- Product copy is sentence case. No emoji in titles or UI.

## Colors

### Primary

- **Amber (`primary`, #FBBF24):** Background of the primary button. Black text
  on top, never white. Hover is `primary-hover` (#F59E0B).
- **`brand` (#134E4A):** The Phorest wordmark only.

### Ink

Default text is pure black.

- **`ink`:** Text, icons.
- **`ink-muted` (#6B7280):** Secondary text, descriptions, metadata.
- **`ink-subtle` (#9CA3AF):** Tertiary text and placeholders.
- **`ink-strong` (#111827):** Border of buttons and switches.

### Surfaces

- **`canvas` (#F3F4F6):** Page background.
- **`surface` (#FFFFFF):** Panels, modals, slideovers, inputs.
- **`surface-muted` (#F3F4F6):** Hover fill for buttons and rows.

### Borders

- **`border` (#E5E7EB):** Panel borders and dividers inside panels.
- **`border-strong` (#9CA3AF):** Input borders, heavier dividers.
- **`divider` (#E0E0E0):** Hairlines at page-section boundaries.

### Status

Each status has a mid tone, a strong tone, a light background and a dark ink.
Alerts and badges use the light background with the dark ink; icons use the
strong tone.

- **Success (green):** Switch and checkbox on-state, success badges and alerts.
- **Warning (amber):** Cautionary badges and alerts.
- **Danger (red):** Danger button, error text and input border, error alerts.
- **Info (blue):** Informational badges, alerts and the notification border.

### Theme

Theme blue (`theme-strong`, #38BDF8) is the footer of modals and slideovers.
It does not appear in navigation, banners or anywhere else on the page.

## Typography

Inter Variable for all product UI. Weights 400, 500 and 700.

- **`h1` (24/700):** Page title. One per view.
- **`title` (18/500):** Modal titles, panel titles, section heads.
- **`body` (16/400):** Running text.
- **`body-sm` (14/400):** Table content, descriptions, inputs, buttons.
- **`label` (14/500):** Button labels, form labels.
- **`meta` (12/400):** Captions, badges, timestamps.
- **`stat` (30/700, tabular):** Dashboard numbers.

### Numerics

Numbers that carry information (money, counts, durations, percentages) use
tabular numerals so digits line up in tables and lists.

### Casing

Sentence case everywhere. Title Case only for proper nouns (client names,
service names, brand names). Uppercase is only for small badges and table
column headers.

## Layout

Tablet landscape (~1024px) is the primary surface, desktop second. Phones are
not a supported product surface.

### Spacing

Spacing uses multiples of 4. Choose by how related things are:

- **Icon and label, label and value:** 8px.
- **Fields side by side:** 12px.
- **Panel padding:** 16px.
- **Between sections:** 24px or 32px.

Tight gaps say "these belong together". Larger gaps say "these are separate".
When unsure, take the tighter one.

### Page structure

- **Page:** `Page::Layout` with a title. The page background is `canvas`.
- **Actions bar:** `Page::ActionsBar` sits at the bottom of the page. The
  primary action of a list page lives there, including when the list is empty.
- **Panels:** group content on the page; see Components.

## Elevation & Depth

The product is mostly flat. Borders define most surfaces. Shadow is used for
things that float or respond to hover.

- **Panels:** no shadow at rest. A bordered panel gets a shadow on hover when it
  is interactive.
- **Dropdowns and date pickers:** small shadow.
- **Modals and dialogs:** `shadow-xl` over a dark overlay (`grey-600` at 75%).
- **Notifications:** `shadow-xl` with a 2px info border.
- **Slideovers:** dark overlay, no shadow, a 2px edge on the open side.
- **Buttons:** a subtle shadow on primary and tertiary buttons.

Shadow signals float, not importance.

### Forbidden

- Gradient backgrounds.
- Glassmorphism and backdrop-blur.
- A coloured left border or top stripe on a panel. Status goes inside the
  panel, as a chip or a leading icon.
- Purple, pink and decorative colours outside the palette.

## Shapes

- **4px (`rounded`):** Buttons, inputs, selects, alerts.
- **6px (`rounded-md`):** Tags and the legacy `card` panel.
- **8px (`rounded-lg`):** Panels, modals, dialogs, notifications.
- **12px (`rounded-xl`):** The open edge of a slideover.
- **Full:** Badges, switches.

## Icons

Heroicons, as inline SVG through `Ui::HeroIcon`.

- **Outline, 24px:** The default.
- **Solid, 20px:** Filled status marks and emphasis.
- **16px:** Inside inputs and dense controls.
- **Colour:** Icons follow text colour. Muted icons use `ink-muted`.
- **Modal icon:** 28px, in the status colour of the modal.

Do not use emoji or unicode glyphs as icons. Do not mix icon sets.

## Components

Use the existing `Ui::*` components and their variants. Do not rebuild a
control by hand.

### Buttons

`Ui::Button`. One height: 40px. 4px radius, 14px medium label, 16px by 8px
padding. Lead the label with a verb: "Save changes", "Add client".

All variants share a 2px bottom edge. On press the button moves 1px down.
Disabled buttons are at 50% opacity and ignore the pointer.

- **Primary:** Amber fill, black text. One per view, at most. Hover darkens to
  amber-500.
- **Secondary:** Light grey fill. The default for everyday actions. Hover is a
  darker grey.
- **Tertiary:** White fill, dark border. Quieter actions such as Cancel.
- **Success:** Green fill, white text.
- **Danger:** Red fill, white text. Only for permanent deletion. Never use
  primary for a destructive action.
- **Ghost:** Text only, for low-emphasis actions on a coloured surface.

Icon-only buttons are 40px squares and must have a screen-reader label
(`@srLabel`). Loading shows a spinner and hides the label (`@showLoading`).
Do not use a button for navigation: links use `LinkTo`, and `Ui::LinkButton`
only when a link must look like a button.

### Button group

`Ui::ButtonGroup` joins related buttons into one control, for example a
Day / Week / Month switch. The active button is marked with `@isActive`.
`Ui::SegmentedControl` is the alternative for a pure view or filter switch.

### Input

`Ui::Input`, with `Ui::Form` and `InputGroup` for labelled fields. 40px tall,
4px radius, 14px text, grey border (`border-strong`). On focus the border
turns near-black with a ring. Disabled is 50% opacity. Errors turn the border,
text and placeholder red and show the message under the field.

Fields do not show a "Required" marker, even when required. The validation
schema enforces it and the error says so.

### Switch and checkbox

The switch is 44 by 24px, a pill with a 1.5px dark border and a white thumb.
Off is grey, on is green. Checkboxes use the same logic: white with a dark
border when unchecked, green with a checkmark when checked. Green signals
state; amber signals action.

### Panel

`Ui::Panel` groups content. White surface, 16px padding. The variant sets the
edge:

- **`bordered`:** The default for new work. 8px radius, 1px `border` stroke
  with a 2px bottom edge, no resting shadow, a shadow only on hover. Use it for
  cards, especially on the grey page background.
- **`rounded`:** The component's current default. 8px radius with a resting
  shadow. Legacy look, still widespread.
- **`outline`:** 8px radius with a theme-blue stroke. Legacy.
- **`flat`:** Top and bottom borders only, no radius. For full-width bands.
- **`card`:** 6px radius, no border. Legacy.

When a panel has a title, it sits top-left in `title` style. Do not add
shadow to signal importance. Do not paint the frame to signal status.

### Badge and tag

`Ui::Badge` is a full-round pill, 12px text, light status background with dark
ink. Variants: default, success, warning, danger, info. `Ui::Tag` is a 6px
rounded chip with a border, for user-applied labels, with an optional icon.
Use a badge for status, counts and labels, not a button.

### Alert and notification

`Ui::Alert` is a 4px rounded box with a light status background, a status icon
and dark status text. Variants: info, success, warning, danger.
`Ui::Notification` is the floating toast, with `shadow-xl` and a 2px info
border.

### Modal

`Ui::Modal` is a centred dialog, 8px radius, `shadow-xl`, default width 512px,
over a dark overlay. It has an optional 28px status icon, an 18px medium
title and a 14px muted description.

The footer is theme blue and holds the buttons. Primary buttons sit on the
right. Use `DangerButton` for destructive confirmation and `CancelButton` for
the way out. Label the confirm button with the outcome: "Delete client".

### Slideover

`Ui::SlideOver` slides in from the right, full height, over a dark overlay.
Three widths: narrow (320px), normal (the default) and wide (up to 768px).

The footer is theme blue and sticky, with secondary actions on the left and
primary actions on the right. Slideovers without a primary action have no
footer.

Let it close the usual ways: click outside, Escape, the back arrow and Cancel.
Avoid `@preventFromClosing`. With unsaved edits, closing goes through the
discard-changes prompt.

### Empty collection

`Ui::EmptyCollection` shows an icon, a title and a description where a list
would be. It is not interactive, so put any action button next to it.

### Separator

A hairline in `border`, with generous vertical space around it.

## Patterns

### List page and edit slideover

For a page that lists records of one kind and lets the user add and edit them.

- **List:** `Page::Table` inside `Page::Layout`, with a filters bar on top.
- **Opening a record:** Clicking anywhere on a row opens it. Cells stay plain
  text. Avoid styling a cell as a link.
- **Add:** The primary action sits in the bottom `Page::ActionsBar`, even when
  the list is empty.
- **Selection:** Optional. Add a selection column only when an action works on
  the selected rows. Use `TC.SelectColumn` as the first column.
- **Small resource:** Create and edit open a slideover over the list.
- **Big resource:** A resource with many fields, such as Client or Package,
  gets its own page.

### Forms

- `Ui::Form` with a validation schema, one `InputGroup` per field in a
  one-column cards layout.
- The first field is focused when the form opens.
- No "Required" marker on fields.
- Cancel and Save sit in the slideover footer. Save is disabled until something
  has changed, and shows a spinner while saving.

## Do's and Don'ts

### Do

- Use one amber primary button per view, at most.
- Pair amber with black text, not white.
- Use secondary for everyday actions and tertiary for Cancel.
- Use danger red only for permanent deletion.
- Use green for state (switch, checkbox, success) and amber for action.
- Use the bordered panel for new cards.
- Use theme blue for modal and slideover footers only.
- Use tabular numerals for numbers that carry information.
- Use sentence case for all UI text.
- Use `Ui::*` components and Heroicons before building anything custom.
- Put the primary action of a list page in the bottom actions bar.

### Don't

- Don't use two amber primary buttons on one view.
- Don't paint a primary button green or a secondary button amber.
- Don't use primary for a destructive action.
- Don't use brand teal anywhere except the wordmark.
- Don't use theme blue outside modal and slideover footers.
- Don't add shadow to a panel at rest, or to signal importance.
- Don't use a coloured left border or top stripe on a panel.
- Don't use gradients, glassmorphism or backdrop-blur.
- Don't use emoji in titles, copy or icons.
- Don't use uppercase for headings or body text.
- Don't show a "Required" marker on form fields.
- Don't style a table cell as a link when the row opens the record.
- Don't use a button for navigation.
- Don't introduce dark mode.

## Out of scope

- **Appointment diary colours.** Appointments use vibrant per-stylist or
  per-service colours. These are data colours, not chrome.
- **Marketing site.** Different type and register.
- **Phorest Go (mobile).** A separate design language.
- **Dark theme.** None exists.
