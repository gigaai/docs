# Image
---
In order to send image, just provide a Image URL instead of text. Giga AI will treat the URL as an image. Facebook supports JPG, PNG and GIF.

```
// Bot sends photo when people asked for it
$bot->answers('photo', 'http://www.gstatic.com/webp/gallery/1.jpg');
```