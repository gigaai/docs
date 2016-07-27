# Thread Settings
---
> Configure the Thread Settings on Messenger to improve the user-experience of your integration. These settings apply to each page individually.


## Greeting Text
You can set a greeting for new conversations. This can be used to communicate your bot's functionality.

![Greeting Text](https://scontent-hkg3-1.xx.fbcdn.net/t39.2365-6/13509175_122152928211838_1175374788_n.png)

> The Greeting Text is only rendered the first time the user interacts with a the Page on Messenger.

To set your Messsenger Greeting text, the easiest way is go to the 'Messaging' tab in your Page settings.

You can also configure Greeting text by go to `Giga AI\Settings`, set your Greeting Text under `Greeting Text` section and go to `https://domain.com/messenger/?giga_action=updateGreetingText`

## Get Started Button
When the Get Started button is tapped, you can send a text message or a Structured Message, containing images and buttons.

The image below shows how the Get Started button can be used to introduce your bot experience and start your user journey.

![Get Started Button](https://scontent-hkg3-1.xx.fbcdn.net/t39.2365-6/13509249_1759503700982612_770421812_n.png)

> The Get Started button and Greeting text only appears for new conversations.

### Creating Get Started Button: 

Just go to `https://domain.com/messenger/?giga_action=updateGetStartedButton`

### Handling Get Started Button:
Simply answer the GIGA_GET_STARTED_PAYLOAD postback event, like so:

```
$bot->answer('payload:GIGA_GET_STARTED_PAYLOAD', 'Hi [first_name]!, welcome to our page');
```

### Removing Get Started Button:
- Go to `Giga AI\Settings`, then set `Get Started Button Payload` section to empty.
- Open `https://domain.com/messenger/?giga_action=updateGetStartedButton`

## Persistent Menu
Documentation for persistent menu will be available soon.