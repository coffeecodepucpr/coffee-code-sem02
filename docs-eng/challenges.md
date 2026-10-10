# Challenges | Week 02

[Português](../docs/desafios.md) · English

Optional challenges, organized by the week's modules. None is required for the basic submission; see `deliverable.md` for what is required. Use these challenges if you finished the main modules and want to go further, or if you want to make the deliverable more robust.

---

## // HTML and Forms (Modules 02 to 03)

**If you are just starting**
- Add extra native validation to the Login form: `minlength` on the password, and a custom error message using the `title` attribute.
- Add a `<fieldset>` with a `<legend>` grouping the fields of the sign-up form, if you created one.

**If you already have experience**
- Research the `autocomplete` attribute on form fields (for example, `autocomplete="email"`) and apply it to the relevant Login fields; it improves the browser's autofill.
- Add a second input type relevant to your project (`type="tel"`, `type="date"`) to some form on the Profile, with the matching `pattern`.

---

## // CSS and Box Model (Modules 04 to 05)

**If you are just starting**
- Create a second button variation (`.botao-secundario`) with colors different from the main one, but reusing `--spacing` and `--radius` from your design system.

**If you already have experience**
- Research the `clamp()` property in CSS and use it for a font size that adjusts smoothly between a minimum and a maximum, without needing a specific media query for it.

---

## // Flexbox and Grid (Modules 06 to 07)

**If you are just starting**
- Add an empty state to the Dashboard: what shows up in the card area if there are no groups? Style that state (even if simple) using Flexbox to center a message.

**If you already have experience**
- In the Dashboard grid, use `grid-template-areas` (instead of only `grid-template-columns`) to explicitly name the layout regions, and read MDN's official documentation on this property before applying it.
- Combine `minmax()` with `auto-fit` in the card grid, testing the behavior without any media query; compare it with the version that uses fixed breakpoints.

---

## // Responsiveness (Module 08)

**If you are just starting**
- Test your three screens at at least two widths you had not tested yet (for example, 900px and 1440px), and adjust any breakpoint that makes sense.

**If you already have experience**
- Research `clamp()` combined with `vw` for truly fluid spacing (which changes continuously, not just in breakpoint jumps), and apply it to some spacing on your Dashboard.

---

## // Tailwind (Module 10)

**If you are just starting**
- Rebuild the entire Login screen using only Tailwind (via the standalone CLI), comparing the final result with the plain CSS version.

**If you already have experience**
- Set up your design system's custom colors inside an `@theme` block in your Tailwind v4 input CSS, and use those custom colors (not Tailwind's default colors) in the rebuilt components.

---

## // Design System in Code (Module 11)

**If you are just starting**
- Add at least two spacing variables that do not exist yet in your `:root` (for example, `--spacing-2xl`), documenting the decision in `/docs/design-system.md`.

**If you already have experience**
- Research `@property` (typed registration of custom properties in CSS) and evaluate whether it would make sense to apply it to any variable in your project; you do not have to use it, just understand what it solves.

---

## // Accessibility (Module 12)

**If you are just starting**
- Run a contrast check on every text/background combination in your design system, not just the main one, documenting the results.

**If you already have experience**
- Install an accessibility audit extension in your browser (search for "Lighthouse accessibility audit" or similar) and run it on your three screens, fixing at least two issues it points out.

---

## // Componentization and Themes (Module 13)

**If you are just starting**
- Document, in `/docs/design-system.md`, the complete list of your project's reusable components and where each one appears.

**If you already have experience**
- Add a manual theme toggle button, using basic JavaScript (`document.documentElement.setAttribute('data-theme'...)`) to toggle the `data-theme` attribute on click. Even though JavaScript is not the focus this week, this is a good first contact driven by curiosity, not obligation.

---

## // General challenge (everyone)

Ask someone else (or yourself, reviewing after a break) to navigate your three screens using only the keyboard, at at least two different screen widths, with no explanation from you. Can that person: understand what each screen does? Fill in the Login form? Move between screens? If the answer is yes to everything, your deliverable is at a good level. If not, go back to the corresponding module.
