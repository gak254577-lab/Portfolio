# CLAUDE.md — Cinematic 3D Developer Portfolio

> Read this file at the start of every session. Update it after EVERY feature (see "Update rule" at the bottom).

## 0. Cross-chat sync (read first)

This file is the project memory. It is also published as an Artifact so any new chat can load it.
- **Start of every new chat about this project:** if the user mentions the portfolio or this project, use the Artifact tool (`list`, then `read`) to open "CLAUDE.md — Portfolio Project Memory" and the page "Cinematic 3D Developer Portfolio", and summarize in 2–3 lines where the project stands before doing anything else.
- **After every feature or change:** edit this file (Artifact `edit` with its url) and also keep `portfolio.html` in sync. Do this without being asked.
- Memory URL: https://claude.ai/artifact/R5Rdt5xaKLHxoooogt1zzB
- Page URL: https://claude.ai/artifact/BNL9YystWVGBphs3mMXmPU

## 1. Project kya hai

A single-page, cinematic, scroll-driven 3D developer portfolio for **[Your Name]** (placeholder, still to be replaced). The goal is that visitors feel they are moving through a 3D world rather than reading an ordinary portfolio. Priorities, in order: 3D storytelling + scroll animation, performance, responsive design.

- Deliverable: one self-contained file, `portfolio.html` (in `/mnt/user-data/outputs/`).
- Hosted as an Artifact: https://claude.ai/artifact/BNL9YystWVGBphs3mMXmPU
- Changes go through the Artifact tool's `edit` action (old_str/new_str) on that URL. For a large rewrite, edit the file and publish it with `url`.
- Visual reference: Cinder by Scrolltide (inspiration only, no copying). Tech-stack look is copied from the owner's other portfolio (portfolio-navneet-pratap-0001.vercel.app).

Sections (in order, one long scrolling page): Home (hero) → About → Tech Stack → Projects → Experience → Contact → Footer.

## 2. Kaunsa stack

| Area | Choice |
|---|---|
| Markup / style | Plain HTML + CSS in one file (CSS variables, no Tailwind) |
| 3D | Three.js r128 (UMD from cdnjs), vanilla, no React Three Fiber |
| Scroll animation | GSAP 3.12.5 + ScrollTrigger (cdnjs) |
| Smooth scroll | Lenis 1.1.13 (jsDelivr), wired to ScrollTrigger via `lenis.on('scroll', ScrollTrigger.update)` |
| Fonts | Google Fonts: Inter (all text), system sans fallback |
| Tech-stack icons | Simple Icons SVG paths, inlined in the page (22 icons) |
| Hosting | Claude Artifact (published page) |

Hard constraints of the hosted page:
- External scripts only from cdnjs.cloudflare.com, cdn.jsdelivr.net/npm, cdn.tailwindcss.com, code.jquery.com. Pin exact versions.
- No remote images, no fetch to other sites, no `window.storage` or Claude API calls.
- File must stay under 16 MB (currently about 43 KB).
- Typographic punctuation in visible text (’ “ ”).

## 3. Kya decide hua

- **Theme (updated 2026-11-05): LIGHT.** Page background is light grey/white like the reference (Madhav_Gediya_Portfolio.html): bg `#f2f2f4` with a soft radial gradient, ink `#0a0a0a`, body text `#52525b`, borders `#d9d9de`. The 3D knot stays dark metal, wireframe and particles are dark, fog matches the background. The only saturated colour is orange (`#ff6b00`) on the hero name letters when the cursor passes over them. The dark values in the next bullet are superseded; its rules for typography, buttons and subheaders still apply.
- **Earlier theme (superseded): strict grayscale design system.** Background `#050505`, surfaces `#0a0a0a`–`#121212`, text white, body text `#9ca3af`, borders `#1f1f1f`, no saturated colors anywhere (3D lights are white/neutral gray). Buttons are outlined pills that invert to white on hover. Subheaders are small uppercase with 0.2em spacing in `#737373`. Hero headline uses a white-to-silver gradient. Font is Inter. Amber and the cool blue-gray tint were removed. Tailwind is not used (single HTML file), so the design tokens live in CSS variables in `:root`.
- **Vanilla Three.js, not R3F/React**, because a published page cannot use ES-module imports. This is why Tailwind, Framer Motion and Drei are not used either.
- **One persistent fixed canvas** for the hero/scene; scroll progress drives camera, object position, scale and rotation through keyframes, so the story feels continuous.
- **3D object is procedural** (torus knot + wireframe icosahedron + particles). No GLB files, no invented model paths.
- **Tech Stack section = 2D badge cluster** (dark discs, white logos, spiral layout, cursor fisheye), copied from the owner's other site. This replaced an earlier 3D golf-ball orbit.
- **Removed on request:** the text-mask hover effect on headings.
- **Placeholders stay editable.** No invented links: every Live Demo / GitHub / LinkedIn / GitHub / Instagram / Resume link is `href="#"` for now.
- **Accessibility and fallback:** `prefers-reduced-motion` respected, WebGL failure falls back to a CSS gradient, burger menu is a real button with `aria-expanded`.
- **Performance:** pixel ratio capped (1.5 on mobile, 2 on desktop), fewer particles and lower geometry detail on mobile, render loops pause when the tab or section is hidden.
- **Lean builds:** small, targeted edits; no polish passes unless asked.

