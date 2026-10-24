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
>   system: "giscus"
> ```

```yaml {filename="params.yaml"}
comments:
  enabled: false
  system: "giscus"
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
    theme: "" # light, dark, or empty to follow browser preference
    domainId: ""
    cssOverride: ""
    liveUpdate: true
    maxLevel: 10
    noFonts: false
    autoInit: true
    autoNonInteractiveSso: false
```

## 主题跟随

`theme`（giscus、utterances、comentario）和 `darkMode`（artalk）留空或使用 `preferred_color_scheme` / `preferred-color-scheme` / `auto` 时，评论跟随站点的明暗切换实时更新。设成固定值时不跟随，避免覆盖你的显式选择。
