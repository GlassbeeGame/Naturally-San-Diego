# CLAUDE.md — Naturally San Diego Website Project

> **This is a living document.** It is the project brain. Read it fully before every session. Update it at the end of every session.

---

## Project Overview

This is the website for **Naturally San Diego**, a 501(c)(6) non-profit serving the natural products and CPG (consumer packaged goods) industry in San Diego. They are part of the larger **Naturally Network** with sibling chapters in New York, Colorado, NorCal, and others.

We are rebuilding their website from a dated WordPress site to a modern, community-forward Astro site. The existing GlueUp member/event management system stays — we are only replacing the frontend.

**Live current site**: https://naturallysandiego.org
**Domain**: naturallysandiego.org
**Client contact**: info@naturallysandiego.org

---

## Pre-Task Protocol

**Before doing ANY work in a session, read these files in order:**

1. **This file** (`CLAUDE.md`) — project rules, status, and established patterns
2. `brand/brand-identity.md` — colors, typography, voice, logo rules
3. `architecture/site-map.md` — full navigation and page hierarchy
4. `architecture/technical-specs.md` — framework, hosting, integrations
5. `architecture/content-strategy.md` — how to write and source content
6. `reference/design-direction.md` — three reference sites and design principles

**Before specific task types, also read:**

| Task | Read First |
|------|-----------|
| Any page creation or editing | `architecture/site-map.md` + `architecture/content-strategy.md` |
| Any GlueUp integration work | `architecture/glueup-widgets.md` |
| Any design or layout decisions | `reference/design-direction.md` |
| Any copy or content writing | `brand/brand-identity.md` (Brand Personality section) + `architecture/content-strategy.md` |
| Working with logos | `assets/logo-reference.md` |

---

## Auto-Update Rules

**This file and the `prompts/` folder must stay current without being asked.** These updates happen automatically — do not wait for the user to request them.

### CLAUDE.md updates automatically when:
- A design decision is made → add to **Established Design Patterns**
- A new component or layout pattern is used → add to **Component Patterns** table
- A page or infrastructure task is completed → update **Project Status** tables
- A new open question surfaces → add to **Open Questions**
- A session ends → add a **Session Log** entry with what was built, decisions made, patterns established, blockers, and what to start with next session
- A pattern from a previous entry is contradicted by something new → update the old entry, don't leave conflicts

### `prompts/` folder — save a prompt file when:
- A task involves building or significantly changing a full page
- A task involves a major component (nav, footer, hero, etc.)
- A multi-step workflow was used to complete a task (brainstorming → spec → build)
- A prompt took significant back-and-forth to refine before the final result

**How to save a prompt:**
1. After the task is complete and the result is approved, write the final refined prompt to `prompts/[descriptive-filename].md`
2. The file should contain the **best version of the prompt** — the version that would produce the approved result if run fresh, with all context and constraints already baked in
3. Strip out the back-and-forth iteration — save only the clean, final prompt
4. Include at the top: what the prompt is for, what phase it belongs to, and the date it was finalized

**Prompt file naming:** `phase-[N]-[short-description].md` — e.g. `phase-1-homepage-build.md`, `phase-1-global-nav.md`, `phase-2-membership-copy.md`

---

## Skill Routing

**This section is mandatory.** Skills are not optional enhancements — they are required workflows for specific task types. Do not skip them. Do not summarize them. Run the full skill before producing output.

---

### Task → Skill Mapping

#### Starting any new page, feature, or major component
1. **`brainstorming`** — Required before touching any code. Explore the approach, get user approval on the design, write a spec, then invoke `writing-plans`. Never jump straight into building.

#### Building or editing any UI component, layout, or page
2. **`frontend-design`** — Required for all component building, page layouts, and visual design decisions. Use this as the primary reference skill for anything visual. Invoke it before writing Astro/Tailwind code.

#### After completing any build task
3. **`simplify`** — Required after every build task. Review the changed code for quality, efficiency, and reuse. Do not skip this step.

#### Auditing any completed page for quality
4. **`web-design-guidelines`** — Required after building any page or major component. Checks accessibility, UX best practices, and interface quality. Run this before marking any page as done.

#### Writing or rewriting any copy on any page
5. **`brand-voice`** — Required before writing any copy. Ensures all text matches the Naturally Network tone: approachable, friendly, casual, entrepreneurial, community-driven. Never corporate, formal, or sterile. Feed the voice profile into any copy work.

