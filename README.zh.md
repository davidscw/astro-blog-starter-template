[English](./README.md) | 繁體中文（當前） | [简体中文](./README_CN.md)

<!-- 狀態：此中文（繁體）文件為首版翻譯，後續將與英文 README.md 同步更新。-->
<!-- 連結：若英文版更新了功能或命令，請在此處同步並標註變更記錄。 -->

# Astro 啟動模板：部落格

[![部署到 Cloudflare](https://deploy.workers.cloudflare.com/button)](https://deploy.workers.cloudflare.com/?url=https://github.com/cloudflare/templates/tree/main/astro-blog-starter-template)

![Astro 模板預覽](https://github.com/withastro/astro/assets/2244813/ff10799f-a816-4703-b967-c78997e8323d)

<!-- dash-content-start -->
使用 Astro 建立部落格，並以[靜態網站](https://developers.cloudflare.com/workers/static-assets/)的形式部署到 Cloudflare Workers。

功能特性：
- ✅ 極簡樣式（歡迎自訂）
- ✅ Lighthouse 效能 100/100
- ✅ SEO 友善：規範化 URL 與 OpenGraph 資料
- ✅ 網站地圖（Sitemap）支援
- ✅ RSS 訂閱支援
- ✅ 支援 Markdown 與 MDX
- ✅ 內建可觀測性日誌
<!-- dash-content-end -->

## 快速開始
在此倉庫之外，你可以使用 [C3](https://developers.cloudflare.com/pages/get-started/c3/)（`create-cloudflare` CLI）基於此模板建立新專案：
```bash
npm create cloudflare@latest -- --template=cloudflare/templates/astro-blog-starter-template
```
<!-- 待補充：常見安裝問題與代理/網路環境說明。 -->

線上示例部署：
https://astro-blog-starter-template.templates.workers.dev

## 🚀 專案結構
Astro 會在 `src/pages/` 目錄中尋找 `.astro` 或 `.md` 檔案。每個檔案會依其檔名對應為路由。
`src/components/` 用於存放 Astro/React/Vue/Svelte/Preact 元件。
`src/content/` 目錄包含相關的 Markdown 與 MDX 文件「集合」。使用 `getCollection()` 從 `src/content/blog/` 讀取文章，並可透過可選的 schema 對 frontmatter 進行型別檢查。詳見[內容集合文件](https://docs.astro.build/en/guides/content-collections/)。
任何靜態資源（如圖片）可放在 `public/` 目錄。
<!-- 連結：此處可補充「目錄結構圖」或連到更詳細的架構說明文件。 -->

## 🧞 指令
以下指令需在專案根目錄的終端機中執行：

| 指令                              | 動作說明                                          |
| :-------------------------------- | :----------------------------------------------- |
| `npm install`                     | 安裝相依套件                                      |
| `npm run dev`                     | 啟動本機開發伺服器（預設 http://localhost:4321） |
| `npm run build`                   | 建置正式版本至 `./dist/`                          |
| `npm run preview`                 | 本機預覽正式建置                                  |
| `npm run astro ...`               | 執行 Astro CLI（如 `astro add`, `astro check`）   |
| `npm run astro -- --help`         | 查看 Astro CLI 說明                               |
| `npm run build && npm run deploy` | 將正式建置部署到 Cloudflare                       |
| `npm wrangler tail`               | 檢視所有 Workers 的即時日誌                        |
<!-- 待補充：Windows/Unix 差異、Node 版本需求、環境變數設定。 -->

## 👀 了解更多
查看 [Astro 文件](https://docs.astro.build) 或加入 [Discord 社群](https://astro.build/chat)。
<!-- 連結：後續可新增繁體中文社群/討論區連結。 -->

## 致謝
本主題基於出色的 [Bear Blog](https://github.com/HermanMartinus/bearblog/)。