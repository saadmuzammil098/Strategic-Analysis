# Best Market Strategy Analysis

A single Jupyter notebook that runs an A/B test comparison between a "control" and a "test" marketing campaign (`control_group.csv` / `test_group.csv`), analyzing ad spend, impressions, reach, clicks, searches, content views, cart adds, and purchases to determine which campaign strategy performs better.

## Tech stack

- Python
- pandas
- Plotly (`plotly.express`, `plotly.graph_objects`) with OLS trendlines for scatter plots and pie/bar charts

## Architecture

```mermaid
flowchart LR
    A["control_group.csv"] --> C["Rename columns to common schema"]
    B["test_group.csv"] --> C
    C --> D["Fill missing numeric values\nwith column mean (control set)"]
    D --> E["Merge control + test data\n(sorted by Date)"]
    E --> F["Scatter plots w/ OLS trend:\nImpressions vs Spend,\nContent Viewed vs Clicks,\nAdded to Cart vs Content Viewed,\nPurchases vs Added to Cart"]
    E --> G["Pie charts:\nControl vs Test totals\n(Searches, Clicks, Content Viewed,\nCart Adds, Spend, Purchases)"]
    F --> H["Conclusion:\nControl drove more overall sales;\nTest had a higher cart-to-purchase\nconversion rate for targeted audiences"]
    G --> H
```

## Setup / How to run

The repo contains only the notebook, `Best Market Strategy Analysis.ipynb`; the source CSVs (`control_group.csv`, `test_group.csv`, semicolon-delimited) are not included in the repository and must be supplied separately to reproduce the analysis.

1. Install dependencies: `pip install pandas plotly statsmodels` (statsmodels is required for the OLS trendlines used by Plotly)
2. Place `control_group.csv` and `test_group.csv` in the same directory as the notebook.
3. Open and run `Best Market Strategy Analysis.ipynb` in Jupyter.
