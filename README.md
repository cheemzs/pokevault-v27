# PokéVault v27

Pokémon card & sealed product portfolio tracker with live TCG prices, price history charts, graded card market data, trade analyser, P/L dashboard, and public portfolio sharing.

## What's new in v27

### Grade selector → dropdown
- **Replaced grade chips** with a clean dropdown menu in the card detail chart — no more row of buttons that wraps on small screens.
- **Curated grade list**: PSA 10, PSA 9, TAG 10, TAG 9, BGS BL 10 (shown only when data is available), BGS 10, BGS 9.
- **BGS BL 10** (Black Label 10.0) is conditionally included — it only appears if the API returns data for that grade.
- The same curated list is also used in the "Add to Portfolio" condition/grade selector.

### 3-month chart default + time range buttons
- **Portfolio Value History** chart now defaults to **3M** (90 days) instead of showing all-time data.
- Added **1M / 3M / 6M / MAX** range buttons to both the portfolio chart modal and the card detail price history chart.

### Bigger card artwork
- The artwork tab in the card detail modal now displays the card image significantly larger (up to 380px wide, 540px tall on desktop; full-width on mobile) with a subtle glow background and hover-zoom effect.
- The thumbnail in the Price Info tab is also slightly larger (88×122px) with a deeper drop shadow.

### Chart visual polish
- Both charts now use smooth gradient fills and **no dot markers** (dots appear only on hover), matching the sleek dark-mode investment app aesthetic.

### Mobile improvements
- Modals slide up as bottom sheets on phones (≤480px), using `border-radius: 20px 20px 0 0`.
- Grade dropdown goes full-width on small screens.
- Card detail header stacks vertically (image above text) on mobile.
- Various padding/spacing tightened for smaller viewports.

## Stack

- **Frontend**: Vanilla HTML/CSS/JS (no build step)
- **Backend**: Vercel serverless functions (`/api/*.js`)
- **Database**: Supabase (Postgres)
- **Prices**: PokémonPriceTracker API v2 with eBay graded sales data

## Supabase schema

Run `supabase_schema_v26.sql` against your Supabase project. No schema changes from v26.

## API endpoints

| Endpoint | Method | Notes |
|---|---|---|
| `/api/pokeprice` | GET | Proxies PokémonPriceTracker API. Pass `includeEbay=true` for graded data. |
| `/api/search` | GET | Card search helper |
| `/api/portfolio` | GET/POST/PATCH/DELETE | Portfolio CRUD (requires auth) |
| `/api/auth` | POST | Auth helper |
| `/api/graded` | GET | Legacy endpoint (unused) |
