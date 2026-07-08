# Fluidseal World

Interactive isometric market mural — the front door to the Fluidseal ecosystem.
Live at **https://world.fluidsealab.com** · Parent property over Marion, Posters, Training, and SealsOnline.

## Repo contents

| File | Purpose |
|---|---|
| `index.html` | The entire app — SVG world, scene mode, panels, all JS/CSS. Single file, no build step. |
| `CNAME` | `world.fluidsealab.com` (GitHub Pages custom domain) |
| `properties.json` | Federation manifest — every Fluidseal property with a `visibility` flag. Children can fetch this to render shared nav. |

## Go-live (one time)

1. Create public repo `fluidseal-world` → clone in GitHub Desktop.
2. Copy this folder's contents in → commit `summary` → push.
3. Repo Settings → Pages → Deploy from branch, `main` / `(root)`. CNAME file auto-sets the domain.
4. GoDaddy DNS: CNAME record, name `world`, value `davidranderson1.github.io`.
5. Pages → Enforce HTTPS once the cert issues. Verify https://world.fluidsealab.com.

404s right after a push are Pages build lag, not missing files.

## Editing guide

All editable data sits at the top of the `<script>` block in `index.html`:

- **`MARKETS`** — 11 market objects: `anchor` (hash key + SVG `data-anchor`), `name`, `color`, `blurb`, `apps`.
- **`FAMILIES`** — the 9-family grid shown in every panel. Slugs are verified live against `sealsonline.com/en/flabed/categories/…`.
- **`PROPERTIES`** — the ecosystem links in the Markets sheet. Mirror changes into `properties.json`.

In the SVG:

- `data-anchor="market"` — district group; scene mode frames its bounding box.
- `data-pin="x,y"` — world-coordinate override for a market's label pin.
- `data-hotspot="market:catalog/path"` + `data-hslabel="Label"` — clickable equipment. Scene mode turns these into labeled dots; clicking opens the panel with that family highlighted. Empty path (`"oilgas:"`) opens the panel with nothing highlighted.
- Animation classes: `.rock` (pumpjacks), `.spin` (turbines), `.bank` (aircraft), `.flick` (flare), `.drift` (clouds). All disabled under `prefers-reduced-motion`.

Deep links: `world.fluidsealab.com/#oilgas` (any market anchor) flies straight into that scene. Use these from Marion, Posters, and campaigns.

## Federation

Children link back with a small `◂ Fluidseal World` header link → `https://world.fluidsealab.com`. The World links out to every property (panel CTAs, posters chips, Properties sheet). `properties.json` is the single source of truth for the property list.

## Security / roles roadmap

This repo is **public and static — nothing sensitive ever lands here.**

- **Public tier (now):** everything in this repo.
- **Internal tier (later):** pricing, branch inventory, margins, OEM cross-ref internals — served from Supabase behind RLS + auth (project `hnmbjqhxvxakhdzgetxw`; RLS enablement already queued for cutover), or an `ops.fluidsealab.com` surface behind Cloudflare Access.
- `properties.json` already carries `visibility: public|internal` per property; the client only renders `public`. When auth lands, authenticated sessions unlock `internal` entries — a flip, not a refactor.

## Commit convention

Commit message: `summary`. Push via GitHub Desktop.
