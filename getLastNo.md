# getLastNo Function

## Description

The `getLastNo` function retrieves the last number from a specified column in a Google Sheets document. If the last entry in the column is 'NO', it returns 1. Otherwise, it increments the last number by 1 and returns the result.

## Function Signature

```javascript
function getLastNo(sheet, noColNum) {
  const lastRow = sheet.getLastRow();
  const lastNo = sheet.getRange(lastRow, noColNum).getValue();
  var result;
  if (lastNo === 'NO') {
    result = 1;
  } else {
    result = lastNo + 1;
  }
  return result;
}
```
## Usage

This function is useful when you need to generate the next number in a sequence stored in a Google Sheets column.

## Parameters

- `sheet` (object): The Google Sheets object representing the sheet from which to retrieve the last number.
- `noColNum` (number): The column number where the numbers are stored.

## Examples

```javascript
const sheet = SpreadsheetApp.getActiveSpreadsheet().getSheetByName('Sheet1');
const nextNumber = getLastNo(sheet, 2); // Assuming the numbers are in the second column
Logger.log(nextNumber); // Output: The next number in the sequence
```

## Notes

- Ensure that `noColNum` is defined and points to the correct column number where the numbers are stored.
- This function assumes that the column contains either numeric values or the string 'NO'.

