# CLAUDE.md — Tom N Jerry's Sports Bar Website

## Always Do First
- **Invoke the `frontend-design` skill** before writing any frontend code, every session, no exceptions.
- **Invoke the `web-design-guidelines` skill** alongside `frontend-design` for every new page or major component.

## Project Context
- This is a sports bar website rebuild for **Tom N Jerry's**
- Vibe: bold, energetic, welcoming — sports-first, neighborhood bar feel
- Key sections typically include: Hero, Menu/Food & Drinks, Events/Specials, Hours & Location, Gallery, Contact/Reservations

## Reference Images
- If a reference image is provided: match layout, spacing, typography, and color exactly. Swap in placeholder content (images via `https://placehold.co/`, generic copy). Do not improve or add to the design.
- If no reference image: design from scratch with high craft (see guardrails below).
- Screenshot your output, compare against reference, fix mismatches, re-screenshot. Do at least 2 comparison rounds. Stop only when no visible differences remain or user says so.

## Local Server
- **Always serve on localhost** — never screenshot a `file:///` URL.
- Start the dev server: `node serve.mjs` (serves the project root at `http://localhost:3000`)
- `serve.mjs` lives in the project root. Start it in the background before taking any screenshots.
- If the server is already running, do not start a second instance.

## Screenshot Workflow
- Puppeteer is installed at `C:/Users/dflet/AppData/Local/Temp/puppeteer-test/`. Chrome cache is at `C:/Users/dflet/.cache/puppeteer/`.
- **Always screenshot from localhost:** `node screenshot.mjs http://localhost:3000`
- Screenshots are saved automatically to `./temporary screenshots/screenshot-N.png` (auto-incremented, never overwritten).
- Optional label suffix: `node screenshot.mjs http://localhost:3000 label` → saves as `screenshot-N-label.png`
- `screenshot.mjs` lives in the project root. Use it as-is.
- After screenshotting, read the PNG from `temporary screenshots/` with the Read tool — Claude can see and analyze the image directly.
- When comparing, be specific: "heading is 32px but reference shows ~24px", "card gap is 16px but should be 24px"
- Check: spacing/padding, font size/weight/line-height, colors (exact hex), alignment, border-radius, shadows, image sizing

## Output Defaults
- Single `index.html` file, all styles inline, unless user says otherwise
- Tailwind CSS via CDN: `<script src="https://cdn.tailwindcss.com"></script>`
- Placeholder images: `https://placehold.co/WIDTHxHEIGHT`
- Mobile-first responsive

## Brand Assets
- Always check the `brand_assets/` folder before designing. It may contain logos, color guides, style guides, or images.
- If assets exist there, use them. Do not use placeholders where real assets are available.
- If a logo is present, use it. If a color palette is defined, use those exact values — do not invent brand colors.

## Sports Bar Design Guardrails
- **Colors:** Dark, rich palette — deep charcoal/black base with amber/gold or red accent. Never default Tailwind blue/indigo. Think: stadium lights, beer, energy.
- **Shadows:** Never flat `shadow-md`. Use layered, color-tinted shadows (amber/warm tones) with low opacity for glow effects on CTAs and hero elements.
- **Typography:** Bold condensed display font for headings (e.g., Oswald, Barlow Condensed, Black Han Sans). Clean readable sans for body. Tight tracking (`-0.02em`) on headings, generous line-height (`1.7`) on body.
- **Gradients:** Dark-to-darker backgrounds with warm accent radial glows. Add grain/texture via SVG noise filter for depth and a "worn bar" feel.
- **Animations:** Only animate `transform` and `opacity`. Never `transition-all`. Use snappy easing for CTAs, subtle parallax on hero.
- **Interactive states:** Every clickable element needs hover, focus-visible, and active states. No exceptions.
- **Images:** Add a gradient overlay (`bg-gradient-to-t from-black/70`) on hero/gallery images. Use warm color treatment layers with `mix-blend-multiply`.
- **Spacing:** Generous padding on sections (py-20+), tighter on cards. Consistent spacing tokens — not random Tailwind steps.
- **Depth:** Base (dark bg) → Elevated (card surfaces) → Floating (nav, modals). All at distinct z-planes with shadow differentiation.

## Hard Rules
- Do not add sections, features, or content not in the reference
- Do not "improve" a reference design — match it
- Do not stop after one screenshot pass
- Do not use `transition-all`
- Do not use default Tailwind blue/indigo as primary color
- Do not use light/pastel color schemes — this is a sports bar, keep it bold and dark