## 4. Kya ban chuka hai

- [x] Floating nav: transparent, blur on scroll, active-section underline, smooth scroll, mobile menu
- [x] Scroll progress bar and custom cursor: red dot (follows instantly) + red ring with soft glow (follows with a lag, grows on links, buttons, cards and tech icons); native cursor hidden on desktop with a mouse only, touch devices keep the normal behaviour
- [x] Hero redesigned like the reference layout: huge name "ABHISHEK" behind the user's own background-removed portrait; orange fill sweeps left to right across the name, following the cursor (portrait ignores pointer events so letters behind it still react; fill slides back when the cursor leaves). Grayscale portrait with a colour circle that follows the cursor (CSS mask, no WebGL), tagline top-left, info card bottom-left, GitHub/LinkedIn/Instagram pills bottom-right (placeholder links). Portrait fades out on scroll
- [x] Hero: staggered character reveal of "BUILDING DIGITAL EXPERIENCES", intro, two buttons
- [x] Scroll-driven 3D scene (camera, object, particles, lights respond to scroll and mouse)
- [x] About section ("BEYOND THE CODE.")
- [x] Tech Stack cluster: 22 icons, fade-in on scroll, floating motion, cursor magnify/push, name shown below on hover or tap
- [x] Projects: 4 full-width entries (CampusVoice, Intern AI, BhoomiRakshak, one editable slot) with description, stack line, Live Demo and GitHub buttons, scale-on-scroll reveal, hover glow
- [x] Experience timeline filled with real entries: 3rd year B.Tech CS, Data Analyst Intern at Trident Group, SIH finalist, Deloitte simulation certificate, VP of Tech Triumphs club (no dates or extra details added)
- [x] Contact section with Email, LinkedIn, GitHub, Instagram, Download Resume (placeholders)
- [x] Footer
- [x] Responsive layout and reduced-motion support
- [x] Strict monochrome design system applied across all components

**Not done / pending**
- [ ] Replace placeholders still left: resume link, email address, BhoomiRakshak links and stack, the fourth project, project screenshots
- [ ] Surname not provided: the hero shows only "ABHISHEK". If a surname is added, split into an outline word + a solid word like the reference
- [ ] Real project screenshots (previews are CSS panels for now)
- [ ] Unknown swirl icon from the reference screenshot (bottom-left) is not added yet
- [ ] Decide whether the original skill list (HTML, CSS, Java, Git, VS Code, Prompt Engineering, etc.) should also appear; the old `SK` data is still in the script but unused
- [ ] Optional extras: horizontal pinned project showcase, image distortion on hover, 3D timeline, 3D effect in the contact section, page-transition effects
- [ ] Not yet tested in a real browser: scroll feel, mobile layout, console errors, performance

## 5. Update rule (har feature ke baad)

After **every** feature, change, or removal, before replying to the user:
1. Tick or add the item in **"Kya ban chuka hai"**; move finished work out of "Not done / pending".
2. Add any new choice, constraint, or removal to **"Kya decide hua"** (with the reason).
3. Update **"Kaunsa stack"** if a library, font, or hosting detail changed.
4. Add one line to the change log below: date, what changed.
5. Keep this file short and accurate. If something here no longer matches the page, fix this file.

## 6. Change log

