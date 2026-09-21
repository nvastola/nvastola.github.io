# Noah Vastola — Personal Website

A hand-built personal website for recruiters: a single-page hub covering my profile, skills,
experience, and contact details, plus two dedicated pages that expand on those highlights —
a full resume and a case study on one project. Written as plain HTML, CSS, and JavaScript
with no framework, no build step, and no site builder, then deployed on GitHub Pages.

**Live site:** https://class.nvastola.com
**Repository:** https://github.com/nvastola/nvastola.github.io

## Structure

| File | Purpose |
| --- | --- |
| `index.html` | Single-page hub — profile, skills, experience, projects, certifications, contact |
| `resume.html` | Full resume: education, certifications, complete experience record, skills by domain |
| `project.html` | Case study on the Jenkins → AWS ECR → EKS deployment pipeline |
| `styles.css` | Shared stylesheet — one design system across every page |
| `js/scripts.js` | Shared behavior — theme toggle, mobile nav, scroll reveal, project filtering |
| `projects/projects.html` | Extended portfolio listing (beyond the assignment requirements) |
| `blog/` | Long-form build logs for individual projects |

Both themes are supported; the choice is stored in `localStorage` and persists across pages.

## Reflection

The thing I did not understand at first was the small `<script>` block the agent put in the
`<head>` of *every* page, above the content, that reads `localStorage` and adds a `dark` class
to `<html>`. It looked redundant — `js/scripts.js` already handles the theme toggle, so why
duplicate part of that logic in the head of nine different files instead of keeping it in one
place? I asked the agent why it could not just live in `scripts.js` with everything else. The
answer was about *when* the code runs, not where it lives: `scripts.js` is loaded at the bottom
of the body, so the browser has already painted the page by the time it executes. If the theme
class were applied there, anyone using dark mode would see a white flash on every single page
load — the "flash of unstyled content." The head script has to be inline and blocking precisely
because it must run before the first paint, which is also why it is deliberately tiny. That
reframed how I think about script placement: `defer`, `async`, and position in the document are
not stylistic preferences, they are a statement about what has to be true before the user sees
anything.

## Built with

Google Antigravity IDE · Git · GitHub Pages · plain HTML/CSS/JS
