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
- **Press** — media mentions, press releases
- **Contact Us** — form that emails directly to client inbox

### Programs
- **Signature Events**
  - Naturally Rising (pitch competition — include past winners like Naturally Colorado does)
  - Fall Fling
- **Forums** — page placeholder (program being developed)
- **Monthly Events** — Coffee & Convos, Facility Tours, etc.
- **Event Calendar** — GlueUp widget embed

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
- **Job Board** — links to Naturally Network job board
- **CPG Academy** — educational resources
- **Member Wins** — links to articles/media about members, social posts
- **Submit News + Events** — form that emails to client inbox (could live under Member Wins)
- **Slack Community** — link/info about joining the Slack

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
- Forums page is a placeholder — program is in development but page should exist
