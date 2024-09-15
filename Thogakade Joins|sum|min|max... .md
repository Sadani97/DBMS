DROP DATABASE Thogakade;
CREATE DATABASE Thogakade;
USE Thogakade;

CREATE TABLE Customer(
	CustID VARCHAR(6) NOT NULL,
	CustTitle VARCHAR(5),
	CustName VARCHAR(30) NOT NULL,
	DOB DATE,
	salary decimal(10,2) not null,
	CustAddress VARCHAR(30),
	City VARCHAR(20),
	Province VARCHAR(20),
	PostalCode VARCHAR(9),
	CONSTRAINT PRIMARY KEY (CustID)
);

CREATE TABLE Orders(
	OrderID VARCHAR(6) NOT NULL,
	OrderDate DATE,
	CustID VARCHAR(6) NOT NULL,
	CONSTRAINT PRIMARY KEY (OrderID),
	CONSTRAINT FOREIGN KEY(CustID) REFERENCES Customer(CustID)
);

CREATE TABLE Item(
	ItemCode VARCHAR(6) NOT NULL,
	Description VARCHAR(50) NOT NULL,
	PackSize VARCHAR(20),
	UnitPrice DECIMAL(6,2) NOT NULL,
	QtyOnHand INT(5) NOT NULL,
	CONSTRAINT PRIMARY KEY (ItemCode)
);

CREATE TABLE OrderDetail(
	OrderID VARCHAR(6) NOT NULL,
	ItemCode VARCHAR(6) NOT NULL,
	OrderQTY INT(11) NOT NULL,
	Discount INT(2),
	CONSTRAINT PRIMARY KEY (OrderID,ItemCode),
	CONSTRAINT FOREIGN KEY (OrderID) REFERENCES Orders(OrderID),
	CONSTRAINT FOREIGN KEY (ItemCode) REFERENCES Item(ItemCode)
);


INSERT INTO Customer VALUES('C001','Mr','Danapala','1981-2-6',40000,'No.20 Walana','Panadura','Western',12500);
INSERT INTO Customer VALUES('C002','Mr','Gunapala','1982-8-12',40000,'No 200, Thalpitiya','Wadduwa','Western',12500);
INSERT INTO Customer VALUES('C003','Mr','Amarapala','1988-1-2',34000,'No 100, Horawala','Matugama','Western',13400);
INSERT INTO Customer VALUES('C004','Mr','Somapala','1952-1-2',67000,'No .10, Ginigama','Galle','Southern',12213);
INSERT INTO Customer VALUES('C005','Mr','Jinapala','1974-1-8',32000,'N0. 34 Ginthota','Aluthgama','Southern',24333);
INSERT INTO Customer VALUES('C006','Miss','Gnanawathee','1982-1-3',78000,'No. 230, Galle Road','Panadura','Western',12500);
INSERT INTO Customer VALUES('C007','Miss','Amarawathee','1984-5-7',98000,'No, Galle Road','Ambalangoda','Southern',43343);
INSERT INTO Customer VALUES('C008','Ms','Leelawathee','1950-4-8',57000,'No 12, Rathnapura Road','Madampe','Sabaragamuwa',32312);
INSERT INTO Customer VALUES('C009','Ms','Gunawathee','1972-3-9',76000,'No122, Anuradhapura Road','Kurunegala','Wayamba',23233);
INSERT INTO Customer VALUES('C010','Mr','Dayapala','1983-4-9',40000,'No. 234, Attidiya Road','Dehiwala','Western',23434);
INSERT INTO Customer VALUES('C011','Mr','Sugathapala','1983-4-9',40000,'No. 234, Attidiya Road','Dehiwala','Western',23434);
INSERT INTO Customer VALUES('C012','Mr','Siripala','1983-4-9',40000,'No. 234, Attidiya Road','Dehiwala','Western',23434);




