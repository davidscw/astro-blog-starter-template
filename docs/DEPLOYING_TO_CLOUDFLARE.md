# Deploying to Cloudflare (Workers)

This project ships with Cloudflare Workers support via Wrangler.

## Prerequisites
- Cloudflare account with Workers enabled
- Node.js LTS and npm installed
- Wrangler CLI: `npm i -g wrangler` (or use npx)

## One-click deploy (optional)
[![Deploy to Cloudflare](https://deploy.workers.cloudflare.com/button)](https://deploy.workers.cloudflare.com/?url=https://github.com/cloudflare/templates/tree/main/astro-blog-starter-template)

## Create from template (C3 CLI)
```bash
npm create cloudflare@latest -- --template=cloudflare/templates/astro-blog-starter-template
```

## Local build & preview
```bash
npm install
npm run build
npm run preview
```

## Deploy with Wrangler
```bash
# Authenticate (browser login)
npx wrangler login
# Deploy to your Cloudflare account
npm run build && npm run deploy
# Tail logs
npx wrangler tail
```

## Configuration files
- `wrangler.json` — account/project configuration
- `worker-configuration.d.ts` — TypeScript type support for Worker config

## Environments (optional)
Use Wrangler environments (e.g., `--env production`) if you maintain multiple deployments.

