# CLAUDE.md

Guidance for Claude Code (and any other agents) working in this repository.

## Stack & Conventions

This is a single-page class project with two hard constraints:

1. **Single-file project.** The entire project must live in one `index.html`
   file. All CSS must be inlined in `<style>` tags and all JavaScript must be
   inlined in `<script>` tags within that file — do not split markup, styles,
   or scripts into separate `.html`, `.css`, or `.js` files, and do not add
   additional pages. Linking to external images and to external CSS/JavaScript
   libraries (e.g. via `<link>`/`<script src="https://...">`) is allowed. This
   constraint exists so the finished project can be copy-pasted as one file
   for sharing in class and on single-file code platforms (e.g. CodePen,
   JSFiddle, single-file gists).
2. **Vanilla only.** Use plain HTML, CSS, and JavaScript only. No frameworks
   or libraries that require a build step (no React, Vue, Svelte, TypeScript,
   Sass/Less, bundlers, etc.), and no build/compile step of any kind — the
   file must run as-is when opened in a browser.

## Tech stack (hard constraints — do not deviate)
- Vanilla HTML, CSS, and JavaScript only. No React, Vue, or any JS framework.
- Tailwind CSS for all styling (via CDN only).
- No backend, no database. Fully static site.
- A toggle for light and dark theme, with the choice remembered
  across visits.

## Working conventions
- Before implementing any non-trivial feature, ask clarifying
  questions about scope, edge cases, and constraints first —
  don't propose a plan until you've asked.

## Feature Plan

The project is a portal where visitors browse and try a growing
collection of small web tools and learning artifacts. Since everything
must live in one `index.html` (see Stack & Conventions), growth means
adding sections to that file, not adding files — each phase below should
follow that pattern.

### Phase 1 — Portal shell + first two tools
**Status:** shell built (`index.html`); Beam Deflection Simulator working,
Word & Character Counter still a placeholder

**Data model** (plain JS, no backend):
- A `TOOLS` registry array, one entry per tool/lesson:
  `{ id, title, description, category: 'tool' | 'lesson' }`
- No persisted app data — the only thing saved is the theme preference
  (`localStorage`, key `theme`).

**Key flows:**
- ✅ **Catalog** — cards render from `TOOLS` into a grid; category tabs
  (All / Tools / Lessons) filter client-side.
- ✅ **Navigation** — hash router (`#/tool/<id>`) shows/hides one
  `<section data-view="...">` per entry; deep links + back/forward work.
- ✅ **Theme** — toggle flips a `dark` class on `<html>` (CSS-variable
  palette, Study Hall direction); preference read/written via
  `localStorage`, falling back to `prefers-color-scheme` on first visit.
- ⬜ **Word & Character Counter** (tool) — catalog entry + tool view exist
  as a placeholder ("logic not built yet"); still needs the live word/char
  count behavior.
- ✅ **Beam Deflection Simulator** (lesson) — replaced the Flexbox
  Playground slot. Cantilever beam (fixed one end, free the other) drawn
  as inline SVG; a slider (0&ndash;500 N) drives a live
  `deflection = load * length^3 / (3 * stiffness)` calculation (3 m
  steel beam, E = 200 GPa, I = 1.7&times;10&#8310; mm&#8308;) shown in mm
  next to the slider, with the beam bending on screen (visually
  magnified) to match.

**Growing the collection later** = add one `TOOLS` entry + one `<section>`
+ its script block. No structural changes needed — proven by the two
placeholder entries already routing correctly.

### Phase 2+ — later tools/lessons
Not yet scoped. Each addition follows the phase 1 pattern (registry entry
+ section); plan the specifics per-tool when picked up.
