# Advanced Text Matching
---

> Giga is **case insensitive**. 

When people text you, they can enter anything which you can't expected all of them. Luckily, Giga ships with powerful text matching mechanism, you have many methods to match text.

## SQL Like Syntax
You can also use `%` (percent) character like SQL LIKE statement to match with any characters. For example. if you set "`%buy%gun%`", then bot will auto reply if people message you: "*buy gun*", or "*buy me a gun*", or "*I want to buy gun*", etc.

Example:
```
$bot->answer('%buy%gun%', 'Guns are not good. Buy meth instead!');
```

## Regular Expression
You can use regular expression by using `regex:/your-regex/` syntax. For example: `regex:/^[0-9]*$/` to match with any numeric characters.

Example:
```
$bot->answers('regex:/^[0-9]*$/', 'You have just enter numeric characters!');
```

## Match with one of keywords list
You can use `(this|syntax)` to match with either *this* or *syntax*. For example. `(foo|bar)` will matches with either *foo* or *bar*

```
$bot->answers('(hello|hi)', 'Hi man');
```

Of course, you can combine it with all another text matching method. For example:
```
$bot->answer('(hello|hi)%', 'Hi man');
```