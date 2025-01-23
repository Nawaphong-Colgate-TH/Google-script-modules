# updateDataValue Function

## Description

The `updateDataValu`e function updates specific cell values in a Google Sheets document based on a given identifier. It searches for a row that matches the provided `detailId` from the input object and updates several columns such as the update timestamp, the user making the update, and status information. This function is useful for maintaining and managing dynamic data records, allowing for modifications to existing entries.

## Function Signature

```javascript
function updateDataValue(formObject) {
  initSpreadSheet();
  const sheet = dataSheet;
  const lastRow = sheet.getLastRow();
  const user = Session.getActiveUser().getEmail();

  const dataId = formObject.detailId;

  for (let i = 2; i <= lastRow; i++) {
    let curId = sheet.getRange(i, idColNum).getValue();
    if (curId == dataId) {
      sheet.getRange(i, updatedAtColNum).setValue(new Date());
      sheet.getRange(i, updatedByColNum).setValue(user);
      sheet.getRange(i, statusByColNum).setValue(formObject.status);
      break;
    }
  }

  return "SUCCESS";
}
```

## Usage

This function is typically used in systems that require updating data entries based on user-triggered actions, such as form submissions or internal record modifications. It focuses on updating specific attributes of a data entry efficiently.

## Parameters

`formObject` (object): Contains details about the data entry to update. It must include at least:
    - `detailId`: The unique identifier of the data entry to update.
    - `status`: The new status to apply to the data entry.

## Examples

Here is an example of how you might use the `updateDataValue` function:
```javascript
// Assumed formObject structure
const formObject = {
  detailId: '12345',  // The ID of the entry to update
  status: 'Completed' // The new status of the entry
};

// Call updateDataValue to modify the entry in the sheet
const updateStatus = updateDataValue(formObject);
Logger.log("Update status: " + updateStatus);
```

## Notes

- **Column Indices**: Ensure that `idColNum`, `updatedAtColNum`, `updatedByColNum`, and `statusByColNum` are correctly defined variables with indices matching the sheet's structure.
- **Sheet Initialization**: The `initSpreadSheet` function should have set up the `dataSheet` effectively to represent the desired sheet.
- **Data Security**: Confirm that handling of user data adheres to privacy and data management guidelines.
- **Error Handling**: Consider adding error handling for scenarios where the `detailId` does not exist in the sheet or other potential errors, improving robustness.
- **Indexing**: The loop starts from the second row assuming the first is a header row; adjust as needed for your data structure.
