# Ex. No: 5 Creating Triggers using PL/SQL

### AIM: To create a Trigger using PL/SQL.

### Steps:
1. Create employee table with following attributes (empid NUMBER, empname VARCHAR(10), dept VARCHAR(10),salary NUMBER);
2. Create salary_log table with following attributes (log_id NUMBER GENERATED ALWAYS AS IDENTITY, empid NUMBER,empname VARCHAR(10),old_salary NUMBER,new_salary NUMBER,update_date DATE);
3. Create a trigger named as log_salary-update.
4. Inside the trigger block, Insert the values into the salary_log table whenever the salary is updated.
5. End the trigger.
6. Update the salary of an employee in employee table.
7. Whenever a salary is updated for the employee it must be logged into the salary_log table with old salary and new salary.
8. Display the employee table, salary_log table.

### Program:

### Create employee table
### QUERY:
```
 CREATE TABLE el
  2  (
  3  empid NUMBER,
  4  empname VARCHAR2(10),
  5  dept VARCHAR2(10),
  6  salary NUMBER
  7  );
```
### OUTPUT:

![image](https://github.com/Anandanaruvi/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/120443233/47af7a89-5817-4795-8004-5a3f7abe6867)

### Create salary_log table
### QUERY:
```
 CREATE TABLE wages_log
  2  (
  3  log_id NUMBER GENERATED ALWAYS AS IDENTITY,
  4  empid NUMBER,
  5  empname VARCHAR2(10),
  6  old_salary NUMBER,
  7  new_salary NUMBER,
  8  update_date DATE
  9  );
```
### OUTPUT:
![image](https://github.com/Anandanaruvi/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/120443233/e7a85f6f-93ae-4559-82a5-4e8755f2f4d1)

### PLSQL Trigger code
### QUERY:
```
 CREATE OR REPLACE TRIGGER logging_sal_update
  2  BEFORE UPDATE ON el
  3  FOR EACH ROW
  4  BEGIN
  5  IF :OLD.salary != :NEW.salary THEN
  6  INSERT INTO wages_log (empid, empname, old_salary, new_salary, update_date)
  7  VALUES (:OLD.empid, :OLD.empname, :OLD.salary, :NEW.salary, SYSDATE);
  8  END IF;
  9  END;
 10  /
```
### Output:
![image](https://github.com/Anandanaruvi/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/120443233/2c4e1a99-6211-4b10-9616-2664f961dcc4)

### Inserting data into the employed table:
### QUERY:
```
insert into el values(1,'Anandan','AIDS',20000);

SQL> insert into el values(1,'Anandan','AIDS',20000);

SQL> insert into el values(2,'Mullai','AIDS',30000);

SQL> insert into el values(3,'Aadhavan','AIDS',40000);

SQL> insert into el values(4,'Aruvi','AIDS',50000);
```
### OUTPUT:

![image](https://github.com/Anandanaruvi/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/120443233/1764f153-aef6-4520-95f5-b1b732083ed3)

### Update the salary of an employed:
### QUERY:
```
SQL> UPDATE e1
  2  SET salary = 120000
  3  where empid=3;
```

### OUTPUT:
![image](https://github.com/Anandanaruvi/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/120443233/90d88553-3fde-40c3-bc25-15d95d4ab0fe)

### Display the employee table:
### QUERY:
```
select * from el
```
### OUTPUT:
![image](https://github.com/Anandanaruvi/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/120443233/757b5193-3c3c-4d85-ba22-66f6cdcc0fe6)

### Display the salary_log table:
### QUERY:
```
select * from wages_log;
```

### OUTPUT:
![image](https://github.com/Anandanaruvi/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/120443233/8b5c3bb4-7a71-4432-b74f-0d91a8a448d0)

### Result:

Thus the program implemented successfully.


