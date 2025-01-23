# getConfig Function

## Description

The `getConfig` function retrieves configuration data from a specified sheet within a Google Sheets document. It initializes the spreadsheet connection, selects the appropriate sheet based on the provided configuration name, and returns the data as an array of objects where each object represents a row in the sheet with its headers as keys.

## Function Signature

```javascript
function getConfig(configName) {
  // Assumes initialization is required only once globally.
  initSpreadSheet();

  let data;

  // Use a more structured approach to retrieve the sheet.
  const sheets = {
    'Location': locationSheet,
    'Area': areaSheet,
    'SubArea': subAreaSheet,
    'Staff': staffSheet,
    'Auditor': auditorSheet,
    'Setting': settingSheet,
    'Activity': activitySheet,
    'Permission': permissionSheet,
    'Data-RPL': dataRPLSheet,
    'Data-GDC': dataGDCSheet
  };

  let sheet = sheets[configName] || dataGDCSheet; // Default to dataGDCSheet
  data = sheet.getDataRange().getValues();

  if (data.length === 0) return []; // Return empty if no data

  const headers = data.shift(); // Consider data always has headers
  const lastCommentDateIndex = headers.indexOf('last comments date');
  const results = data.map(row => {
    const obj = {};
    row.forEach((cell, index) => {
      if (index === lastCommentDateIndex && cell) {
        obj[headers[index]] = Utilities.formatDate(cell, "GMT+7", "dd/MM/yyyy");
      } else {
        obj[headers[index]] = cell;
      }
    });
    return obj;
  });

  return results;
}
```

## Usage

This function is essential for dynamically retrieving configuration data from various predefined sheets in a Google Sheets document. It maps the data to an easy-to-use object format, allowing for seamless integration into applications that require structured data handling.

## Parameters

- `configName` (string): The name of the configuration or dataset being requested. This corresponds to a key in the sheets mapping, aligning with a specific sheet object.
- 
## Examples

```javascript
// Initialize required global variables and sheet references before calling
initSpreadSheet();

// Retrieve configuration data for 'Staff'
const staffData = getConfig('Staff');
Logger.log(staffData);

// Output might look like: [{"Name":"John Doe", "Position":"Manager", ...}, ...]
```
In this example, data for the 'Staff' sheet is retrieved and logged, with each object representing a row of data from the sheet.

## Notes

Ensure that the `initSpreadSheet` function has been called to properly initialize all necessary global variables and sheet references.
The function assumes each sheet has a header row which maps to object keys in each returned data entry.
If no data is found in the sheet, the function returns an empty array.
It includes custom date formatting if the `last comments date` field is present.
