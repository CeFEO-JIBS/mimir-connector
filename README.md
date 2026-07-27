# mimir-connector

Public **landing site** for the Mímir MCP connector, served by GitHub Pages at
**mimir.familybusiness.se**.

Four static pages (`index`, `install`, `faq`, `contact`) sharing one `styles.css`,
plus `assets/`, `CNAME` and `.nojekyll`. No build step.

> ⚠️ **This repo holds the SITE, not the service.** The Deno connector — OAuth server,
> six MCP tools, systemd unit — lives in **`CeFEO-JIBS/fbp-mcp-connector`** (private)
> and runs at `/opt/fbp-mcp-connector` on the Hetzner host. Never push connector code
> here, and never push site files there. The names are close; the contents are not.

> Header, nav and footer are **hardcoded in all four pages** — there is no shared
> include, so any sitewide chrome change must touch every file.

## Deploy

GitHub Pages publishes `main` automatically. The repo must be **Public** (Pages will not
serve a private repo on the free plan), and DNS needs a CNAME `mimir` →
`cefeo-jibs.github.io` at one.com.

```bash
git add -A && git commit -m "…" && git push
```

Verify via the Pages host, which resolves before the custom domain propagates:

```bash
curl -s "https://cefeo-jibs.github.io/mimir-connector/?cb=$(date +%s)" | head -5
```

Old content on first check → wait 60–90 s for the Pages rebuild and re-check.

## Editing

Clone first, never clobber — the repo may be ahead of any local copy:

```bash
git clone https://github.com/CeFEO-JIBS/mimir-connector.git
```

Then check the diff is only what you intended before committing:

```bash
git diff --cached --stat
```

## Related

| | |
|---|---|
| Connector service (private) | `CeFEO-JIBS/fbp-mcp-connector` → `mcp.familybusiness.se/fbp` |
| Sibling site | `CeFEO-JIBS/dashy-connector` → `claude.fbdashboard.org` |