INSERT INTO Orders VALUES('D001','2008-2-5','C001');
INSERT INTO Orders VALUES('D002','2008-2-15','C001');
INSERT INTO Orders VALUES('D003','2008-2-20','C001');
INSERT INTO Orders VALUES('D004','2008-2-28','C001');
INSERT INTO Orders VALUES('D005','2008-3-20','C001');
INSERT INTO Orders VALUES('D006','2008-4-10','C001');
INSERT INTO Orders VALUES('D007','2008-5-10','C001');
INSERT INTO Orders VALUES('D008','2008-6-20','C001');
INSERT INTO Orders VALUES('D009','2008-8-12','C001');
INSERT INTO Orders VALUES('D010','2008-9-20','C001');
INSERT INTO Orders VALUES('D011','2008-2-6','C002');
INSERT INTO Orders VALUES('D012','2008-2-16','C002');
INSERT INTO Orders VALUES('D013','2008-2-20','C002');
INSERT INTO Orders VALUES('D014','2008-3-16','C002');
INSERT INTO Orders VALUES('D015','2008-4-15','C002');
INSERT INTO Orders VALUES('D016','2008-8-26','C002');
INSERT INTO Orders VALUES('D017','2008-2-16','C003');
INSERT INTO Orders VALUES('D018','2008-3-26','C003');
INSERT INTO Orders VALUES('D019','2008-6-11','C003');
INSERT INTO Orders VALUES('D020','2008-9-26','C003');



INSERT INTO OrderDetail VALUES('D001',	'P001',	3,0);
INSERT INTO OrderDetail VALUES('D001',	'P002',	5,0);
INSERT INTO OrderDetail VALUES('D001',	'P003',	8,0);
INSERT INTO OrderDetail VALUES('D001',	'P006',	10,0);
INSERT INTO OrderDetail VALUES('D002',	'P002',	4,0);
INSERT INTO OrderDetail VALUES('D002',	'P003',	4,0);
INSERT INTO OrderDetail VALUES('D002',	'P008',	3,0);
INSERT INTO OrderDetail VALUES('D002',	'P010',	12,0);
INSERT INTO OrderDetail VALUES('D002',	'P012',	3,0);
INSERT INTO OrderDetail VALUES('D003',	'P001',	9,0);
INSERT INTO OrderDetail VALUES('D003',	'P004',	6,0);
INSERT INTO OrderDetail VALUES('D003',	'P016',	70,0);
INSERT INTO OrderDetail VALUES('D004',	'P002',	12,0);
INSERT INTO OrderDetail VALUES('D004',	'P005',	7,0);
INSERT INTO OrderDetail VALUES('D004',	'P008',	10,0);
INSERT INTO OrderDetail VALUES('D004',	'P013',	9,0);
INSERT INTO OrderDetail VALUES('D004',	'P015',	5,0);
INSERT INTO OrderDetail VALUES('D004',	'P016',	8,0);
INSERT INTO OrderDetail VALUES('D004',	'P020',	5,0);
INSERT INTO OrderDetail VALUES('D004',	'P021',	2,0);
INSERT INTO OrderDetail VALUES('D004',	'P022',	3,0);
INSERT INTO OrderDetail VALUES('D005',	'P003',	8,0);


INSERT INTO Item VALUES('P001','Keerisamba Retail','1kg',105.00,3000);
INSERT INTO Item VALUES('P002','Keerisamba 5Kg ','5kg',525.00,200);
INSERT INTO Item VALUES('P003','Keerisamba 10Kg','10kg',995.00,36);
INSERT INTO Item VALUES('P004','Keerisamba 50Kg','50kg',4100.00,36);
INSERT INTO Item VALUES('P005','Red Raw Rice','1kg',60.00,6000);
INSERT INTO Item VALUES('P006','Red Raw Rice 10Kg Pack','10kg',560.00,300);
INSERT INTO Item VALUES('P007','Red Raw Rice 50Kg Pack','50kg',5230.00,80);
INSERT INTO Item VALUES('P008','White Raw Rice 5Kg Pack','5kg',275.00,130);
INSERT INTO Item VALUES('P009','White Raw Rice 50Kg Pack','50kg',2600.00,13);
INSERT INTO Item VALUES('P010','Wattana Dhal 500g','500kg',90.00,83);
INSERT INTO Item VALUES('P011','Wattana Dhal 1Kg','1kg',170.00,40);
INSERT INTO Item VALUES('P012','Mysoor Dhal 500g','500g',90.00,89);
INSERT INTO Item VALUES('P013','Mysoor Dhal 1Kg','1Kg',180.00,59);
INSERT INTO Item VALUES('P014','Orient Green Gram 500g','500g',118.00,39);
INSERT INTO Item VALUES('P015','Orient Green Gram 1Kg','1kg',220.00,12);
INSERT INTO Item VALUES('P016','Anchor F/C Milk powder 450g','450g',220.00,93);
INSERT INTO Item VALUES('P017','Anchor F/C Milk powder 1Kg','1Kg',580.00,40);
INSERT INTO Item VALUES('P018','Anchor N/F Milk powder 1Kg','1Kg',560.00,33);
INSERT INTO Item VALUES('P019','Milo Packet 400g','400g',240.00,33);
INSERT INTO Item VALUES('P020','Lipton Ceylon Tea 100g','100g',107.00,40);
INSERT INTO Item VALUES('P021','Lipton Ceylon Tea 200g','200g',198.00,40);
INSERT INTO Item VALUES('P022','Lipton Ceylon Tea 400g','400g',360.00,20);
INSERT INTO Item VALUES('P023','White Suger 500g','500g',55.00,45);
INSERT INTO Item VALUES('P024','White Suger 1Kg','1kg',109.00,25);
INSERT INTO Item VALUES('P025','Astra Margarine 250g','250g',129.00,25);

