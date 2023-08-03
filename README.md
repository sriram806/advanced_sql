Microsoft Windows [Version 10.0.22621.2070]
(c) Microsoft Corporation. All rights reserved.

C:\Users\lagad>cd/

C:\>cd xampp

C:\xampp>cd mysql

C:\xampp\mysql>cd bin

C:\xampp\mysql\bin>mysql.exe -u root
Welcome to the MariaDB monitor.  Commands end with ; or \g.
Your MariaDB connection id is 10
Server version: 10.4.28-MariaDB mariadb.org binary distribution

Copyright (c) 2000, 2018, Oracle, MariaDB Corporation Ab and others.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

MariaDB [(none)]> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| performance_schema |
| phpmyadmin         |
| student            |
| test               |
+--------------------+
6 rows in set (0.001 sec)

MariaDB [(none)]> use student;
Database changed
MariaDB [student]> show tables;
+-------------------+
| Tables_in_student |
+-------------------+
| customer          |
| data              |
| info              |
+-------------------+
3 rows in set (0.001 sec)

MariaDB [student]> desc info;
+-----------+-------------+------+-----+---------+-------+
| Field     | Type        | Null | Key | Default | Extra |
+-----------+-------------+------+-----+---------+-------+
| Cust_id   | int(10)     | YES  |     | NULL    |       |
| Full_Name | varchar(20) | YES  |     | NULL    |       |
| Country   | varchar(20) | YES  |     | NULL    |       |
| Income    | int(20)     | YES  |     | NULL    |       |
+-----------+-------------+------+-----+---------+-------+
4 rows in set (0.006 sec)

MariaDB [student]> select * from info;
+---------+-----------+-----------+--------+
| Cust_id | Full_Name | Country   | Income |
+---------+-----------+-----------+--------+
|     105 | John      | India     |  45000 |
|     106 | Smith     | USA       |  50000 |
|     108 | Varun     | Australia |  75000 |
+---------+-----------+-----------+--------+
3 rows in set (0.000 sec)

MariaDB [student]> insert into info(Cust_id,Full_Name,Country,Income)values(112,'Meg','Canada',99000),(117,'Kat','UK',73000);
Query OK, 2 rows affected (0.006 sec)
Records: 2  Duplicates: 0  Warnings: 0

MariaDB [student]> select * from info;
+---------+-----------+-----------+--------+
| Cust_id | Full_Name | Country   | Income |
+---------+-----------+-----------+--------+
|     105 | John      | India     |  45000 |
|     106 | Smith     | USA       |  50000 |
|     108 | Varun     | Australia |  75000 |
|     112 | Meg       | Canada    |  99000 |
|     117 | Kat       | UK        |  73000 |
+---------+-----------+-----------+--------+
5 rows in set (0.000 sec)

MariaDB [student]> select count(Cust_id) from info;
+----------------+
| count(Cust_id) |
+----------------+
|              5 |
+----------------+
1 row in set (0.000 sec)

MariaDB [student]> select sum(Income) from info;
+-------------+
| sum(Income) |
+-------------+
|      342000 |
+-------------+
1 row in set (0.000 sec)

MariaDB [student]> select sum(Cust_id) from info;
+--------------+
| sum(Cust_id) |
+--------------+
|          548 |
+--------------+
1 row in set (0.000 sec)

MariaDB [student]> select avg(Income) from info;
+-------------+
| avg(Income) |
+-------------+
|  68400.0000 |
+-------------+
1 row in set (0.001 sec)

MariaDB [student]> select avg(Cust_id) from info;
+--------------+
| avg(Cust_id) |
+--------------+
|     109.6000 |
+--------------+
1 row in set (0.001 sec)

MariaDB [student]> select min(Income) from info;
+-------------+
| min(Income) |
+-------------+
|       45000 |
+-------------+
1 row in set (0.001 sec)

MariaDB [student]> select min(Cust_id) from info;
+--------------+
| min(Cust_id) |
+--------------+
|          105 |
+--------------+
1 row in set (0.000 sec)

MariaDB [student]> select max(Income) from info;
+-------------+
| max(Income) |
+-------------+
|       99000 |
+-------------+
1 row in set (0.000 sec)

MariaDB [student]> select max(Income) from info; select Full_Name from info;
+-------------+
| max(Income) |
+-------------+
|       99000 |
+-------------+
1 row in set (0.000 sec)

