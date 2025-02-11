# getActiveSpreadsheet

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

  var name = ss.getSheetName();
  Logger.log(name);
}

```
