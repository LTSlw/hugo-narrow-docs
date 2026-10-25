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

`gap`, `targetRowHeight`, `lastRowBehavior`, `columnWidth`, and `columns` use theme defaults; most sites do not need to set them. Override them in page front matter when needed:

```yaml {filename="gallery-post.md"}
gallery:
  enabled: true
  defaultLayout: masonry
  gap: 12
  columns: 3
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
