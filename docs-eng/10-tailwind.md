# Module 10 | Tailwind CSS

[Português](../docs/10-tailwind.md) · English

`WEEK 02 // Web Interface, Part 1: Layout`

---

## // Before you start

This module only makes sense after Modules 04 to 08. If `display: flex`, `padding` or `grid-template-columns` are not yet clear as plain CSS, go back there before continuing. Tailwind does not teach CSS; it shortens the writing of CSS you already understand.

## // The problem

In an interface with several components, it is common to write a lot of repetitive CSS:

```css
.card {
    display: flex;
    padding: 1rem;
    border-radius: 0.75rem;
}

.card-secundario {
    display: flex;
    padding: 1rem;
    border-radius: 0.5rem;
}
```

Each new component asks for a new class name, and many of the declarations repeat from one to the next. Tailwind proposes a different way to solve this.

## // What Tailwind is

> **TAILWIND: IN SIMPLE WORDS**
> Tailwind is a CSS library that, instead of giving you ready-made classes per component (like `.card` or `.botao-primario`), gives you small classes, one for each CSS property, and you combine several of them right in the HTML to build the style.

This idea has a name: **utility-first**. Instead of naming and defining an entire component, you apply *utilities* (utility classes) until you reach the result.

## // Comparing side by side

**Traditional CSS:**

```css
.card {
    display: flex;
    padding: 1rem;
    border-radius: 0.75rem;
}
```
```html
<div class="card">...</div>
```

**Tailwind:**

```html
<div class="flex p-4 rounded-xl">...</div>
```

Translating each class:

| Tailwind class | Equivalent CSS |
|---|---|
| `flex` | `display: flex;` |
| `p-4` | `padding: 1rem;` |
| `rounded-xl` | `border-radius: 0.75rem;` |

> **DON'T LET THIS BECOME MAGIC**
> The `flex` class is not a special word that "makes the layout work"; it is literally `display: flex` written in a shorter way. Every Tailwind class represents one or more real CSS declarations. If you do not know which CSS a class represents, you do not know what it is doing: you are just copying something that seems to work.

## // Utility classes you already recognize

Since you already studied plain CSS in the previous modules, most Tailwind classes will look familiar as soon as you know the pattern:

| Category | Examples | Equivalent to |
|---|---|---|
| Spacing (scale) | `p-4`, `m-2`, `gap-6` | `padding`, `margin`, `gap`, on a consistent scale |
| Colors | `bg-amber-700`, `text-white` | `background-color`, `color`, using Tailwind's palette |
| Flex | `flex`, `justify-between`, `items-center` | `display: flex`, `justify-content`, `align-items` |
| Grid | `grid`, `grid-cols-3`, `gap-4` | `display: grid`, `grid-template-columns`, `gap` |
| Width | `w-full`, `w-64` | `width: 100%`, `width: 16rem` |
| Responsiveness | `md:grid-cols-2` | the same rule, only active from the `md` breakpoint up |
| Hover | `hover:bg-amber-800` | the rule only applies on `:hover` |
| Focus | `focus:outline-none` | the rule only applies on `:focus` |

Notice: `justify-between` is `justify-content: space-between`, a concept you already saw in full in Module 06. Tailwind does not invent new layout; it shortens CSS that already exists.

## // The spacing scale

```html
<div class="p-1">...</div>  <!-- 0.25rem -->
<div class="p-2">...</div>  <!-- 0.5rem -->
<div class="p-4">...</div>  <!-- 1rem -->
<div class="p-8">...</div>  <!-- 2rem -->
```

The numbers are not pixels or a free unit; they are positions on a predefined scale, designed to keep spacing consistent (the same consistency principle as your Week 01 design system, just applied through a ready-made scale).

## // Responsiveness in Tailwind

```html
<div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3">
```

This says: 1 column by default (mobile-first, just like Module 08), 2 columns from the `md` breakpoint, 3 from `lg`. The `md:` and `lg:` prefixes are Tailwind's own conventions for breakpoints. By default, `md` equals `768px` and `lg` equals `1024px`, the same values you already used by hand in Module 08.

## // Dark mode, when relevant

```html
<div class="bg-white dark:bg-gray-900 text-black dark:text-white">
```

The `dark:` prefix applies the rule when dark mode is active. We will dig into light/dark themes in Module 13; for now, just recognize the pattern.

## // Installing Tailwind | what this guide uses, and why

> **VERSION AND DATE CHECKED**
> This module was written based on the official Tailwind CSS documentation (tailwindcss.com/docs) on September 21, 2026. The current stable version is **Tailwind CSS v4** (build 4.3.x). v4 changed the installation compared to older versions: `tailwind.config.js` is no longer required, and the old `@tailwind base; @tailwind components; @tailwind utilities;` was replaced by a single `@import "tailwindcss";`. If you find an older tutorial using those commands, it is outdated: follow what is here.

### > For quick testing (Play CDN)

```html
<head>
  <script src="https://cdn.tailwindcss.com"></script>
</head>
```

One line, nothing to install, no terminal. The browser downloads Tailwind and generates the needed CSS in real time, right in the browser. **Use this only for testing and learning**; it is not the recommended way for the final project, because the processing happens in the visitor's browser, on every load, with no optimization.

