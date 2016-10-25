# Storage
---
Saving leads information and bot configurations to the database is the most common task - must have feature, and [Giga AI](/) supports it without any hassle. Let's jump in to see the awesomeness.

## Getting Leads Data
By default, when people sent you first message, their basic [information](/docs/standalone/shortcodes) are automatically saved. To get lead info, you can use `$bot->storage->get($user_id);` method. For example:

```
$bot->answer('hi', function ($bot, $user_id) {
	$user = $bot->storage->get($user_id);
	
	$first_name = $user['first_name'];

	return 'Hey ' . $first_name;
});
```

As you can see `$bot->storage->get($user_id)` returns an array of user info. If you want to get specified field, set the second parameter:

```
$bot->storage->get($user_id, $field)
```

So, to get `profile_pic`, you can use:

```
$bot->storage->get($user_id, 'profile_pic');
```

You can also set the default value when no data received by using third parameter:

```
$bot->storage->get($user_id, $field, $default);
```

## Saving Leads Data

### Multiple Fields
To saving people data, use `$bot->storage->set($lead)` method. While `$lead` is an array of lead information. For example:

```
$bot->storage->set([
	'lead_id' 		=> '1197994363555408',
	'first_name' 	=> 'Daryl',
	'last_name' 	=> 'Dixon',
	'email'			=> 'daryl@dixon.com'
]);
```

Please note that `lead_id` key is required.

**Other way**
There is another way to do it, you can set the first parameter is lead_id and second parameter is array of fields:
```
$bot->storage->set('1197994363555408', [
	'first_name' 	=> 'Daryl',
	'last_name' 	=> 'Dixon',
	'email'			=> 'daryl@dixon.com'
]);
```

> When you set a field which already exists, it overrides old field.

### Single Field
To update specified field, you can set the first parameter is the lead id, second parameter is the field name and third parameter is field value:
```
$bot->storage->set('1197994363555408', 'email', 'daryn@dixon.com');
```

## Deleting Lead
To delete lead, use `$bot->storage->delete($user_id)` method

## Searching Lead
To search lead, use `$bot->storage->search($terms)` method. Where terms is an associate array of field and value. For example:

Find people which named `Daryl`
```
$bot->storage->search([
	'first_name' => 'Daryl'
]);
```
