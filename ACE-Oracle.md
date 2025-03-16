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

### Check permissions on existing folder (Windows)
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
