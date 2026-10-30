<!-- cover -->
# Contentrain Next White-Label Portal

A Next.js (App Router) starter for a portal that serves several tenants: each tenant's name, terminology, available locales, support links and brand badge are typed Contentrain content, not conditionals in components.

It shows how a white-label product keeps tenant-specific language governed and reviewable: a new tenant or a renamed term is a content change, versioned in git next to the code.

## Use this template

Click **Use this template** on GitHub to create your own repository. To edit the content visually, connect the new repository in [Contentrain Studio](https://contentrain.io/studio): it reads `.contentrain/` as it is, and saves edits as commits.

## Quick start

```bash
pnpm install
pnpm dev        # http://localhost:3000
```

| Command | What it does |
|---|---|
| `pnpm dev` | Next.js dev server |
| `pnpm validate` | Checks models and content (`contentrain validate`) |
| `pnpm check` | Type check |
| `pnpm build` | Production build |
| `pnpm contentrain:generate` | Regenerates the typed client in `.contentrain/client/` after a model or content change |

## Pages

- `/`: portal overview
- `/tenants`: every tenant profile
- `/tenants/[slug]`: one tenant's portal, prerendered for each profile (`acme-finance`, `apex-logistics`, `northwind-health`)
- `/settings`: settings groups
- `/billing`: billing plans
- `/operations`: notices and audit events
- `/architecture`: how the starter is put together

## Content model

Content lives in `.contentrain/` (models in `models/`, entries in `content/`). Pages read it in Server Components through the generated `#contentrain` client.

| Model | Kind | Domain | Used for |
|---|---|---|---|
| `tenant-profile` | collection | brand | Tenant name, slug, industry, terminology, locales, support and docs links, brand badge |
| `site-settings` | singleton | system | Site name, tagline, theme, default locale |
| `navigation` | singleton | system | Sidebar items, announcement, call to action |
| `footer` | singleton | system | Footer blurb, link columns, legal notice |
| `seo-defaults` | singleton | system | Default meta title, description, canonical base, OG image |
| `dashboard-overview` | singleton | app | Overview heading, summary and primary action |
| `settings-group` | collection | app | Settings sections and their items |
| `billing-plan` | collection | app | Plans, prices, features, call to action |
| `ui-copy` | dictionary | app | Interface labels used across the shell |
| `ops-notice` | collection | ops | Operational notices with tone and action |
| `audit-event` | collection | ops | Audit log entries |

## Contentrain

Contentrain is a content governance ecosystem for teams and AI agents: content stays in your repository as typed JSON, with schemas, validation and git history.

- Docs, CLI and SDK: [ai.contentrain.io](https://ai.contentrain.io)
- Next.js guide: [ai.contentrain.io/guides/frameworks#next-js-app-router](https://ai.contentrain.io/guides/frameworks#next-js-app-router)
- Studio: [contentrain.io/studio](https://contentrain.io/studio)

## Deploy

`netlify.toml` builds with `pnpm deploy:netlify` on Node 22; leave the publish directory empty so Netlify's Next.js runtime handles it. Any host that runs Next.js works.

[![Deploy to Netlify](https://www.netlify.com/img/deploy/button.svg)](https://app.netlify.com/start/deploy?repository=https%3A%2F%2Fgithub.com%2FContentrain%2Fcontentrain-starter-next-white-label-portal)

## License

MIT
