## 🚀 **Practical 1**

- **Creating Database**
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

- **Creating tables**
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
- **Importing data into table using csv**
```

```
