# Intended Actions
- [Named Intended Actions](#wait-syntax)
- [Fluent Intended Actions](#fluent-syntax)
- [Release Intended Action](#release-intended-action)

---
One of most powerful features of Giga AI is *Intended Actions*. This helps you mark next message of people as a Variable, collect leads information and make the conversation between Bot and People more native. The Intended Actions is a core part of Conversation User Interface which sometimes, friendlier than traditional Forms.

**Example**:

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

As you can see, after people sent **john@doe.com** Bot knows that's an answer for **Please give me your email** question. To do so, we'll chain `wait($action)` method after `$bot->answers()`.

**Example**:

```
$bot->answers('I want to check my flight status', 'Please give me your email')
	->wait('email'); // Wait for next text message.
```

After this step, the next message of user will be marked as *email*. We'll now handle that intended action. Just use `answers()` method with `@` sign before intended action name:

```
$bot->answer('@email', function ($bot) {
	// Process your business here
	
	// Then response user
	return 'The flight will arrive at today, 20:00';
});
```

**Advanced example, wait until email is correct**:

```
$bot->answers('I want to check my flight status', 'Please give me your email')
	->wait('email');

$bot->answers('@email', function ($bot, $lead_id, $input) {
   
  	if ( ! filter_var($input, FILTER_VALIDATE_EMAIL)) {
		$bot->says('Your email is not valid! Please enter again')
			->wait('email');

		return;
	}

	$bot->says('The flight will arrive at today, 20:00');
});
```

> In the above example, we use `$bot->says()` method which same as `return` but since it's a method, it can chain `->wait()`.

<a name="fluent-syntax"></a>
## Fluent Intended Actions

Instead of `wait()` syntax, we can chain nodes together by using fluent `then()` syntax. This makes your code shorter, prettier. The above example can be rewrite like so:

```
$bot->answers('I want to check my flight status', 'Please give me your email')->then(function ($bot, $lead_id, $input) {

	if ( ! filter_var($input, FILTER_VALIDATE_EMAIL)) {
		$bot->keep('Your email is not valid! Please enter again');
		return;
	}

	return 'The flight will arrive at today, 20:00';
});
```

We've just used a new method `$bot->keep()`, this is used to keep printing a message until the `if` condition is correct.

> Of course, you can chain `then()` as many times as you want. 

**Example**:

```
$bot->answer('register', 'Please enter your email')->then(function ($bot, $lead_id, $input) {

	...
	
	return 'Please enter your password';
})->then(function ($bot, $lead_id, $input) {
	
	...

	return 'Thanks for registering';
});
```

In the above example, when people say *"register"*, bot will prompt *"Please enter your email"*, and then when people sent email, bot will prompt *"Please enter your password"*, and then when people sent password, bot says *"Thanks for registering"*.

<a name="release-intended-action"></a>
## Release Intended Action
What happens when you ask: *"Please enter your email"* but people don't send email, instead, they click on a persistent menu item or send another message? 

In the above example, we use `$bot->says()->wait()` or `$bot->keep()` to prompt a message to force people sending until we have correct email format. Sometimes, if people don't enter email, instead, they may click on a menu item, for example: SUBSCRIBE_PAYLOAD, you'll want to ignore current intended action and lets them subscribe your bot. To do so, we'll use `$bot->release()` method.

**Example**
```
$bot->answers('I want to check my flight status', 'Please give me your email')->then(function ($bot, $lead_id, $input) {

	if ( ! filter_var($input, FILTER_VALIDATE_EMAIL)) {
		$bot->release();
		return;
	}

	return 'The flight will arrive at today, 20:00';
});
```