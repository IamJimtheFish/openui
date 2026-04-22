---
name: landing-page-design
description: Use this skill when the task is to create a landing page, homepage, marketing page, hero page, design concept page, or multiple landing-page variants. First ensure repo-root AGENTS.md contains the landing-page workflow guidance, then create the repo-root design.md file with fully resolved inputs and a filled version of the master generation prompt for each variant, then implement the page or pages from design.md. Do not use this skill for unrelated coding tasks.
---

# Purpose

This skill converts a user request for a landing page into:
1. repo-root workflow guidance in `AGENTS.md` when the repository is missing it
2. a required planning artifact at `/design.md`
3. one or more implemented page outputs that follow `/design.md` exactly

# Mandatory workflow

## Phase 0 — Ensure repo guidance

Before resolving variants or writing `/design.md`, ensure the repository has durable guidance for this workflow.

Determine the repository root:
- If inside a git repository, use the output of `git rev-parse --show-toplevel`.
- Otherwise, use the current workspace root.

Then inspect `<repo-root>/AGENTS.md`.

Rules:
- If `<repo-root>/AGENTS.md` does not exist, create it using the "Required AGENTS.md content" below.
- If `<repo-root>/AGENTS.md` exists and already contains equivalent landing-page workflow guidance, leave it unchanged.
- If `<repo-root>/AGENTS.md` exists but does not contain equivalent landing-page workflow guidance, append only the marked landing-page section from the content below.
- Preserve all existing user or repository instructions. Do not replace, reorder, or remove unrelated `AGENTS.md` content.
- Do not ask the user before creating or appending this guidance. This setup is part of the skill workflow.
- Complete this phase before creating `/design.md`.

Required `AGENTS.md` content for a new file:

```markdown
# AGENTS.md

<!-- landing-page-design-plugin:start -->
## Mandatory landing-page workflow

When a task asks for any of the following, use the `landing-page-design` skill before editing implementation files:
- landing page
- homepage
- marketing page
- hero page
- design concept page
- multiple landing-page variants
- high-concept page generation

## Required process

1. Before generating page code, create or replace `/design.md` at the repository root.
2. `design.md` is mandatory and is the source of truth for implementation.
3. Never leave unresolved placeholders such as `[Topic]` or `[Offer]` inside `design.md`.
4. If the user omitted inputs, resolve them first and write concrete values into `design.md`.
5. If the user explicitly fixed an input, preserve it.
6. If the user asked for multiple variants:
   - create one section per variant in `design.md`
   - resolve inputs independently for each variant
   - do not copy one variant's input set into another
   - a variant is invalid if it differs only by palette, copy polish, spacing, or superficial decoration
   - each variant must represent a materially different concept direction
7. After `design.md` is written, implement the page variants one by one in the same order they appear in `design.md`.
8. Do not invent proof assets, fake metrics, fake testimonials, fake logos, or fake screenshots.
9. Keep support highlights in one lower support cluster only.
10. Do not use cardified hero layouts, floating sub-surfaces, or generic SaaS dashboard patterns unless the topic explicitly requires that artifact.

## Implementation policy

- For a single HTML deliverable, prefer `index.html`.
- For multiple HTML variants, prefer:
  - `variants/variant-01/index.html`
  - `variants/variant-02/index.html`
  - `variants/variant-03/index.html`
- For a single React deliverable, prefer one component file in the existing project structure.
- For multiple React variants, create one component per variant with clear naming.

Do not start implementation until `design.md` is complete.
<!-- landing-page-design-plugin:end -->
```

When appending to an existing `AGENTS.md`, append only the marked section from `<!-- landing-page-design-plugin:start -->` through `<!-- landing-page-design-plugin:end -->`, separated from existing content by one blank line.

## Phase 1 — Determine variant count

Infer the number of required variants from the user request.

Rules:
- If the user asks for one page, create one variant.
- If the user asks for multiple variants, create exactly that many variants.
- If the user asks for "a few" or similarly vague plurality, default to 3 variants.

## Phase 2 — Resolve inputs for each variant

For each variant, resolve all of these inputs before implementation:

- Topic
- Offer
- Audience
- Primary user action
- Deliverable
- Style direction
- Tonal key
- Icon policy
- Proof assets
- Motion intensity

