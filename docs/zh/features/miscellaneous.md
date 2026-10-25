---
title: 其他
---

# 其他

## 阅读进度

```yaml {filename="params.yaml"}
readingProgress:
  enabled: true
  showOnHomepage: false
```

## 站点通知

站点通知是右上角的浮层提示。默认可关闭，关闭状态在当前浏览器会话内保留。

```yaml {filename="params.yaml"}
announcement:
  enabled: true
  message: "周五站点维护。"
  type: info # info | warning | destructive
  dismissible: true
  autoClose: 8 # 秒；0 或不写表示一直显示
```

`autoClose` 大于 0 时生效。自动关闭后会在当前会话内记为已关闭，效果与点击关闭按钮一致。

## 图片

Markdown 图片和文章封面会自动生成响应式尺寸，宽度跟随 `contentWidth`。JPEG 和 PNG 额外提供 WebP 版本，浏览器优先使用；AVIF、WebP、GIF 直接使用原图。

```yaml {filename="params.yaml"}
image:
  webp: true # 为 JPEG/PNG 生成 WebP 变体
  quality: 82 # WebP 质量，1-100
```

`webp: false` 时只输出原格式。

## 日期本地化

主题使用 Hugo 的 `time.Format`，按当前语言的 `locale` 自动本地化日期。只保留三个变体：

```yaml {filename="params.yaml"}
dateFormat:
  long: ":date_long" # 文章详情、页头
  short: ":date_short" # 卡片、归档、系列
  month: "January 2006" # 归档页的月份标题
```

这个配置块是可选的，主题已经内置上面这组默认值。只有需要改变格式时才需要写入 `params.yaml`，也可以按语言覆盖：

```yaml {filename="languages.yaml"}
zh-hans:
  locale: zh-Hans
  params:
    dateFormat:
      short: "2006/1/2"
```

`long` 和 `short` 推荐使用 Hugo 的本地化 token，具体输出由 `locale` 决定：

- `:date_long`：英文 `January 27, 2023`，中文 `2023年1月27日`
- `:date_short`：英文 `1/27/23`，中文 `23/1/27`（Hugo 当前 locale 数据使用两位年份）

如果需要固定四位年份，可以用 Go 布局覆盖 `short`，例如 `"2006/1/2"`。

### 归档页月份

Hugo 没有“年月”token，主题在 `data/dateFormats.yaml` 中为需要调整顺序或措辞的语言提供了默认值：

- `zh-hans`、`zh-hant`、`zh`、`ja`：`2006年1月`
- `ko`：`2006년 1월`
- `vi`：`Tháng 1, 2006`
- `es`、`pt`：`January de 2006`

其他语言使用 `"January 2006"`，Hugo 会按 `locale` 本地化月份名称。通常情况下不需要配置 `month`；需要自定义时再覆盖：

```yaml {filename="languages.yaml"}
zh-hans:
  locale: zh-Hans
  params:
    dateFormat:
      month: "2006年1月"
```

### locale 取值

`locale` 必须是 Hugo 支持的 BCP 47 标签。中文请使用 `zh-Hans` / `zh-Hant`；`zh-CN`、`zh-TW` 在当前 Hugo 的 locale 数据中会回退到英文日期。

主题不渲染时间；需要时间格式时，在自定义模板里直接调用 `time.Format`，例如 `time.Format ":time_short"`。
