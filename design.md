# Design System

## 1. Purpose

This document is the **SINGLE SOURCE OF TRUTH** for the visual and interaction design of the application. It governs all user interface decisions, visual styles, component behaviors, interaction patterns, accessibility standards, and spatial layouts across light and dark themes.

All developers and AI coding agents must consult and adhere strictly to this specification before creating, modifying, or refactoring any interface element. No styling decisions—such as custom colors, one-off spacing, arbitrary font sizes, custom corner radii, or bespoke animations—may be introduced unless explicitly defined herein.

This is a **custom design system** constructed on top of `shadcn-vue` primitives. While influenced by the functional clarity of Material Design 3, it is **not** a Material Design implementation. Material components, Material tokens, and Google-specific visual identities must not be blindly reproduced. The principles and tokens established in this file are authoritative.

When implementing UI features, developers and AI agents must follow this precedence hierarchy:

1. **Semantic Token** →
2. **shadcn-vue Primitive** →
3. **Component State** →
4. **Application Composition**

---

## 2. Design Philosophy

### The Adaptive Canvas

An interface is a context-aware medium that mediates human intent. Its sole purpose is to reduce friction between human thought and desired outcomes, transforming complex underlying systems into clear, controllable, and responsive mental models.

Software must respect human cognition, conserve human energy, and adapt fluidly to human context. When an interface succeeds, technology recedes into the background, leaving the user feeling capable, oriented, and in total control.

### Philosophy Statement

A good digital interface believes that **clarity is empathetic, adaptivity is respectful, and restraint is powerful**.

* **What an interface is for:** To extend human capability—converting intent into action with minimal cognitive friction, maximum predictability, and zero artificial complexity.
* **What users should understand:** Where they are, what the active system state is, what actions are available, and what the consequences of those actions will be.
* **What users should feel:** Safe, oriented, capable, and respected—never confused, overwhelmed, tricked, or patronized.
* **What users should accomplish confidently:** Explore, initiate, execute, and recover from complex workflows with complete clarity on system activity and outcome.

```
┌───────────────────────────────────────────────────────────────────────────┐
│                            DECISION HIERARCHY                             │
├───────────────────────────────────────────────────────────────────────────┤
│ 1. HUMAN NEEDS          (Safety, agency, cognitive well-being)            │
│ 2. ACCESSIBILITY        (Universal perception, interaction, & inclusion)  │
│ 3. CLARITY              (Unambiguous meaning, explicit intent)            │
│ 4. USABILITY            (Ergonomics, efficiency, error prevention)        │
│ 5. COHERENCE            (Systemic logic, predictable mental models)         │
│ 6. CONTEXT              (Adaptation to space, task, device, & environment)│
│ 7. EXPRESSION           (Brand voice, character, editorial flair)         │
│ 8. AESTHETIC PREFERENCE (Visual novelty, stylistic trends)                │
└───────────────────────────────────────────────────────────────────────────┘

```

### The Five Experiential Pillars

| Dimension | System Requirement |
| --- | --- |
| **Understand** | Spatial position, active system state, and structural logic are always transparent. |
| **Accomplish** | Direct paths, protected focus, and zero arbitrary friction across workflows. |
| **Control** | Clear intent triggers, configurable views, and explicit human choices. |
| **Anticipate** | Predictable outcomes, clear warnings, and obvious visual affordances. |
| **Recover From** | Non-destructive operations, simple undo options, and helpful error recovery. |

---

## 3. Core Design Principles

### Principle 01: Cognitive Ergonomics First

* **Meaning:** Human working memory is strictly limited. Interfaces that demand excessive processing cause fatigue, error, and frustration.
* **Why it exists:** To preserve user attention and prevent operational mistakes during complex tasks.
* **Implementation:** Structure information into logical chunks, eliminate redundant choices, use predictable visual cues, and keep active task canvases free of ambient visual noise.

### Principle 02: Multi-Signal Redundancy

* **Meaning:** Critical information must never depend on a single perceptual channel (such as color alone or font weight alone).
* **Why it exists:** Single channels fail under varying lighting, display scale differences, and human visual impairments.
* **Implementation:** Pair color cues with explicit text labels, distinct icons, shape changes, or border indicators.

### Principle 03: Multi-Signal Hierarchy

* **Meaning:** Hierarchy emerges from coordinated visual signals applied simultaneously with appropriate emphasis.
* **Why it exists:** Weak visual hierarchy forces users into linear scanning, increasing task completion time.
* **Implementation:** Combine scale, surface contrast, typographic weight, and spatial placement to mark structural priority without overloading any single channel.

### Principle 04: Structural Layout Transformation

* **Meaning:** Canvases must reorganize structural layouts based on available space and task context rather than uniformly scaling UI down.
* **Why it exists:** Uniformly shrinking desktop views makes text unreadable and controls hard to target on smaller screens.
* **Implementation:** Convert multi-column desktop arrangements into sequential single-pane flows on compact viewports or during focused task execution.

### Principle 05: Functional Layering & Depth

* **Meaning:** Depth and layering communicate spatial relationships, temporal focus, and component hierarchy—never decoration.
* **Why it exists:** Excessive drop shadows create visual clutter, while flat interfaces obscure boundaries between primary content and temporary overlays.
* **Implementation:** Rest resting cards on baseline canvases using surface tone shifts. Reserve elevation shadows and z-index layers for floating triggers, dropdown popovers, slide-over drawers, and modal dialogs.

### Principle 06: Temporal Orientation

* **Meaning:** Motion explains spatial origins, element transformations, and state transitions across time.
* **Why it exists:** Instant visual cuts disrupt cognitive momentum, forcing the human brain to re-orient.
* **Implementation:** Animate view transformations to show where elements come from and go to. Keep transitions fast (100ms–300ms), physical, and restrained.

