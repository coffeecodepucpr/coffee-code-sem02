# Coffee & Code | WEEK 02 | Web Interface (Part 1: Layout)

[Português](README.md) · English

```text
> module: sem-02
> topic: web interface (layout)
> status: online
> coffee loaded
```

Material for **Week 02** of the Coffee & Code track, a technology club founded by Software Engineering students at PUCPR and open to anyone who wants to learn by building.

In Week 01 you planned. This week you build. That Figma prototype is a representation of the interface; it is not the interface. A Figma file does not run in anyone's browser.

Week 02 exists to close that gap: take what was decided and turn it into real HTML and CSS. By the end of the week you open your three screens in the browser, resize the window down to the size of a phone, and nothing breaks.

> **About the language:** the English material lives in [`docs-eng/`](docs-eng/), with the same structure as [`docs/`](docs/) (Portuguese); the READMEs have an English version with the `.en.md` suffix. The diagrams, the runnable example and the example project's file and class names stay in Portuguese.

## Where to start

**[docs-eng/00-start-here.md](docs-eng/00-start-here.md)**: read this one first. It explains the week's path and how to study.

Then follow the modules in order:

| # | Module | About |
|---|---|---|
| 01 | [How the web works](docs-eng/01-how-the-web-works.md) | Browser, server, and the role of HTML/CSS/JS |
| 02 | [HTML](docs-eng/02-html.md) | Structure: tags, elements, parent/child/sibling |
| 03 | [Semantic HTML and forms](docs-eng/03-semantic-html-and-forms.md) | Meaning in the markup and the Login form |
| 04 | [CSS](docs-eng/04-css.md) | Selectors, cascade, connecting CSS to HTML |
| 05 | [Box Model and units](docs-eng/05-box-model-and-units.md) | `border-box`, padding, margin, px/rem/%/vh |
| 06 | [Flexbox](docs-eng/06-flexbox.md) | Axes, alignment, distribution |
| 07 | [Grid](docs-eng/07-grid.md) | Rows, columns, `fr`, and when not to use Flexbox |
| 08 | [Responsiveness](docs-eng/08-responsiveness.md) | Viewport, breakpoints, mobile-first |
| 09 | [From Figma to code](docs-eng/09-figma-to-code.md) | Breaking down a screen before coding |
| 10 | [Tailwind](docs-eng/10-tailwind.md) | Utility-first CSS with Tailwind v4 |
| 11 | [Design System in code](docs-eng/11-design-system-in-code.md) | Figma tokens as CSS Custom Properties |
| 12 | [Accessibility](docs-eng/12-accessibility.md) | Contrast, focus, keyboard navigation |
| 13 | [Componentization and themes](docs-eng/13-componentization-and-themes.md) | Reusable components, light/dark theme |
| 14 | [Guided project](docs-eng/14-guided-project.md) | Building the three screens, from start to finish |

And, to look up whenever you need:

- [Runnable example](docs/example/): the three screens in plain HTML/CSS, for reference
- [Challenges](docs-eng/challenges.md): optional, to go beyond what is asked
- [Deliverable](docs-eng/deliverable.md): final checklist before closing the week

## The runnable example

