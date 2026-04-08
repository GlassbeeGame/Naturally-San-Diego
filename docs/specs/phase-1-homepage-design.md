# Homepage Design Spec — Phase 1
**Direction**: Option 2 — Full-Bleed Photo Hero + Event Cards
**Date approved**: 2026-04-06
**Status**: Approved, ready to build

---

## Skills to Invoke (In Order)

Before touching any code, follow this skill sequence:

| Step | Skill | When |
|------|-------|------|
| 1 | `brainstorming` | Already complete — direction locked |
| 2 | `brand-voice` | Before writing ANY copy — run this first to lock the voice profile |
| 3 | `direct-response-copy` | For hero headline, CTA copy, and section subheads — these need to persuade |
| 4 | `positioning-angles` | For the "Become a Member" and "Become a Sponsor" CTAs specifically |
| 5 | `frontend-design` | Reference for all component building and layout decisions |
| 6 | `simplify` | After completing the build — review all changed code for quality |
| 7 | `web-design-guidelines` | Final audit before marking the page done |

---

## Client Alignment Notes

These are the client's stated priorities, pulled from the brand guide and reference site docs:

- **Current site "feels cringe"** — the new site must feel modern, 2025, community-forward
- **Three reference sites**: Naturally NY, NorCal, and Colorado — all have full-bleed photo heroes, clean mission blocks, sponsor logos, and strong "Become a Member" CTAs
- **Voice is everything**: approachable, entrepreneurial, friendly, community-driven — NOT corporate, NOT a nonprofit brochure
- **Content strategy**: hero headline must be identity-driven and San Diego-localized (e.g. "New York is the Heart of Natural Products" is the NY pattern — SD needs its own version)
- **1% for the Planet partnership** — credibility signal that should appear somewhere on homepage (footer or mission block)
- **Sponsor tiers**: Titanium, Platinum levels expected — display tiered in Phase 2 with real logos
- **No stats bar** — user preference; credibility comes from sponsor logos, pull quote, and visible event activity instead

---

## Section-by-Section Spec

### 1. Navigation

**Client requirement (from site-map.md):** Three CTA buttons + Member Portal link — not two.

- White background, `border-bottom: 1px solid #f0f0f0`
- **Left**: Naturally San Diego logo — use `NSD_WhiteLogo.png` is for dark backgrounds; on white nav use the dark version. See `assets/logo-reference.md` for correct file. Links to `/`
- **Center**: Four dropdown nav items — About, Programs, Community, Resources (Poppins 600, 13px, `#333`)
- **Right**: Three pill CTAs + portal link:
  - `Be a Member` → `/community/membership` — orange fill (`#F26447`, white text)
  - `Be a Sponsor` → `/community/sponsorship` — ghost pill (`border: 1.5px solid #ddd`, dark text)
  - `Upcoming Events` → `/programs/event-calendar` — ghost pill
  - `Member Portal` — plain link (no pill), links to GlueUp login
- Mobile: hamburger menu collapses all nav items; CTAs collapse to primary "Be a Member" only

**Skill note**: Button copy ("Be a Member" vs "Join Now" vs "Become a Member") — run `direct-response-copy` to validate the highest-converting phrasing before finalizing.

---

### 2. Hero

- Full-bleed community photo, `height: 560px`, `object-fit: cover`, `object-position: center`
- Dark overlay: `linear-gradient(135deg, rgba(0,40,20,0.88) 0%, rgba(0,60,35,0.7) 50%, rgba(0,100,69,0.4) 100%)`
- Subtle lime radial glow: `radial-gradient(ellipse at 70% 40%, rgba(195,219,102,0.15) 0%, transparent 60%)`
- Content anchored bottom-left, `padding: 0 48px 52px`, `max-width: 600px`
- Eyebrow tag pill: `"San Diego · Natural Products · CPG"` — lime border `rgba(195,219,102,0.3)`, lime text `#C3DB66`, uppercase, 10px, 1.5px letter-spacing, `border-radius: 100px`
- **H1**: Poppins 900, 58px, `letter-spacing: -2.5px`, `line-height: 0.95`, white
  - Must be identity-driven + San Diego-localized (content strategy directive)
  - Placeholder: "Where great brands begin." — **replace with final copy from `brand-voice` + `direct-response-copy` run**
  - Key phrase on line 2: `color: #C3DB66`, displayed as block
