# CLAUDE.md — Frontend Website Rules

## Always Do First
- **Invoke the `frontend-design` skill** before writing any frontend code, every session, no exceptions.

## Client Context — Emrik Refrigeration & AC

### Business Identity
- **Business name:** Emrik Refrigeration & AC
- **Industry:** HVAC and commercial refrigeration
- **Owner:** Rick
- **Physical address:** None — new business, no fixed location. Do NOT include an address in schema or contact info.
- **Phone (for site — GHL tracking number):** TBD — will replace (361) 815-3667 once GHL number confirmed
- **Phone (current):** (361) 815-3667 / tel:+13618153667 — use until GHL number confirmed
- **Email:** emrikrefrigerationandac@gmail.com
- **Location base:** Corpus Christi, South Texas
- **Established:** 2025 (new business, experienced team — years of hands-on experience)
- **Domain:** emrikrefrigeration.com — use as canonical/OG base URL

### Credentials (display prominently on every page)
- TDLR License # TACLA144129C
- EPA Universal certified
- Licensed and insured in Texas
- Registered with the Texas Department of Licensing & Regulation (TDLR)

### Service Area (in priority order — use this order everywhere)
1. Corpus Christi (primary market)
2. Portland, TX
3. Rockport, TX
4. Aransas Pass, TX
5. Calallen, TX
6. Ingleside, TX

All cities are in the Corpus Christi metro and surrounding South Texas coastal area. The site should feel locally rooted in this region. San Antonio and Victoria can be mentioned in general "service area" copy but do NOT build dedicated pages for them.

### Services (six dedicated pages — in priority order)
1. **AC Repair & Service** — highest search volume, most important page
2. **AC Installation & Replacement** — highest ticket residential job, different search intent from repair
3. **Commercial Refrigeration Repair** — walk-ins, reach-ins, ice machines; high urgency, low competition in South Texas
4. **Commercial HVAC Service** — offices, restaurants, retail; higher value clients, repeat business
5. **Heating Repair & Installation** — captures seasonal search spike every fall/winter
6. **AC Maintenance & Tune-Up** — recurring revenue, spring seasonal searches, sells the ongoing relationship

