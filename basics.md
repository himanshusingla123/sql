# What are purpose of tcast and substring in sql
1. **CAST/CONVERT Function:**
   - The `CAST` or `CONVERT` functions in SQL are used to convert a value from one data type to another. For example:
     ```sql
     SELECT CAST(column_name AS VARCHAR(10)) FROM table_name;
     ```
     This converts the values in `column_name` to VARCHAR with a maximum length of 10 characters.

2. **SUBSTRING Function:**
   - The `SUBSTRING` function is used to extract a portion of a string. It takes three arguments: the string, the starting position, and the length of the substring. For example:
     ```sql
     SELECT SUBSTRING(column_name, 1, 3) FROM table_name;
     ```
     This extracts a substring of length 3, starting from the first character of the values in `column_name`.