### Principle 07: Systemic Visual Roles

* **Meaning:** Colors and visual treatments map strictly to systemic visual roles and interaction states rather than aesthetic preference.
* **Why it exists:** Arbitrary decorative color creates confusion; systematic mapping establishes instantaneous mental shortcuts across the product.
* **Implementation:** Use abstract functional tokens (`primary`, `accent`, `destructive`, `surface-card`) and ban raw HEX assignments in UI code.

### Principle 08: Proportional Typographic Rhythm

* **Meaning:** Typography structures reading cadence through proportional scaling, inverse line-heights, and bounded column widths.
* **Why it exists:** Text forms the core of human-computer dialogue; poor typography causes severe eye fatigue.
* **Implementation:** Bound narrative body blocks to ergonomic reading widths (45–75 characters), scale line-heights inversely with font size, and maintain distinct weight shifts between headings and body text.

### Principle 09: Causal State Feedback

* **Meaning:** Every human action produces an immediate, physical visual response at the point of contact.
* **Why it exists:** Unacknowledged input creates user anxiety, leading to accidental double-clicks and repeated submissions.
* **Implementation:** Provide point-of-contact actuation highlights within 100ms for hover, press, focus, and selection events.

### Principle 10: System State Transparency

* **Meaning:** The interface must explicitly distinguish between completed, pending, processing, failed, unavailable, uncertain, and action-required states.
* **Why it exists:** Hiding processing or failure causes lost confidence and duplicate operations.
* **Implementation:** Never imply success before validation completes. Display explicit status indicators, progress bars, or active verb labels during asynchronous operations.

### Principle 11: Progressive Task Disclosure

* **Meaning:** Surface primary tools directly while stowing secondary configurations in collapsible or on-demand overlays.
* **Why it exists:** Revealing every feature simultaneously paralyzes decision-making and hides primary workflows.
* **Implementation:** Keep primary task canvases clear by moving auxiliary context, filter options, and settings into drawers, popovers, or expandable panels.

### Principle 12: Human Language as Infrastructure

* **Meaning:** UI copy, labels, and messages are structural infrastructure equal in importance to visual controls.
* **Why it exists:** Technical jargon and cryptic codes halt user momentum.
* **Implementation:** Write clear, concise copy starting with active verbs ("Save changes", "Export report"). Structure error messages around what happened, why, and how to recover.

### Principle 13: Asynchronous State Honesty

* **Meaning:** Asynchronous operations that take time or run in the background must be represented honestly without false finality.
* **Why it exists:** Treating optimistic or pending changes as final results causes confusion if back-end processes fail.
* **Implementation:** Mark optimistic updates as pending until back-end confirmation arrives. Update state indicators dynamically upon completion.

### Principle 14: Systematic Visual Restraint

* **Meaning:** Interfaces default to quiet, low-chroma neutral canvases, reserving high saturation for focal triggers and status cues.
* **Why it exists:** When every visual element demands attention, nothing stands out.
* **Implementation:** Eliminate decorative borders, saturated wallpaper fills, ambient animations, and unneeded badges. Let content lead.

### Principle 15: Responsive & Contextual Adaptation

* **Meaning:** Screen structure, spatial density, target boundaries, and navigation adapt fluidly to screen space, input hardware, and task intent.
* **Why it exists:** Pointer-optimized tools fail on touch screens; spacious consumer layouts frustrate dense data management tasks.
* **Implementation:** Expand interactive targets to 44x44px minimum on touch devices; offer high density in data grids and relaxed density in reading or onboarding flows.

### Principle 16: Expression & Personality

* **Meaning:** Brand personality and editorial warmth belong in overview states, empty states, and onboarding flows, receding in utilitarian workspaces.
* **Why it exists:** Overly decorative workspaces slow down expert execution.
* **Implementation:** Use expressive typography and atmospheric tones in welcome views, transitioning to high-contrast, uncluttered workspaces during active tasks.

---

## 4. Design Personality

### Visual Character

* **Quiet & Structured:** Built on low-chroma neutral surfaces (`surface-base`, `surface-card`, `surface-muted`) that allow content to stand out.
* **Precise & High-Contrast:** Sharp contrast ratios, deliberate grid alignment, clean typography, and purposeful borders.
* **Functional Geometry:** Rounded corners (`radius-md` 6px for controls, `radius-lg` 8px for containers) that feel modern yet disciplined.

### Emotional Tone

* **Calm & Oriented:** Never frantic, saturated, or noisy.
* **Empathetic & Honest:** Communicates failures and uncertainty clearly without technical jargon or deceptive patterns.
* **Dependable & Responsive:** Responds instantly to physical touch and mouse interaction.

### Visual Density & Hierarchy

* **Adaptive Density:** High spatial efficiency for complex management views and data grids; spacious padding for reading, onboarding, and consumer flows.
* **Strict Layering:** Clear spatial separation through surface contrast and elevated overlay levels.

### Anti-Identity (What the Interface Must NOT Become)

* **NOT Skeuomorphic:** No faux textures, leather patterns, or heavy embossed gradients.
* **NOT Flat Monotony:** No borderless, shadowless sheets where buttons and cards blend into background canvases.
* **NOT Saturated Wallpaper:** No bright brand background fills or saturated full-bleed containers.
* **NOT Material Design Copy:** No floating action buttons (FABs), ripple effects, heavy color roles, or Google visual branding.
* **NOT A noisy arcade:** No continuous ambient animations, floating card flutters, or bouncy spring effects.

---

## 5. Design Tokens

### 5.1 Color Tokens

The color architecture is built on a 20-role semantic system. Raw HEX values must never be referenced directly in application components; components must consume semantic tokens exclusively.

#### Complete Semantic Color Token System

