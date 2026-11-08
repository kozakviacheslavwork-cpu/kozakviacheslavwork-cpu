# Retail Sales Performance & Customer Insights

**Google Sheets · Retail Analytics · KPI Reporting · Data Quality · Interactive Dashboard**

An extended portfolio case study based on a guided Google Sheets course by Nikita Tymoshenko. I independently audited the calculations, corrected transaction-count logic, excluded cancelled orders, added a dynamic brand filter, built five dashboard charts and documented all metric assumptions.

> **Educational dataset:** Australian bicycle retail transactions, January–December 2017. Financial figures are proxies derived from source prices and standard costs, **not** audited company revenue or net profit.

![Sales trend](assets/monthly_sales_trend.svg)

## Business questions

- What are the list-price sales, profit proxy, average order value and customer count for **approved** transactions?
- Which months, brands and product lines lead on performance?
- How balanced are online versus in-store transactions?
- Which Australian states account for the highest value, with unknown records explicitly tracked?
- Can dashboard numbers be reconciled with the underlying data?

## Headline KPIs

| Metric | Approved transactions only |
|---|---:|
| Approved orders | **19,625** |
| Cancelled orders excluded | **178** |
| List-price sales proxy | **$21,739,495.00** |
| Profit proxy (price minus standard cost) | **$10,831,504.00** |
| Profit-proxy margin | **49.82%** |
| Unique purchasing customer IDs | **3,493** |
| Average transaction value | **$1,108.00** |

**Key findings:** Solex leads by list-price sales; WeareA2B leads by profit proxy. Oct has the highest monthly sales in 2017, while Sep has the lowest. 352 approved transactions have an unknown sales channel.

## Google Sheets implementation

The private working workbook includes **Portfolio Dashboard**, **Portfolio Metrics**, and **Project Notes** as the portfolio deliverable. It features five KPI tiles, five charts, a brand dropdown, formula-backed summaries and a reconciliation block returning **PASS**.

The **brand filter** changes key KPIs, the monthly trend, channel mix and product-line performance. The brand comparison and regional snapshot intentionally stay **all-brand benchmarks**.

The interactive workbook is currently **private**. A public view link should be added only after reviewing the legacy source tabs and their customer/address columns.

## Files

- `data/kpi_snapshot.csv` — metric definitions and audited top-line values
- `data/monthly_performance.csv` — approved monthly metrics
- `data/brand_performance.csv` — brand orders, sales and profit proxy
- `data/channel_performance.csv` — online, in-store, unknown mix
- `data/product_line_performance.csv` — product category breakdown
- `data/regional_performance_snapshot.csv` — **static** regional breakdown
- `assets/monthly_sales_trend.svg` — chart derived from audited aggregates
- `METHODOLOGY.md` — definitions, quality checks and limitations

**Privacy:** Only aggregate CSVs are published. Customer names, street addresses, and raw records are excluded.

## Audit and limitations

- There were **178 cancelled transactions** that should not be included in completed-sale totals.
- Transaction count is a **COUNT**, never `SUM(transaction_id)`.
- The source contains the misspelled channel category `UNKOWN`; it is shown as **Unknown**, rather than silently treated as online/offline.
- Source `Address_clean` uses an external Google Sheets `IMPORTDATA` connection that may show `#REF!` without explicit permission. Regional figures are therefore a **verified static snapshot** from the user's downloaded XLSX export, joined by customer ID; 87 transactions remain unmapped.
- `list_price` is not verified settled revenue and `list_price - standard_cost` is not full accounting net profit.
- Only 2017 is included; no multi-year trend can be inferred.

## Skills

Google Sheets · SUMIFS · COUNTIFS · COUNTUNIQUE · data cleaning · Excel · data quality · KPI definitions · business analytics · dashboarding.

## Credits

- [Nikita Tymoshenko — Google Sheets Data Analytics tutorial](https://youtu.be/gYjQRW6N6Ws)
- [Source materials referenced in the original workbook](https://github.com/Youtube-NikitaTymoshenko/googleSheets-course)

The tutorial and initial dataset belong to their respective authors. The data audit, approved-only metric policy, filter and visual redesign, reconciliation and reporting structure are independent extensions.