#### Membership page, Sponsorship page, or any CTA copy
6. **`positioning-angles`** — Run first to find the compelling hook before writing a word of copy.
7. **`direct-response-copy`** — Use for all headlines, CTAs, membership benefits copy, and sponsorship pitch copy. These are conversion pages — write them to persuade, not inform.

#### Any email capture, newsletter section, or email sequence
8. **`email-sequences`** — Use for footer newsletter signup copy, any email onboarding flows, or follow-up sequences.

#### Repurposing any site content for social media
9. **`content-atomizer`** — Use when turning a blog post, event recap, member win, or page section into social posts.

#### Generating any image, photo, or visual asset
10. **`ai-creative-strategist`** — Run this first to figure out what to create before generating anything.
11. **`ai-image-generation`** / **`ai-product-photo`** / **`ai-social-graphics`** — Use the appropriate skill for the asset type after the strategy is set.

#### End of every session
12. **`obsidian-markdown`** — Use for formatting any doc updates properly before writing them.

---

### Quick Reference Table

| Task | Skills to Invoke (in order) |
|------|-----------------------------|
| New page or major feature | `brainstorming` → `writing-plans` → `frontend-design` → `simplify` → `web-design-guidelines` |
| New component or UI element | `frontend-design` → `simplify` → `web-design-guidelines` |
| Any copy writing | `brand-voice` → write copy |
| Membership or Sponsorship copy | `positioning-angles` → `direct-response-copy` → `brand-voice` check |
| CTAs and headlines | `direct-response-copy` |
| Email / newsletter copy | `email-sequences` |
| Social content from existing pages | `content-atomizer` |
| Image or visual generation | `ai-creative-strategist` → appropriate generation skill |
| Code cleanup after build | `simplify` |
| Page quality audit | `web-design-guidelines` |
| Unclear or multi-step request | `orchestrator` — let it route to the right skill sequence |

---

## Framework & Technical Rules

### Stack
- **Framework**: Astro (with `@astrojs/sitemap` for automatic sitemap generation)
- **Styling**: Tailwind CSS (utility-first — no custom CSS files unless absolutely necessary)
- **Hosting**: Vercel (connected to GitHub, auto-deploys on push to main)
- **Version Control**: GitHub
- **Fonts**: Google Fonts — Poppins, Roboto Condensed, Lato

### Automatic Sitemap
`@astrojs/sitemap` is installed and configured. Every page added to `src/pages/` is automatically included in `sitemap.xml` on build. **Do NOT manually manage the sitemap.**

### Non-Negotiable Rules
- **Never install new dependencies without asking the user first**
- **Never change the color palette** — it comes from the official Naturally Network brand guide
- **Never alter logo files** — use them as provided, per brand guidelines
- **Always use Tailwind utility classes** — no inline styles, no custom CSS unless Tailwind genuinely cannot handle it
- **Always commit to GitHub after completing a task** — with a clear, descriptive commit message
- **Always use semantic HTML** — proper heading hierarchy, landmark elements, ARIA labels where needed
- **Mobile-first** — design for mobile, then scale up. Every component must work on 320px screens
- **Images**: always use WebP format, always lazy load below-fold images
- **SEO is NOT a priority** — basic meta tags and semantic HTML are sufficient. No keyword optimization, no location pages, no SEO strategy

### GlueUp Integration
- Organization ID: **1739**
- Base URL: **naturallysandiego.glueup.com**
- The GlueUp script tag (`eb-widgets.min.js`) must appear **only once** per page in the global layout
- All GlueUp integrations are iframe embeds — see `architecture/glueup-widgets.md` for exact codes
- **Never rebuild GlueUp functionality** — use their widgets as-is

---

## Brand Rules (Quick Reference)

Full details in `brand/brand-identity.md`. These are the essentials:

### Colors
| Role | Color | Hex |
|------|-------|-----|
| Primary brand green | Medium Green | `#00AD5A` |
| Headers, dark accents | Dark Green | `#006A45` |
| Highlights, badges | Light Green | `#C3DB66` |
| Backgrounds | White | `#FFFFFF` |
| Body text | Black | `#000000` |
| CTA buttons, energy | Red Orange | `#F26447` |
| Accent | Teal | `#00B2AD` |
| Accent | Purple | `#7E4558` |

