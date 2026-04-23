# OpenUI Design Plan

## Variant 1

### Resolved inputs
- Topic: A browser game concept that fuses space-opera sword energy with pirate-adventure island hunting, inspired by the worlds of Star Wars and One Piece without using official logos or assets.
- Offer: A playable teaser landing page for a fictional game project called Grand Line of the Stars.
- Audience: Anime and space-fantasy fans who want a cinematic browser-game prototype.
- Primary user action: Explore the teaser.
- Deliverable: Single-file HTML with embedded CSS and JS.
- Style direction: Cinematic space-pirate.
- Tonal key: Dark.
- Icon policy: Minimal topic-native glyphs in the lower support cluster only.
- Proof assets: none.
- Motion intensity: Rich but controlled.

### Composition contract
- Hero archetype: immersive
- First-viewport structure: a full-screen sticky hero opens on a custom-shaded Three.js glowing planet against a deep starfield; the headline, supporting copy, and two CTAs sit centered over the planet but begin hidden, then scroll into view while the planet scales down and fades.
- Primary visual/proof artifact: a rotating GLSL-shaded glowing planet with ringed energy bands, plasma coastlines, and a luminous rim that suggests a sea map projected onto a moon.
- Interaction behavior: scroll-driven GSAP sequence scales and fades the sphere, then reveals the headline with a Framer Motion style stagger where each word slides up independently; CTAs have direct hover and focus feedback.
- Reuse boundary: only reset styles, accessibility utilities, and small shader/canvas setup patterns may be shared; the planet shader, scroll reveal, copy, and support cluster are custom to this variant.

### Filled generation prompt
Create one high-concept landing page for A browser game concept that fuses space-opera sword energy with pirate-adventure island hunting, inspired by the worlds of Star Wars and One Piece without using official logos or assets.

## Inputs
- Topic: A browser game concept that fuses space-opera sword energy with pirate-adventure island hunting, inspired by the worlds of Star Wars and One Piece without using official logos or assets.
- Offer: A playable teaser landing page for a fictional game project called Grand Line of the Stars.
- Audience: Anime and space-fantasy fans who want a cinematic browser-game prototype.
- Primary user action: Explore the teaser.
- Deliverable: Single-file HTML with embedded CSS and JS.
- Style direction: Cinematic space-pirate.
- Tonal key: Dark.
- Icon policy: Minimal topic-native glyphs in the lower support cluster only.
- Proof assets: none.
- Motion intensity: Rich but controlled.

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
- Prefer the strongest fully resolved concept that fits the constraints, not the fastest concept that merely fits in.

## Ambition and scope discipline
- Do not treat missing implementation detail as permission to reduce conceptual ambition, visual specificity, or interaction richness when the concept clearly benefits from them.
- Prefer the simplest structure that preserves the strongest concept, not the simplest structure that merely satisfies the rules.
- Do not add extra content sections unless they are structurally necessary.
- If conceptual depth is needed, absorb it into the hero, proof gesture, support highlight copy, CTA behavior, or background logic rather than creating a new section by default.
- When choosing between restraint and richness, keep the stronger topic-native idea and remove only what weakens clarity, hierarchy, or credibility.
- Implementation simplicity is not a goal by itself. Concept strength, coherence, and usability take priority.

## Non-negotiables
- Use a strong hero-first composition.
- Headline: 3-12 words, max 3 lines.
- Supporting copy: 1-2 short sentences, concise, specific.
- CTAs: exactly 1 primary and 1 secondary.
- CTA labels must be specific to the offer and action, not generic.
- Supporting highlights: shown only in a single lower support cluster beneath the hero.
- Keep the hero dominant, focused, readable, and uncluttered.
- Proof is optional. Use it only if it clearly strengthens the concept.
- If no real proof assets are provided, do not invent metrics, testimonials, customer logos, screenshots, or fake UI proof.
- CTA behavior may be simple or richer, but it should fit the offer; do not default to generic anchor-link behavior if a more specific interaction model would strengthen the concept.

## Composition
- A full-screen immersive hero is required.
- Build hierarchy through scale, contrast, spacing, alignment, overlap, rhythm, and composition before using frames, dividers, or containers.
- Keep supporting content clearly subordinate to the hero.

## Visual system
- Build one coherent visual world from starfields, pirate navigation marks, luminous sword-energy color, sea-chart contour lines, and a glowing planet shader.
- Use a dark background with cyan plasma, amber chart marks, and restrained crimson highlights.
- Treat headline typography as active: one phrase receives chromatic energy emphasis while every word participates in the stagger reveal.

## Motion
- Use Three.js for a slowly rotating Y-axis planet with a custom GLSL fragment shader.
- Use GSAP ScrollTrigger so scrolling scales the sphere down and fades it out while headline copy fades in.
- Emulate a Framer Motion word stagger in plain JavaScript/GSAP: each word starts below its mask and slides upward in sequence.
- Respect reduced-motion preferences by showing the final readable state without scroll-driven dependence.

## Accessibility and readability
- Preserve strong readability and clear hierarchy at all viewport sizes.
- Maintain sufficient contrast between text and background.
- Use semantic HTML structure, visible focus states, keyboard-friendly interactions, and reduced-motion handling.

## Output
Return only the final Single-file HTML with embedded CSS and JS.

### Output target
- Path: /mnt/z/codex_new/10/index.html
