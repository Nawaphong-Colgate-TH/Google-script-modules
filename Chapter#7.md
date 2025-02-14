# Chapter #6 Google Apps Script with Google Docs

```javascript
function autoFillGoogleDocFromForm(record_object) {
  var sku = '12312332133213';
  var date = '2025-02-14';
  var line = 'M (Small Tube)';
  var shift = '1';

  // var sku = record_object['SKU (Stock Keeping Unit)'];
  // var date = record_object['วันที่ผลิต (MFG date)'];
  // var line = record_object['ไลน์ผลิต (Line)'];
  // var shift = record_object['กะ (Shift) '];

  

  // Get the template file by ID
  var templateFile = DriveApp.getFileById('');

  // Get the destination folder by ID
  var templateResponseFolder = DriveApp.getFolderById('');

  // Make a copy of the template in the specified folder
  var copy = templateFile.makeCopy(sku+date+line, templateResponseFolder); 

  // Open the newly created document
  var doc = DocumentApp.openById(copy.getId()); 

  // Get the body of the document
  var body = doc.getBody(); 

  // Replace placeholders with actual values
  body.replaceText('{{sku}}', sku); 
  body.replaceText('{{date}}', date);  
  body.replaceText('{{line}}', line); 
  body.replaceText('{{shift}}', shift); 
  
  // Save and close the document
  doc.saveAndClose(); 
}

```

### test

```javascript
function test() {
  autoFillGoogleDocFromForm();
}
```

```javascript
function formResponse(event) {

  let record_object = {};

  var form = FormApp.openById('-FnbN0'); // Form ID
  var formResponses = form.getResponses();
  var formCount = formResponses.length;

  var formResponse = formResponses[formCount - 1];
  var itemResponses = formResponse.getItemResponses();

  for (var j = 0; j < itemResponses.length; j++) {
  var itemResponse = itemResponses[j];
    var title = itemResponse.getItem().getTitle();
    var answer = itemResponse.getResponse();

    // console.log(title);
    // console.log(answer);
    record_object[title] = answer;

  }
   
   console.log(record_object)

   autoFillGoogleDocFromForm(record_object)

}
```
