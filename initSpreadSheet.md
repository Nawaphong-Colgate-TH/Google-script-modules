# initSpreadSheet Function

## Description

The `initSpreadSheet` function initializes a connection to a Google Sheets spreadsheet and retrieves a specific sheet within it. This setup function is essential for scripts that need to manipulate data within a particular sheet of a Google Sheets document.

## Function Signature

```javascript
function initSpreadSheet() {
  // Open the spreadsheet using the specified ID
  ss = SpreadsheetApp.openById(sheetId);
  // Attempt to get the specified sheet by name
  dataSheet = ss.getSheetByName(sheetName);
}
```

## Usage

This function is used to establish global references to a spreadsheet and a specific sheet, allowing other functions within the script to perform operations such as reading or writing data without re-initializing the spreadsheet object each time.

## Parameters

The function does not take any parameters but relies on two global variables:
  - `sheetId` (string): The ID of the Google Sheets spreadsheet. Replace 'xxxx' with your actual spreadsheet ID.
  - `sheetName` (string): The name of the specific sheet within the spreadsheet. Replace 'xxxx' with your actual sheet name.
    
## Examples
```javascript
// Set your specific spreadsheet ID and sheet name
const sheetId = 'your-spreadsheet-id';
const sheetName = 'your-sheet-name';

// Initialize the spreadsheet and sheet
initSpreadSheet();

// Example of reading the first cell's content
function readFirstCell() {
  const firstCellValue = dataSheet.getRange("A1").getValue();
  Logger.log(firstCellValue);
}
```
In this example, after initializing, you can directly use `dataSheet` to interact with your chosen sheet.

## Notes

The global variables `sheetId` and `sheetName` must be set to valid values before calling initSpreadSheet.
It is important to ensure that the Google Sheets ID and the sheet name are correct and that you have appropriate permissions to access the sheet.
The function sets up global variables (`ss` and `dataSheet`) which are required for subsequent Google Sheets API operations within the script.
