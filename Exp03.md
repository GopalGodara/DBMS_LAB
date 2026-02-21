# Experiment 3: Retrieving Data – Set 2 (Employee Table)


## 1. Employees & jobs in Dept 30, ordered by salary (DESC)
```sql
SELECT ename, job, sal FROM employee
WHERE deptno = 30
ORDER BY sal DESC;  -- Highest salary first
```

## 2. Job & DeptNo of employees whose name is 5 letters, starts with A and ends with N
```sql
SELECT job, deptno FROM employee
WHERE ename LIKE 'A___N';  -- _ represents exactly one character
```

## 3. Names of employees starting with S
```sql
SELECT ename FROM employee
WHERE ename LIKE 'S%';
```

## 4. Names of employees ending with S
```sql
SELECT ename FROM employee
WHERE ename LIKE '%S';
```

## 5. Employees working in Dept 10 / 20 / 40 OR working as Clerk / Salesman / Analyst
```sql
SELECT ename FROM employee
WHERE deptno IN (10,20,40) OR job IN ('CLERK','SALESMAN','ANALYST');
```

## 6. Employee number & name of employees who earn commission
```sql
SELECT empno, ename FROM employee
WHERE comm IS NOT NULL AND comm > 0;  -- Ensures commission exists
```

## 7. Employee number & total salary for each employee (Salary + Commission)
```sql
SELECT empno, (sal + IFNULL(comm,0)) AS total_salary
FROM employee;  -- IFNULL avoids NULL issues
```

## 8. Employee number & annual salary
```sql
SELECT empno, sal*12 AS annual_salary FROM employee;
```

## 9. Employees who are clerks earning more than 3000
```sql
SELECT ename FROM employee
WHERE job = 'CLERK' AND sal > 3000;
```

## 10. Employees who are clerk / salesman / analyst and earning more than 3000
```sql
SELECT ename FROM employee
WHERE job IN ('CLERK','SALESMAN','ANALYST') AND sal > 3000;
```
