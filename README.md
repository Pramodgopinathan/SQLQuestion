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

insert into PRODUCT values (1111,'col1','col2',70000);
insert into PRODUCT values (1112,'col2','col3',65000);
insert into PRODUCT values (1113,'col3','col4',65000);
insert into PRODUCT values (1114,'col4','col5',85000);
insert into PRODUCT values (1115,'col5','col6',95000);

select * from PRODUCT;
