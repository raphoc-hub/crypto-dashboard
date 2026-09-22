# CryptoEdge — Market Dashboard

A browser interface for cryptocurrency prices, exchange spreads, funding rates and market indicators. The public repository contains the frontend only.

[Interface preview](https://raphoc-hub.github.io/crypto-dashboard/) · [Portfolio](https://raphoc-hub.github.io/#work)

## What is here

- Bitcoin and Ethereum price panels, sentiment and market-summary fields.
- Exchange-spread and funding-rate tables.
- A Chart.js spread-history chart and indicator list.
- A single [`index.html`](index.html) containing the HTML, CSS and JavaScript.

Chart.js and Google Fonts are loaded from external hosts. There is no package installation or build step.

## Preview locally

Requires Git, Python 3 and an internet connection for the external assets.

```sh
git clone https://github.com/raphoc-hub/crypto-dashboard.git
cd crypto-dashboard
python3 -m http.server 8000 --bind 127.0.0.1
```

Open <http://127.0.0.1:8000/>. The layout loads, but market values remain empty without a compatible backend. Stop the server with `Ctrl+C`.

## Data flow and limitations

The client requests **`GET /status` every five seconds** from the same origin. It expects JSON containing `btc`, `eth`, `fng`, `market`, `funding`, `signals` and `ts`; the exact field usage is in `poll()` in `index.html`.

No `/status` server, market-data collector, sample dataset or random-data generator is included. A plain static server returns `404` for that route. After three failed polls, the interface displays a connection-loss banner. The spread chart accumulates successful responses during the browser session; it is not a bundled historical dataset.

## Status and provenance

**Frontend prototype, not a working public market-data service.** The visible `LIVE` label is part of the interface and does not confirm a connection. This repository does not execute trades or establish the accuracy, timeliness or usefulness of any externally supplied indicators. It is not investment advice.

## License

[MIT](LICENSE).
