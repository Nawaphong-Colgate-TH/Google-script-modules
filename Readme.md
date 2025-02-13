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

## สร้างไฟล์ใหม่

```javascript
function myFunction() {
  var new_spreadsheet = SpreadsheetApp.create("new_file");
  Logger.log(new_spreadsheet);
}
```

## เปิดไฟล์

```javascript
function myFunction() {
  var ss = SpreadsheetApp.getActive();
  // var ss = SpreadsheetApp.getActiveSpreadsheet();
  // var ss = SpreadsheetApp.openByUrl(url);
  // var ss = SpreadsheetApp.openById(id);

  Logger.log(ss.getName());
}
```

## sheet

```javascript
function myFunction() {
  var ss = SpreadsheetApp.getActiveSpreadsheet();
  // var sheet = ss.getActiveSheet();
  // var sheet = ss.getSheetByName('Sheet2');
  // var sheets = ss.getSheets();

  Logger.log(sheet);
}
```
