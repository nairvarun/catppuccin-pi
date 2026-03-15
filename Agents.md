# Theme Creation Guide for Pi-Agent

This document provides the information needed to create themes for pi-agent, with specific guidance for implementing Catppuccin-based themes.

---

## Pi-Agent Theme System

**Source:** https://github.com/badlogic/pi-mono/blob/main/packages/coding-agent/docs/themes.md

### Theme Locations

Pi loads themes from:
- Built-in: `dark`, `light`
- Global: `~/.pi/agent/themes/*.json`
- Project: `.pi/themes/*.json`
- Packages: `themes/` directories or `pi.themes` entries in `package.json`
- Settings: `themes` array with files or directories
- CLI: `--theme <path>` (repeatable)

### Theme Format

```json
{
  "$schema": "https://raw.githubusercontent.com/badlogic/pi-mono/main/packages/coding-agent/src/modes/interactive/theme/theme-schema.json",
  "name": "theme-name",
  "vars": {
    "primary": "#00aaff",
    "secondary": 242
  },
  "colors": {
    // All 51 required color tokens
  }
}
```

- `name` is required and must be unique
- `vars` is optional - define reusable colors here, then reference them in `colors`
- `colors` must define all 51 required tokens
- The `$schema` field enables editor auto-completion and validation

### Color Values

| Format | Example | Description |
|--------|---------|-------------|
| Hex | `"#ff0000"` | 6-digit hex RGB |
| 256-color | `39` | xterm 256-color palette index (0-255) |
| Variable | `"primary"` | Reference to a `vars` entry |
| Default | `""` | Terminal's default color |

### Required Color Tokens (51 total)

#### Core UI (11 colors)

| Token | Purpose |
|-------|---------|
| `accent` | Primary accent (logo, selected items, cursor) |
| `border` | Normal borders |
| `borderAccent` | Highlighted borders |
| `borderMuted` | Subtle borders (editor) |
| `success` | Success states |
| `error` | Error states |
| `warning` | Warning states |
| `muted` | Secondary text |
| `dim` | Tertiary text |
| `text` | Default text (usually `""`) |
| `thinkingText` | Thinking block text |

#### Backgrounds & Content (11 colors)

| Token | Purpose |
|-------|---------|
| `selectedBg` | Selected line background |
| `userMessageBg` | User message background |
| `userMessageText` | User message text |
| `customMessageBg` | Extension message background |
| `customMessageText` | Extension message text |
| `customMessageLabel` | Extension message label |
| `toolPendingBg` | Tool box (pending) |
| `toolSuccessBg` | Tool box (success) |
| `toolErrorBg` | Tool box (error) |
| `toolTitle` | Tool title |
| `toolOutput` | Tool output text |

#### Markdown (10 colors)

| Token | Purpose |
|-------|---------|
| `mdHeading` | Headings |
| `mdLink` | Link text |
| `mdLinkUrl` | Link URL |
| `mdCode` | Inline code |
| `mdCodeBlock` | Code block content |
| `mdCodeBlockBorder` | Code block fences |
| `mdQuote` | Blockquote text |
| `mdQuoteBorder` | Blockquote border |
| `mdHr` | Horizontal rule |
| `mdListBullet` | List bullets |

#### Tool Diffs (3 colors)

| Token | Purpose |
|-------|---------|
| `toolDiffAdded` | Added lines |
| `toolDiffRemoved` | Removed lines |
| `toolDiffContext` | Context lines |

#### Syntax Highlighting (9 colors)

| Token | Purpose |
|-------|---------|
| `syntaxComment` | Comments |
| `syntaxKeyword` | Keywords |
| `syntaxFunction` | Function names |
| `syntaxVariable` | Variables |
| `syntaxString` | Strings |
| `syntaxNumber` | Numbers |
| `syntaxType` | Types |
| `syntaxOperator` | Operators |
| `syntaxPunctuation` | Punctuation |

#### Thinking Level Borders (6 colors)

| Token | Purpose |
|-------|---------|
| `thinkingOff` | Thinking off |
| `thinkingMinimal` | Minimal thinking |
| `thinkingLow` | Low thinking |
| `thinkingMedium` | Medium thinking |
| `thinkingHigh` | High thinking |
| `thinkingXhigh` | Extra high thinking |

#### Bash Mode (1 color)

| Token | Purpose |
|-------|---------|
| `bashMode` | Editor border in bash mode (`!` prefix) |

### Hot Reload

When you edit the currently active custom theme file, pi reloads it automatically for immediate visual feedback.

