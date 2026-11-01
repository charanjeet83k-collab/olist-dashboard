# Olist E-Commerce Dashboard (Streamlit)

Rebuild of `olist_Ecommerce_dashboard_FIXED_v2.pbix`.

## Run
    pip install -r requirements.txt
    streamlit run app.py

## Data
`data/` holds a snapshot of the tables inside the .pbix (orders, order_items, payments, date table).
It is NOT live from SQL Server. To refresh, re-export the SQL views
(vw_analytics_orders, vw_analytics_order_items, vw_clean_order_payments) to parquet with the same columns.

## Known differences from the Power BI file (details in chat)
1. Avg Item Price: Power BI shows 1.00 (DAX bug: Item_Sales / Item_Sales). Here it is Item_Sales / Items_Sold.
2. Date_Table has no relationship in the model. Here it is linked to orders.purchase_date (intended behaviour).
3. "Seller state" slicer does nothing in Power BI (relationship direction). Here it filters order_items.
4. Payment-by-state map is a filled map (state shapes from data/brazil_states.geojson).
