# Subscription & Notifications
- [Channels](#channels)
    - [Adding Channels](#adding-channels)
    - [Removing Channels](#removing-channels)
- [Adding Leads to Channels](#adding-leads-to-channels)
    - [Manually](#manually)
    - [Automatically](#automatically)
- [Removing Leads from Channels](#removing-leads-from-channels)
- [Sending Notifications](#sending-notifications)
- [Adding Routines](#adding-routines)

---
Let's say you want to send notification messages to people when they subscribed your bot. Giga provides support for sending notification to people without hassle, you can group your subscribers by channels , sending routine messages, opt-in lead to subscribe... all without coding knowledge.

<a name="channels"></a>
## Channels
Channels are similar with Lists in Mailchimp. It help you categorize your leads easier.

By default, when people interact with your bot, GigaAI will let them subscribe channel 1 automatically.

<a name="adding-channels"></a>
### Adding Channels
To add a channel, go to CRM, select any lead, in Subscription tab, you'll have a text field ... enter channel name, for example: "*buyers*".

Your lead will become a subscriber of that channel also. Please remember that a channel should have at least 1 subscriber to exists.

<a name="removing-channels"></a>
### Removing Channels
Because channel should have at least 1 member to exists, to remove a channel, just remove all leads from that channel to make channel empty. The channel will be removed from the list.

<a name="adding-leads-to-channels"></a>
## Adding Leads to Channels

<a name="manually"></a>
### Manually
To add a lead to channels, you can go to Subscription tab in Lead detail page, check or uncheck the channel checkbox to add/remove lead to/from channel.

<a name="automatically"></a>
### Automatically
Of course, you won't want to add leads to channels manually, with many leads, it's a nightmare task. In real life situation, you will want to opt-in your lead to become a subscriber. For example, when they text "subscribe" or click "subscribe" button, add them to *"buyers"* channel, and vice versa, when they text "unsubscribe" or click "unsubscribe" button, remove them from *"buyers"* channel.

To do so, you can use Bot Builder. Let's say you want to let people subscribe *"buyers"* channel when they text "subscribe".

- In **When Receive** drop-down select Text
- In *Text* content, enter `subscribe`
- Click <kbd>+ Add Action</kbd>
- In **Bot will** dropdown, select *Update Current Lead*.
- In **Command** dropdown, select *Add to Subscription Channels*
- Then select *buyers*
- Click <kbd>+ Add Action</kbd> again to create a thank you message, for example, *Thanks for becoming our subscriber"*.
- Click <kbd>Save Changes</kbd> to save your node.

<a name="removing-leads-from-channels"></a>
## Removing Leads from Channels
Removing leads from channel task is opposite with Adding Leads to Channel. Please refer to Adding leads to channel section.

<a name="sending-notifications"></a>
## Sending Notifications
Now you have subscribers well categorized in channels, it's time to send a notification message. Let's say you just want to say "hi" to all subscribers in "buyers" channel everyday. Just for demoing purpose:

- Go to **Dashboard \ Giga AI \ Notification** page, from there you have a powerful notification builder.
- In **To Channel** checkbox list, select channels which you want to send, in this case, select "buyers".
- In **With Messages** section, create message like you do in Bot Builder. You'll also have Live Preview pane which lets you see the result.
- In **Routines** dropdown, select *Once Daily*,
- In **Sending Limit**, keep `0` to send unlimited messages.
- In **Start at**, keep the value to start the routine from now, or enter a date to start the routine at your decided time.
- Do similar with **End at**
- Click <kbd>Save Changes</kbd> to save your changes.

**Question:** 
- Q: What happen when a leads subscribe many channels, and a notification sent to multiple channels which contains that lead. Did they receive duplicated message?
- A: The answer is no, they will receive only 1 message.

<a name="adding-routines"></a>
## Adding Routines
Giga use WP Cronjob to sending routine notification. By default, it has **Once Hourly**, **Twice Daily**, **Once Daily**, **Once Weekly**, **Once Monthly** routines. In case you need more  routines, please following [WP Cron Schedules](https://codex.wordpress.org/Plugin_API/Filter_Reference/cron_schedules) documentation.

