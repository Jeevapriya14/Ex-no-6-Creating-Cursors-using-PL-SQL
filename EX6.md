# Ex. No: 5 Creating Cursors using PL/SQL
## DATE:

### AIM: To create a cursor using PL/SQL.

### Steps:
1. Create employee table with following attributes (empid NUMBER, empname VARCHAR(10), dept VARCHAR(10),salary NUMBER);
2. Create a cursor named as employee_cursor
3. Using cursor read each record and display the result
4. Close the cursor

### Program:
### Create employee table:
```
CREATE TABLE employee (
  empid NUMBER,
  empname VARCHAR(20),
  dept VARCHAR(20),
  salary NUMBER
);

INSERT INTO employee VALUES (1, 'Jeevapriya', 'Sales', 100000);
INSERT INTO employee VALUES (2, 'Anitha', 'Marketing', 120000);
select * from employee;
```
### Employee table :
![Employee table creation](https://github.com/Jeevapriya14/Ex-no-6-Creating-Cursors-using-PL-SQL/assets/121003043/f2e423c5-7157-4295-ac91-c9548ea6dd71)


### PL/SQL Cursor code:
```
DECLARE
   CURSOR employee_cursor IS
   SELECT empid,empname,dept,salary
   FROM employee;
   emp_id NUMBER;
   emp_name VARCHAR(50);
   emp_dept VARCHAR(50);
   emp_salary NUMBER;
BEGIN
  OPEN employee_cursor;

  LOOP
    FETCH employee_cursor INTO emp_id, emp_name, emp_dept, emp_salary;

    EXIT WHEN employee_cursor%NOTFOUND;

    DBMS_OUTPUT.PUT_LINE('Employee ID: ' || emp_id);
    DBMS_OUTPUT.PUT_LINE('Employee Name: ' || emp_name);
    DBMS_OUTPUT.PUT_LINE('Department: ' || emp_dept);
    DBMS_OUTPUT.PUT_LINE('Salary: ' || emp_salary);
  END LOOP;

  CLOSE employee_cursor;
END;
/
```

### Output:
![PL/SQL CREATION](https://github.com/Jeevapriya14/Ex-no-6-Creating-Cursors-using-PL-SQL/assets/121003043/facdd270-7c49-4d14-8367-490856d63083)

### Result:
Thus,PL/SQL procedure completed successfully.
