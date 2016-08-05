# Custom Callback
- [Custom Callback](#custom-callback)
	- [Retrieve People Sent Message](#retrieve-people-sent-message)
	
---
Giga also brings a fluent way to handle postback by using custom callback, this make the plugin becomes the ultimate weapon for you, for real.

<a name="custom-callback"></a>
## Custom Callback
Instead of only using supported [Message Types](message-types). You can also use custom callback function to do anything you want. For example, if people click "Buy Now" button, you'll need to handle that event and send them a message wether that transaction is completed. Let's see this example:

```
// When people clicked BuyNowButton. We handle it here

$bot->answer('payload:BUY_NOW_BUTTON', function ($bot) 
{
	// Free to do your jobs here. These lines below are pseudo code
	global $db;
	$db->checkCurrentUserAccount()->createTransaction()->update();
	
	// Response user via $bot->say(); instead of $bot->answer();
	$bot->say('We have processed your action!');
});
``` 
Please note that `$bot` argument in callback function is not required.

Also, note that we use `$bot->say()` instead of `$bot->answer()` in callback function. This method has same signature as `$bot->answer()` but doesn't take first argument (*action*) because we don't need to redefine action there. 

<a name="retrieve-people-sent-message"></a>
### Retrieve People Sent Message
Sometimes, you'll want to retrieve user sent message as a variable to process your business. You can use `$bot->received_text`, please note that it will receive both your own message and people message. This example will show how to get only people sent message:

```
$bot->answer('@email', function ($bot)
{
	// This is how we get user entered text. You should set your page id in config.php
	if ($bot->sender_id != $bot->config->get('page_id'))
		$received_text = $bot->received_text;

	$bot->say("You've just entered ". $received_text);
});
```