Rules:
- Preserve any input explicitly specified by the user.
- Infer any missing input.
- Re-resolve every input independently for each variant.
- Do not reuse the same inferred combination across variants.
- Variants must differ conceptually, not just cosmetically.
- If the overall topic is fixed by the user, create different topic angles or framings within that topic instead of changing the topic entirely.
- Never invent proof assets. If none are provided and none are credibly available from the prompt, write `none`.
- If motion intensity is not specified by the user, use `Rich but controlled`.

## Phase 3 — Create `/design.md`

Before generating any page code, create or replace `/design.md`.

`/design.md` must contain:

- one top-level title
- one section per variant in order
- a resolved input list for each variant
- the fully filled master prompt for each variant
- the intended output file path for each variant

Use this structure exactly:

# Landing Page Design Plan

## Variant 1

### Resolved inputs
- Topic: ...
- Offer: ...
- Audience: ...
- Primary user action: ...
- Deliverable: ...
- Style direction: ...
- Tonal key: ...
- Icon policy: ...
- Proof assets: ...
- Motion intensity: ...

### Filled generation prompt
[paste the full master prompt with all placeholders replaced by concrete values for this variant]

### Output target
- Path: ...

Repeat for each additional variant.

Validation rules:
- No square-bracket placeholders may remain.
- No variant may be a near-duplicate of another.
- Differences must affect concept, audience framing, offer framing, interaction model, visual logic, or composition strategy — not only color.

## Phase 4 — Implement

After `/design.md` is complete:
- read Variant 1
- implement Variant 1
- then proceed to Variant 2
- then proceed to Variant 3, and so on

Rules:
- Follow `/design.md` exactly
- Do not silently drift from the resolved inputs
- Do not merge variants together
- Keep one dominant hero
- Keep one coherent visual world per variant
- Keep support highlights in one lower cluster only
- Do not introduce fake proof
- Do not introduce generic SaaS UI patterns unless the variant explicitly calls for them

# Master prompt to render into design.md

Create one high-concept landing page for [Topic].

## Inputs
- Topic: [Topic].
- Offer: [What is being offered. If missing, infer one plausible offer and stay consistent.]
- Audience: [Who it is for. If missing, infer one clear primary audience.]
- Primary user action: [What is the single most important thing the visitor should do next? Examples: explore, sign up, book, join, apply, RSVP, compare, configure, browse, watch, listen, read, download, buy, request access, contact, start demo, view schedule, view collection, submit.]
- Deliverable: [Single-file HTML with embedded CSS and JS | React component. If missing, choose the most appropriate format for the concept and return only that.]
- Style direction: [Optional. Choose one dominant direction and use it consistently. Representative anchors: Swiss, Editorial, Organic, Airy, Playful, Glitch, Bauhaus, Industrial, Terminal, Synthwave. You may choose another single direction if it fits the topic better.]
- Tonal key: [Optional. Light / Mid / Dark / Topic-derived. If missing, choose the strongest topic-native tonal key.]
- Icon policy: [Optional. None / Minimal / Expressive / Topic-native / Auto-if-useful. If missing, use icons only when they improve scanability, recognition, or support clarity.]
- Proof assets: [Optional. Real numbers, testimonials, screenshots, product surfaces, physical artifacts, references, or none.]
- Motion intensity: [Optional. Minimal / Ambient / Rich but controlled. Rich but controlled by default.]

## Objective
Design one premium, memorable landing page concept with a dominant hero and one coherent visual world derived from the topic itself.
The page should feel specific, intentional, and conversion-minded, not like a generic startup or SaaS template.

Choose the strongest clear solution.
Do not collapse the concept into a simpler generic pattern just to make execution easier.

## Effort and resolution policy
- Do not infer that the task is simple merely because the deliverable is a single file, a direct chat response, or a self-contained component.
- Output directness is not a signal to reduce conceptual ambition, visual specificity, interaction richness, implementation care, or production quality.
- Even when the final deliverable is concise, resolve the concept fully rather than defaulting to the quickest acceptable structure.
- Treat single-file execution as a packaging constraint, not a creative constraint.
- Prefer the strongest fully resolved concept that fits the constraints, not the fastest concept that merely fits in one file.

