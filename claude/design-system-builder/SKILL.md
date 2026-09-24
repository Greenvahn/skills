---
name: design-system-builder
description: >
  Generates a complete, production-quality HTML/CSS design system from scratch using an interactive prompt builder. 
  Use this skill whenever the user wants to create a new design system, build a brand's visual foundation, 
  set up CSS design tokens, or needs a starter UI kit — even if they just say "build me a design system", 
  "I need a component library", "create a brand style guide", "set up tokens for my project", or 
  "I'm starting a new UI from scratch". Trigger even for vague requests like "make something that looks good 
  for my app" where establishing a visual system would help.
---

# Design System Builder

This skill creates a complete, production-quality HTML/CSS design system by first gathering brand inputs through
an interactive prompt builder, then generating the system based on those inputs.

## When this skill triggers

Any time the user wants to:
- Create a design system from scratch
- Set up CSS custom properties / design tokens
- Build a visual brand foundation (colours, typography, spacing)
- Get a starter UI kit or component library
- Establish a style guide for a new project

---

## Workflow

### Step 1 — Launch the Prompt Builder

Present the interactive prompt builder to the user so they can fill in their brand details.

Open the file at: `assets/design-system-prompt-builder.html`

Render it as an artifact so the user can interact with it directly in the chat. Tell the user:

> "Fill in your brand details below — brand name, colours, fonts, and personality. When you're ready, hit **✦ Generate Design System** and I'll build it for you automatically."

### Step 2 — Receive the Auto-Submitted Prompt

The builder's **✦ Generate Design System** button calls `sendPrompt()` to submit the generated prompt directly into the chat — the user does not need to copy/paste anything. The incoming message will look like:

```
I'm building a design system for [Brand Name] — [about project].

The audience is [audience]. The brand personality is [personality].

Brand colours: #hex1, #hex2, ...
Fonts I want to use: [Font] for headings, [Font] for body

Build me a design system foundation as a single HTML/CSS file that includes:
- CSS custom properties for all tokens ...
...
```

When you receive this message, proceed immediately to Step 3 — no confirmation needed.

### Step 3 — Build the Design System

Using the pasted prompt as your spec, generate a **single, self-contained HTML/CSS file** that includes:

#### Required Deliverables

1. **CSS Custom Properties (Design Tokens)**
   - Full colour palette (primary, secondary, neutrals, semantic: success/warning/error/info)
   - Typography scale (font families, sizes, weights, line heights, letter spacing)
   - Spacing scale (4px base unit, named: xs/sm/md/lg/xl/2xl/3xl)
   - Border radius tokens
   - Shadow tokens (subtle, medium, strong)
   - Grid tokens (max-width, gutters, columns)
   - Transition tokens (duration, easing)

2. **Typography System**
   - Display / Hero text
   - H1–H4 heading styles
   - Body large, body regular, body small
   - Caption / label / eyebrow patterns
   - Mono / code style

3. **Button Components**
   - Primary (gradient or solid brand colour)
   - Secondary (outline)
   - Ghost / text
   - Disabled states
   - Size variants (sm, md, lg)

4. **Responsive Grid**
   - Max-width container
   - Gutter system
   - Column helpers

5. **Demo Sections**
   - Hero section demonstrating the system in context
   - Card grid section
   - Token reference / swatch page (colour swatches, type scale, spacing scale)

#### Quality Standards

- **Not a wireframe** — must look finished and production-ready
- Respect all design constraints from the prompt (dark mode, border radius rules, etc.)
- Load fonts from Google Fonts if non-system fonts are specified
- Fully responsive (mobile-first)
- Accessible — WCAG AA minimum contrast on all text
- All CSS in `<style>` block, no external CSS dependencies (except Google Fonts)
- Comprehensive comments explaining the token system

### Step 4 — Deliver

Present the file using `present_files`. Also offer to:
- Adjust colours, fonts, or spacing
- Add more components (forms, nav, badges, modals)
- Export tokens as JSON or Tailwind config
- Create a dark mode variant

---

## Tips for a Great Output

- If the user skips the builder and describes their brand in words, extract the intent and build anyway
- If colours aren't specified, derive a coherent palette from the brand name/personality
- If fonts aren't specified, recommend something appropriate for the brand personality
- Always apply the stated constraints strictly — they are non-negotiable design decisions
- The token reference section at the bottom of the output is very useful; always include it