The [`docs/example/`](docs/example/) folder has a reference implementation of the three screens, in plain HTML and CSS. Download the repository and open `index-semana02.html` in the browser to move between them, or [open it online](https://coffeecodepucpr.github.io/coffee-code-sem02/docs/example/index-semana02.html).

It is **reference material, not an answer key**. Your project has its own screens, decided in Week 01: the example is there for you to see one possible solution when you get stuck, not to copy.

## The deliverable

At the end of Week 02, the repository of **your project** (not this one) should have the three screens of your prototype implemented:

```text
login.html
dashboard.html
perfil.html
css/
└── styles.css    ← shared by all three
```

The three pages need to open without errors, use semantic HTML, share the same CSS built on your design system's tokens, and work from ~375px up to ~1200px without horizontal scrolling.

The full checklist is in [docs-eng/deliverable.md](docs-eng/deliverable.md).

> **Beauty is not the criterion.** A simple structure with correct semantic HTML, CSS organized in variables and working responsiveness is worth more, this week, than an elaborate look with `<div>` instead of `<button>` that breaks on a phone.

## Class submissions

Projects from people who submitted Week 02. Want to submit yours? See [how to submit](entregas/README.en.md).

| Person | Project | About | Links |
|---|---|---|---|
| Pedro Henrique Gouveia | No name yet | Login, sign-up, dashboard with engineering courses and profile, with Tailwind | [own repository](https://github.com/gorfofnf/coffee-and-code/tree/main/semana_2_entregavel) |
| Guilherme Barbosa | Shelf Hub | Personal library of movies, series, books, games and other content | [folder](entregas/Guilherme%20Barbosa/) · [Figma](https://www.figma.com/proto/qzzGhfapnxVoYsicLXboxt/Shelf-Hub?node-id=5-788&p=f&t=A6Dyj4L6kNFV6My3-1&scaling=min-zoom&content-scaling=fixed&page-id=0%3A1&starting-point-node-id=3%3A7) · [view screens](https://coffeecodepucpr.github.io/coffee-code-sem02/entregas/Guilherme%20Barbosa/login.html) |
| Luis Medina | Estom | Price tracking for online products | [folder](entregas/Luis%20Medina/) · [Figma](https://www.figma.com/proto/oL9MehNA1Gea3Zhzh8I69z/Sem-t%C3%ADtulo?node-id=0-1&t=SoRcZQfwCZWOKUVi-1) · [view screens](https://coffeecodepucpr.github.io/coffee-code-sem02/entregas/Luis%20Medina/index.html) |
| Mikhail Kalinin | Online Learning Platform | Online course platform connecting teachers and students | [folder](entregas/Mikhail%20Kalinin/) · [view screens](https://coffeecodepucpr.github.io/coffee-code-sem02/entregas/Mikhail%20Kalinin/pages/login.html) |
| Rodrigo Fagnani | FixAqui | Connects clients with professionals for small services | [folder](entregas/Rodrigo%20Fagnani/) · [Figma](https://www.figma.com/proto/8NBkV8NkIjlPJSXg4am1bf/Untitled?node-id=0-1&t=aBlZ6abbcyV5SmwH-1) · [view screens](https://coffeecodepucpr.github.io/coffee-code-sem02/entregas/Rodrigo%20Fagnani/login.html) |

## What is not part of this week

To avoid unnecessary anxiety: no backend, database or real authentication. Working JavaScript is not expected. Tailwind is optional: plain CSS is an equally valid submission. And pixel-perfect fidelity to Figma is not expected: small adjustments when moving from a static design to real HTML/CSS are normal.

## Ongoing project

All modules use the same fictional project from Week 01: the **Study Group Finder** (*Buscador de Grupos de Estudo*), a platform for students to find classmates studying the same subject. If you have your own project, the reasoning in each module applies the same way: just change the name.

## How it works

Coffee & Code is **100% online**. Each module was written to be self-contained: you study at your own pace, and you can move ahead faster, go back to previous weeks and look things up during the project.

The weekly meetings, also online, are there to answer questions, review concepts, code together and show what you have built, **not to lecture** (Brasília time, UTC-3):

- **Wednesday**: 8:00 PM to 9:30 PM
- **Saturday**: 10:00 AM to 11:30 AM

Both cover the same content. Pick whichever fits your week best, and you do not need to stay on the call for the whole time.

## Stuck?

Bring a specific question to the meeting or to Discord. `"I got stuck on X, I already tried Y"` usually gets solved much faster than `"I didn't understand anything in module Z"`.

And remember: not knowing something is not a problem. Knowing how to research is part of the field.

## Diagrams

All the diagrams used in the modules are in [`docs/assets/`](docs/assets/), as editable SVG.

## Previous weeks

- [WEEK 01: Kickoff & Design System](https://github.com/coffeecodepucpr/coffee-code-sem01)

Full track and upcoming weeks: [Coffee & Code profile](https://github.com/coffeecodepucpr)

---

```text
HTTP 418: I'm a teapot
> ready to code
```
