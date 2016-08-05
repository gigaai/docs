# Advanced Text Matching
- [SQL Like Syntax](#sql-like-syntax)
- [Regular Expression](#regular-expression)
- [Match with one of keywords list](#match-with-one-of-keywords-list)

---

> Giga is **case insensitive**. 

When people text you, they can enter anything which you can't expected all of them. Luckily, Giga ships with powerful text matching mechanism, you have many methods to match text.

<a name="sql-like-syntax"></a>
## SQL Like Syntax
You can also use `%` (percent) character like SQL LIKE statement to match with any characters. For example. if you set "`%buy%gun%`", then bot will auto reply if people message you: "*buy gun*", or "*buy me a gun*", or "*I want to buy gun*", etc.

Example:
```
$bot->answer('%buy%gun%', 'Guns are not good. Buy meth instead!');
```
<a name="regular-expression"></a>
## Regular Expression
You can use regular expression by using `regex:/your-regex/` syntax. For example: `regex:/^[0-9]*$/` to match with any numeric characters.

Example:
```
$bot->answer('regex:/^[0-9]*$/', 'You have just enter numeric characters!');
```
<a name="match-with-one-of-keywords-list"></a>
## Match with one of keywords list
You can use `(this|syntax)` to match with either *this* or *syntax*. For example. `(foo|bar)` will matches with either *foo* or *bar*

```
$bot->answer('(hello|hi)', 'Hi man');
```

Of course, you can combine it with all another text matching method. For example:
```
$bot->answer('(hello|hi)%', 'Hi man');
```