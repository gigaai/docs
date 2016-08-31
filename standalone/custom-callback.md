# Custom Callback
- [Custom Callback](#custom-callback)
- [Callback Arguments](#callback-arguments)
- [$bot->say()](#bot-say)
	
---
Giga also brings a fluent way to handle postback by using custom callback, this make the plugin becomes the ultimate weapon for you, for real.

<a name="custom-callback"></a>
## Custom Callback
Instead of only using supported [Message Types](message-types). You can also use custom callback function to do anything you want. For example, if people click "Get Weather" button, you'll need to handle that event and send them a message by get weather from database and send back to them. Let's see this example:

```
// When people clicked BuyNowButton. We handle it here

$bot->answer('payload:GET_WEATHER', function ($bot, $user_id) 
{
	// Free to do your jobs here. These lines below are pseudo code
	$user_location  = $bot->storage->get($user_id, 'location');
	$weather        = \Weather::ofLocation($user_location)->get();
	
	// Response user via $bot->say(); instead of $bot->answer();
	$bot->say("Your weather today is {$weather}");
});
``` 

<a name="callback-arguments"></a>
## Callback Arguments

In the above example, you can see we've used `$bot` and `$user_id` arguments. There're totally 3 arguments: `$bot`, `$user_id`, and `$input`. All of them are optional.

`$bot` is `GigaAI\MessengerBot` instance

`$user_id` is current user id

`$input` is user sent message

<a name="bot-say"></a>
## $bot->say()

In the end of custom callback, we'll need to send message to current user. Because `$bot->answer()` is used to answer incoming message, not to send message to user. So we'll use `$bot->say()` method. This method has same signature as `$bot->answer()` but doesn't take first argument (*action*) because we don't need to redefine action there. 