| Token | Light Theme | Dark Theme | Functional Role & Intended Usage | Prohibited Usage |
| --- | --- | --- | --- | --- |
| `surface-base` | `#fefefe` | `#0a0a0a` | Application root canvas (Level 0 depth). Main view background. | Card fills, floating dialogs, buttons. |
| `surface-card` | `#f8f8f8` | `#171717` | Resting content containers (Level 1 depth). Cards, panels, modal sheets. | Root application canvas. |
| `surface-muted` | `#f1f1f1` | `#171717` | Recessed structural fills. Form inputs, unselected tab tracks, segmented controls. | Elevated cards, primary action triggers. |
| `border` | `#eeeeee` | `#242424` | Structural containment edges. Input borders, card outlines, quiet dividers. | Active focus rings, high-contrast badges. |
| `foreground` | `#0e0e0e` | `#fefefe` | High-contrast content layer. Headings, main body copy, primary icons. | Large background canvas fills. |
| `foreground-muted` | `#767676` | `#737373` | Secondary supporting layer. Metadata, captions, secondary labels, disabled text. | Primary headings, dense body text. |
| `primary` | `#0a0a0a` | `#fefefe` | Inverted primary action trigger fill. Main CTA buttons, key focal actions. | Standard text, resting card fills. |
| `primary-foreground` | `#fefefe` | `#0a0a0a` | Content overlay on `primary` actions. Text/icons rendered inside primary buttons. | Base canvas body copy. |
| `interactive-pressed` | `#e5e5e5` | `#2e2e2e` | Point-of-contact actuation surface fill. Pressed button/item highlight. | Resting container backgrounds. |
| `interactive-pressed-fg` | `#0a0a0a` | `#e5e5e5` | Foreground content during point-of-contact actuation. Text inside pressed items. | Resting text layers. |
| `accent` | `#365ef8` | `#365ef8` | Primary interactive blue accent. Active tab indicator, radio selection, links. | Large background canvas fills. |
| `accent-alt` | `#7714f4` | `#a78bfa` | Secondary brand purple accent. Badges, special highlights, active brand icons. | System state feedback (success/error). |
| `accent-alt-surface` | `#f3e8ff` | `#7714f4` | Soft brand container background. Feature banners, promo cards paired with white text. | Main application background. |
| `success` | `#0bb980` | `#34d399` | Verified completion indicator. Positive status text, success icons, verified badges. | Standard action links, pending alerts. |
| `success-surface` | `#daf3eb` | `#0f271f` | Soft container background for positive feedback. Verified alert banners, success badges. | Primary action button fills. |
| `destructive` | `#ef4443` | `#f87171` | Critical error & deletion trigger. Delete actions, error messages, critical icons. | Cautionary/pending warnings. |
| `destructive-surface` | `#fcefef` | `#2c1818` | Soft container background for critical alerts. Error banners, validation callouts. | Resting content cards. |
| `warning` | `#d97706` | `#fbbf24` | Cautionary & pending state indicator. Warning text, pending status icons, risk badges. | Permanent error/deletion states. |
| `warning-surface` | `#fef3c7` | `#2a2111` | Soft container background for warnings. Cautionary alerts, pending state banners. | Verified success containers. |
| `focus-ring` | `#365ef8` | `#365ef8` | Mandatory keyboard focus boundary. Visible 2px outline for focused controls. | Resting container outlines. |

#### Color Accessibility & Contrast Audit

All primary pairings fulfill WCAG 2.1 AA standards (minimum 4.5:1 for body text, 3:1 for UI components and large text):

* `foreground` on `surface-base`: Light (19.1:1 - AAA), Dark (19.1:1 - AAA)
* `foreground-muted` on `surface-base`: Light (4.54:1 - AA), Dark (4.61:1 - AA)
* `primary-foreground` on `primary`: Light (19.1:1 - AAA), Dark (19.1:1 - AAA)
* `accent` (`#365ef8`) on `surface-base`: Light (4.32:1 - AA Large/UI), Dark (4.32:1 - AA Large/UI)
* *Requirement:* 14px body text links using `accent` must feature an explicit underline rule.


* `accent-alt` on `surface-base`: Light (`#7714f4` = 8.34:1 - AAA), Dark (`#a78bfa` = 7.12:1 - AAA)
* `primary-foreground` (`#fefefe`) on `accent-alt-surface` (`#7714f4` Dark): 8.34:1 (AAA)

---

### 5.2 Typography Tokens

The typography system uses a single clean font family stack (e.g., Inter, system-ui, sans-serif) paired with monospaced tabular figures for numerical data.

```
┌───────────────────────────────────────────────────────────────────────────┐
│                       TYPOGRAPHIC HIERARCHY SCALE                         │
├─────────────────┬──────────┬────────┬─────────────┬───────────┬───────────┤
│ Role            │ Size     │ Weight │ Line Height │ Letter Sp.│ Usage     │
├─────────────────┼──────────┼────────┼─────────────┼───────────┼───────────┤
│ Display / Hero  │ 32px     │ 700    │ 1.20 (38px) │ -0.02em   │ Hero views│
│ Title Large (H1)│ 24px     │ 600    │ 1.25 (30px) │ -0.01em   │ Page titles│
│ Title Medium(H2)│ 20px     │ 600    │ 1.30 (26px) │ -0.01em   │ Sections  │
│ Title Small (H3)│ 16px     │ 600    │ 1.35 (22px) │ 0.00em    │ Card titles│
│ Body Large      │ 16px     │ 400    │ 1.50 (24px) │ 0.00em    │ Lead text │
│ Body Standard   │ 14px     │ 400    │ 1.50 (21px) │ 0.00em    │ Main body │
│ Body Small      │ 13px     │ 400    │ 1.45 (19px) │ 0.00em    │ Compact data│
│ Label / Control │ 14px     │ 500    │ 1.25 (18px) │ 0.00em    │ Buttons/Inputs│
│ Caption / Meta  │ 12px     │ 400    │ 1.40 (17px) │ 0.01em    │ Timestamps│
│ Monospace / Data│ 13px/14px│ 400/500│ 1.40        │ 0.00em    │ Code/OTP/Nums│
└─────────────────┴──────────┴────────┴─────────────┴───────────┴───────────┘

```

