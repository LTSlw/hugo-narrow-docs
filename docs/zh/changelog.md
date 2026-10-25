---
title: "更新日志"
---

# 更新日志

## v2.1.0 - 2026-10-25

- refactor!: 评论参数 `comments.system` 改名为 `comments.provider`，站点配置和页面 frontmatter 都需要同步修改。
- refactor: 评论和统计 provider 增加必填项校验，未知名称或缺少配置时输出构建警告。
- feat: 搜索改用 MiniSearch，无空格语言按词切分；关闭搜索时不再加载搜索脚本，索引输出为空。
- feat: 图片响应式宽度改为按 `contentWidth` 推导，JPEG/PNG 额外生成 WebP；新增 `image.webp` 和 `image.quality`。
- feat: 文章页面包屑向下滚动隐藏，向上滚动收起为标题胶囊，点击胶囊平滑展开为原面包屑。
- feat: 图库间距、列数等布局参数可在 `params.gallery` 统一设置并按页面覆盖；布局切换合并为单个循环按钮。
- feat: 标签页在禁用 JS 时仍能显示第一个面板。
- feat: 适配 iOS 安全区；触摸设备上放大 Dock、系列步骤、图库切换、搜索清除和通知关闭按钮。
- fix: giscus 要求同时配置 `repo`、`repoId`、`categoryId`；统计 provider 缺少必填项时不再输出空脚本，改为构建警告。
- fix: 关闭搜索时索引输出为空数组，不再导致构建失败。
- fix: 图库布局按钮通过 `aria-label` 播报当前布局。
- fix: Twikoo 不再在首次加载时闪烁错误的主题。
- fix: 修正 Go 模块路径为 `github.com/tom2almighty/hugo-narrow/v2`。
- ci: 新增格式检查、`compiled.css` 产物一致性和示例站点构建检查，PR 同样触发。
- chore: 新增孟加拉语翻译。

## v2.0.2 - 2026-10-22

- fix: 移除 SVG sprite preload，避免浏览器重复下载和 Chrome 的未使用 preload 警告。
- fix: Dock 容器由 `nav` 改为 `div`，`role="toolbar"` 现在合法。
- fix: Dock 菜单按钮改用 `menu` 图标、目录按钮改用 `toc` 图标，移除未使用的展开/收起图标样式。
- feat: 新增 `announcement.autoClose`，按秒自动关闭通知并记录当前会话的关闭状态。
- chore: 清理 26 个未使用的图标，sprite 从约 27 KB 降至约 17.5 KB。

## v2.0.1 - 2026-10-22

- fix: 修复部署在子路径时的栏目入口、分页、菜单和 404 返回首页链接。
- fix: Dock 收起后只保留单个按钮的宽度。
- fix: 重新区分 Dock 收起、展开和目录图标。
- chore: GitHub Pages 站点增加 v1 演示，恢复文档、演示和中文 README 链接。

## v2.0.0 - 2026-10-22

- refactor!: 移除顶部导航栏，页面导航改为 Dock，页面位置由上下文栏展示。
- refactor!: 设计 token 迁移到 shadcn 原始变量名，运行时外观参数与主题色分离。
- refactor!: 正文改用 `@tailwindcss/typography`，只保留站点特有的标题锚点、代码块和表格覆盖。
- refactor!: 卡片统一为无封面实现，通过 `post` / `project` / `series` variant 区分元信息。
- feat: Dock 宽屏右侧竖排、滚动自动收起，窄屏底部常驻，并补回移动端返回顶部和评论入口。
- feat: 外观面板集中配色、亮暗、宽度、模糊、颗粒和语言设置；语言切换改为二级弹出列表。
- feat: 代码块改用 `markup.highlight.style` 与 `css.ChromaStyles` 生成亮暗两套配色，不再维护 `style` / `darkStyle`。
- feat: 日期格式收敛为 `long` / `short` / `month`；归档月份通过 `data/dateFormats.yaml` 按语言本地化，支持 CJK、越南语、西班牙语和葡萄牙语。
- feat: 增加 RTL 基础支持、hreflang、PWA 元数据、打印样式、reduced-transparency/contrast 和 forced-colors 处理。
- refactor!: 配置收敛，移除 `header.*`、`dock`、`timeFormat`、`toc.position`、`toc.pinned`、`themes` 等参数；配色注册表移到 `data/themes.yaml`。
- refactor!: 项目移除 `status` front matter，项目卡片不再显示状态。
- refactor!: 文章版权配置精简为单个标题字符串 `post.license`，并移到文章顶部元信息行；移除链接和独立版权区块。
- docs: 新增 v1 配置（旧版）页面，说明 v1.4.1 参数和迁移对应关系。

