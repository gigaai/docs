# Says Method
---
The `says()` method is similar to `answers()` method but with only the content of the response, we can either use `says()` method or `return` in callback argument.

**Example**

```
$bot->answers('who', function () {
    $bot->says('Mike');
});
```

Which is equivalent to:
```
$bot->answers('who', function () {
    return 'Mike';
});
```