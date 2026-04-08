# Naturally San Diego — Website Project

> This Obsidian vault is the single source of truth for the Naturally San Diego website rebuild. All project decisions, brand assets, architecture, and prompts live here.

---

## Quick Links

### Brand
- [[brand/brand-identity]] — Colors, typography, voice, logo usage, core values

### Architecture
- [[architecture/site-map]] — Full navigation structure and page hierarchy
- [[architecture/technical-specs]] — Framework, hosting, integrations, performance
- [[architecture/content-strategy]] — How content should be sourced, written, and styled
- [[architecture/glueup-widgets]] — All GlueUp embed codes with implementation notes

### Reference
- [[reference/design-direction]] — Three comparison sites with analysis and design principles
- [[reference/current-site]] — Content extracted from the existing naturallysandiego.org

### Prompts
- [[prompts/phase-1-foundation]] — Master prompt for Claude Code (Phase 1: skeleton build)

### Assets
- [[assets/logo-reference]] — Logo file inventory and usage guide
- `assets/NSD_WhiteLogo.png` — Full white logo (for dark backgrounds)
- `assets/NSD_WhiteNaturallyLogo.png` — White logo alternate variant
- `assets/NN_Icon.png` — Leaf icon (favicon, small marks)
- `assets/brand-guide-images/` — All images extracted from brand guide

---

## Project Status

| Phase | Status | Description |
|-------|--------|-------------|
| Phase 1 | **Ready to execute** | Foundation — layout, nav, design system, components |
| Phase 2 | Pending | Content population — rewrite copy, add real assets |
| Phase 3 | Pending | Integrations — GlueUp widgets, forms, newsletter |
| Phase 4 | Pending | Refinement — client review, QA, launch |

---

## Open Questions (To Resolve with Client)

- [x] Which of the three reference sites is her favorite? Specific elements she likes from each?
- [ ] Updated leadership bios and headshots
- [ ] Current membership tier names and pricing
- [ ] Current sponsorship package details and pricing
- [ ] Community photos for the site (events, networking, people)
- [ ] Specific event descriptions for signature events
- [ ] FAQ content for membership section
- [ ] CPG Academy — what does this program include?
- [ ] Social media profile links
- [ ] Slack community join link
- [ ] Is the shopping cart on the current site still needed?
- [ ] Form handler preference (or just route to email?)
- [ ] Press/media mentions to include

---

## Project Details

- **Client**: Naturally San Diego
- **Type**: Non-profit 501(c)(6) website rebuild
- **Framework**: Astro
- **Hosting**: Vercel (via GitHub)
- **Current Site**: https://naturallysandiego.org (WordPress)
- **Parent Org**: Naturally Network
- **Member Platform**: GlueUp (keeping existing — no backend changes)