+-----------+
| Full_Name |
+-----------+
| John      |
| Smith     |
| Varun     |
| Meg       |
| Kat       |
+-----------+
5 rows in set (0.000 sec)

MariaDB [student]> select Country from info group by Country;
+-----------+
| Country   |
+-----------+
| Australia |
| Canada    |
| India     |
| UK        |
| USA       |
+-----------+
5 rows in set (0.001 sec)

MariaDB [student]> select Full_Name, sum(Income) from info group by Full_Name;
+-----------+-------------+
| Full_Name | sum(Income) |
+-----------+-------------+
| John      |       45000 |
| Kat       |       73000 |
| Meg       |       99000 |
| Smith     |       50000 |
| Varun     |       75000 |
+-----------+-------------+
5 rows in set (0.003 sec)

MariaDB [student]> select Cust_id, sum(Country) from info group by Cust_id;me;
+---------+--------------+
| Cust_id | sum(Country) |
+---------+--------------+
|     105 |            0 |
|     106 |            0 |
|     108 |            0 |
|     112 |            0 |
|     117 |            0 |
+---------+--------------+
5 rows in set, 5 warnings (0.003 sec)

MariaDB [student]> select Cust_id, sum(Country) from info group by Cust_id;                                                                                                 +---------+--------------+
| Cust_id | sum(Country) |
+---------+--------------+
|     105 |            0 |
|     106 |            0 |
|     108 |            0 |
|     112 |            0 |
|     117 |            0 |
+---------+--------------+
5 rows in set, 5 warnings (0.001 sec)

MariaDB [student]> select Cust_id, sum(Income) from info group by Cust_id;                                                                                                  +---------+-------------+
| Cust_id | sum(Income) |
+---------+-------------+
|     105 |       45000 |
|     106 |       50000 |
|     108 |       75000 |
|     112 |       99000 |
|     117 |       73000 |
+---------+-------------+
5 rows in set (0.001 sec)

MariaDB [student]> select Full_Name, avg(Income) from info group by Full_Name;
+-----------+-------------+
| Full_Name | avg(Income) |
+-----------+-------------+
| John      |  45000.0000 |
| Kat       |  73000.0000 |
| Meg       |  99000.0000 |
| Smith     |  50000.0000 |
| Varun     |  75000.0000 |
+-----------+-------------+
5 rows in set (0.001 sec)

MariaDB [student]> select Full_Name, min(Income) from info group by Full_Name;
+-----------+-------------+
| Full_Name | min(Income) |
+-----------+-------------+
| John      |       45000 |
| Kat       |       73000 |
| Meg       |       99000 |
| Smith     |       50000 |
| Varun     |       75000 |
+-----------+-------------+
5 rows in set (0.000 sec)

MariaDB [student]> select Full_Name, max(Income) from info group by Full_Name;
+-----------+-------------+
| Full_Name | max(Income) |
+-----------+-------------+
| John      |       45000 |
| Kat       |       73000 |
| Meg       |       99000 |
| Smith     |       50000 |
| Varun     |       75000 |
+-----------+-------------+
5 rows in set (0.001 sec)


MariaDB [student]> select now();
+---------------------+
| now()               |
+---------------------+
| 2023-08-03 20:23:01 |
+---------------------+
1 row in set (0.000 sec)

MariaDB [student]> select date(now());
+-------------+
| date(now()) |
+-------------+
| 2023-08-03  |
+-------------+
1 row in set (0.000 sec)

MariaDB [student]> select curdate();
+------------+
| curdate()  |
+------------+
| 2023-08-03 |
+------------+
1 row in set (0.000 sec)

MariaDB [student]> SELECT DATE_FORMAT(CURDATE(), '%d/%m/%Y') today;
+------------+
| today      |
+------------+
| 03/08/2023 |
+------------+
1 row in set (0.000 sec)

MariaDB [student]> create table sales(ID int, CustomerID int, OrderDate date, FinancialCode char(2), Region char(7), SalesRep int);
Query OK, 0 rows affected (0.028 sec)

MariaDB [student]> desc sales;
+---------------+---------+------+-----+---------+-------+
| Field         | Type    | Null | Key | Default | Extra |
+---------------+---------+------+-----+---------+-------+
| ID            | int(11) | YES  |     | NULL    |       |
| CustomerID    | int(11) | YES  |     | NULL    |       |
| OrderDate     | date    | YES  |     | NULL    |       |
| FinancialCode | char(2) | YES  |     | NULL    |       |
| Region        | char(7) | YES  |     | NULL    |       |
| SalesRep      | int(11) | YES  |     | NULL    |       |
+---------------+---------+------+-----+---------+-------+
6 rows in set (0.006 sec)

