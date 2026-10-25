---
title: Analytics
---

# Analytics

Hugo Narrow supports these analytics providers:

- [Baidu](https://tongji.baidu.com/)
- [Clarity](https://clarity.microsoft.com)
- [Google](https://tagmanager.google.com)
- [Umami](https://umami.is/)

Set exactly one `provider`; leave it empty to disable analytics:

```yaml {filename="params.yaml"}
analytics:
  provider: "google" # google | baidu | clarity | umami
  google:
    id: "G-XXXXXXXXXX"
```

Another provider:

```yaml {filename="params.yaml"}
analytics:
  provider: "umami"
  umami:
    id: "your-umami-website-id"
    src: "https://umami.example.com/script.js"
    domains: "example.com"
```

The selected provider only renders when its required keys are set: `id` for google, baidu, and clarity; `id` and `src` for umami. A missing key logs a build warning.
