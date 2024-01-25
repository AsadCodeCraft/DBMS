# Practical 1
mysql> desc orders;
+-------------+------+------+-----+---------+-------+
| Field       | Type | Null | Key | Default | Extra |
+-------------+------+------+-----+---------+-------+
| ord_no      | int  | NO   | PRI | NULL    |       |
| purch_amt   | int  | YES  |     | NULL    |       |
| ord_date    | date | YES  |     | NULL    |       |
| customer_id | int  | YES  | MUL | NULL    |       |
| salesman_id | int  | YES  | MUL | NULL    |       |
+-------------+------+------+-----+---------+-------+
5 rows in set (0.00 sec)

mysql> desc customer;
+-------------+------+------+-----+---------+-------+
| Field       | Type | Null | Key | Default | Extra |
+-------------+------+------+-----+---------+-------+
| customer_id | int  | NO   | PRI | NULL    |       |
| cust_name   | text | NO   |     | NULL    |       |
| city        | text | NO   |     | NULL    |       |
| grade       | int  | YES  |     | NULL    |       |
| salesman_id | int  | YES  | MUL | NULL    |       |
+-------------+------+------+-----+---------+-------+
5 rows in set (0.00 sec)

mysql> desc salesman;
+-------------+-------+------+-----+---------+-------+
| Field       | Type  | Null | Key | Default | Extra |
+-------------+-------+------+-----+---------+-------+
| salesman_id | int   | NO   | PRI | NULL    |       |
| name        | text  | NO   |     | NULL    |       |
| city        | text  | NO   |     | NULL    |       |
| comission   | float | YES  |     | NULL    |       |
+-------------+-------+------+-----+---------+-------+
4 rows in set (0.00 sec)

#Display name and commission for all the salesmen.
Query OK, 0 rows affected (0.04 sec)

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
6 rows in set (0.21 sec)

#Retrieve salesman id of all salesmen from orders table without any repeats.
Query OK, 0 rows affected (0.00 sec)

mysql> select distinct salesman_id from orders;
+-------------+
| salesman_id |
+-------------+
|        5001 |
|        5002 |
|        5003 |
|        5005 |
|        5006 |
|        5007 |
+-------------+
6 rows in set (0.01 sec)

mysql> select name,city from salesman where city = "paris";
+------------+-------+
| name       | city  |
+------------+-------+
| Nail Knite | Paris |
| Mc Lyon    | Paris |
+------------+-------+
2 rows in set (0.01 sec)

#Display all the information for those customers with a grade of 200.
Query OK, 0 rows affected (0.00 sec)

mysql> select * from customers where grade = 200;
ERROR 1146 (42S02): Table 'prac1.customers' doesn't exist
mysql> select * from customer where grade = 200;

+-------------+--------------+------------+-------+-------------+
| customer_id | cust_name    | city       | grade | salesman_id |
+-------------+--------------+------------+-------+-------------+
|        3003 | Jozy Altidor | Moscow     |   200 |        5007 |
|        3005 | Graham Zusi  | California |   200 |        5002 |
|        3007 | Brad Davis   | New York   |   200 |        5001 |
+-------------+--------------+------------+-------+-------------+
3 rows in set (0.01 sec)

mysql> #Display the order number, order date and the purchase amount for order(s) which will be delivered by the salesman with ID 5001
Query OK, 0 rows affected (0.00 sec)

mysql> select ord_no, ord_date, purch_amt from orders where salesman_id = 5001;
+--------+------------+-----------+
| ord_no | ord_date   | purch_amt |
+--------+------------+-----------+
|  70002 | 2012-10-05 |        65 |
|  70005 | 2012-07-27 |      2401 |
|  70008 | 2012-09-10 |      5760 |
|  70013 | 2012-04-25 |      3046 |
+--------+------------+-----------+
4 rows in set (0.17 sec)