#### Typography Rules

1. **Numeric Tables & OTP Inputs:** Must use monospaced fonts or set `font-variant-numeric: tabular-nums` to prevent layout jitter when numbers change.
2. **Column Bounds:** Narrative body text must be bounded between 45 and 75 characters (max-width ~65ch) per line to eliminate horizontal reading fatigue.
3. **Inverse Line-Height Scaling:** Larger font sizes consume tighter line-height multipliers (Display = 1.20), while small body copy consumes relaxed multipliers (Body = 1.50).

---

### 5.3 Spacing Tokens

Spacing follows an 8pt grid scale with 2pt/4pt sub-steps for micro controls.

```
┌───────────────────────────────────────────────────────────────────────────┐
│                              SPACING SCALE                                │
├───────────────┬───────┬───────────────────────────────────────────────────┤
│ Token Name    │ Value │ Primary Structural Purpose                        │
├───────────────┼───────┼───────────────────────────────────────────────────┤
│ space-3xs     │ 2px   │ Micro offsets, focus ring offsets, badge borders  │
│ space-2xs     │ 4px   │ Tight label gaps, tab track padding, sub-elements │
│ space-xs      │ 8px   │ Button internal vertical padding, icon gaps       │
│ space-sm      │ 12px  │ Input horizontal padding, card header gaps        │
│ space-md      │ 16px  │ Container padding, form field vertical gaps       │
│ space-lg      │ 24px  │ Card internal padding, section margins            │
│ space-xl      │ 32px  │ Dialog internal padding, grid column gaps         │
│ space-2xl     │ 48px  │ Page section separation, major layout blocks      │
│ space-3xl     │ 64px  │ Overview section margins, hero canvas separation  │
└───────────────┴───────┴───────────────────────────────────────────────────┘

```

#### Density Modulation Rules

* **High Density (Workspaces, Data Grids, Admin Toolbars):** Use `space-2xs` for inline gaps, `space-xs` for cell padding, and `space-sm` for container padding.
* **Spacious Density (Consumer Views, Onboarding, Marketing Canvases):** Use `space-sm` for inline gaps, `space-lg` for card padding, and `space-2xl` for section separation.

---

### 5.4 Shape Tokens

Corner rounding is systematically applied based on element size and component role.

```
┌───────────────────────────────────────────────────────────────────────────┐
│                              SHAPE RADIUS SYSTEM                          │
├───────────────┬───────┬───────────────────────────────────────────────────┤
│ Token Name    │ Value │ Primary Applied Controls & Surfaces               │
├───────────────┼───────┼───────────────────────────────────────────────────┤
│ radius-none   │ 0px   │ Full-bleed banners, dividers, table rows          │
│ radius-sm     │ 4px   │ Checkboxes, badges, tooltips, tab trigger items   │
│ radius-md     │ 6px   │ Buttons, form inputs, textareas, select triggers  │
│ radius-lg     │ 8px   │ Content cards, dropdown menus, alert banners      │
│ radius-xl     │ 12px  │ Modal dialogs, slide-over drawers, notification toast│
│ radius-full   │ 9999px│ Radio buttons, switches, avatars, status pills    │
└───────────────┴───────┴───────────────────────────────────────────────────┘

```

#### Shape Rules

* Interactive controls (Buttons, Inputs) must consistently consume `radius-md` (6px).
* Containers (Cards, Dropdowns) consume `radius-lg` (8px), while elevated modals consume `radius-xl` (12px).
* Do not mix arbitrary corner radii (e.g., an 18px rounded button inside a 4px card container).

---

### 5.5 Elevation / Surface Tokens

Hierarchy is established through surface contrast first, subtle borders second, and elevation shadows third.

```
┌───────────────────────────────────────────────────────────────────────────┐
│                           ELEVATION & SURFACE DEPTH                       │
├───────┬───────────────┬───────────────────┬───────────────────────────────┤
│ Level │ Layer Type    │ Surface Token     │ Visual Boundary Treatment     │
├───────┼───────────────┼───────────────────┼───────────────────────────────┤
│ Level 0│ Root Canvas   │ surface-base      │ None (Base application level) │
│ Level 0│ Recessed Field│ surface-muted     │ border (Quiet inset boundary) │
│ Level 1│ Resting Card  │ surface-card      │ border (Quiet border, shadow-none)│
│ Level 2│ Floating UI   │ surface-card      │ border + shadow-md (z-index:20)│
│ Level 3│ Modal Overlay │ surface-card      │ border + shadow-lg (z-index:50)│
└───────┴───────────────┴───────────────────┴───────────────────────────────┘

```

#### Overlay Backdrop Rule

Level 3 Modal Overlays and Drawers must be paired with a semi-transparent dark backdrop overlay (`rgba(0, 0, 0, 0.4)` in Light Mode, `rgba(0, 0, 0, 0.7)` in Dark Mode) to occlude the base canvas and enforce temporal focus.

---

### 5.6 Motion & Interaction Tokens

#### Duration Tokens

* `duration-instant` (`0ms`): Immediate cuts, reduced-motion fallbacks, hard DOM swaps.
* `duration-fast` (`100ms`): Micro feedback: hover highlights, press state actuation, focus rings, check/radio toggles.
* `duration-standard` (`200ms`): Standard UI transitions: dropdown openings, tab switching, accordion expand, alert reveals.
* `duration-emphasized` (`300ms`): Emphasized transforms: modal dialog entries, drawer slide-overs, toast notifications.
* `duration-complex` (`400ms`): Multi-stage layout reorganizations, multi-step wizard view shifts.

