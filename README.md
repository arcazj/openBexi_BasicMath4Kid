# 3D Math Playground for kids

## Live Demo

[Live Demo](https://arcazj.github.io/openBexi_BasicMath4Kid/index.html)


An all-in-one HTML file that uses **Three.js r176** to teach 5-year-olds the four basic arithmetic operations with shiny metallic cubes.  
No build tools, no external assets—just copy, open, and play.

---

## ✨ Features

| Category | Details |
|----------|---------|
| **One-file deploy** | HTML + CSS + JS embedded in a single file |
| **Operations** | Addition • Subtraction • Multiplication • Division |
| **Kid-safe logic** | Operands randomly chosen 0–9 • Result never > 18 |
| **Interactive keypad** | 4 × 5 grid (0–18) with green/red feedback, 😊/😕 emoji |
| **Languages** | English (default), Français, Español |
| **Graphics** | Metallic cubes, HDR room environment, ACES tone-mapping |
| **Responsive UI** | Scrollable/wrapping control panel for phones & desktops |

---

## 📥 Installation

1. Clone or download this repo.
2. Open `math-playground.html` in any modern browser (Chrome, Edge, Firefox, Safari).  
   *No local server required—CDN imports handle Three.js.*

---

## 🕹️ Usage

1. Pick a **language** (top row).
2. Click a blue **operation** button.
3. Watch the cubes animate the question.
4. When the keypad lights up, tap your answer (0–18).
5. Key turns **green** and shows 😊 if correct, **red** and 😕 if wrong.
6. Choose another operation to try again!

---

## 🛠️ Tech Stack

- **Three.js r176** (module build)
- `RoomEnvironment` & `OrbitControls` from `three/examples/jsm/`
- Plain CSS (no framework)
- No build step / bundler

---

## 🔧 Customization

| What | Where |
|------|-------|
| Palette / fonts | Edit CSS variables in the `<style>` block |
| Operand range   | `demoAdd`, `demoSub`, `demoMul`, `demoDiv` functions |
| Keypad layout   | `grid-template-columns` & `--btn-w` in keypad CSS |
| Extra languages | Extend the `TXT` object in the script |

---

## 🖼️ Screenshots

| Operation | Preview |
|-----------|---------|
| Addition  | ![Addition demo](docs/screenshots/add.png) |
| Subtraction | ![Subtraction demo](docs/screenshots/sub.png) |

*(Screenshots optional; add your own to `/docs/screenshots/` for GitHub Pages readme rendering.)*

---

## 🤝 Contributing

Pull requests are welcome—feel free to fix bugs, improve animations, or add new learning modes.  
Open an issue first to discuss major changes.

---

## 🤝 Full chatGPT Prompt (for reproducibility)
Create a single, fully self-contained HTML file (no external CSS/JS aside from the CDN imports below) that implements an interactive “Math Playground” for 5-year-olds.

1  General Requirements• Everything—HTML structure, CSS, JS—must live in one file.• Use Three.js r176 ES-modules through this exact import map:

<script type="importmap">
{
  "imports": {
    "three":         "https://unpkg.com/three@0.176.0/build/three.module.js",
    "three/addons/": "https://unpkg.com/three@0.176.0/examples/jsm/"
  }
}
</script>

• Do not create global variables except THREE; keep code modular.• Must run offline once copied to disk.

2  UI Layout (responsive)• Left (or top on small screens): a control panel #controls– Width ≈ 340 px, rounded right edge, scrollable if taller than viewport.– Sections (from top to bottom):

Language row – three buttons (“English”, “Français”, “Español”), with active-state highlight.

Operation buttons – four big buttons (“Addition, Subtraction, Multiplication, Division”); exactly one can be active at a time.

Equation banner – black background, white 2 rem text, centred (#equation).

Prompt text – single-line instruction beneath the equation.

Keypad – 4 columns × 5 rows grid of square buttons (0-18) plus one invisible spacer in the 20th cell.• Right (or below): full-size WebGL canvas (#sceneContainer) for Three.js.

3  Visual & Style Details• Colour palette already chosen in CSS variables; keep existing values.• Keypad button states:

.key-btn          { background: var(--yellow); color: var(--navy); }
.key-btn.correct  { background:#10984d; color:#fff; }
.key-btn.wrong    { background:#d60709; color:#fff; }
.key-btn:disabled { opacity:.75; cursor:not-allowed; }

• Cubes must look metallic and reflective:– Use MeshPhysicalMaterial with metalness:1, roughness:0.05, clearcoat:0.3, etc.– Add a RoomEnvironment HDR and enable physicallyCorrectLights, ACESFilmicToneMapping, renderer.outputColorSpace = SRGB.• Scene lighting: one directional key light, one ambient light, one rim point light.

4  Game Logic• Operands are random 0 – 9.• Regenerate until the result is ≤ 18 for every operation.• Operations behave visually:– Addition: two coloured rows slide together (no overlap).– Subtraction: last b cubes blink then vanish.– Multiplication: a × b grid scales up from zero.– Division: total cubes split into equal groups that slide apart.• Animation ends before the keypad is unlocked.• Kid taps a keypad number to answer:– Correct → button turns green and “😊” appended to equation.– Wrong   → button turns red   and “😕” appended.– All keys disable after first tap.

5  Internationalisation• Texts (operation names, prompt, default “Pick an operation!” message) must switch instantly on language-button click.• Use the provided English/French/Spanish strings.

6  Accessibility / UX• Buttons require only left-click/tap.• Control panel must remain usable on small screens (wrap into top bar).• All interactive elements should have obvious hover / active cues.

Deliverable: the complete <html> file implementing all of the above—no commentary, no missing pieces.

---

## 📜 License

This project is licensed under the **MIT License**.

