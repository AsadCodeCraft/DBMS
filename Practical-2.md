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
