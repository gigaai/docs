# Subscriptions
---
By default, when a lead have first interact with your bot. It automatically saves lead information to database also set their subscription channel to `1`.

## Adding Subscribers

To add [a] lead[s] to channel[s], use `$bot->subscription->addSubscribers()` method. 

**Example**
```
$bot->answer('subscribe', function ($bot, $lead_id) {
    $bot->subscription->addSubscribers($lead_id);
});
```

### To Default Channel

To add a subscriber to channel, just set the lead id to the first argument, and the channel name to second argument of `addSubscribers()` method. By default, channel name is `1`

```
$bot->subscription->addSubscribers('1197994363555408');
```

### To Named Channel

Of course, you're free to name your channels

```
$bot->subscription->addSubscribers('1197994363555408', 'news');
```

### One To Many

You can add a subscriber to many channels, use comma separated or array syntax:

```
$bot->subscription->addSubscribers('1197994363555408', 'news,frankfurt');
```

Same as

```
$bot->subscription->addSubscribers('1197994363555408', ['news','frankfurt']);
```

### Many To Many

To set many subscribers subscribe channels, set the array for both arguments:

```
$bot->subscription->addSubscribers(['1197994363555408', '1065693993499150'], ['news','frankfurt']);
```

### Many Subscribers with Different Channels

To add many subscribers to different channels, just set a key => value pairs of subscriber and channels:

```
$bot->subscription->addSubscribers([
    '1197994363555408' => 'lawyer, nantes', 
    '1065693993499150' => 'lawyer, frankfurt'
]);
```

## Remove Leads from Channel

In order to remove leads from channel use `$bot->subscription->removeSubscribers()` method. This method has similar signature with `$bot->subscription->addSubscribers()` method.

For example:
```
$bot->subscription->removeSubscribers('1197994363555408', 'lawyer');
```

## Creating Notification

The main purpose Subscription feature is to sending push notification to leads. To do so, open your `/public/subscription.php` and start editing.

### Create a Subscription Message

In order to create a subscription message, we'll use `$bot->subscription->create()` method, this method takes 1 argument, it will create a message if it doesn't exists. 
let's see the example:

```
$bot->subscription->create([
    'content'       => 'Your message content',
    'to_channel'    => 1,
    'unique_id'     => 'a-unique-id',
    'send_limit'    => 1
]);
```

A list of available key for the message are listed below:

- `content` message content, can be any message type, like Text, Button, Generic Template...
- `to_lead` lead ids to send, string, array, or comma separated
- `to_channel` channel ids to send, string, array, or comma separated 
- `unique_id` set the unique id for the subscription.
- `send_limit` total times (not messages count) to send.
- `start_at` can send only after that date
- `end_at` can send only before that date  

### Sending a Subscription Message

After creating, we'll send a subscription message to users, just chain `->send()` method after `->create()` method

```
$bot->subscription->create([
    'content'       => 'Your message content',
    'to_channel'    => 1,
    'unique_id'     => 'a-unique-id',
    'send_limit'    => 1
])->send();
```

If you've set the unique id, you can find the subscription message and then send:

```
$bot->subscription->find('a-unique-id')->send();
```

#### Prevent Sending Multiple Times

In the above example, we use `unique_id` and `send_limit` to prevent sending same message multiple times. When you load `/public/subscription.php` file. It can only send one time. After you refresh, it will throws an error because message has already reached limit. Of course, Giga is a library which you can include in your project and you can call `$bot->subscription` anywhere you want.

You can remove `->send()` method or all code after message sent.

#### Grouping Channels

In the above example, we've sent message to channel `1`, to send to multiple channels, you can set comma separated values of channels, for example `'lawyer, frankfurt'`. 

**Sending a Message to Subscribers in either `lawyer` or `frankfurt` Channels**

```
'to_channel' => 'nantes, frankfurt'
```

This is helpful when you want to send message to all leads which live in either `nantes` or `frankfurt`

**Sending a Message to Subscribers in both `lawyer` and `frankfurt` Channels**

In order to send to all subscribers which subscribe both `lawyer` and `frankfurt` channels, we'll use array syntax. For example

```
'to_channel' => ['lawyer', 'frankfurt']
```

This is helpful when you create a job board website, and want to send messages to all users who live in `frankfurt` and look for a `lawyer` job.