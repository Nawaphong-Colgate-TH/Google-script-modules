# Chapter #3 Google Apps Script with Google Gmail

```javascript
function sendEmailWithCC() {
  var recipient = "recipient@example.com"; // Replace with the recipient's email address
  var ccRecipient = "cc@example.com"; // Replace with the CC recipient's email address
  var subject = "Test Email with CC"; // Replace with your email subject
  var body = "Hello, this is a test email sent from Google Apps Script with CC."; // Replace with your email body text

  MailApp.sendEmail({
    to: recipient,
    cc: ccRecipient,
    subject: subject,
    body: body
  });
}
```

# [Chapter#4](Chapter%234.md) - Google Apps Script with Google Chat