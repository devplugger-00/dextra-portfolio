# DEXTRA creative studio website

Static site for DEXTRA (founder: Dev). No build step is needed to run it.

## What is inside
- **`index.html` is fully self-contained** (CSS, JavaScript, data and artwork are inside it). You can copy that single file to a phone or any host and it works. The other files are the editable source.
- `index.html` standalone page (generated from `page.html` by `node build.js`)
- `styles.css`, `app.js` design system, interactions, routing
- `data.js` all text content: 48 projects, 9 services, process, contact details
- `art.js` the artwork engine. It draws every project visual as SVG from the data in `data.js`
- `config.js` contact form endpoint setting

## Run locally
Any static server works. From this folder:

    python3 -m http.server 8080
    # open http://localhost:8080

Opening `index.html` directly also works.

## Edit content
- Projects, services, process and contact details live in `data.js`.
- Contact details are defined once in `CONTACT` and used everywhere.
- After editing `page.html`, run `node build.js` to regenerate `index.html`.

## Deploy
Upload the folder to any static host (Netlify, Vercel, Cloudflare Pages, GitHub Pages).
Publish directory is the folder itself. There is no build command.

## Make the contact form send messages
The form has no server. Without configuration it validates input and prepares a message the visitor
copies and sends to Dev on Telegram, Discord or email.
To receive submissions directly, create a form on a service such as Formspree or Web3Forms and paste
its endpoint into `config.js` as `formEndpoint`. The form then POSTs JSON and shows success or error states.

## Contact links
- Telegram: https://t.me/dev_serenity (exact link)
- Email: mailto link
- Discord: no profile URL was supplied, so the button copies the username `@dev.criptic`.

## Notes and limits
- Stack: plain HTML, CSS and JavaScript with no required libraries. GSAP is optional and not loaded.
  React, TypeScript and Tailwind were not used because packages could not be installed in the build environment.
- Portfolio visuals are original vector artwork generated in code, not photographs or AI-generated images.
  All 48 projects are labelled as concepts. None is client work.
- Fonts load from Google Fonts without blocking the page. Offline, the site uses system fonts and the layout still works, but headlines are wider and less condensed.
- Fonts load from Google Fonts (Anybody, Hanken Grotesk, Instrument Serif, Space Grotesk, DM Mono).
- Add an `og:image`, a real domain and a sitemap before launch if you want rich link previews.

## Your own images (they always win)
- Put images in `images/` named after the project id, for example `images/harbor-roast.jpg`. The ids are listed in `PROMPTS.md`.
- Accepted types: jpg, png, webp, jpeg. If a file has another name, map it in `config.js` with `imageMap`.
- An image is always shown instead of the built-in artwork. The artwork appears only for a project that has no image.
- Images keep their own proportions, so nothing is cropped.
- After changing files or `config.js`, run `node build.js` to rebuild `index.html`. Note: `index.html` is one file, but your images stay in the `images/` folder next to it, so keep them together.

## 3D showcase
- The hero has a 3D coverflow of featured projects (swipe, drag, arrows, keyboard). Edit the list in `buildCoverflow` in `app.js`.
- Project cards, the project view and case studies tilt with the pointer on desktop. On phones and with reduced motion, tilt is turned off.