SELECT * FROM Customer;
SELECT * FROM Item;
SELECT * FROM Orders;
SELECT * FROM OrderDetail;

SELECT Orders.OrderID, Customer.CustName
FROM Orders
INNER JOIN Customer 
ON Orders.CustID = Customer.CustID;

SELECT Customer.CustID, Customer.CustName, Orders.OrderID
FROM Customer
LEFT JOIN Orders ON Orders.CustID = Customer.CustID;

SELECT Customer.CustID, Customer.CustName, Orders.OrderID
FROM Orders
LEFT JOIN Customer 
ON Orders.CustID = Customer.CustID;
 

SELECT Orders.OrderID, Customer.CustID, Customer.CustName
FROM Orders
RIGHT JOIN Customer 
ON Orders.CustID = Customer.CustID;




SELECT Customer.CustID, Customer.CustName, Orders.OrderID
FROM Customer
LEFT JOIN Orders ON Orders.CustID = Customer.CustID

UNION

SELECT Orders.OrderID, Customer.CustID, Customer.CustName
FROM Orders
RIGHT JOIN Customer ON Orders.CustID = Customer.CustID;


==================================================

SELECT Customer.CustID, Customer.CustName, Orders.OrderID
FROM Customer
LEFT JOIN Orders ON Orders.CustID = Customer.CustID

UNION

SELECT Customer.CustID, Customer.CustName, Orders.OrderID
FROM Orders
RIGHT JOIN Customer ON Orders.CustID = Customer.CustID;


====================================================

SELECT Customer.CustID,Customer.CustName,Orders.OrderID,  Orders.OrderDate
FROM Orders
INNER JOIN Customer 
ON Orders.CustID = Customer.CustID
WHERE Orders.OrderID='D005' AND Customer.CustID='C001';


SELECT Customer.CustID,Customer.CustName,Orders.OrderID,  Orders.OrderDate
FROM Orders
INNER JOIN Customer 
ON Orders.CustID = Customer.CustID
WHERE Customer.CustID='C001' ORDER BY Orders.OrderID DESC;




SELECT Customer.CustID,Customer.CustName,Orders.OrderID,  Orders.OrderDate
FROM Orders
INNER JOIN Customer 
ON Orders.CustID = Customer.CustID
WHERE Customer.CustID='C001' 
ORDER BY Orders.OrderID DESC 
LIMIT 3;

SELECT COUNT(Customer.CustID)
FROM Customer
INNER JOIN  Orders
ON Customer.CustID = Orders.CustID
GROUP BY Customer.CustID;


SELECT Customer.CustID, Customer.CustName, COUNT(Customer.CustID)
FROM Customer 
INNER JOIN Orders 
ON Customer.CustID = Orders.CustID 
GROUP BY Customer.CustID;




SELECT Customer.CustID, Customer.CustName, Orders.OrderID, COUNT(Customer.CustID)
FROM Customer 
INNER JOIN Orders 
ON Customer.CustID = Orders.CustID 
GROUP BY Customer.CustID;




SELECT * FROM OrderDetail;




=======================================

SELECT Customer.CustID, Customer.CustName, Orders.OrderID,Order.OrderDate,OrderDetail.OrderQTY
FROM Customer 
INNER JOIN Orders 
ON Customer.CustID = Orders.CustID 
INNER JOIN OrderDetail
ON Orders.OrderID=OrderDetail.OrderID;


SELECT Customer.CustID, Customer.CustName, Orders.OrderID,Order.OrderDate,OrderDetail.OrderQTY
FROM Customer 
INNER JOIN Orders 
ON Customer.CustID = Orders.CustID 
INNER JOIN OrderDetail
ON Orders.OrderID=OrderDetail.OrderID;



=====================================


