## SAP Vora - SAP HANA Integration

### Prerequisites
For the SAP Vora - SAP HANA Integration scenario, we will use SHINE (SAP HANA Interactive Education) which is a demo content for native SAP HANA application development. SHINE will be used for providing SAP HANA Tables with Master Data.


### SAP HANA System Setup
1. Setup a [SAP HANA Express Edition](https://www.sap.com/developer/topics/sap-hana-express.html) or get access to a SAP HANA Platform Edition system
2. Download and install SHINE(SAP HANA Interactive Education) for XSC in your HANA system. SHINE for XSC can be downloaded from [github](https://github.com/SAP/hana-shine/blob/master/HCO_DEMOCONTENT_200.tgz?raw=true) . Please note that a file with name HCO_DEMOCONTENT_200.tgz will get downloaded
3. Follow the steps in Chapter 2.2 of [SHINE installation guide](https://help.sap.com/doc/bf0ee2761d9240b984425545869eac80/2.0.01/en-US/SAP_HANA_Interactive_Education_SHINE_en_HANA2.0SPS01.pdf) to install SHINE for XSC
4. Note down the SAP HANA System host ipaddress, instance Nnmber, HANA User Name, HANA User Password and tenantdatabase


### Queries
Query 1
- Create virtual table PRODUCTS in Vora from the HANA table sap.hana.democontent.epm.data::MD.Products under the Schema "SAP_HANA_DEMO".Other SAP HANA connectivuty details like , host, instance number, HANA User Name and HANA User Password also must be provided to facilitate the connection.
     
   ```sql
    CREATE TABLE SHINE_PRODUCTS
    USING com.sap.spark.hana
    OPTIONS (
    path "sap.hana.democontent.epm.data::MD.Products",
    dbschema "SAP_HANA_DEMO",
    host "<host ipaddress>",
    instance "<instance number>",
    user "<HANA User Name>",
    passwd "<HANA User Password>",
    tenantdatabase "<dbname>"
    )
      
   ```

Query 2
- Create view ORDER_ITEM_DETAILS that has all the details of the every product sold in an order.
      
   ```sql
    CREATE VIEW ORDER_ITEM_DETAILS AS
    SELECT SO_HEADER.SALESORDERID , CREATEDAT , CATEGORY , SO_ITEM.PRODUCTID , QUANTITY  
    FROM  SO_HEADER
  	INNER JOIN SO_ITEM 
    ON SO_HEADER.SALESORDERID = SO_ITEM.SALESORDERID 
  	INNER JOIN SHINE_PRODUCTS 
  	ON SO_ITEM.PRODUCTID = SHINE_PRODUCTS.PRODUCTID
   	ORDER BY SALESORDERID
   USING com.sap.spark.view
      
   ```

Query 3
- Visualise how many products are sold in each category.
      
   ```sql
    SELECT * FROM ORDER_ITEM_DETAILS 
   ```
