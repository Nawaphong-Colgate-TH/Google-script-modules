# doGet Function

## Description
The `doGet` function handles incoming HTTP GET requests for a web application built with Google Apps Script. It determines which HTML page template to serve based on the requested path. If the path corresponds to a valid page, it serves that page; otherwise, it defaults to serving the 'Index' page. The function also ensures the rendered page is responsive and configurable for embedding.
Function Signature

## Function Signature

```javascript
function doGet(event) {
  const validPages = ['detail', 'timeline', 'lists'];
  const pathInfo = event.pathInfo;
  
  // Default page is 'Index', update only if pathInfo is valid
  const page = validPages.includes(pathInfo) ? pathInfo : 'Index';
  
  // Create and evaluate the HTML template based on the page
  const html = HtmlService.createTemplateFromFile(page).evaluate();
  const htmlOutput = HtmlService.createHtmlOutput(html);
  
  // Add meta tag for responsive design
  htmlOutput.addMetaTag('viewport', 'width=device-width, initial-scale=1');
  
  // Allow embedding of the page (optional, based on your security needs)
  htmlOutput.setXFrameOptionsMode(HtmlService.XFrameOptionsMode.ALLOWALL);
  
  return htmlOutput;
}
```

## Usage

This function is useful for serving different web pages from a Google Apps Script project based on the requested URL path. It provides a flexible way to manage multiple views or sections of a web application.

## Parameters

- `event` (object): The event parameter containing data about the HTTP request, such as the pathInfo that indicates which page is requested.


