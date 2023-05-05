To get the maximum length for each column in a table, you can use the MAX() function with the LENGTH() function, and apply them to each column in the SELECT statement. Here's an example:

```
SELECT 
    MAX(LENGTH(column1)) AS max_length_column1,
    MAX(LENGTH(column2)) AS max_length_column2,
    MAX(LENGTH(column3)) AS max_length_column3
FROM 
    table_name;

```
This query will return the maximum length for each column in table_name. You can replace column1, column2, and column3 with the actual names of the columns you want to check.
