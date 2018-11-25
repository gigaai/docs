# Custom Callback
- [Custom Callback](#custom-callback)
- [Callback Arguments](#callback-arguments)
	
---
Back to the first example, instead set the second argument of `$bot->answers()` method to either `string` or `array`, we use function callback to pick a random fruit:

```
 $bot->answers('help me pick some fruit tonight', function () {
    $fruits = ['Orange', 'Apple', 'Banana', 'Kiwi'];

    return $fruits[array_rand($fruits)];
});
```

Because we can put anything to function callback, so it's really powerful and flexible. In real life application, you can fetch data from database and response, updating lead data, parsing location...

<a name="custom-callback"></a>
## Custom Callback
Instead of only using supported [Message Types](message-types). You can also use custom callback function to do anything you want. For example, if people click "Get Weather" button, you'll need to handle that event and send them a message by get weather from database and send back to them. Let's see this example:

```
// When people clicked GET_WEATHER. We handle it here

$bot->answer('payload:GET_WEATHER', function ($bot, $lead_id) {
	// Free to do your jobs here. These lines below are pseudo code
	$user_location  = $bot->storage->get($lead_id, 'location');
	$weather        = \Weather::ofLocation($user_location)->get();
	
	// Response user via return
	return "Your weather today is {$weather}";
});
``` 

<a name="callback-arguments"></a>
## Callback Arguments

In the above example, you can see we've used `$bot` and `$lead_id` arguments. There're totally 3 arguments: `$bot`, `$lead_id`, and `$input`. All of them are optional.

- `$bot` is the `GigaAI\MessengerBot` instance.
- `$lead_id` is the current user id.
- `$input` is the user sent message or clicked button.