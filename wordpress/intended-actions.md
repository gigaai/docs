# Intended Actions
- [Named Intended Actions](#wait-syntax)
- [Fluent Intended Actions](#fluent-syntax)

---
One of most powerful features of Giga is *Intended Actions*. This helps you mark next message of people as a Variable, make the conversation between Bot and People more native and collect users information. This will make your bot become a Lead Generator, friendlier than traditional Forms.

For example:

```
People:
- I want to check my flight status

Bot:
- Please give me your email
// Bot set next people message as: email

People:
- john@doe.com

Bot:
// Bot now check people who has email john@doe.com and response:
- Hi John, the flight will arrive at today, 20:00
```

<a name="wait-syntax"></a>
## Named Intended Actions

As you can see, after people sent **john@doe.com** Bot knows that's an answer for **Please give me your email** question. To do so, we'll chain `wait($action)` method after `$bot->answer()`.

For example:

```
$bot->answer('I want to check my flight status', 'Please give me your email')
	->wait('email'); // Wait for next text message.
```

After this step, the next message of user will be marked as *email*. We'll now handle that intended action. Just use `answer()` method with `@` sign before intended action name:

```
$bot->answer('@email', function ($bot) {
	// Process your business here
	
	// Then response user
	return 'The flight will arrive at today, 20:00';
});
```

Advanced example, wait until email is correct:

```
$bot->answer('I want to check my flight status', 'Please give me your email')
	->wait('email');

$bot->answer('@email', function ($bot, $lead_id, $input) {
   
  	if ( ! filter_var($input, FILTER_VALIDATE_EMAIL)) {
		$bot->say('Your email is not valid! Please enter again')
			->wait('email');

		return;
	}

	$bot->say('The flight will arrive at today, 20:00');
});
```

> In the above example, we use `$bot->say()` method which same as `return` but can chain `->wait()`.

<a name="fluent-syntax"></a>
## Fluent Intended Actions

Instead of `wait()` syntax, we can chain nodes together by using fluent `then()` syntax. This makes your code shorter, prettier. The above example can be rewrite like so:

```
$bot->answer('I want to check my flight status', 'Please give me your email')->then(function ($bot, $lead_id, $input) {

	if ( ! filter_var($input, FILTER_VALIDATE_EMAIL)) {
		$bot->keep('Your email is not valid! Please enter again');
		return;
	}

	return 'The flight will arrive at today, 20:00';
});
```

We've just used a new method `$bot->keep()`, this is used to keep printing a message until the `if` condition is correct.

Of course, you can chain `then()` many times you want. For example:

```
$bot->answer('register', 'Please enter your email')->then(function ($bot, $lead_id, $input) {

	...
	
	return 'Please enter your password';
})->then(function ($bot, $lead_id, $input) {
	
	...

	return 'Thanks for registering';
});
```