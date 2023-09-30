# Ex. No: 6 Creating Cursors using PL/SQL

### AIM: To create a cursor using PL/SQL.

### Steps:
1. Create employee table with following attributes (empid NUMBER, empname VARCHAR(10), dept VARCHAR(10),salary NUMBER);
2. Create a cursor named as employee_cursor
3. Using cursor read each record and display the result
4. Close the cursor

### Program:
### Create employee table
```
 create table employee(empid int,empname varchar(10),dept varchar(10),salary decimal(10,2));
```

### PLSQL Cursor code
```
 DELIMITER //
 CREATE PROCEDURE fetch_employee_data()
    BEGIN
       DECLARE v_empid INT;
       DECLARE v_empname VARCHAR(10);
       DECLARE v_dept VARCHAR(10);
       DECLARE v_salary DECIMAL(10, 2);
    
       DECLARE emp_cursor CURSOR FOR
         SELECT empid, empname, dept, salary
         FROM employee;
    
       DECLARE CONTINUE HANDLER FOR NOT FOUND SET @finished = 1;
    
    
       OPEN emp_cursor;
    
    
       SET @finished = 0;
    
       FETCH_NEXT: LOOP
         FETCH emp_cursor INTO v_empid, v_empname, v_dept, v_salary;
         IF @finished = 1 THEN
           LEAVE FETCH_NEXT; -- Exit the loop when no more rows
         END IF;
    
         SELECT v_empid, v_empname, v_dept, v_salary;
       END LOOP FETCH_NEXT;
    
    
       CLOSE emp_cursor;
     END //
```

### Output:
![Screenshot 2023-09-30 221808](https://github.com/Saravana-kumar369/Ex-no-6-Creating-Cursors-using-PL-SQL/assets/117925254/584ab501-dece-4e6d-995d-d686250a7180)
![Screenshot 2023-09-30 222234](https://github.com/Saravana-kumar369/Ex-no-6-Creating-Cursors-using-PL-SQL/assets/117925254/5b1a283b-6a8a-4865-9255-df3b5597a6a9)

### Result:
Thus cursor using PL/SQL created successfully
