# Olist_Project

```sql
CREATE OR REPLACE TABLE `iron-foundry-431315-d7.olist_project.olist_order_review_pay` AS
SELECT
    o.*,
    r.review_score,
    p.payment_sequential,
    p.payment_type,
    p.payment_installments,
    p.payment_value,
FROM 
    `iron-foundry-431315-d7.olist_project.olist_orders_dataset` o
LEFT JOIN 
    `iron-foundry-431315-d7.olist_project.olist_order_reviews_dataset` r
    USING(order_id) 
LEFT JOIN
    `iron-foundry-431315-d7.olist_project.olist_order_payments_dataset` p 
    USING(order_id) 



CREATE OR REPLACE TABLE `iron-foundry-431315-d7.olist_project.olist_items_product_sellers` AS
SELECT
    i.*,
    c.string_field_1,
    s.seller_city,
    s.seller_state,
    s.seller_zip_code_prefix
FROM 
    `iron-foundry-431315-d7.olist_project.olist_order_items_dataset` i
LEFT JOIN 
    `iron-foundry-431315-d7.olist_project.olist_products_dataset` p
    USING(product_id) 
LEFT JOIN
    `iron-foundry-431315-d7.olist_project.product_category_name_translation` c 
    ON 	product_category_name = string_field_0
LEFT JOIN
    `iron-foundry-431315-d7.olist_project.olist_sellers_dataset` s
    USING(seller_id) 


```
