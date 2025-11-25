# Astro Starter Kit: Blog

English (current) | [繁體中文](./README.zh.md) | [简体中文](./README_CN.md)

[![Deploy to Cloudflare](https://deploy.workers.cloudflare.com/button)](https://deploy.workers.cloudflare.com/?url=https://github.com/cloudflare/templates/tree/main/astro-blog-starter-template)

![Astro Template Preview](https://github.com/withastro/astro/assets/2244813/ff10799f-a816-4703-b967-c78997e8323d)

<!-- dash-content-start -->

Create a blog with Astro and deploy it on Cloudflare Workers as a [static website](https://developers.cloudflare.com/workers/static-assets/).

Features:

- ✅ Minimal styling (make it your own!)
- ✅ 100/100 Lighthouse performance
- ✅ SEO-friendly with canonical URLs and OpenGraph data
- ✅ Sitemap support
- ✅ RSS Feed support
- ✅ Markdown & MDX support
- ✅ Built-in Observability logging

<!-- dash-content-end -->

## Getting Started

To start a new project using this template and learn how to deploy, see the Deployment section below.

## 🚀 Project Structure

Astro looks for `.astro` or `.md` files in the `src/pages/` directory. Each page is exposed as a route based on its file name.

There's nothing special about `src/components/`, but that's where we like to put any Astro/React/Vue/Svelte/Preact components.

The `src/content/` directory contains "collections" of related Markdown and MDX documents. Use `getCollection()` to retrieve posts from `src/content/blog/`, and type-check your frontmatter using an optional schema. See [Astro's Content Collections docs](https://docs.astro.build/en/guides/content-collections/) to learn more.

Any static assets, like images, can be placed in the `public/` directory.

## 🧞 Commands

All commands are run from the root of the project, from a terminal:

| Command                           | Action                                           |
| :-------------------------------- | :----------------------------------------------- |
| `npm install`                     | Installs dependencies                            |
| `npm run dev`                     | Starts local dev server at `localhost:4321`      |
| `npm run build`                   | Build your production site to `./dist/`          |
| `npm run preview`                 | Preview your build locally, before deploying     |
| `npm run astro ...`               | Run CLI commands like `astro add`, `astro check` |
| `npm run astro -- --help`         | Get help using the Astro CLI                     |
| `npm run build && npm run deploy` | See Deployment for Cloudflare instructions       |
| `npm wrangler tail`               | View real-time logs for all Workers (see Deployment) |

## DevOps & Versioning

This repo uses semantic versioning (x.y.z) with scripts and, optionally, CI.
- Version policy: see [VERSIONING.md](./VERSIONING.md)
- Manual release:
  - Patch: `npm run version:patch && npm run release:push`
  - Minor: `npm run version:minor && npm run release:push`
  - Major: `npm run version:major && npm run release:push`
- Automation (if configured in CI):
  - On merged PRs into `main`, CI bumps version based on branch/labels:
    - `feat/*` → minor, `fix/*|bugfix/*` → patch, `major` label or `[major]` in title → major
  - A GitHub Release is created on tag push.

## Deployment
See [docs/DEPLOYING_TO_CLOUDFLARE.md](./docs/DEPLOYING_TO_CLOUDFLARE.md) for Cloudflare deployment, logs, and CLI usage.

## Content author checklist (non-technical)
Use this list to prepare and submit a new blog post.

1) Prepare content
- Title (human-friendly)
- Short description (1–2 sentences)
- Publication date (e.g., “Jan 31 2025”)
- Optional: Updated date
- Hero image (optional): JPG/PNG 1200×630, place under `public/` and note its path, e.g., `/my-image.jpg`

2) Create the post file
- File path: `src/content/blog/<slug>.md` (or `.mdx` for advanced embeds)
- Paste this frontmatter at the top:

```md
---
title: "My post"
description: "One-line summary"
pubDate: "Jan 31 2025"
updatedDate: "Feb 10 2025" # optional
heroImage: "/my-image.jpg"   # optional
---
```

- Write your content below the frontmatter. For MDX, you can embed components.

3) Open a Pull Request
- From your branch, open a PR with:
  - If it’s a new feature/content: branch `feat/<topic>`
  - If it’s a fix/tweak: branch `fix/<topic>`
- Fill the PR template and pick the release type.

4) Review and publish
- A maintainer merges the PR into `main`.
- CI may bump the version and create a tag/release.
- Deployment to Cloudflare: follow the deployment doc or your team’s release cadence.

Troubleshooting: If you need help, ping a maintainer; you don’t need local tools to contribute content.

## 👀 Want to learn more?

Check out [our documentation](https://docs.astro.build) or jump into our [Discord server](https://astro.build/chat).

## Credit

This theme is based off of the lovely [Bear Blog](https://github.com/HermanMartinus/bearblog/).
