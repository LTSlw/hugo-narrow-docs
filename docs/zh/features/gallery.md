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

图库右上角只有一个布局切换按钮，点击会在 `justified` → `masonry` → `grid` 之间循环。切换只对当前图库分组生效，刷新后回到 `defaultLayout`。

布局参数可以在站点配置里统一设置，也可以在页面 frontmatter 覆盖；未设置的键使用下面的主题默认值：

```yaml {filename="params.yaml"}
gallery:
  enabled: true
  defaultLayout: justified # justified | masonry | grid
  gap: 10 # 所有布局的图片间距，单位 px
  targetRowHeight: 200 # justified：目标行高
  lastRowBehavior: center # justified：left | center | right | fill | hide
  columnWidth: 200 # masonry 在 columns 为 auto 时的列宽
  columns: 4 # grid 列数；masonry 可填数字或 auto
```

`columns: auto` 会根据 `columnWidth` 自动计算列数，窄屏下 masonry 和 grid 更易读。页面 frontmatter 使用同样的键名：

```yaml {filename="gallery-post.md"}
gallery:
  defaultLayout: masonry
  columns: auto
  gap: 12
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
