# ACE & Oracle database

## Download and install free version of Oracle database

### Prepare folder (Windows)
```bat
:: Create folder
mkdir c:\dbfree
:: Disable inheritance
icacls c:\dbfree /inheritancelevel:d
:: Remove the Authenticated Users permissions
icacls c:\dbfree /remove:g *s-1-5-11
```

Check permissions on existing folder:
```bat
icacls c:\dbfree
```

### Check listener and connect
```bat
cd c:\dbfree\dbhomeFree\bin
lsnrctl status

cd c:\dbfree\dbhomeFree\bin
sqlplus system@172.16.13.130:1521
```
Disconnect with `exit`

## Demo database

### Create table

```sql
DROP TABLE DEPARTMENTS;

CREATE TABLE DEPARTMENTS(
ID VARCHAR (3) NOT NULL,
DEPARTMENT_NAME VARCHAR (20) NOT NULL
);

INSERT INTO DEPARTMENTS VALUES('P01','Planning');
INSERT INTO DEPARTMENTS VALUES('P02','Preparations');
INSERT INTO DEPARTMENTS VALUES('M01','Manufacturing-1');
INSERT INTO DEPARTMENTS VALUES('M02','Manufacturing-2');
INSERT INTO DEPARTMENTS VALUES('C01','Control');
INSERT INTO DEPARTMENTS VALUES('E01','Packaging');
```

### Stored procedure

Create procedure
```sql
CREATE OR REPLACE
PROCEDURE NEW_DEPARTMENT
( dep_id IN VARCHAR
, dep_name IN VARCHAR
) AS
BEGIN
  -- NULL;
  INSERT INTO DEPARTMENTS VALUES(
    NEW_DEPARTMENT.dep_id,
    NEW_DEPARTMENT.dep_name
  );
END NEW_DEPARTMENT;
/
```

List procedure
```sql
SELECT * FROM ALL_SOURCE WHERE TYPE = 'PROCEDURE' AND NAME = 'NEW_DEPARTMENT';
```

Invoke procedure
```sql
EXECUTE NEW_DEPARTMENT('X01','Test1');
```

Delete procedure
```sql
DROP PROCEDURE NEW_DEPARTMENT;
```

### Stored function

Create function
```sql
CREATE OR REPLACE
FUNCTION calculate_score
( num1 IN NUMBER
, num2 IN NUMBER
) RETURN NUMBER AS
BEGIN
  RETURN num1 + num2;
END calculate_score;
/
```
List
```sql
SELECT * FROM ALL_SOURCE WHERE TYPE = 'FUNCTION' AND NAME = 'CALCULATE_SCORE';
```

Execute
```sql
var x number
exec :x := CALCULATE_SCORE(1,3);
print x;
```

Delete
```sql
DROP FUNCTION CALCULATE_SCORE;
```
