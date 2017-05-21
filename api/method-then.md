# Then method
---
`then(Callable $callback)` method is always chaining after `$bot->answers()` method or another `then()` method to define [Fluent Intended Action](/docs/api/intended-actions#fluent-syntax).

**Field**
- `Callable $callback` the [callback closure](/docs/api/callback)

**Example**

```
$bot->answers('register', 'Please give me your email')->then(function ($bot, $lead_id, $input) {
    $bot->storage->set($lead_id, 'email', $input);

    return 'Thanks for registering';
});
```