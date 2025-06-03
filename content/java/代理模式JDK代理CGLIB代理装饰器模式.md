- 
- 代理模式
  - JDK代理
  - CGLIB代理

- 装饰器模式

```sql
 WITH query_store_id AS ( SELECT customer_records_sales_data.store_id FROM store_main_info INNER JOIN customer_records_sales_data ON store_main_info.store_id = customer_records_sales_data.store_id WHERE store_main_info.country_region_code IN (?) ), query_sku_id AS ( SELECT sku_id FROM product_main_info WHERE product_main_info.material_group IN (?) ) SELECT distinct p.order_id, p.reason_code, ppto.store_forbidding_sale, ppto.warehouse_forbidding_sale, ppto.store_forbidding_assembly, ppto.warehouse_forbidding_assembly, ppto.store_forbidding_purchase, ppto.warehouse_forbidding_purchase, ppto.creator, ppto.department FROM product_prohibited_interior_order_reason p inner join product_prohibited_interior_order ppto on p.order_id = ppto.record_number inner join query_sku_id k on k.sku_id = p.sku_id inner join query_store_id s on s.store_id = p.store_id AND p.forbid_type IN (?,?)AND p.reason_code = ?AND p.brand_organization = ? LIMIT (? +1) offset (?-1) * ?

Parameters: CN(String), 11010704(String), JS_D(String), JP_D(String), JD05(String), 20(String), 1000(Integer), 1(Integer), 1000(Integer)
```



