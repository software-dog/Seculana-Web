# Seculana-Web

The public storytelling site for Seculana.

The product repository, `software-dog/Loom`, is the authoritative source for product behaviour and roadmap status. This repository is intentionally separate so the site can evolve without coupling its deployment or design dependencies to the Seculana engine.

## Development

Requires Node.js 22.23.4 or newer.

```bash
npm install
npm run dev
```

Validate a production build:

```bash
npm run build
```

The site is static output. Core reading should work without client-side JavaScript.

## Project documents

- `SECULANA-SITE-INTAKE.md` — narrative and build brief
- `ROADMAP.md` — website increments
- `docs/SOURCE-AUDIT.md` — live product facts and status
- `docs/VISUAL-COLLABORATION.md` — authentic capture workflow

## Authentic product media

Real Seculana screenshots/video belong under `public/media/captures/`. Until a capture exists, use the `CapturePlaceholder` component rather than fabricating product UI.
