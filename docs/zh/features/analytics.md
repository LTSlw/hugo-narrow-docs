---
title: 站点统计
---

# 站点统计

Hugo Narrow 支持多种站点统计：

- [百度分析](https://tongji.baidu.com/)
- [Clarity](https://clarity.microsoft.com)
- [Google](https://tagmanager.google.com)
- [Umami](https://umami.is/)

只配置一个 `provider`，留空即关闭：

```yaml {filename="params.yaml"}
analytics:
  provider: "google" # google | baidu | clarity | umami
  google:
    id: "G-XXXXXXXXXX"
```

其他提供商：

```yaml {filename="params.yaml"}
analytics:
  provider: "umami"
  umami:
    id: "your-umami-website-id"
    src: "https://umami.example.com/script.js"
    domains: "example.com"
```

选中的 provider 必须填好必填项才会输出脚本：google、baidu、clarity 为 `id`，umami 为 `id` 和 `src`。缺少时构建会给出警告。
