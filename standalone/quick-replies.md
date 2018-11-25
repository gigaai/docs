# Quick Replies
---
Quick Replies provide a new way to present buttons to the user. Quick Replies appear prominently above the composer, with they keyboard less prominent. When a button is tapped, the message is sent in the conversation with developer-defined metadata in the callback. After a button is tapped, the buttons are dismissed preventing the issue where users could tap on buttons attached to old messages in a conversation.

Quick Replies contain text. Optionally, you can add an image.

![Quick Replies](https://scontent-hkg3-1.xx.fbcdn.net/t39.2365-6/14175277_1582251242076612_248078259_n.png)

You can also use Quick Replies let users send their location.

![Quick Replies with Location](https://scontent-hkg3-1.xx.fbcdn.net/t39.2365-6/14235551_1274248235927465_1935714581_n.png)

## Adding Quick Replies
Quick Replies work with all message types. To add quick replies, put them and your message together in an array. For example:

```
$bot->answer('I wanna buy a dress', [
	'Which dress do you want to buy?',
	'quick_replies' => [
		[
			'content_type' => 'text',
			'title'	=> 'Red',
			'payload' => 'USER_TAPPED_RED'
		],
		[
			'content_type' => 'text',
			'title'	=> 'Blue',
			'payload' => 'USER_TAPPED_BLUE'
		],
		[
			'content_type' => 'text',
			'title'	=> 'Green',
			'payload' => 'USER_TAPPED_GREEN'
		]
	]
]);
```

`content_type` is either `text` or `location`. If it's `location`, `title` and `payload` cannot be used.

`title` is text to appear

`payload` is payload postback to the webhook

`image_url` is url which sending with text



## Handling Quick Replies
There're two ways to handle Quick Replies. You can handle quick reply as normal text message or payload.

### As Normal Text
When user tap quick replies, it sends a text message to you, so just handle it like normal text message.

```
$bot->answer('Red', 'Great, red dress will ship to you soon!');
```

### As Payload Postback
It also sends a payload postback, you can handle it as payload postback if you want

```
$bot->answer('payload:USER_TAPPED_RED', 'Great, red dress will ship to you soon!');
```

