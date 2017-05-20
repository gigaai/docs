# Handling Postbacks
---
When people click on the `postback` button, Facebook will send a request to your server which contains the payload name. Back to this example:

```
$bot->answers('button', [
    'text' => 'What do you want to do next?',
    'buttons' => [
        [
            'type' => 'web_url',
            'title' => 'Show Website',
            'url' => 'https://giga.ai/',
        ],
        [
            'type' => 'postback',
            'title' => 'Start Chatting',
            'payload' => 'START_CHATTING_PAYLOAD'
        ]
    ]
]);
```

When people click on the Start Chatting button, it will send a request which contains `START_CHATTING_PAYLOAD` payload. To handle this, we'll use `$bot->answer()` method again.

**Example**

```
$bot->answers('payload:START_CHATTING_PAYLOAD', 'You are talking with Saul Goodman');
```

Just like [Handling Text](/docs/api/handling-text), you can use Text Matching feature also.

```
$bot->answers('payload:USER_CLICKED_%_BUTTON', 'You have clicked on the button'); 
```