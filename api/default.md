# Default Message
---
In the conversation, people can send any messages, of course, your bot cannot understand all messages. In that case, we'll need to use fallback message to answer. To do so: use `default:` as the first parameter.

```
$bot->answers("default:", "Sorry, I don't understand!");
```