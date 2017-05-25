## Schema
	
- BUSINESS_PARTNER table has details  of  customers , this table has ADDRESSID which is mapped to ADDRESSES table where details of customers address are stored.
		
- When a BUSINESS_PARTNER  buys a product, Sales Order is generated (SO_HEADER) and each sales order has multiple order items (SO_ITEM).

- SO_HEADER has PARTERID , foreign key which links to BUSINESS_PARTNER table.

- SO_ITEM has SALESORDERID, foreign key which links to SO_HEADER.

- Each SO_ITEM will have PRODUCTID which is mapped to PRODUCTS table where details of products are stored.

- So basically we have 5 tables, PRODUCTS table we are accessing from HANA.

- ADDRESS_HIER_INPUT is created using the file address_hierarchy which we have used for hierarchy

![Alt text](./images/image.png "Optional title")

