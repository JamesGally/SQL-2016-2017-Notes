# TSQL Changes


### STRING_SPLIT

This is a table-valued function and converts a delimited string into a single column table.

* **input**:     char, separator (single character)
* **output**:    single column table with values. Column name is value

```

SELECT value FROM STRING_SPLIT('1,2,3,4,5',',')
WHERE RTRIM(value) <> '';  --removes any empty strings (optional)

```

Note: STRING_SPLIT requires at least compatibility mode 130.

`SELECT name,compatibility_level FROM sys.databases `



### STRING_ESCAPE

This is a scalar function and escapes special characters in an input string.

* **input**:     string, type (As of SQL Server 2016, the only supported value for type is 'json')
* **output**:    string with escaped special characters

` SELECT STRING_ESCAPE('a\bc/de"f','JSON') AS escaped_input; `

List of characters that can be escaped can be found here https://docs.microsoft.com/en-us/sql/t-sql/functions/string-escape-transact-sql


### CONCAT_WS 

Concatenates a variable number of arguments with a delimiter specified in the 1st argument.

* **input**:     string, args (1..n arguments of any type)
* **output**:    string 

Note: Null values are ignored during concatenation, and does not add the separator. 

` SELECT CONCAT_WS(',','Adress line 1', NULL, NULL, 'Boston', 'MA', 12345) AS Address; `
