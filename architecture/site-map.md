# Site Architecture — Naturally San Diego

> From client directive. This is the approved navigation structure and page hierarchy.

---

## Persistent Elements (Always Visible)

### Top Navigation Bar
- **Left**: Naturally San Diego logo (links to home)
- **Center/Left**: Main nav items (About, Programs, Community, Resources)
- **Right**: Three CTA buttons + Member Portal link
  - `[Be a Member]` — links to Membership page
  - `[Be a Sponsor]` — links to Sponsorship page
  - `[Upcoming Events]` — links to Event Calendar
  - `Member Portal` link (top right) — links to GlueUp login

### Footer
- Newsletter signup (email capture)
- Social media follow links
- Standard footer links (Privacy, Terms, Contact)

---

## Navigation Structure

### About
- **Our Story** — mission, history, how NSD fits within the Naturally Network
- **Leadership** — Board of Directors + Executive Director (bios, headshots)
- **Our Sponsors** — sponsor logos organized by tier
- **Contact Us** — form that emails directly to client inbox
- ~~**Press**~~ — **REMOVED** (decision: 2026-04-09, no active press to display)

### Programs
- **Naturally Rising** — full page for annual pitch competition
- **Monthly Events** — Coffee & Convos, Facility Tours, annual events (Naturally Rising + Fall Fling)
- **Event Calendar** — GlueUp widget embed
- ~~**Forums**~~ — **REMOVED** (301 redirect → Monthly Events; program not active)

### Community
- **Membership**
  - Why Join
  - Member Benefits
  - Levels & Pricing
  - Member Directory Link (GlueUp)
  - FAQs
- **Sponsorship**
  - Why Sponsor Naturally San Diego
  - Sponsorship Packages
  - Sponsor Inquiry (form that emails to client inbox)

### Resources
- **Job Board** — links to Naturally Network job board (via ForceBrands)
- **Blog** — Member Wins & Stories (wins + founder story cards, labeled "Blog" in nav/footer)
- **Submit News + Events** — form that emails to client inbox
- **Slack Community** — link/info about joining the Slack
- ~~**CPG Academy**~~ — **REMOVED** (301 redirect → Job Board; no program description exists)

---

## Forms Required

| Form | Location | Destination |
|------|----------|-------------|
| Contact Us | About > Contact Us | Client inbox |
| Sponsor Inquiry | Community > Sponsorship | Client inbox |
| Submit News + Events | Resources > Member Wins | Client inbox |
| Newsletter Signup | Footer (all pages) | Email service (TBD) |

---

## External Integrations

| Integration | Type | Widget ID | Pages |
|-------------|------|-----------|-------|
| GlueUp Event Calendar | iframe embed (`eb-widget-event-list`) | Full view | Programs > Event Calendar |
| GlueUp Membership Types | iframe embed (`eb-widget-membership-type-list`) | Pricing list | Community > Membership > Levels & Pricing |
| GlueUp Member Directory | iframe embed (`eb-widget-membership-directory`) | Corporate | Community > Membership > Directory |
| GlueUp Login | iframe embed (`eb-widget-login`) | Login form | Member Portal page |
| GlueUp Subscription | iframe embed (`eb-widget-subscription-list`) | Newsletter | Footer or dedicated page |
| Naturally Network Job Board | External link | — | Resources > Job Board |
| Slack Community | External link | — | Resources > Slack Community |

> Full embed codes with implementation notes: [[architecture/glueup-widgets]]

---

## Notes
- All GlueUp widget embed codes are available and ready to implement
- Form handler TBD — options include Formspree, Astro native, or similar
- Forums page has been removed — 301 redirect to Monthly Events
- CPG Academy page has been removed — 301 redirect to Job Board
- Press page has been removed from nav and footer — page file still exists at /about/press but is not linked anywhere
- Member Wins is now called "Blog" in nav and footer but the page title remains "Member Wins & Stories"
- Do NOT re-add Forums, CPG Academy, or Press to nav/footer without explicit client direction
