# Kane Tools

Landing page linking to internal tools built by The Kane Company.

- **Kane Intelligence Brief** — https://kane-intelligence-brief.vercel.app
- **Zoning Watcher** — Seacoast NH zoning & planning board monitor (web app coming soon)

Static single-page site — just [public/index.html](public/index.html), no build step. Anything placed in `public/` is served as-is.

## Hosting & access control

Hosted on **Cloudflare Workers** (static assets), connected to this repo — every push to `main` deploys automatically. [wrangler.jsonc](wrangler.jsonc) tells Cloudflare to serve the `public/` directory; there is no build command.

- **Domain**: `kanetools.com` (registered in AWS Route 53; DNS delegated to and managed in Cloudflare). Each internal tool gets its own Worker project on its own subdomain of kanetools.com.
- **Access control**: Cloudflare Access (Zero Trust) sits in front of the site. Policy: allow email addresses ending in `@kane.co`, verified by a one-time PIN emailed to the visitor. Sessions last up to 30 days. Configured in the Cloudflare Zero Trust dashboard, not in this repo.
- DNS changes are reviewed by IT before being applied.
