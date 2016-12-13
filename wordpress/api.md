# Giga API
- [Getting Started](#getting-started)
- [Sending Message](#sending-message)
- [Multiple Answers per Node](#multiple-responses)
- [Default Answer](#default-answer)
- [Multiple Nodes](#multiple-nodes)

---

> Sometimes, you'll want to send dynamic data to people. For example, the latest products of your shop, weather of your city, the product status... Giga AI provides fluent API to simply that process. Let's dig in:

<a name="getting-started"></a>
## Getting Started
To send dynamic data. Simply hook into `giga_pre_seed` action, you'll have `$bot` variable, which is the instance of `MessengerBot` class that used to create nodes.

In this example, we'll send a random text to people when they say: *"help me pick some fruit tonight"*

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

<a name="sending-message"></a>
## Sending Message

In the previous guide, you've knew that in order to response lead, we'll have to create a node by using `$bot->answer()` method.

Example:

Say *hola!* when leads say *hi*
```
$bot->answer('hi', 'hola!');
```

**Text Matching**

The [Text Matching](/docs/wordpress/text-matching) feature is works seamless with our API. 

Example:
```
$bot->answer('%buy%gun%', 'Guns are not good. Buy meth instead');
```

<a name="multiple-responses"></a>
## Multiple Answers per Node
You can send multiple responses per event, just pass them to array instead of simple string. Of course, you can send any message types which you want:

```
$bot->answer('What does the fox says?', [
    // Send 3 texts
    'Dog goes woof',
    'Cat goes meow',
    'Bird goes tweet'
]);
```

<a name="default-answer"></a>
## Default Answer
Of course, Bot can't answer all people questions or click events until you teach her. To create responses for unexpected events, you can use default answer. The syntax is:

```
$bot->answer('default:', 'Sorry, bot cannot answer this question right now');
```

<a name="multiple-nodes"></a>
## Multiple Nodes
You can also create multiple nodes at one time. To do so, pass an array to first parameter on `$bot->answer()` method:

```
$bot->answer([
    'payload:USER_CLICKED_HEISENBERG_BUTTON' => 'You clicked Heisenberg button',
    'default:'          => 'Default action',
    'tell me your name' => 'My name is FMB'
]);
```