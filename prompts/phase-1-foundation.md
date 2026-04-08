# Master Prompt — Phase 1: Foundation Build

> This is the primary prompt for Claude Code. It builds the site skeleton — layout, navigation, component structure, and visual design system. Content, integrations, and details come in later phases.

---

## Status: DRAFT — Brand assets received. GlueUp widget codes confirmed. Awaiting client input on reference site preferences before finalizing.

---

## The Prompt

```
I need you to build the foundation of a website for Naturally San Diego, a 501(c)(6) non-profit that serves the natural products and CPG (consumer packaged goods) industry in the San Diego area. They're part of the larger Naturally Network, with sibling chapters in New York, Colorado, NorCal, and others.

This is Phase 1 — we're building the skeleton: layout, navigation, component structure, and the full visual design system. We'll fill in content, integrations, and details in later passes.

## Framework
- Astro
- Push to GitHub, deploy on Vercel
- Tailwind CSS for styling
- Mobile-first responsive design

## Brand Identity

### Colors
Primary palette:
- Dark Green: #006A45 (headers, dark accents)
- Medium Green: #00AD5A (primary brand green)
- Light Green: #C3DB66 (highlights, accent areas)
- White: #FFFFFF (backgrounds)
- Black: #000000 (text)

Accent colors:
- Teal: #00B2AD
- Red Orange: #F26447 (CTAs, energy)
- Purple: #7E4558

### Typography (Google Fonts)
- Poppins (Bold, Regular, Light) — headlines, subheads
- Roboto Condensed (Bold) — condensed headlines where space is tight
- Lato — body copy

### Tone
The brand is approachable, friendly, casual, entrepreneurial, upbeat, and community-driven. It is NOT corporate, formal, sterile, or serious. Think: a smart, passionate community leader talking to peers — not a nonprofit brochure.

## Navigation Structure

### Top Bar (Persistent)
- Logo (left) — links to home
- Main nav (center-left): About, Programs, Community, Resources
- Three CTA buttons (right): [Be a Member] [Be a Sponsor] [Upcoming Events]
- Member Portal link (top right corner) — external link to GlueUp

### About (Dropdown)
- Our Story
- Leadership
- Our Sponsors
- Press
- Contact Us

### Programs (Dropdown)
- Signature Events (Naturally Rising, Fall Fling)
- Forums
- Monthly Events
- Event Calendar

### Community (Dropdown)
- Membership (with sub-sections: Why Join, Benefits, Levels & Pricing, Directory Link, FAQs)
- Sponsorship (Why Sponsor, Packages, Inquiry Form)

### Resources (Dropdown)
- Job Board
- CPG Academy
- Member Wins
- Submit News + Events
- Slack Community

### Footer
- Newsletter signup
- Social media links
- Standard links (Privacy, Terms, Contact)
- Address: 3780 Governor Drive, San Diego, CA 92122
- Email: info@naturallysandiego.org

## Design Direction

Look at these three sibling sites for design inspiration:
- https://www.naturallynewyork.org/ (high energy, social feed, carousel hero)
- https://naturallynorcal.org/ (cleanest layout, stats section, visual program grid, community spotlight)
- https://www.naturallycolorado.org/ (story-driven, strong testimonials)

The design should feel modern, community-forward, and editorial — NOT like a dated WordPress template. Key principles:
- Full-bleed hero section with community photography placeholder and bold headline
- Generous whitespace between sections
- Clean section transitions
- Visual hierarchy through typography, not decoration
- Community stats section (members, sponsors, events, attendees)
- Sponsor logos display area (tiered)
- Programs/What We Do visual grid
- Community testimonials/spotlight section
- Upcoming events section
- Newsletter signup in footer

## Homepage Section Order
1. Hero — full-bleed photo, bold San Diego-focused headline, CTA buttons
2. Mission/identity statement block
3. Community stats (placeholder numbers for now)
4. What We Do / Programs visual grid
5. Sponsor logos section
6. Community spotlight / testimonials
7. Upcoming events
8. Newsletter signup + footer

## What I Need in Phase 1
- Complete Astro project structure
- All pages created with proper routing (can have placeholder content)
- Full navigation with dropdowns working
- Responsive layout — mobile hamburger menu
- Design system implemented (colors, typography, spacing)
- Component library for reusable sections (hero, stats, sponsor grid, testimonial carousel, event cards, forms, CTAs)
- Homepage fully laid out with placeholder content in the correct structure
- All other pages with basic layout and placeholder content
- Push to GitHub and deploy to Vercel

Do NOT focus on SEO. Basic meta tags and semantic HTML are fine — no keyword optimization needed.
```

---

## Phase 2 (Future): Content Population
- Rewrite all copy using current site as source material
- Insert real sponsor logos
- Add leadership bios and headshots
- Populate event descriptions
- Write membership and sponsorship content

## Phase 3 (Future): Integrations & Details
- GlueUp widget embeds (all codes confirmed — see `architecture/glueup-widgets.md`):
  - Membership type list → Membership Levels & Pricing page
  - Membership directory (corporate) → Member Directory page
  - Event list (full view) → Event Calendar page
  - Login widget → Member Portal
  - Subscription list → Newsletter signup
  - Organization ID: 1739 | Base URL: naturallysandiego.glueup.com
- Form handler setup (Contact, Sponsor Inquiry, Submit News)
- Newsletter integration (may use GlueUp subscription widget)
- Image optimization (WebP, lazy loading)
- Performance pass (Core Web Vitals)

## Phase 4 (Future): Refinement
- Client review and feedback
- Design adjustments
- Content polish
- Final QA and launch prep
