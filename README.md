# Abhishek - Portfolio

Cinematic 3D developer portfolio (plain HTML, CSS and JavaScript, no build step).

## Run it
- Quick: double-click `index.html`.
- Better in VS Code: install the **Live Server** extension, right-click `index.html`, choose *Open with Live Server*.
- It needs internet for the CDN scripts (Three.js, GSAP, Lenis) and Google Fonts.

## Files
- `index.html` - page structure (hero, about, tech stack, projects, journey, contact)
- `css/style.css` - all styling (colours are CSS variables in `:root`)
- `js/main.js` - all behaviour: 3D scene, scroll animation, cursor, tech-stack cluster, project cards
- `assets/portrait.webp` - background-removed portrait used in the hero
- `CLAUDE.md` - project notes: stack, decisions, what is built, change log

## Where to edit common things
- Name, tagline, links: `index.html` (hero and contact sections)
- Projects (title, text, stack, links): the `PR` array in `js/main.js`
- Journey entries: the `.tl` block in `index.html`
- Tech stack icons: the `IC` array in `js/main.js`
- Colours and sizes: `:root` and the section rules in `css/style.css`
- 3D knot path: the `K` keyframes array in `js/main.js`
