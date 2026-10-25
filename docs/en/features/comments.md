---
title: Comments
---

# Comments

Hugo Narrow supports the following comment providers:

- [artalk](https://artalk.js.org/)
- [disqus](https://disqus.com/)
- [giscus](https://giscus.app/)
- [twikoo](https://twikoo.js.org/)
- [utterances](https://utteranc.es/)
- [waline](https://waline.js.org/)
- [Comentario](https://comentario.app/)

> [!TIP]
> Comments settings can be overridden in a post's front matter.
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
    theme: "" # light, dark, or empty to follow the site theme
    domainId: ""
    cssOverride: ""
    liveUpdate: true
    maxLevel: 10
    noFonts: false
    autoInit: true
    autoNonInteractiveSso: false
```

A provider only renders when its required keys are set:

- giscus: `repo`, `repoId`, `categoryId`
- utterances: `repo`
- disqus: `shortname`
- waline: `serverURL`
- artalk: `server`
- twikoo: `envId`
- comentario: `server`

Otherwise the comments section shows a short "not configured" notice.

## Following the theme

Comments follow the site's light/dark switch live when the theme value is left empty, or when it uses the provider's "follow system" value: `preferred_color_scheme` for giscus, `preferred-color-scheme` for utterances, and `auto` for artalk. Comentario follows the site only when `theme` is empty. A fixed value disables the sync so your explicit choice is not overridden.
