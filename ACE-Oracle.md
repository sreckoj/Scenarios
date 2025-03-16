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