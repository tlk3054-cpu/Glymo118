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
