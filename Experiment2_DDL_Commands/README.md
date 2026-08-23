# Experiment 2: DDL Commands
# NAME : INDHUJA.K
# Register no : 212225040133
## AIM
To study and implement DDL commands and different types of constraints.

## THEORY

### 1. CREATE
Used to create a new relation (table).

**Syntax:**
```sql
CREATE TABLE (
  field_1 data_type(size),
  field_2 data_type(size),
  ...
);
```
### 2. ALTER
Used to add, modify, drop, or rename fields in an existing relation.
(a) ADD
```sql
ALTER TABLE std ADD (Address CHAR(10));
```
(b) MODIFY
```sql
ALTER TABLE relation_name MODIFY (field_1 new_data_type(size));
```
(c) DROP
```sql
ALTER TABLE relation_name DROP COLUMN field_name;
```
(d) RENAME
```sql
ALTER TABLE relation_name RENAME COLUMN old_field_name TO new_field_name;
```
### 3. DROP TABLE
Used to permanently delete the structure and data of a table.
```sql
DROP TABLE relation_name;
```
### 4. RENAME
Used to rename an existing database object.
```sql
RENAME TABLE old_relation_name TO new_relation_name;
```
### CONSTRAINTS
Constraints are used to specify rules for the data in a table. If there is any violation between the constraint and the data action, the action is aborted by the constraint. It can be specified when the table is created (using CREATE TABLE) or after it is created (using ALTER TABLE).
### 1. NOT NULL
When a column is defined as NOT NULL, it becomes mandatory to enter a value in that column.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) NOT NULL
);
```
### 2. UNIQUE
Ensures that values in a column are unique.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) UNIQUE
);
```
### 3. CHECK
Specifies a condition that each row must satisfy.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) CHECK (logical_expression)
);
```
### 4. PRIMARY KEY
Used to uniquely identify each record in a table.
Properties:
Must contain unique values.
Cannot be null.
Should contain minimal fields.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) PRIMARY KEY
);
```
### 5. FOREIGN KEY
Used to reference the primary key of another table.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size),
  FOREIGN KEY (column_name) REFERENCES other_table(column)
);
```
### 6. DEFAULT
Used to insert a default value into a column if no value is specified.

Syntax:
```sql
CREATE TABLE Table_Name (
  col_name1 data_type,
  col_name2 data_type,
  col_name3 data_type DEFAULT 'default_value'
);
```

**Question 1**
Create a new table named item with the following specifications and constraints:
item_id as TEXT and as primary key.
item_desc as TEXT.
rate as INTEGER.
icom_id as TEXT with a length of 4.
icom_id is a foreign key referencing com_id in the company table.
The foreign key should cascade updates and deletes.
item_desc and rate should not accept NULL.

```sql
CREATE TABLE item (
item_id TEXT PRIMARY KEY,
item_desc TEXT NOT NULL,
rate INTEGER NOT NULL,
icom_id TEXT CHECK (Length(4)),
FOREIGN KEY (icom_id)REFERENCES company(com_id)
     ON UPDATE CASCADE
     ON DELETE CASCADE

);
```

**Output:**

<img width="1251" height="711" alt="image" src="https://github.com/user-attachments/assets/fd968e8c-21b2-42e1-b8e6-fb4e7dae7020" />

**Question 2**
---
Write an SQL command can to add a column named email of type TEXT to the customers table

```sql
alter table Customers
add email TEXT;
```

**Output:**

<img width="1266" height="674" alt="image" src="https://github.com/user-attachments/assets/411b04c1-8f32-4e28-a430-c0726f6bc1f2" />

**Question 3**
---
Create a table named Products with the following constraints:
ProductID as INTEGER should be the primary key.
ProductName as TEXT should be unique and not NULL.
Price as REAL should be greater than 0.
StockQuantity as INTEGER should be non-negative.
```sql
CREATE TABLE Products(
ProductID INTEGER  primary key,
ProductName TEXT UNIQUE not NULL,
Price  REAL CHECK(Price>0),
StockQuantity  INTEGER CHECK(StockQuantity>0));
```

**Output:**

<img width="1259" height="698" alt="image" src="https://github.com/user-attachments/assets/49ebdfdf-468a-45cd-85e5-8654d7fa6b62" />

**Question 4**
---
Insert all employees from Former_employees into Employee

Table attributes are EmployeeID, Name, Department, Salary

For example:

```sql
INSERT INTO Employee (EmployeeID, Name, Department, Salary)
SELECT EmployeeID, Name, Department, Salary
FROM Former_employees;
```

**Output:**

<img width="1250" height="657" alt="image" src="https://github.com/user-attachments/assets/a7b6f3d9-537e-4f87-b6df-3fbdd9565406" />

**Question 5**
---
Write a SQL Query  to Rename attribute "name" to "first_name"  and add mobilenumber as number ,DOB as Date,State as varchar(30) in the table Companies. 

```sql
ALTER TABLE Companies
RENAME COLUMN name TO first_name;

