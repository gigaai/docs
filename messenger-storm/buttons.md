#Buttons
- [Call Button](#call-button)
- [Share Button](#share-button)
- [Login Button](#login-button)
- [Logout Button](#logout-button)
- [Handling Postback](#handling-postback)

---

In the [Templates](/docs/wordpress/templates) reference, we've included buttons in Button Group, Generic, List, it works with [Persistent Menu](/docs/wordpress/thread-settings#persistent-menu) also.

<a name="web-url-button"></a>
### Web URL Button
The Web URL button can be used to redirect leads to an URL, or open an URL in the in-app browser.

To create URL button, set the button `type` to `web_url`, `url` to your URL and `title` for button title:
```
...
'buttons' => [
    [
        'type' => 'web_url',
        'url' => 'https://giga.ai',
        'title' => 'Go to Giga AI'
    ]
]
...
```

### Postback Button
Sometimes, you'll want to let leads click on the button and response instead of redirect, in that case, we'll use Postback button.

To create Postback button, set the button `type` to `postback`, `title` for button title, and `payload` to any payload name. We'll use payload name to handle. See [Handling Postback](#handling-postback) section for more detail:

```
'buttons' => [
    [
        'type' => 'postback',
        'title' => 'Bookmark Item',
        'payload' => 'DEVELOPER_DEFINED_PAYLOAD'
    ]
]
```

<a name="call-button"></a>
### Call Button
Call Button is a quick way to make a phone call. It can be used with the Button or Generic Templates.
![Call Button](https://scontent-hkg3-1.xx.fbcdn.net/t39.2365-6/14174889_175312432876430_128371202_n.png)

To create Call Button, just set type to `phone_number` and payload to the target phone number. For example:

```
...
'buttons' => [
    [
        'type'      => 'phone_number',
        'title'     => 'Call Saul Goodman',
        'payload'   => '+123456789'
    ]
]
...
```

<a name="share-button"></a>
### Share Button
Share Button enables people to share message bubbles with their contacts using a native share dialog in Messenger.
![Share Button](https://scontent-hkg3-1.xx.fbcdn.net/t39.2365-6/14235587_623632261149104_420720127_n.png)
Messages that are shared display the page name and profile pic, indicating the origin of the message. 
This attribution can be tapped, enabling friends to start their own conversations from shared content.
![Share Bubble](https://scontent-hkg3-1.xx.fbcdn.net/t39.2365-6/14130007_1097233913704658_67138787_n.png)

Notes: 
- Only individual message bubbles can be shared.
- If your message bubble has a URL Button using Messenger Extensions, Postback, Buy Button, the behavior of those buttons will change such that tapping on them will start a new thread with your bot. Share, URL (without Messenger Extensions) and Phone number buttons will behave normally.

The Share Button only works with the Generic Template. In the Send API, set the button type to `element_share`. This will generate a Share Button with title set as "Share".

```
...
'buttons' => [
    [
        'type' => 'element_share'
    ]            
]
...
```

<a name="login-button"></a>
### Log In Button
As the button name, when leads click on this button, it will open a window to let them login to your website. 

To create Log In button, just the button `type` to `account_link` and `url` to your login URL. Please note that this button doesn't have the `title` property.

```
'buttons' => [
    [
        'type' => 'account_link',
        'url' => 'https://giga.ai/authorize'
    ]
]
```

<a name="logout-button"></a>
### Log Out Button
As the button name, when leads click on this button, it will logout your website.

To create Log Out button, just the button `type` to `account_unlink`

```
'buttons' => [
    [
        'type' => 'account_unlink'
    ]
]
```

<a name="handling-postback"></a>
## Handling Postback Button (Click/Tap Event)
If user click on a `web_url` button, it will automatically redirect to that URL. Otherwise, to handle Click/Tap event on payload button. Just do the same as Text but prepend `payload:`

```
// When user clicked Heisenberg button which has USER_CLICKED_HEISENBERG_BUTTON payload
$bot->answer('payload:USER_CLICKED_HEISENBERG_BUTTON', 'You are Heisenberg?');
```