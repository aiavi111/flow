# Flow Design System

Flow is a boutique yoga studio: a physical practice space, a companion booking app, and a marketing
website for people finding their way to a class. This design system was built from a single source
— there was no existing brand, codebase, or Figma file to pull from — so everything here is an
original visual identity, invented to serve that one starting image and the brief that came with it.

## Sources

- **`uploads/Gemini_Generated_Image_1d2kge1d2kge1d2k.jpeg`** — the only material provided. An
  AI-generated interior photo of two people practicing yoga in a bright, wood-floored studio with
  floor-to-ceiling glass doors onto a Japanese-influenced garden. Copied into
  `assets/imagery/studio-practice-01.jpg`. Every color, material cue, and mood decision in this
  system traces back to this one image — there was no logo, codebase, Figma file, deck, or product
  copy to reference.
- **Brief answers**: brand name "Flow"; offering = physical yoga/fitness studio. Color mood,
  typography, voice, and which surfaces to design were left to this system's judgment (no
  existing logo or brand files were supplied).

No repo, Figma link, or deck is associated with this project. If one exists, attach it and this
system should be revised to match it as ground truth — right now it is a from-scratch invention.

## Index

- `styles.css` — root stylesheet, `@import`s everything below. Link this one file.
- `tokens/` — `colors.css`, `typography.css`, `spacing.css`, `radius.css`, `shadow.css`,
  `motion.css`, `fonts.css`
- `base.css` — element resets (body defaults, link colors, focus ring)
- `guidelines/` — foundation specimen cards (colors, type, spacing, radius, shadow, motion, brand)
- `components/core/` — Button, IconButton, Badge, Tag, Card, Icon
- `components/forms/` — Input, Select, Checkbox, Radio, Switch
- `components/feedback/` — Dialog, Toast, Tooltip
- `components/navigation/` — Tabs, NavBar, BottomNav
- `ui_kits/website/` — marketing site: Home, Schedule, Pricing, Instructors
- `ui_kits/app/` — booking app: Welcome, Schedule, Class detail, Profile
- `ui_kits/shared-data.js` — class/instructor/pricing data shared by both kits
- `assets/imagery/` — the one source photo
- `thumbnail.html` — homepage tile for this design system
- `SKILL.md` — Claude Code / Agent Skills-compatible entry point

## Content fundamentals

**Voice: calm and meditative.** Flow writes the way a good teacher cues a pose — short, grounded
sentences, present tense, room to breathe. Copy never rushes or hypes.

- **Person**: second person, direct and warm — "you" throughout ("Start where you are"), never
  "our members" or third-person distancing.
- **Sentence length**: short. One idea per sentence. Line breaks do work that punctuation would
  otherwise have to.
- **Casing**: sentence case everywhere — headlines, buttons, nav labels. No title case, no
  all-caps except small eyebrow labels (e.g. "TODAY", tracked wide, used sparingly).
  Sample eyebrow only — not the mid-body voice.
- **Exclamation points**: none. Enthusiasm is conveyed through word choice and rhythm, not
  punctuation.
- **Emoji**: never. Flow's calm doesn't need decoration.
- **Jargon**: avoided. No "synergy," "wellness journey," "unlock your potential." Plain, physical,
  sensory words instead: breathe, move, land, return, settle.
