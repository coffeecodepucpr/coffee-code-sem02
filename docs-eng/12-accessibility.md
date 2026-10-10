# Module 12 | Accessibility

[Português](../docs/12-acessibilidade.md) · English

`WEEK 02 // Web Interface, Part 1: Layout`

---

## // Before you start

Accessibility is not an isolated module you "do last"; that is why much of what you need has already shown up, spread across the previous modules: `<label>` in Module 03, `<button>` instead of a clickable `<div>` in Module 03, heading hierarchy in Module 02, visible focus mentioned in Module 04. This module brings all of that together, explains the why in more depth, and adds what was still missing.

## // What accessibility really means here

> **ACCESSIBILITY: IN SIMPLE WORDS**
> It means building an interface that works for as many people as possible, including people who do not use a mouse, who have low vision, who use a screen reader, who have motor difficulties with precise clicks.

It is not an "extra" feature for a small group of people. In practice, it is testing whether your interface depends on a single way of being used (mouse, perfect eyesight, click precision) in order to work.

## // Review: what you already did without calling it "accessibility"

| Practice | Module | Why it helps accessibility |
|---|---|---|
| Semantic HTML (`<header>`, `<nav>`, `<main>`) | 03 | Screen readers navigate by these regions |
| `<label for="...">` connected to the field's `id` | 03 | The screen reader announces the right label when the field is focused |
| `<button>` instead of `<div onclick>` | 03 | Receives keyboard focus and is announced as a button |
| `alt` on images | 02 | The screen reader describes the image; it shows up if the image fails |
| Heading hierarchy without skipping levels | 02 | Screen readers navigate the page by the heading structure |

## // What is still missing: contrast

> **CONTRAST: IN SIMPLE WORDS**
> It is the difference in brightness between the text and the background behind it. Contrast that is too low makes text hard to read, not only for people with low vision, but for anyone on a dim screen or in direct sunlight.

There is a reference standard called WCAG (Web Content Accessibility Guidelines) that defines minimum contrast levels. You do not need to calculate it by hand: there are free contrast checker tools (search for "WCAG contrast checker") where you enter the two colors from your design system and get a verdict. Run this test with your project's main text/background combination.

## // Font size and touch area

- **Font size**: avoid text smaller than 16px for main content; very small sizes are hard to read, especially on phone screens.
- **Touch area**: buttons and links need a minimum clickable/tappable area; a common reference is about 44x44px. A button that looks small but has enough padding can still have an adequate touch area.

## // Focus and `focus-visible`

You already saw, in Module 04, that the browser shows a default outline when an element is focused by keyboard (Tab key). It is common to see projects removing that outline for looks:

```css
/* DON'T DO THIS WITHOUT A REPLACEMENT */
button:focus {
    outline: none;
}
```

> **WHO GETS HURT**
> Someone who navigates entirely by keyboard (by preference, or because they cannot use a mouse precisely) depends on that outline to know where they are on the page. Removing it without putting another visual cue in its place leaves that person "lost", not knowing which element is active.

If you want to change the look of focus for visual reasons, replace it with something equally visible:

```css
/* A deliberate alternative */
button:focus-visible {
    outline: 2px solid var(--color-primary);
    outline-offset: 2px;
}
```

`:focus-visible` (unlike `:focus`) applies the style only when the browser understands the focus came from keyboard navigation, not on every mouse click. This keeps the outline from showing up where it visually bothers more than it helps, without removing it from where it is essential.

## // Keyboard navigation | introduction

Quick test: take any of your three screens, click on an empty spot of the page, and navigate using only the Tab key (Shift+Tab to go back). Ask:

- Does the navigation order make sense (does it follow the visual/logical order of the screen)?
- Can you reach every interactive element (fields, buttons, links) with the keyboard alone?
- Is the focused element always visible?

If any answer is "no", that is a real accessibility problem, not a hypothetical one.

## // States that do not depend only on color

