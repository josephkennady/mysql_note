

```
function connectTowwwMySQL() {
  // Get the spreadsheet and sheet objects.
  var spreadsheet = SpreadsheetApp.getActiveSpreadsheet();
  var sheet = spreadsheet.getSheets()[1];

  // Create a new JDBC connection object.
  var connection = Jdbc.getConnection("jdbc:mysql://localhost:3306/mydb", "root", "password");

  // Execute the SQL query.
  var statement = connection.createStatement();
  var resultSet = statement.executeQuery("SELECT * FROM users LIMIT 20");

  // Get the starting row index
  var startRowIndex = sheet.getLastRow() + 1;

  // Add column headers
  var headers = [];
  var metaData = resultSet.getMetaData();
  for (var i = 1; i <= metaData.getColumnCount(); i++) {
    headers.push(metaData.getColumnName(i));
  }
  sheet.getRange(startRowIndex, 1, 1, headers.length).setValues([headers]);
  startRowIndex++;

  // Iterate over the results and add them to the sheet.
  while (resultSet.next()) {
    var rowData = [];
    for (var i = 1; i <= metaData.getColumnCount(); i++) {
      rowData.push(resultSet.getString(i));
    }
    sheet.getRange(startRowIndex, 1, 1, rowData.length).setValues([rowData]);
    startRowIndex++;
  }

  // Close the connection.
  resultSet.close();
  statement.close();
  connection.close();
}

```
