
## Basic SQL

### Queries

Query 1
- Average order size for each Country.

    ```sql
    SELECT * FROM ORDER_DETAILS
    ```
Query 2
- Create view, TOP_CUSTOMERS_SALES_VOLUME to get the top 5 companies with maximum purchases made.

    ```sql
      CREATE VIEW TOP_CUSTOMERS_SALES_VOLUME AS
      SELECT "VORA"."BUSINESS_PARTNER"."COMPANYNAME" , (sum("VORA"."SO_HEADER"."GROSSAMOUNT")) AS "TOTAL_SALES"  
      FROM  "VORA"."BUSINESS_PARTNER"
	        INNER JOIN "VORA"."SO_HEADER" 
	        ON "VORA"."BUSINESS_PARTNER"."PARTNERID" = "VORA"."SO_HEADER"."PARTNERID" 
      GROUP BY "VORA"."BUSINESS_PARTNER"."COMPANYNAME" 
      ORDER BY "TOTAL_SALES" DESC LIMIT 5;
    ```
    

Query 3
- Display the top 5 companies and their total purchases, in terms of amount. 

    ```sql
      SELECT * FROM TOP_CUSTOMERS_SALES_VOLUME
     ```
