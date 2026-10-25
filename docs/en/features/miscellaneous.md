---
title: Miscellaneous
---

# Miscellaneous

## Reading progress

```yaml {filename="params.yaml"}
readingProgress:
  enabled: true
  showOnHomepage: false
```

## Announcement

The site-wide announcement is a floating toast. It is dismissible by default, and the dismissed state is kept for the browser session.

```yaml {filename="params.yaml"}
announcement:
  enabled: true
  message: "Site maintenance on Friday."
  type: info # info | warning | destructive
  dismissible: true
  autoClose: 8 # seconds; 0 or omit to keep it visible
```

`autoClose` only takes effect when it is greater than 0. When the announcement closes automatically, it is marked as dismissed for the current session, the same as clicking the close button.

## Images

Markdown images and post covers get a responsive `srcset`. Candidate widths are fractions of `contentWidth` (0.5, 0.75, 1, 1.5 and 2 times), capped at twice the reading width and at the intrinsic image width, so changing `contentWidth` also changes the generated sizes. The `sizes` attribute follows the same value.

For JPEG and PNG sources the theme also emits a WebP `<source>`, which browsers prefer. AVIF, WebP, and GIF sources are served as-is.

```yaml {filename="params.yaml"}
image:
  webp: true # emit WebP variants for JPEG/PNG
  quality: 82 # WebP quality, 1-100
```

Set `webp: false` to serve only the original format. Hugo caches the generated variants between builds.

## Date localization

The theme uses Hugo's `time.Format`, so dates follow the current language's `locale`. There are only three variants:

```yaml {filename="params.yaml"}
dateFormat:
  long: ":date_long" # post detail, page headers
  short: ":date_short" # cards, archives, series
  month: "January 2006" # archive month heading
```

This block is optional; the theme already uses these defaults. Add it only when changing a format, or override per language:

```yaml {filename="languages.yaml"}
en:
  locale: en-US
  params:
    dateFormat:
      short: "01/02/2006"
```

`long` and `short` should use Hugo's localization tokens; the output depends on `locale`:

- `:date_long`: `January 27, 2023` in English, `2023年1月27日` in Chinese
- `:date_short`: `1/27/23` in English, `23/1/27` in Chinese (the current Hugo locale data uses a two-digit year)

Use a Go layout such as `"2006/1/2"` to force a four-digit year in `short`.

### Archive month heading

Hugo has no "month year" token. `data/dateFormats.yaml` provides defaults for languages whose order or wording differs from the default month-first layout:

- `zh-hans`, `zh-hant`, `zh`, `ja`: `2006年1月`
- `ko`: `2006년 1월`
- `vi`: `Tháng 1, 2006`
- `es`, `pt`: `January de 2006`

Other languages use `"January 2006"`, and Hugo localizes the month name from `locale`. The `month` value normally needs no configuration; override it only for custom wording:

```yaml {filename="languages.yaml"}
en:
  locale: en-US
  params:
    dateFormat:
      month: "January 2006"
```

### Locale values

`locale` must be a BCP 47 tag supported by Hugo. For Chinese, use `zh-Hans` or `zh-Hant`. `zh-CN` and `zh-TW` currently fall back to English dates in Hugo's locale data.

The theme does not render times. Use `time.Format` directly in a custom partial if you need one, for example `time.Format ":time_short"`.
