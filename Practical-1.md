## 🚀 **Practical 1**

### > **Creating Database**
```
mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| performance_schema |
| sys                |
+--------------------+
  4 rows in set (0.01 sec)

mysql> create database prac1;
Query OK, 1 row affected (0.11 sec)

mysql> use prac1;
Database changed
```

### > **Creating tables**
```
mysql> CREATE TABLE `salesman` (`salesman_id` int, `name` text,`city` text,`comission` float,PRIMARY KEY (`salesman_id`));
Query OK, 0 rows affected (0.25 sec)

mysql> desc salesman;
+-------------+-------+------+-----+---------+-------+
| Field       | Type  | Null | Key | Default | Extra |
+-------------+-------+------+-----+---------+-------+
| salesman_id | int   | NO   | PRI | NULL    |       |
| name        | text  | YES  |     | NULL    |       |
| city        | text  | YES  |     | NULL    |       |
| comission   | float | YES  |     | NULL    |       |
+-------------+-------+------+-----+---------+-------+
4 rows in set (0.03 sec)
```

### > **Importing data into table using csv**

**Note: keep the file in path as follwos C:/ProgramData/MySQL/MySQL Server 8.3/Uploads/**

```
mysql> load data infile "C:/ProgramData/MySQL/MySQL Server 8.3/Uploads/salesman.csv"
    -> into table salesman
    -> fields terminated by ',' enclosed by '"'
    -> lines terminated by '\n'
    -> ignore 1 rows;
Query OK, 6 rows affected (0.05 sec)
Records: 6  Deleted: 0  Skipped: 0  Warnings: 0
```
**Similarly Create Table for ***Customers & Orders*****

### > **Show tables data**

```
mysql> show tables;
+-----------------+
| Tables_in_prac1 |
+-----------------+
| customer        |
| orders          |
| salesman        |
+-----------------+
3 rows in set (0.00 sec)

mysql> select * from customer;
+-------------+----------------+------------+-------+-------------+
| customer_id | cust_name      | city       | grade | salesman_id |
+-------------+----------------+------------+-------+-------------+
|        3001 | Brad Guzan     | London     |  NULL |        5005 |
|        3002 | Nick Rimando   | New York   |   100 |        5001 |
|        3003 | Jozy Altidor   | Moscow     |   200 |        5007 |
|        3004 | Fabian Johnson | Paris      |   300 |        5006 |
|        3005 | Graham Zusi    | California |   200 |        5002 |
|        3007 | Brad Davis     | New York   |   200 |        5001 |
|        3008 | Julian Green   | London     |   300 |        5002 |
|        3009 | Geoff Cameron  | Berlin     |   100 |        5003 |
+-------------+----------------+------------+-------+-------------+
8 rows in set (0.00 sec)

mysql> select * from salesman;
+-------------+------------+----------+-----------+
| salesman_id | name       | city     | comission |
+-------------+------------+----------+-----------+
|        5001 | James Hoog | New York |      0.15 |
|        5002 | Nail Knite | Paris    |      0.13 |
|        5003 | Lauson Hen | San Jose |      0.12 |
|        5005 | Pit Alex   | London   |      0.11 |
|        5006 | Mc Lyon    | Paris    |      0.14 |
|        5007 | Paul Adam  | Rome     |      0.13 |
+-------------+------------+----------+-----------+
6 rows in set (0.00 sec)

mysql> select * from orders;
+--------+-----------+------------+-------------+-------------+
| ord_no | purch_amt | ord_date   | customer_id | salesman_id |
+--------+-----------+------------+-------------+-------------+
|  70001 |       151 | 2012-10-05 |        3005 |        5002 |
|  70002 |        65 | 2012-10-05 |        3002 |        5001 |
|  70003 |      2480 | 2012-10-10 |        3009 |        5003 |
|  70004 |       111 | 2012-08-17 |        3009 |        5003 |
|  70005 |      2401 | 2012-07-27 |        3007 |        5001 |
|  70007 |       949 | 2012-09-10 |        3005 |        5002 |
|  70008 |      5760 | 2012-09-10 |        3002 |        5001 |
|  70009 |       271 | 2012-09-10 |        3001 |        5005 |
|  70010 |      1983 | 2012-10-10 |        3004 |        5006 |
|  70011 |        75 | 2012-08-17 |        3003 |        5007 |
|  70012 |       250 | 2012-06-27 |        3008 |        5002 |
|  70013 |      3046 | 2012-04-25 |        3002 |        5001 |
+--------+-----------+------------+-------------+-------------+
12 rows in set (0.00 sec)
```

> ### **Q.1) Display name and commission for all the salesmen.**
```
 mysql> select name, comission from salesman;
  +------------+-----------+
  | name       | comission |
  +------------+-----------+
  | James Hoog |      0.15 |
  | Nail Knite |      0.13 |
  | Lauson Hen |      0.12 |
  | Pit Alex   |      0.11 |
  | Mc Lyon    |      0.14 |
  | Paul Adam  |      0.13 |
  +------------+-----------+
  6 rows in set (0.00 sec)
```
> ### **Q.2) Retrieve salesman id of all salesmen from orders table without any repeats.**
> ### **Q.3)Display names and city of salesman, who belongs to the city of Paris.**
> ### **Q.4)Display all the information for those customers with a grade of 200.**
> ### **Q.5)Display the order number, order date and the purchase amount for order(s) which will be delivered by the salesman with ID 5001**
