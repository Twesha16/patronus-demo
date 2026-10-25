# Patronus — product demo prototype

## What this is
A click-through **demo** (dummy content, no backend) of Patronus: a product that helps people explore, notice, remember, own and express their preferences (art, decor, gifts, writing, LinkedIn posts, SOPs…). Setting: a future where everyone has a personal AI agent that knows them better than they know themselves. The demo shows one user ("Riya") moving through the product. Built originally as a claude.ai artifact; this folder is the handoff for deployment and final polish.

## Files
- `index.html` — the whole app: HTML + CSS + JS in one file. Images (deer, deer head, wordmark) are inlined as base64 `data:` URIs.
- `assets/` — original logo images (`deer.png`, `wordmark.png`) and the cropped `deer-head.jpg` avatar. Not referenced yet; use them if you move images out of base64.
- Fonts come from Google Fonts: Inter (Notion-like UI font, required), Marcellus (brand moments), Fraunces + IBM Plex Mono (font samples on the main site).

## Working rules from the owner (Twesha)
- Clarify before building; ask about layout/placement before making UI changes.
- Keep it distinctive, not a generic AI-built site. UI font must stay Notion-like (Inter).
- Be critical; suggest better copy/UX when something is weak.
- Glow: low-to-moderate only, never wide or heavy.
- Typing animation: ONLY for the opening line and for the user's mock answers/prompts. Everything Patronus says fades in.
- Leave generous pauses in every question → answer exchange.

## Visual system
- Black `#000` + cyan `#99FFFF` (tokens in `:root`). Dots as accents: cursor trail (intro only), progress dots, background dot grid, dotted note icon, dotted thumbnails.
- Dot-wave transition (`wipe()`) plays ONLY when moving between inside Patronus and outside it (`OUT` set: intro, brand, mock AI agent, ambient demo, article).
- The Patronus deer is a small round "guide" avatar next to anything Patronus says. In Active mode it's a bottom-right orb labelled "In active mode".

## Navigation engine (bottom `<script>`)
- Each `<section class="screen" data-k="...">` is a screen; behaviour lives in object `D[key]` with `enter(ep)`, `beats[]`, and optional `next()`, `light`, `trail`, `anywhere`, `last`, `parent`.
- `advance()` runs the next beat (e.g. Copy, Paste, Send) before moving on. The right ~18% of the screen (`#zone`) is a big click target for the arrow. → / Space go forward, ← and the bottom-left back button go back. Screens with `parent` (demos, main site) go back to the modes screen.
- Screen HTML is restored from a template every time a screen is entered (`tpl`), so screens always replay from the start. `epoch`/`alive(ep)` cancel stale async timers.
- `window.__go(i)` jumps to a screen index (handy for testing).

## Screen order
0 intro typewriter (no collage) → 1 "Catch up to yourself with PATRONUS" → 2 copy context prompt (shown as abstract lines) + sensitive-info note → 3 mock "Riya's personal AI agent" (light) → 4 paste back (214 prefs / 9 areas / 0 sensitive) → 5 quiz card (3 turns) → 6 explore. notice. & remember. → 7 permissions (click both toggles, then Grant access) → 8 areas (Patronus suggests 3 of 5: fonts, leadership principles, fashion; just click next) → 9 modes (Quiet: no demo; Ambient/Active: "See … mode demo"; "Proceed to main site") → 10 ambient demo → 11 active demo (original newsletter article on "leadership"; scroll locks at "Sometimes it’s shorthand for intuition."; ⌘/Ctrl+K saves it — ⌘N can't be captured by browsers; second stop asks for a reflection) → 12 main site (Explore: photo cards mixing the 3 areas, each opens a 3-question card — picked image, a comparison from the next area, a recall of a past answer from the third; round + opens a "slow down" prompt with rolling research. Daily take: pineapple on pizza → for/not for me → strength → two whys → results with For/Not-for-me word clouds → share options. Taste profile: origins split, specificity, noticed moments, experiments, next areas).
- `parent` is a screen key (e.g. `'modes'`); use `idx(key)` rather than hard-coded indexes. Skip-tutorial button shows on walkthrough screens 2+.
- Every answer field has an "I don't know" button. Mock answers never type on their own: tutorial answers wait for Next (quiz/ambient/active screens have `ask:true`, which also shows a faint "Click anywhere to continue" after 12s idle); main-site answers wait for a click in the field.
- Main site sidebar switches pages (`.pg[data-pg]`): Explore, Daily takes, Taste profile, Reflections, Your friends (no taste overlap), Modes. Taste profile sections come from the `TP` template. Photos live in `assets/{type,biz,fashion,takes}`; credits in `assets/type/CREDITS.md` (CC BY/BY-SA need attribution if published).

## Open items
- Daily takes and Taste profile contents: owner will specify.
- A scripted journey on the main site: owner will specify.
- The article in the active demo is original text in a newsletter look-alike, with a made-up author and publication. Don't replace it with the real Substack article's text.

## Deploy
Static site, no build step. Any static host works: Vercel (`npx vercel`), Netlify (drag the folder or `npx netlify deploy`), or GitHub Pages.
