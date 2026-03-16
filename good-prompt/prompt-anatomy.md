# Prompt Anatomy — Good Prompt

> This file breaks down **why** each line of this prompt produced an on-brand, precise result.
> Use it alongside `good-prompt.html` to trace every design decision back to the prompt.

---

## The Prompt

```
"Act as a Lead UI Designer. Create a high-fidelity landing page layout
for 'Reatcurly,' a gourmet hot dog brand, strictly following these
brand guidelines:

1. Visual Palette:
   - Primary Background: Off White (#FFFDF2).
   - Hero Section: Solid Yellow (#FFD706).
   - Typography: Use 'F37 Gruffy Medium' for main headlines and 'FT Polar
     Regular' for body text (fallback to Roboto/Roboto Mono). All text in
     Off Black (#0D0D0B).

2. Component Styling:
   - Primary CTA: Background Tangerine (#FF8200) with Off Black text.
   - Icons: Use rounded, curvy 'Phosphor' style icons.
   - Accents: Incorporate Recurly's signature 'fluid, curvy yellow linework'
     to frame sections. Do not use closed shapes.

3. Layout & Content:
   - Follow a strict hierarchy: Eyebrow (All caps) -> Headline (Sentence
     case) -> Body -> CTA.
   - Ensure a left-aligned layout with significant whitespace.
   - Hero Image: A warm, unposed lifestyle photo of people eating hot dogs
     outdoors, using the 'repeating scale' (X, X/2, X/4) photo treatment.

4. Tone: Energetic, warm, and precise. Avoid traditional 'fast food'
   red; stick to the Tangerine/Yellow/Off-White sophistication."

Use the sources on public as needed.
```

---

## Line-by-Line Breakdown

### `"Act as a Lead UI Designer"`
**Technique: Role injection.**
Assigning a specific role shifts the model's perspective and vocabulary. A "Lead UI Designer" thinks about design systems, hierarchy, and brand consistency — not just "making something pretty." It also implies seniority: this person won't take shortcuts or use placeholder emoji.

> **Effect on output:** The model structured CSS with design tokens (`:root` variables), used a spacing scale, and organized components as a real design system.

---

### `"Create a high-fidelity landing page layout"`
**Technique: Output format specification.**
"High-fidelity" signals the model should produce polished, production-ready output — not a wireframe or a rough draft. "Landing page layout" defines the document type and implied sections.

---

### `"strictly following these brand guidelines"`
**Technique: Constraint framing.**
The word "strictly" removes creative latitude. The model is no longer interpreting guidelines — it's implementing them. This shifts its mode from creative generation to constrained execution.

---

### `"Primary Background: Off White (#FFFDF2)"`
**Technique: Hex code over adjective.**
"Off white" alone is still vague. The hex code `#FFFDF2` is unambiguous. The model cannot substitute a different white — there is only one valid answer.

> **Effect on output:** `background: var(--off-white)` → `#FFFDF2` throughout. No guessing.

---

### `"Hero Section: Solid Yellow (#FFD706)"`
**Technique: Component-scoped color assignment.**
Instead of just listing colors, this maps each color to a specific component. The model knows exactly where each color belongs — it doesn't have to decide.

> **Effect on output:** `.hero { background: var(--yellow) }` — the hero is visually distinct and on-brand.

---

### `"fallback to Roboto/Roboto Mono"`
**Technique: Graceful degradation instruction.**
The brand fonts (F37 Gruffy, FT Polar) aren't on Google Fonts. By specifying fallbacks, the prompt ensures the output is still usable without the paid fonts, while preserving the intended typographic rhythm.

> **Effect on output:** CSS font stacks load via Google Fonts with the correct fallbacks. The page renders correctly in any browser.

---

### `"Do not use closed shapes"`
**Technique: Negative constraint.**
Telling the model what NOT to do is as powerful as telling it what to do. Without this, curvy accents default to circles, ovals, or blobs — all closed shapes. "Do not use closed shapes" forces the model to use open linework (arcs, waves, sweeping curves).

> **Effect on output:** SVG decorators in the HTML use `path` elements with open strokes — no `fill`, no closed loops.

---

### `"Eyebrow (All caps) → Headline (Sentence case) → Body → CTA"`
**Technique: Explicit content hierarchy.**
This defines the exact reading order and typographic treatment for every content block. The model doesn't have to guess whether a section should start with a headline or a subhead.

> **Effect on output:** Every section follows the pattern: small all-caps label → large headline → paragraph → button. Consistent across the entire page.

---

### `"left-aligned layout with significant whitespace"`
**Technique: Layout intent, not decoration.**
"Left-aligned" prevents the default centered-everything pattern. "Significant whitespace" gives the model permission to use large padding and not fill every pixel — a common failure mode in AI-generated layouts.

> **Effect on output:** Text blocks are left-aligned. Spacing uses the `--sp-xl / --sp-lg / --sp-md` scale (96/48/24px). The layout breathes.

---

### `"repeating scale (X, X/2, X/4) photo treatment"`
**Technique: System reference.**
Naming a specific design system pattern (a scaling grid for image sizes) gives the model a precise rule to follow rather than an aesthetic vibe to approximate.

---

### `"Avoid traditional 'fast food' red"`
**Technique: Explicit avoidance with category context.**
This doesn't just say "don't use red." It explains *why* — red is a fast food cliché. This gives the model enough context to apply the rule to edge cases (what about orange-red? dark red?) and consistently choose Tangerine instead.

> **Effect on output:** Not a single `#E63946` or similar red anywhere in the CSS. CTAs use Tangerine `#FF8200`.

---

### `"Use the sources on public as needed"`
**Technique: Asset reference.**
Pointing the model to real image assets means it can reference actual files instead of generating placeholder content.

> **Effect on output:** `<img src="../../public/recurly-logo-black.webp">` — real assets wired in correctly.

---

## What the Model Got Right (and Why)

| Decision | Prompt instruction | Output result |
|---|---|---|
| Background | `#FFFDF2` specified | `--off-white: #FFFDF2` in `:root` |
| CTA color | Tangerine `#FF8200` | `.btn-cta { background: var(--tangerine) }` |
| Font | F37 Gruffy + Roboto fallback | Correct font stack with Google Fonts |
| Icons | Phosphor style | Phosphor CDN loaded, icons used throughout |
| Decorative lines | Open curvy linework | SVG paths with open strokes, no fills |
| Layout | Left-aligned + whitespace | All text blocks left-aligned, large padding |
| Section structure | Eyebrow → Headline → Body → CTA | Every section follows the pattern |
| No red | "Avoid fast food red" | Zero red in the entire stylesheet |

---

## The Core Principle

Every vague word in the bad prompt (`modern`, `cool`, `fun`, `stand out`) was replaced with a **specification** in this prompt:

| Vague | Specific |
|---|---|
| "modern" | `left-aligned layout, significant whitespace` |
| "cool" | `F37 Gruffy, Phosphor icons, curvy linework` |
| "buttons stand out" | `Background: Tangerine (#FF8200) with Off Black text` |
| "white background" | `Off White (#FFFDF2)` |
| "professional but fun" | `Energetic, warm, and precise` |

**The model didn't become smarter. The prompt became more precise.**
