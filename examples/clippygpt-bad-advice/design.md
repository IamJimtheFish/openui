# Landing Page Design Plan

## Variant 1

### Resolved inputs

- Topic: ClippyGPT, a fake assistant that gives unhelpful life advice.
- Offer: A playful mock assistant demo that dispenses glossy, misguided, Y2K-era advice on demand.
- Audience: Internet culture fans, designers, and developers who enjoy nostalgic software parody.
- Primary user action: Ask for bad advice.
- Deliverable: Single-file HTML with embedded CSS and JS.
- Style direction: Y2K old-software chrome.
- Tonal key: Bright candy desktop with electric blue, chrome silver, hot pink, acid green, and soft lavender gradients.
- Icon policy: Topic-native only, using old-toolbar symbols and a paperclip mascot shape where useful.
- Proof assets: none.
- Motion intensity: Rich but controlled.

### Composition contract

- Hero archetype: immersive.
- First-viewport structure: The page reads as a glossy retro desktop window. A chrome title bar and toolbar establish old-software atmosphere, while the first viewport centers the product name and offer in a large two-line headline. A custom paperclip assistant and speech bubble sit beside the copy on desktop and tuck beneath it on mobile. The two CTAs sit under the supporting sentence. The lower support cluster is visible within the first viewport as the next-section hint.
- Primary visual/proof artifact: A custom paperclip assistant illustration with reflective chrome strokes, wide eyes, and a speech bubble that displays deliberately unhelpful advice. This is a product gesture, not invented proof.
- Interaction behavior: The primary CTA cycles the speech bubble through unhelpful advice and briefly shimmers the assistant. The secondary CTA changes the advice mood and accent color.
- Reuse boundary: Shared reset and accessibility helpers may be reused by the examples gallery; the hero, mascot, advice interaction, and Y2K chrome palette are custom to this example.

### Filled generation prompt

Design a Y2K-style landing page for ClippyGPT, a fake assistant that gives unhelpful life advice. Use glossy UI, retro gradients, chrome effects, old-software vibes, and a playful but polished layout.

The page must be a single-file HTML deliverable with embedded CSS and JS. It should have exactly one primary CTA, "Ask Bad Advice", and exactly one secondary CTA, "Change Advice Mood". Use a custom paperclip assistant as the hero artifact. Keep support highlights in one lower cluster only. Do not invent proof, metrics, testimonials, logos, or screenshots.

### Output target

- Path: examples/clippygpt-bad-advice/index.html
