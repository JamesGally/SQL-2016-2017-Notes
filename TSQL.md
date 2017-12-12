# TSQL Changes

### STRING_SPLIT

This is a table-valued function and converts a delimited string into a single column table.

* **input**:      string, separator (single character)
* **output**:    single column table with values. Column name is value

```

SELECT value FROM STRING_SPLIT('1,2,3,4,5',',')
WHERE RTRIM(value) <> '';  --removes any empty strings (optional)

```

Note: STRING_SPLIT requires at least compatibility mode 130.

`SELECT name,compatibility_level FROM sys.databases `
