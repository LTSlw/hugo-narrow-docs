---
title: 图库
---

# 图库

Hugo Narrow 支持图片点击放大，以及 `justified`、`masonry`、`grid` 三种图库布局。使用原生 Markdown 图片语法即可创建图库。

```yaml {filename="params.yaml"}
gallery:
  enabled: true
  defaultLayout: justified # justified | masonry | grid

lightbox:
  enabled: true
```

图库右上角只有一个布局切换按钮，点击会在 `justified` → `masonry` → `grid` 之间循环。切换只在当前页面生效，不写入配置。

`gap`、`targetRowHeight`、`lastRowBehavior`、`columnWidth`、`columns` 由主题内部给默认值，普通站点不需要配置。需要精细调整时可以在页面 frontmatter 覆盖：

```yaml {filename="gallery-post.md"}
gallery:
  enabled: true
  defaultLayout: masonry
  gap: 12
  columns: 3
lightbox:
  enabled: true
```

## 图库使用

每行一个图片链接，中间没有空行的图片组视为同一个图库。下面示例是两个图库：

```markdown
![](images/image01.jpg)
![](images/image02.jpg)

![](images/image03.jpg)
![](images/image04.jpg)
![](images/image05.jpg)
```
