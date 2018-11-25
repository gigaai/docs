# Keep Method
---
Keep prompting user until the `if` condition is correct. Use with [Fluent Intended Action](/docs/api/intended-actions#fluent-syntax).

This method is a little bit similar to `says()->wait()` methods but with there are two differences:

- `$bot->says(Mixed $responses)->wait($action)` methods are used in normal intended actions because we can set the name of the handler whilst `$bot->keep(Mixed $responses)` method is used in fluent intended action because the handler is current function callback.

**Fields**
- `Mixed $responses` The responses, similar to [says()](/docs/api/method-says) method.

**Example**

*Keep sending 'Your email is not valid! Please enter again' until the email is correct*

```
$bot->answers('register', 'Please give me your email')->then(function ($bot, $lead_id, $input) {

	if ( ! filter_var($input, FILTER_VALIDATE_EMAIL)) {
		$bot->keep('Your email is not valid! Please enter again');
		return;
	}

	return 'Thanks for registering';
});
```