# AE Comic Text Bubble (v2.0.0)

> **Ground-Up Parametric Comic Balloon Generator for Adobe After Effects — Combining Zero-Shift Precomposition, Center Anchor Alignment, Trim-Paths-Style Tail Targeting, and Full Preset Management.**  
> *Co-authored & architected with Google DeepMind Antigravity for `work2survive` motion graphics ecosystems.*

[![Live Web Demo](https://img.shields.io/badge/Live%20Demo-AE%20JS%20Builder-4183C4?style=for-the-badge&logo=adobeaftereffects&logoColor=white)](https://work2survive.github.io/AE_JS_builder/?jsx=AE_Comic_Text_Bubble.jsx&autobuild=true)
[![Adobe After Effects](https://img.shields.io/badge/AE-CS6%20to%202026%2B-9999FF?style=for-the-badge&logo=adobe&logoColor=white)](https://www.adobe.com/products/aftereffects.html)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg?style=for-the-badge)](https://opensource.org/licenses/MIT)

---

## Live Interactive Demo

Test **AE Comic Text Bubble** directly in your browser without opening After Effects:

**[Launch Live Web Simulator](https://work2survive.github.io/AE_JS_builder/?jsx=AE_Comic_Text_Bubble.jsx&autobuild=true)**

---

## Overview & Ecosystem Architecture

**`AE Comic Text Bubble`** grabs any existing Point Text or Paragraph (Box) Text layer and builds a clean, parametric vector comic balloon around it.

Built from the ground up upon:
- **[AE-text-precomp](https://github.com/work2survive/AE-text-precomp)**: Zero-shift precomposition (`"comic balloon <HEX>"`, enabled by default) with symmetric non-clipping exterior bounds that comfortably fit tails, spikes, and thick strokes.
- **[AE-Align-AnchorPoint](https://github.com/work2survive/AE-Align-AnchorPoint)**: Automatically places both the Text Box and Balloon Anchor Points at the exact horizontal & vertical center (`[centerX, centerY]`) without shifting content on screen, linking the Balloon as a direct child of the Text Layer.

### Seamless Compatibility with Sibling Text Tools
Text layers can be freely combined with:
- **[AE-replace-color-emojis](https://github.com/work2survive/AE-replace-color-emojis)** — Preserves child vector emoji layers in front of text and compensates local offsets during anchor centering & precomposing.
- **[AE-advanced-text-wrap](https://github.com/work2survive/AE-advanced-text-wrap)** — Preserves wrapped paragraph structure and non-destructive wrap effects.
- **[AE-Text-Highlight](https://github.com/work2survive/AE-Text-Highlight)** — Keeps word highlight layers tucked between the text and the comic balloon background.

---

## Key Features & UI Organization

### 1. Top Bar: Full Preset Management
Manage reusable comic styles right at the top of the panel:
- **Store**: Save current balloon, tail, and appearance settings under a custom name.
- **Rename**: Rename any existing preset in place.
- **Delete**: Remove unwanted presets cleanly.
- **Open**: Import single-preset or multi-preset `.json` files from disk.
- **Download**: Export/download the selected preset as a portable `.json` file.

### 2. Tab 1 — `Balloon` (Geometry & Exterior Padding)
- **4 Parametric Balloon Geometries**:
  - **Square**: Crisp comic caption / sharp rectangular dialogue box.
  - **Rounded Corners**: Exact cubic Bézier rounded rectangle with adjustable **Corner Radius**.
  - **Cloud Shape (Thoughts)**: Scalloped comic cloud perimeter with configurable **Cloud Puffs** and **Puff Depth** (guaranteed never to clip text corners).
  - **Explosion / Shout**: High-energy radial comic starburst with configurable **Burst Spikes** and **Spike Length**.
- **Exterior Padding (`Padding X`, `Padding Y`)**: Expands balloon space around the rendered text bounds while keeping both the Text Box and Balloon Anchor Points centered horizontally & vertically.

### 3. Tab 2 — `Tail` (Styles & Trim-Paths Perimeter Targeting)
Every tail style works with **any** balloon geometry regardless of preset:
- **5 Tail Styles**:
  - **None**: Closed standalone balloon / caption box.
  - **Line**: Single comic pointer line from the perimeter to the tail target.
  - **Triangle Sharp**: Seamless sharp speech wedge spliced directly into the balloon perimeter (zero internal seam line).
  - **Lightning Shaped**: Non-self-intersecting zig-zag radio/electronic comic bolt spliced seamlessly into the balloon perimeter.
  - **Thinking Clouds**: Chain of diminishing circular cloud puffs leading toward the thinker.
- **Trim-Paths-Style Perimeter Placement**:
  - **Start (%)**, **End (%)**, and **Offset (°)** (`0%` = Top, `25%` = Right, `50%` = Bottom, `75%` = Left) with exact arc-length parameterization and De Casteljau cubic Bézier splitting.
  - Includes a live interactive **Perimeter Preview Widget** + quick edge snap buttons (`Top 0%`, `Right 25%`, `Bot 50%`, `Left 75%`, `Bot-L 56%`, `Bot-R 44%`).
  - **Tail Length (px)** & **Tip Slant (°)** target controls.

### 4. Tab 3 — `Appearance` (Fill, Stroke Styles & Color Pickers)
- **Line / Stroke Styles**:
  - **None**: Fill-only balloon without outline.
  - **Solid**: Classic uniform comic ink outline (**Thickness**).
  - **Variable Thickness**: Dynamic comic brush stroke tapering smoothly between **Min Thickness** and **Max Thickness** (`ADBE Vector Taper`).
  - **Dotted (Whisper)**: Rounded whisper dots/dashes with configurable **Thickness** and **Dot Spacing** (`ADBE Vector Stroke Dashes`).
- **Color Pickers**: Interactive color swatch + hex input for both **Fill Color** (with enable toggle & opacity) and **Stroke Color**.

### 5. Bottom Bar — Precomp, Idempotent Build / Update & Full Reversal
- **Make Precomp (`"comic balloon <HEX>"`)**: Checked by default (`true`). Precomposes the centered Text Layer + linked Balloon child (and any attached Emoji / Highlight layers) into an isolated precomposition named `"comic balloon " + 4-digit HEX`. Uncheck at any time to keep or unpack layers directly in the main composition.
- **Original State Stored in Effects**: Pristine text content, box properties, and original Transform (`Position`, `Anchor Point`, `Scale`, `Rotation`) are stored in Effect Controls (`Comic Balloon State`, `CB Orig Position`, `CB Orig Anchor`, `CB Orig Scale`, `CB Orig Rotation`, `CB Orig Box Size`).
- **Build / Update Balloon**: Creates a new balloon or updates an existing balloon / precomp in place without visual drift.
- **Remove Balloon**: Reverses the entire operation — unpacks the precomp (if precomposed), deletes the balloon, removes state effects, and restores the original text box, content, and transform properties.

---

## Installation

1. Copy [`AE_Comic_Text_Bubble.jsx`](AE_Comic_Text_Bubble.jsx) into your After Effects `ScriptUI Panels` folder:
   - **Windows**: `C:\Program Files\Adobe\Adobe After Effects <Version>\Support Files\Scripts\ScriptUI Panels\`
   - **macOS**: `/Applications/Adobe After Effects <Version>/Scripts/ScriptUI Panels/`
2. Restart After Effects and open **Window > AE_Comic_Text_Bubble.jsx**, or run directly via **File > Scripts > Run Script File...**.

---

## License

MIT License — Part of the [`work2survive`](https://github.com/work2survive) After Effects procedural tools suite.
