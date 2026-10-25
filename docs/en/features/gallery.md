---
title: Gallery
---

# Gallery

Hugo Narrow supports a lightbox and three gallery layouts: `justified`, `masonry`, and `grid`. Plain Markdown images are enough to create a gallery.

```yaml {filename="params.yaml"}
gallery:
  enabled: true
  defaultLayout: justified # justified | masonry | grid

lightbox:
  enabled: true
```

Each gallery has a single layout button in its top-right corner. Clicking it cycles through `justified` → `masonry` → `grid`. The choice applies to that gallery group only and resets to `defaultLayout` on reload.

The layout values can be set site-wide and overridden per page. Unset keys keep the theme defaults shown here:

```yaml {filename="params.yaml"}
gallery:
  enabled: true
  defaultLayout: justified # justified | masonry | grid
  gap: 10 # px between items, all layouts
  targetRowHeight: 200 # justified: target row height
  lastRowBehavior: center # justified: left | center | right | fill | hide
  columnWidth: 200 # masonry when columns is auto
  columns: 4 # grid count; masonry accepts a number or auto
```

`columns: auto` derives the column count from `columnWidth`, which keeps masonry and grid readable on narrow screens. Page front matter accepts the same keys:

```yaml {filename="gallery-post.md"}
gallery:
  defaultLayout: masonry
  columns: auto
  gap: 12
lightbox:
  enabled: true
```

## Usage

Put one image per line. Consecutive images without a blank line form one gallery. The example below creates two galleries:

```markdown
![](images/image01.jpg)
![](images/image02.jpg)

![](images/image03.jpg)
![](images/image04.jpg)
![](images/image05.jpg)
```
