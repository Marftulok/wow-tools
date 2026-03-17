# ⚔️ WoW Market Tools

A lightweight, browser-based toolkit for analyzing World of Warcraft Auction House prices and predicting market trends — powered by [WowPriceHub](https://wowpricehub.com) data.

**No server required.** Just open in your browser or host on GitHub Pages.

## 🔗 Live Demo

> **[marftulok.github.io/wow-tools/wow_deals_dashboard.html](https://marftulok.github.io/wow-tools/wow_deals_dashboard.html)**

## Tools

### 📈 Rising Deals Dashboard

Scans rising (or falling) AH deals and cross-references them with **US market data** to generate trading signals.

- Fetches EU deals from WowPriceHub
- For each item, checks the US market's 24h price change as a **leading indicator** (US resets happen ~24h before EU)
- Generates a weighted signal: **STRONG BUY → BUY → HOLD → SELL → STRONG SELL**
- Sortable by signal strength, US change, EU change, price, or quantity
- Click any row to open the detailed predictor

### ⚔️ Price Predictor

Deep-dive into a single item's price history with trend forecasting.

- Paste any WowPriceHub item URL
- Interactive chart with **Linear Regression** and **Moving Average** forecast lines
- Optional **US Market overlay** (red line, shifted +24h) to preview reset impact
- **US Reset Impact** prediction card
- Persistent search history with autocomplete

## How It Works

Both tools call the WowPriceHub API directly from your browser — there's no backend server.

The US comparison feature uses the idea that US servers reset ~24 hours before EU. By checking how US prices moved after their reset, you get an early preview of what might happen on EU.

```
EU rising items → fetch US price data for each → calculate 24h % change
→ combine EU momentum (40%) + US leading indicator (60%) → signal
```

## Setup

**Local:** Just open `wow_deals_dashboard.html` in your browser.

**GitHub Pages:** Fork this repo, enable Pages in Settings (deploy from `main` branch), done.

## Tech

- Vanilla HTML + CSS + JavaScript (no build step, no dependencies to install)
- [Chart.js](https://www.chartjs.org/) for data visualization
- [WowPriceHub API](https://wowpricehub.com) for market data
- `localStorage` for persistent search history
- `sessionStorage` for dashboard state caching

## Disclaimer

This tool is for informational purposes only. Price predictions are based on simple trend analysis and US/EU market correlation — not financial advice. Use at your own risk.

## License

[MIT](LICENSE)
