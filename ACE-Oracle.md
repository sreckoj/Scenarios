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
:: Start installation
```

### Check permissions on existing folder (Windows)
```bat
icacls c:\dbfree
:: Or using Explorer
```
