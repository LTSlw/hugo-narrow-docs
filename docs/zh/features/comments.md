---
title: 评论
---

# 评论

Hugo Narrow 支持多种评论系统：

- [artalk](https://artalk.js.org/)
- [disqus](https://disqus.com/)
- [giscus](https://giscus.app/)
- [twikoo](https://twikoo.js.org/)
- [utterances](https://utteranc.es/)
- [waline](https://waline.js.org/)
- [Comentario](https://comentario.app/)

> [!TIP]
> 评论参数可在文章 frontmatter 覆盖设置。
>
> ```yaml {filename="first-post.md"}
> comments:
>   enabled: true
>   provider: "giscus"
> ```

```yaml {filename="params.yaml"}
comments:
  enabled: false
  provider: "giscus"
  giscus:
    repo: "tom2almighty/hugo-narrow-giscus"
    repoId: ""
    category: "General"
    categoryId: ""
    mapping: "pathname"
    strict: "0"
    reactionsEnabled: "1"
    emitMetadata: "0"
    inputPosition: "bottom"
    theme: "preferred_color_scheme"
    lang: "en"
  disqus:
    shortname: ""
  utterances:
    repo: ""
    issueTerm: "pathname"
    label: "comment"
    theme: "preferred-color-scheme"
  waline:
    serverURL: ""
    lang: "zh-CN"
  artalk:
    server: ""
    site: ""
    locale: "zh-CN" # String|Object|"auto"
    darkMode: "auto"
    gravatar:
      mirror: "https://cravatar.cn/avatar/"
  twikoo:
    envId: ""
    region: "ap-shanghai"
    path: ""
    lang: "zh-CN"
  comentario:
    server: ""
    lang: "zh-CN"
    theme: "" # light、dark，留空则跟随站点主题
    domainId: ""
    cssOverride: ""
    liveUpdate: true
    maxLevel: 10
    noFonts: false
    autoInit: true
    autoNonInteractiveSso: false
```

选择 provider 后，必须填好它的必填项才会渲染：

- giscus：`repo`、`repoId`、`categoryId`
- utterances：`repo`
- disqus：`shortname`
- waline：`serverURL`
- artalk：`server`
- twikoo：`envId`
- comentario：`server`

缺少必填项时评论区会显示“未配置”的提示。

## 主题跟随

主题值留空，或使用对应组件的“跟随系统”值时会实时跟随站点明暗切换：giscus 为 `preferred_color_scheme`，utterances 为 `preferred-color-scheme`，artalk 为 `auto`。Comentario 仅在 `theme` 留空时跟随。设成固定值时不跟随，避免覆盖你的显式选择。

## 自定义 provider

把 `provider` 设成任意名字，并在站点的 `layouts/_partials/features/comments/<名字>.html` 放一个同名 partial 即可。站点模板优先于主题，partial 会收到 `Page`、`Site`、`id` 和 `config`（`provider` 对应的配置块）四个参数。
