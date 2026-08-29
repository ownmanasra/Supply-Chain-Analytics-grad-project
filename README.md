# Supply Chain Analytics: Optimizing Inventory Management and Logistics Operations

Graduation project applying supply chain analytics to inventory management and logistics operations. The project generates a synthetic supply chain dataset, performs exploratory data analysis, builds a predictive model for delivery delays, applies K-Means clustering for product segmentation, and conceptualizes Business Intelligence dashboards for supply chain monitoring.

## Overview

Modern supply chains struggle with suboptimal inventory levels and inconsistent delivery performance due to a lack of real-time visibility and predictive capability. This project builds an end-to-end analytical pipeline to address both problems:

- **Descriptive analytics** — exploratory data analysis of delivery performance, revenue by category, and inventory health
- **Predictive analytics** — a Random Forest classifier (with a Logistic Regression baseline) that forecasts delivery delays
- **Prescriptive analytics** — K-Means clustering to segment products into actionable groups (Stars, Reliables, Niche, Risky)
- **Business Intelligence** — dashboard mockups translating the analysis into monitoring tools for executives, logistics managers, and inventory planners

## Tech Stack

- Python 3.10+
- pandas, numpy — data generation and manipulation
- scikit-learn — Random Forest classifier, Logistic Regression, K-Means clustering
- matplotlib, seaborn — visualizations and dashboard mockups

## Project Structure

```
supply-chain-analytics/
├── main.py                    # Runs the full pipeline end-to-end
├── requirements.txt
├── src/
│   ├── data_generation.py     # Synthetic dataset generation (5,000 orders)
│   ├── eda.py                 # Exploratory data analysis & visualizations
│   ├── predictive_modeling.py # Random Forest delivery-delay classifier
│   ├── clustering.py          # K-Means product segmentation
│   └── dashboards.py          # BI dashboard mockups (dark theme)
├── data/                      # Generated dataset (CSV, git-ignored)
└── outputs/                   # Generated figures & dashboards (git-ignored)
```

## Getting Started

```bash
# Clone the repo
git clone https://github.com/<your-username>/supply-chain-analytics.git
cd supply-chain-analytics

# Install dependencies
pip install -r requirements.txt

# Run the full pipeline
python main.py
```

This generates a synthetic dataset in `data/`, and all figures (EDA plots, model results, cluster visualization, dashboards) in `outputs/`.

You can also run each stage independently, e.g.:

```bash
python -m src.data_generation
python -m src.eda
python -m src.predictive_modeling
python -m src.clustering
python -m src.dashboards
```

## Dataset

A synthetic dataset of 5,000 order records is generated, simulating a one-year period across five product categories (Electronics, Fashion, Home & Kitchen, Automotive, Health). Key fields include order details, supplier information, stock levels, reorder points, lead times, shipping costs, and delivery status.

| Variable | Description |
|---|---|
| `OrderID`, `OrderDate` | Order identifier and timestamp |
| `ProductCategory` | Product classification |
| `Quantity`, `UnitPrice`, `TotalRevenue` | Order size and value |
| `Supplier`, `WarehouseLocation` | Sourcing and fulfillment origin |
| `StockLevel`, `ReorderPoint`, `SafetyStock` | Inventory health metrics |
| `LeadTime`, `ShippingCost` | Logistics metrics |
| `DeliveryStatus` | On Time / Delayed / Cancelled (target variable) |

## Predictive Modeling

A Random Forest Classifier predicts whether an order will be delivered **On Time** or **Delayed**, using lead time, shipping cost, quantity, unit price, and stock level as features. Lead time and shipping cost are consistently the strongest predictors. A Logistic Regression model is included as a baseline for comparison.

## Product Segmentation

K-Means clustering (k=4, chosen via the elbow method and silhouette score) groups products by revenue, quantity, and lead time into four segments, each suited to a different inventory and logistics strategy:

- **Stars** — high revenue, high volume: prioritize speed and tight inventory control
- **Reliables** — medium revenue, consistent demand: standard replenishment cycles
- **Niche** — low volume, high lead time: higher safety stock or make-to-order
- **Risky** — high lead time variability: diversified sourcing, contingency buffers

## BI Dashboards

Dashboard mockups (`src/dashboards.py`) conceptualize how these analytics would surface in a production BI tool (Power BI, Tableau, or similar):

- **Executive Overview** — revenue trend, order volume, delivery status breakdown
- **Logistics & Delivery Performance** — daily on-time delivery rate, delay breakdown
- **Inventory & Stockout Analysis** — monthly stockout frequency, stock health

## License

This project is licensed under the MIT License — see [LICENSE](LICENSE) for details.