### Key Differentiators (feature prominently)
- 24/7 availability — same-day emergency and after-hours service
- Free residential and commercial installation estimates
- Free commercial/refrigeration equipment surveys
- Residential financing available
- Transparent pricing — "straight answers and options with no BS and no hidden costs" (Rick's exact phrasing — use it)
- Licensed, insured, TDLR registered — credentials matter in this industry
- New business, experienced team — "from your home to your office or restaurant, more than capable"
- Focus on open communication — "smooth, swift outcome no matter the situation"

### Brand Voice & Tone
- Direct, plainspoken, confident — not corporate, not salesy
- Use Rick's actual phrasing where possible: "straight answers," "no BS," "no hidden costs," "smooth, swift outcome"
- Avoid HVAC industry jargon unless the audience is clearly commercial
- Open communication and client satisfaction are core values — weave naturally
- New business but experienced team — lean into the expertise, not the newness

### Brand Colors
- Red (primary) — custom hex, trustworthy and professional, not aggressive. Suggested: ~#C0392B or similar — NOT default Tailwind red
- White (backgrounds)
- Blue (secondary accent) — custom hex, NOT default Tailwind blue
- Always check brand_assets/ for logo — refine palette to match logo colors exactly

### Social Proof
- Do NOT mention Google reviews — only 3 reviews, too few to feature
- Trust signals instead: TDLR license number, EPA certification, licensed & insured, free estimates, 24/7 availability

### Brand Tagline
- TBD — confirm with Rick or develop based on "straight answers, no BS" positioning

### Assets Status
- Logo: Ready — check brand_assets/ folder before designing. Use it, do not use a text wordmark.
- Photos: TBD — use placehold.co until Rick provides real photos
- Hero background: TBD — use placeholder until provided
- CTA section background: TBD — use dark overlay placeholder until provided

### Site Architecture
- Homepage (index.html)
- About Us (about.html)
- Contact / Thank You (thank-you.html)
- 6 service pages at /services/[service-name].html:
  - ac-repair-service.html
  - ac-installation-replacement.html
  - commercial-refrigeration-repair.html
  - commercial-hvac-service.html
  - heating-repair-installation.html
  - ac-maintenance-tune-up.html
- 6 city pages at /areas/[city].html (one per city, in priority order):
  - corpus-christi.html (primary — most important, ~800-900 words)
  - portland.html (~600-700 words)
  - rockport.html (~600-700 words)
  - aransas-pass.html (~500-600 words)
  - calallen.html (~500-600 words)
  - ingleside.html (~500-600 words)

### Nav Structure
- Services dropdown (all 6 service pages)
- Areas We Serve dropdown (all 6 city pages)
- About
- Contact (links to contact section on homepage)
- Call Now button (prominent, orange/red CTA)

### Final CTA Section Pattern (apply on every page)
- All pages use the same final CTA section just before the footer
- Dark overlay on a background image (or solid dark if no image yet)
- Headline + supporting copy + dual CTAs (Call + Get a Free Quote)
- Same treatment across all pages for brand consistency

### Hero Layout Standard (LOCKED — apply to every homepage, service, and city page)
The hero is a single dark-left / bright-equipment-right composition. Build every new page's hero to match this exactly — do not redesign per page.

- **Full-viewport hero:** `min-height:100svh` (use `dvh`/`svh` for mobile correctness), content vertically centered. On subpages, the breadcrumb sits above the H1 inside the hero content.
- **Background:** desktop video / equipment photo covering the hero; mobile swaps to a static hero image (`.hero-mobile-img` shown ≤767px, `.hero-video` hidden).
- **Text column width:** `--hero-content-max: 700px` on `.hero-content`. Wide, comfortable wrapping (fewer/wider lines) — NEVER a narrow crammed column. The H1's own `max-width` in `ch` governs line breaks; keep `--hero-content-max` larger than that so it never becomes the binding constraint.
- **Left shift:** `--hero-pad-left: clamp(1.5rem, 5vw, 4rem)`. `.hero-inner` is NOT centered (`max-width:none; margin:0; padding:0 var(--pad-x) 0 var(--hero-pad-left)`) so the whole block hugs near the left edge with a clean, intentional margin.
- **Gradient (equipment is the focal point):** `.hero-overlay` linear-gradient at ~100deg holds strong dark (≈.9 alpha) only across the left ~40% (behind the text), then fades fast — roughly `.45` at 60%, `.25` at 80%, near-clear (`.05`) at 100%. The equipment on the right must read as the bright visual focus; the left text zone must stay dark enough for white/red text to remain crisp. Keep the supporting red/cobalt radial accents.
- **Mobile (≤767px):** `.hero-content { max-width:none; }` (full width) and `.hero-inner { padding-left:var(--pad-x); }` (symmetric padding) — the desktop left-shift and width cap do NOT apply.
- **Type scale & spacing (IDENTICAL on every page — copy these exact values, do not diff against index.html):**
  - **H1** (`.hero-h1`): `font-size:clamp(2.6rem,6.4vw,5rem)`; `max-width:16ch`; `font-weight:800`; `letter-spacing:-.035em`; white, `.accent` span in `--red300`.
  - **Subhead** (`.hero-sub`): `font-size:1.28rem` (`clamp(1.05rem,1.7vw,1.28rem)`); `max-width:54ch`; `margin-top:1.5rem`; color `#C7D1E0`.
  - **CTA row** (`.hero-cta-row`): `margin-top:2.2rem`.
  - **Trust badges** (`.trust-row`): `margin-top:2.4rem`. Badge style (`.trust-badge`) is identical across all pages — do not restyle.
  - **Eyebrow** (`.eyebrow`): identical across all pages — `font-size:.74rem`, `letter-spacing:.18em`, uppercase, `--red` (or `--red300` via `.on-dark`); do not restyle.
- **Breadcrumb (subpages only — faint trail, NOT a button bar):** `.crumb` `font-size:.72rem`; `margin-bottom:2rem` (generous gap above the eyebrow); base text `rgba(255,255,255,.34)`; links `rgba(255,255,255,.5)` (hover `.85`); separators (`.sep`) `rgba(255,255,255,.22)`; current page (`.current`) `rgba(255,255,255,.6)`. Keep the BreadcrumbList JSON-LD. It must read as a quiet navigational note, never compete with the H1.
- **Source of truth:** `--hero-content-max` and `--hero-pad-left` live in `:root` under a labeled comment; new pages inherit the pattern by carrying those two variables plus the `.hero-inner` / `.hero-content` / `.hero-overlay` rules.

### Open Items / To Confirm With Rick
- GHL tracking phone number (replaces (361) 815-3667 site-wide when confirmed)
- Real photos
- Brand tagline
- Financing program details (which lender/program?)

## Content Writing Methodology
For all page COPY/content, read and follow SEO-CONTENT-PROMPT.md (in the project root) as the PRIMARY writing methodology before writing any page content. Apply the COMPLETE methodology — not just the Words to Avoid list. This includes the writing mission, all optimization guidelines (for both Google Algorithm and AI Systems), the balanced writing approach, content structure, language guidelines, quality signals, and the Words to Avoid list. The Local SEO Requirements below govern TECHNICAL implementation (meta tags, schema, sitemap, file structure) and work in tandem. If there is ever a conflict on wording or content approach, SEO-CONTENT-PROMPT.md takes precedence.

## Local SEO Requirements

Every page built for this site must follow these SEO standards. This is a local service business — local SEO is the primary lead driver.

### Per-Page Metadata (every page needs all of these)
- Unique `<title>` tag, under 60 characters, format: "[Page Topic] | Emrik Refrigeration & AC"
- Unique `<meta name="description">`, under 160 characters, includes a service, a city, and a call to action with the phone number
- `<meta name="keywords">` with relevant local terms (service + city combinations)
- `<meta name="robots" content="index, follow, max-image-preview:large, max-snippet:-1, max-video-preview:-1">`
- `<link rel="canonical">` pointing to that page's own URL using https://emrikrefrigeration.com as the base
- `<html lang="en">` and proper viewport meta

### Open Graph + Twitter Cards (every page)
- og:title, og:description, og:url, og:type, og:image, og:locale, og:site_name
- twitter:card (summary_large_image), twitter:title, twitter:description, twitter:image
- Base URL: https://emrikrefrigeration.com

### Structured Data (JSON-LD)
- Homepage: HVACBusiness LocalBusiness schema
- Include: name ("Emrik Refrigeration & AC"), telephone, email, priceRange, openingHoursSpecification (24/7), areaServed (all 6 cities), hasOfferCatalog (all 6 services)
- Include TDLR license number in schema additionalProperty
- Do NOT include a PostalAddress — no fixed address
- Service pages: add Service schema referencing the parent business
- City pages: reference areaServed for that specific city
- Validate all schema at search.google.com/test/rich-results before launch

### Visible On-Page SEO
- Each page must have exactly ONE `<h1>` with the page's primary keyword
- H2/H3 used for section hierarchy, no skipped levels
- City names must appear in human-readable body text, not just metadata
- Service + city combinations should appear naturally in copy
- All images need descriptive alt text including service/location context

### City Pages — Critical Anti-Duplicate Rule
- Each city page MUST have 30-40% unique content minimum
- Do NOT just swap the city name — Google penalizes doorway pages
- Reference local landmarks, neighborhoods, highways, area-specific details
- Unique intro paragraph and unique "why [city] chooses Emrik" angle per page

### Technical SEO Files
- sitemap.xml listing all indexable pages (exclude thank-you.html)
- robots.txt allowing crawl, disallowing /thank-you.html, pointing to sitemap
- thank-you page must have noindex, nofollow

### Per-Page Title/Description Pattern
- Homepage: "AC Repair & HVAC Service in Corpus Christi | Emrik Refrigeration & AC"
- Service page: "[Service] in Corpus Christi | Emrik Refrigeration & AC"
- City page: "AC Repair & HVAC Service in [City], TX | Emrik Refrigeration & AC"

## Local Server
- **Always serve on localhost** — never screenshot a `file:///` URL.
- Start the dev server: `node serve.mjs` (serves the project root at `http://localhost:3000`)
- `serve.mjs` lives in the project root. Start it in the background before taking any screenshots.
- If the server is already running, do not start a second instance.

## Screenshot Workflow
- Puppeteer is installed at `C:/Users/nateh/AppData/Local/Temp/puppeteer-test/`. Chrome cache is at `C:/Users/nateh/.cache/puppeteer/`.
- **Always screenshot from localhost:** `node screenshot.mjs http://localhost:3000`
- Screenshots are saved automatically to `./temporary screenshots/screenshot-N.png` (auto-incremented, never overwritten).
- Optional label suffix: `node screenshot.mjs http://localhost:3000 label` → saves as `screenshot-N-label.png`
- `screenshot.mjs` lives in the project root. Use it as-is.
- After screenshotting, read the PNG from `temporary screenshots/` with the Read tool — Claude can see and analyze the image directly.

## Output Defaults
- Single `index.html` file, all styles inline, unless user says otherwise
- Tailwind CSS via CDN: `<script src="https://cdn.tailwindcss.com"></script>`
- Placeholder images: `https://placehold.co/WIDTHxHEIGHT`
- Mobile-first responsive

## Brand Assets
- Always check the `brand_assets/` folder before designing. It may contain logos, color guides, style guides, or images.
- If assets exist there, use them. Do not use placeholders where real assets are available.
- If a logo is present, use it. If a color palette is defined, use those exact values — do not invent brand colors.

## Anti-Generic Guardrails
- **Colors:** Never use default Tailwind palette (indigo-500, blue-600, etc.). Pick a custom brand color and derive from it.
- **Shadows:** Never use flat `shadow-md`. Use layered, color-tinted shadows with low opacity.
- **Typography:** Never use the same font for headings and body. Pair a display/serif with a clean sans. Apply tight tracking (`-0.03em`) on large headings, generous line-height (`1.7`) on body.
- **Gradients:** Layer multiple radial gradients. Add grain/texture via SVG noise filter for depth.
- **Animations:** Only animate `transform` and `opacity`. Never `transition-all`. Use spring-style easing.
- **Interactive states:** Every clickable element needs hover, focus-visible, and active states. No exceptions.
- **Images:** Add a gradient overlay (`bg-gradient-to-t from-black/60`) and a color treatment layer with `mix-blend-multiply`.
- **Spacing:** Use intentional, consistent spacing tokens — not random Tailwind steps.
- **Depth:** Surfaces should have a layering system (base → elevated → floating), not all sit at the same z-plane.

## Hard Rules
- Do not add sections, features, or content not in the reference (when a reference is provided)
- Do not "improve" a reference design — match it (when a reference is provided)
- Do not stop after one screenshot pass
- Do not use `transition-all`
- Do not use default Tailwind blue/indigo as primary color

## Git Discipline (CRITICAL — do not let Claude Code touch git)
After every completed page:
```
git add -A
git commit -m "describe what was built"
git push
```
Owner runs these in the VS Code terminal. Claude Code is forbidden from running git commands.
