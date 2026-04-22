# Target repo setup

The plugin skill can create or append repository guidance automatically when it runs.

Optional manual setup before the first skill run:

- `AGENTS.md` -> `<repo>/AGENTS.md`

Optional reference:
- `design.md.example` -> not required; only for structure reference

Expected repo behavior after setup:
- Codex uses the OpenUI skill for landing-page tasks
- Codex creates `<repo>/AGENTS.md` if it is missing
- Codex appends marked landing-page workflow guidance if `AGENTS.md` exists without it
- Codex creates `/design.md` first
- Codex fills all prompt inputs with concrete values
- Codex resolves inputs separately for each variant
- Codex adds a composition contract for every variant
- Codex implements the pages from `/design.md` in order
- For four or more variants, Codex works in batches of at most three and visually inspects desktop and mobile screenshots before continuing
