# Module 00 | Start Here

[Português](../docs/00-comece-aqui.md) · English

`WEEK 02 // Web Interface, Part 1: Layout`

---

## // Welcome to Week 02

In Week 01 you planned. This week you build.

If you followed Week 01 to the end, your repository already has a `/docs` folder with requirements, user stories, a documented design system and a clickable prototype in Figma. None of that, on its own, runs in anyone's browser. A Figma file is a representation of the interface; it is not the interface.

Week 02 exists to close that gap: take what was decided and turn it into real HTML and CSS, which any browser can open and display.

> **WHERE WE CAME FROM**
> Week 01: idea → problem → user → requirements → user stories → flow → UX/UI → Figma → design system → initial architecture.
>
> That sequence ends in decisions. Week 02 starts exactly where it stopped.

## // What you are going to build

Three pages, the same three screens you designed in Figma:

- **Login**
- **Dashboard**
- **Profile**

By the end of the week, you should be able to open these three pages in a browser, see the layout you planned, and resize the window without anything breaking, from the size of a monitor down to that of a phone.

## // What "web interface" means

A web interface is the part of a system that lives inside a browser: the set of pages, elements and styles a person interacts with directly. "Frontend" is the name given to the work of building that part: everything that runs in the browser of the person using the system, as opposed to the "backend", which runs on a server, out of the user's direct reach.

This week you work entirely on the frontend, and on a specific slice of it: structure and appearance, without complex dynamic behavior.

## // What will NOT be done yet

This needs to be very clear before you start, because it is easy to confuse "the screen exists" with "the feature exists".

**This week:**
- structure (HTML)
- visuals (CSS)
- layout (Flexbox, Grid)
- responsiveness (the screen adapts to any size)

**Not yet:**
- real authentication
- database
- communication with an API
- complex programming logic
- anything backend

A "Sign in" button can, and should, exist visually this week, without actually authenticating anyone. That is not a limitation of your work; it is the right scope for this stage. Real authentication is a topic for future weeks of the club, once the interface already exists.

> **CONCEPT: IN SIMPLE WORDS**
> A page can be visually 100% done and functionally 0% done at the same time. That is not a problem; it is exactly what "static interface" means, and it is exactly this week's deliverable.

## // What we will use from Week 01

Three things, specifically:

1. **The Figma prototype**: every screen you build this week starts from a screen that already exists there. You are not inventing a new layout, you are translating a layout that was already decided.
2. **The design system** (`/docs/design-system.md`): the colors, typography and spacing you defined are not chosen again; they become real values in CSS.
3. **The ongoing project**: if you followed Week 01 with the Study Group Finder (*Buscador de Grupos de Estudo*, a platform for students to find study groups), this is the same project that gets an interface now. If you already had your own project, the reasoning is identical: just change the name.

## // From Week 01 to Week 02, on a single map

```
WEEK 01                            WEEK 02
──────────                         ──────────
FIGMA                              PAGE STRUCTURE
  ↓                                  ↓
                                    HTML
                                     ↓
                                    STYLING
                                     ↓
                                    CSS
                                     ↓
                                    LAYOUT
                                     ↓
                                    FLEXBOX / GRID
                                     ↓
                                    RESPONSIVENESS
                                     ↓
                                    TAILWIND
                                     ↓
                                    IMPLEMENTED SCREEN
```

The question that guides the whole week:

> How do you turn an interface planned in Figma into a page the browser can render?

Every module from here on exists to answer a piece of that question. HTML, CSS, Flexbox, Grid, responsiveness and Tailwind are not five unrelated topics; they are five tools that solve different parts of the same problem.

## // The two tracks

**If you are just starting**: you have never written an HTML tag, never opened a `.css` file. The main path of each module assumes this and does not skip any step.

**If you already have experience**: you have built interfaces before. Each module has deeper-dive blocks, clearly marked, after the essential content: componentization, design tokens in CSS, light/dark themes, advanced accessibility.

Nobody works on a different project. Everyone builds the same three screens: what changes is the depth.

## // Map of Week 02

| Module | Content | You will be able to |
|---|---|---|
| 00 | Start here | Know where this week comes from and where it goes |
| 01 | How the web works | Explain what happens between opening a file and seeing a screen |
| 02 | HTML: structure | Structure a page from scratch |
| 03 | Semantic HTML and forms | Give the structure real meaning, build the Login |
| 04 | CSS: how the browser styles | Connect CSS to HTML and apply the first rules |
| 05 | Box Model, sizes and spacing | Predict the exact size of any element |
| 06 | Flexbox | Align and distribute elements in one dimension |
| 07 | CSS Grid | Arrange cards in two dimensions |
| 08 | Responsiveness | Adapt the layout to any screen width |
| 09 | From Figma to code | Break down a screen before coding it |
| 10 | Tailwind CSS | Write CSS through utility classes |
| 11 | Design System in code | Carry Figma tokens over to real variables |
| 12 | Accessibility | Build interfaces that work for more people |
| 13 | Componentization and themes | Recognize repeated patterns, light/dark theme |
| 14 | Guided project | Build Login, Dashboard and Profile from start to finish |
| 15 | Review, testing and submission | Confirm the deliverable is complete |

Each module is a standalone file, but they were written to be read in this order: HTML needs to exist before CSS, basic CSS needs to exist before Flexbox/Grid, and both need to exist before Tailwind makes any sense.

---

**Next module:** `01-how-the-web-works.md`: before writing the first tag, understand what the browser really does with it.

`Study Material // Coffee & Code`
