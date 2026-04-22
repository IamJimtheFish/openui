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
