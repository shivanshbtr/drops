# Drops — A Poem Website

> *"Is it that their scars were gone, / Or that they learned to carry on?"*

A scroll-driven poetry experience built entirely in the browser. The poem **Drops** — about regret, the safer path, and moving forward — is presented as a living landscape that shifts as you read.

---

## The Poem

Five stanzas. A journey from the shoreline of longing through a chosen path, quiet regret, a storm, and finally — a clearing.

| Stanza | Theme |
|--------|-------|
| 1 | Longing — the shore almost reached |
| 2 | The safer path chosen |
| 3 | Peaceful silence, then regret |
| 4 | The storm — unanswered questions |
| 5 | Moving forward |

---

## Two Versions

### 1. `drops_pure_html5_canvas_js.html` — Pure Canvas Edition *(the main one)*

Every visual is drawn in code. No images. No external libraries. Just the browser's `<canvas>` API and JavaScript.

**What's inside:**
- **6 animated scenes** that crossfade as you scroll, each matched to its stanza:
  - Start → moonlit open sea
  - Stanza 1 → turbulent ocean, figure wading, dramatic sunset
  - Stanza 2 → coastal path, the road not taken
  - Stanza 3 → quiet lakeside at dusk
  - Stanza 4 → heavy storm, rain particle system
  - Stanza 5 → clearing sky, birds, calm water
- **Procedural rain system** — animated drops that sync with the storm stanza and fade as the poem ends
- **Sea spray particles** and water shimmer
- **Dynamic sky rendering** — sun, moon, clouds, stars, horizon glow — all computed
- **Scroll-driven crossfading** between scenes using `requestAnimationFrame`
- **`IntersectionObserver`** for stanza reveal animations
- `prefers-reduced-motion` support
- Mobile-aware layout using `100svh`
- Fully responsive — canvas resizes on window change

**Stats:** ~3,300 lines · 905+ canvas draw calls · 0 external dependencies (fonts aside)

---

### 2. `drops_website_AI_gen_images/drops.html` — AI Image Edition

The same poem with AI-generated photography as scroll backgrounds. A parallax-driven layout with per-stanza full-viewport scenes.

**Assets:**
- `cover.jpg` / `1.jpg`–`5.jpg` / `end.jpg` — desktop images
- `1-mob.jpg`, `2-mob.jpg`, `end-mob.jpg` — mobile variants

---

## Project Structure

```
drops_pure_html5_canvas_js.html       ← Pure canvas version (self-contained)
Poem.png                              ← Original poem image
drops_website_AI_gen_images/
  drops.html                          ← AI image version
  cover.jpg, 1.jpg … end.jpg         ← Desktop background images
  1-mob.jpg, 2-mob.jpg, end-mob.jpg  ← Mobile background images
```

---

## Running Locally

Both files are self-contained HTML — just open them in a browser.

```bash
# Option 1 — open directly
open drops_pure_html5_canvas_js.html

# Option 2 — serve locally (avoids any path issues with the image version)
python3 -m http.server 8000
# then visit http://localhost:8000
```

No build step. No npm. No frameworks.

---

## Technical Notes

The canvas engine crossfades between scenes by tracking scroll position as a normalized value and interpolating `globalAlpha` across overlapping scene draw calls. Each scene function is stateful — particle arrays, stone slab positions, and spray data are seeded once and reused across frames for performance.

The rain system runs on a separate canvas layer (`#rain-canvas`) composited above the scene canvas, so rain can be faded in/out independently without redrawing the background.

Fonts used: [Cinzel](https://fonts.google.com/specimen/Cinzel), [Cormorant Garamond](https://fonts.google.com/specimen/Cormorant+Garamond), [Inter](https://fonts.google.com/specimen/Inter) — all via Google Fonts.

---

## Credits

Poem written by me.
Canvas rendering and scroll engine — built with AI assistance (~80% of the canvas code was developed through iterative prompting, requiring significant domain knowledge of canvas APIs, particle systems, and scene architecture to direct).
AI-generated images — created for the image version.

---

*stillness after rain*