## Ambition and scope discipline
- Do not treat missing implementation detail as permission to reduce conceptual ambition, visual specificity, or interaction richness when the concept clearly benefits from them.
- Prefer the simplest structure that preserves the strongest concept, not the simplest structure that merely satisfies the rules.
- Do not add extra content sections unless they are structurally necessary.
- If conceptual depth is needed, absorb it into the hero, proof gesture, support highlight copy, CTA behavior, or background logic rather than creating a new section by default.
- When choosing between restraint and richness, keep the stronger topic-native idea and remove only what weakens clarity, hierarchy, or credibility.
- Implementation simplicity is not a goal by itself. Concept strength, coherence, and usability take priority.

## Internal concept choice
Before composing, decide internally:
- one dominant hero archetype: centered / asymmetrical / immersive
- one dominant proof mode: none / embedded gesture / single artifact
- one palette driver derived from the topic
- one tonal key: light / mid / dark / topic-derived
- one motion role: minimal / ambient / interactive
- one icon approach: none / minimal / expressive / topic-native
- optionally one secondary accent only if it strengthens the dominant direction without creating a second visual world

The secondary accent may adjust rhythm, detail, or interaction, but must not introduce a second layout model, second proof system, or second style direction.
Do not output this planning.

## Non-negotiables
- Use a strong hero-first composition.
- Headline: 3–12 words, max 3 lines.
- Supporting copy: 1–2 short sentences, concise, specific.
- CTAs: exactly 1 primary and 1 secondary.
- CTA labels must be specific to the offer and action, not generic.
- Supporting highlights: shown only in a single lower support cluster beneath the hero.
- Keep the hero dominant, focused, readable, and uncluttered.
- Proof is optional. Use it only if it clearly strengthens the concept.
- If no real proof assets are provided, do not invent metrics, testimonials, customer logos, screenshots, or fake UI proof.
- CTA behavior may be simple or richer, but it should fit the offer; do not default to generic anchor-link behavior if a more specific interaction model would strengthen the concept.

## Composition
- A centered hero is allowed, not required.
- Choose the clearest structure for the topic; do not default to left-text / right-visual or automatic two-column marketing layouts.
- The hero may be a fully integrated composition rather than a separate object or framed block.
- The hero does not need to become a panel, dashboard, device mockup, rounded card, or floating showcase unless the topic genuinely demands that artifact.
- Build hierarchy through scale, contrast, spacing, alignment, overlap, rhythm, and composition before using frames, dividers, or containers.
- Keep supporting content clearly subordinate to the hero.
- Do not interpret structural restraint as a reason to flatten the concept into a generic or minimal default.

## Visual system
- Build one coherent visual world derived from the topic itself.
- Treat style as design logic, not decorative skin. It should shape typography, spacing, contrast, geometry, motion, and proof language.
- Derive palette character, accents, contrast behavior, motifs, materials, and shape language from the topic.
- Even restrained palettes must feel specific and intentional, not generic premium-neutral.
- The background must actively contribute mood, depth, and topic logic.
- If the topic suggests a real system language, structural logic, physical behavior, or interface grammar, show that logic directly instead of using generic abstract-tech decoration.
- Treat headline typography as an active part of the visual system, not as neutral text.
- The headline may use topic-derived color, selective color emphasis, multi-tone treatment, or gradient accents when they strengthen the concept and remain readable.
- Do not default the headline to white, near-white, black, or neutral text unless that is clearly the strongest topic-native choice.
- One or two key words may receive differentiated treatment through color, gradient, outline, texture, contrast shift, or other topic-native emphasis, as long as hierarchy stays clear.

## Background and tonal diversity
- Premium, high-concept, and atmospheric design may be expressed through light, mid-tone, or dark visual worlds; do not default to dark.
- Choose the tonal key from the topic, offer, audience, and style direction rather than from default cinematic or tech aesthetics.
- When a light or bright world is stronger, use it confidently.
- Contrast may come from hue, saturation, temperature, texture, scale, spacing, or density, not only from darkness.

