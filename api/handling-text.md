# Handling Text

- [Text Matching](#text-matching)
    - [SQL Like Syntax](#sql-like-syntax)
    - [Regular Expression](#regular-expression)

---
All previous examples shows you how to handle simple text, in order to handle text, we use `$bot->answers()` method, the first argument is the text we want to handle.

```
$bot->answers('call jesse', 'Yo yo yo. 148-3 to the 3 to the 6 to the 9, representing the ABQ, what up, biatch?!');
```

<a name="text-matching"></a>
## Text Matching

> Giga AI is **case insensitive**. 

When lead send a text, they can enter anything which you can't expected all of them. Luckily, Giga AI ships with powerful text matching mechanism, you have many methods to match text. The Text Matching feature works with both Bot Builder and Bot API. In Bot Builder, it's located in the **When Receive** **Text** text box. In Bot API, it's first parameter in `$bot->answers()` method. 

<a name="sql-like-syntax"></a>
### SQL Like Syntax
You can also use `%` (percent) character like SQL LIKE statement to match with any characters. 

For example. 

```
$bot->answers('%buy%gun%', 'Guns are not good. Buy meth instead');
```

Can match with *buy gun*, or *buy me a gun*, or *I want to buy gun*, etc.

<a name="regular-expression"></a>

### Regular Expression
Since V2, Giga AI interacts with MySQL REGEXP syntax. So you can choose either use SQL Like above or REGEXP.

For example:

```
(nice|good|great)(.*)man
```

This example will matches with any sentence which begins with either `nice` or `good` or `great` then with any words then ends with `man`. Like: *nice man*, *good day man*, *great done man*

*Note: You don't need to add `^` and `$` for start and stop the regex*