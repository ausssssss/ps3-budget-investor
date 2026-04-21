# 💰 Budget Investor — Minimum Downfall Finder

A live crypto analysis dashboard for budget investors aiming for maximum profit with minimal risk. Identifies the coin with the **least average downfall** (1H + 24H + 7D) across five selectable price ranges using a slicer-connected KPI system.

**Built by Austin | Completed: 23 March 2026**

---

## 📌 Features

- **5 Price Range Slicer** — `$0–$0.05` / `$0.05–$0.5` / `$0.5–$5` / `$5–$50` / `>$50`
- **5 KPIs** that update on every slicer click:
  - Coin Name — least avg downfall coin in range
  - Coin Symbol — ticker
  - Current Price — live USD
  - Avg Downfall % — mean of 1H, 24H, 7D absolute drops
  - Total Coins in Range — count of records considered
- **Detail table** — all coins in range sorted by avg downfall ascending (best pick highlighted)
- **Zero dependencies** — pure HTML/CSS/JS + CoinGecko API

---

## 🧮 Avg Downfall % Formula

```
Avg Downfall % = ( |1H Change%| + |24H Change%| + |7D Change%| ) / 3
```

All three period changes are assumed to represent **downfall** (price drops from current). Absolute values are used so the metric remains positive regardless of API sign.

---

## 🎛️ Price Range Slicer

| Slicer Button | Price Condition |
|---------------|----------------|
| $0 – $0.05    | 0 ≤ price < 0.05 |
| $0.05 – $0.5  | 0.05 ≤ price < 0.5 |
| $0.5 – $5     | 0.5 ≤ price < 5 |
| $5 – $50      | 5 ≤ price < 50 |
| > $50         | price ≥ 50 |

All 5 KPIs and the detail table update instantly when the slicer changes.

---

## 🔌 API Used

**CoinGecko Public API v3** — no key required.

```
GET https://api.coingecko.com/api/v3/coins/markets
  ?vs_currency=usd
  &order=market_cap_desc
  &per_page=250
  &page=1,2,3
  &sparkline=false
  &price_change_percentage=1h,24h,7d
```

Pages 1–3 fetched in parallel (~750 coins), filtered and classified client-side.

---

## 📁 Files

```
ps3-budget-investor/
├── index.html    # Complete dashboard
└── README.md     # Documentation
```

---

*Completed: 23 March 2026 | Author: Austin*
