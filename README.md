# Reatcurly — Prompt Engineering Showcase

A hands-on demo for the **Recurly AI Workshop** showing how a single prompt change can be the difference between a generic AI output and a polished, on-brand result.

---

## What's Inside

This repo contains two versions of the same task — build a landing page for **Reatcurly**, a gourmet hot dog brand — each generated from a different prompt.

```
reatcurly/
├── bad-prompt/
│   ├── prompt.md            # The vague, underspecified prompt
│   ├── prompt-anatomy.md    # Line-by-line breakdown of what went wrong
│   └── bad-prompt.html      # The resulting generic website
│
└── good-prompt/
    ├── prompt.md            # The precise, constraint-driven prompt
    ├── prompt-anatomy.md    # Line-by-line breakdown of what worked
    └── good-prompt.html     # The resulting on-brand website
```

---

## The Core Idea

> **Vague language gives the model creative freedom. Creative freedom produces average output.**

When you leave decisions up to the model — color, typography, layout, tone — it defaults to whatever it has seen most often in training data. That usually means a red-button startup template with Montserrat and emoji.

Precise constraints do the opposite. They collapse the model's decision space so that the only remaining task is execution.

---

## Side-by-Side Comparison

### The Prompts

**Bad prompt** (`bad-prompt/prompt.md`)
```
Hey, please execute this prompt:
Design a modern and cool website for a hot dog company called Reatcurly.
It should look professional but fun. Use a white background and make
sure the buttons stand out so people want to buy hot dogs. Include a
section for pricing.
Play with the images as needed.
```

**Good prompt** (`good-prompt/prompt.md`)
```
Act as a Lead UI Designer. Create a high-fidelity landing page layout
for 'Reatcurly,' a gourmet hot dog brand, strictly following these
brand guidelines:

1. Visual Palette:
   - Primary Background: Off White (#FFFDF2)
   - Hero Section: Solid Yellow (#FFD706)
   - Typography: F37 Gruffy Medium / FT Polar Regular (fallback: Roboto)
   - Text: Off Black (#0D0D0B)

2. Component Styling:
   - Primary CTA: Tangerine (#FF8200) with Off Black text
   - Icons: Rounded, curvy Phosphor style
   - Accents: Fluid, curvy yellow linework (no closed shapes)

3. Layout & Content:
   - Strict hierarchy: Eyebrow (All caps) → Headline → Body → CTA
   - Left-aligned layout with significant whitespace
   - Hero Image: Lifestyle photo, repeating scale (X, X/2, X/4) treatment

4. Tone: Energetic, warm, precise. Avoid fast food red.
```

### The Results

| | Bad Prompt | Good Prompt |
|---|---|---|
| **CTA color** | Red `#E63946` | Tangerine `#FF8200` |
| **Background** | Pure white `#FFFFFF` | Off white `#FFFDF2` |
| **Typography** | Montserrat + Inter | F37 Gruffy + FT Polar |
| **Icons** | Emoji | Phosphor icon set |
| **Layout** | Centered, generic blobs | Left-aligned, open linework |
| **Tone** | Fun / casual startup | Energetic but sophisticated |
| **Design system** | Ad-hoc | CSS tokens + spacing scale |

---

## Key Prompt Engineering Techniques

Each `prompt-anatomy.md` file walks through every line of the prompt. Here are the headline techniques demonstrated:

**Role injection** — `Act as a Lead UI Designer`
Shifts the model's perspective and activates design-domain knowledge before any instructions are given.

**Constraint framing** — `strictly following these brand guidelines`
Removes ambiguity about whether these are suggestions or requirements.

**Hex codes over adjectives** — `#FFFDF2` instead of "white"
Hex is unambiguous. "White" can mean a hundred different whites.

**Negative constraints with context** — `Avoid fast food red`
Tells the model what *not* to do and explains *why*, which helps it generalize the constraint.

**Graceful degradation** — `F37 Gruffy Medium / FT Polar Regular (fallback: Roboto)`
Defines premium assets and a realistic fallback in one instruction.

**Scoped component colors** — Each color is mapped to a specific element, not applied globally.

**Explicit content hierarchy** — `Eyebrow → Headline → Body → CTA` defines the exact reading order for every section.

---

## How to View

Open either HTML file directly in a browser — no build step or server required.

```bash
open bad-prompt/bad-prompt.html
open good-prompt/good-prompt.html
```

---

## Workshop Takeaways

1. **Adjectives are not specifications.** "Modern," "cool," and "professional" are instructions to *you*, not to the model.
2. **The model fills gaps with defaults.** Every detail you omit gets replaced with the most common thing it has seen.
3. **Role + format + constraints = leverage.** These three elements do most of the heavy lifting in a well-formed prompt.
4. **Negative space matters.** Telling the model what to *avoid* is as powerful as telling it what to include.
5. **You don't need more words — you need more signal.**