Derive SUM (orderQTY) >>> Group by (OrderID) >>  SELECT Customer.CustName,orders.orderID,orders.OrderDate, SUM (orderQTY) >> OrderDetail


SELECT Customer.CustID, Customer.CustName, orders.OrderID,SUM(orderdetail.OrderQTY)
FROM Customer
INNER JOIN Orders
ON Customer.CustID = Orders.CustID
Inner join orderdetail
On orders.OrderID=orderdetail.OrderID
Group BY orders.OrderID;




//          Derive MAX (orderQTY) >>> Group by (OrderID) >>  SELECT 



Customer.CustName,orders.orderID,orders.OrderDate, MAX (orderQTY) >> OrderDetail

SELECT Customer.CustID, Customer.CustName, orders.OrderID,MAX(orderdetail.OrderQTY)
FROM Customer
INNER JOIN Orders
ON Customer.CustID = Orders.CustID
Inner join orderdetail
On orders.OrderID=orderdetail.OrderID
Group BY orders.OrderID;


SELECT Customer.CustID, Customer.CustName, orders.OrderID,MAX(orderdetail.OrderQTY), 
SUM(orderdetail.OrderQTY)
FROM Customer
INNER JOIN Orders
ON Customer.CustID = Orders.CustID
Inner join orderdetail
On orders.OrderID=orderdetail.OrderID
Group BY orders.OrderID;

SELECT Customer.CustID, Customer.CustName, orders.OrderID,COUNT(orderdetail.OrderQTY) 
AS COUNT,MAX(orderdetail.OrderQTY)
AS MAX, MIN(orderdetail.OrderQTY)
AS MIN, AVG(orderdetail.OrderQTY)\
AS AVG, SUM(orderdetail.OrderQTY)
AS SUM
FROM Customer
INNER JOIN Orders
ON Customer.CustID = Orders.CustID
Inner join orderdetail
On orders.OrderID=orderdetail.OrderID
Group BY orders.OrderID;




SELECT VERSION();

SELECT CURDATE();

SELECT YEAR('2019-05-15');

SELECT MONTH('2019-05-15');

SELECT DATE('2019-05-15');

SELECT UCASE('Hello');

SELECT LCASE('HELLO');



SELECT * FROM Customer;

SELECT * FROM Customer WHERE CustName LIKE  '%pala';

SELECT * FROM Customer WHERE CustName LIKE  'S%';

SELECT * FROM Customer WHERE CustName LIKE  '%na%';

SELECT * FROM Customer WHERE CustName LIKE  '_i%';

SELECT * FROM Customer WHERE CustName LIKE  '__r%';


============================================================
having
============================================================

CREATE TABLE CustomerDetails(
	customerId VARCHAR(6) NOT NULL,
	name VARCHAR(30),
	address VARCHAR(30),
	salary FLOAT(10,2),
	CONSTRAINT PRIMARY KEY (customerId)
);

INSERT INTO CustomerDetails VALUES('C001','Danapala','Panadura',54000);

INSERT INTO CustomerDetails VALUES('C002','Gunapala','Matara',44000);

INSERT INTO CustomerDetails VALUES('C003','Somapala','Matara',35000);

INSERT INTO CustomerDetails VALUES('C004','Somapala','Galle',62000);

INSERT INTO CustomerDetails VALUES('C005','Siripala','Galle',87000);

INSERT INTO CustomerDetails VALUES('C006','Sumanapala','Matara',82000);


SELECT * FROM CustomerDetails;


SELECT name,salary FROM CustomerDetails WHERE salary>50000;

SELECT name,salary FROM CustomerDetails HAVING salary>50000;

SELECT name,address FROM CustomerDetails WHERE salary>50000;

//SELECT name,address FROM CustomerDetails HAVING salary>50000;

SELECT name,address,salary FROM CustomerDetails HAVING salary>50000;

(When using HAVING, the mentioning of the relavant field name is mandatory.)

SELECT name,address FROM CustomerDetails WHERE salary>50000;


//      SELECT customerId,name,address,salary,(salary*3/100) AS ETF,(salary-(salary*3/100)) AS NetSalary FROM CustomerDetails WHERE ETF>2000;
(Pre Checking : WHERE always check details from PRIMARY TABLE)

SELECT customerId,name,address,salary,(salary*3/100) AS ETF,(salary-(salary*3/100)) AS NetSalary FROM CustomerDetails HAVING ETF>2000;
(Past Checking : HAVING always check details from new TABLE)




















