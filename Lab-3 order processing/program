create database Order_processing;
use Order_processing;
CREATE TABLE CUSTOMER
(
 cust_no int,
 cname VARCHAR(15),
 city VARCHAR(15),
 PRIMARY KEY(cust_no)
); 
CREATE TABLE ORDERS(
 order_no int,
 odate date,
 cust_no int,
 foreign key(cust_no) references CUSTOMER(cust_no) on delete cascade,
 ord_Amt int,
 primary key(order_no)
 ); 
 create table ITEM (
 item_no int,
 unit_price int,
 primary key(item_no)
 );
create table ORDER_ITEM (
order_no int,
item_no int, 
qty int,
foreign key(order_no) references ORDERS(order_no) on delete cascade,
foreign key(item_no) references ITEM(item_no) on delete SET NULL
);
create table WAREHOUSE(
warehouseno int, 
city varchar(30),
primary key(warehouseno)
);
create table SHIPMENT(
order_no int,
warehouseno int,
ship_date date,
foreign key(order_no) references ORDERS(order_no) on delete cascade,
foreign key(warehouseno) references WAREHOUSE(warehouseno) on delete cascade
);
insert into CUSTOMER(cust_no,cname,city)values(771,'PUSHPA K','BANGALORE');
insert into CUSTOMER(cust_no,cname,city)values(772,'SUMAN','MUMBAI');
insert into CUSTOMER(cust_no,cname,city)values(773,'SOURAV','CALICUT');
insert into CUSTOMER(cust_no,cname,city)values(774,'LAILA','HYDERABAD');
insert into CUSTOMER(cust_no,cname,city)values(775,'FAIZAL','BANGALORE');
COMMIT;
desc CUSTOMER;
SELECT *FROM CUSTOMER;
insert into ORDERS(order_no,odate,cust_no,ord_Amt)values(111,'22-01-02',771,18000);
insert into ORDERS(order_no,odate,cust_no,ord_Amt)values(112,'30-07-02',774,6000);
insert into ORDERS(order_no,odate,cust_no,ord_Amt)values(113,'03-04-03',775,9000);
insert into ORDERS(order_no,odate,cust_no,ord_Amt)values(114,'03-11-03',775,29000);
insert into ORDERS(order_no,odate,cust_no,ord_Amt)values(115,'10-12-03',773,29000);
insert into ORDERS(order_no,odate,cust_no,ord_Amt)values(116,'19-08-04',772,56000);
insert into ORDERS(order_no,odate,cust_no,ord_Amt)values(117,'10-09-04',771,20000);
insert into ORDERS(order_no,odate,cust_no,ord_Amt)values(118,'20-11-04',775,29000);
insert into ORDERS(order_no,odate,cust_no,ord_Amt)values(119,'13-02-05',774,29000);
insert into ORDERS(order_no,odate,cust_no,ord_Amt)values(120,'13-10-05',775,29000);
COMMIT;
desc ORDERS;
SELECT *FROM ORDERS;
insert into ITEM(item_no,unit_price)values(5001,503);
insert into ITEM(item_no,unit_price)values(5002,750);
insert into ITEM(item_no,unit_price)values(5003,150);
insert into ITEM(item_no,unit_price)values(5004,600);
insert into ITEM(item_no,unit_price)values(5005,890);
COMMIT;
desc ITEM;
SELECT *FROM ITEM;
insert into ORDER_ITEM(order_no,item_no,qty)values(111,5001,50);
insert into ORDER_ITEM(order_no,item_no,qty)values(112,5003,20);
insert into ORDER_ITEM(order_no,item_no,qty)values(113,5002,50);
insert into ORDER_ITEM(order_no,item_no,qty)values(114,5005,60);
insert into ORDER_ITEM(order_no,item_no,qty)values(115,5004,90);
insert into ORDER_ITEM(order_no,item_no,qty)values(116,5001,10);
insert into ORDER_ITEM(order_no,item_no,qty)values(117,5003,80);
insert into ORDER_ITEM(order_no,item_no,qty)values(118,5005,50);
insert into ORDER_ITEM(order_no,item_no,qty)values(119,5002,10);
insert into ORDER_ITEM(order_no,item_no,qty)values(120,5004,45);
COMMIT;
desc ORDER_ITEM;
SELECT *FROM ORDER_ITEM;
insert into WAREHOUSE(warehouseno,city)values(1,'DELHI');
insert into WAREHOUSE(warehouseno,city)values(2,'BOMBAY');
insert into WAREHOUSE(warehouseno,city)values(3,'CHENNAI');
insert into WAREHOUSE(warehouseno,city)values(4,'BANGALORE');
insert into WAREHOUSE(warehouseno,city)values(5,'BANGALORE');
insert into WAREHOUSE(warehouseno,city)values(6,'DELHI');
insert into WAREHOUSE(warehouseno,city)values(7,'BOMBAY');
insert into WAREHOUSE(warehouseno,city)values(8,'CHENNAI');
insert into WAREHOUSE(warehouseno,city)values(9,'DELHI');
insert into WAREHOUSE(warehouseno,city)values(10,'BANGALORE');
COMMIT;
desc WAREHOUSE;
SELECT *FROM WAREHOUSE;
insert into SHIPMENT(order_no,warehouseno,ship_date)values(111,1,'10-02-02');
insert into SHIPMENT(order_no,warehouseno,ship_date)values(112,5,'10-09-02');
insert into SHIPMENT(order_no,warehouseno,ship_date)values(113,8,'10-02-03');
insert into SHIPMENT(order_no,warehouseno,ship_date)values(114,3,'10-12-03');
insert into SHIPMENT(order_no,warehouseno,ship_date)values(115,9,'19-01-04');
insert into SHIPMENT(order_no,warehouseno,ship_date)values(116,1,'20-09-04');
insert into SHIPMENT(order_no,warehouseno,ship_date)values(117,5,'10-09-04');
insert into SHIPMENT(order_no,warehouseno,ship_date)values(118,7,'30-11-04');
insert into SHIPMENT(order_no,warehouseno,ship_date)values(119,7,'30-04-05');
insert into SHIPMENT(order_no,warehouseno,ship_date)values(120,6,'21-12-05');
COMMIT;
desc SHIPMENT;
SELECT *FROM SHIPMENT;
/*Produce a listing: CUSTNAME, #oforders, AVG_ORDER_AMT, where the middle column
is the total numbers of orders by the customer and the last column is the average order amount for that customer.*/
SELECT C.CNAME as CUSTNAME, COUNT(*) as no_of_orders,AVG(O.ord_Amt) as AVG_ORDER_AMT FROM CUSTOMER C, ORDERS O WHERE C.cust_no=O.cust_no GROUP BY C.CNAME;
/*List the order# for orders that were shipped from all warehouses that the company has in a specific city.*/
SELECT order_no FROM WAREHOUSE W, SHIPMENT S WHERE W.warehouseno=S.warehouseno AND CITY='BANGALORE';
/*Demonstrate how you delete item# 10 from the ITEM table and make that field null in the ORDER_ITEM table.*/
delete from ITEM where item_no=5005;
select *from ITEM;
select *from ORDER_ITEM;
