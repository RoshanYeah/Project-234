WITH query_1 AS (select
customers.last_name AS customer_last_name,
customers.phone AS customer_phone,
company_orders.id AS order_id 
FROM customers
INNER JOIN 
company_orders 
ON customers.id = company_orders.customer_id),
query_2 AS (select 
order_items.order_id, 
company_products.name AS product_name, 
suppliers.contact_name AS supplier_name FROM order_items
INNER JOIN 
company_products 
ON company_products.id = order_items.product_id
INNER JOIN 
suppliers 
ON suppliers.id = company_products.supplier_id)
SELECT DISTINCT
query_1.customer_last_name, query_1.customer_phone,
query_2.product_name, query_2.supplier_name
FROM query_1 INNER JOIN query_2 ON query_1.order_id = query_2.order_id
![image](https://github.com/RoshanYeah/Project-234/assets/98729871/ae8d9180-873b-461f-b822-14eb033ab9a2)
