# Chapter #6 Google Apps Script with Google Drive


```javascript
let sheet;

function initial() {
  // Access the active spreadsheet
  var spreadsheet = SpreadsheetApp.getActiveSpreadsheet();
  // Get the sheet named 'Sheet1' from the spreadsheet
  sheet = spreadsheet.getSheetByName('Chapter#6');
  // Log the name of the sheet to the console
  console.log(sheet.getName());
}
```

```javascript
function generateAndSaveQRCodeForSheet() {


  // Define the folder where the QR codes will be saved
  var folderId = ''; // Replace with your folder ID
  var folder = DriveApp.getFolderById(folderId);

  // Get the data from column D (e.g., D2:D10)
  var range = sheet.getRange('A2:A');  // Adjust range as needed
  // var range = sheet.getRange(2, 1, sheet.getLastRow()-1, 1);
  var values = range.getValues();

  // console.log(values)

  // for (var i = 0; i < values.length; i++) {
  //     var input = values[i][0];
  //     // console.log('input ::: >>> ', input)
  //     if (input) {  // Check that there is text to process
  //       var qrCodeUrl = 'https://api.qrserver.com/v1/create-qr-code/?size=300x300&data=' + encodeURIComponent(input);

  //       // console.log("qrCodeUrl :::: >>>> ", qrCodeUrl)

  //       // Define the filename for the QR code
  //       var fileName = encodeURIComponent(input) + '.png';

  //       // // Check if a file with this name already exists in the folder
  //       // var existingFiles = folder.getFilesByName(fileName);
  //       // while (existingFiles.hasNext()) {
  //       //   var existingFile = existingFiles.next();
  //       //   existingFile.setTrashed(true); // Move existing file to Trash
  //       // }

  //       // // Fetch the QR code image
  //       // var imageBlob = UrlFetchApp.fetch(qrCodeUrl).getBlob();
        
  //       // // Create a new file in the specified folder
  //       // var newFile = folder.createFile(imageBlob);
  //       // newFile.setName(fileName);

  //       // // Save the file URL in column B
  //       // var fileUrl = newFile.getUrl();
  //       // sheet.getRange(i + 2, 2).setValue(fileUrl); // +2 assumes data starts from row 2, adjust as needed

  //       // // Use the IMAGE function to display the QR code in column C
  //       // var imageFormula = '=IMAGE("' + reUrlImage(fileUrl) + '")';
  //       // sheet.getRange(i + 2, 3).setFormula(imageFormula); // Displays the image in column C


  //     }
  // }
}
```


```javascript
function reUrlImage(url) {
  const id = extractFileIdFromUrl(url);
  if (id) {
    // return "https://drive.google.com/thumbnail?id="+id;
    return "https://lh3.google.com/d/"+id;
  } 
  return url;
}
```

```javascript
function extractFileIdFromUrl(url) {
  const regex = /\/d\/([^/]+)\//;
  const matches = url.match(regex);
  return matches ? matches[1] : ''; // Return the ID or null if not matched
}
```

```javascript
function onOpen() {
  // สร้างอินสแตนซ์ของ UI ใน Spreadsheet
  let ui = SpreadsheetApp.getUi();
  // สร้างเมนูใหม่บนแถบเมนูของ Google Sheets
  ui.createMenu('Custom Scripts') // ตั้งชื่อเมนูว่า 'Custom Scripts'
    .addItem('Generate QR Codes', 'generateAndSaveQRCodeForSheet') // เพิ่มรายการย่อยในเมนู 'Custom Scripts' ชื่อว่า 'Generate QR Codes' ซึ่งจะเรียกใช้ฟังก์ชัน generateAndSaveQRCodeForSheet
    .addToUi(); // เพิ่มเมนูไปยัง UI จริง
}
```


# [Chapter#7](Chapter%237.md) - Google Apps Script with Google DocsDrive