# Contributing to cmdIDE Themes

Thank you for wanting to contribute a theme! This guide covers everything you need to submit a community theme or improve an existing one.

---

## Table of Contents

- [Types of Contributions](#types-of-contributions)
- [Submitting a Community Theme](#submitting-a-community-theme)
- [Theme File Format](#theme-file-format)
- [Naming Conventions](#naming-conventions)
- [Design Guidelines](#design-guidelines)
- [Testing Locally](#testing-locally)
- [Pull Request Checklist](#pull-request-checklist)
- [Reporting Bugs](#reporting-bugs)

---

## Types of Contributions

| Type | Where | How |
|------|-------|-----|
| New community theme | `community/` | Pull request |
| Fix a built-in theme | `built-in/` | Pull request with description of the issue |
| New built-in theme proposal | `built-in/` | Open a Theme Request issue first |
| Documentation improvement | Anywhere | Pull request |

---

## Submitting a Community Theme

### 1. Fork and clone

```bash
git clone https://github.com/<your-handle>/cmdide-themes
cd cmdide-themes
```

### 2. Create your theme file

Create a file in `community/` named `_<your-github-handle>-<theme-name>.scss`.

```
community/_jsmith-mocha.scss
```

See [Theme File Format](#theme-file-format) below for the required structure.

### 3. Register your theme

Open `community/_index.scss` and add a `@use` line for your theme, in alphabetical order by your handle:

```scss
// community/_index.scss
@use 'jsmith-mocha';  // ← add this line
```

### 4. Open a pull request

Use the **Community Theme Submission** PR template. Fill out all fields — incomplete submissions will be asked to revise before review.

---

## Theme File Format

Every theme file must follow this structure exactly:

```scss
// THEME: My Mocha Theme
// AUTHOR: jsmith
// DESCRIPTION: A warm, coffee-inspired dark theme
// VERSION: 1.0.0
// LICENSE: MIT

[data-theme="jsmith-mocha"] {
  --app-bg:               #2c1f14;
  --border-color:         #3e2b1a;
  --info-bar-bg:          #332416;
  --info-bar-color:       #6e4e34;
  --info-bar-hover-bg:    #3e2b1a;
  --info-bar-hover-color: #c8966a;
  --tab-color:            #6e4e34;
  --tab-color-hover:      #d4a87a;
  --tab-add-border:       #4a3020;
}
```

### Required CSS Custom Properties

All nine properties are required. Missing any will cause the theme to render incorrectly.

| Property | Description | Tips |
|----------|-------------|------|
| `--app-bg` | Main app background | Should be the darkest surface |
| `--border-color` | Panel and component borders | Subtle — slightly lighter than `--app-bg` |
| `--info-bar-bg` | Status bar background | Often same as or close to `--app-bg` |
| `--info-bar-color` | Status bar text | Should be readable but subdued |
| `--info-bar-hover-bg` | Status bar hover background | Slightly lighter than `--info-bar-bg` |
| `--info-bar-hover-color` | Status bar hover text | More prominent than `--info-bar-color` |
| `--tab-color` | Inactive tab text | Muted; can match `--info-bar-color` |
| `--tab-color-hover` | Tab text on hover | Lighter/brighter than `--tab-color` |
| `--tab-add-border` | New-tab button border | Subtle separator |

### Header Comment Block

The comment block at the top of each file is parsed by tooling. Use exact keys:

```
// THEME:       Display name of the theme
// AUTHOR:      Your GitHub handle (no @)
// DESCRIPTION: One sentence describing the theme
// VERSION:     Semantic version starting at 1.0.0
// LICENSE:     SPDX license identifier (MIT, Apache-2.0, etc.)
```

---

## Naming Conventions

### Theme key (the `data-theme` value)

- Format: `<author-handle>-<theme-name>` — all lowercase, hyphens only
- Examples: `jsmith-mocha`, `acme-pastel-light`, `kp-gruvbox-soft`
- Must be globally unique — check existing files before picking a name
- Built-in themes use their name directly (no author prefix): `minimal`, `nord`, etc.

### File name

- Format: `_<author-handle>-<theme-name>.scss`
- Must match the `data-theme` key exactly (with `_` prefix and `.scss` extension)

---

## Design Guidelines

These are guidelines, not hard rules. Reviewers will flag obvious accessibility issues.

- **Contrast ratio**: Aim for at least 3:1 between text colors and their backgrounds (WCAG AA for large text). Check with [WebAIM Contrast Checker](https://webaim.org/resources/contrastchecker/).
- **Hover states**: `--info-bar-hover-bg` and `--info-bar-hover-color` should be visibly distinct from their non-hover counterparts.
- **Borders**: `--border-color` should be subtle but visible — avoid making it identical to `--app-bg`.
- **Dark themes only**: Currently the app layout is built for dark backgrounds. Light theme support may come later.
- **Originality**: Don't submit a near-identical copy of an existing theme. Minor tweaks to built-ins belong in an issue or a fork.

---

## Testing Locally

To preview your theme inside cmdIDE before submitting:

1. Clone the main [cmdIDE repo](https://github.com/Command-IDE/terminal-IDE)
2. The `app/themes/` directory is this repo (as a submodule) — replace or symlink it with your fork
3. Run the Wails dev server:
   ```bash
   cd app
   wails dev
   ```
4. Open Settings → Theme and type your theme key into the custom theme editor, or temporarily add your key to `themes.ts` to make it appear in the preset list
5. Verify all UI surfaces look correct: app background, borders, tabs, info bar, hover states

---

## Pull Request Checklist

Before submitting, confirm all of the following:

- [ ] File is in `community/` and named `_<handle>-<name>.scss`
- [ ] `[data-theme]` key matches the file name (minus `_` and `.scss`)
- [ ] All nine CSS custom properties are defined
- [ ] Header comment block is complete (THEME, AUTHOR, DESCRIPTION, VERSION, LICENSE)
- [ ] `@use` line added to `community/_index.scss` in alphabetical order
- [ ] Theme tested locally in the running app
- [ ] Contrast ratios checked
- [ ] No copying of another theme with only trivial color shifts

---

## Reporting Bugs

Use the **Bug Report** issue template for problems with existing themes (wrong colors, missing variables, rendering issues). Include:

- Which theme and which version of cmdIDE
- A screenshot showing the problem
- The expected vs actual appearance
