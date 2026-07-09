# Lease New vs Buy Used — Ontario Car Cost Calculator

A single-file static website that compares the total long-term cost of **leasing new cars back-to-back** versus **buying a used car (and replacing it when it wears out)** over a user-selected number of years. All amounts are in Canadian dollars, with defaults based on Ontario averages and Ottawa figures where available (as of July 2026).

The entire site is [`index.html`](index.html) — no build step, no dependencies, no backend.

## Try it locally

Just double-click `index.html`, or serve it:

```
python -m http.server
```

## Deploy to GitHub Pages

1. Create a new repository on GitHub (e.g. `lease-vs-buy-calculator`).
2. From this folder:
   ```
   git init
   git add index.html README.md
   git commit -m "Lease vs buy used car calculator"
   git branch -M main
   git remote add origin https://github.com/<your-username>/lease-vs-buy-calculator.git
   git push -u origin main
   ```
3. On GitHub: **Settings → Pages → Source: Deploy from a branch → Branch: `main` / root → Save**.
4. Your site goes live at `https://<your-username>.github.io/lease-vs-buy-calculator/` within a minute or two.

To update the site later, edit `index.html`, commit, and push — Pages redeploys automatically.

## How the model works

- **Leasing:** consecutive leases for the whole horizon. Each renewal is repriced upward by new-vehicle inflation. Costs = (payments + upfront fees) × 1.13 HST + insurance + fuel + maintenance.
- **Buying:** a used car purchased with a loan (or cash if rate = 0), 13% HST on the price. When the car reaches its lifespan, it is sold at residual value and replaced with a comparable used car at an inflation-adjusted price. The plotted "net cost" subtracts your vehicle equity (resale value minus remaining loan balance), since the buyer holds an asset the leaser doesn't.
- Operating costs are held flat in today's dollars for both options, which keeps the comparison fair.

## Updating the default statistics

Defaults are hard-coded in the `value=` attributes of the inputs in `index.html`, and the sources are listed in the page's "Assumptions & data sources" section. Suggested refresh points:

| Default | Source to re-check |
|---|---|
| Lease payment, used/new prices | [AutoTrader Price Index](https://www.autotrader.ca/editorial/price-index/), [LeaseCosts Canada](https://www.leasecosts.ca/en/articles/how-much-canadians-pay-average-every-month-car-lease) |
| Ottawa insurance premiums | [Ratehub](https://www.ratehub.ca/blog/how-much-is-car-insurance-in-ottawa/), [RATESDOTCA](https://rates.ca/insurance-quotes/auto/ottawa) |
| Fuel and operating costs | [CAA Driving Costs Calculator](https://carcosts.caa.ca/), [Ontario motor fuel prices](https://www.ontario.ca/motor-fuel-prices/) |
