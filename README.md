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




CREATE TABLE `iron-foundry-431315-d7.olist_project.olist_product_analysis` AS
SELECT
    products.product_id,
    products.product_category_name,
    translation.string_field_1 AS product_category_name_english,
    SUM(items.price) AS total_revenue,
    COUNT(items.order_item_id) AS total_items_sold
FROM
    `iron-foundry-431315-d7.olist_project.olist_order_items_dataset` AS items
JOIN
    `iron-foundry-431315-d7.olist_project.olist_products_dataset` AS products
    USING(product_id)
JOIN
    `iron-foundry-431315-d7.olist_project.product_category_name_translation` AS translation
    ON product_category_name=string_field_0
GROUP BY
    products.product_id, products.product_category_name, product_category_name_english



CREATE TABLE `iron-foundry-431315-d7.olist_project.olist_logistics_analysis` AS
SELECT 
    orders.order_id,
    orders.order_purchase_timestamp,
    orders.order_delivered_customer_date,
    orders.order_estimated_delivery_date,
    TIMESTAMP_DIFF(orders.order_delivered_customer_date, orders.order_purchase_timestamp, DAY) AS delivery_time,
    review.review_score,
    SUM(items.price) AS total_order_value
FROM
    `iron-foundry-431315-d7.olist_project.olist_orders_dataset` AS orders
JOIN
    `iron-foundry-431315-d7.olist_project.olist_order_reviews_dataset` AS review
    USING(order_id)
JOIN
    `iron-foundry-431315-d7.olist_project.olist_order_items_dataset` AS items
    USING(order_id)
GROUP BY
    orders.order_id, orders.order_purchase_timestamp, orders.order_delivered_customer_date, orders.order_estimated_delivery_date, review.review_score
```
