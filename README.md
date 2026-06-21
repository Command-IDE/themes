# Binder Themes

The official theme repository for [Binder](https://github.com/BinderTools/binder) — a terminal-first IDE built on Wails and React.

Themes are written in SCSS and applied via the `data-theme` HTML attribute. Each theme defines a set of CSS custom properties that control the shell UI — background, borders, tabs, and the info bar.

---

## Directory Structure

```
themes/
├── built-in/          # Official themes shipped with Binder
│   ├── _index.scss    # Imports all built-in themes
│   ├── _minimal.scss
│   ├── _dark.scss
│   └── ...
├── community/         # Community-contributed themes (added via pull request)
│   ├── _index.scss    # Imports all accepted community themes
│   ├── README.md      # Community contribution guide
│   └── _author-themename.scss
├── index.scss         # Root entry point — imports built-in + community
├── README.md
├── CONTRIBUTING.md
└── CODE_OF_CONDUCT.md
```

---

## Built-in Themes

| Key | Name | Style |
|-----|------|-------|
| `minimal` | Minimal | Apple iOS/macOS dark, muted grays |
| `dark` | Dark | VS Code dark default |
| `blackout` | Blackout | Pure black, high contrast |
| `dim-green` | Dim Green | Retro phosphor green terminal |
| `dim-blue` | Dim Blue | Cool blue monochrome terminal |
| `neon-night` | Neon Night | Cyberpunk — deep purple with neon pink and green |
| `solarized` | Solarized | Classic Solarized Dark palette |
| `nord` | Nord | Arctic, north-bluish color palette |
| `coffee` | Coffee | Warm espresso browns and amber |
| `gruvbox` | Gruvbox | Retro groove — warm dark oranges and greens |

---

## How Themes Work

Themes define CSS custom properties scoped to a `[data-theme]` attribute selector. When a user selects a theme in Binder, the app sets `document.documentElement.setAttribute('data-theme', 'theme-key')` and the SCSS variables take effect immediately.

```scss
// Example: built-in/_minimal.scss
[data-theme="minimal"] {
  --app-bg:               #1c1c1e;
  --border-color:         #2d2d2f;
  --info-bar-bg:          #252527;
  --info-bar-color:       #636366;
  --info-bar-hover-bg:    #2d2d2f;
  --info-bar-hover-color: #aeaeb2;
  --tab-color:            #636366;
  --tab-color-hover:      #c7c7cc;
  --tab-add-border:       #3a3a3c;
}
```

### CSS Custom Properties Reference

| Property | Description |
|----------|-------------|
| `--app-bg` | Main application background |
| `--border-color` | Panel and component borders |
| `--info-bar-bg` | Info/status bar background |
| `--info-bar-color` | Info/status bar text |
| `--info-bar-hover-bg` | Info bar item hover background |
| `--info-bar-hover-color` | Info bar item hover text |
| `--tab-color` | Tab label text color |
| `--tab-color-hover` | Tab label text on hover |
| `--tab-add-border` | New tab button border |

> **Note:** Monaco editor syntax highlighting and xterm.js terminal colors are configured separately in the main app's `themes.ts`. Shell themes (defined here) control the surrounding UI chrome only.

---

## Community Themes

Want to share your theme? See [`community/README.md`](community/README.md) and [`CONTRIBUTING.md`](CONTRIBUTING.md) for the full submission guide.

Community themes live in `community/` and are loaded alongside built-in themes at build time.

---

## Using This Repo in Your Build

This repository is consumed as a git submodule inside the main Binder app:

```
app/themes/  ← this repo
```

The frontend imports the root entry point:

```ts
// app/frontend/src/main.tsx
import '../../themes/index.scss'
```

Vite + sass compile the SCSS at build time — no runtime loading.

---

## License

MIT — see individual theme files for attribution where applicable.