---

## Catppuccin Style Guide

**Source:** https://github.com/catppuccin/catppuccin/blob/main/docs/style-guide.md

Catppuccin is a soothing pastel theme with 4 flavors: **Latte** (light), **Frappé**, **Macchiato**, and **Mocha** (darkest).

### General Usage Principles

> Text colors are guidelines, certain cases require deviations. Legibility always comes first.

### Background Colors

| Function | Colors |
|----------|--------|
| Background Pane | Base |
| Secondary Panes | Crust, Mantle |
| Surface Elements | Surface 0, Surface 1, Surface 2 |
| Overlays | Overlay 0, Overlay 1, Overlay 2 |

### Typography

| Function | Colors |
|----------|--------|
| Body Copy / Main Headline | Text |
| Sub-Headlines, Labels | Subtext 0, Subtext 1 |
| Subtle | Overlay 1 |
| On Accent | Base |
| Links, URLs | Blue |
| Success | Green |
| Warnings | Yellow |
| Errors | Red |
| Tags, Pills | Blue |
| Selection Background | Overlay 2 (20-30% opacity) |
| Cursor | Rosewater |

### Syntax Highlighting

| Syntax | Color |
|--------|-------|
| Keywords | Mauve |
| Strings | Green |
| Symbols, Atoms | Red |
| Escape Sequences, Regex | Pink |
| Comments | Overlay 2 |
| Constants, Numbers | Peach |
| Operators | Sky |
| Braces, Delimiters | Overlay 2 |
| Methods, Functions | Blue |
| Parameters | Maroon |
| Builtins | Red |
| Classes, Interfaces, Types | Yellow |
| Enum Variants | Teal |
| Property (e.g. JSON keys) | Blue |
| Attributes | Yellow |
| Macros | Rosewater |

### Terminals

| Element | Color |
|---------|-------|
| Cursor | Rosewater |
| Cursor Text | Base (Latte) / Crust (dark flavors) |
| Active Border | Lavender |
| Inactive Border | Overlay 0 |
| Bell Border | Yellow |

### Diff & Merge

| Function | Color |
|----------|-------|
| Diff Header | Blue |
| Index Metadata | Overlay 2 |
| File Path Markers | Pink |
| Hunk Header | Peach |
| Changed Text BG | Blue (10-20% opacity) |
| Inserted Text BG | Green (10-20% opacity) |
| Removed Text BG | Red (10-20% opacity) |

---

## Catppuccin Color Palette

**Source:** https://github.com/catppuccin/palette

### Accent Colors (14 colors)

These are the vibrant, saturated colors used for highlighting and emphasis.

| Name | Latte | Frappé | Macchiato | Mocha |
|------|-------|--------|-----------|-------|
| Rosewater | `#dc8a78` | `#f2d5cf` | `#f4dbd6` | `#f5e0dc` |
| Flamingo | `#dd7878` | `#eebebe` | `#f0c6c6` | `#f2cdcd` |
| Pink | `#ea76cb` | `#f4b8e4` | `#f5bde6` | `#f5c2e7` |
| Mauve | `#8839ef` | `#ca9ee6` | `#c6a0f6` | `#cba6f7` |
| Red | `#d20f39` | `#e78284` | `#ed8796` | `#f38ba8` |
| Maroon | `#e64553` | `#ea999c` | `#ee99a0` | `#eba0ac` |
| Peach | `#fe640b` | `#ef9f76` | `#f5a97f` | `#fab387` |
| Yellow | `#df8e1d` | `#e5c890` | `#eed49f` | `#f9e2af` |
| Green | `#40a02b` | `#a6d189` | `#a6da95` | `#a6e3a1` |
| Teal | `#179299` | `#81c8be` | `#8bd5ca` | `#94e2d5` |
| Sky | `#04a5e5` | `#99d1db` | `#91d7e3` | `#89dceb` |
| Sapphire | `#209fb5` | `#85c1dc` | `#7dc4e4` | `#74c7ec` |
| Blue | `#1e66f5` | `#8caaee` | `#8aadf4` | `#89b4fa` |
| Lavender | `#7287fd` | `#babbf1` | `#b7bdf8` | `#b4befe` |

### Base Colors (11 colors)

These are the muted colors used for backgrounds, text, and UI elements.

