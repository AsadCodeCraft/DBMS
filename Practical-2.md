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
