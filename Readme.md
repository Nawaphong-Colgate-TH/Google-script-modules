# Google Apps Script - Beginner 101


```javascript
function myFunction() {
  Logger.log(SpreadsheetApp.getActiveSpreadsheet().getUrl());
}


function myFunction() {
  var ss = SpreadsheetApp.getActive();
  Logger.log(ss.getName());

  var url = ss.getUrl();
  Logger.log(url);

  var id = ss.getId();
  Logger.log(id);

  var sheet_name = ss.getSheetName();
  Logger.log(sheet_name);
}

```

## Creating new file

```javascript
function myFunction() {
  var new_spreadsheet = SpreadsheetApp.create("new_file");
  Logger.log(new_spreadsheet);
}
```

## Accessing a spreadsheet

```javascript
function myFunction() {
  var ss = SpreadsheetApp.getActive();
  // var ss = SpreadsheetApp.getActiveSpreadsheet();
  // var ss = SpreadsheetApp.openByUrl(url);
  // var ss = SpreadsheetApp.openById(id);

  Logger.log(ss.getName());
}
```

## Accessing a sheet

```javascript
function myFunction() {
  var ss = SpreadsheetApp.getActiveSpreadsheet();
  // var sheet = ss.getActiveSheet();
  // var sheet = ss.getSheetByName('Sheet2');
  // var sheets = ss.getSheets();

  Logger.log(sheet);
}
```

## Accessing and Modifying Cell Values in Google Sheets using Google Apps Script


- `getRange(row, column)`
```javascript
let sheet;

function initial() {
  // Access the active spreadsheet
  var spreadsheet = SpreadsheetApp.getActiveSpreadsheet();
  // Get the sheet named 'Sheet1' from the spreadsheet
  sheet = spreadsheet.getSheetByName('Sheet1');
  // Log the name of the sheet to the console
  console.log(sheet.getName());
}

function myFunction() {
  initial();

  // Define the range for a specific cell in the sheet (row 1, column 1)
  var cellRange = sheet.getRange(1, 1);

  // Get the cell's current value
  var currentValue = cellRange.getValue();
  
  // Log the current value of the cell to the console
  console.log(currentValue);

  // Set a new value for the cell
  cellRange.setValue(10);
}
```