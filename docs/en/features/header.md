---
title: Context Bar
---

# Context Bar

Version 2.0 removes the top navigation bar. Page navigation lives in the dock; the current location lives in the context bar.

- Every page except home and 404 shows a breadcrumb at the top.
- Scroll collapsing is enabled on article pages only: scrolling down hides the context bar, scrolling up reveals a title-only capsule, and reaching the top restores the full trail. The capsule shows the series position when the page belongs to one; other page kinds keep the breadcrumb visible.
- Clicking or tapping the capsule expands it smoothly back into the original breadcrumb trail. There is no separate navigation panel.
- Posts that belong to a series also get series progress, previous/next controls, and a series popover.
- Appearance, color scheme, page width, and language switching live in the dock's appearance panel. There are no `header.*` parameters anymore.
- The site logo and title are no longer navigation elements. The home entry is the first button in the dock.

The context bar has no configuration. Breadcrumbs are derived from the page hierarchy, and series data comes from the `series` taxonomy plus `series_order`.
