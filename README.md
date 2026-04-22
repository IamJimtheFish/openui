# Landing Page Design Codex Package

This package is a **local Codex marketplace** that exposes one installable plugin:

- `landing-page-design-plugin`

The plugin contains one skill:
- `landing-page-design`

It is designed for landing-page generation workflows where Codex must:

1. ensure repo-root `AGENTS.md` contains the landing-page workflow guidance
2. create `/design.md` before implementation
3. resolve all missing inputs before implementation
4. create separate resolved inputs for every requested variant
5. avoid fake proof and generic SaaS drift
6. implement each page **from `design.md`**, one by one

---
## What is inside

- `.agents/plugins/marketplace.json`  
  Local marketplace definition for Codex.
- `plugins/landing-page-design-plugin/.codex-plugin/plugin.json`  
  Plugin manifest.
- `plugins/landing-page-design-plugin/skills/landing-page-design/SKILL.md`  
  The actual workflow Codex uses.
- `repo-files/AGENTS.md`  
  Optional repo-level rules reference. The skill can create or append this guidance automatically.
- `repo-files/design.md.example`  
  Example shape of the design plan file.
- `repo-files/TARGET_REPO_SETUP.md`  
  Short instructions for the target repository.

---
## Repo guidance behavior

The skill now self-seeds repo guidance when it runs:

- If the target repository has no `AGENTS.md`, the skill creates one.
- If the target repository has an `AGENTS.md` without landing-page workflow guidance, the skill appends a marked section.
- If equivalent guidance already exists, the skill leaves the file unchanged.

You can still copy `repo-files/AGENTS.md` manually if you want the repository guidance present before the first skill run.

---
## Fastest install path

1. Unzip this package anywhere.
2. Add the local marketplace to Codex:

```bash
codex plugin marketplace add ./landing-page-design-codex-marketplace
```

Run that command from the directory that contains the unzipped folder, or replace the path with an absolute path.

3. Restart Codex.

---
## Alternative manual repo-scoped install

If you want this plugin available only to one repository:

1. Copy `plugins/landing-page-design-plugin` into:

   `<repo>/plugins/landing-page-design-plugin`

2. Copy this marketplace file into:

   `<repo>/.agents/plugins/marketplace.json`

   using the provided marketplace file from this package.

3. Optional: copy or merge `repo-files/AGENTS.md` into:

   `<repo>/AGENTS.md`

4. Restart Codex.

---
## Suggested usage prompt in Codex

Example:

```text
Create 3 landing page variants for an AI-native interior design studio.
Use the landing-page-design workflow.
```

The skill should then:
- create `/design.md`
- resolve inputs independently for each variant
- keep variants materially different
- implement variants one by one from the design plan

---
## Notes

- The skill preserves user-specified inputs when present.
- When inputs are missing, the skill resolves them before writing `design.md`.
- For multi-variant requests, the skill re-resolves every input for every variant instead of reusing one inferred set.
