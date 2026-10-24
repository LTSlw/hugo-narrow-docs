---
title: Dock
---

# Dock

The dock is the theme's only page-level action surface: home, menu, search, TOC, comments (when enabled), appearance, and back-to-top.

Placement is fixed; there is no display-mode parameter:

- At `>= 75rem` wide in landscape, the dock is a vertical capsule on the right. Scrolling down collapses it to the menu button; scrolling up, hovering, or focusing expands it.
- Everywhere else (narrow screens, portrait, vertically folded devices) it is a bottom capsule and stays visible.
- Back-to-top appears after scrolling past 80% of the viewport.
- When comments are enabled, the dock gets a jump-to-comments button.
- When search is disabled, the search button is skipped and the search script is not loaded.

```yaml {filename="params.yaml"}
comments:
  enabled: true
  system: "giscus"
```

## Search

Search opens from the dock button or `Ctrl/Cmd + K`; the index is generated at build time. Turn it off entirely:

```yaml {filename="params.yaml"}
search:
  enabled: true
```

## Table of contents

The TOC opens from the dock as a single panel: right side on wide screens, bottom sheet on narrow screens. A post can disable it in front matter.

```yaml {filename="params.yaml"}
toc:
  enabled: true
```

```yaml {filename="first-post.md"}
toc: false
```

On very wide screens (`>= 105rem` in landscape) the panel shows a pin button. The pin state is stored in the browser; there is no site parameter for it.

## Language switching

On multilingual sites, language selection sits at the bottom of the appearance panel. The panel shows the current language, and clicking it opens a secondary language list. There is no cycle button and no site-level switching-mode parameter. The list uses translations of the current page when available.
