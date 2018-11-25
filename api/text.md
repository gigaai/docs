# Sending Text

- [Basics](#basics)
- [Multiple Messages](#multiple-messages)
- [With Shortcode](#with-shortcode)

---
<a name="basics"></a>
## Basics
Back to previous example, you can see in order to response people, we can use `$bot->answers()` method. This method may takes 2 arguments, the first is the people text, the second is the bot answers.

Example:

```
// People say 'hi', bot say 'Hi Jesse!'
$bot->answers('hi', 'Hi Jesse!');
// People say 'bye' bot say 'Have an A1 day!'
$bot->answers('bye', 'Have an A1 day!');
```

Text must be UTF-8 and has maximum 640 characters.

<a name="multiple-messages"></a>
## Multiple Messages
You can send multiple lines of messages also, just set the second argument as an array. In this example, when people say *hi*, bot responses with two messages: *Hi Jesse!* and then *Can I help you?*.

```
$bot->answers('hi', [
    'Hi Jesse!',
    'Do you want to buy some meth?'
]);
```

<a name="with-shortcode"></a>
## With Shortcode
Of course, we can use with shortcode feature too:

```
$bot->answers('hi', 'Hi [first_name]!');
```