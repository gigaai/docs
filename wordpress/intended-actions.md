# Intended Actions
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
	$bot->say('The flight will arrive at today, 20:00');
});
```

Advanced example, wait until email is correct:

```
$bot->answer('I want to check my flight status', 'Please give me your email')
	->wait('email');

$bot->answer('@email', function ($bot) {

   // Get user entered text. You have to enter page id in config.php
   if ($bot->sender_id != $bot->config->get('page_id'))
      $received_text = $bot->received_text;
   
  	if ( ! filter_var($received_text, FILTER_VALIDATE_EMAIL)) {
		$bot->say('Your email is not valid! Please enter again')
			->wait('email');

		return;
	}

	$bot->say('The flight will arrive at today, 20:00');
});
```