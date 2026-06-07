# Relational Commerce Schema Reference

### 1. Table: `inventory_logs`
Tracks individual SKU stock parameters and unit valuations.
* `item_id` (INT, PRIMARY KEY): Unique identifier for each product.
* `item_name` (VARCHAR): Name/Description of the product (e.g., Luxury Journal, Calligraphy Set).
* `stock_count` (INT): Active physical pieces available in inventory.
* `unit_price` (DECIMAL): Base sale price per individual unit in INR.

### 2. Table: `customer_orders`
Tracks transaction telemetry across customer activation cycles.
* `order_id` (INT, PRIMARY KEY): Unique identifier for each transaction milestone.
* `customer_id` (VARCHAR): Masked unique identifier for individual consumers.
* `purchase_date` (TIMESTAMP): Date and time execution log of the transaction.
* `item_id` (INT, FOREIGN KEY): Maps back directly to `inventory_logs`.
* `quantity` (INT): Total volume of items ordered in a single transaction sequence.
* `order_status` (VARCHAR): Current operational status (`'Completed'`, `'Pending'`, `'Refunded'`).