### Typography
| Use | Font | Weight |
|-----|------|--------|
| Headlines, subheads | Poppins | Bold, Regular, Light |
| Condensed headlines | Roboto Condensed | Bold |
| Body copy | Lato | Regular, varying weights |

### Voice
**Be**: approachable, friendly, casual, entrepreneurial, upbeat, community-driven, inspirational
**Never be**: corporate, formal, sterile, serious, heavy-handed, overly trendy, overly wholesome

---

## Established Design Patterns

> **This section is a living log.** Every time a design decision is made — a component style, a layout pattern, a spacing convention — document it here so every future page stays consistent.

### Visual Direction (Decided Session 1)
- **Hero approach**: Photography-led with strong typographic overlay — photo fills right column, headline dominates left (split layout) OR full-bleed photo with headline overlaid
- **No stats bar** — raw "200+ members / 50+ sponsors" strips feel dated; credibility comes from sponsor logos, testimonials, and event activity instead
- **Sponsor logos**: Appear immediately below hero as a subtle credibility signal (not a big "OUR SPONSORS" section)
- **Events**: Show as upcoming event cards (horizontal scroll) OR a clean date-list layout — both are approved patterns
- **Community proof**: One large pull quote in a dark/green section beats a grid of testimonial cards
- **CTA section**: Dark (#111) rounded card with membership + sponsorship buttons side by side
- **Footer**: Dark (#111) background, newsletter signup inline, two nav columns

### Component Patterns

| Component | Pattern | Notes |
|-----------|---------|-------|
| Bento grid (programs) | 3-col grid, mixed sizes, colored tiles (green/lime/teal/dark/white), border-radius 16px | Established in visual brainstorming |
| Event cards | Colored top band (event-color), title + date, body with type label + desc + CTA link | Horizontal scroll on homepage; scroll container needs `pt-3` to prevent hover-lift clip |
| Event list rows | Date (month + large day number) / title+desc / CTA — clean row layout on #f9f9f8 bg | Alternative to cards for tighter layouts |
| Pull quote | Full-width dark section, 34px+ Poppins 800, accent color on key phrase, single attribution line | Not a carousel — one powerful quote |
| Sponsor logos | Inline pill/rectangle placeholders in a flex row, subdued gray tone | Right below hero, labeled "Our Sponsors" small-caps |
| Nav CTA buttons | Pill shape (border-radius: 100px), ghost + filled orange side by side | "Member Portal" ghost, "Be a Member" orange-fill |
| Dark info card | `bg-[#111]` rounded-3xl, dot-grid texture overlay, `#C3DB66` lime section labels, white body text | Used on Contact left panel, Submit News left panel, Member Portal left panel — consistent treatment |
| Two-col form layout | Dark info card (left) + white form card (right), `grid-cols-2`, `max-w-5xl`, `items-start` | Contact, Submit News pages |
| Annual event cards | `bg-[#111]` with dot-grid, `#C3DB66` lime badge, white headline/body — side-by-side grid | Monthly Events page — Naturally Rising + Fall Fling |
| Person cards (leadership) | `w-32 h-32` circle photo centered, `ring-4 ring-[#C3DB66]/30`, name + lime role badge below | All staff and board use same circle size |

### Spacing Conventions
- Section padding: `52px 48px` standard, `72px 48px` for hero/CTA sections
- Card gap: `12px` (bento), `16px` (event cards)
- Border radius: `16px` cards, `20px` feature sections, `24px` CTA blocks, `100px` pills/buttons

### Button Styles
- **Primary CTA**: `background: #F26447`, white text, `border-radius: 100px`, `padding: 14px 28–32px`, Poppins 700 13px
- **Secondary/Ghost**: transparent or `border: 1.5px solid`, matching text color, same radius/padding
- **Nav pill ghost**: `border: 1.5px solid #ddd`, dark text
- **Nav pill fill**: `background: #F26447`, white text

---

## Project Status

### Pages

| Page | Status | Notes |
|------|--------|-------|
| Homepage | **DONE** | Full build — hero, sponsor strip, mission, events, programs grid, pull quote, CTA |
| About > Our Story | **DONE** | Mission text, values, Naturally Network block, 1% for Planet |
| About > Leadership | **DONE** | BoardGrid with all 20 board members + 1 staff (Nicole Strohbehn removed) |
| About > Our Sponsors | **DONE** | SponsorGrid with all 6 tiers; unmapped logos as text chips |
| About > Press | **REMOVED FROM NAV** | Page file exists at /about/press but not linked anywhere in nav or footer — do not re-add |
| About > Contact Us | **DONE** | Two-col: contact info + form; **🔴 Formspree endpoint needed** |
| Programs > Naturally Rising | **DONE** | Full page — description, stats, timeline, photo gallery; **🔴 application link needed** |
| Programs > Forums | **REMOVED** | 301 redirect → /programs/monthly-events — do not re-add to nav |
| Programs > Monthly Events | **DONE** | 5 event type cards + annual events grid (Naturally Rising + Fall Fling side-by-side, both #111 black) + GlueUp calendar CTA |
| Programs > Event Calendar | **DONE** | GlueUp event list widget + "View All Events on GlueUp" banner CTA |
| Community > Membership | **DONE** | Why Join, benefits, pricing, GlueUp widgets, FAQs |
| Community > Sponsorship | **DONE** | Rebuilt inquiry form as dark card + white form (matches Submit News pattern); **🔴 Formspree + PDF link needed** |
| Resources > Job Board | **DONE** | ForceBrands description + account request link |
| Resources > CPG Academy | **REMOVED** | 301 redirect → /resources/job-board — do not re-add to nav |
| Resources > Blog (Member Wins & Stories) | **DONE** | Wins + founder story cards with colored bands and badges; placeholder notice for Renee |
| Resources > Submit News + Events | **DONE** | Two-col layout: black context card + form card; **🔴 Formspree endpoint needed** |
| Resources > Slack Community | **DONE** | Description + topic pills; **🔴 Slack invite link needed** |
| Member Portal | **DONE** | Full-screen split layout — black brand panel left, white sign-in CTA right, redirects to GlueUp login |
| Thank You | **DONE** | Post-form redirect page |
| Privacy Policy | **DONE** | Placeholder — **🔴 legal content needed** |
| Terms of Use | **DONE** | Placeholder — **🔴 legal content needed** |
| Section index redirects | **DONE** | /about, /programs, /community, /resources all redirect to correct pages |

### Infrastructure

| Task | Status | Notes |
|------|--------|-------|
| Astro project setup | **DONE** | v6.1.4 |
| GitHub repo created | **DONE** | GlassbeeGame/Naturally-San-Diego |
| Vercel deployment | **PENDING** | Repo exists — needs Vercel connection |
| Tailwind configured | **DONE** | v4 via @tailwindcss/vite, brand colors as @theme tokens |
| Google Fonts loaded | **DONE** | Poppins, Roboto Condensed, Lato |
| @astrojs/sitemap installed | **DONE** | Auto-generates sitemap.xml — 25 pages on last build |
| Global layout with nav | **DONE** | Layout.astro + Nav.astro with dropdowns |
| Footer component | **DONE** | Newsletter bar + nav links + social icons + badges |
| GlueUp script in global layout | **DONE** | Single script tag in Layout.astro head |
| Responsive nav with mobile menu | **DONE** | Hamburger + expanded mobile sublinks |
| Favicon from NN_Icon.png | **DONE** | favicon.png |

### Phases

| Phase | Status | Description |
|-------|--------|-------------|
| Phase 1+2: Build with Real Content | **DONE** | All 25 pages built, 0 build errors. 12 reusable components. |
| Phase 3: Integrations + Launch Prep | **CURRENT** | GitHub push → Vercel deploy, Formspree wiring, client review |
| Phase 4: Refinement | Pending | QA, performance, client feedback pass, missing content from client |

> **Phase 1 and 2 are merged.** Real content from `reference/current-site.md` is used in the build directly. Items marked 🔴 in that file still need client input and will use minimal placeholders only where necessary.

---

## Session Log

### Session 2026-04-09 — Nav Cleanup, Sponsor Strip, Copy Polish, GitHub Push
**What was built:**
- **Newsletter + footer success states**: Animated SVG checkmark (circle draws, then checkmark strokes in) for both the popup and footer newsletter forms. Popup auto-closes after 3s. Both set `localStorage` permanently after subscribe to suppress future popup.
- **Mobile nav rebuilt**: Full-screen overlay with Events + Member Portal pinned as prominent quick-access buttons at top; accordion sections for About/Programs/Community/Resources; Become a Member + Become a Sponsor CTA strip at bottom. Body scroll locked when open.
- **Em dash reduction**: Replaced `—` with `.` or `·` across site-wide copy (monthly events, programs grid, membership, CTA, etc.)
- **SponsorStrip expanded**: From 9 to 32 confirmed logo files. All sponsors with matching files in `/public/sponsors/` now shown. SponsorGrid also fixed 5 previously null-mapped entries.
- **Forums removed**: Page replaced with 301 redirect → `/programs/monthly-events`. Removed from nav and footer.
- **CPG Academy removed**: Page replaced with 301 redirect → `/resources/job-board`. Removed from nav and footer.
- **Member Wins → Blog**: Renamed to "Blog" in nav and footer. Page rebuilt as "Member Wins & Stories" with win cards + founder story cards, colored top bands, badge chips. Placeholder notice at bottom.
- **Sponsorship inquiry form**: Rebuilt to match Submit News dark card pattern — `#111` dark card left (logo lockup, "What You Get" checklist, Renee's email) + white form card right.
- **Press removed from nav + footer**: `/about/press` page still exists but is no longer linked anywhere.
- **Homepage mission block**: Changed to "San Diego's home for natural products founders, brands, and the people who support them."
- **Hero headline mobile fix**: Removed `hidden sm:block` from `<br>` tags so line breaks show on all screen sizes.
- **Monthly Events subtitle**: Changed from cringe "Social butterfly or wallflower..." to "Something worth showing up for, every single month."
- **Naturally Rising subtitle**: Changed to "San Diego's biggest night in natural products."
- **Member Wins subtitle**: Updated copy.
- **GitHub**: All changes pushed to `GlassbeeGame/Naturally-San-Diego` (main branch).

**Design decisions made:**
- Press is removed — not enough active press to warrant a page in nav
- Forums is removed — program not active, redirect keeps URL clean
- CPG Academy is removed — no program description exists, redirect to Job Board
- Member Wins is "Blog" in nav/footer only — page title stays "Member Wins & Stories"
- Mobile nav: full-screen overlay is the canonical pattern (not inline dropdown)
- Do NOT re-add Forums, CPG Academy, or Press to nav without explicit client direction

**Patterns established:**
- Mobile nav: full-screen overlay, Events + Member Portal pinned top, accordion body, CTA strip bottom
- Newsletter success state: animated SVG checkmark draw, auto-close popup after 3s, permanent localStorage suppression

**Issues or blockers:**
- Vercel not yet connected to GitHub repo — needs to be done next
- 3 Formspree endpoints still needed: Contact Us, Sponsor Inquiry, Submit News
- Still outstanding from client: Slack invite link, sponsorship PDF, Naturally Rising application link, legal content

**Next session should start with:**
1. Connect Vercel to GitHub repo (GlassbeeGame/Naturally-San-Diego → auto-deploy on push)
2. Client creates Formspree account — 3 endpoints: Contact Us, Sponsor Inquiry, Submit News
3. Phase 4 client review pass — walk through live site

---

### Session 2026-04-08 — UI Polish + SEO + New Components
**What was built:**
- **Leadership page**: Redesigned all headshots to uniform `w-32 h-32` circles with lime ring; staff cards side-by-side layout; fixed blur by constraining display to near-native 180px resolution. Removed Nicole Strohbehn (left organization).
- **Our Story — What We Stand For**: Replaced card grid with editorial row layout (number | title | body, dividers). Numbers changed from lime to dark green.
- **Contact page**: Redesigned as two-col layout — `#111` dark card (logo, address, emails, social pills) + white form card. Equal `grid-cols-2` columns.
- **Submit News page**: Same two-col dark card pattern as Contact — left card has "What Counts" checklist + after-submit note; right card has form.
- **Membership page**: Added Naturally Rising crowd photo with caption badge alongside the pitch/benefits section.
- **Monthly Events page**: Replaced single Fall Fling section with side-by-side annual events grid — Naturally Rising (teal→black) + Fall Fling, both `#111` with dot-grid and lime badges. Added GlueUp calendar CTA banner.
- **Event Calendar page**: Upgraded "View all events" text link to matching banner CTA with teal pill button.
- **Member Portal**: Full redesign — removed GlueUp login widget (couldn't be styled), replaced with full-screen split layout. Left: `#111` brand panel with dot-grid. Right: white card with orange "Sign In via GlueUp →" button redirecting to `naturallysandiego.glueup.com/login`.
- **Newsletter Popup**: New `NewsletterPopup.astro` component — `#111` dark top band, 10s delay OR 60% scroll trigger, sessionStorage (once per session), never shows after subscribe (localStorage). Skips member-portal and thank-you pages.
- **SEO**: Added canonical URL, full Open Graph tags, Twitter card meta, Schema.org Organization JSON-LD to Layout.astro. Added `defer` to GlueUp script.
- **Accessibility/contrast**: Footer low-opacity text bumped to WCAG AA. Popup `aria-labelledby` + email `aria-label`. Mobile popup stacks email+button vertically.
- **Bug fixes**: Event card hover-lift top clip fixed (added `pt-3` to scroll container). Removed background photo overlays from Member Portal panel and ProgramsGrid Naturally Rising tile.

**Design decisions made:**
- `#111` dark card is the canonical pattern for info/context panels — Contact, Submit News, Member Portal all use it
- All leadership headshots: `w-32 h-32` circle, same size for staff and board
- Annual event cards: always `#111` black (not colored) — consistent pair aesthetic
- Member Portal: redirect to GlueUp login rather than embed widget (widget can't be styled, other Naturally Network chapters do the same)
- Newsletter popup: sessionStorage not localStorage — shows on every new browser session, permanent suppression only after subscribe

**Next session should start with:**
1. Push code to GitHub (`git init` → `git remote add origin` → `git push`)
2. Connect Vercel to GitHub repo → auto-deploy
3. Client needs Formspree account — 3 form endpoints: Contact Us, Sponsor Inquiry, Submit News
4. Outstanding client inputs: Slack invite link, CPG Academy description, sponsorship PDF, application link for Naturally Rising, legal content for Privacy/Terms
5. Walk through live site with client for Phase 4 feedback pass

---

### Session 2026-04-06 (continued — Design Polish + Nav Logo)
**What was built:**
- Removed ghosted large background text watermark from `PageHero.astro` — banners now cleaner with only dot grid + angled SVG bottom cut
- Replaced nav logo in `Nav.astro` — switched from `NSD_WhiteLogo.png` (dark-background badge, looked muddy on white nav) to `NN_Icon.png` (green circle icon) paired with "Naturally / San Diego" text lockup in brand greens (#006A45 / #00AD5A). All original logo PNGs have opaque dark backgrounds and are designed for dark navbars; the icon + text solution works correctly on the white sticky nav.
- Build passes: 25 pages, 0 errors

**Design decisions made:**
- PageHero ghosted text is removed — the dot grid pattern + angled white cut provides enough visual interest without the large background words
- Nav logo: `NN_Icon.png` (green circle) + Poppins 800 "Naturally" + Poppins 600 "San Diego" — this is the canonical nav logo treatment

**Patterns established:**
- Nav logo pattern: `NN_Icon.png` (h-9 rounded-full) + two-line text lockup — do NOT use `NSD_WhiteLogo.png` or `NSD_WhiteNaturallyLogo.png` on white nav (both have opaque dark backgrounds)

**Next session should start with:**
1. Push code to GitHub (`git init`, `git remote add origin [repo]`, `git push`)
2. Connect Vercel to GitHub repo → auto-deploy
3. Client needs to create Formspree account (formspree.io) — 3 forms: Contact Us, Sponsor Inquiry, Submit News
4. Walk through the live site with client for feedback pass (Phase 4 begins)

---

### Session 2026-04-06 (continued — Phase 1+2 Build)
**What was built:**
- Fixed `src/pages/index.astro` — replaced bare Astro stub with proper Layout + all homepage sections
- Built 12 reusable components: `PageHero`, `SectionHeader`, `GlueUpWidget`, `CTASection`, `FormspreeForm`, `SponsorStrip`, `EventCard`, `ProgramsGrid`, `PullQuote`, `BoardGrid`, `SponsorGrid`, `FaqAccordion`
- Updated `Nav.astro` — added dropdown submenus for all 4 nav items (desktop hover + mobile expanded); updated Member Portal link to `/member-portal`
- Built all 25 pages: homepage, 5 About pages, 4 Programs pages, 2 Community pages, 5 Resources pages, Member Portal, Thank You, Privacy, Terms, 4 section index redirects
- All pages pass `npm run build` — 0 errors, `sitemap.xml` auto-generated with all 25 routes

**Design patterns established (added to Component Patterns table above):**
- `PageHero` — interior page hero with optional bgImage + color overlay, supports `darkText` for lime (#C3DB66) backgrounds
- `SectionHeader` — eyebrow + H2 + optional body, supports `left` or `center` align
- `CTASection` — lime→green gradient background wrapping dark #111 card, CTA buttons inside
- `EventCard` — 260px fixed width, colored top band, snap-scroll row
- `ProgramsGrid` — 6-tile bento grid, 3-col desktop, colored tiles with Learn more → links
- `SponsorStrip` — grayscale logos, `OUR SPONSORS` small-caps label, horizontal scroll on mobile
- `FaqAccordion` — `<details>/<summary>` native, lime border-left on open, chevron rotation
- `BoardGrid` — staff (larger) + board (5-col desktop), lime role badges, 180×180 headshots

**Component file locations:**
- All components: `src/components/` (12 files)
- All pages: `src/pages/` and subdirectories

**Issues or blockers:**
- 4 items need client action before forms work (see Open Questions below)
- Several unmapped numeric sponsor logo files (12-, 14-, etc.) — using text chips for now
- Chosen Foods and Suja Juice logo files not identified — using text chips

**Next session should start with:**
1. Push code to GitHub (`git init`, `git remote add origin [repo]`, `git push`)
2. Connect Vercel to GitHub repo → auto-deploy
3. Client needs to create Formspree account (formspree.io) — 3 forms: Contact Us, Sponsor Inquiry, Submit News — then add endpoints
4. Walk through the live site with client for feedback pass (Phase 4 begins)
5. Obtain from client: sponsorship deck PDF, Slack invite link, CPG Academy description, real testimonial

### Session 2026-04-06 (earlier — content + scaffolding)
**What was built:**
- Fixed progressive JPEG encoding issue on `photo.jpg` (and `testimage.jpg`) — converted to baseline JPEG so Claude API can process images
- Relaunched visual companion server at new session dir `8787-1775508935`
- Fixed server image path issue — server only serves images via `/files/` route, updated compare-all.html accordingly
- Locked homepage design direction: **Option 2 — Full-Bleed Photo Hero + Event Cards**
- Wrote homepage design spec: `docs/specs/phase-1-homepage-design.md` — includes all section specs, skill routing, client alignment notes, open questions
- Processed raw site dump (`Raw Info from Site.md`) — extracted all useful content via agent into `docs/content/site-content-extraction.md`
- Created brand voice profile: `brand/voice-profile.md` — full voice guide with on/off-brand examples, vocabulary rules, rhythm patterns
- Rewrote all extracted content in brand voice and consolidated into `reference/current-site.md` — this is now the single source of truth for all site copy
- Merged Phase 1 and Phase 2 — building with real content from the start

**Design decisions made:**
- Option 2 (full-bleed photo hero + event cards) confirmed as homepage direction
- Nav corrected to 3 CTA buttons: Be a Member, Be a Sponsor, Upcoming Events + Member Portal link
- Mission/identity block added as required section (was missing from original mockup)
- No shopping cart needed on new site

**Key content facts now known:**
- Membership pricing: $99/year (brand), $299/year (service provider)
- Sponsor tiers: Platinum, Gold, Silver, Bronze, Emerging Brands, Naturally Network Partners
- Full sponsor roster by tier (40+ sponsors) — see `reference/current-site.md`
- Full board of directors (20 members) with names, titles, companies
- Staff: Renee Solares (ED), Nicole Strohbehn (Programs & Events)
- Founded mid-2020 — 5+ years of community building
- Naturally Rising history: 5 annual events, $100K+ prize package, 350-person audience
- Social links: Facebook, Instagram, LinkedIn, YouTube — all confirmed
- 1% for the Planet certified nonprofit partner

**Content gaps flagged (🔴 items in current-site.md):**
- Staff + board headshots and bios
- Sponsorship tier pricing/benefits (in PDF — request from Renee)
- CPG Academy description (not on current site at all)
- Forums description (in development)
- Real member testimonial/pull quote
- Community event photos for hero

**Patterns established:**
- Image files for the brainstorm server must be referenced as `/files/photo.jpg` not `photo.jpg`
- Progressive JPEGs must be converted to baseline before use (use Pillow: `progressive=False`)

**Issues or blockers:**
- None currently

**Next session should start with:**
1. Begin Astro project setup (run `npm create astro@latest` in project directory)
2. Install and configure Tailwind, @astrojs/sitemap
3. Load Google Fonts (Poppins, Roboto Condensed, Lato)
4. Build global layout: nav + footer
5. Then build homepage using `docs/specs/phase-1-homepage-design.md` + `reference/current-site.md`

---

### Session 2026-03-26
**What was built:**
- Visual brainstorming session using the browser-based visual companion
- Created 3 homepage layout mockups (HTML prototypes, not Astro code)
- Created a 4th combined comparison file with tab switcher
- All mockups saved at `.superpowers/brainstorm/72363-1774453260/compare-all.html`

**Design decisions made:**
- No stats bar (200+ members / 50+ sponsors strip) — feels dated, credibility comes from other signals
- Liked Options 2 (full-bleed photo hero + event cards) and 3 (type-led hero + editorial layout) over Option 1
- Session ended before final direction was locked — needs one more pass next session

**Patterns established (see Design Patterns section above):**
- Bento grid for programs
- Event cards (colored top) and event list rows (date + title + CTA)
- Single large pull quote pattern
- Sponsor logo strip placement (right below hero)
- Button, pill, and spacing conventions

**Issues or blockers:**
- localhost server needed a restart mid-session (port conflict)
- CLAUDE.md was not physically present on disk — recreated this session

**Next session should start with:**
1. Relaunch the visual companion: `bash ~/.claude/skills/brainstorming/scripts/start-server.sh --project-dir /Users/jammermurphy/Downloads/naturally-san-diego`
2. Copy saved designs into new screen_dir: `cp prompts/homepage-design-mockups-v1.html [new-screen-dir]/compare-all.html`
3. Open the browser to review all 3 homepage design options (Option 1: Split Hero, Option 2: Photo Hero + Event Cards, Option 3: Type-Led)
4. Get user's final direction decision — lean toward a mix of Options 2 + 3 based on prior feedback
5. Once direction is locked, write the design spec to `docs/superpowers/specs/`
6. Run spec review loop (brainstorming skill step 7)
7. User approves spec (brainstorming skill step 8)
8. Invoke `writing-plans` skill to create the implementation plan
9. Begin Astro build

---

## Open Questions (Resolve with Client)

- [ ] Which of the three reference sites (NY, NorCal, Colorado) is her favorite? Specific elements?
- [ ] Updated leadership bios and headshots
- [ ] Current membership tier names and pricing
- [ ] Current sponsorship package details and pricing
- [ ] Community photos (events, networking, people)
- [ ] Specific event descriptions for signature events
- [ ] FAQ content for membership section
- [ ] CPG Academy details — what does this program include?
- [ ] Social media profile links
- [ ] Slack community join link
- [ ] Is the shopping cart on the current site still needed?
- [ ] Press/media mentions to include
- [ ] Form handler preference (Formspree, Astro endpoints, etc.)

---

## File Structure Reference

```
naturally-san-diego/
├── CLAUDE.md              ← YOU ARE HERE (project brain — read first, update last)
├── architecture/
│   ├── site-map.md
│   ├── technical-specs.md
│   ├── content-strategy.md
│   └── glueup-widgets.md
├── brand/
│   └── brand-identity.md
├── reference/
│   ├── design-direction.md
│   └── current-site.md
├── prompts/
│   └── phase-1-foundation.md
├── assets/
│   ├── logo-reference.md
│   ├── logos/
│   │   ├── NSD_WhiteLogo.png
│   │   ├── NSD_WhiteNaturallyLogo.png
│   │   ├── NN_Icon.png
│   │   └── NaturallySanDiego_Logos.ai
│   └── brand-guide-images/
└── .superpowers/
    └── brainstorm/
        └── [session-dir]/
            └── compare-all.html   ← homepage mockups (3 options)
```
