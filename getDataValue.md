# getDataValue Function

## Description

The `getDataValue` function retrieves data rows from a Google Sheets document that match a specified dataId. This function filters and formats the data into objects based on headers for easy use in applications. It provides a structured way to manipulate and query data from large datasets within Google Sheets.

## Function Signature

```javascript
function getDataValue(dataId) {
  initSpreadSheet();
  const sheet = dataSheet;
  const data = sheet.getDataRange().getValues();

  // Extract headers
  const headers = data[0]; // Use the first row as headers
  const idCol = 6; 

  // Filter data for matching dataId
  const matchingRows = data.slice(1).filter(row => row[idCol] === dataId);

  // Format matched data as objects
  const tableData = matchingRows.map(row => {
    const obj = {};
    headers.forEach((header, index) => {
      if (header === 'createdAt' || header === 'timestamp' || header === 'updatedAt') {
        obj[header] = row[index] ? Utilities.formatDate(new Date(row[index]), "GMT+7", "dd/MM/yyyy HH:mm:ss") : row[index];
      } else if (header === 'image') {
        obj[header] = reUrlImage(row[index]);
      } else if (header === 'Start Date' || header === 'Due Date' || header === 'last comments date') {
        if (row[index]) {
          obj[header] = Utilities.formatDate(row[index], "GMT+7", "dd/MM/yyyy");
        } else {
          obj[header] = row[index];
        }
      } else {
        obj[header] = row[index];
      }
    });
    return obj;
  });

  return tableData;
}
```

## Usage

This function is useful for applications that need to extract and work with structured data from spreadsheets. By converting data rows into objects with named properties, it simplifies data handling and enhances readability within applications.

## Parameters

- `dataId` (string or number): The unique identifier used to filter rows. It should match the value in the specified identifier column to retrieve relevant data.

## Examples

Here is an example illustrating the use of the `getDataValue` function:
```javascript
// Example usage of getDataValue
const dataId = '12345';  // Replace with an actual identifier value

// Retrieve and log data entries corresponding to the specified dataId
const dataEntries = getDataValue(dataId);
Logger.log(dataEntries);
```
This example retrieves and logs all data entries that match the given `dataId`.

## Notes

- **Initialization**: Ensure `initSpreadSheet` correctly initializes the `dataSheet` variable to represent the appropriate sheet.
- **Column Indices**: `idCol` should be set to the index of the column containing the identifier used for matching (indexed from zero).
- **Date Formatting**: Dates are formatted using specified patterns to standardize their appearance. Adjust formats as necessary for your application requirements.
- **Additional Functions**: The function uses `reUrlImage` for converting image URLs, which should be defined elsewhere in your script.
- **Header Integrity**: It assumes the first row of the sheet comprises headers, which it uses to map column indices to object properties.