- **Example copy** (for reuse verbatim across mocks):
  - Hero: "Breathe. Move. Return to yourself."
  - Sub-head: "A quiet studio for morning and evening practice, ten minutes from downtown."
  - Body: "Start where you are. Every class meets you there — new to the mat or ten years in."
  - Button labels: "Book a class", "See today's schedule", "Reserve your spot" (never "Sign up
    now!" or "Get started today!!")
  - Empty state: "Nothing booked yet. Today's schedule is below."
  - Confirmation: "You're in. See you on the mat."

## Visual foundations

- **Color**: warm and earthy, sampled directly from the source photo — light oak floor, plaster
  walls, and dark umber wood become the "stone" neutral scale (`--stone-50`…`--stone-900`); the
  terracotta practicewear becomes "clay," the primary accent; the garden greenery becomes "sage,"
  the secondary accent. Backgrounds stay in cream/paper tones; ink is a warm near-black
  (`--stone-900`, #241c15), never pure black. Max two accent hues on top of the neutral scale, per
  system discipline.
- **Type**: a serif display face (Newsreader) for headlines paired with a clean humanist sans
  (Public Sans) for everything functional — body copy, labels, buttons, UI chrome. Display type
  runs at tight tracking and large sizes for a quiet, editorial confidence; body type stays highly
  legible and neutral. No monospace — Flow has no code or tabular data that needs it.
  **Note**: no brand font files were supplied, so these are Google Fonts standing in for a real
  brand typeface. See Caveats.
- **Spacing**: 4px base grid, from 4px to 128px. Layouts are generous and airy — the studio photo
  is full of negative space, and the UI should breathe the same way. Section padding defaults to
  `--space-16`–`--space-24` on desktop.
- **Backgrounds**: mostly flat cream (`--bg-page`) or warm white (`--bg-surface`) fields. Full-bleed
  photography is used for hero moments (the studio photo). No gradients, no repeating patterns or
  textures, no hand-drawn illustration — the brand's calm comes from restraint, not decoration.
- **Imagery mood**: warm, naturally lit, real interiors and real bodies in motion — not stock-glossy.
  Soft daylight, wood and plaster tones, greenery. No black-and-white, no heavy grain, no cool/blue
  color grading.
- **Animation**: gentle fades and soft upward slides only (`--duration-base` 240ms,
  `--ease-standard`). No bounce, spring, or elastic easing anywhere — those read as playful/energetic,
  which is off-brand for a calm, meditative studio. Motion should feel like an exhale, not a bounce.
- **Hover states**: primary surfaces darken one step (`--accent-primary` → `--accent-primary-hover`);
  ghost/text buttons gain a soft tinted background (`--accent-primary-soft`). No lightening, no glow.
- **Press/active states**: darken one step further (`--accent-primary-active`) with no scale/shrink
  transform — presses are calm, not springy.
- **Borders**: hairline (1px), warm-neutral (`--border-subtle` / `--border-default`), never black.
  Used to separate flat surfaces of the same color rather than shadows, especially in dense UI
  (schedule rows, form fields).
  Note: components and specimen cards render 1px borders as CSS `border: 1px solid`; if the
  compiler's adherence linting expects `border-width` as a distinct declared token, treat
  `border-default`/`border-subtle` as valid literal 1px hairlines rather than a numeric token.
- **Shadow**: soft and warm-tinted (`rgba(36,28,21,…)`, never pure black), used sparingly — resting
  cards mostly rely on a hairline border instead of a shadow; shadow is reserved for elevated/
  overlaid surfaces (menus, dialogs, toasts).
- **Corner radii**: soft but not bubbly — `--radius-md` (14px) is the default for cards, fields, and
  buttons; `--radius-lg`/`--radius-xl` for larger sheets and modals; `--radius-full` for pills and
  avatars only.
- **Cards**: warm-white surface, hairline border, `--radius-md`, `--shadow-xs` at rest,
  `--shadow-sm`/`--shadow-md` only on hover or when elevated (menus/popovers). No colored left-border
  accent strips.
- **Transparency & blur**: reserved for overlays only — the modal scrim (`--bg-overlay`, 45% warm
  black) and a sticky nav bar that gains a blurred translucent background once the page scrolls.
  Not used decoratively elsewhere.
- **Layout rules**: top nav is sticky on the marketing site; the app uses a fixed bottom tab bar.
  Content otherwise scrolls normally — no other fixed/pinned elements.
- **Iconography**: see below.

## Iconography

No icon set shipped with the source material, so this system uses **Lucide** (ISC-licensed) via
the `lucide-static` CDN mirror on unpkg — thin 1.75px-equivalent stroke, rounded caps/joins, no
fill, which matches the calm, unadorned line-quality of the rest of the system better than a
filled or duotone set would. Each icon loads as a single static SVG, tinted via a CSS `mask-image`
so it inherits `currentColor`/a `color` prop with no JS icon runtime required. Substitution
flagged: if Flow later adopts its own icon set, swap the base URL in one place (`Icon.jsx`) and
every component/kit updates.

- Components and kits consume icons through `components/core/Icon.jsx` (`<Icon name="calendar" />`),
  never inline hand-drawn SVG.
- Sizes: 16px (inline with text/labels), 20px (default, buttons/fields), 24px (standalone tap
  targets in nav).
- Emoji and Unicode symbols are never used as icons (see Content fundamentals — no emoji anywhere).
- No custom icon font; no PNG icons.

## Intentional additions

The brief defined no existing component inventory (no attached codebase or Figma), so this system
authors the standard primitive set the instructions call for, sized to what a small studio's site
and booking app actually need. Two additions beyond that standard list, because the product
concretely needs them:

- **`Icon`** — thin wrapper around the Lucide CDN icon set (see Iconography). Every other
  component that shows an icon (Select's chevron, Toast's status glyph, NavBar's menu glyph...)
  composes this rather than inlining SVG.
- **`NavBar`** / **`BottomNav`** — the marketing site's sticky top nav and the app's fixed bottom
  tab bar are structural chrome every screen in their respective kit reuses, so they're primitives
  rather than one-off markup repeated in each screen.

## Caveats — please help me iterate

- **No brand assets were provided.** There is no logo, no existing color palette, no brand
  typeface, and no product copy. Every visual and verbal decision here (palette, type pairing,
  voice, even the name "Flow" as a studio rather than something else) was invented from one mood
  photo. If you have a real logo, brand fonts, or existing copy, send them over and I'll rebuild
  the affected foundations to match.
- **Typefaces are Google Fonts substitutes** (Newsreader + Public Sans) chosen to match the mood of
  the source photo, not a licensed brand typeface. Swap `tokens/fonts.css` if you have real font
  files.
- **Iconography is a CDN substitution** (Lucide), not a brand-original icon set — flagged above.
- **No logo mark exists** — every place a mark would go instead shows "Flow" set in
  `--font-display`, italic, as a plain wordmark. If you have a real logo, drop it in `assets/` and
  I'll wire it through the nav and cards.
- **Component inventory was invented**, not sourced — there was no Figma file or codebase defining
  which primitives Flow actually uses in production, so I built the standard set a studio site/app
  needs (see Intentional additions above for the two beyond that baseline).

**The single clearest way to make this dramatically more accurate: send a real logo, brand font
files, existing product copy, or a Figma/codebase link if one exists.** Short of that, tell me if
the palette, voice, or component set feels off and I'll tune it.
