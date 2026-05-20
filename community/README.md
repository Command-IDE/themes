# Community Themes

This directory contains themes contributed by the cmdIDE community. Every theme here was submitted via pull request and reviewed by a maintainer.

## How to Submit a Theme

See [CONTRIBUTING.md](../CONTRIBUTING.md) for the full guide. The short version:

1. Create `_<your-github-handle>-<theme-name>.scss` in this directory
2. Add a `@use` line to `_index.scss` in alphabetical order
3. Open a pull request using the **Community Theme Submission** template

## Theme File Template

Save this as `community/_<handle>-<name>.scss`:

```scss
// THEME:       My Theme Name
// AUTHOR:      your-github-handle
// DESCRIPTION: One sentence about the theme's mood or inspiration
// VERSION:     1.0.0
// LICENSE:     MIT

[data-theme="your-github-handle-my-theme-name"] {
  --app-bg:               #000000;  /* Main app background */
  --border-color:         #111111;  /* Panel borders */
  --info-bar-bg:          #080808;  /* Status bar background */
  --info-bar-color:       #444444;  /* Status bar text */
  --info-bar-hover-bg:    #111111;  /* Status bar item hover bg */
  --info-bar-hover-color: #aaaaaa;  /* Status bar item hover text */
  --tab-color:            #444444;  /* Inactive tab text */
  --tab-color-hover:      #cccccc;  /* Tab text on hover */
  --tab-add-border:       #222222;  /* New-tab button border */
}
```

## Accepted Community Themes

| Key | Name | Author |
|-----|------|--------|
| *(none yet — be the first!)* | | |

---

> Want full Monaco editor and terminal color support for your theme? See the `themes.ts` contribution guide in the [main cmdIDE repo](https://github.com/Command-IDE/terminal-IDE).
