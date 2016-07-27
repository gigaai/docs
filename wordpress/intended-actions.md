# Intended Actions
---
One of most powerful features of Giga is intended actions. This helps you mark people message as intended action, make the conversation between Bot and People more native.

For example:

```
People:
- I want to check my flight status

Bot:
- Please give me your email
// Intended Action: get user email

People:
- john@doe.com

Bot:
// Check the status of john@doe.com and then response
- Hi John, the flight will arrive at today, 20:00
```

As you can see, after people sent their email. Bot will responses a relate request also stores their email to database for futher use. To do so, we'll chain `wait()` method after `answer()`.

Method detail:

`wait($action, $message_type)`

where

`$action`: Intended action name

`$message_type`: (Optional) Message type, if specified it won't mark next message as intended action until it's same as `$message_type`

```
$bot->answer('I want to check my flight status', 'Please give me your email')
	->wait('email', 'text'); // Wait for next text message.
```

After this step, the next **text** message of user will be marked as *email*. We'll now handle that intended action. Just use `answer()` method with `@` sign before intended action name:
```
$bot->answer('@email', function ($bot) 
{
	// Process your business here
	$bot->reply('The flight will arrive at today, 20:00');
});
```

Advanced example, wait until email is correct:
```
$bot->answer('I want to check my flight status', 'Please give me your email')
	->wait('email', 'text');

$bot->answer('@email', function ($bot, $answer)
{
	if (!filter_var($answer, FILTER_VALIDATE_EMAIL))
	{
		$bot->reply('Your email is not valid! Please enter again')
			->wait('email', 'text');

		return;
	}

	$bot->reply('The flight will arrive at today, 20:00');
});
```
