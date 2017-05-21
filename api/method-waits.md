# Waits
---
The `wait(String $action)` method is always chaining after `answers()` method or `says()` method for defining [Intended Actions](/docs/api/intended-actions).

**Fields**
- ***String $action*** *(required)*: Intended action name

**Example**

```
$bot->answers('register', 'Please give me your email')
	->wait('email');
```

**Then we can handle that intended action**

```
$bot->answers('@email', function ($bot, $lead_id, $input) {
    $bot->storage->set($lead_id, 'email', $input);

    return 'Thanks for registering';
});
```