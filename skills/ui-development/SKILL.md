---
name: ui-development
description: Use when building or refactoring frontend interfaces, web artifacts, or UI mockups to ensure premium aesthetics and audience alignment.
---

# UI Development & Premium Aesthetics

## Overview
This skill enforces a "Premium-First" approach to UI development, moving beyond basic functionality to create state-of-the-art, visually stunning artifacts. It prioritizes audience research before implementation and utilizes flexible design systems (shadcn/ui, Mantine, DaisyUI).

## The Audience-First Protocol

**MANDATORY**: Before writing a single line of UI code for a major feature, you must understand who you are building for.

### Discovery Questions
1. **Persona**: Who is the primary user? (e.g., "Developer looking for logs" vs. "Manager looking for trends")
2. **Context**: How will they access this? (e.g., "Phone on-the-go" vs. "27-inch secondary monitor")
3. **Complexity**: What is their technical literacy? (e.g., "Internal admin tool" vs. "Public-facing landing page")
4. **Tone**: What vibe should it project? (e.g., "Cyberpunk/High-tech" vs. "Clean/Minimalist/Professional")

## Design System Selection

Choose the baseline based on the audience research:

| Design System | Best For | Technical Stack |
| :--- | :--- | :--- |
| **shadcn/ui** | Professional SaaS, Clean Admin Tools | React, Tailwind, Lucide Icons |
| **Mantine** | Complex "OS-style" Apps, Micro-animations | React, Mantine Core, Framer Motion |
| **DaisyUI** | High-impact prototypes, Creative landing pages | Tailwind, CSS Variables, Glassmorphism |

## Implementation Patterns

### 1. The "WOW" Factor (Visual Moats)
- **Gradients**: Use mesh gradients or subtle linear fades instead of solid colors.
- **Glassmorphism**: Use `backdrop-blur` and translucent backgrounds for depth.
- **Animations**: Subtle entry/hover animations using CSS transitions or Framer Motion.
- **Typography**: Go beyond system fonts; use modern Google Fonts (Inter, Outfit, Roboto).

### 2. High-Performance Structure
- **Component Splitting**: Break complex artifacts into small, reusable atoms.
- **Responsive-First**: Use Tailwind's `sm:`, `md:`, `lg:` prefixes religiously.
- **Dark Mode**: Always support `dark` variants for a premium midnight feel.

## Common Mistakes
- **Placeholder Overload**: Never use "Lorem Ipsum." Use `imagen` or realistic mock data.
- **Flat Design**: Avoid total flatness; use layers, shadows (z-index), and blurs to create hierarchy.
- **Ignoring Constraints**: Ensure the UI actually works with the data provided.

## Verification Checklist
- [ ] Audience discovery questions asked and answered.
- [ ] Design system chosen based on audience profile.
- [ ] Responsive behavior verified on mobile and desktop.
- [ ] No default system colors (pure red/blue/green used).
- [ ] Typography is consistent and modern.
