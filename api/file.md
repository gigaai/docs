# File
---
In case you send a URL which doesn't have Image, Audio, or Video extension, it will send File attachment.

```
// Bot sends file when people asked for it
$bot->answers('file', 'http://www.pdf995.com/samples/pdf.pdf');
```

## Force Detection
Sometimes, you'll want to send Image, Audio, or Video as File. And sometimes, your URL doesn't contains file extension, so you'll want to tell the bot which exactly media type to send to user. Just prepend your extension before your URL. For example:

```
// Send Image as File
$bot->answers('send image as file', 'file:http://www.gstatic.com/webp/gallery/1.jpg');

// Send URL which doesn't have image extension as image
$bot->answers('send image', 'image:https://placeholdit.imgix.net/~text?txtsize=33&txt=350%C3%97150&w=350&h=150')
```