- Body: 15px Lato, `rgba(255,255,255,0.7)`, `max-width: 420px`, `line-height: 1.65`
  - Placeholder: "San Diego's home for natural products and CPG founders..."
  - **Final copy**: run `brand-voice` first, then write
- CTAs: "Become a Member" (orange pill `#F26447`) + "See Events →" (white ghost text link)
- Hero photo: `<img>` tag, `position: absolute`, `inset: 0`, `width: 100%`, `height: 100%`, `object-fit: cover` — **do NOT lazy-load** (above fold)
- Phase 2: replace `testimage.jpg` with real community event photo from client

---

### 3. Sponsor Strip

- White background, `padding: 24px 48px`, `border-bottom: 1px solid #f0f0f0`
- Label: "OUR SPONSORS" — 10px, `#bbb`, uppercase, 2px letter-spacing (Poppins 700)
- Flex row of sponsor logo placeholders — 32px tall pills, `#f5f5f3` background
- **Phase 2**: Replace with real sponsor logos (WebP, lazy-loaded), organized by tier:
  - Titanium tier: largest display
  - Platinum tier: medium display
  - Standard: smaller inline row
- This strip is a credibility signal — appears immediately after hero, before any other content

---

### 4. Mission / Identity Block

**Required — present on all three reference sites. Missing from original mockup.**

- White or very light background (`#f9f9f8`), `padding: 52px 48px`
- Short, punchy mission statement: 1–2 sentences max
- Ref: NorCal has a mission tagline with icon; NY has a "Who We Are" block
- Copy direction (content strategy): "harness, accelerate, and elevate conscious business in the natural products industry" — rewrite this in brand voice, not nonprofit-brochure language
- Optional: include 1% for the Planet badge/logo as a credibility signal here
- **Copy must be written using `brand-voice` skill** — this section is easy to make sound stiff/generic

---

### 5. Upcoming Events

- White background, `padding: 52px 0 0`
- Header row: eyebrow "What's Coming Up" + H2 "Events worth showing up for." + "Full Calendar →" link (right-aligned, links to `/programs/event-calendar`)
- H2: Poppins 700, ~32px, `#111`, `letter-spacing: -1px`
- Cards: horizontal scroll row, `gap: 16px`, `padding: 32px 48px`, `overflow-x: auto`, hide scrollbar on desktop
- Each card (fixed `width: 260px`):
  - Colored top band (~140px) — date (12px, `opacity: 0.7`) + title (Poppins 700, 18px, white)
  - Band colors: orange `#F26447`, green `#00AD5A`, lime `#C3DB66` (use dark text), teal `#00B2AD`
  - White card body: event type label (10px, uppercase, matching band color) + description (13px Lato, `#555`) + CTA link
  - `border-radius: 16px`, `box-shadow: 0 2px 12px rgba(0,0,0,0.06)`
- Placeholder events: Naturally Rising, Coffee & Convos, Facility Tour, Fall Fling
- **Phase 3**: Replace placeholder cards with GlueUp event list widget embed

---

### 6. Programs Grid

- `background: #f9f9f8`, `padding: 52px 48px`
- Eyebrow + H2: "Everything you need to grow your brand."
- 3-column grid (desktop) → 2-col (tablet) → 1-col (mobile), `gap: 32px`
- Each item: icon (emoji Phase 1, SVG Phase 2) + title (Poppins 700, 16px, `#111`) + description (Lato 14px, `#555`)
- 6 items matching site-map programs:
  1. **Signature Events** — Naturally Rising pitch competition + Fall Fling
  2. **CPG Academy** — practical education for every stage
  3. **Monthly Events** — Coffee & Convos, facility tours, community hangouts
  4. **Job Board** — natural products jobs in San Diego
  5. **Slack Community** — the conversation that never stops
  6. **Naturally Network** — part of a national community (NY, NorCal, Colorado, and beyond)
