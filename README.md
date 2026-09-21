# Noah Vastola — Personal Website

A personal website for recruiters: a single-page hub covering my profile, skills,
experience, and contact details, plus two dedicated pages that expand on those highlights —
a full resume and a case study on one project. Written as plain HTML, CSS, and JavaScript
with no framework, no build step, and no site builder, then deployed on GitHub Pages.

**Live site:** https://class.nvastola.com
**Repository:** https://github.com/nvastola/nvastola.github.io

## Reflection

I learned the reason why Claude Code was placing a script block containing the dark mode/light mode toggle at the top of every page. Initially, I thought this was redundant and unnecessary since the scripts.js file already handles the toggle. I asked Claude why it did this, and the answer was about when the code runs and not where it lives. scripts.js is loaded at the bottom of the body, so the browser has already run most of the page by the time it executes. If the theme was applied there, anyone using the dark mode would see a white flash on every page load. This changed how I think about script placement