ALTER TABLE Companies
ADD COLUMN mobilenumb number;

ALTER TABLE Companies
ADD COLUMN DOB Date;

ALTER TABLE Companies
ADD COLUMN State varchar(30);
```

**Output:**

<img width="1245" height="779" alt="image" src="https://github.com/user-attachments/assets/3efce06e-904f-4339-a984-5349b3c9e11a" />

**Question 6**
---
In the Employee table, insert a record where some fields are NULL, another record where all fields are filled without any NULL values, and a third record where some fields are filled, and others are left as NULL.

EmployeeID  Name          Position    Department  Salary
----------  ------------  ----------  ----------  ----------
5           George Clark  Consultant
7           Noah Davis    Manager     HR          60000
8           Ava Miller    Consultant  IT
 

```sql
INSERT INTO Employee (EmployeeID, Name, Position)
VALUES (5, 'George Clark', 'Consultant');
INSERT INTO Employee (EmployeeID, Name, Position, Department, Salary)
VALUES (7, 'Noah Davis', 'Manager', 'HR', 60000);
INSERT INTO Employee (EmployeeID, Name, Position, Department)
VALUES (8, 'Ava Miller', 'Consultant', 'IT');
```

**Output:**

<img width="1256" height="662" alt="image" src="https://github.com/user-attachments/assets/c4b311b5-06f5-4931-8a40-f888d90d2bc9" />

**Question 7**
---
Create a table named Shipments with the following constraints:
ShipmentID as INTEGER should be the primary key.
ShipmentDate as DATE.
SupplierID as INTEGER should be a foreign key referencing Suppliers(SupplierID).
OrderID as INTEGER should be a foreign key referencing Orders(OrderID).

```sql
CREATE TABLE Shipments(
ShipmentID INTEGER PRIMARY KEY,
ShipmentDate DATE,
SupplierID INTEGER,
OrderID INTEGER,
FOREIGN KEY(SupplierID)REFERENCES Suppliers(SupplierID)
FOREIGN KEY(OrderID)REFERENCES Orders(OrderID)
);
```

**Output:**

<img width="1253" height="634" alt="image" src="https://github.com/user-attachments/assets/ab98f73a-231a-4e9f-bf14-3e7e93890337" />


**Question 8**
---
Create a table named Employees with the following columns:

EmployeeID as INTEGER
FirstName as TEXT
LastName as TEXT
HireDate as DATE

```sql
CREATE TABLE Employees(
EmployeeID INTEGER,
FirstName TEXT,
LastName TEXT,
HireDate DATE
);
```

**Output:**

<img width="1257" height="693" alt="image" src="https://github.com/user-attachments/assets/780c255b-8331-46d6-9d79-c21271eba38e" />


**Question 9**
---
Create a table named Attendance with the following constraints:
AttendanceID as INTEGER should be the primary key.
EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).
AttendanceDate as DATE.
Status as TEXT should be one of 'Present', 'Absent', 'Leave'.

```sql
CREATE TABLE Attendance(
AttendanceID INTEGER PRIMARY KEY,
EmployeeID INTEGER,
AttendanceDate DATE,
Status TEXT CHECK(Status='Present'OR Status='Absent'OR Status='Leave'),
FOREIGN KEY(EmployeeID) REFERENCES Employees(EmployeeID)
);
```

**Output:**

<img width="1262" height="692" alt="image" src="https://github.com/user-attachments/assets/6ba32a5e-ade7-4967-b2d7-6b5c053e6c71" />


**Question 10**
---
Insert the below data into the Customers table, allowing the City and ZipCode columns to take their default values.

CustomerID  Name          Address
----------  ------------  ----------
304         Peter Parker  Spider St      

Note: The City and ZipCode columns will use their default values.
 

```sql
INSERT INTO Customers (CustomerID, Name, Address)
VALUES (304, 'Peter Parker', 'Spider St');
```

**Output:**

<img width="1258" height="699" alt="image" src="https://github.com/user-attachments/assets/6167394c-4088-42ef-bec6-4b1f7d7ebf93" />



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
