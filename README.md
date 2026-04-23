[README.md](https://github.com/user-attachments/files/26991384/README.md)
# 📊 Order Intelligence — Analytics Dashboard

A single-file, client-side analytics dashboard for visualizing e-commerce order data. Upload your CSV datasets and get a fully interactive dashboard rendered instantly in the browser — no backend, no server, no setup.

![HTML](https://img.shields.io/badge/HTML-single--file-c8ff57?style=flat-square&labelColor=0a0a0f)
![Chart.js](https://img.shields.io/badge/Chart.js-4.4.1-7b61ff?style=flat-square&labelColor=0a0a0f)
![PapaParse](https://img.shields.io/badge/PapaParse-5.4.1-ff6b6b?style=flat-square&labelColor=0a0a0f)
![No Backend](https://img.shields.io/badge/backend-none-c8ff57?style=flat-square&labelColor=0a0a0f)

---

## 🖥️ Preview

> Dark editorial aesthetic — lime green accents, DM Mono typography, brutalist grid layout.

**KPI Row**
- Total Revenue · Total Orders · Unique Customers · Avg Order Value · Late Deliveries · On-Time Rate

**Charts & Visualizations**
- Revenue / Orders / Late Deliveries trend line (weekly or monthly)
- Payment method doughnut breakdown
- Top product categories ranked table
- Order status pie chart + summary pills
- Revenue by state (horizontal bar)
- Purchase heatmap — Day × Hour
- Category revenue bar chart

---

## 📁 Required CSV Files

Upload all 5 files on the landing screen. The dashboard auto-joins them in memory.

| # | File | Key Columns |
|---|------|-------------|
| 1 | `orders_rev_df.csv` | `order_id`, `customer_id`, `order_status`, `order_purchase_timestamp`, `order_delivered_timestamp`, `order_estimated_delivery_date` |
| 2 | `df_OrderItems.csv` | `order_id`, `product_id`, `price`, `shipping_charges` |
| 3 | `df_Products.csv` | `product_id`, `product_category_name` |
| 4 | `df_Payments.csv` | `order_id`, `payment_type`, `payment_installments`, `payment_value` |
| 5 | `df_Customers.csv` | `customer_id`, `customer_city`, `customer_state` |

---

## 🚀 How to Use

1. Download or clone this repo
2. Open `index.html` in any modern browser (Chrome, Firefox, Safari, Edge)
3. Upload your 5 CSV files on the landing screen
4. Hit **Launch Dashboard**
5. Use the top bar dropdowns to switch metrics and time granularity

No installation. No dependencies to install. No internet required after the page loads (Chart.js and PapaParse are loaded from CDN on first open).

---

## ⚙️ How It Works

All data processing happens entirely in the browser using JavaScript:

```
CSV files
   ↓ PapaParse
Raw JS arrays
   ↓ Map joins (order_id, product_id, customer_id)
Master dataset (one object per order)
   ↓ Chart.js
Interactive visualizations
```

**Data joins performed:**
- Orders ← Customers (by `customer_id`) → adds `state`, `city`
- Orders ← Order Items (by `order_id`) → adds `revenue`, `categories`
- Orders ← Products (by `product_id`) → adds `category_name`
- Orders ← Payments (by `order_id`) → adds `payment_type`, `payment_value`

**Late delivery detection:** an order is marked late if `order_delivered_timestamp > order_estimated_delivery_date`.

---

## 🛠️ Tech Stack

| Tool | Purpose |
|------|---------|
| Vanilla HTML/CSS/JS | Everything — zero frameworks |
| [Chart.js 4.4.1](https://www.chartjs.org/) | All charts and graphs |
| [PapaParse 5.4.1](https://www.papaparse.com/) | CSV parsing |
| [Google Fonts](https://fonts.google.com/) | Syne + DM Mono typography |

---

## 📐 Design

- **Theme:** Dark (`#0a0a0f` background) with lime green (`#c8ff57`) primary accent
- **Typography:** Syne (headings/values) + DM Mono (labels/numbers)
- **Layout:** CSS Grid, editorial/brutalist style, 1px dividers
- **Responsive:** 3-col KPI grid → 2-col on tablet → 1-col on mobile

---

## 📊 Dataset

This dashboard was built and tested on the **Brazilian E-Commerce Public Dataset by Olist**, available on [Kaggle](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce).

- ~89,000 orders
- 2016–2018 time range
- Multiple sellers and product categories

---

## 📄 License

MIT — free to use, modify, and distribute.
