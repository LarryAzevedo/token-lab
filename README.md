# Token lab

A small test project for a light and dark token pipeline:

**Tokens Studio (Figma)** → **GitHub** (`tokens/` folder) → **Style Dictionary** (GitHub Action) → **`dist/tokens.css`** with `light-dark()`

## What's in here

| Path | What it is |
| --- | --- |
| `tokens/primitives/color.json` | Raw palette. Theme-agnostic. |
| `tokens/semantic/light.json` | Semantic tokens, light values |
| `tokens/semantic/dark.json` | Same semantic tokens, dark values |
| `tokens/$themes.json` | Written by Tokens Studio Themes. Tells the build which sets make up Light and Dark. |
| `tokens/$metadata.json` | Token set order for Tokens Studio |
| `build.mjs` | Runs Style Dictionary for each theme and pairs the results into `light-dark()` |
| `.github/workflows/build-tokens.yml` | Runs the build on GitHub whenever `tokens/` changes |
| `dist/tokens.css` | The output. Generated, never edited by hand. |
| `index.html` | Demo card that uses only semantic tokens |

## Rules the build enforces

- Every semantic token must exist in both Light and Dark, or the build fails with a message naming the token.
- Primitives are written with a `--_` prefix to mark them private.
- Semantic tokens keep their references: `light-dark(var(--_color-gray-900), var(--_color-gray-50))`.

## Optional: run the build on your own computer

1. Install Node.js (the LTS version) from nodejs.org.
2. Open Terminal in this folder and run `npm install` once.
3. Run `npm run build` whenever you want to rebuild `dist/tokens.css`.
