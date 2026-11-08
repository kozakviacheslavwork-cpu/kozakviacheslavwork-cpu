# Methodology & Quality Assurance

## Source and population

- User's educational Google Sheets workbook, imported from the attached XLSX snapshot.
- Clean transaction rows: 19803 with recognized order statuses.
- **Approved:** 19625; **Cancelled:** 178; timeframe: 2017.
- Regional aggregation: join of approved transaction customer IDs to XLSX-exported address records; state names standardized to NSW, VIC and QLD. Unmatched IDs are **Unmapped**.

## Metrics

| KPI | Implementation |
|---|---|
| Approved orders | `COUNTIF(status, "Approved")` |
| List-price sales | `SUMIFS(list_price, status, "Approved")` |
| Profit proxy | `SUMIFS(profit, status, "Approved")`; source `profit = list_price - standard_cost` |
| Margin | `profit_proxy / list_price_sales` |
| Distinct customers | `COUNTUNIQUE(FILTER(customer_id, status="Approved"))` |
| Average order value | `list_price_sales / approved_orders` |
| Monthly / brand / category | Additional `COUNTIFS` and `SUMIFS` criteria |
| Channels | Boolean TRUE/FALSE, or literal `UNKOWN` mapped to Unknown |

## Audit

- Monthly, channel, and product-line totals reconcile to overall approved KPIs.
- Regional snapshot approved orders and list-price sales reconcile to the all-brand approved total.
- Native dashboard calculation integrity is checked in **Portfolio Metrics!A57:B64**; status **PASS** under All brands.
- Changing the brand dropdown to Solex and back was tested; all-brand values restored.

## Important qualifications

1. **List price ≠ settled sales revenue.** The source does not document discounts, payment adjustments, returns, shipping or tax.
2. **Profit proxy ≠ net profit.** Indirect expenses and taxes are not subtracted.
3. **Regional numbers are static.** The live source's external address import is blocked without Google Sheets URL authorization, so the published aggregate comes from an audited XLSX address-table snapshot.
4. **No source PII is published.** The raw training workbook and customer names/addresses are intentionally not in this repository.
5. **Attribution:** based on guided course practice; new analyses and dashboard are original additions.
