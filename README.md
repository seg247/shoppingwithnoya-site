# shoppingwithnoya-site

Static SEO deal site for [@shoppingwithnoya](https://t.me/shoppingwithnoya) — auto-generated from the deal bot's post log.

**Live site:** https://seg247.github.io/shoppingwithnoya-site

## What this is

A public-facing Astro static site that:
- Publishes every Amazon deal as a standalone indexed page
- Drives organic Google traffic to the Telegram channel
- Auto-rebuilds when deal data is pushed from the bot repo

## Stack

- [Astro](https://astro.build) — static site generator (zero JS by default, great SEO)
- GitHub Pages — free hosting
- GitHub Actions — auto-deploy on push

## Data

Deal data comes from the private bot repo (`seg247/shoppingwithnoya`) via a push script.

**Do not manually edit** `src/data/site-data.json` — it is overwritten automatically by `scripts/push-site-data.sh` in the bot repo.

## Local development

```bash
npm install
npm run dev        # dev server at localhost:4321
npm run build      # static build → dist/
npm run preview    # preview built site
```

## Deployment

Automatic on push to `main` via `.github/workflows/deploy.yml`.

## Adding new deals

Deals are pushed from the bot repo. Run on the bot machine:

```bash
cd ~/projects/shoppingwithnoya
node scripts/export-site-data.js --out ../shoppingwithnoya-site/src/data/site-data.json
cd ../shoppingwithnoya-site
git add src/data/site-data.json && git commit -m "chore: update deal data" && git push
```

Or run automatically via cron — see `scripts/push-site-data.sh` in the bot repo.

## SEO

Each deal page includes:
- Unique `<title>` and `<meta description>`
- Open Graph + Twitter card tags
- JSON-LD Product structured data (eligible for Google rich results)
- Sitemap at `/sitemap.xml`
- robots.txt allowing all crawlers
