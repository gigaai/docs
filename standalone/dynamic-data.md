# Dynamic Data
---
> Sometimes, you'll want to send dynamic data to people. For instance, the latest products of your shop, weather of your city, the product status... 
You'll need to fetch from database, put it to a variable but, that variable will be cached in database so it won't dynamic. To use dynamic data, you'll have to use function callback.

Let's see two examples:

Example 1:
```
$date = date('Y-m-d');

$bot->answer('what day is today?', 'Today is ' . $date);
```

In the example 1, when people ask about today, it will return the day you run the `seeder.php` because that's the date which stored in database.

Example 2:

```
$bot->answer('what day is today?', function () {
    return 'Today is ' . date('Y-m-d');
});
```

In the example 2, the callback function is return current day. Because function callback cannot be cache in db, it's return a string so it will print `Today is ...` message.