#### Easing Tokens

* `ease-standard` (`cubic-bezier(0.2, 0.0, 0.0, 1.0)`): Natural deceleration for standard UI transforms.
* `ease-in` (`cubic-bezier(0.3, 0.0, 1.0, 1.0)`): Acceleration curve for elements exiting off-screen.
* `ease-out` (`cubic-bezier(0.0, 0.0, 0.2, 1.0)`): Deceleration curve for elements entering the canvas.
* `ease-emphasized` (`cubic-bezier(0.2, 0.0, 0.0, 1.0)`): Controlled physical curve for modals and sheets.

---

## 6. LAYOUT & RESPONSIVE DESIGN

### Page Structure & Containers

The page canvas consists of three main structural layers:

1. **Application Shell:** Outer layout framing containing sidebars, persistent header navigation, and utility footers.
2. **Main Canvas:** Root scroll container holding page headers, view tabs, and content sections (`surface-base`).
3. **Content Containers:** Grouped sections, cards, and data panels (`surface-card`).

Max container widths for centered page views:

* **Compact / Form Flow:** `640px`
* **Standard Content / Reading:** `1024px`
* **Wide Data Canvas / Dashboard:** `1280px` or full width with `24px` margins.

### Breakpoints & Adaptive Behavior

Layouts adapt fluidly based on viewport width:

* **Mobile (`<640px`):** Single-column stacked layout. Sidebar collapses into a bottom drawer/sheet. Navigation transforms into bottom bars or hamburger drawers. Primary action triggers span 100% container width.
* **Tablet (`640px - 1024px`):** Multi-column grids collapse to 2 columns. Sidebars collapse into icon-only rails or slide-over sheets.
* **Desktop (`>1024px`):** Full multi-column dashboard layouts. Sidebars expanded. High-density data tables and side panels active.

---

## 7. VISUAL HIERARCHY

Visual hierarchy must be established through coordinated multi-signal reinforcement. Never rely on a single visual property to convey importance.

```
┌───────────────────────────────────────────────────────────────────────────┐
│                    MULTI-SIGNAL HIERARCHY REINFORCEMENT                   │
├───────────────────┼───────────────────────────────────────────────────────┤
│ Hierarchy Level   │ Coordinated Visual Signals Applied                    │
├───────────────────┼───────────────────────────────────────────────────────┤
│ Primary Focus     │ • Title Large (24px, 600 weight)                      │
│                   │ • Primary button fill (high contrast)                 │
│                   │ • Focal placement at top/center of primary canvas     │
│                   │ • Distinct surface card container with border         │
├───────────────────┼───────────────────────────────────────────────────────┤
│ Secondary Context │ • Title Small / Body Standard (14px, 500 weight)      │
│                   │ • Secondary / Outline button fill                     │
│                   │ • Surface-muted inset container                       │
├───────────────────┼───────────────────────────────────────────────────────┤
│ Tertiary / Utility│ • Caption / Metadata (12px, 400 weight)               │
│                   │ • Foreground-muted text color                         │
│                   │ • Ghost / Link variant trigger anchored to perimeter  │
└───────────────────┴───────────────────────────────────────────────────────┘

```

---

## 8. INTERACTION & SYSTEM STATES

### State Matrix & Visual Signals

| State | Visual Mechanism | Token Mapping / Rule |
| --- | --- | --- |
| **Default** | Resting state | Base semantic tokens (`surface-card`, `foreground`). |
| **Hover** | 8% semi-transparent overlay or surface lightness shift | `surface-muted` fill or 8% opacity shift (100ms `ease-standard`). |
| **Focus-Visible** | 2px outline boundary with 2px offset | `focus-ring` (`#365ef8`) outline ring (`:focus-visible` only). |
| **Pressed** | Point-of-contact actuation surface shift | `interactive-pressed` fill, `interactive-pressed-fg` text (100ms). |
| **Selected** | Persistent active selection state | `accent` (`#365ef8`) fill or border indicator. |
| **Active** | Active view / current tab indicator | `accent` underline or `surface-card` active elevated fill. |
| **Disabled** | Visual fade and locked input | `opacity: 0.5`, `pointer-events: none`, `cursor: not-allowed`. |
| **Loading** | Locked pointer, layout preserved, spinner/skeleton | Skeleton pulses using `surface-muted`; CLS must equal 0. |
| **Success** | Verified completion cue | `success` text/icon on `success-surface` container. |
| **Warning** | Cautionary risk / pending status cue | `warning` text/icon on `warning-surface` container. |
| **Error / Destructive** | Critical failure / destructive action cue | `destructive` text/icon on `destructive-surface` container. |
| **Empty State** | Quiet canvas with clear recovery path | Neutral icon, clear heading, concise explanation, primary recovery CTA. |
| **Pending** | Work initiated but unconfirmed | `warning` or `foreground-muted` status badge with clock icon. |
| **Processing** | Active asynchronous operation running | `accent` spinner with active verb copy ("Saving changes..."). |

### System State Transparency Rules

1. **Never Lie About State:** Do not display a success checkmark until the back-end operation returns HTTP 200/ACK.
2. **Preserve Layout Bounds:** Loading states must occupy the exact spatial dimensions of the target content to eliminate Cumulative Layout Shift (CLS = 0).
3. **Multi-Signal Cues:** Pair error/warning colors with explicit icons and actionable copy.

---

## 9. ACCESSIBILITY

