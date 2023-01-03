# Insert/Update Current Time in MySQL

If you want to specify a different time zone for the current date and time, you can use the CONVERT_TZ function. For example:

SET `date_column` = CONVERT_TZ(NOW(), 'UTC', 'Asia/Kolkata')

### Ex:
`UPDATE database_name.table_name `
 <br> `SET` </br>
      `database_name.table_name.column_name = CONVERT_TZ(NOW(), 'UTC', 'Asia/Kolkata')`
  <br> `WHERE` </br>
      `database_name.table_name.`id` IN ('1','2','3','.....')`

This will set the column to the current date and time in the Asia/Kolkata time zone.

Note that you may need to adjust the syntax of the SET statement depending on the context in which it is being used, such as whether it is part of an UPDATE or INSERT statement.
