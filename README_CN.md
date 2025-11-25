[English](./README.md) | [繁體中文](./README.zh.md) | 简体中文（当前）

<!-- 状态：此中文文档为首版翻译，后续将与英文 README.md 同步更新.-->
<!-- 连接：若英文版更新了功能或命令，请在此处同步并标注变更记录。 -->

# Astro 启动模板：博客

[![部署到 Cloudflare](https://deploy.workers.cloudflare.com/button)](https://deploy.workers.cloudflare.com/?url=https://github.com/cloudflare/templates/tree/main/astro-blog-starter-template)

![Astro 模板预览](https://github.com/withastro/astro/assets/2244813/ff10799f-a816-4703-b967-c78997e8323d)

<!-- dash-content-start -->
使用 Astro 创建博客，并以[静态网站](https://developers.cloudflare.com/workers/static-assets/)的形式部署到 Cloudflare Workers。

功能特性：
- ✅ 极简样式（欢迎自定义）
- ✅ Lighthouse 性能 100/100
- ✅ SEO 友好：规范化 URL 与 OpenGraph 数据
- ✅ 站点地图（Sitemap）支持
- ✅ RSS 订阅支持
- ✅ 支持 Markdown 与 MDX
- ✅ 内置可观测性日志
<!-- dash-content-end -->

## 快速开始
若要使用此模板开始新项目并了解如何部署，请参见下方“部署”章节。

## 🚀 项目结构
Astro 会在 `src/pages/` 目录中查找 `.astro` 或 `.md` 文件。每个文件会根据其文件名暴露为路由。
`src/components/` 用于存放 Astro/React/Vue/Svelte/Preact 组件。
`src/content/` 目录包含相关的 Markdown 与 MDX 文档“集合”。使用 `getCollection()` 从 `src/content/blog/` 读取文章，并可通过可选的 schema 对 frontmatter 进行类型检查。详见[内容集合文档](https://docs.astro.build/en/guides/content-collections/)。
任何静态资源（如图片）可放在 `public/` 目录。
<!-- 连接：此处可补充“目录结构图”或链接到更详细的架构说明文档。 -->

## 🧞 命令
以下命令需在项目根目录终端中运行：

| 命令                              | 动作说明                                          |
| :-------------------------------- | :----------------------------------------------- |
| `npm install`                     | 安装依赖                                          |
| `npm run dev`                     | 启动本地开发服务器（默认 http://localhost:4321） |
| `npm run build`                   | 构建生产版本至 `./dist/`                          |
| `npm run preview`                 | 本地预览生产构建                                  |
| `npm run astro ...`               | 运行 Astro CLI（如 `astro add`, `astro check`）   |
| `npm run astro -- --help`         | 查看 Astro CLI 帮助                               |
| `npm run build && npm run deploy` | Cloudflare 部署请见下方“部署”章节                 |
| `npm wrangler tail`               | 查看所有 Workers 的实时日志（详见“部署”）        |
<!-- 待补充：Windows/Unix 差异、Node 版本要求、环境变量配置。 -->

## DevOps 与版本管理

本仓库采用语义化版本（x.y.z），并提供脚本与（可选）CI 集成。
- 版本政策：参见 [VERSIONING.md](./VERSIONING.md)
- 手动发布：
  - 修订版（Patch）：`npm run version:patch && npm run release:push`
  - 次版本（Minor）：`npm run version:minor && npm run release:push`
  - 主版本（Major）：`npm run version:major && npm run release:push`
- 自动化（若已在 CI 配置）：
  - 合并 PR 至 `main` 后，CI 按分支/标签调整版本：
    - `feat/*` → 次版本、`fix/*|bugfix/*` → 修订版、`major` 标签或标题含 `[major]` → 主版本
  - 推送标签时创建 GitHub Release。

## 部署
请参见 [docs/DEPLOYING_TO_CLOUDFLARE.md](./docs/DEPLOYING_TO_CLOUDFLARE.md) 以获取 Cloudflare 部署、日志与 CLI 用法。

## 内容作者检查清单（非技术）
暂请参考英文版对应章节：[`README.md#content-author-checklist-non-technical`](./README.md#content-author-checklist-non-technical)。

## 👀 了解更多
查看 [Astro 文档](https://docs.astro.build) 或加入 [Discord 社区](https://astro.build/chat)。
<!-- 连接：后续可添加中文社区/讨论区链接。 -->

## 致谢
本主题基于出色的 [Bear Blog](https://github.com/HermanMartinus/bearblog/)。