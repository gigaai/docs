# Buttons

- [Buttons Group](#buttons-group)
- [URL Button](#url-button)
- [Postback Button](#postback-button)
    - [Handling Postback](#handling-postback)
- [Call Button](#call-button)
- [Share Button](#share-button)
- [Login Button](#login-button)
- [Logout Button](#logout-button)

---

<a name="buttons-group"></a>
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

<a name="url-button"></a>
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
- `webview_height_ratio`: Height of the webview. Can be `compact`, `tall`, or `full`.
- `messenger_extensions`: `true` if using Messenger Extension.
- `fallback_url`: The URL to use on clients that don't support Messenger Extensions. If this is not defined, the `url` will be used as the fallback. It may only be specified if messenger_extensions is true. Must use HTTPS protocol.
- `webview_share_button`: Set to hide to disable the share button in the Webview (for sensitive info). This does not affect any shares initiated by the developer using Extensions.

<a name="postback-button"></a>
## Postback Button
Sometimes, you'll want to let leads click on the button and response instead of redirect, in that case, we'll use Postback button.

```
...
'buttons' => [
    [
        'type' => 'postback',
        'title' => 'Start Chatting',
        'payload' => 'START_CHATTING_PAYLOAD'
    ]
    ...
]
...
```

**Fields**
- `type` ***(required)***: Should be `postback`
- `title` ***(required)***: Button title
- `payload` ***(required)***: Payload name, so we can use it to handle.

<a name="handling-postback"></a>
### Handling Postback (Click/Tap Event)
When people click on the Postback button, you'll want to handle that action. For example, send a message, save a data. Please check out [Handling Postback](/docs/api/handling-postback) guide.

<a name="call-button"></a>
## Call Button
Call Button is a quick way to make a phone call. It can be used with the Button Group or Generic Templates.

![Call Button](/images/call-button.png)

To create Call Button, just set `type` to `phone_number` and `payload` to the target phone number. For example:

```
...
'buttons' => [
    [
        'type'      => 'phone_number',
        'title'     => 'Better Call Saul',
        'payload'   => '+123456789'
    ]
]
...
```

<a name="share-button"></a>
## Share Button
Share Button enables people to share message bubbles with their contacts using a native share dialog in Messenger.
![Share Button](/images/messenger-share.png)
Messages that are shared display the page name and profile pic, indicating the origin of the message. 
This attribution can be tapped, enabling friends to start their own conversations from shared content.

```
...
'buttons' => [
    [
        'type' => 'element_share'
    ]            
]
...
```

**Fields**
- ***type*** (required): Should be `element_share`
- ***share_contents*** (optional): The message that you wish the recipient of the share to see, if it is different from the one this button is attached to. The format follows that used in Send API, but must be a generic template with up to one URL button.

Example with `share_contents`:
```
...
"buttons" =>  [
    [
        "type" =>  "element_share",
        "share_contents" =>  [ 
            "attachment" =>  [
                "type" =>  "template",
                "payload" =>  [
                    "template_type" =>  "generic",
                    "elements" =>  [
                        [
                            "title" =>  "I took Peter's 'Which Hat Are You?' Quiz",
                            "subtitle" =>  "My result =>  Fez",
                            "image_url" =>  "https://bot.peters-hats.com/img/hats/fez.jpg",
                            "default_action" =>  [
                            "type" =>  "web_url",
                            "url" =>  "https://m.me/petershats?ref=invited_by_24601"
                        ],
                        "buttons" =>  [
                                [
                                    "type" =>  "web_url",
                                    "url" =>  "https://m.me/petershats?ref=invited_by_24601", 
                                    "title" =>  "Take Quiz"
                                ]
                            ]
                        ]
                    ]
                ]
            ]
        ]
    ]
]
...
```

Caveats: 
- Only individual message bubbles can be shared.
- The Share Button can only be sent inside the Generic Template.
- If your message bubble has a URL Button that uses Messenger Extensions (without a fallback URL), then the behavior of postback and buy buttons will change. When the recipient taps on one of these buttons, they will start a new thread with the bot.
    - In the case of a URL Button using Messenger Extensions, the fallback URL will be opened if specified. Share, URL, and Phone Number buttons will behave normally.


<a name="login-button"></a>
## Log In Button
As the button name, when leads click on this button, it will open a window to let them login to your website. 

![Login Button](/images/login-button.png)

To create Log In button, just the button `type` to `account_link` and `url` to your login URL. Please note that this button doesn't have the `title` property.

By default, WordPress login URL is: https://your-website.com/wp-admin and Laravel login URL is https://your-website.com/login so you can just use that URL.

```
'buttons' => [
    [
        'type' => 'account_link',
        'url' => 'https://giga.ai/login'
    ]
]
```

<a name="logout-button"></a>
## Log Out Button
As the button name, when leads click on this button, it will logout your website.

To create Log Out button, just the button `type` to `account_unlink`

```
'buttons' => [
    [
        'type' => 'account_unlink'
    ]
]
```