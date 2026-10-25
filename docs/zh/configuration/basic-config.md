---
title: 站点基础配置
---

# 站点基础配置

Hugo 配置文件格式支持：`hugo.toml`、`hugo.yaml`、`hugo.json`，并按照上述顺序索引，支持根据环境、根配置键、语言拆分单个配置文件。

> [!NOTE]
> 访问 [Hugo 文档](https://gohugo.io/configuration/introduction/#configuration-directory) 查看详细内容。

Hugo Narrow 使用拆分的配置结构，格式采用 `YAML`。

```bash
exampleSite/
├── config/
│   └── _default/
│       ├── hugo.yaml
│       ├── languages.yaml
│       ├── menus.yaml
│       └── params.yaml
└── content/
```

站点配置和一般 Hugo 站点差别不大，较为特殊的是：

1. `permalinks.projects` 为项目永久链接设置
2. `outputFormats.WebAppManifest` 为主题自动生成 `WebAppManifest` 配置
3. `highlight.lineNumbersInTable` 需要设置为 `false`
4. 代码块配色由 `highlight.style` 控制。主题会用同一 style 的 dark counterpart 生成暗色样式，因此请选择成对的 style，例如 `catppuccin-latte`、`github` 或 `monokai`。
5. Hugo 最低版本为 0.165.0
6. 从 1.x 升级时，先查看 [v1 配置（旧版）](/zh/configuration/v1-config) 中的迁移说明。

```yaml
baseURL: https://hugo-narrow.vercel.app/
languageCode: en-US
defaultContentLanguage: en
defaultContentLanguageInSubdir: false
title: Hugo Narrow
theme: "hugo-narrow"

hasCJKLanguage: true
enableEmoji: true

permalinks:
  posts: /posts/:slug/
  projects: /projects/:slug/
  pages: /:slug/

pagination:
  pagerSize: 6
  path: "page"

taxonomies:
  category: categories
  tag: tags
  series: series

markup:
  tableOfContents:
    startLevel: 2
    endLevel: 4
    ordered: false
  goldmark:
    renderer:
      unsafe: true
    extensions:
      extras:
        delete:
          enable: true
        insert:
          enable: true
        mark:
          enable: true
        subscript:
          enable: false
        superscript:
          enable: false
      strikethrough: false
  highlight:
    codeFences: true
    guessSyntax: false
    lineNos: false
    lineNumbersInTable: false # 设置为 false
    noClasses: false
    style: catppuccin-latte # 需要带 dark counterpart 的 style
    tabWidth: 2

outputs:
  home: ["HTML", "RSS", "JSON", "WebAppManifest"]

# 自定义输出格式
outputFormats:
  WebAppManifest:
    mediaType: "application/manifest+json"
    baseName: "site"
    isPlainText: true

module:
  hugoVersion:
    extended: true
    min: 0.165.0
```

## 主要 Sections

Hugo Narrow 可以配置搜索索引的 Sections，用于全局搜索。

```yaml {filename="config/_default/hugo.yaml"}
mainSections: ["posts", "projects", "pages"]
```

主页最近文章列表会使用第一个 Section。

## 搜索

搜索索引在构建时生成，可以调整每篇文章写入索引的字符数，也可以整体关闭搜索；关闭后索引输出为空。

```yaml {filename="config/_default/params.yaml"}
search:
  enabled: true            # 关闭后 Dock 隐藏搜索按钮，也不再加载搜索脚本
  indexContentLength: 2000 # 每篇文章写入索引的字符数
```
