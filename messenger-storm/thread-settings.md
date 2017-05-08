# Thread Settings
---
> This feature is deprecated. Please use [Messenger Profile](/docs/wordpress/messenger-profile) instead.

- [Greeting Text](#greeting-text)
- [Get Started Button](#get-started-button)
    - [Creating Get Started Button](#creating-get-started-button)
    - [Handling Get Started Button](#handling-get-started-button)
    - [Removing Get Started Button](#removing-get-started-button)
- [Persistent Menu](#persistent-menu)
    - [Updating Persistent Menu](#updating-persistent-menu)
    - [Removing Persistent Menu](#removing-persistent-menu)

> Configure the Thread Settings on Messenger to improve the user-experience of your integration. These settings apply to each page individually.

![Giga AI Thread Settings](https://giga.ai/images/thread-settings.png)

<a name="greeting-text"></a>
## Greeting Text
You can set a greeting for new conversations. This can be used to communicate your bot's functionality.

![Greeting Text](https://scontent-hkg3-1.xx.fbcdn.net/t39.2365-6/13509175_122152928211838_1175374788_n.png)

> The Greeting Text is only rendered the first time the user interacts with a the Page on Messenger.

To set your Messsenger Greeting text, the easiest way is go to the 'Messaging' tab in your Page settings.

You can also configure Greeting text by changing text under **Dashboard \ Giga AI \ Settings \ Thread Settings \ Greeting Text** box.

<a name="get-started-button"></a>
## Get Started Button
When the Get Started button is tapped, you can send a text message or a Structured Message, containing images and buttons.

The image below shows how the Get Started button can be used to introduce your bot experience and start your user journey.

![Get Started Button](https://scontent-hkg3-1.xx.fbcdn.net/t39.2365-6/13509249_1759503700982612_770421812_n.png)

> The Get Started button and Greeting text only appears for new conversations.

<a name="creating-get-started-button"></a>
### Creating Get Started Button: 

Get Started button is created by default as `GIGA_GET_STARTED_PAYLOAD`. You don't have to do anything.

<a name="handing-get-started-button"></a>
### Handling Get Started Button:
Simply create a node to response the `GIGA_GET_STARTED_PAYLOAD` event. By using Bot Builder or Giga API.

<a name="removing-get-started-button"></a>
### Removing Get Started Button:
Simple delete the whole text box value.

<a name="persistent-menu"></a>
## Persistent Menu
The Persistent Menu is a menu that is always available to the user. This menu should contain top-level actions that users can enact at any point. Having a persistent menu easily communicates the basic capabilities of your bot for first-time and returning users.
The menu can be invoked by a user, by tapping on the 3-caret icon on the left of the composer.

![Persistent Menu](https://scontent-hkg3-1.xx.fbcdn.net/t39.2365-6/13509228_581512925362726_878211705_n.png)

<a name="creating-persistent-menu"></a>
### Update Persistent Menu
Persistent Menu is created for you by default. You can start updating Persistent Menu right under
**Dashboard \ Giga AI \ Settings \ Thread Settings \ Persistent Menu** section.

<a name="removing-persistent-menu"></a>
### Removing Persistent Menu
Persistent Menu is great, we're not recommended to delete it. But if you want. Simply delete all menu items.