| Name | Latte | Frappé | Macchiato | Mocha |
|------|-------|--------|-----------|-------|
| Text | `#4c4f69` | `#c6d0f5` | `#cad3f5` | `#cdd6f4` |
| Subtext 1 | `#5c5f77` | `#b5bfe2` | `#b8c0e0` | `#bac2de` |
| Subtext 0 | `#6c6f85` | `#a5adce` | `#a5adcb` | `#a6adc8` |
| Overlay 2 | `#7c7f93` | `#949cbb` | `#939ab7` | `#9399b2` |
| Overlay 1 | `#8c8fa1` | `#838ba7` | `#8087a2` | `#7f849c` |
| Overlay 0 | `#9ca0b0` | `#737994` | `#6e738d` | `#6c7086` |
| Surface 2 | `#acb0be` | `#626880` | `#5b6078` | `#585b70` |
| Surface 1 | `#bcc0cc` | `#51576d` | `#494d64` | `#45475a` |
| Surface 0 | `#ccd0da` | `#414559` | `#363a4f` | `#313244` |
| Base | `#eff1f5` | `#303446` | `#24273a` | `#1e1e2e` |
| Mantle | `#e6e9ef` | `#292c3c` | `#1e2030` | `#181825` |
| Crust | `#dce0e8` | `#232634` | `#181926` | `#11111b` |

### Flavor Characteristics

| Flavor | Type | Description |
|--------|------|-------------|
| **Latte** 🌻 | Light | For light terminals and daytime use |
| **Frappé** 🍵 | Dark | Medium-dark, softer contrast |
| **Macchiato** 🌺 | Dark | Darker than Frappé, more saturated |
| **Mocha** 🌿 | Dark | Darkest, highest contrast - most popular |

---

## Creating a Catppuccin Theme for Pi-Agent

### Step 1: Choose a Flavor

Decide which Catppuccin flavor to implement:
- `catppuccin-latte` for light terminals
- `catppuccin-frappe` for medium-dark terminals
- `catppuccin-macchiato` for dark terminals
- `catppuccin-mocha` for dark terminals (most popular)

### Step 2: Create the Theme File

```bash
touch ~/.pi/agent/themes/catppuccin-mocha.json
```

### Step 3: Define Vars

Use Catppuccin color names as variables for easy reference:

```json
{
  "$schema": "https://raw.githubusercontent.com/badlogic/pi-mono/main/packages/coding-agent/src/modes/interactive/theme/theme-schema.json",
  "name": "catppuccin-mocha",
  "vars": {
    "rosewater": "#f5e0dc",
    "flamingo": "#f2cdcd",
    "pink": "#f5c2e7",
    "mauve": "#cba6f7",
    "red": "#f38ba8",
    "maroon": "#eba0ac",
    "peach": "#fab387",
    "yellow": "#f9e2af",
    "green": "#a6e3a1",
    "teal": "#94e2d5",
    "sky": "#89dceb",
    "sapphire": "#74c7ec",
    "blue": "#89b4fa",
    "lavender": "#b4befe",
    "text": "#cdd6f4",
    "subtext1": "#bac2de",
    "subtext0": "#a6adc8",
    "overlay2": "#9399b2",
    "overlay1": "#7f849c",
    "overlay0": "#6c7086",
    "surface2": "#585b70",
    "surface1": "#45475a",
    "surface0": "#313244",
    "base": "#1e1e2e",
    "mantle": "#181825",
    "crust": "#11111b"
  },
  "colors": {
    // Map pi-agent tokens to Catppuccin variables
  }
}
```

### Step 4: Map Tokens to Colors

Reference the Catppuccin Style Guide section above to map pi-agent's 51 color tokens to appropriate Catppuccin colors. Consider:

- **Semantic meaning**: Use Green for success, Red for errors, Yellow for warnings
- **Visual hierarchy**: Use Text, Subtext, and Overlay colors for different text prominence levels
- **Context**: Background colors should use Base, Mantle, Crust, and Surface variants
- **Syntax**: Follow Catppuccin's syntax highlighting conventions

### Step 5: Test and Iterate

1. Select the theme via `/settings`
2. Test with different message types, tool states, markdown content
3. Edit and rely on hot reload for immediate feedback

---

## References

- **Pi-Agent Theme Docs:** https://github.com/badlogic/pi-mono/blob/main/packages/coding-agent/docs/themes.md
- **Catppuccin Style Guide:** https://github.com/catppuccin/catppuccin/blob/main/docs/style-guide.md
- **Catppuccin Palette:** https://github.com/catppuccin/palette
- **Theme JSON Schema:** https://raw.githubusercontent.com/badlogic/pi-mono/main/packages/coding-agent/src/modes/interactive/theme/theme-schema.json
