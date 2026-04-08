# GlueUp Widget Embed Codes — Naturally San Diego

> These are the actual embed codes for GlueUp integrations. The script tag only needs to appear ONCE per page, even if multiple widgets are used.

---

## Shared Script (Include Once Per Page)

```html
<script src='https://app.glueup.com/compiled/js/eb-widgets.min.js' type='text/javascript'></script>
```

**RequireJS alternative** (if site uses requireJS):
```html
<script>require(['https://app.glueup.com/compiled/js/eb-widgets.min']);</script>
```

---

## 1. Membership Type List
**Use on**: Community > Membership (Levels & Pricing)

```html
<iframe class="eb-widget" id="eb-widget-membership-type-list" name="eb-widget-membership-type-list" data-auto-adjust-height="true" data-auto-adjust-width="true" style="display:block; margin: 0; padding: 0; border: 0; outline: 0; font-size: 100%; vertical-align: baseline; background:transparent;" src="https://naturallysandiego.glueup.com/organization/1739/widget/membership-type-list/?itemPerPage=10"></iframe>
```

---

## 2. Membership Directory (Corporate)
**Use on**: Community > Membership > Member Directory

```html
<iframe class="eb-widget" id="eb-widget-membership-directory" name="eb-widget-membership-directory" data-auto-adjust-height="true" data-auto-adjust-width="true" style="display:block; margin: 0; padding: 0; border: 0; outline: 0; font-size: 100%; vertical-align: baseline; background:transparent;" src="https://naturallysandiego.glueup.com/organization/1739/widget/membership-directory/corporate"></iframe>
```

---

## 3. Subscription List (Newsletter)
**Use on**: Footer newsletter signup (or dedicated subscription page)

```html
<iframe class="eb-widget" id="eb-widget-subscription-list" name="eb-widget-subscription-list" data-auto-adjust-height="true" data-auto-adjust-width="true" style="display:block; margin: 0; padding: 0; border: 0; outline: 0; font-size: 100%; vertical-align: baseline; background:transparent;" src="https://naturallysandiego.glueup.com/organization/1739/widget/subscription-list/"></iframe>
```

---

## 4. Login Widget
**Use on**: Member Portal page (or as modal/redirect)

```html
<iframe class="eb-widget" id="eb-widget-login" name="eb-widget-login" data-auto-adjust-height="true" data-auto-adjust-width="true" style="display:block; margin: 0; padding: 0; border: 0; outline: 0; font-size: 100%; vertical-align: baseline; background:transparent;" src="https://naturallysandiego.glueup.com/organization/1739/widget/login/"></iframe>
```

---

## 5. Event List (Full View)
**Use on**: Programs > Event Calendar

```html
<iframe class="eb-widget" id="eb-widget-event-list" name="eb-widget-event-list" data-auto-adjust-height="true" data-auto-adjust-width="false" style="display:block; margin: 0; padding: 0; border: 0; outline: 0; font-size: 100%; vertical-align: baseline; background:transparent; width: 100%; height: 100%;" src="https://naturallysandiego.glueup.com/organization/1739/widget/event-list/full-view"></iframe>
```

---

## 6. Direct GlueUp URLs (No Widget Embed Needed)

These pages are hosted directly on GlueUp — link to them rather than embedding a widget:

| Purpose | URL | Use On |
|---------|-----|--------|
| Member Portal login | `https://app.glueup.com/account/login` | Nav "Member Portal" link, footer |
| Become a Member | `https://app.glueup.com/org/naturallysandiego/memberships/` | Primary "Be a Member" CTA buttons |
| Full Events listing | `https://naturallysandiego.glueup.com/org/naturallysandiego/events/` | "View All Events" links |

> **Note:** The current site links "Become a Member" directly to the GlueUp-hosted memberships page rather than embedding the widget. Consider the same approach for the new site — it reduces iframe complexity and lets GlueUp handle the purchase flow entirely.

## 7. Job Board (Not GlueUp)

The Job Board is **not** a GlueUp integration. It is the national Naturally Network Job Board powered by ForceBrands:
- **URL**: `jobs.naturallynetwork.org` — external link only, no embed
- **Account request form**: `https://naturally-network-job-board-request.webflow.io/` (Webflow-hosted)
- Members/sponsors submit this form to get posting access

---

## Implementation Notes for Astro

- The GlueUp script tag should be loaded in the `<head>` or at the bottom of the layout template — only once globally
- Each iframe widget can be wrapped in an Astro component for reuse
- The `data-auto-adjust-height="true"` handles responsive height
- The event list widget has `width: 100%; height: 100%` — may need a container with a min-height
- Organization ID is **1739** across all widgets
- Base URL: `naturallysandiego.glueup.com`
