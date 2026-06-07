# Day 1: Advanced Operational Inventory & Risk Profiling

### Operational Objective
Construct an automated monitoring telemetry to flag stock velocity risk metrics and isolate high-value inventory items based on stock counts, filtering out dormant or depleted stock items.

### Data Schema Reference
* Table Architecture: `inventory_logs`
* Core Columns: `item_id` (INT), `stock_count` (INT), `unit_price` (DECIMAL)

### Production Query
```sql
SELECT 
    item_id, 
    stock_count, 
    unit_price,
    CASE 
        WHEN stock_count < 10 THEN 'Critical Reorder Alert'
        WHEN stock_count BETWEEN 10 AND 30 THEN 'Moderate Monitor'
        ELSE 'Stable Runway'
    END AS risk_profile
FROM 
    inventory_logs
WHERE 
    stock_count > 0
ORDER BY 
    unit_price DESC;
