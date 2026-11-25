# AE Comic Text Bubble

> **Parametric Comic & Speech Balloon Generator with Drag & Drop Tail Targeting, Advanced Text Wrapping, and Dynamic Transitions for Adobe After Effects.**  
> *Co-authored & architected with Google DeepMind Antigravity for `work2survive` motion graphics ecosystems.*

[![Live Web Demo](https://img.shields.io/badge/Live%20Demo-AE%20JS%20Builder-4183C4?style=for-the-badge&logo=adobeaftereffects&logoColor=white)](https://work2survive.github.io/AE_JS_builder/?jsx=AE_Comic_Text_Bubble.jsx&autobuild=true)
[![Adobe After Effects](https://img.shields.io/badge/AE-CS6%20to%202026%2B-9999FF?style=for-the-badge&logo=adobe&logoColor=white)](https://www.adobe.com/products/aftereffects.html)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg?style=for-the-badge)](https://opensource.org/licenses/MIT)
[![Built with Antigravity](https://img.shields.io/badge/Built%20With-Antigravity-4285F4?style=for-the-badge&logo=google)](https://deepmind.google/)

---

## 🚀 Live Interactive Demo

Experience **AE Comic Text Bubble** directly in your browser without launching After Effects:

👉 **[Launch Live Web Simulator](https://work2survive.github.io/AE_JS_builder/?jsx=AE_Comic_Text_Bubble.jsx&autobuild=true)**

---

## 📖 Overview

Creating authentic comic speech balloons in Adobe After Effects has traditionally been a painful, manual process:
- Drawing shape layers manually and constantly readjusting tails when dialogue changes.
- Text overflow causing words to collide with balloon borders.
- Ungainly line wrapping with dangling words, widows, and orphans.
- Seams or stroke mismatches where the tail joins the balloon.
- Difficulty animating speech bubbles popping in from the speaker's mouth.

**`AE Comic Text Bubble`** unifies four core `work2survive` technologies into a single production ScriptUI panel:
1. **[AE-advanced-text-wrap](https://github.com/work2survive/AE-advanced-text-wrap)**: Knuth-Plass dynamic programming paragraph composer, 5 wrapping methods, and micro-typographic bindings.
2. **[AE-replace-color-emojis](https://github.com/work2survive/AE-replace-color-emojis)**: Comic emoji palette insertion bar and full Unicode emoji / emoticon parsing.
3. **[AE-Text-Highlight](https://github.com/work2survive/AE-Text-Highlight)**: Sub-pixel typography bounding box measurement and word highlight accents.
4. **[AE-Align-AnchorPoint](https://github.com/work2survive/AE-Align-AnchorPoint)**: Zero-shift invariant anchor compensation and tail-origin growth scaling.

```
+-------------------------------------------------------------+
|                     COMIC SPEECH BALLOON                    |
|  ( )  POW! 💥 That was incredible! What do we do next?      |
|   \                                                         |
|    \                                                        |
|     \                                                       |
|     [🎯 Tail Target] (Drag & drop anywhere on comp canvas)   |
+-------------------------------------------------------------+
```

---

## 🌟 Key Features

### 1. 💬 Starting from Any Text Layer (Non-Destructive & Reversible)
- **Automatic Contextual Detection**: Select any existing text layer in your active composition, and the panel automatically extracts its dialogue and styling.
- **Pristine Property Backup**: Stores original text string, font size, font family, position, anchor point, scale, and rotation in a dedicated `AE Comic Bubble State` effect.
- **One-Click Revert**: Click `↩ Revert to Original Text Layer` at any time to remove the generated bubble and target null, cleanly restoring your original text layer.

### 2. 📐 Advanced Typographic Text Wrapping
- **5 Wrap Methods**:
  - **Balanced Knuth-Plass**: Evaluates all candidate line breaks across the entire paragraph to minimize raggedness variance and balance line lengths.
  - **Greedy First-Fit**: Polished standard wrapping up to target width.
  - **Optical Pyramid**: Expanding lines centered gracefully (ideal for quotes, cards, and punchy dialogue).
  - **Reverse Pyramid**: Top-heavy headline style tapering downwards.
  - **Compact Block**: Maximum density within maximum pixel bounds.
- **Micro-Typographic Rules**: Non-breaking spaces (NBSP) prevent dangling prepositions, bind numbers to units (`100 px`, `50 %`), prevent widows & orphans, and strip manual breaks (`\r`, `\n`).
- **Multilingual Hyphenation**: English, Spanish, French, German, Italian, and Universal grammar syllable segmentation.

### 3. 💥 Comic Emoji Quick Insertion Bar
- Integrated one-click emoji insertion buttons:
  `[💥 POW]` `[💬 SAY]` `[🗯️ SHOUT]` `[⚡ ZAP]` `[💡 IDEA]` `[❤️ LOVE]` `[❓ WHAT]` `[❗ HEY]` `[💣 BOOM]` `[💤 ZZZ]`
- Click any button to insert the symbol directly into your speech text.

### 4. 🗯️ 6 Balloon Body Presets
| Preset | Visual Shape | Ideal Use Case |
| :--- | :--- | :--- |
| **Classic Speech Oval** | Smooth elliptical curve | Standard dialogue, narrative dialogue |
| **Modern Rounded Rect** | Pill / Box with customizable corner radii | Modern graphic novels, comics, subtitles |
| **Action / Shout Burst** | Spiky jagged explosion balloon | Screams, sound effects, action bursts (POW! BOOM!) |
| **Thought Cloud** | Puffy scalloped cloud arcs | Inner monologues, dreams, contemplation |
| **Whisper Bubble** | Dashed outline rounded bubble | Whispers, secretive dialogue, soft speech |
| **Golden Age Caption Box** | Crisp rectangular box ($R=0$) | Narrator captions, timecards, comic boxes |

### 5. ⚡ 7 Tail Style Presets
- **Curved Hook / Horn**: Classic comic tail with smooth inward Bézier curvature pointing towards the speaker.
- **Straight Cone / Triangle**: Direct crisp triangular speech pointer.
- **Wide Speech Wedge**: Sturdy, broad-base dialogue wedge.
- **Thought Bubbles**: Chain of 3 diminishing circles leading from the cloud to the thinker.
- **Lightning / Electric Bolt**: 3-segment jagged zigzag tail for robots, radio broadcasts, phone calls, and electronic screams.
- **Scream Spike**: Exaggerated, needle-sharp action barb.
- **None**: Floating bubble or caption box without tail.

### 6. 🎯 Drag & Drop Tail Placement Target
- **In-Comp Null Controller**: Automatically creates a dedicated `"🎯 Tail Target"` null layer in your After Effects composition. Drag the null handle directly in the AE comp viewer to point the tail at any character's mouth interactively!
- **Interactive In-Panel 2D Target Pad**: Visual pad with a draggable target crosshair.
- **3x3 Quick Direction Matrix**:
  `[ ↖ Top-Left ]` `[ ↑ Top-Center ]` `[ ↗ Top-Right ]`  
  `[ ← Mid-Left ]` `[ 🎯 Center ]`    `[ → Mid-Right ]`  
  `[ ↙ Bot-Left ]` `[ ↓ Bot-Center ]` `[ ↘ Bot-Right ]`  
- **Precision Sliders**: Tail Angle (`-180°` to `+180°`) and Tail Distance (`20` to `350 px`).

### 7. 🎨 Color Pickers & Comic Palettes
- **Background Fill Color**: Hex text box + Clickable Color Swatch (compatible with `windows-color-picker.js` and native AE picker).
- **Stroke Outline Color**: Hex text box + Clickable Color Swatch.
- **Stroke Width**: `0` to `30 px` bold comic line control with round cap & join.
- **Quick Comic Themes**: Instant 1-click theme palettes:
  - **Classic**: Pure White fill (`#FFFFFF`), Solid Black stroke (`#000000`)
  - **Action**: Vibrant Yellow fill (`#FFE600`), Jet Black stroke (`#111111`)
  - **Hero**: Electric Cyan fill (`#00E5FF`), Midnight Navy stroke (`#1A237E`)
  - **Manga**: Charcoal Dark fill (`#18181B`), Crisp White stroke (`#FFFFFF`)

### 8. 🎬 Dynamic Animation In & Out Transitions
- **Entrance (In) Presets**:
  - **Pop & Comic Bounce**: Elastic overshoot (`0%` $\to$ `118%` $\to$ `96%` $\to$ `100%`).
  - **Elastic Zoom In**: High-energy explosive comic zoom.
  - **Whip & Slide In**: Snappy slide from the tail direction with bounce.
  - **Smooth Fade & Scale**: Modern clean transition.
  - **None (Static)**: Bubble starts visible immediately.
- **Exit (Out) Presets**:
  - **Pop / Shrink Out**: Anticipation scale bump (`108%`) then rapid snap down to `0%`.
  - **Fade & Float Out**: Drifts upwards 25px while fading to `0%` opacity.
  - **Comic Puff / Dissolve**: Quick puff scale expansion and dissolve.
  - **None**: Stays indefinitely.
- **Animate from Tail Origin**: When enabled, the bubble's transform anchor point is automatically locked to the tail tip so the balloon scales and blows up directly from the speaker's mouth!

---

## 📦 Installation & Usage

### Option 1: Dockable ScriptUI Panel (Recommended)
1. Download [`AE_Comic_Text_Bubble.jsx`](AE_Comic_Text_Bubble.jsx).
2. Copy `AE_Comic_Text_Bubble.jsx` into your After Effects ScriptUI Panels directory:
   - **Windows**: `C:\Program Files\Adobe\Adobe After Effects <Version>\Support Files\Scripts\ScriptUI Panels\`
   - **macOS**: `/Applications/Adobe After Effects <Version>/Scripts/ScriptUI Panels/`
3. Restart After Effects.
4. In After Effects, open the **Window** menu and select **`AE_Comic_Text_Bubble.jsx`**.
5. Dock the panel anywhere in your workspace!

### Option 2: Run via File Menu
1. In After Effects, navigate to **File > Scripts > Run Script File...**
2. Select `AE_Comic_Text_Bubble.jsx`.

---

## 📐 Mathematical Architecture

### 1. Zero-Shift Anchor Point Invariance
The relationship between layer space $\mathbf{x}_{\text{layer}}$, anchor point $\mathbf{A}$, layer position $\mathbf{P}$, rotation $\mathbf{R}(\theta)$, and scale $\mathbf{S}$ adheres to:
$$\mathbf{X}_{\text{comp}} = \mathbf{P} + \mathbf{R}(\theta) \cdot \mathbf{S} \cdot (\mathbf{x}_{\text{layer}} - \mathbf{A})$$

When repositioning the anchor point to the tail origin $\mathbf{A}_{\text{target}}$:
$$\mathbf{P}_{\text{new}} = \mathbf{P}_{\text{base}} + \mathbf{R}(\theta) \cdot \mathbf{S} \cdot (\mathbf{A}_{\text{target}} - \mathbf{A}_{\text{base}})$$
This guarantees zero visual drift of layer content regardless of scale or rotation.

### 2. Seamless Bézier Tail Welding
The tail connects to the bubble body perimeter at two base vertices $B_1$ and $B_2$ spanning angle:
$$\Delta\theta = \frac{W_{\text{base}}}{2 \cdot R_{\text{mean}}}$$
For curved hook tails, control points $C_1, C_2$ incorporate inward normal vectors $\mathbf{n}_{\perp}$:
$$\mathbf{n}_{\perp} = \left(-\frac{v_y}{\|\mathbf{v}\|}, \frac{v_x}{\|\mathbf{v}\|}\right) \cdot \kappa_{\text{curvature}}$$
creating a single continuous, airtight cubic Bézier path with zero stroke overlaps.

---

## 🔗 Related Repositories

- **[AE JS Builder](https://github.com/work2survive/AE_JS_builder)**: Agnostic browser-based After Effects 2D/3D & ScriptUI simulator.
- **[AE Advanced Text Wrap](https://github.com/work2survive/AE-advanced-text-wrap)**: Knuth-Plass dynamic paragraph composer and typography optimizer.
- **[AE Replace Color Emojis](https://github.com/work2survive/AE-replace-color-emojis)**: OpenMoji & Twemoji vector shape replacement engine.
- **[AE Text Highlight](https://github.com/work2survive/AE-Text-Highlight)**: Procedural typography word and bounding box highlighter.
- **[AE Align Anchor Point](https://github.com/work2survive/AE-Align-AnchorPoint)**: Zero-shift anchor point alignment utility.

---

## 💖 Support / Sponsor

If you find this tool helpful in your motion design workflow:

[![Sponsor work2survive](https://img.shields.io/badge/Sponsor-%E2%9D%A4-ea4aaa?style=for-the-badge&logo=github)](https://github.com/sponsors/work2survive)

---

## 📄 License

Released under the [MIT License](LICENSE). Copyright © 2026 Manuel Campagnoli.
