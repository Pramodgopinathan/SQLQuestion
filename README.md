# SQL Question 

## Create Table
### Create the following 3 tables for an online store. The primary keys are underlined, and the foreign keys are shown in italic. You can personalize the tables if needed to be fit to store the information you need for the products you sell on your website.
 
PRODUCT(ProductID, PName, PDescription, Price) – this table records information about each product. <br/>
SALE(SaleID, DeliveryAddress, CreditCard) – this table records information about each sale/transaction. <br/>
SALEITEM(SaleID, ProductID, Quantity) – this table records information about which products were sold in each sale/transaction

``` SQL
create table PRODUCT (
	ProductID number default 0,
	PName varchar2(50) not null,
	Price_Rs number default 0,
	constraint pk_product primary key (ProductID)
);

create table SALE (
	SaleID number default 0,
	DeliveryAddress varchar2(100) not null,
	constraint pk_sale primary key (SaleID)
);


create table SALEITEM (
	SaleID number default 0,
	ProductID number default 0,
	Quantity number,

	constraint fk_sale foreign key (SaleID)
		references SALE (SaleID),
	constraint fk_product foreign key (ProductID)
		references PRODUCT (ProductID)
);
 
```

### Insert 5 records in each table.

``` SQL

insert into PRODUCT values (1111,'col1','col2',70000);
insert into PRODUCT values (1112,'col2','col3',65000);
insert into PRODUCT values (1113,'col3','col4',65000);
insert into PRODUCT values (1114,'col4','col5',85000);
insert into PRODUCT values (1115,'col5','col6',95000);

insert into SALE values (1, 'test', 2323);
insert into SALE values (2, 'test1', 23231);
insert into SALE values (3, 'test2', 23232);
insert into SALE values (4, 'test3', 23233);
insert into SALE values (5, 'test4', 23234);

insert into SALEITEM values (200201, 1000201, 10);
insert into SALEITEM values (200202, 1000211, 11);
insert into SALEITEM values (200203, 1000221, 12);
insert into SALEITEM values (200204, 1000231, 13);
insert into SALEITEM values (200205, 1000241, 14);

``` 
### List all records from the PRODUCT, SALE and SALEITEM table.

``` SQL
select * from PRODUCT;
select * from SALE;
select * from SALEITEM;

```

### Update the price of one of your products in the PRODUCT table to cost Rs.100 more than original price.

``` SQL
UPDATE PRODUCT
	SET Prices_Rs = Prices_Rs + 100
	WHERE ProductID = 1111;
	
```
### Delete all products with price higher than 10,000 from your PRODUCT table. 
(Hint: You can insert such a product first and then use this command to delete it for testing purposes)

``` SQL
ALTER TABLE SALEITEM
DROP COSTRAINT fk_product;

DELET FROM PRODUCT WHERE Price_RS >= 10000;
```
### UNION
The UNION operator is used to combine the result-set of two or more SELECT statements.
### UNION ALL
The UNION operator is used to combine the result-set of two or more SELECT statements with duplicated
### MINUS
The SQL MINUS operator is used to return all rows in the first SELECT statement that are not returned by the second SELECT statement. Each SELECT statement will define a dataset. The MINUS operator will retrieve all records from the first dataset and then remove from the results all records from the second dataset.
### INTERSECT
The SQL INTERSECT operator is used to return the results of 2 or more SELECT statements. However, it only returns the rows selected by all queries or data sets. If a record exists in one query and not in the other, it will be omitted from the INTERSECT results.

``` SQL

Create table FIRST (
	ID number,
	Name varchar2(50)
);

Create table SECOND (
	ID number,
	Name varchar2(50)
);

Select * from FIRST
Union OR Union All OR Minus OR INTERSECT
Select * from Second;

```
