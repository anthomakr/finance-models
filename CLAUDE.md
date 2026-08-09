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

- **Published models are frozen.** Every model listed below is a live model backing a public page. Do not edit or delete one for a demo, a test or a quick fix: the page here would keep describing a model that no longer exists. Fork it and work on the fork. The weekly `check-links` workflow catches a dead model or OG card, but only after the fact.
- Page copy is **English** (public-facing). The underlying model may stay in another language when the structure is jurisdiction-specific (e.g. the HoldCo/SPV template is French: PPA tariffs, régime mère-fille). In that case the page says so in a badge and a short note, rather than translating the model and breaking its accuracy.
- **This catalog and the Layerz system templates are two different lists.** A model can be a system template without a page here, and vice versa. Reconcile deliberately (`layerz_list_templates({ scope: "system" })`), never assume they match.
- **Open in Layerz** button → `https://layerz.cc/models/<model_id>` (same URL used for sharing).
- Voice: *"we share the recipe, not the black box."* Personal repo, not corporate Layerz Labs.
- Dashboard screenshots are real Layerz exports dropped in `.github/assets/` (concierge step, not auto-generated).

## Model IDs

| slug | model_id |
|---|---|
| coffee-shop-nyc | `d161c3c4-ade6-48e4-b162-48fa2f81c545` |
| saas-reporting-forecast | `39550987-f253-4a36-b067-6daddcb1e3ff` |
| project-finance | `5e54258d-e4b6-48a0-91b0-32d4271fe224` |
| saas-series-a | `3f9737d9-e7c8-4f56-b962-6bb9963d6095` |
| lbo | `57af5678-5e56-44bc-9d46-379b8eb961b6` |
| monthly-close | `ccea856a-6ee5-4f79-b891-e1c321daac4d` |
| valuation | `29f9cebe-cfc3-403b-82c4-bd50e1f8e042` |
| tech-ma-lbo | `3657668b-4684-4010-bd9b-c83845db1dff` |
| saas-cohort | `0cf40614-eb52-48b9-8d72-cbecc84860b2` |
| professional-services | `d0e3688b-eceb-4341-ada1-e8a45957b3d8` |
| ecommerce-retail | `d5e899c7-a710-4f2a-9b05-cc3e88690af1` |
| holdco-spv | `9548419c-9659-4da0-af74-14d58e61a220` |
| inventory-methods | `4dd73ff7-3ce6-4e87-b823-6699f4985255` |

## Monthly models — read the right period

For a monthly model, `granularity: "yearly"` **sums flows and closes stocks**. A balance-sheet formula (Total Assets, Receivables) has no `aggregation`, so it defaults to sum and the yearly figure is meaningless. Read balance-sheet and stock lines with explicit `periods: ["2026-12", ...]`; keep the yearly grain for P&L flows only.
