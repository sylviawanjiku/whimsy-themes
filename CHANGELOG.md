# Changelog

## 0.2.0 — 2026-07-20

Three new themes, each a full palette remap of the Candy Dark base
(workbench, syntax, semantic tokens, terminal, and rainbow brackets):

- **Whimsy Storybook Light** — cream paper with warm storybook inks
  (berry keywords, leaf-green strings, dusty-blue functions).
- **Whimsy Fairy Neon** — vivid fairy-tale neon on midnight indigo
  (neon pink, aqua glow, electric blue and violet).
- **Whimsy Garden** — earthy garden tones on forest floor
  (floral pink, moss, stream blue, mushroom tan, wisteria).

All palettes pass the same contrast checks applied to Candy Dark in 0.1.1.

## 0.1.1 — 2026-07-20

Contrast fixes from code review; no visible change to the theme's character.

- Terminal ANSI black `#2A2540` → `#585174` — was 1.21:1 against the terminal
  background, effectively invisible. Bright black moves `#585174` → `#7A7295`
  to preserve ordering.
- Input placeholder text `#6B6488` → `#8A82A8` (2.81:1 → 4.31:1).
- Editor line numbers `#585174` → `#6B6488` (2.27:1 → 3.04:1) — still dim,
  now legible.

## 0.1.0 — 2026-07-20

Initial Open VSX release.

- Whimsy Candy Dark: deep indigo background with pastel candy accents
  (rose keywords, mint strings, baby-blue functions, peach numbers,
  soft-violet types, italic muted-lavender comments).
- Full workbench styling: sidebar, tabs, status bar, terminal ANSI palette,
  git decorations, diff and peek views.
- Rainbow bracket pairs and bracket-pair guides in six candy colors, with
  mismatched brackets highlighted in error rose.
- Semantic highlighting for modern language servers.