## v1.4.1 - 2026-10-22

- fix: 移除失效的外观面板 `header.showThemeSwitch` / `showDarkModeSwitch` / `showContentWidthSwitch` 开关。
- refactor: 语言切换固定为弹出式列表，移除 `showLanguageSwitch` 和 `languageSwitchMode`。
- refactor: 代码块配色改用 `markup.highlight.style` 的双模式 style，移除 `codeblock.style` / `darkStyle`。
- ci: Hugo 版本固定在分支 workflow 中，v1 使用 Hugo 0.165.0。

## v1.3.16 - 2026-09-01

- feat: 优化侧边目录展示，添加 `params.toc.pinned` 变量，控制侧边目录下是否固定显示目录。
- feat: 优化正文中链接样式。
- feat: 统一 `posts` 布局模板和默认布局模板的列表页（list.html）和详情页（single.html）。

## v1.3.15 - 2026-07-12

- feat: 导航栏添加页面宽度调整功能

## v1.3.14 - 2026-07-11

- chore: 图库布局更新
- chore: 许可协议变更为 GNU General Public License V3
- fix: 统一模板行为，文件未设置日期时不显示 Hugo 默认日期输出

## v1.3.13 - 2026-06-29

- style: 优化项目元信息样式
- fix: 优化文章标题和日期显示逻辑，简化代码结构

## v1.3.12 - 2026-05-31

