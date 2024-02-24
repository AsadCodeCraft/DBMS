## **🚀 Practical 2 Subquery-join operations on Relational Schema**
### **USING (practical 1)**
> ### **Q.1) Count the customers with grades above New York’s average.**
```
mysql> select count(*) as Average_Count from customer where grade > (select avg(grade) from customer where city = "New York");
+---------------+
| Average_Count |
+---------------+
|             5 |
+---------------+
1 row in set (0.00 sec)
```

> ### **Q.2) Find the name and numbers of all salesmen who had more than one customer.**
```
mysql> select salesman_id,name from salesman a where 1<(select count(*) from
    -> customer where salesman_id=a.salesman_id);
+-------------+------------+
| salesman_id | name       |
+-------------+------------+
| 5001        | James Hoog |
| 5002        | Nail Knite |
+-------------+------------+
2 rows in set (0.01 sec)

```
> ### **Q.3) Demonstrate the DELETE operation by removing salesman with id 1000. All his orders must also be deleted**
```
mysql> ALTER TABLE orders
    -> ADD CONSTRAINT fk_salesman_id
    -> FOREIGN KEY (salesman_id)
    -> REFERENCES salesman(salesman_id)
    -> ON DELETE CASCADE;
Query OK, 12 rows affected (0.22 sec)
Records: 12  Duplicates: 0  Warnings: 0

mysql> DELETE FROM salesman where salesman_id = 5001;
Query OK, 1 row affected (0.01 sec)
```