```html
<!-- Only color indicates the error (bad) -->
<input class="campo-vermelho">

<!-- Color + explicit text (better) -->
<input class="campo-erro" aria-describedby="erro-email">
<span id="erro-email">Invalid e-mail</span>
```

People with color blindness (a significant share of the population) may not notice the difference between a "normal" field and one "with an error" if the only cue is color. Always pair color cues with text, an icon, or another cue that does not depend on color.

## // Good example × bad example

**Bad example:**

```html
<div class="botao-fake" onclick="entrar()">Sign in</div>
```

**Good example:**

```html
<button type="submit">Sign in</button>
```

Already seen in Module 03, repeated here because it is, on its own, one of the most common accessibility mistakes and one of the easiest to avoid.

## // Going deeper

For those who already have the essentials down:

- **Landmarks**: semantic tags (`<header>`, `<nav>`, `<main>`, `<footer>`) already work as landmarks for screen readers. You can reinforce this with ARIA attributes (`role="navigation"`), but the right semantic tags are usually enough.
- **ARIA, with care**: `aria-*` attributes (such as `aria-label`, `aria-describedby`) complement HTML when native semantics are not enough. They **do not replace** misused semantic HTML: adding `role="button"` to a `<div>` does not bring back the native keyboard behavior a `<button>` already has for free. Use ARIA to complement, not to fix a wrong choice of tag.
- **`prefers-reduced-motion`**: a media query that detects whether the person has set their system to reduce animations (important for people who are sensitive to motion). Keep it as a reference for when the project has animations.
- **WCAG contrast**: level AA is the common minimum reference for professional projects; level AAA is stricter.

## // Common mistakes

| Mistake | Why it happens | How to fix it |
|---|---|---|
| Removing the focus `outline` without a replacement | It looks "cleaner" | Use `:focus-visible` with an alternative style; never remove it without a replacement |
| Color as the only state indicator | It looks like enough visually | Pair it with text or an icon |
| `<div>` or `<span>` acting as a button | It seems easier to style | Use `<button>` and style it: CSS handles the whole look |
| ARIA used to "fix" wrong HTML | It looks like a shortcut | Fix the tag first; ARIA complements, it does not replace |

## // Guided practice

1. Navigate the Login screen using only the keyboard (Tab, Shift+Tab, Enter). Note any point where the navigation did not make sense.
2. Check the contrast between text and background on your main buttons, using a WCAG contrast checker.
3. Confirm that no state (error, success, disabled) depends only on color; add text or an icon where it is missing.

## // Practice on your own

> **CHALLENGE**
> Add a custom `:focus-visible` style, using your design system's colors, to every interactive element in the project (buttons, links, fields). Test by tabbing through all three screens.

## // Applying it to the week's project

1. Confirm semantic HTML, `label`/`for`, `button` (not `div`) and `alt` on the three screens (a review of what you already did in the previous modules).
2. Check your main palette's contrast with a WCAG tool.
3. Add a custom `:focus-visible`.
4. Make sure no state depends only on color.
5. Commit: `git commit -m "Review and strengthen accessibility on the three screens"`.

## // Checkpoint

> **BEFORE MOVING ON, THINK ABOUT THIS**
> Your button has no visible focus state. Who specifically gets hurt by that?

Answer: anyone navigating by keyboard, whether by preference or because they cannot use a mouse precisely (a motor disability, for example). Without a visible focus cue, that person loses track of where they are on the page, making navigation practically unusable.

## // Module summary

- [ ] I can list at least five accessibility practices that already appeared in the previous modules.
- [ ] I know what contrast is and how to check it.
- [ ] I know why removing `outline` without a replacement hurts keyboard navigation, and I can use `:focus-visible`.
- [ ] I know why states should not depend only on color.
- [ ] I tested my three screens navigating with the keyboard only.

---

**Next module:** `13-componentization-and-themes.md`: recognizing repeated patterns, and a first light/dark theme.

`Study Material // Coffee & Code`