- No card borders — clean open grid with generous whitespace

---

### 7. Pull Quote

- `background: #111`, `padding: 72px 48px`
- Single large quote: Poppins 800, ~34px, white, `letter-spacing: -1px`, `line-height: 1.2`
- Key phrase "Naturally SD." in `#C3DB66`
- Attribution: Poppins 600, 13px, `rgba(255,255,255,0.5)` — Name · Title, Brand · Member Since
- One quote only — not a carousel
- **Phase 2**: Replace with real testimonial from client. Must feel authentic — not generic "great community!" copy.

---

### 8. Join CTA

- `background: linear-gradient(135deg, #C3DB66 0%, #00AD5A 100%)`, `padding: 72px 48px`
- Two-column layout: left = headline + body, right = two buttons
- H2: Poppins 800, `#003d22`, `letter-spacing: -1px`
- Body: Lato 15px, `#003d22` at 80% opacity
- Button 1: "Become a Member" → `/community/membership` — `background: #003d22`, white text, pill shape
- Button 2: "Become a Sponsor" → `/community/sponsorship` — `background: rgba(0,0,0,0.1)`, `#003d22`, pill shape
- **Copy**: Run `positioning-angles` then `direct-response-copy` — this is a conversion section

---

### 9. Footer

- `background: #111`, `padding: 40px 48px 32px`
- Top row: White logo (`NSD_WhiteLogo.png`) left + newsletter signup inline right (input + orange submit button)
- Bottom row: Two nav columns (About/Programs left, Community/Resources right) + social links + copyright
- Include: 1% for the Planet logo if not used in mission block
- **Phase 3**: Wire up newsletter form (GlueUp subscription widget or TBD email service)
- **Copy for newsletter CTA**: Run `email-sequences` for the signup hook line

---

## Placeholder Content (Phase 1)

Use this for the build. Phase 2 replaces with final client-approved copy.

| Section | Placeholder | Skill to use for final copy |
|---------|-------------|----------------------------|
| H1 | "Where great brands begin." | `brand-voice` + `direct-response-copy` |
| Hero body | "San Diego's home for natural products and CPG founders..." | `brand-voice` |
| Mission block | "We harness, accelerate, and elevate conscious business in natural products." | `brand-voice` |
| Pull quote | "Met my co-packer, my first investor, and my best customer all through Naturally SD." | Client-supplied in Phase 2 |
| Join CTA headline | "Ready to find your people?" | `positioning-angles` + `direct-response-copy` |
| Newsletter hook | "Stay in the loop." | `email-sequences` |
| Events | Naturally Rising, Coffee & Convos, Facility Tour, Fall Fling | Client-supplied in Phase 2 |
| Hero photo | `testimage.jpg` from `assets/brand-guide-images/` | Real community photo in Phase 2 |

---

## Build Rules

- **Framework**: Astro — each section is a `.astro` component in `src/components/`
- **Styling**: Tailwind utility classes only — no custom CSS files
- **Hero image**: `<img>` absolute positioned, `object-fit: cover`, no lazy load (above fold)
- **All other images**: `loading="lazy"`, WebP format
- **Event cards scroll**: `overflow-x: auto`, `scroll-snap-type: x mandatory` on container, `-webkit-overflow-scrolling: touch`, hide scrollbar with `::-webkit-scrollbar { display: none }`
- **Mobile breakpoints**: `sm: 480px`, `md: 768px`, `lg: 1024px`
- **Logo in nav**: Check `assets/logo-reference.md` — use the correct variant for white background
- **GlueUp script**: Must appear once only in the global layout — do NOT add it again on this page
- **Commit to GitHub** after build is complete

---

## Open Questions (Resolve Before Phase 2)

- [x] Which reference site (NY, NorCal, Colorado) does the client like most?
- [ ] Final hero headline — needs client input + `direct-response-copy` run
- [ ] Real community photos for hero
- [ ] Real pull quote / testimonial from a member
- [ ] Actual sponsor names and tier breakdown (Titanium, Platinum, etc.)
- [ ] Should 1% for the Planet logo appear in mission block or footer?
