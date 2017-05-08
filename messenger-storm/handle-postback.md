# Handle Postback
---
Giga also brings a fluent way to handle postback, this make the plugin becomes the ultimate weapon for you, for real.

> Sometimes, people actions sent to server and you'll want to process them. This section show you how to do that.

## Handle Postback
Instead of only using supported [Message Types](message-types). You can also use custom callback function to do anything you want. Awesome hah?

```
// When people clicked BuyNowButton. We handle it here

$bot->answer('payload:BUY_NOW_BUTTON', function ( $bot ) {

	// You can use $wpdb or anything here
	global $wpdb;

	// Free to do your jobs here

	return 'We have processed your action!';
});
``` 

Please note that `$bot` argument in callback function is not required.