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
mysql> SELECT s.salesman_id, s.name AS salesman_name, COUNT(c.customer_id) AS num_customers
    -> FROM salesman s
    -> JOIN customer c ON s.salesman_id = c.salesman_id
    -> GROUP BY s.salesman_id, s.name
    -> HAVING COUNT(c.customer_id) > 1;
+-------------+---------------+---------------+
| salesman_id | salesman_name | num_customers |
+-------------+---------------+---------------+
|        5001 | James Hoog    |             2 |
|        5002 | Nail Knite    |             2 |
+-------------+---------------+---------------+
2 rows in set (0.00 sec)
```
