# Chapter #2 Function in Google Apps Script

```javascript
// Define the main function, which currently does not perform any operations
function myFunction() {
  // Placeholder for future code or operations
}


// Define a function that takes two parameters, a and b, and returns their sum
function sum(a, b) {
  // Return the result of adding a and b
  return a + b;
}

function test() {
  var result = sum(1,2); 
  console.log(result);
}
```

## What is Array? [[ref.](https://www.geeksforgeeks.org/what-is-array/)]

Array is a linear data structure where all elements are arranged sequentially. It is a collection of elements of same data type stored at contiguous memory locations. 

[![What is Array](https://media.geeksforgeeks.org/wp-content/uploads/20240410101419/Getting-Started-with-Array-Data-Structure.webp)](https://www.geeksforgeeks.org/what-is-array/)

### 2-Dimensionnal Arrays [[ref.](https://www.digitalocean.com/community/tutorials/two-dimensional-array-in-c-plus-plus)]

[![What is Array 2D](https://journaldev.nyc3.cdn.digitaloceanspaces.com/2020/03/2D-array-representation.png)](https://www.digitalocean.com/community/tutorials/two-dimensional-array-in-c-plus-plus)


```javascript
function myFunction() {
  initial();
  var cellRange = sheet.getRange("A1:C3");
  var currentValues = cellRange.getValues();

  console.log(currentValues);
  console.log(currentValues[0]);
  console.log(currentValues[0][1]);
}
```

### For-Loop

```javascript
function myFunction() {
  initial();
  var cellRange = sheet.getRange("A1:C3");
  var currentValues = cellRange.getValues();
  console.log(currentValues);
  console.log('##### solution 1');

  for ( let i of currentValues) {
    console.log(i)
  }
  console.log('##### solution 2');
  for (let i=0 ; i < currentValues.length; i++) {
    console.log(currentValues[i])
  }
  console.log('#####');
  // 

  for (let i=0 ; i < currentValues.length; i++) {
    for (let j=0 ; j < currentValues[i].length; j++) {
      console.log(`row [${i}], col [${j}] : ${currentValues[i][j]}`)
    }
  }
}
```

# [Chapter#3](Chapter%233.md) - Google Apps Script with Google Gmail