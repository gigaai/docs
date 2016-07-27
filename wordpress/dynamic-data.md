# Dynamic Data
---
> Sometimes, you'll want to send dynamic data to people. For example, the latest products of your shop, weather of your city, the product status... GigaAI provides fluent API to simply that process. Let's dig in:

## Send a Basic Message
To send dynamic data. Simply hook into `giga_pre_run` action, you'll have `$bot` variable, which is the instance of `MessengerBot` class, that you can use it to create nodes.

In this example, we'll send `hola!` when people text `hello`. Note that we have `answers` method which we can use it to set response for each action. Open your theme `functions.php` or any file of your plugin and add this code:

```
add_action( 'giga_pre_run', function ($bot) {
	$bot->answer( 'hello', 'hola!' );
});
```
Simply huh!?

Of course, you're free to add any content which you want. Let's make it dynamic, by reply date today when peopl ask for it :
```
// When people ask 'what day is today?', response with current date:
// Response with text and with content is the current date. 
// For example: 'Today is: Wed Jun 15, 2016'
add_action( 'giga_pre_run', function ($bot) {
	$bot->answer( 'what day is today?', 'Today is:' . date('D d/m/Y') );
} );
```

Now you know you can use `giga_pre_run` and `$bot` variable to send dynamic data. Let's read more about [GigaAI API](api) to master your skills.