MariaDB [student]> insert into sales values(200, 100, '2000-03-01', 'r1','Eastern',299);
Query OK, 1 row affected (0.008 sec)

MariaDB [student]> insert into sales values(201, 101, '2000-03-03', 'r2','Western',399);
Query OK, 1 row affected (0.006 sec)

MariaDB [student]> insert into sales values(202, 102, '2000-03-05', 'r3','Western',499);
Query OK, 1 row affected (0.005 sec)

MariaDB [student]> insert into sales values(203, 103, '2000-03-07', 'y1','Western',599);
Query OK, 1 row affected (0.006 sec)

MariaDB [student]> insert into sales values(204, 104, '2000-03-09', 'y2','Western',699);
Query OK, 1 row affected (0.006 sec)

MariaDB [student]> insert into sales values(205, 105, '2000-03-10', 'y3','Eastern',799);
Query OK, 1 row affected (0.005 sec)

MariaDB [student]> select * from sales;
+------+------------+------------+---------------+---------+----------+
| ID   | CustomerID | OrderDate  | FinancialCode | Region  | SalesRep |
+------+------------+------------+---------------+---------+----------+
|  200 |        100 | 2000-03-01 | r1            | Eastern |      299 |
|  201 |        101 | 2000-03-03 | r2            | Western |      399 |
|  202 |        102 | 2000-03-05 | r3            | Western |      499 |
|  203 |        103 | 2000-03-07 | y1            | Western |      599 |
|  204 |        104 | 2000-03-09 | y2            | Western |      699 |
|  205 |        105 | 2000-03-10 | y3            | Eastern |      799 |
+------+------------+------------+---------------+---------+----------+
6 rows in set (0.000 sec)

MariaDB [student]> select * from sales where year(OrderDate) = 200;
Empty set (0.005 sec)

MariaDB [student]> select * from sales where year(OrderDate) = 204;
Empty set (0.000 sec)

MariaDB [student]> select * from sales where year(OrderDate) = 2000;
+------+------------+------------+---------------+---------+----------+
| ID   | CustomerID | OrderDate  | FinancialCode | Region  | SalesRep |
+------+------------+------------+---------------+---------+----------+
|  200 |        100 | 2000-03-01 | r1            | Eastern |      299 |
|  201 |        101 | 2000-03-03 | r2            | Western |      399 |
|  202 |        102 | 2000-03-05 | r3            | Western |      499 |
|  203 |        103 | 2000-03-07 | y1            | Western |      599 |
|  204 |        104 | 2000-03-09 | y2            | Western |      699 |
|  205 |        105 | 2000-03-10 | y3            | Eastern |      799 |
+------+------------+------------+---------------+---------+----------+
6 rows in set (0.000 sec)

MariaDB [student]> select * from sales where OrderDate between '2000-03-05' and '2000-03-10';
+------+------------+------------+---------------+---------+----------+
| ID   | CustomerID | OrderDate  | FinancialCode | Region  | SalesRep |
+------+------------+------------+---------------+---------+----------+
|  202 |        102 | 2000-03-05 | r3            | Western |      499 |
|  203 |        103 | 2000-03-07 | y1            | Western |      599 |
|  204 |        104 | 2000-03-09 | y2            | Western |      699 |
|  205 |        105 | 2000-03-10 | y3            | Eastern |      799 |
+------+------------+------------+---------------+---------+----------+
4 rows in set (0.004 sec)

MariaDB [student]> select extract(year from OrderDate) from sales;
+------------------------------+
| extract(year from OrderDate) |
+------------------------------+
|                         2000 |
|                         2000 |
|                         2000 |
|                         2000 |
|                         2000 |
|                         2000 |
+------------------------------+
6 rows in set (0.002 sec)

MariaDB [student]> select date_format(STR_TO_DATE(OrderDate,'%Y-%m-%d'),'%d-%m-%Y') as DateFormat from sales;
+------------+
| DateFormat |
+------------+
| 01-03-2000 |
| 03-03-2000 |
| 05-03-2000 |
| 07-03-2000 |
| 09-03-2000 |
| 10-03-2000 |
+------------+
6 rows in set (0.005 sec)

MariaDB [student]>
