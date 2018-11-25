# Thread Settings
---
> Configure the Thread Settings on Messenger to improve the user-experience of your integration. These settings apply to each page individually.


## Greeting Text
You can set a greeting for new conversations. This can be used to communicate your bot's functionality.

![Greeting Text](https://scontent-hkg3-1.xx.fbcdn.net/t39.2365-6/13509175_122152928211838_1175374788_n.png)

> The Greeting Text is only rendered the first time the user interacts with a the Page on Messenger.

To set your Messsenger Greeting text, the easiest way is go to the 'Messaging' tab in your Page settings.

You can also configure Greeting text by go to edit your `/giga-messenger-bot/config.php`, set your Greeting Text under `greeting_text` section and go to `https://domain.com/giga-messenger-bot/public/?giga_action=updateGreetingText`

## Get Started Button
When the Get Started button is tapped, you can send a text message or a Structured Message, containing images and buttons.

The image below shows how the Get Started button can be used to introduce your bot experience and start your user journey.

![Get Started Button](https://scontent-hkg3-1.xx.fbcdn.net/t39.2365-6/13509249_1759503700982612_770421812_n.png)

> The Get Started button and Greeting text only appears for new conversations.

### Creating Get Started Button: 

Just go to `https://domain.com/giga-messenger-bot/public/?giga_action=updateGetStartedButton`

### Handling Get Started Button:
Simply answer the GIGA_GET_STARTED_PAYLOAD postback event, like so:

```
$bot->answer('payload:GIGA_GET_STARTED_PAYLOAD', 'Hi [first_name]!, welcome to our page');
```

### Removing Get Started Button:
- Open `/giga-messenger-bot/config.php`, then remove `get_started_button_payload` section or simply set its value to empty string.
- Go to `https://domain.com/giga-messenger-bot/public/?giga_action=updateGetStartedButton`

## Persistent Menu

The Persistent Menu is a menu that is always available to the user. This menu should contain top-level actions that users can enact at any point. Having a persistent menu easily communicates the basic capabilities of your bot for first-time and returning users.
The menu can be invoked by a user, by tapping on the 3-caret icon on the left of the composer.

![Persistent Menu](https://scontent-hkg3-1.xx.fbcdn.net/t39.2365-6/13509228_581512925362726_878211705_n.png)

### Creating Persistent Menu

- Open `/giga-messenger-bot/config.php`, in the `persistent_menu` section, enter menu items.
- Go to `https://domain.com/giga-messenger-bot/public/?giga_action=updatePersistentMenu`

Menu items example:

```
'persistent_menu' => [
  [
      "type" => "postback",
      "title" => "Help",
      "payload" => "DEVELOPER_DEFINED_PAYLOAD_FOR_HELP"
  ],
  [
      "type" => "postback",
      "title" => "Start a New Order",
      "payload" => "DEVELOPER_DEFINED_PAYLOAD_FOR_START_ORDER"
  ],
  [
      "type" => "web_url",
      "title" => "View Website",
      "url" => "http://petersapparel.parseapp.com/"
  ]
];
```

#### Menu Item Object
Parameter Name | Description | Type | Required?
--- | --- | --- | ---
`type` | `web_url` or `postback` | String | Y
`title` | Menu item title. Limit 30 characters. | String | Y
`url` | For web_url buttons, this URL is opened in a mobile browser when the button is tapped | String | Y, if type is `web_url`
`payload` | For postback buttons, this data will be sent back to you via webhook. Limit 1000 characters | String | Y, if type is `postback`

### Handling Postback Event
Simply handle it like normal postback using `$bot->answer('payload:...')` method.

### Deleting Persistent Menu
- Open `/giga-messenger-bot/config.php`, then remove `persistent_menu` section or simply set its value to empty string.
- Go to `https://domain.com/giga-messenger-bot/public/?giga_action=updatePersistentMenu`
