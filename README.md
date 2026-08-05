# Whimsy Themes

A collection of whimsical color themes for VS Code and Cursor.

## Themes

### Whimsy Candy Dark

Deep indigo/charcoal background with soft pastel candy accents.
![Whimsy Candy Dark](https://github.com/user-attachments/assets/5e4006b2-a820-4826-abb5-7763405acb3b)



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

All four themes share this bracket treatment, each in its own palette.

### Whimsy Storybook Light

Cream paper with warm storybook inks.
![Whimsy Storybook Light](https://github.com/user-attachments/assets/f7ee67d6-b6b8-47df-a07a-0dd8c96adb4d)


| Role | Color | Swatch name |
| --- | --- | --- |
| Background | `#FBF6EA` | Cream paper |
| Foreground | `#453A2F` | Warm ink |
| Keywords | `#B04A73` | Berry |
| Strings | `#3E7A4E` | Leaf green |
| Functions | `#3D6E99` | Dusty blue |
| Numbers / constants | `#AD5C2B` | Terracotta |
| Types / classes | `#7A55A3` | Plum |
| Comments | `#98876C` | Faded ink (italic) |

### Whimsy Fairy Neon

Vivid fairy-tale neon on deep indigo.
![Whimsy Fairy Neon](https://github.com/user-attachments/assets/0709000f-84e5-43ce-8665-5aef0e23ce1f)


| Role | Color | Swatch name |
| --- | --- | --- |
| Background | `#16102E` | Midnight indigo |
| Foreground | `#EDE7FF` | Starlight |
| Keywords | `#FF6EC7` | Neon pink |
| Strings | `#50FAC8` | Aqua glow |
| Functions | `#5CC8FF` | Electric blue |
| Numbers / constants | `#FFAE57` | Neon amber |
| Types / classes | `#B98CFF` | Electric violet |
| Comments | `#7E71B0` | Dusk (italic) |

### Whimsy Garden

Earthy garden whimsy: mosses, florals, mushroom tones.
![Whimsy Garden](https://github.com/user-attachments/assets/2048ad3d-54e2-4cb4-a7a2-0c4583f54ea3)


| Role | Color | Swatch name |
| --- | --- | --- |
| Background | `#20261C` | Forest floor |
| Foreground | `#E7EDDD` | Morning mist |
| Keywords | `#D98BA6` | Floral pink |
| Strings | `#A8C686` | Moss |
| Functions | `#8FBFD9` | Stream blue |
| Numbers / constants | `#D9B98C` | Mushroom tan |
| Types / classes | `#B3A3D6` | Wisteria |
| Comments | `#87957B` | Sage (italic) |

### Whimsy Tidepool

Deep Solarized-style lagoon teal with bright rock-pool accents.
![Whimsy Tidepool](https://github.com/user-attachments/assets/d834f641-50a1-4406-9905-4122397f792a)

| Role | Color | Swatch name |
| --- | --- | --- |
| Background | `#002B36` | Deep tidepool |
| Foreground | `#C9D6D4` | Sea foam |
| Keywords | `#E86FA9` | Anemone pink |
| Strings | `#43BFB4` | Lagoon cyan |
| Functions | `#7EC0FD` | Sky blue |
| Numbers / constants | `#D8A648` | Sunlit gold |
| Types / classes | `#9FA8DF` | Sea-glass violet |
| Comments | `#5E7B82` | Driftwood teal (italic) |

## Developing

1. Open this folder in Cursor (or VS Code).
2. Press `F5` to launch an Extension Development Host window with the theme available.
3. Edit `themes/*.json` and save — changes hot-reload in the dev host window.

## Installing locally

```bash
npx @vscode/vsce package
cursor --install-extension whimsy-themes-*.vsix
```

(The wildcard picks up whatever version you just built.)

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

## Releasing

Releases are published to [Open VSX](https://open-vsx.org/extension/sylviawanjiku/whimsy-themes)
automatically by the [Publish workflow](.github/workflows/publish.yml) when a
version tag is pushed:

1. Bump `version` in `package.json` and add a `CHANGELOG.md` entry.
2. Commit and push to `main` (the Validate workflow checks the theme JSON and packaging).
3. Tag the release and push the tag:

```bash
git tag v0.4.0
git push origin v0.4.0
```

The workflow fails if the tag doesn't match the `version` in `package.json`.
It authenticates with the `OVSX_PAT` repository secret (an access token from
open-vsx.org → account → Access Tokens); if the token expires, generate a new
one and update the secret under Settings → Secrets and variables → Actions.

Screenshots in this README must be plain markdown images (`![name](url)`),
not `<img>` tags with fixed `width`/`height` — Open VSX narrows images to fit
its page while keeping any fixed height, which distorts them.