- feat: 支持 Comentario 评论系统 [@LTSlw](https://github.com/LTSlw)
- chore: 移除冗余依赖说明，优化构建和 README.md 文件。
- feat: 统一评论系统未配置组件提示，优化跳转评论按钮逻辑。
- feat: 添加 CLAUDE.md 文档说明。

## v1.3.11 - 2026-05-24

- feat: 添加简历模板 [@svenvg93](https://github.com/svenvg93)
- feat: 灯箱图片描述移动到底部中间区域 [@svenvg93](https://github.com/svenvg93)

## v1.3.10 - 2026-05-05

- fix: 更新时间和日期格式化模板，避免上游错误
- chore: 更新 Hugo 最低版本到 0.158.0

## v1.3.9 - 2026-05-05

- feat!: 迁移旧的语言参数

## v1.3.8 - 2026-05-03

- feat: 添加日期格式化模板和参数
- chore: 更新 Hugo 最低版本到 0.156.0

## v1.3.7 - 2026-04-27

- feat: 添加系列分类法列表布局 [@svenvg93](https://github.com/svenvg93)

## v1.3.6 - 2026-03-27

- refactor!: 使用自实现灯箱替换PhotoSwipe

  ```diff
    lightbox:
      enabled: true
  -   bgOpacity: 0.8
  -   showHideAnimationType: zoom
  -   showAnimationDuration: 333
  -   hideAnimationDuration: 333
  ```

## v1.3.5 - 2026-03-18

- refactor: 重构 i18n 翻译。
- feat: 新增短代码 `tabs`。

## v1.3.2 - 2026-3-10

- fix: 修复项目元信息字段错误。
- fix: 修复翻译问题导致的日期错误。
- fix: 添加表格基础样式。
- feat: 导航栏添加子菜单。
- feat: 标题添加锚链接。

## v1.3.1 - 2026-02-21

- refactor: 重构项目卡片和项目详情模板。
- refactor: 精简项目头信息。

## v1.3.0 - 2026-02-20

- refactor!: 使用自实现库替换 justified gallery 库，图库现在支持两端对齐、瀑布流和网格布局，支持前端切换布局。
- refactor!: 使用 photoswipe 替换 Glightbox。
- refactor!: 移除 masonry 短代码。
- refactor!: 目录重构，现在支持顶部和侧边悬浮显示。
- refactor!: 文章封面重构，移除冗杂占位图逻辑。
- feat: 添加 `timeline` 布局，使用 `h2` 区分时间块，使用原生 markdown 语法。
- style: 简化部分样式，移除冗余样式文件。
- style: 面包屑导航恢复图标。

## v1.2.3 - 2026-02-03

- feat: 定义搜索主区域。
- refactor!: baseof 模板使用网格样式。
- refactor!: 移除 series 参数。
- refactor!: 移除 toc 侧边栏宽度参数。

## v1.2.2 - 2026-01-09

- feat: 首页通知支持多语言。
- feat: 支持系列文章分类法字段。
- fix: 修复相关文章计数参数。
- fix: 修复评论参数。
- fix: 修复某些语言下 header 按钮溢出。

## v1.2.1 - 2025-12-26

- feat: 添加目录开关（`params.toc.enabled: true`）。
- feat: 添加自定义 head 模板。
- feat: 添加项目内容。
- feat: 添加 `button` 和 `icon` 短代码。
- fix: 移除冗余样式文件。
- fix: 调整链接样式以修复不必要的下划线。

## v1.2.0 - 2025-12-24

- fix: icon 模板支持填充图标
- fix: 调整部分样式类名
- feat: 支持侧边栏目录
- feat: 支持 Hugo Mod 形式引入主题
- feat: 首页模块支持自定义顺序
- refactor: 结构化站点配置
- refactor: 调整 header 相关参数的层级
- refactor!: 调整 Header 相关参数的层级, 添加目录位置参数。

## v1.1.6 - 2025-11-16

- feat: 首页作者信息支持 i18n 翻译
- feat: 首页作者信息和最近文章之间添加自定义内容模板
- fix: 修复站点配置文件中 clarity 参数名称错误

## v1.1.5 - 2025-09-05

- style: 修改上标下标颜色
- style: 修改 alert 引用块底部 padding
- feat: 使用新标签页打开外部链接
- feat: 支持自定义 js 文件
- feat: 添加 404 模板
- feat: 添加 dock 显示模式参数

  ```diff
  params
  +  dock: float # Options: "scroll" (show on scroll up), "always" (always visible), "float" (floating)
  ```

## v1.1.4 - 2025-08-22

- fix: 修复文章卡片摘要索引顺序
- fix: 修复阅读进度和代码块设置
- feat: 添加语言切换选项，添加参数 `params: languageSwitchMode`，支持 `dropdown` 和 `cycle` 选项
- style: 页脚添加版权信息

## v1.1.3 - 2025-08-06

- fix: 修复文章展位图不生效
- fix: 修复普通页面评论不显示
- fix: 修复版权组件中 URL 过长导致页面溢出
- style: GitHub Alert 样式优化
- style: Plaintext 代码块样式优化
- style: 文章卡片样式优化
- style: 有序列表颜色优化
- style: 相关文章卡片样式精简
- style: 文章导航卡片高度
- feat: 添加 `About` 模板
- feat: 添加 `link` 短代码
- feat: 优化搜索和目录功能点击事件
- refactor!: 重构 CSS 样式框架，移除 `@tailwindcss/typography` 依赖

## v1.1.2 - 2025-07-02

- fix: 修复 Frontmatter 版权参数不生效
- style: 图片居中显示
- refactor!: license 字段添加 `author` 和 `show` 参数
- refactor!: 删除 `showLicense` 参数

## v1.1.1 - 2025-06-25

- fix: 修复 masonry 短代码 ID 重复导致的样式失效问题。
- fix: 修复 glightbox 和 justified 参数设置不生效问题 。
- style: 优化链接、脚注样式。
- style: 添加 scrollbar 样式。
- style: 添加主题配色，来自[tweakcn](https://tweakcn.com/)。

## v1.1.0 - 2026-06-17

- feat: 瀑布流图库短代码：新增 `{\{< masonry >}}` 短代码，支持瀑布流布局。
- refactor: 重构图库，更新参数。
- feat: 全新灯箱系统：图库灯箱由 lightGallery 迁移至 GLightbox，提升性能与现代化体验。
- feat: 优化分栏布局：jQuery 版 justified gallery 替换为 flickr-justified-gallery，全面支持原生 JavaScript。
- feat: 移除 jQuery 依赖：图库系统完全去除 jQuery，提升加载速度并减小包体积。
- fix:修复 post-meta 组件的 i18n 翻译问题。
- fix:解决统计模板导入异常问题。

## v1.0.0 - 2025-06-14

- feat: 集成 Hugo 内置 SEO 模板
- feat: 实现图库功能支持
- feat: 添加文章封面自定义占位图功能
- fix: 移除冗余元数据字段
- fix: 修复文章页导航描述显示问题
