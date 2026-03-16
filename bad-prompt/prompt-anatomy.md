# Prompt Anatomy — Bad Prompt

> This file breaks down **why** this prompt produced a generic, off-brand result.
> Use it alongside `bad-prompt.html` to spot the cause of each design decision.

---

## The Prompt

```
Hey, please execute this prompt:

Design a modern and cool website for a hot dog company called Reatcurly.
It should look professional but fun. Use a white background and make
sure the buttons stand out so people want to buy hot dogs. Include a
section for pricing.

Play with the images as needed.
```

---

## Line-by-Line Breakdown

### `"Hey, please execute this prompt:"`
**Problem: Filler with no signal.**
This line gives the model zero context. It doesn't set a role, a goal, or any constraint. The word "execute" implies the model should just do something — anything.

---

### `"Design a modern and cool website"`
**Problem: Vague adjectives.**
"Modern" and "cool" are subjective. Every era has its own definition of modern. The model defaults to what it has seen most: rounded corners, Montserrat, hero emoji, a marquee band. All perfectly generic.

> **What was generated:** Montserrat font, emoji hero (`🌭`), generic startup aesthetic.
> **What was intended:** F37 Gruffy, lifestyle photography, gourmet brand feel.

---

### `"for a hot dog company called Reatcurly"`
**Problem: Brand name only, no brand identity.**
The model knows the name but nothing about the brand's personality, palette, or positioning. It has to invent everything — and it will default to category clichés.

> **What was generated:** Red (#E63946) buttons — the default "food brand" color.
> **What was intended:** Tangerine (#FF8200) and Yellow (#FFD706) — no red at all.

---

### `"It should look professional but fun"`
**Problem: Contradictory adjectives without anchors.**
"Professional" and "fun" pull in opposite directions. Without specifics, the model resolves the tension by picking one side: it went fun (emoji, red, badges like "🔥 Fan Favorite").

---

### `"Use a white background"`
**Problem: One constraint, imprecise.**
"White" is technically correct but too broad. There are hundreds of whites. The model used pure `#FFFFFF`. The brand uses Off White `#FFFDF2` — a warm, deliberate choice that changes the entire feel.

---

### `"make sure the buttons stand out"`
**Problem: Describes the goal, not the solution.**
"Stand out" tells the model _what effect_ you want, not _how to achieve it_. The model chose red because red pops — but red was explicitly the wrong choice for this brand.

> **What was generated:** `background: #E63946` (red) buttons throughout.
> **What was intended:** `background: #FF8200` (tangerine) for CTAs.

---

### `"Include a section for pricing"`
**Problem: No structure, no content, no hierarchy.**
The model built a pricing section, but with zero guidance it invented plan names, prices, and features. There's no instruction about tone, layout, or how many tiers.

---

### `"Play with the images as needed"`
**Problem: Complete creative freedom = maximum generic output.**
This is an open invitation for the model to do whatever it wants with visuals. It chose emoji placeholders and decorative circles because those are safe, common choices.

> **What was generated:** Floating `🌭` emoji, yellow/red CSS circle blobs.
> **What was intended:** Lifestyle photography with a specific "repeating scale" (X, X/2, X/4) photo treatment.

---

## What the Model Assumed (and Got Wrong)

| Decision | What model chose | What brand needed |
|---|---|---|
| Primary CTA color | Red `#E63946` | Tangerine `#FF8200` |
| Background | Pure white `#FFFFFF` | Off White `#FFFDF2` |
| Font | Montserrat | F37 Gruffy / FT Polar |
| Icons | Emoji | Phosphor (rounded/curvy) |
| Decorative elements | CSS circles | Fluid curvy linework (open shapes) |
| Layout alignment | Centered | Left-aligned |
| Visual tone | Fun/casual | Energetic but sophisticated |

---

## Root Cause Summary

The prompt had **1 concrete constraint** (white background) and **6+ subjective descriptors** (modern, cool, professional, fun, stand out, play with).

The model filled every gap with the most statistically common choice for a food brand website. The output is competent but entirely generic — it could be for any hot dog company anywhere.

**The fix isn't writing more words. It's replacing adjectives with specifications.**
