# getCustomUUID Function

## Description

The `getCustomUUID` function generates a custom UUID (Universally Unique Identifier) by utilizing the built-in `Utilities.getUuid()` method. It formats the UUID by removing the hyphens and allows the caller to specify the number of characters to truncate, providing flexibility in the length of the identifier.

## Function Signature

```javascript
function getCustomUUID(characterCount) {
  let rawId = Utilities.getUuid().split('-').join("");
  rawId = rawId.slice(0, characterCount);
  return rawId;
}
```

## Usage

This function is useful when you need a lightweight, unique identifier for use within your application without conforming to the full length and format of a standard UUID.

### Parameters

- `characterCount` (number): The number of characters to truncate the UUID to. If not specified, the function will return the full UUID without hyphens.

### Examples

```javascript
// Generate a custom UUID with the default length (full UUID without hyphens)
let customUUID = getCustomUUID();
console.log(customUUID); // Output: A unique 32-character string

// Generate a custom UUID with a specified length
let customUUID10 = getCustomUUID(10);
console.log(customUUID10); // Output: A unique 10-character string

// Generate a custom UUID with a different specified length
let customUUID20 = getCustomUUID(20);
console.log(customUUID20); // Output: A unique 20-character string
