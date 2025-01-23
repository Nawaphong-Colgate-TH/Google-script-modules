# getCustomUUID Function

## Description

The `getCustomUUID` function generates a custom UUID (Universally Unique Identifier) by utilizing the built-in `Utilities.getUuid()` method. It formats the UUID by removing the hyphens and truncating it to the first 12 characters.

## Function Signature

```javascript
function getCustomUUID() {
  let rawId = Utilities.getUuid().split('-').join("");
  rawId = rawId.slice(0, 12);
  return rawId;
}
```

## Usage

This function is useful when you need a lightweight, unique identifier for use within your application without conforming to the full length and format of a standard UUID.
```javascript
let customUUID = getCustomUUID();
console.log(customUUID); // Output: A unique 12-character string
```
