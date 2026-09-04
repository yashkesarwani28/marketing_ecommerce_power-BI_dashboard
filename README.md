# 📊 E-Commerce & Marketing Analytics — Power BI Dashboard

![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
![Status](https://img.shields.io/badge/Status-Complete-4CAF50?style=for-the-badge)
![Records](https://img.shields.io/badge/Records-300K%2B-blue?style=for-the-badge)
![License](https://img.shields.io/badge/License-MIT-lightgrey?style=for-the-badge)

**Prepared by:** Yash Kesarwani &nbsp;|&nbsp; **Date:** April 2026

---

## 📝 What is this project?

A 6-page Power BI dashboard that turns **300,000+ raw e-commerce and marketing records** (transactions, browsing events, campaigns, products, and customers) into a single connected data model — surfacing revenue trends, campaign ROI, customer loyalty behavior, funnel drop-off, product performance, and country-level sales, with a written insight and recommendation on every page.

**In one line:** *Five raw tables → cleaned and modeled in Power Query/DAX → six interactive report pages answering "where is revenue coming from, and what should we do next."*

---

## 🧹 ETL & Data Modeling

### Step 1 — Extract
Five source tables were loaded into Power BI:
- **`transactions`** — every order (transaction_id, timestamp, customer_id, product_id, quantity, discount_applied, gross_revenue, campaign_id, refund_flag)
- **`events (2)`** — every browsing/behavior event (event_id, timestamp, customer_id, session_id, event_type, product_id, device_type, traffic_source, campaign_id, page_category, session_duration_sec, experiment_group, Hour, day, datee, year)
- **`campaigns`** — every marketing campaign (campaign_id, channel, objective, start_date, end_date, target_segment, expected_uplift)
- **`products`** — product catalog (product_id, category, brand, base_price, launch_date, is_premium)
- **`customers`** — customer master data (customer_id, demographic and loyalty attributes)

### Step 2 — Clean (Power Query)
- **Type correction:** enforced correct data types on every column — dates as Date/DateTime (not text), numeric fields as Decimal/Whole Number, flags (`refund_flag`, `is_premium`) as consistent Boolean/Text values.
- **Date literal fix:** caught and corrected a downstream DAX bug where a date was written as `14-04-2023` instead of `DATE(2023,4,14)` — DAX had been silently evaluating it as arithmetic rather than a real date, which affected the Active Campaigns measure until fixed.
- **Duplicate & null checks:** removed exact duplicate rows on primary keys (`transaction_id`, `event_id`, `campaign_id`, `product_id`, `customer_id`) and profiled each column for nulls/blanks before loading.
- **Text standardization:** trimmed whitespace and standardized casing on categorical fields (`channel`, `objective`, `event_type`, `device_type`, `category`) so grouping/filtering doesn't silently split identical values (e.g., "Email" vs "email").
- **campaign_id = 0 handling:** kept `0` as a valid "no campaign attribution" value in `transactions`/`events` rather than treating it as a missing/error value, since it's a meaningful business state (organic activity with no campaign behind it).

### Step 3 — Model (relationships)
A star-schema-style model was built with `transactions` and `events (2)` as fact tables, and `customers`, `products`, `campaigns` as dimension tables:

| From | To | Cardinality |
|---|---|---|
| `transactions[customer_id]` | `customers[customer_id]` | Many-to-One |
| `transactions[product_id]` | `products[product_id]` | Many-to-One |
| `transactions[campaign_id]` | `campaigns[campaign_id]` | Many-to-One |
| `events (2)[customer_id]` | `customers[customer_id]` | Many-to-One |
| `events (2)[product_id]` | `products[product_id]` | Many-to-One |
| `events (2)[campaign_id]` | `campaigns[campaign_id]` | Many-to-One |

This lets a single slicer (e.g., Country, Channel, Loyalty Tier) filter across both behavioral (events) and financial (transactions) metrics at once.

### Step 4 — Transform into measures (DAX)
Raw columns were turned into report-ready KPIs — Total Revenue, Total Orders, Average Order Value, Conversion Rate, Refund Rate, Average Campaign Uplift, Active Campaigns, and Formatted Session Duration. Full formulas and a documented bug-fix (Active Campaigns date logic) are in [`dax/measures.md`](dax/measures.md).

---

## 📈 Reporting / Dashboard

Six connected report pages, each ending in a **Key Insights** panel with an action-ready recommendation:

| Page | Focus |
|---|---|
| **Executive Overview** | Revenue trend, channel mix, funnel snapshot — the 30-second health check |
| **Campaign Analysis** | Revenue and uplift by channel/objective, best-performing campaign quadrant |
| **Customer Insights** | Demographics, loyalty-tier distribution, country breakdown |
| **User Behavior & Event Analysis** | Funnel drop-off, device usage, session duration by event |
| **Product Performance** | Top products, category revenue mix, price-vs-revenue performance |
| **Transaction & Geographical Revenue Analysis** | Country-level revenue/orders, refund rate vs. target, AOV by country |

Every page shares a common set of slicers (Channel, Country, Objective, Category, Date) so filtering one page's context can be carried across the story. Full quantified insights per page are documented in [`docs/insights_summary.md`](docs/Insights_summary.md).

---

## 📂 Repo Structure

```
pulse-commerce-analytics/
├── README.md
├── assets/                  # dashboard page screenshots
├── data/
│   └── data_dictionary.md   # full table/column documentation
├── pbix/
│   └── Marketing_Ecommerce_Dashboard.pbix
├── dax/
│   └── measures.md          # documented DAX formulas + bug fixes
└── docs/
    └── insights_summary.md  # per-page insights and recommendations
```

---

## 🛠️ Tech Stack
**Power BI Desktop** (data modeling + visuals) · **Power Query** (ETL/cleaning) · **DAX** (KPI measures)

---

## 📜 License
MIT License — free to fork, adapt, and build on.

---

## 🙋 Author
**Yash Kesarwani** — Data Analytics Dashboard Project, April 2026
