# NEXT SESSION HANDOFF — Fluidseal World

Updated: 2026-07-08 (go-live session)

## State
- **LIVE**: https://world.fluidsealab.com (repo `fluidseal-world`, Pages main/root, Azure DNS CNAME `world` → davidranderson1.github.io, HTTPS enforced).
- Local repo: `ClaudeAgent\Marion\fluidseal-world\` (nested under Marion folder — cosmetic only, own .git).
- App = v8: spread 2000×1560 layout, scene mode (24 equipment hotspots, labeled dots), 9-family grid (all slugs verified live on sealsonline), hash deep links (#oilgas…), Properties section, stat strip, intro zoom, sandbox-safe setHash(), drag-then-click pin fix, scenebar hide fix.

## Pending commits on David's machine (commit `summary` + push each)
1. `fluidseal-world` — drop in latest index.html (v8, from chat download) if not already pushed.
2. `marion` — edited on disk: World nav link + `?q=` chat prefill (World's "Ask Marion" CTA passes ?q=<Market> seals).
3. `fluidseal-training` — edited on disk: ◂ Fluidseal World header link.
4. `fluidseal-posters` — edited on disk: ◂ Fluidseal World banner link. 31MB write verified byte-exact (+270B, valid tail). Workbook untouched (nav-only edit).

## Backlog
- Training portal says "Internal Staff Training" but is public — first candidate for internal tier (Supabase RLS or Cloudflare Access) when auth lands. properties.json already carries visibility flags.
- Scene v2 ideas: more hotspots (forestry log truck, downtown fleet), per-scene blurbs.
- Profile photos in panels: host copies on marion.fluidsealab.com (do NOT hotlink hallite.com).
- Supabase: RLS enable + final data load + Pro tier before production cutover (unchanged).
- JD overflow harvest decision (stage vs direct write) — unchanged.
- anyseals.json yellow-chip UI render fix — unchanged.

## Build chain (Claude computer, may reset)
gen2.py (generator, all hotspot attrs) → world-hd2.html → splice SVG into shell → v3..v8 patches. Canonical final: world-v8.html = repo index.html. If container reset, repo index.html is source of truth.
