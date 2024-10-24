# Olist_Project

```sql
CREATE TABLE `iron-foundry-431315-d7.olist_project.olist_customers_analysis` AS
SELECT 
    customers.customer_id,
    customers.customer_unique_id,
    orders.order_id,
    orders.order_status,
    orders.order_purchase_timestamp,
    SUM(items.price) AS total_spent,
    COUNT(orders.order_id) AS total_orders
FROM
    `iron-foundry-431315-d7.olist_project.olist_customers_dataset` AS customers
JOIN
    `iron-foundry-431315-d7.olist_project.olist_orders_dataset` AS orders
    USING(customer_id)
JOIN
    `iron-foundry-431315-d7.olist_project.olist_order_items_dataset` AS items
    USING(order_id) 
GROUP BY
    customers.customer_id, customers.customer_unique_id, orders.order_id, orders.order_status, orders.order_purchase_timestamp
```
