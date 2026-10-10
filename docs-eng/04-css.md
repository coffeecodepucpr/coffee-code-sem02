# Module 04 | CSS: How the Browser Styles the Page

[Português](../docs/04-css.md) · English

`WEEK 02 // Web Interface, Part 1: Layout`

---

## // The problem

Your Login screen already has a complete structure (Modules 02 and 03): heading, form, fields, button. Open it in the browser now. Does it look like what you drew in Figma in Week 01?

Almost certainly not. Black heading and paragraph, fields without spacing, a button with no color: the browser's default style, generic, the same on any site without CSS. HTML gave meaning and structure; the visual presentation is missing.

## // What is CSS?

> **CSS: IN SIMPLE WORDS**
> CSS is the language that describes how each HTML element should look: color, size, spacing, position.
>
> Technically: CSS (Cascading Style Sheets) is a styling language that selects HTML elements and applies appearance declarations to them. "Cascading", the most important part of the name, describes how the browser decides which rule wins when more than one could apply to the same element. We will come back to that shortly.

## // Anatomy of a CSS rule

```css
button {
    background-color: #6f4e37;
    color: white;
}
```

| Part | Name | What it is |
|---|---|---|
| `button` | Selector | Which element(s) this rule affects |
| `background-color: #6f4e37;` | Declaration | A property + a value, separated by a colon, ending in a semicolon |
| `background-color` | Property | What is being changed |
| `#6f4e37` | Value | What it is being changed to |
| everything between `{ }` | Rule (or "declaration block") | The set of declarations applied to that selector |

This whole rule says: "every `<button>` element on the page should have a `#6f4e37` background and white text."

## // Selectors: choosing what to style

### > Element selector

```css
button {
    color: white;
}
```

Affects **every** `<button>` on the page, no exceptions.

### > Class selector

```html
<button class="btn-primario">Sign in</button>
```

```css
.btn-primario {
    background-color: #6f4e37;
}
```

The dot (`.`) before the name indicates a class. Unlike the element selector, a class only affects elements that explicitly receive it. That is useful when not every button on the page should look the same (a "Sign in" button and a "Cancel" button probably should not have the same color).

### > ID selector (for context)

```css
#form-login {
    max-width: 400px;
}
```

The `#` selects by the `id` attribute. Unlike classes, an `id` must be unique on the page: only one element can have that `id`. In practice, classes are used much more often than IDs for styling, precisely because a reusable style (like a button) usually needs to apply to several elements, not just one.

### > Pseudo-classes (introduction)

```css
button:hover {
    background-color: #5a3e2c;
}
```

`:hover` selects the element only while the mouse is over it. There are many pseudo-classes; we will look at `:focus` in more depth in Module 12 (Accessibility), because it is essential for people who navigate by keyboard.

## // Cascade, inheritance and specificity | at an introductory level

These three words answer the same practical question: **what happens when two CSS rules compete for the same element?**

> **CASCADE: IN SIMPLE WORDS**
> The cascade is the mechanism the browser uses to decide, among several rules that could apply to an element, which one actually counts. In simple terms, the more specific rule usually wins; between equally specific rules, the one that comes later in the file wins.

Example:

```css
button {
    color: white;
}

.btn-secundario {
    color: black;
}
```

A `<button class="btn-secundario">` ends up with black text, because a class selector is more specific than an element selector. That is **specificity**: a way of measuring a selector's "weight". You do not need to memorize a specificity scoring table this week; just understand that classes weigh more than elements, and that this explains why "my rule isn't working" almost always means "another, more specific rule is winning".

> **INHERITANCE: IN SIMPLE WORDS**
> Some styles (such as text color and font) automatically pass from a parent element to its children, unless the child has its own rule. If you set the font on `<body>`, every element inside it inherits that font, without repeating the rule on each one.

## // Connecting CSS to HTML

There are three ways to apply CSS. Only one of them is recommended for real projects:

| Way | How | When to use it |
|---|---|---|
| Inline | `<button style="color: white;">` | Avoid it: it mixes structure and presentation, hard to maintain |
| `<style>` in the `<head>` | A CSS block inside the HTML itself | Acceptable for quick tests, not for the project |
| External `.css` file | A separate `.css` file, connected via `<link>` | **This is the way used in the project** |

