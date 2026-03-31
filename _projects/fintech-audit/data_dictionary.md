# Data Dictionary: Trattoria Luigi Digital Transformation

## Table: Fact_Restaurant_KPIs
| Column | Type | Description |
|---|---|---|
| Date | Date | The date of the transaction. |
| DineIn_Revenue | Decimal | Revenue from physical dine-in customers. |
| ThirdParty_Delivery_Revenue | Decimal | Revenue from third-party delivery apps (e.g., UberEats, Lieferando). |
| Direct_Digital_Revenue | Decimal | Revenue from direct digital ordering (WhatsApp, App, Website). |
| Subscription_Revenue | Decimal | Revenue from the "Pasta Club" monthly subscription. |
| Customer_Reach | Integer | Number of unique customers reached (estimated). |
| Operational_Cost | Decimal | Total operational costs (rent, labor, food, delivery commissions). |
| Total_Revenue | Decimal | Sum of all revenue streams. |
| Net_Profit | Decimal | Total Revenue minus Operational Cost. |
| Model | String | Either "Traditional (As-Is)" or "Digital (To-Be)". |

## Key Performance Indicators (KPIs)
- **Customer Acquisition Cost (CAC)**: Cost of marketing divided by new customers.
- **Customer Lifetime Value (CLV)**: Projected revenue from a single customer over their relationship with the restaurant.
- **Table Turnover Rate**: Number of times a table is occupied per shift (improved by online booking).
- **Delivery Margin**: Comparison of profit from third-party delivery vs. direct digital ordering.
