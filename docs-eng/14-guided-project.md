# Module 14 | Guided Project: Login, Dashboard and Profile

[Português](../docs/14-projeto-guiado.md) · English

`WEEK 02 // Web Interface, Part 1: Layout`

---

## // What this module is for

This module does not teach any new concept. It exists to bring together, in order, everything Modules 01 to 13 taught separately, and show how the project's three screens are built, from start to finish, in a single workflow.

If any step below does not make sense, that is a sign it is worth reviewing the corresponding module before continuing, instead of just copying the code.

## // Before you start: the folder structure

```text
project/
├── index.html          (redirects to or presents the project)
├── login.html
├── dashboard.html
├── perfil.html
├── css/
│   └── styles.css
└── docs/
    ├── requisitos.md
    ├── historias-de-usuario.md
    ├── design-system.md
    └── arquitetura.md
```

## // Step 1 | HTML structure of the three screens (Modules 02 and 03)

For each screen, follow the same sequence:

1. Write the minimum structure (`<!DOCTYPE html>` to `</html>`), with a screen-specific `<title>`.
2. Add a `<header>` with navigation (the same on all three screens, for consistency).
3. Add a `<main>` with that screen's specific content.
4. Use semantic tags (`<section>`, `<form>`, `<nav>`) instead of a generic `<div>` whenever it makes sense.

**Login**: form with e-mail, password, "Sign in" button, link to sign up.
**Dashboard**: navbar, and a main area with search and a grid of group cards.
**Profile**: navbar, avatar, user information, action buttons.

## // Step 2 | Analysis before CSS (Module 09)

Before styling any screen, draw its component tree (if you have not done it in Module 09 yet). For the Dashboard, for example:

```text
Dashboard
├── Navbar
└── Main
    ├── Search
    └── CardGrid
        ├── Card
        ├── Card
        └── Card
```

## // Step 3 | Base CSS and Box Model (Modules 04 and 05)

```css
* {
    box-sizing: border-box;
}

body {
    margin: 0;
    font-family: var(--font-family-base, sans-serif);
    background-color: var(--color-background, #f7f2ed);
    color: var(--color-text, #241c18);
}
```

Connect `css/styles.css` to the three pages with `<link rel="stylesheet" href="css/styles.css">`, adjusting the relative path to the position of each HTML file.

## // Step 4 | Design tokens (Module 11)

Add the `:root` block with your design system's variables at the top of `styles.css`, before any other rule.

## // Step 5 | Layout with Flexbox and Grid (Modules 06 and 07)

- **Navbar** (every screen): Flexbox, `justify-content: space-between`, `align-items: center`.
- **Login form**: Flexbox, `flex-direction: column`, `gap`.
- **Dashboard card grid**: CSS Grid, `grid-template-columns: repeat(3, 1fr)`, `gap`.
- **Inside each card**: Flexbox, `flex-direction: column`.
- **Profile avatar + information**: Flexbox, `align-items: center`, `gap`.

## // Step 6 | Responsiveness (Module 08)

For each screen, in this order:

1. Write the base CSS with mobile in mind (one column, stacked elements).
2. Add `@media (min-width: 768px)` for the tablet layout.
3. Add `@media (min-width: 1024px)` for the desktop layout.
4. Test by resizing the browser on each screen.

## // Step 7 | Componentization (Module 13)

Review: do Button, Card, Input and Navbar use the same CSS class everywhere they appear? If you noticed any unintended variation between them, this is the moment to unify.

## // Step 8 | Accessibility (Module 12)

Final checklist per screen:

- [ ] Heading hierarchy without skipped levels.
- [ ] Every form field has a `label` connected via `for`/`id`.
- [ ] Every action uses `<button>`, never `<div onclick>`.
- [ ] Every image has a descriptive `alt`.
- [ ] Text/background contrast checked.
- [ ] `:focus-visible` visible on every interactive element.
- [ ] Full keyboard navigation tested.

## // Step 9 | (Optional) Tailwind or dark theme (Modules 10 and 13)

If you chose Tailwind, this is the step to rebuild components with utility classes, keeping the same visual tokens. If you are implementing a dark theme, this is the step to test switching between `data-theme="light"` and `data-theme="dark"`.

## // Wrap-up checklist for the three screens

- [ ] `login.html`, `dashboard.html` and `perfil.html` exist and open without errors in the browser.
- [ ] All three share the same `styles.css`.
- [ ] All three use the same design system variables.
- [ ] All three have the same navbar, visually consistent.
- [ ] All three work at at least three screen widths (mobile, tablet, desktop).
- [ ] No screen depends on `position: absolute` for its main structure.
- [ ] The Step 8 accessibility checklist is complete on all three.

## // Common mistakes when putting it all together

| Mistake | Why it happens | How to fix it |
|---|---|---|
| Each screen with a different `styles.css` | Copying and pasting without consolidating | A single source of styles shared by the three |
| Navbar looking different between screens | Styling each screen in isolation | Reuse exactly the same navbar class/structure on all three |
| Forgetting to test responsiveness on one of the three | Focusing only on the "main" screen | Repeat the resize test on each of the three screens, not only the first |

## // Applying it to the week's project

This is the application; there is no separate activity. By the end of this module, the three screens should be complete enough to pass the Module 15 checklist.

Final commit for this step: `git commit -m "Finish structure, layout and responsiveness of the three screens"`.

## // Checkpoint

> **BEFORE MOVING ON, THINK ABOUT THIS**
> If you had to explain to someone, in three sentences, why the order HTML → base CSS → layout → responsiveness → accessibility made sense (instead of, for example, starting with responsiveness), what would you say?

Possible answer: without HTML, there is nothing to style. Without understanding base CSS and the Box Model, layout (Flexbox/Grid) becomes unpredictable, because box sizes do not behave as expected. And without a working main layout, there is no point adapting that layout to smaller screens: responsiveness adjusts something that already exists; it does not replace the step of creating that something first.

## // Module summary

- [ ] I can repeat, from memory, the sequence of steps used to build a screen from scratch.
- [ ] My project's three screens (Login, Dashboard, Profile) went through all nine steps.
- [ ] The wrap-up checklist for the three screens is complete.

---

**Next module:** `15`: before considering the week done, a final review against the deliverable's real criteria (see `deliverable.md`).

`Study Material // Coffee & Code`
