# Chapter #5 Google Apps Script with Google Forms

### Solution 1

```javascript
function formResponse(e) {
  var results = e.namedValues;
  console.log(results);
}
```

```javascript
function formResponse(e) {
  var results = e.namedValues;
  console.log('Form submission received:');
  
  for (var key in results) {
    if (results.hasOwnProperty(key)) {
      console.log(key + ': ' + results[key]);
    }
  }
}
```
### Solution 2

```javascript
function onFormSubmit(event) {

  record_array = []

  var form = FormApp.openById(''); // Form ID
  var formResponses = form.getResponses();
  var formCount = formResponses.length;

  var formResponse = formResponses[formCount - 1];
  var itemResponses = formResponse.getItemResponses();

  for (var j = 0; j < itemResponses.length; j++) {
  var itemResponse = itemResponses[j];
    var title = itemResponse.getItem().getTitle();
    var answer = itemResponse.getResponse();

    Logger.log(title);
    Logger.log(answer);

    record_array.push(answer);
  }
   
  AddRecord(record_array[0], record_array[1], record_array[2]);

}

function AddRecord(first_name, last_name, color) {
  var url = '';   //URL OF GOOGLE SHEET;
  var ss= SpreadsheetApp.openByUrl(url);
  var dataSheet = ss.getSheetByName("Sheet1");
  dataSheet.appendRow([first_name, last_name, color, new Date()]);
}
```



### Triggers set up

![Add Trigger](AddTrigger.png)



# [Chapter#6](Chapter%236.md) - Google Apps Script with Google Drive