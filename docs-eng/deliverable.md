# Deliverable | Week 02

[Português](../docs/entregavel.md) · English

`WEEK 02 // Web Interface, Part 1: Layout`

Use this file as the final checklist before considering Week 02 done. It gathers what is **required**: the extra challenges in `challenges.md` are optional.

## // What you should have in hand now

If you followed the modules in order, your repository should now have, in addition to everything from Week 01: three HTML pages (Login, Dashboard, Profile), complete, styled, responsive and connected to a shared `styles.css`, built on top of the design system defined in Week 01.

## // Deliverable checklist

### > Structure

- [ ] `login.html`, `dashboard.html` and `perfil.html` exist and open without errors.
- [ ] The three pages share the same `css/styles.css`.
- [ ] The folder structure is organized (`css/`, `docs/`, HTML files at the root or in `pages/`).

### > HTML

- [ ] Each page has the complete minimum structure (`<!DOCTYPE>`, `<html lang>`, `<head>` with `charset` and `viewport`, a specific `<title>`).
- [ ] Semantic HTML used correctly (`<header>`, `<nav>`, `<main>`, `<section>`, `<footer>` where it makes sense).
- [ ] Heading hierarchy without skipped levels.
- [ ] Login form with a `<label>` connected to each field via `for`/`id`.
- [ ] Every clickable action uses `<button>`, never `<div onclick>`.
- [ ] Every image has a descriptive `alt`.

### > CSS / Layout

- [ ] `box-sizing: border-box` applied globally.
- [ ] `styles.css` correctly connected on the three pages (correct relative paths).
- [ ] The navbar (or equivalent) uses Flexbox, consistent across the three screens.
- [ ] The Dashboard card grid uses CSS Grid.
- [ ] Colors, typography and spacing come from CSS Custom Properties in `:root`, not from loose values scattered through the code.

### > Responsiveness

- [ ] `<meta name="viewport">` present on the three pages.
- [ ] Layout tested at at least three widths (~375px, ~768px, ~1200px).
- [ ] No unwanted horizontal scrolling at any of the tested widths.
- [ ] Mobile-first approach used in the media queries.

### > Consistency

- [ ] Button, Card, Input and Navbar use the same CSS class everywhere they appear.
- [ ] `/docs/design-system.md` updated with the implementation section (tokens used in the code).

### > Accessibility

- [ ] Text/background contrast checked for the main palette.
- [ ] `:focus-visible` visible on interactive elements (no `outline: none` without a replacement).
- [ ] No state depends only on color to be identified.
- [ ] Full keyboard navigation tested on at least one of the screens.

### > Project

- [ ] The three screens from the Figma prototype (Week 01) are implemented, even if with adjustments.
- [ ] Organized commit history, with clear messages, reflecting progress module by module.

## // What is NOT expected this week

To make it clear and avoid unnecessary anxiety:

- No backend, database or real authentication is expected.
- No working JavaScript is expected (a manual theme button, for example, is an optional challenge, not a requirement).
- Pixel-perfect visual fidelity to Figma is not expected: small spacing and proportion adjustments are normal and expected when moving from a static design to real HTML/CSS.
- Using Tailwind is not expected: plain CSS is an equally valid submission.

> **BEAUTY IS NOT THE CRITERION**
> A project with a simple structure, correct semantic HTML, CSS organized in variables and working responsiveness is worth more, in this evaluation, than a visually elaborate project with a generic `<div>` instead of `<button>`, no `label`, or one that breaks completely on a phone. Structure and fundamentals are what is being evaluated this week, not aesthetics.

## // How to review before submitting

> **THE MOST IMPORTANT TEST THIS WEEK**
> Ask someone else (a Coffee & Code classmate, a friend, or yourself reviewing after a while) to open your three pages, with no explanation from you, and: fill in the Login form, navigate to the Dashboard, see the Profile, all while resizing the window to simulate a phone at some point. Can that person do all of this without getting stuck or confused?

If the answer is yes, your submission is on the right track. If not, go back to the corresponding module and adjust; that is not a failure, it is exactly the kind of adjustment this final review exists to catch before the deadline.

## // Where to ask questions

Coffee & Code's weekly meetings exist for exactly this. Bring a specific question: "my grid isn't breaking into 2 columns on tablet, I already tried X and Y" is much faster to solve than "I didn't understand anything about CSS Grid".

If you want to go beyond what was asked, see `challenges.md`.

## // What comes in Week 03

Week 02 ends with three static screens, visually ready and responsive, but with no dynamic behavior yet. A click on "Sign in" does not really do anything; the Dashboard cards are always the same, no matter who is "logged in". That gap (behavior, interactivity, data that changes) is exactly what the club's next weeks start to fill.

Good work so far.

`Study Material // Coffee & Code`
