# Design System Documentation: The Cognitive Sanctuary

## 1. Overview & Creative North Star
This design system is anchored by a Creative North Star we call **"The Cognitive Sanctuary."** 

In an era of high-velocity interfaces and dark patterns, this system serves as a digital deep breath. For a decision-making app, our goal is to eliminate choice fatigue by reducing visual noise. We break the "standard app" template by moving away from rigid grids and cluttered dashboards, opting instead for a high-end editorial layout. By utilizing intentional asymmetry, expansive whitespace (using `spacing-16` and `spacing-20`), and a sophisticated tonal palette, we guide the user to focus on exactly one thought at a time. The experience should feel less like a utility and more like a curated gallery of one's own thoughts.

---

## 2. Colors: Tonal Architecture
The palette is a sophisticated arrangement of sage greens and muted minerals, designed to lower the heart rate. 

### The "No-Line" Rule
**Strict Mandate:** Designers are prohibited from using 1px solid borders for sectioning or containment. Structural boundaries must be defined solely through background color shifts. Use `surface_container_low` against a `surface` background to define areas. This creates a softer, more organic transition that feels "built" rather than "drawn."

### Surface Hierarchy & Nesting
Treat the UI as a series of physical layers—like stacked sheets of fine, heavy-stock paper. 
- **Base Layer:** `surface` (#f8faf9).
- **Secondary Content:** `surface_container_low` (#f1f4f3).
- **Interactive Elements:** `surface_container_highest` (#dde4e3).
By nesting these tiers, you create depth without visual clutter. An inner container should always be at least one tier higher or lower than its parent to maintain clarity.

### The "Glass & Gradient" Rule
To elevate the experience beyond flat design, use Glassmorphism for floating elements (e.g., a "Next" button fixed to the bottom). Apply a background blur to a semi-transparent `surface_container_lowest` (#ffffff at 85% opacity). 
- **Signature Textures:** For primary CTAs, apply a subtle linear gradient from `primary` (#4c645a) to `primary_dim` (#40584e) at a 135-degree angle. This adds "soul" and a tactile, premium weight to the interaction.

---

## 3. Typography: Editorial Clarity
We use two typefaces: **Manrope** for the narrative and **Inter** for the mechanics.

- **The Voice (Manrope):** Use `display-md` or `headline-lg` for primary questions. The geometric nature of Manrope feels modern yet authoritative. Headlines should have a negative letter-spacing of `-0.02em` to feel like high-end print.
- **The Guide (Inter):** Use Inter for `label-md` and `label-sm`. It provides a technical, neutral contrast to the warmth of Manrope, signaling "utility" for functional data.
- **Hierarchy as Identity:** Use extreme scale shifts. A `display-md` question paired with a `body-lg` description creates an intentional, breathable hierarchy that respects the user's intelligence.

---

## 4. Elevation & Depth: Tonal Layering
Traditional drop shadows are too "digital" for this system. We convey hierarchy through environmental light.

- **The Layering Principle:** Depth is achieved by "stacking." For example, place a `surface_container_lowest` card on a `surface_container_low` section. The subtle shift in hex code provides enough contrast for the human eye without creating a hard edge.
- **Ambient Shadows:** When a floating effect is mandatory (e.g., a decision modal), use an ultra-diffused shadow.
    - **Blur:** 40px - 60px.
    - **Color:** `on_surface` (#2d3433) at 4% to 6% opacity.
    - **Offset:** Y: 8px.
- **The "Ghost Border" Fallback:** If accessibility requires a container edge, use a "Ghost Border." This is the `outline_variant` token (#acb3b2) set to 15% opacity. Never use 100% opaque borders.

---

## 5. Components: Intentional Primitives

### Buttons
- **Primary ("Next"):** Use `primary` background with `on_primary` text. Shape: `rounded-full`. Padding: `spacing-4` vertical, `spacing-8` horizontal. Apply the signature gradient for depth.
- **Secondary:** Use `secondary_container` with `on_secondary_container` text. Shape: `rounded-xl`. 
- **Tertiary:** No background. Use `primary` text weight with an `on_surface_variant` icon.

### Input Fields
- **The Editorial Input:** Large-scale fields using `surface_container` backgrounds and `rounded-lg`. 
- **State:** Active states should transition the background to `surface_container_high` and use a "Ghost Border" of `primary` at 40% opacity. 
- **Interaction:** Labels should use `label-md` in `on_surface_variant` and always remain visible to reduce cognitive load.

### Progress Indicators
- **Subtle Momentum:** Forgo the "loading bar." Use a series of soft-edged `rounded-full` dots. Active state: `primary`. Inactive state: `surface_container_highest`. Use `spacing-1.5` for the gap between dots.

### Cards & Lists
- **Rule of No Dividers:** Forbid the use of 1px lines between list items. Use `spacing-4` of vertical whitespace to separate content. For grouped content, use a `surface_container_low` background with `rounded-xl` corners to cluster items naturally.

### Decision-Specific Components
- **Weighted Selection Chips:** Instead of standard radio buttons, use large cards for options. When selected, the background shifts from `surface_container` to `primary_container`, and the text shifts to `on_primary_container`.

---

## 6. Do's and Don'ts

### Do
- **Do** use `spacing-16` (5.5rem) as a standard margin for top-level headlines to create a "Gallery" feel.
- **Do** use `surface_bright` to highlight the most important action on a screen.
- **Do** lean into asymmetry; align text to the left but place the "Next" button in a floating, bottom-right glass container.
- **Do** ensure all interactive targets are at least 48px in height.

### Don't
- **Don't** use pure black (#000000) for text. Always use `on_surface` to keep the tone soft.
- **Don't** use standard Material or iOS transition animations. Use slow, ease-in-out transitions (300ms-500ms) to maintain the "calm" atmosphere.
- **Don't** crowd the screen. If a question has more than four options, use a scrollable `surface_container` rather than shrinking the text.
- **Don't** use 100% opacity for `outline` tokens. Always soften the stroke.