# Dynamic Data
---
> Sometimes, you'll want to send dynamic data to people. For example, the latest products of your shop, weather of your city, the product status... Giga AI provides fluent API to simply that process. Let's dig in:

## Send a Basic Message
To send dynamic data. Simply hook into `giga_pre_seed` action, you'll have `$bot` variable, which is the instance of `MessengerBot` class, that you can use it to create nodes.

In this example, we'll send a random response to leads

```
add_action('giga_pre_seed', function ($bot) {
    
    // We'll create Nodes by using $bot->answer() method
	$bot->answer('help me pick some fruit tonight', function () {
	    $fruits = ['Orange', 'Apple', 'Banana', 'Kiwi'];
	    
	    return $fruits[array_rand($fruits)];
	});
	
});
```

Now, open **Bot Builder** and you'll see new Node has been added.

If you understand these above lines, that's awesome. Otherwise, don't be panic. Let's continue reading API documentation.