# Advanced Text Matching
- [SQL Like Syntax](#sql-like-syntax)
- [Regular Expression](#regular-expression)
- [Match with one of keywords list](#match-with-one-of-keywords-list)

---

> Giga is **case insensitive**. 

When people text you, they can enter anything which you can't expected all of them. Luckily, Giga ships with powerful text matching mechanism, you have many methods to match text.


<a name="sql-like-syntax"></a>
## SQL Like Syntax
You can also use `%` (percent) character like SQL LIKE statement to match with any characters. 

For example. 

```
%buy%gun%
```

Can match with *buy gun*, or *buy me a gun*, or *I want to buy gun*, etc.

<a name="regular-expression"></a>

## Regular Expression
Since V2, Giga AI interacts with MySQL REGEXP syntax. So you can choose either use SQL Like above or REGEXP.

For example:

```
^(nice|good|great)(.*)man$
```

This example will matches with any sentence which begins with either `nice` or `good` or `great` then with any words then ends with `man`. Like: *nice man*, *good day man*, *great done man*