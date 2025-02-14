# Chapter #4 Google Apps Script with Google Chat

# [Link](https://docs.google.com/document/d/10jY5UDjfqTNGCcpqnB4l9iAOJIyejKMoS3Cdie569Ok/edit?tab=t.0) - วิธีสร้าง webhook Google Chat  สำหรับ Alert


### Example

`https://chat.googleapis.com/v1/spaces/AAAAXXXX/messages?key=AIzaSyDdI0hCZtE6vySjMm-XXXXXXXX&token=wQU0Sqd_Qp0QXXROHCXL-XXXXXXX`

```javascript
const secret = {
  url: "https://chat.googleapis.com/v1/spaces/AAAAXXXX/messages",
  key: "AIzaSyDdI0hCZtE6vySjMm-XXXXXXXX",
  token: "wQU0Sqd_Qp0QXXROHCXL-XXXXXXX",
};


function webhook() {
  const url = `${secret.url}?key=${secret.key}&token=${secret.token}`
  const options = {
    "method": "post",
    "headers": {"Content-Type": "application/json; charset=UTF-8"},
    "payload": JSON.stringify(content())
  };
  const response = UrlFetchApp.fetch(url, options);
  console.log(response.getContentText());
}

function content() {
  return {"text": "Hello from Apps Script!"}
}

```

### Card Example

```javascript
function content() {
  return {
    cardsV2: [
      {
        card: {
        "header": {
          "title": "D&A Training for new comer (S&C)",
          "subtitle": "Google Apps Script 101",
          "imageUrl": "https://lh3.google.com/d/1S8NK9WnEg1V7flNQMlH4A41CrcgtljWT",
          "imageType": "CIRCLE"
        }
      }
      }
    ]
  }
}
```

`https://lh3.google.com/d/<image_id>`

[Link](https://developers.google.com/workspace/chat/api/reference/rest/v1/cards) - Cards v2


# [Chapter#5](Chapter%235.md) - Google Apps Script with Google Forms