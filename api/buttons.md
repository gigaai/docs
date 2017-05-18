# Buttons
---

## Buttons Group
Buttons group is a text with set of 1-3 buttons. Each button can either open a URL, or make a back-end call to your webhook via `messaging_postbacks` event.

**Example**
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

**Fields**
- `text`: UTF-8-encoded text of up to 640 characters that appears above buttons group.
- `buttons`: Set of 1-3 buttons that appear as call-to-actions.

## URL Button
The Web URL button can be used to redirect leads to an URL, or open an URL in the in-app browser. This button can be used with the Buttons Group, List and Generic Templates. Like above example:

```
...
'buttons' => [
    [
        'type' => 'web_url',
        'title' => 'Show Website',
        'url' => 'https://giga.ai/',
    ],
    ...
]
...
```
**Fields**
- `type` ***(required)***: Should be `web_url`.
- `title` ***(required)***: Button title.
- `url` ***(required)***: The URL to redirect or open webview.
- `webview_height_ratio`: Height of the webview. Can be `compact`, `tall`, or `full`. Default `full`.
- `messenger_extensions`: `true` if using Messenger Extension.
- `fallback_url`: The URL to use on clients that don't support Messenger Extensions. If this is not defined, the url will be used as the fallback. It may only be specified if messenger_extensions is true. Must use HTTPS protocol.
- `webview_share_button`: Set to hide to disable the share button in the Webview (for sensitive info). This does not affect any shares initiated by the developer using Extensions.

## Postback Button
Sometimes, you'll want to let leads click on the button and response instead of redirect, in that case, we'll use Postback button.

```
...
'buttons' => [
    [
        'type' => 'web_url',
        'title' => 'Show Website',
        'url' => 'https://giga.ai/',
    ],
    ...
]
...
```