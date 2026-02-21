# Experiment 06


## 1. Display empno, ename, dept name instead of deptno
```sql
SELECT
    e.empno,
    e.ename,
    CASE e.deptno
        WHEN 10 THEN 'RESEARCH'
        WHEN 20 THEN 'ACCOUNTING'
        WHEN 30 THEN 'SALES'
        WHEN 40 THEN 'OPERATIONS'
    END AS department
FROM employee e;
```

## 2. Display your age in days (Assuming birthdate = 2000-01-01)
```sql
SELECT DATEDIFF(CURDATE(), '2000-01-01') AS age_in_days;
```

## 3. Display your age in months
```sql
SELECT TIMESTAMPDIFF(MONTH, '2000-01-01', CURDATE()) AS age_in_months;
```

## 4. Display current date as 15th August Friday Nineteen Ninety-Seven
```sql
SELECT DATE_FORMAT('1997-08-15', '%D %M %W %Y') AS formatted_date;
```

## 5. Display formatted output for each employee, e.g., Scott joined company on Wednesday 13th August Nineteen Ninety
```sql
SELECT CONCAT(
        ename,' has joined the company on ',
        DATE_FORMAT(hiredate,'%W %D %M %Y')
    ) AS joining_info
FROM employee
WHERE ename = 'SCOTT';
```

## 6. Find nearest Saturday after current date
```sql
SELECT DATE_ADD(
    CURDATE(),
    INTERVAL CASE
        WHEN DAYOFWEEK(CURDATE()) = 7 THEN 7  -- If today is Saturday, add 7 days for next Saturday
        ELSE 7 - DAYOFWEEK(CURDATE())         -- Otherwise, add days left to Saturday
    END DAY
) AS NEXT_SATURDAY;
```

## 7. Display current time
```sql
SELECT CURTIME();
```

## 8. Display the date three months before current date
```sql
SELECT DATE_SUB(CURDATE(), INTERVAL 3 MONTH) AS date_three_months_ago;
```

## 9. Employees who joined in the month of December
```sql
SELECT ename, hiredate FROM employee
WHERE MONTH(hiredate) = 12;
```

## 10. Employees whose first 2 characters of hiredate = last 2 characters of salary
```sql
SELECT ename FROM employee
WHERE LEFT(YEAR(hiredate),2) = RIGHT(sal,2);
```

## 11. Employees whose 10% salary = year of joining
```sql
SELECT ename FROM employee
WHERE sal * 0.10 = YEAR(hiredate);
```

## 12. Employees who joined before 15th of the month
```sql
SELECT ename, hiredate FROM employee
WHERE DAY(hiredate) < 15;
```

## 13. Employees whose joining date is available in deptno
```sql
SELECT ename FROM employee
WHERE DAY(hiredate) = deptno;
```
