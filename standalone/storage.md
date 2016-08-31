# Storage
---
Saving leads information and bot configurations to the database is the most common task - must have feature, and [Giga AI](/) supports it without any hassle. Let's jump in to see the awesomeness.

## Storage Driver
By default, Giga uses `file` storage driver as you can see in `config.php`, that means leads are store in flat-file and bot configurations are saving in PHP array. Giga also supports `mysql` driver and `wordpress` driver. Please check [Storage Driver](/docs/standalone/storage-driver) for configuration.

## Getting Leads Data
By default, when people sent you first message, their basic [information](/docs/standalone/shortcodes) are automatically saved (based your storage driver destination). To get lead information, you can use `$bot->storage->get($lead_id);` method. For example:

```
$bot->answer('tell me my name', function ($bot, $user_id) {
	$user = $bot->storage->get($user_id);
	
	$first_name = $user['first_name'];

	$bot->say('Hey ' . $first_name);
});
```

As you can see `$bot->storage->get($user_id)` return an array of user information. If you want to get specified field, set the second parameter:

```
$bot->storage->get($user_id, $field)
```

So, to get `first_name`, you can use:

```
$bot->storage->get($user_id, 'first_name');
```

You can also set the default value when no data received by using third parameter:

```
$bot->storage->get($user_id, $field, $default);
```

## Saving Leads Data

### Mass Field
To saving people data, use `$bot->storage->set($lead)` method. While `$lead` is an array of lead information. For example:

```
$bot->storage->set([
	'lead_id' 		=> '123456',
	'first_name' 	=> 'Daryl',
	'last_name' 	=> 'Dixon',
	'email'			=> 'daryl@dixon.com'
]);
```
Please note that `lead_id` key is required.

**Other way**
There is another way to do it, you can set the first parameter is lead id and second parameter is array of fields:
```
$bot->storage->set('123456', [
	'first_name' 	=> 'Daryl',
	'last_name' 	=> 'Dixon',
	'email'			=> 'daryl@dixon.com'
]);
```

> When you set a field which already exists, it overrides old field.

### Specified Field
To update specified field, you can set the first parameter is the lead id, second parameter is the field name and third parameter is field value:
```
$bot->storage->set('123456', 'email', 'daryn@dixon.com');
```

## Deleting Lead
To delete lead, use `$bot->storage->delete($lead_id)` method

## Searching Lead
To search lead, use `$bot->storage->search($terms)` method. Where terms is an associate array of field and value. For example:

Find people which named `Daryl`
```
$bot->storage->search([
	'first_name' => 'Daryl'
]);
```