1. **Color Contrast:** Body copy must achieve $\ge 4.5:1$ contrast against underlying surfaces. Large headers and UI components must achieve $\ge 3:1$.
2. **Keyboard Focus:** Keyboard focus must display a visible 2px `focus-ring` (`#365ef8`) with 2px offset. Never set `outline: none` without providing an explicit focus style.
3. **Non-Color Indicators:** All status signals (success, warning, error, pending) must combine color with text labels and distinct iconography.
4. **Touch Target Size:** Interactive elements on touch-enabled devices must provide a minimum target area of **44x44px**.
5. **Dynamic Text Scaling:** Layout containers must use fluid auto-heights and flexbox/grid wrapping to accommodate text scaling up to 200% without clipping labels.
6. **Reduced Motion:** When `prefers-reduced-motion: reduce` is detected, spatial translations, sliding drawers, and scaling animations must be replaced with `0ms` instant cuts or `100ms` opacity fades.

---

## 10. COMPONENT GUIDELINES

The following specifications define how `shadcn-vue` primitives must be styled and used.

### Group A: Inputs & Forms

#### 1. Button

* **Purpose:** Primary action trigger for user workflows and state mutations.
* **Hierarchy:** Level 1 (Primary solid fill) to Level 3 (Ghost / Link borderless trigger).
* **Variants:** `primary` (`primary` fill, `primary-foreground` text), `secondary` (`surface-muted` fill, `foreground` text), `outline` (`border` outline, `surface-card` fill), `ghost` (borderless hover highlight), `destructive` (`destructive` text/fill), `link` (`accent` text with underline).
* **States:** Default, Hover (8% opacity shift), Focus-Visible (2px `focus-ring` with 2px offset), Pressed (`interactive-pressed`), Disabled (`opacity: 0.5`, `pointer-events: none`), Loading (icon swapped for Spinner).
* **Typography:** Label level (14px, `font-weight: 500`).
* **Spacing:** Internal padding: 8px vertical, 16px horizontal. Icon gap: 8px.
* **Shape:** `radius-md` (6px).
* **Accessibility:** Minimum target size 44x44px on touch viewports; mandatory `aria-disabled` and `aria-busy` when loading.
* **Anti-Patterns:** Do not place multiple primary buttons inside the same container.

#### 2. Button Group

* **Purpose:** Segmented group of closely related action triggers or view toggles.
* **Hierarchy:** Secondary control group.
* **Visual Treatment:** Joined control buttons where outer edges retain `radius-md` and inner edges consume `radius-none` with 1px `border` dividers.
* **Usage Rules:** Use for 2–4 mutually exclusive view choices or grouped actions.

#### 3. Input & Textarea

* **Purpose:** Single-line and multi-line textual data entry.
* **Visual Treatment:** Inset container with `surface-muted` background, `border` edge, and `foreground` text.
* **States:** Default, Hover, Focused (`focus-ring` active, `border` shifts to `accent`), Error (`border` shifts to `destructive`), Disabled (`opacity: 0.5`).
* **Typography:** Body Standard (14px). Monospaced for technical inputs.
* **Spacing:** Padding: 8px vertical, 12px horizontal. Textarea min-height: 80px.
* **Shape:** `radius-md` (6px).
* **Anti-Patterns:** Do not use `radius-full` (pill shape) for text inputs or textareas.

#### 4. Input Group & Field

* **Purpose:** Structural wrapper attaching inline prefix/suffix icons, currency symbols, or action buttons to inputs.
* **Visual Treatment:** Seamless container joining addons to inputs with continuous `border`.

#### 5. Label

* **Purpose:** Text label bound to form controls.
* **Visual Treatment:** Label level (14px, `font-weight: 500`, `foreground`).
* **Usage Rules:** Must be linked via `for`/`id` attribute to its target input. Never use placeholders as labels.

#### 6. Checkbox & Radio Group

* **Purpose:** Multi-selection options (Checkbox) and mutually exclusive single selection (Radio).
* **Visual Treatment:** Checkbox consumes `radius-sm` (4px); Radio consumes `radius-full` (9999px). Active state fills with `accent` (`#365ef8`).
* **Target Size:** Control size 20x20px, padded to 44x44px touch target. Label gap: 8px.

#### 7. Switch

* **Purpose:** Immediate binary setting toggle.
* **Visual Treatment:** Track: 36x20px (`radius-full`). Thumb: 16x16px (`radius-full`, white). Active track consumes `accent` (`#365ef8`).
* **Usage Rules:** Takes effect immediately upon actuation without requiring form submit button clicks.

#### 8. Select & Native Select

* **Purpose:** Single option selection from a collapsible list.
* **Desktop:** Custom floating popover list (`surface-card`, `radius-lg`, `shadow-md`).
* **Mobile:** Automatically fallback to `Native Select` to leverage native device picker wheels.

#### 9. Number Field & Input OTP

* **Purpose:** Numerical value entry and single-digit verification code input.
* **Visual Treatment:** Tabular numbers (`font-variant-numeric: tabular-nums`). OTP input renders discrete 40x48px cell boxes with `radius-md`.

---

### Group B: Layout & Surfaces

#### 10. Card & Item

* **Purpose:** Resting content panel and structured list item grouping.
* **Visual Treatment:** `surface-card` fill, `border` outline, `radius-lg` (8px). Level 1 depth (`shadow-none`). Padding: 24px (`space-lg`).

#### 11. Separator

* **Purpose:** Quiet visual divider between major layout sections.
* **Visual Treatment:** 1px thickness consuming `border` token. Use whitespace preferred over hard lines.

#### 12. Sidebar, Drawer & Dialog

* **Purpose:** Structural navigation framing (Sidebar), slide-over panels (Drawer), and high-priority modal popups (Dialog).
* **Visual Treatment:** Dialog consumes `surface-card`, `radius-xl` (12px), `shadow-lg` (Level 3 depth), paired with a 40% opacity dark backdrop overlay.