## Proof and concept expression
- Prefer the minimum visual evidence needed to make the idea feel specific, credible, and native to the topic.
- If the concept is strongest with typography, atmosphere, and one precise gesture, do that.
- If a stronger proof artifact is justified, use one legible, unified artifact rather than multiple fragmented panels.
- Proof may take the form of a signal, trace, contour, command line, path, specimen, structural mark, scene fragment, or other topic-native evidence.
- Typography itself may carry part of the concept or proof.
- When appropriate, use one precise typographic gesture—such as selective word emphasis, chromatic offset, gradient emphasis, distortion, signal breakup, or structural interruption—to make the concept feel more specific and alive.
- Prefer one strong typographic intervention over many scattered decorative effects.
- Avoid decorative pseudo-proof.
- Avoid turning simple ideas into framed showcases, dashboard fragments, floating panels, softened slabs, or generic marketing geometry.

## Icons and symbolic language
- Icons are optional.
- Use icons only when they improve scanability, recognition, navigation, proof clarity, or support-cluster legibility.
- Prefer topic-native icon logic over generic startup glyphs.
- Keep icon style consistent in stroke weight, geometry, corner logic, and detail level.
- Use icons primarily in the lower support cluster or other clearly secondary roles unless a single topic-native symbol is central to the concept.
- Do not let icons compete with the hero headline, proof artifact, or CTA hierarchy.
- Avoid decorative icon spam, mismatched icon packs, emoji-like symbols, or generic feature-list pictograms.
- If the concept is stronger without icons, omit them.

## Support cluster
- Show supporting highlights only once, in a single lower cluster beneath the hero.
- Each highlight should be short, fast to scan, and clearly secondary to the hero.
- Supporting highlights may use concise icons or symbolic marks when they improve recognition and remain visually subordinate.
- Card-like grouping is allowed only inside this lower support cluster.
- These support modules may use at most one light surface treatment, such as a subtle stroke, tonal fill, or very soft shadow.
- Support modules must remain uniform, non-nested, and visually subordinate.
- Do not use card-like structures in the hero, proof, CTA area, or as nested containers anywhere else on the page.

## Motion
- Motion is optional.
- Use motion only when it supports hierarchy, continuity, feedback, or atmosphere.
- Default motion role is ambient unless the inputs justify a stronger intensity.
- Motion may also live inside typography when it fits the topic and style direction.
- A single key word or short phrase may use subtle text-based motion such as glitch, flicker, jitter, scanline shift, chromatic split, text scramble, pulse, or reveal if it strengthens the concept.
- Prefer one focal animated word or accent treatment rather than animating the entire headline continuously.
- Keep typographic motion controlled, readable, and subordinate to clarity.
- Do not let motion delay access to the headline, copy, or CTAs.
- Keep interaction-critical motion brief, clear, and subtle.
- Avoid scrolljacking, attention-hijacking motion, and ornamental animation loops.
- Respect reduced-motion preferences.

## Accessibility and readability
- Preserve strong readability and clear hierarchy at all viewport sizes.
- Maintain sufficient contrast between text and background.
- Do not place essential text over busy imagery unless readability remains strong.
- Avoid cramped spacing, visual collisions, and weak focal hierarchy.
- If the deliverable is code, use semantic HTML structure, visible focus states, keyboard-friendly interactions, and reduced-motion handling.

## Anti-drift rules
- Do not drift into bland corporate SaaS styling.
- Do not default to generic dashboard aesthetics, feature-grid thinking, or boxed-section composition.
- Do not use disconnected motifs, random color choices, or interchangeable abstract-tech shapes.
- Do not use card-within-card composition, nested surfaces, fake proof, or stock-looking UI.
- Do not let the page feel template-like, compartmentalized, or overly modular.

## Output
Return only the final [Deliverable].
Do not mistake concise delivery for permission to produce a reduced or under-resolved concept.

If the deliverable is code:
- Output a complete production-ready file or component.
- Keep dependencies minimal unless explicitly requested.
- Make it responsive.
- Keep support highlights in one lower support cluster only.

If the deliverable is a visual design brief:
- Include: concept thesis, hero composition, palette logic, tonal-key logic, type direction, proof logic, icon logic, motion behavior, support cluster contents, and CTA copy.

## Final self-check
Before returning, verify that the result keeps:
- one dominant hero
- one coherent visual world
- no invented proof
- no cardification outside the lower support cluster
- no generic SaaS drift
- no unnecessary simplification justified only by ease of execution
- no nested containment
- no floating sub-surfaces

## Recap
Make one clear, memorable, topic-native landing page.
Hero first.
One visual world.
Specific CTAs.
Optional proof only if justified.
Lower support cluster.
No generic SaaS drift.
