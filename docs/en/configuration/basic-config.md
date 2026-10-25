---
title: Basic Site Configuration
---

# Basic Site Configuration

Hugo supports `hugo.toml`、`hugo.yaml`、`hugo.json` format and follow the order, supporting split configuration file by envirament, root configuration key, and language.

> [!NOTE]
> See [Hugo Documentation](https://gohugo.io/configuration/introduction/#configuration-directory) for more details.

Hugo Narrow uses split configuration with `YAML`.

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

The site configuration is not much different from that of a regular Hugo site; the special part is:

1. `permalinks.projects` sets the permalinks for projects.
2. `outputFormats.WebAppManifest` automatically generates the `WebAppManifest` configuration for the theme.
3. `highlight.lineNumbersInTable` needs to be set to `false`.
4. Code block colors come from `highlight.style`. The theme generates dark mode from that style's dark counterpart, so choose a paired style such as `catppuccin-latte`, `github`, or `monokai`.
5. The minimum required version of Hugo is 0.165.0.
6. When upgrading from 1.x, see [v1 Configuration (Legacy)](/en/configuration/v1-config) for migration notes.

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
    lineNumbersInTable: false # Set to false
    noClasses: false
    style: catppuccin-latte # must have a dark counterpart
    tabWidth: 2

outputs:
  home: ["HTML", "RSS", "JSON", "WebAppManifest"]

# Custom output
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

Hugo Narrow could configure the main sections, which are used for global search.

```yaml {filename="config/_default/hugo.yaml"}
mainSections: ["posts", "projects", "pages"]
```

The recent posts of home page will use the first section.

## Search

The search index is generated at build time. You can tune how much of each page goes into it, or turn search off entirely; when disabled, the index is emitted empty.

```yaml {filename="config/_default/params.yaml"}
search:
  enabled: true            # hide the dock button and skip the search script when false
  indexContentLength: 2000 # characters of each page stored in the index
```

## Appearance defaults

Appearance parameters set the initial page state. Readers can still change them in the appearance panel; runtime changes are stored in the browser and never written back to the site config.

```yaml {filename="config/_default/params.yaml"}
contentWidth: "56rem" # reading column width, rem or px; readers can adjust 40-90rem
backdropBlur: 12      # backdrop blur radius for floating surfaces, 0-24 px
grainSize: 25         # background grain size, 0-100; 0 disables
```

`contentWidth` also drives the responsive image width ladder, so changing it regenerates image sizes for the new reading width.