---

### Group C: Navigation

#### 13. Navigation Menu & Dropdown Menu

* **Purpose:** Application header navigation trees and contextual action menus.
* **Visual Treatment:** Floating popover panel consuming `surface-card`, `radius-lg` (8px), `shadow-md` (Level 2 depth). Item hover consumes `interactive-pressed`.

#### 14. Menubar & Breadcrumb

* **Purpose:** Desktop window-level menu triggers and hierarchical location paths.
* **Visual Treatment:** Breadcrumbs use Caption / Body Small typography separated by `/` or `>` quiet chevron icons.

#### 15. Tabs

* **Purpose:** Switching between parallel content views within the same page context.
* **Variants:** Recessed (`surface-muted` track, active tab `surface-card` with `shadow-sm`) or Underline (minimal text tabs with `accent` bottom border rule).

#### 16. Pagination & Stepper

* **Purpose:** Navigating multi-page tables and tracking linear multi-step wizard progress.
* **Visual Treatment:** Stepper node consumes `radius-full` (24x24px). Active step consumes `accent` fill; completed step consumes `success` fill with checkmark icon.

---

### Group D: Feedback & Status

#### 17. Alert & Alert Dialog

* **Purpose:** Inline feedback callout banners (Alert) and critical confirmation modals (Alert Dialog).
* **Variants:**
* `info`: `surface-card` fill with `accent` icon.
* `success`: `success-surface` fill, `success` text/icon.
* `warning`: `warning-surface` fill, `warning` text/icon.
* `destructive`: `destructive-surface` fill, `destructive` text/icon.



#### 18. Badge & Avatar

* **Purpose:** Entity status tag (Badge) and user profile thumbnail (Avatar).
* **Visual Treatment:** Badge consumes Caption level text (12px, 500 weight), `radius-sm` (4px) or Status Pill (`radius-full`). Avatar consumes `radius-full` with fallback initials.

#### 19. Progress, Skeleton & Spinner

* **Purpose:** Asynchronous loading indicators.
* **Visual Treatment:** Skeleton pulses using `surface-muted` fill. Spinner renders 16x16px or 20x20px rotating accent ring.

#### 20. Tooltip & Popover

* **Purpose:** Brief hover metadata callout (Tooltip) and rich interactive popup container (Popover).
* **Visual Treatment:** Tooltip consumes `primary` fill with `primary-foreground` text (`radius-sm`, 12px text). Popover consumes Level 2 floating surface rules.

#### 21. Sonner / Toast

* **Purpose:** Transient system feedback notification appearing at screen perimeter.
* **Visual Treatment:** Floating notification card (`surface-card`, `border`, `shadow-lg`, `radius-xl`). Auto-dismisses in 4000ms. Must include explicit dismiss action button.

---

### Group E: Data Display & Specialized

#### 22. Table & Data Table

* **Purpose:** High-density structured record display.
* **Visual Treatment:** Header row consumes `surface-muted` background with Label Bold typography (13px/14px). Cells consume tight padding (8px–12px). Alternating row highlights prohibited; hover row consumes 4% surface shift.

#### 23. Date Picker & Command

* **Purpose:** Calendar date selection popover and quick command search palette (`Cmd+K`).
* **Visual Treatment:** Command palette renders centered Level 3 modal sheet with continuous keyboard search selection.

#### 24. Accordion & Attachment

* **Purpose:** Vertically stacked collapsible content panels and file uploading/attachment cards.
* **Visual Treatment:** Accordion trigger reveals content via 200ms `ease-standard` expansion transition. Attachment card displays file preview, file size metadata, upload progress bar, and removal trigger.

---

## 11. COMPOSITION PATTERNS

### Page Headers

* **Layout:** Flex row with Title Large (24px H1) on the left, supporting metadata underneath, and primary/secondary action triggers aligned to the right.
* **Responsive:** Stack action buttons full-width below the title on mobile screens.

### Form Layouts

* **Layout:** Single-column vertical flow with 16px (`space-md`) gap between fields. Group related fields into Card sections (`space-lg` internal padding). Primary submit action placed at bottom left or right of the form panel.

### Dashboards & Management Grids

* **Layout:** Top summary KPI card grid (3–4 cards in a row), followed by main canvas containing filter bars and primary Data Table container.

### Empty States

* **Layout:** Centered content stack inside card container. Includes 48x48px quiet icon (`foreground-muted`), Title Medium header, Body Standard explanation copy (max 40 words), and a single primary CTA button.

---

## 12. CONTENT & INFORMATION HIERARCHY

1. **Active Verb Labels:** Action triggers must begin with clear verbs ("Create account", "Save changes", "Export report"). Avoid generic text like "OK" or "Submit".
2. **Error Copy Structure:** Error messages must contain three clear parts:
* **What happened:** "Password export failed."
* **Why it happened:** "Network connection was interrupted."
* **How to recover:** "Check your connection and try again."


3. **Metadata Formatting:** Render timestamps, file sizes, and ID strings using `foreground-muted` Caption level copy (12px).

---

## 13. LIGHT & DARK THEMING

```
┌───────────────────────────────────────────────────────────────────────────┐
│                      THEME MAPPING RELATIONSHIPS                          │
├───────────────────┬───────────────────┬───────────────────┬───────────────┤
│ Semantic Token    │ Light Value       │ Dark Value        │ Pattern Type  │
├───────────────────┼───────────────────┼───────────────────┼───────────────┤
│ surface-base      │ #fefefe           │ #0a0a0a           │ Inverted      │
│ surface-card      │ #f8f8f8           │ #171717           │ Inverted      │
│ border            │ #eeeeee           │ #242424           │ Inverted      │
│ foreground        │ #0e0e0e           │ #fefefe           │ Inverted      │
│ foreground-muted  │ #767676           │ #737373           │ Inverted      │
│ primary           │ #0a0a0a           │ #fefefe           │ Inverted      │
│ primary-foreground│ #fefefe           │ #0a0a0a           │ Inverted      │
│ accent            │ #365ef8           │ #365ef8           │ Constant      │
│ accent-alt        │ #7714f4           │ #a78bfa           │ Shifted (AA)  │
│ accent-alt-surface│ #f3e8ff           │ #7714f4           │ Role Shift    │
└───────────────────┴───────────────────┴───────────────────┴───────────────┘

```

