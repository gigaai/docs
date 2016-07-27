# Custom Callback
---
Giga also brings a fluent way to handle postback by using custom callback, this make the plugin becomes the ultimate weapon for you, for real.

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