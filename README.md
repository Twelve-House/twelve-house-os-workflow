# Twelve House OS — Workflow Map

Interactive drag-and-zoom map of the whole Twelve House OS: platform core, sales, delivery,
client portal, support and the daily automation run.

**Live:** https://twelve-house.github.io/twelve-house-os-workflow/workflow/

> This repository and the site are **public**. Do not add secrets, personal names, customer
> data or env var values. Everything here can be read by anyone with the link.

## Layout

```
index.html            redirects to workflow/
workflow/index.html   the map (single file, no build step)
```

## Updating the map

All content lives in the `<script>` block of `workflow/index.html`:

| Constant | What it holds |
|---|---|
| `BANDS`  | the horizontal bands and which areas sit in each, left to right |
| `ZONES`  | one entry per area: `title`, `tag`, `sub`, `nodes`, `edges` |
| `CROSS`  | links between areas, written as `zone.node` ids |

- Node: `[id, col, row, kind, title, detail, code?, span?, jumpToZone?]`.
  Position is a grid cell inside its area; sizes and spacing are computed automatically.
- Kinds: `act` human action · `sys` system · `evt` outbox event · `st` status · `gate` decision/approval ·
  `agt` agent · `ext` external service · `data` store · `stop` paused · `fut` planned (P5/P6).
- Edge: `[from, to, label?, style?]` with style `''` (direct), `evt`, `gate`, `cron`, `neg`.

Open `workflow/index.html` locally in a browser to check, then commit and push to `main`.
GitHub Pages redeploys within a minute or two.

Commit messages follow the house rule: `CU-<task-id> <summary>`.
