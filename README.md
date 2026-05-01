# OpenUI Codex Package

This package is a **local Codex plugin** that exposes one installable plugin with same named skill: - `openui`

---

## Live examples

> I intentionally kept the previews as real one-shot outputs rather than polished, hand-picked examples. I could have run more iterations, fixed small issues, and selected only the cleanest results, but that would not reflect the actual behavior honestly. These previews are meant to show what the project produces in a realistic first pass, not a fake-perfect final result.

Better results are still possible by steering the model more directly in the prompt, for example by specifying style, composition, mood, constraints, or other concrete visual ideas.

## Inside codex app - Model codex-5.4 high

| Example                  | Preview                                                                                                                | Prompt or design source                                  |
| ------------------------ | ---------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------- |
| ClippyGPT Bad Advice     | [Preview](https://iamjimthefish.github.io/openui/examples/clippygpt-bad-advice/)        | Design a Y2K-style landing page for ClippyGPT — fake assistant that gives unhelpful life advice. Use glossy UI, retro gradients, chrome effects, old-software vibes, and playful but polished layout|
| Coffee Optimization Unit | [Preview](https://iamjimthefish.github.io/openui/examples/coffee-optimization-unit/)    | Create a blueprint-inspired landing page for “Coffee Optimization Unit”, a fake system that calculates the perfect caffeine dose for productivity. Use white linework on deep blue background, schematic diagrams, labeled components, and precise industrial layout. |
| Stillwell Bottled Silence | [Preview](https://iamjimthefish.github.io/openui/examples/stillwell-bottled-silence/)   | Design a premium landing page for a startup that sells bottled silence. |
| LTT Drop-Test Department | [Preview](https://iamjimthefish.github.io/openui/examples/ltt-drop-test-department/)    | Create a parody landing page about an AI code leak, but make it look like a real product launch, you can use imagengen if needed. |
| Ship Happens             | [Preview](https://iamjimthefish.github.io/openui/examples/ship-happens-terminal-comic/) | Design a meme-worthy bug tracker for developers. |
| Grand Line of the Stars  | [Preview](https://iamjimthefish.github.io/openui/examples/grand-line-of-the-stars/)     | task is I want you to build a single HTML file for a game project combining the worlds of Star Wars in One Piece. full creen hero section with a dark background, a rotating 3D sphere in 3.js with custom VLSL fragment charter that makes it looks like like a glowing planet and a sphere that slowly rotates on its y-axis. On scroll, GSAP animates the sphere, scaling down and fading out as the text headline fades in. Then the headline has a framer motion style stagger entrance. Each word slides up, so it should work in Chrome. No mpn.@openui

## Used in chatgpt.com web page, extended reasoning, all prompts are same just different topic/style input

| Example              | Preview                                                                                                       | Prompt or design source                         |
| -------------------- | ------------------------------------------------------------------------------------------------------------- | ----------------------------------------------- |
| Mnemonic Glitch      | [Preview](https://iamjimthefish.github.io/openui/examples/mnemonic-glitch/)    | [Prompt](examples/mnemonic-glitch/prompt.md)    |
| Theo Survival Holo   | [Preview](https://iamjimthefish.github.io/openui/examples/theo-survival-holo/) | [Prompt](examples/theo-survival-holo/prompt.md) |
| Tiny Truce Club      | [Preview](https://iamjimthefish.github.io/openui/examples/tiny-truce-club/)    | [Prompt](examples/tiny-truce-club/prompt.md)    |
| Theo Clears the Feed | [Preview](https://iamjimthefish.github.io/openui/examples/theo-clears-feed/)   | No prompt included                              |
| Theo t3.gg           | [Preview](https://iamjimthefish.github.io/openui/examples/theo-t3gg/)          | No prompt included                              |

Open the [examples gallery](https://iamjimthefish.github.io/openui/) or preview individual examples:

Playwright can help a lot for visual QA: use it to open every generated route, capture desktop and mobile screenshots, check console errors, and catch overflow or overlap before calling a page done.

The imagegen skill can also help a lot when the page needs topic-native hero images, proof artifacts, textures, product shots, or other bitmap assets that should not be faked with generic placeholders.

---

A few issues I’m currently working on:
- overlap — already fixed locally
- hardcoded CTAs and support cluster — also fixed locally
- headline is still a bit too busy — this one is still pending

---

## Suggested usage prompt in Codex

Example:

```text
Create 3 landing page variants for an AI-native interior design studio.
Use the openui workflow.
```

The skill should then:

- create `/design.md`
- resolve inputs independently for each variant
- write a composition contract for each variant
- keep variants materially different
- implement variants one by one from the design plan
- for four or more variants, inspect desktop and mobile screenshots in batches of at most three before continuing

---

## Notes

- The skill preserves user-specified inputs when present.
- When inputs are missing, the skill resolves them before writing `design.md`.
- For multi-variant requests, the skill re-resolves every input for every variant instead of reusing one inferred set.
- For larger multi-variant requests, the skill discourages a single generic renderer unless every variant still has a custom hero composition, visual/proof artifact, and interaction behavior.

---

OpenUI is designed for landing-page generation workflows where Codex must:

1. ensure repo-root `AGENTS.md` contains the landing-page workflow guidance
2. create `/design.md` before implementation
3. resolve all missing inputs before implementation
4. create separate resolved inputs for every requested variant
5. avoid fake proof and generic SaaS drift
6. implement each page **from `design.md`**, one by one
7. for larger variant sets, work in small batches with visual quality gates so later variants do not degrade into reskins

---

## What is inside

- `.agents/plugins/marketplace.json`  
  Local marketplace definition for Codex.
- `plugins/openui/.codex-plugin/plugin.json`  
  Plugin manifest.
- `plugins/openui/skills/openui/SKILL.md`  
  The actual workflow Codex uses.
- `repo-files/AGENTS.md`  
  Optional repo-level rules reference. The skill can create or append this guidance automatically.
- `repo-files/design.md.example`  
  Example shape of the design plan file, including the per-variant composition contract.
- `repo-files/TARGET_REPO_SETUP.md`  
  Short instructions for the target repository.
- `examples/`  
  Previewable generated examples, each in its own folder with its prompt or design notes when available.

---

## Repo guidance behavior

OpenUI self-seeds repo guidance when it runs:

- If the target repository has no `AGENTS.md`, the skill creates one.
- If the target repository has an `AGENTS.md` without landing-page workflow guidance, the skill appends a marked section.
- If equivalent guidance already exists, the skill leaves the file unchanged.

You can still copy `repo-files/AGENTS.md` manually if you want the repository guidance present before the first skill run.

---

## Fastest install path

1. Unzip this package anywhere.
2. Add the local marketplace to Codex:

```bash
codex plugin marketplace add ./openui
```

Run that command from the directory that contains the unzipped folder, or replace the path with an absolute path.

3. Restart Codex.

---

## Alternative manual repo-scoped install

If you want this plugin available only to one repository:

1. Copy `plugins/openui` into:

   `<repo>/plugins/openui`

2. Copy this marketplace file into:

   `<repo>/.agents/plugins/marketplace.json`

   using the provided marketplace file from this package.

3. Optional: copy or merge `repo-files/AGENTS.md` into:

   `<repo>/AGENTS.md`

4. Restart Codex.

---