### > For the real project (standalone CLI, no Node.js needed)

This is the recommended way for the week's deliverable, because it generates a real, compiled `.css` file without depending on Node.js being installed, which most people who are just starting do not have set up yet:

1. Download the executable for your operating system, directly from Tailwind's official releases page on GitHub (`github.com/tailwindlabs/tailwindcss/releases`).
2. Give the downloaded file execution permission (on Mac/Linux: `chmod +x tailwindcss`).
3. Create an `input.css` file with the content:
   ```css
   @import "tailwindcss";
   ```
4. Run the command that compiles that file into a final CSS, watching for changes:
   ```bash
   ./tailwindcss -i input.css -o styles.css --watch
   ```
5. Connect `styles.css` (the generated file) to your HTML, exactly as you have done since Module 04.

> **IF YOU ALREADY HAVE NODE.JS INSTALLED**
> There is also the npm route: `npm install tailwindcss @tailwindcss/cli`, then `npx @tailwindcss/cli -i input.css -o styles.css --watch`. It is equivalent to the standalone version; choose whatever is more convenient for your environment.

## // Tailwind does not replace CSS

Reinforcing the most important point of this module: Tailwind is built on top of the concepts you already studied, not in place of them. Look at this snippet:

```html
<div class="flex items-center justify-between gap-4">
```

The goal is for you to read this and think: *Flexbox, vertically centered alignment, distribution with space between items, 1rem spacing between them*, and not "these are classes that make it work". If you only memorize class names without knowing the CSS behind them, any situation off the obvious path (a bug, a need not covered by a ready-made utility) will leave you stuck.

## // Good example × bad example

**Bad example**: copying classes without understanding them:

> "I saw this set of classes in a template and pasted it. I don't know what each one does, but it looks similar."

**Good example**: applying them knowing what each class represents:

> "I used `flex` because I need to align these items in a row, `justify-between` because I want the logo on one side and the links on the other, and `gap-4` for the spacing: the same decision I would make writing plain CSS, just faster to write."

## // Common mistakes

| Mistake | Why it happens | How to fix it |
|---|---|---|
| Tailwind "doesn't apply any class" | The Play CDN script did not load, or the compiled CSS was not connected | Check whether the `<script>` is in the `<head>` (Play CDN) or whether the generated `styles.css` has a correct `<link>` |
| Mixing CDN and CLI in the same project | Confusion about which path to follow | Pick one: CDN only for testing, CLI for the real project |
| Using `tailwind.config.js` from an old tutorial | Tutorial based on Tailwind v3 or earlier | In v4, custom configuration goes directly in the CSS, inside an `@theme` block |
| Applying dozens of classes without understanding any | Copying from another project without checking | Mentally translate each class into the equivalent CSS before using it |

## // Guided practice

1. Add the Play CDN (`<script src="https://cdn.tailwindcss.com"></script>`) to a separate test page, outside your main project.
2. Rebuild the navbar from Module 06 using only Tailwind classes: `flex`, `justify-between`, `items-center`, `p-4`.
3. Visually compare it with the plain CSS version you already had: the result should be identical.
4. For each class you used, say out loud the equivalent CSS, without checking the table in this section.

## // Practice on your own

> **CHALLENGE**
> Rewrite the Dashboard card grid (Module 07) using `grid`, `grid-cols-1`, `md:grid-cols-2`, `lg:grid-cols-3` and `gap-4`. Test by resizing the browser window, and confirm the responsive behavior matches what you had already built by hand with media queries.

## // Applying it to the week's project

1. Decide: will your project use Tailwind via the standalone CLI, or stay with plain CSS? (Both are valid: what matters is that the choice is deliberate, not copied without understanding.)
2. If you choose Tailwind, install the standalone CLI and generate your `styles.css` from `@import "tailwindcss";`.
3. Rebuild at least one component of your project (for example, the main button) using utility classes, keeping the same colors and spacing from your design system.
4. Commit: `git commit -m "Add Tailwind CSS and rebuild a component with utility classes"`.

## // Checkpoint

> **BEFORE MOVING ON, THINK ABOUT THIS**
> Why doesn't the Tailwind class `class="flex items-center gap-4"` remove the need to understand Flexbox?

Answer: because that class is just a shorthand for writing `display: flex; align-items: center; gap: 1rem;`. Without understanding what Flexbox does (container, items, axes), you cannot predict the result, adjust it when something turns out differently than expected, or decide which other utility classes to combine to solve a layout problem that has no ready-made solution.

## // Module summary

- [ ] I can explain the utility-first concept, with an example comparing plain CSS and Tailwind.
- [ ] I can translate common Tailwind classes (`flex`, `p-4`, `grid-cols-3`, `md:`, `hover:`) into the CSS they represent.
- [ ] I know the difference between using the Play CDN (testing) and installing the standalone CLI (real project), and why.
- [ ] I know why Tailwind does not replace knowing CSS.
- [ ] I have already rebuilt at least one component of my project using Tailwind.

---

**Next module:** `11-design-system-in-code.md`: your colors and spacing already exist in Figma. Time to turn them into real tokens in code.

`Study Material // Coffee & Code`
