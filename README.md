# Inventory Management Database & EDA Pipeline

A robust Python and SQLite pipeline designed for ingesting, cleaning, and performing exploratory data analysis on large-scale retail inventory and transactional datasets.

## Project Architecture


├── data/                       # Raw CSV data files (purchases, sales, invoices)
├── ingestion_db.py             # Bulk CSV-to-SQLite loading script
├── get_vendor_summary.py       # Data integration and financial metric pipeline
└── inventory.db                # SQLite database repository





#Database Schema & Core Tables
purchases: Records transaction logs for purchase orders, supplier IDs, unit volumes, and purchase pricing (spanning over 2.37M rows).

purchase_prices: Maintains product-level pricing benchmarks, standard purchase costs, and actual retail prices.

vendor_invoice: Captures invoice-level data including quantities, transaction dollars, and associated freight expenses.

sales: Granular daily store-level transaction records detailing store locations, brand descriptions, units sold, revenue, and excise taxes (exceeding 12.8M rows).

begin_inventory & end_inventory: Year-opening and year-closing physical inventory counts segmented by store and brand.






Key Financial & Operational Metrics
The processing script aggregates operational data to compute critical key performance indicators (KPIs) per vendor:

Gross Profit: Total Sales Dollars - Total Purchase Dollars

Profit Margin (%): (Gross Profit / Total Sales Dollars) * 100

Stock Turnover: Total Sales Quantity / Total Purchase Quantity

Sales-to-Purchase Ratio: Total Sales Dollars / Total Purchase Dollars

Installation & Execution
1. Prerequisites
Ensure Python 3.11 or higher is installed, along with the required dependencies:

pip install pandas sqlalchemy

2. Execution Steps
Step 1: Ingest Raw Data into SQLite


python ingestion_db.py
Step 2: Generate Aggregated Vendor Summaries
python get_vendor_summary.py
