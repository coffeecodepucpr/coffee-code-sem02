# Module 03 | Semantic HTML and Forms

[Português](../docs/03-html-semantico-e-formularios.md) · English

`WEEK 02 // Web Interface, Part 1: Layout`

---

## // Before you start

In Module 02 you saw the difference between `<div>Sign in</div>` and `<h1>Sign in</h1>`: the second carries meaning, the first does not. This module goes deeper into exactly that point, and completes the full structure of the Login screen with a real form.

## // The problem: divs inside divs inside divs

A common pattern in poorly structured HTML:

```html
<div>
  <div>
    <div>Study Group Finder</div>
  </div>
  <div>
    <div>Home</div>
    <div>Groups</div>
    <div>Profile</div>
  </div>
</div>
```

Stop and ask: what does each `<div>` represent here? Without reading the content inside, it is impossible to know. The first one could be a header, a footer, a notice; there is no way to tell just by looking at the tag.

> **THE MAIN POINT**
> `<div>` is a generic element; it groups content, but says nothing about what that content *is*. Using `<div>` for everything is like labeling every box in a move as "stuff".

## // Semantic HTML

> **Semantic HTML, in simple words**
> It means using tags that describe the role of the content, instead of generic tags, so that the meaning is in the HTML itself, before any CSS.

Rewriting the previous example with meaning:

```html
<header>
  <h1>Study Group Finder</h1>
</header>
<nav>
  <a href="inicio.html">Home</a>
  <a href="grupos.html">Groups</a>
  <a href="perfil.html">Profile</a>
</nav>
```

Now a `<header>` is clearly a header, and `<nav>` is clearly a navigation area: for whoever reads the code, for the browser and for tools that depend on meaning.

### > The main semantic tags

| Tag | Represents |
|---|---|
| `<header>` | Header of a page or section |
| `<nav>` | Navigation area (menu, main links) |
| `<main>` | Main content of the page: should exist only once |
| `<section>` | A thematic section of content |
| `<article>` | Independent content, which would make sense on its own |
| `<footer>` | Footer of a page or section |

## // Why this really matters

Three concrete reasons, not just "good practice":

1. **Reading and maintenance**: whoever opens your code (including you, months later) understands the structure without reading every line of content.
2. **Accessibility**: screen readers (used by people with visual impairments) navigate by semantic region. A screen reader announces "navigation" when it reaches a `<nav>`; with a generic `<div>`, it has no such information.
3. **SEO, as a bonus**: search engines use the semantic structure to understand what the page is about. That is not the focus this week, but it is a positive side effect of doing the right thing.

> **`BUTTON` ≠ CLICKABLE `DIV`**
> **Wrong:** `<div onclick="...">Sign in</div>`. It may even look like a button, but to the browser it is just a div. It does not receive keyboard focus, is not announced as a button by screen readers, and depends on JavaScript even for the click to work.
>
> **Right:** `<button>Sign in</button>`. It is a real button. It receives keyboard focus (Tab key), is announced correctly, and comes with built-in click behavior, without needing anything extra.

The same goes for `<label>` and `alt`, which you already saw in Module 02: they are not visual details; they are meaning the HTML carries before CSS even comes into play.

## // Forms

> **FORM: IN SIMPLE WORDS**
> A form is a structured way of collecting information that a person fills in, to be processed in some way.

Even without any backend this week (remember Module 00: no real authentication yet), the Login form already represents, structurally, what will happen once the backend exists: fields the person fills in, and a button that triggers an action.

### > The elements of a form

```html
<form>
  <label for="email">Email</label>
  <input type="email" id="email" name="email" placeholder="you@example.com" required>

  <label for="senha">Password</label>
  <input type="password" id="senha" name="senha" required>

  <button type="submit">Sign in</button>
</form>
```

| Element/Attribute | What it does |
|---|---|
| `<form>` | Groups the fields that belong to the same submission |
| `<label>` | A field's label: `for` connects it to the matching field's `id` |
| `<input type="email">` | Text field, with basic e-mail format validation by the browser itself |
| `<input type="password">` | Text field that hides what is typed |
| `placeholder` | Example text that disappears when you type: it does not replace the `label` |
| `name` | Identifies the field when the form is sent to a server (important for future weeks, with a backend) |
| `required` | Prevents submission if the field is empty, without any extra code |
| `<button type="submit">` | Button that tries to submit the form |

