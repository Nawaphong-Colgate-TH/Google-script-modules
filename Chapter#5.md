# Chapter #5 Google Apps Script with Google Forms

```javascript
/**
 * Handles form responses by logging each response in detail.
 * @param {Object} e - The event object containing form response data.
 */
function formResponse(e) {
  var results = e.namedValues;
  console.log('Form submission received:');
  
  for (var key in results) {
    if (results.hasOwnProperty(key)) {
      console.log(key + ': ' + results[key]);
    }
  }
}