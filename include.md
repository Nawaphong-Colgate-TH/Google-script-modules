# include Function

## Description

The `include` function facilitates the inclusion of additional HTML files into a primary HTML template within a Google Apps Script project. It allows for modular code organization by enabling the reuse of common components or templates across multiple pages.

## Function Signature

```javascript
function include(fileName) {
  return HtmlService.createHtmlOutputFromFile(fileName).getContent();
}
```

## Usage

This function is particularly useful when you want to insert HTML files, such as headers or footers, into a main HTML file, promoting DRY (Don't Repeat Yourself) principles in web development with Google Apps Script.

## Parameters

- `fileName` (string): The name of the HTML file to include. This file should be part of the project files in Google Apps Script.

## Examples

```html
<!-- main.html -->
<!DOCTYPE html>
<html>
  <head>
    <base target="_top">
    <!-- Include header.html -->
    <?!= include('header') ?>
  </head>
  <body>
    <h1>Welcome to My App</h1>
    <!-- Include footer.html -->
    <?!= include('footer') ?>
  </body>
</html>
```
In this example, `header.html` and `footer.html` are HTML files within the same Google Apps Script project, which are included in main.html.

## Notes

Ensure that the `fileName` parameter corresponds to an existing HTML file in your Google Apps Script project.
The function returns the content of the HTML file as a string, which can be inserted into other HTML templates using `<?!= include('fileName') ?>`.
Helps in managing and organizing HTML content efficiently, especially in larger projects where reusable components are beneficial.
