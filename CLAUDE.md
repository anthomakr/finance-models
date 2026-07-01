# finance-models — briefing

A curated library of forkable Layerz financial models, published under **@anthomakr**.
Each `models/<slug>/README.md` is a rendered page for **one live Layerz model**.
The models live in Layerz; this repo is the readable catalog that points into them.

## Golden rule

Pages are **generated from the live model via the Layerz MCP**, not hand-edited.
To publish or refresh a model page:

1. `layerz_get_finance_md(model_id)` + `layerz_read(model_id, with_values: true, granularity: "yearly", roles: ["section","formula","kpi","balance"])`
2. Regenerate `models/<slug>/README.md` with, in order:
   - title + one-line purpose
   - badges (Open in Layerz, currency, horizon, `3-statement balanced`)
   - **Dashboard — at a glance** (headline KPIs of the last year)
   - **P&L** + a domain table (SaaS metrics, cash & balance…), all **real numbers**
   - a **mermaid** flowchart of the structure
   - conventions (currency, periodicity, sign)
   - how to use it + the Open in Layerz button (top and bottom)
3. Update the model row in the root `README.md`.
4. `git commit` + `git push`.

## Conventions

- Copy is **English** (public-facing).
- **Open in Layerz** button → `https://app.layerz.cc/models/<model_id>` (same URL used for sharing).
- Voice: *"we share the recipe, not the black box."* Personal repo, not corporate Layerz Labs.
- Dashboard screenshots are real Layerz exports dropped in `.github/assets/` (concierge step, not auto-generated).

## Model IDs

| slug | model_id |
|---|---|
| coffee-shop-nyc | `d161c3c4-ade6-48e4-b162-48fa2f81c545` |
| saas-reporting-forecast | `39550987-f253-4a36-b067-6daddcb1e3ff` |