Dark mode is an inverted luminance model, not a color transformation. High-glare full-white text on pitch-black canvas is avoided by using `#fefefe` on `#0a0a0a` with muted borders (`#242424`).

---

## 14. ANTI-PATTERNS

Developers and AI coding agents must **NEVER**:

1. **Use arbitrary raw colors:** Using raw HEX, RGB, or HSL values in component files (e.g., `#1e293b`, `bg-[#121212]`).
2. **Use arbitrary spacing:** Applying custom pixel padding or margins outside the 8pt spacing scale (e.g., `padding: 13px`).
3. **Use arbitrary typography sizes:** Defining custom font sizes outside the typographic scale (e.g., `font-size: 15px`).
4. **Use arbitrary corner radii:** Mixing random rounded corners (e.g., `border-radius: 17px`).
5. **Apply excessive drop shadows:** Adding ambient shadows to resting flat cards.
6. **Use hard decorative dividers:** Drawing heavy border lines between every list item when whitespace is sufficient.
7. **Create component-specific color tokens:** Inventing custom color variables for single components (e.g., `--my-button-color`).
8. **Place multiple primary buttons in a container:** Including two primary solid action triggers in the same view.
9. **Rely solely on color for state:** Indicating success or error through color changes without text labels or icons.
10. **Hide focus rings:** Setting `outline: none` or `ring-0` on keyboard-navigable controls without replacement.
11. **Blink or loop ambient animations:** Adding continuous spinning, hovering card flutters, or bouncy spring effects.
12. **Prematurely display success states:** Showing confirmed checkmarks before server validation completes.
13. **Blindly copy Material Design:** Adding floating action buttons (FABs), ripple tap animations, or Google material styling.
14. **Introduce a second design system:** Importing secondary UI component libraries or Tailwind presets.
15. **Cause layout shift during loading:** Allowing card containers to collapse while loading data (CLS > 0).

---

## 15. DECISION-MAKING RULES FOR FUTURE DEVELOPERS

When resolving design ambiguity, follow these strict rules:

1. **Reuse an existing semantic token before inventing a role.**
2. **Reuse an existing `shadcn-vue` primitive before writing a custom component.**
3. **Prefer layout composition over creating component variants.**
4. **Prefer semantic visual consistency over visual novelty.**
5. **Prefer the established 8pt spacing scale over custom padding.**
6. **Prefer the defined typography hierarchy over custom font scaling.**
7. **Prefer multi-signal redundancy (color + icon + text) over color alone.**
8. **Preserve WCAG AA accessibility requirements even if visual styling changes.**
9. **Do not introduce Material Design patterns simply because they exist in MD3.**
10. **When uncertain, preserve the quiet, structured baseline design system.**

---

## 16. AI IMPLEMENTATION CONTRACT

This document serves as an explicit contract for AI coding agents generating or modifying UI code.

### Mandatory Directives for AI Agents

* **Read Before Modifying:** The AI agent must parse `design.md` before generating or refactoring UI components.
* **Strict Token Compliance:** The AI agent must consume semantic tokens exclusively (`surface-base`, `primary`, `accent`, `border`, `destructive`).
* **Primitive Reuse:** The AI agent must construct interfaces using established `shadcn-vue` primitives.
* **No Arbitrary Classes:** The AI agent must not generate inline styles or arbitrary Tailwind values (e.g., `p-[11px]`, `text-[15px]`, `bg-[#334155]`).
* **Preserve State Logic:** The AI agent must implement default, hover, focus-visible, pressed, disabled, and loading states for every interactive component.
* **Preserve Accessibility:** The AI agent must output semantic HTML tags, ARIA attributes (`aria-expanded`, `aria-invalid`, `aria-busy`), and explicit keyboard focus indicators.
* **Ask for Clarification:** If a complex UI requirement is not defined by this system, the AI agent must ask the user for guidance rather than inventing a new design direction.

---

## 17. DESIGN SYSTEM COMPLETENESS CHECK

* [x] Design philosophy ("The Adaptive Canvas" & 5 Experiential Pillars)
* [x] All 16 finalized design principles
* [x] Complete 20-role semantic color token system
* [x] Light theme palette & Dark theme palette
* [x] WCAG 2.1 AA accessibility contrast validation audit
* [x] Complete typography token system & reading rules
* [x] 8pt spacing token scale & density modulation rules
* [x] Corner radius shape tokens & component mapping
* [x] Elevation & surface depth hierarchy (Levels 0–3)
* [x] Motion tokens (durations, easings, interaction states)
* [x] Interaction states (Hover, Focus-Visible, Pressed, Disabled, Loading)
* [x] System state transparency rules
* [x] Accessibility requirements (Contrast, Target bounds, Reduced motion)
* [x] Layout and responsive breakpoint rules
* [x] Visual hierarchy multi-signal guidelines
* [x] `shadcn-vue` primitive adaptation mappings for all 24 component groups
* [x] Composition patterns (Headers, Forms, Dashboards, Empty states)
* [x] Content & information hierarchy copy rules
* [x] Light & Dark theme inverted/constant token relationship mapping
* [x] Comprehensive anti-patterns prohibition list
* [x] Decision-making rules for future developers
* [x] AI implementation contract