- 2026-11-02: First build (amber theme, Three.js scene, GSAP + Lenis, all sections).
- 2026-11-02: Theme changed to dark + white light.
- 2026-11-02: Skills became a golf-ball 3D orbit with names written on the balls (later replaced).
- 2026-11-02: Tech Stack replaced with a 22-icon badge cluster copied from the owner's other portfolio.
- 2026-11-02: Added heading text-mask hover effect, then removed it on request.
- 2026-11-02: Created this CLAUDE.md.
- 2026-11-04: Applied the strict black/white/gray design system (Inter, outlined buttons, silver hero gradient, uppercase subheaders).
- 2026-11-02: Published CLAUDE.md as an Artifact and added cross-chat sync instructions.
- 2026-11-05: Experience timeline updated with the user's real education, internship, hackathon, certificate and leadership entries.
- 2026-11-05: Tried a white marker-style highlight on "JOURNEY." in The Journey heading, then removed it on request (heading is plain again).
- 2026-11-05: Page switched from dark to light grey/white background (like the reference). Name set to Abhishek (stated by the user; nav logo AB). Hero name letters turn orange on hover, as in the reference.
- 2026-11-06: REVERTED the heading marquee on the user's request: section headings (h2) are plain static text again, with no scrolling strip, no outline repeats and no rolling-letter hover. (Superseded entry below kept for history.)
- 2026-11-06: (reverted above) All five section headings (h2) were moving text strips (marquees): the heading repeats with dashes between and scrolls left continuously at roughly the same speed on every section (the loop uses two identical halves and moves by 50% so it never jumps); every second repeat is drawn as outline text. Each letter is a small "roller": hovering a letter slides it up and the same letter rises from below (two stacked copies, 0.45s). Done by a script that rebuilds each h2 and keeps its text in aria-label; the hero name (h1) is not affected. Reduced-motion users get a still strip.
- 2026-11-06: Before the cursor reaches the Tech Stack the icons now visibly circle around: the whole spiral revolves faster (0.32 rad/s, one turn in about 20 seconds, was 45) and each badge also moves in its own small circle (radius about 0.22 of the spacing unit, each with its own phase) instead of a tiny back-and-forth drift. While the pointer is over the cluster the revolving still slows to 30%.
- 2026-11-06: Tech Stack icons must keep floating at all times, including while hovered: the hovered icon now keeps its own float (before it was held still), and the revolving only slows to about 30% (before 6%) while the pointer is over the cluster instead of almost stopping.
- 2026-11-06: Tech Stack is now always moving: the whole spiral slowly revolves around its center (about 0.14 rad/s, one full turn in roughly 45 seconds) and each badge also drifts twice as much as before. The revolving slows almost to a stop while the pointer is over the cluster so icons can be hovered easily, then speeds back up; hover detection and the push-away effect follow the rotated positions. Reduced-motion users get no rotation or drift.
- 2026-11-06: Tech Stack badges were crowding each other after being enlarged, so the cluster is now spread out: the spiral is 25% wider (radius factor 1.25), badges are 1.25x the spacing unit (not 1.5x), logo 54% of the badge, and the spacing unit is sized so the wider cluster still fits the screen width and about 58% of its height. Rule going forward: keep the badges open and spaced, do not let them touch.
- 2026-11-06: 3D knot now stays on the RIGHT side while the "Beyond the Code" screen is read (first two keyframes: x 2.7 on desktop, camera a bit further back at 5.8, scale 1.0, held until about 20% of its journey) so it no longer covers the About text; the rest of the original travel is unchanged.
- 2026-11-06: Tech Stack badges made bigger: each disc is now 1.5x the cluster spacing unit (was 1.02x), the logo inside fills 56% of the disc (was 52%), and the spacing unit stays capped by screen width and height so the section still fits one screen.
- 2026-11-06: 3D knot returned to the ORIGINAL continuous scroll-driven animation (the first version's keyframes: camera pushes in and out, the knot travels right, left, center, right, center, and grows to a big finish, rotating with scroll), but limited to start after the hero photo and end before it. Its progress now runs from the About section to the bottom of the page (instead of the whole page), and it is also scaled in/out by how far the hero has scrolled away (fully hidden until the hero is 40% scrolled past, and shrinks to nothing before the photo comes back when scrolling up). The per-section pose table (POSE) is no longer used. On mobile it is 0.6x and shifted down.
- 2026-11-06: REVERTED the separate-pages change on the user's request: the six sections are one scrolling page again (nav smooth-scrolls, active link follows scroll, no "Next" buttons, no hash routing). The 3D knot keeps its per-section positions, but the current section is now found from the scroll position (the section crossing the middle of the screen) instead of the URL hash, so the knot still glides from spot to spot as you scroll: hidden on Home, right of the About heading, then Skills left, Projects top-right and small, Experience left, Contact right and large.
- 2026-11-06: (superseded, reverted above) The six sections are now six separate pages inside the one file, using hash routing (#home, #about, #skills, #projects, #experience, #contact). Only the active page is shown, with a fade-up transition; nav links, the hero button and a "Next: ..." button at the bottom of each page switch pages (the last one goes back to Home), and every page opens at the top. Plain hash names only, no reserved ones. The tech-stack cluster re-measures itself when its page appears.
- 2026-11-06: The 3D knot now lives on every page after Home as one persistent canvas: it is hidden on Home, sits on the right of the About heading, then glides smoothly to a new spot on each later page (Skills left, Projects top-right and small, Experience left, Contact right and large). Scrolling inside a page adds a gentle rotation and drift. On mobile it stays small at the bottom-right.
- 2026-11-06: Tech Stack hover effect strengthened: pointing at one icon enlarges it (1.7x, kept in place, raised above the rest) and pushes all the other icons away from it, with the nearest ones moving the most (about 1.15 icon-widths) and the effect fading with distance; when the pointer is between icons the earlier gentle magnify/push is used. Springs are a bit snappier.
- 2026-11-05: Real links added. Social (hero pills and contact): GitHub https://github.com/gak254577-lab, LinkedIn https://www.linkedin.com/in/abhishek-4a4405345, Instagram https://www.instagram.com/abh_9087 (tracking parameter removed). CampusVoice: live https://campus-voice-new.vercel.app/, GitHub https://github.com/gak254577-lab/CampusVoiceNew, stack HTML · CSS · TypeScript. Intern AI: live https://intern-ai-lyart.vercel.app/, GitHub https://github.com/gak254577-lab/InternAI, stack JavaScript · HTML · CSS. All open in a new tab.
- 2026-11-05: 3D knot made properly scroll-linked inside the About section: its size, side-slide, upward drift and rotation now follow a smoothed 0-to-1 value for how far About has scrolled past (instead of an on/off switch), so it grows in from the right edge as About enters, turns and drifts while scrolling, and shrinks away as About leaves. Time-based spin kept slow.
- 2026-11-05: Fixes from the user's screenshots: (1) the random dark square in the About section was a particle sprite growing huge near the camera, so particles are now fixed-size round dots (sizeAttenuation off); (2) the 3D knot is now parked on the right side of the About heading, appears when About comes into view and shrinks away when it leaves (no travelling through other sections; its scroll keyframes are no longer used for position or scale); (3) section headings (h2) made smaller, clamp(2rem, min(5vw, 9vh), 4.4rem); (4) sections resized to fit one browser screen: smaller section padding, project rows about one screen tall with the preview capped at 52vh, tighter timeline, tech-stack cluster capped by viewport height.
- 2026-11-05: The earlier scroll-progress gate for the 3D knot left it invisible, so it was replaced: the knot now fades in as soon as the About section reaches the lower part of the screen (checked every frame from the section's position) and shrinks away again when scrolling back up into the hero. It stays parked on the left, never in the center.
- 2026-11-05: 3D knot now appears later: it stays hidden (scale gated) until the hero has scrolled past, and it is parked at its side position (not the center) so it can never shrink into the portrait when scrolling back up.
- 2026-11-05: Custom cursor changed to a red dot + glowing red ring (matches the user's reference screenshot). Red (#ff2d20) is a deliberate exception to the monochrome rule, like the orange name effect.
- 2026-11-05: Name effect changed from per-letter orange hover to an orange fill that sweeps left to right with the cursor (user's choice).
- 2026-11-05: Hero rebuilt around the user's own photo (cropped the frame, removed the background, embedded as WebP). The 3D knot starts at scale ~0 in the hero so it does not clash with the portrait and grows in at the About section. Same dark grayscale theme kept.
- 2026-11-05: Added hero portrait colour-reveal feature inspired by the uploaded Madhav_Gediya_Portfolio.html (technique only; his photos and text are not used). Uses a placeholder until the user's photo is provided. Scene knot moved toward center to sit behind the portrait.