### > Why `for` and `id` need to match

```html
<label for="email">Email</label>
<input type="email" id="email">
```

The value of `for` on the label needs to be identical to the `id` on the input. That connection does two things: clicking the text "Email" automatically focuses the field, and screen readers correctly announce which label belongs to which field. Without that connection, the label is just loose text next to the field: visually similar, structurally disconnected.

## // Focus states

When you navigate a form using the Tab key, the browser visually highlights the active field; this is called the **focus** state. You do not need to do anything for it to exist (the browser already shows a default outline), but it will be important to remember it when we get to CSS (Module 04) and Accessibility (Module 12): removing that outline without putting another visual cue in its place directly hurts people who navigate by keyboard.

## // Good example × bad example

**Bad example:**

```html
<div>Email</div>
<input type="text">
<div>Password</div>
<input type="text">
<div onclick="entrar()">Sign in</div>
```

No connected `label`, password in a regular `text` field (it shows the characters!), and a button that is actually a div.

**Good example:**

```html
<form>
  <label for="email">Email</label>
  <input type="email" id="email" name="email" required>

  <label for="senha">Password</label>
  <input type="password" id="senha" name="senha" required>

  <button type="submit">Sign in</button>
</form>
```

## // Common mistakes

| Mistake | Why it happens | How to fix it |
|---|---|---|
| `for` and `id` do not match | Typing fast, or copying/pasting without adjusting | Always check them side by side |
| Using `type="text"` for passwords | Forgetting there is a specific type | Use `type="password"` |
| Clickable `<div>` instead of `<button>` | Styling a div seems easier | Use `<button>` and style it: CSS handles the look (Module 04) |
| `placeholder` instead of `label` | Having both seems redundant | `placeholder` disappears when typing; without a `label`, nobody knows what to fill in after that |

## // Guided practice

Let's complete the structure of the Login screen you started in Module 02.

1. Open `login.html`.
2. Wrap the heading and the paragraph in a `<header>`.
3. Add a `<main>` right below, containing the rest of the screen.
4. Inside `<main>`, add a `<form>` with the e-mail and password fields, following the structure in this section.
5. Add the `<button type="submit">Sign in</button>`.
6. Open the file in the browser. Click the text "Email": does the field get focus? Use Tab to move between fields: does the order make sense?

## // Practice on your own

> **CHALLENGE**
> In the `cadastro.html` file (created in Module 02), add a complete form: name, e-mail, password, and a "Create account" button. Use `<header>` for the top of the page and `<main>` for the form. Confirm that each `label` is correctly connected to its field by clicking the label text.

## // Applying it to the week's project

1. Add `<header>` and `<main>` to your project's three screens (Login, Dashboard, Profile), even if the content inside is still simple.
2. Make sure the Login form has correct `label`, `type` and `required` on every field.
3. If the Dashboard or Profile has any action button (e.g. "Sign out", "Edit profile"), confirm they are `<button>`, not `<div>`.
4. Commit: `git commit -m "Add semantic HTML and Login form"`.

## // Checkpoint

> **BEFORE MOVING ON, THINK ABOUT THIS**
> Why is using `<button>` better than `<div class="button">` for an action, even though both can look identical after CSS?

Answer: `<button>` comes with native browser meaning and behavior: it receives keyboard focus, can be activated with Enter/Space, and is announced correctly by screen readers. A `<div>` has none of that by default; to match the behavior, you would have to add attributes and JavaScript by hand. Extra work to get something `<button>` already gives you for free.

## // Module summary

- [ ] I can explain why a generic `<div>` is a problem, even when it works visually.
- [ ] I know the main semantic tags and what each one represents.
- [ ] I know why `<button>` is different from a clickable `<div>`.
- [ ] I can build a form with `label`, `input`, `type`, `required` and `button` correctly connected.
- [ ] My project's Login screen has a complete semantic HTML structure.

---

**Next module:** `04-css.md`: the structure is ready. Time to make the page look like what was planned in Figma.

`Study Material // Coffee & Code`
