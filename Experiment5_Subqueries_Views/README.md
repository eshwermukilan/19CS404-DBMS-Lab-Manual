# NAME : ESHWER M
# REG NO :212224040086

# Experiment 5: Subqueries and Views
## AIM
To study and implement subqueries and views.

## THEORY

### Subqueries
A subquery is a query inside another SQL query and is embedded in:
- WHERE clause
- HAVING clause
- FROM clause

**Types:**
- **Single-row subquery**:
  Sub queries can also return more than one value. Such results should be made use along with the operators in and any.
- **Multiple-row subquery**:
  Here more than one subquery is used. These multiple sub queries are combined by means of ‘and’ & ‘or’ keywords.
- **Correlated subquery**:
  A subquery is evaluated once for the entire parent statement whereas a correlated Sub query is evaluated once per row processed by the parent statement.

**Example:**
```sql
SELECT * FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```
### Views
A view is a virtual table based on the result of an SQL SELECT query.
**Create View:**
```sql
CREATE VIEW view_name AS
SELECT column1, column2 FROM table_name WHERE condition;
```
**Drop View:**
```sql
DROP VIEW view_name;
```

**Question 1**

![image](https://github.com/user-attachments/assets/4b15168e-5ff1-4234-914f-0850f8a16861)

```sql
select grade, COUNT(*)
from customer
group by grade
having grade > (
select avg(grade)
from customer
where city='New York');
```

**Output:**

![image](https://github.com/user-attachments/assets/f11a6105-9038-420d-8ffa-8623bd91da18)

**Question 2**

![image](https://github.com/user-attachments/assets/4ecaf60e-7e18-49cd-9d04-a30ddf389041)

```sql
select student_name, grade
from grades g1
where grade=(select MIN(grade)
from grades g2
where g2.subject=g1.subject)
```

**Output:**

![image](https://github.com/user-attachments/assets/95688a8f-b1c7-4a2a-8fe5-d1bdd63e8a83)

**Question 3**

![image](https://github.com/user-attachments/assets/8b0de4e3-e23b-495d-b57b-f30e309d0691)

```sql
select name
from customer
where phone is NOT NULL
AND phone IN(
select phone
from customer
group by phone
having count(*)=1
);
```

**Output:**

![image](https://github.com/user-attachments/assets/cd62d2d1-2bb6-4981-9b40-09ba575dae40)

**Question 4**

![image](https://github.com/user-attachments/assets/9934ac57-71d0-4877-bcfe-f04e79e83392)

```sql
select o.ord_no, o.purch_amt, o.ord_date, o.customer_id, o.salesman_id
from orders o
join salesman s on o.salesman_id=s.salesman_id
where s.city='New York';
```

**Output:**

![image](https://github.com/user-attachments/assets/1a9e0435-6ad1-4658-8d90-756690352ea6)

**Question 5**

![image](https://github.com/user-attachments/assets/08f4e08e-9c8e-444c-9258-41c4d234a3cd)

```sql
select id, name, age, city, income from Employee
where age<(
select avg(age) from Employee
where income>250000);
```

**Output:**

![image](https://github.com/user-attachments/assets/1ad51780-e00e-4f47-8399-615c57e4ffad)

**Question 6**

![image](https://github.com/user-attachments/assets/ba9de523-f933-4f52-b8aa-b6f504840c39)

```sql
select * from Departments
where length(department_name)>
(
select avg(length(department_name))
from Departments)
```

**Output:**

![image](https://github.com/user-attachments/assets/5adb6bfd-4baa-4b82-af59-2556fc8aec22)

**Question 7**

![image](https://github.com/user-attachments/assets/dfdf281d-3c78-47c9-acdc-80b3358d54a8)

```sql
select commission from salesman
where salesman_id in(
select salesman_id from customer
where city='Paris');
```

**Output:**

![image](https://github.com/user-attachments/assets/4991be0f-e390-49a8-9882-b4e900a84ee9)

**Question 8**

![image](https://github.com/user-attachments/assets/84f1c0f6-22e7-4713-86de-5d5318dc5d6d)

```sql
select * from CUSTOMERS
where id in(
select ID from customers
where SALARY>4500);
```

**Output:**

![image](https://github.com/user-attachments/assets/3191695b-873f-4420-a2b4-5e07b04f84f5)

**Question 9**

![image](https://github.com/user-attachments/assets/cde86a4f-778e-4abb-859b-5c7ccc0dd3b9)

```sql
select o.ord_no, o.purch_amt, o.ord_date, o.customer_id, o.salesman_id
from orders o
join salesman s on o.salesman_id=s.salesman_id
where s.city='New York';
```

**Output:**

![image](https://github.com/user-attachments/assets/a51329bc-09e8-4c46-ba93-14ccb07ebf36)

**Question 10**

![image](https://github.com/user-attachments/assets/69d2db15-bf7a-4d1f-8cd9-fba7b400b1c7)

```sql
select * from CUSTOMERS
where id in(
select ID from customers
where ADDRESS='Delhi' and AGE<30);
```

**Output:**

![image](https://github.com/user-attachments/assets/094a7e80-d7f8-461d-8bbb-393223363d24)

## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.
