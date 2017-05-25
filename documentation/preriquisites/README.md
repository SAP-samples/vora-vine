## Queries

Query 1 to 4 
- Creating the necessary tables.

    ```sql
    CREATE TABLE ADDRESSES (ADDRESSID string, CITY string, POSTALCODE string, STREET string, BUILDING string, COUNTRY string, REGION string, ADDRESSTYPE string, STARTDATE date, ENDDATE date, LATITUDE string, LONGITUD string)
    USING com.sap.spark.vora
    OPTIONS (tableName "ADDRESSES",
    files "/user/vora/addresses.parquet")
    
    CREATE TABLE BUSINESS_PARTNER (PARTNERID string, PARTNERROLE string, EMAILADDRESS string, PHONENUMBER string, FAXNUMBER string, WEBADDRESS string, ADDRESSID string, COMPANYNAME string, LEGALFORM string, CREATEDBY_EMPLOYEEID string, CREATEDAT date, CHANGEDBY_EMPLOYEEID string, CHANGEDAT date, CURRENCY string)
    USING com.sap.spark.vora
    OPTIONS (tableName "BUSINESS_PARTNER",
    files "/user/vora/businessPartner.orc")
    
    CREATE TABLE SO_HEADER (SALESORDERID string, CREATEDBY_EMPLOYEEID string, CREATEDAT date, CHANGEDBY_EMPLOYEEID string, CHANGEDAT date, NOTEID string, PARTNERID string, CURRENCY string, GROSSAMOUNT decimal(15,2), NETAMOUNT decimal(15,2), TAXAMOUNT decimal(15,2), LIFECYCLESTATUS string, BILLINGSTATUS string, DELIVERYSTATUS string) 
    USING com.sap.spark.engines.relational
    OPTIONS (tableName "SO_HEADER",
    files "/user/vora/soHeaderData.csv")
    
    CREATE TABLE SO_ITEM (SALESORDERID string, SALESORDERITEM string, PRODUCTID string, NOTEID string,  CURRENCY string, GROSSAMOUNT decimal(15,2), NETAMOUNT decimal(15,2), TAXAMOUNT decimal(15,2), ITEMATPSTATUS string, OPITEMPOS string, QUANTITY decimal(15,2), QUANTITYUNIT string, DELIVERYDATE date  ) 
    USING com.sap.spark.engines.relational
    OPTIONS (tableName "SO_ITEM",
    files "/user/vora/soItemData.csv")

    ```

Query 5
- Create view, ORDER_COUNT to get the number of items sold for each order

    ```sql
    CREATE VIEW ORDER_COUNT
    AS SELECT SALESORDERID , COUNT(SALESORDERITEM) AS NOOFITEMS  
    FROM  SO_ITEM 
    GROUP BY SALESORDERID
    USING com.sap.spark.view
    ```

Query 6
- Create view, ORDER_DETAILS to get the important details of each order like details of the Business Partner (Customer), Address associated to the order, No. of items & Gross Amount per order, when the order was created, etc.

    ```sql
    CREATE VIEW ORDER_DETAILS
    AS SELECT ORDER_COUNT.SALESORDERID , NOOFITEMS , SO_HEADER.CREATEDAT , SO_HEADER.PARTNERID , SO_HEADER.GROSSAMOUNT , COMPANYNAME ,       CITY , STREET , BUILDING , COUNTRY , REGION , LATITUDE , LONGITUD  
    FROM  ADDRESSES
          INNER JOIN BUSINESS_PARTNER 
          ON ADDRESSES.ADDRESSID = BUSINESS_PARTNER.ADDRESSID
          INNER JOIN SO_HEADER
          ON SO_HEADER.PARTNERID = BUSINESS_PARTNER.PARTNERID
          INNER JOIN ORDER_COUNT
          ON ORDER_COUNT.SALESORDERID = SO_HEADER.SALESORDERID
    ORDER BY SO_HEADER.CREATEDAT
    Using com.sap.spark.view

    ```