### > Why split into files

```text
login.html
dashboard.html
perfil.html
styles.css
```

A `.css` file shared by the three pages ensures a button looks the same on all of them: changing the color once changes it on all three screens at once, instead of editing it in three separate places.

### > Connecting the file

```html
<head>
  <link rel="stylesheet" href="styles.css">
</head>
```

| Part | What it does |
|---|---|
| `<link>` | Element that connects external resources to the HTML |
| `rel="stylesheet"` | Says what kind of resource this is: a style sheet |
| `href="styles.css"` | Where the file is, relative to the HTML file's location |

### > Relative paths: the most common reason CSS "doesn't work"

If `styles.css` is in the same folder as `login.html`, `href="styles.css"` works. But if your structure is:

```text
pages/
  login.html
css/
  styles.css
```

`href="styles.css"` will fail: the browser looks for `styles.css` inside `pages/`, where it does not exist. The right path, from `pages/login.html`, would be `href="../css/styles.css"` (the `../` goes up one folder level before going down into `css/`).

## // Guided example: styling the Login button

```css
button {
    background-color: #6f4e37;
    color: white;
    padding: 12px 24px;
    border: none;
    border-radius: 8px;
}
```

Each line handles a visible part: `background-color` and `color` set the background and text colors; `padding` adds inner space (more on that in Module 05); `border: none` removes the browser's default border; `border-radius` rounds the corners.

## // Common mistakes

| Mistake | Why it happens | How to fix it |
|---|---|---|
| CSS "doesn't work" | Wrong `href` path, or file not saved | Open DevTools (Module 12 covers this better) and check whether the CSS was loaded |
| Forgetting the `;` at the end of a declaration | Easy to forget when typing fast | Every declaration ends with a semicolon, even the last one in the block |
| Mixing up `.class` and `#id` | The symbols look similar at first glance | `.` for class (reusable), `#` for id (unique) |
| A rule does not apply because another is more specific | Not understanding cascade/specificity yet | Class selectors beat element selectors; the last one declared wins in a tie |

## // Guided practice

1. Create the `styles.css` file at the root of your project.
2. Connect it in `login.html` using `<link rel="stylesheet" href="styles.css">`.
3. Write a rule for `body` setting a `font-family` (for example, `font-family: sans-serif;`).
4. Write a rule for `button`, using the colors from your Week 01 design system.
5. Save, reload the browser, and visually confirm the changes showed up.

## // Practice on your own

> **CHALLENGE**
> Add a `.link-secundario` class to the "Don't have an account yet?" link on the Login, styling it with a color different from your design system's primary color. Then, without using `!important` or duplicating the rule, try this: add a second rule for `a` (all links) with another color, and observe which of the two wins, and why.

## // Applying it to the week's project

1. Connect `styles.css` to the three pages (Login, Dashboard, Profile).
2. Set base styles for `body` (font, background color) using the Week 01 design system.
3. Style the main buttons and links.
4. Commit: `git commit -m "Add initial CSS and connect it to the three screens"`.

## // Checkpoint

> **BEFORE MOVING ON, THINK ABOUT THIS**
> You have two rules in your CSS: one for `button` and another for `.btn-cancelar`, and both set a different `background-color`. For a button with `class="btn-cancelar"`, which background color will it have, and why?

Answer: the color set in `.btn-cancelar`, because a class selector is more specific than an element selector, so it wins the cascade, regardless of the order in which the rules appear in the file.

## // Module summary

- [ ] I can explain what CSS is and why it exists separately from HTML.
- [ ] I know the anatomy of a rule: selector, property, value, declaration.
- [ ] I know the difference between element, class and id selectors.
- [ ] I understand, at an introductory level, what the cascade is and why one rule can "lose" to another.
- [ ] I can connect an external CSS file to the HTML, and I can diagnose a wrong relative path.
- [ ] My project's three screens already have a connected `styles.css`, with the first styles applied.

---

**Next module:** `05-box-model-and-units.md`: why your 300px element rarely takes up exactly 300px.

`Study Material // Coffee & Code`
