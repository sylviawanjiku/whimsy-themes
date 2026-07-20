# Whimsy Themes

A collection of whimsical color themes for VS Code and Cursor.

## Themes

### Whimsy Candy Dark

Deep indigo/charcoal background with soft pastel candy accents.

| Role | Color | Swatch name |
| --- | --- | --- |
| Background | `#1E1B2E` | Deep indigo |
| Foreground | `#E8E3F5` | Moonlight lavender |
| Keywords | `#F5A3C7` | Rose pink |
| Strings | `#A8E6CF` | Mint |
| Functions | `#9DD6F5` | Baby blue |
| Numbers / constants | `#FFCBA8` | Peach |
| Types / classes | `#C9B8F0` | Soft violet |
| Comments | `#7A7295` | Muted lavender (italic) |

#### Rainbow brackets

Nested bracket pairs cycle through six candy colors (rose, mint, baby blue,
peach, violet, butter), with matching pair guides connecting each opening
bracket to its closing one. Mismatched brackets show in error rose `#FF8FA3`.

Two editor settings control this (both should be on):

```json
{
  "editor.bracketPairColorization.enabled": true,
  "editor.guides.bracketPairs": true
}
```

`bracketPairColorization.enabled` defaults to true; `guides.bracketPairs`
defaults to false and must be enabled by hand. Use `"active"` instead of
`true` to draw a guide only for the pair under the cursor.

## Developing

1. Open this folder in Cursor (or VS Code).
2. Press `F5` to launch an Extension Development Host window with the theme available.
3. Edit `themes/*.json` and save — changes hot-reload in the dev host window.

## Installing locally

```bash
npx @vscode/vsce package
cursor --install-extension whimsy-themes-0.0.1.vsix
```

Then pick the theme via `Cmd+K Cmd+T` (Preferences: Color Theme).

## Adding a new theme

1. Create `themes/<name>-color-theme.json` (copy an existing one as a starting point).
2. Add an entry to the `contributes.themes` array in `package.json`:

```json
{
  "label": "Whimsy <Name>",
  "uiTheme": "vs-dark",
  "path": "./themes/<name>-color-theme.json"
}
```

Use `"uiTheme": "vs"` for light themes.

3. Bump the `version` in `package.json`, re-package, and re-install.
