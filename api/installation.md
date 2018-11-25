# Welcome

- [Using API with WordPress](#wordpress)
- [Using API with Laravel](#laravel)

---
Since both [Giga Messenger](/docs/) and [Messenger Storm](/docs/messenger-storm) built on top of Giga AI framework, they are using the same API.

Using API lets you use PHP code to interact with messages and database to make your bot more smart and flexible.

## Using API
<a name="wordpress"></a>
### WordPress
If you're using [Giga Messenger](/docs/), it works with wp hook like other plugins. Just use `add_action` to hook into `giga_pre_seed` action, the function callback has `$bot` argument which is instance of `GigaAI\MessengerBot` class and let you do further.

Of course, you can put your code on any file of your project. The easiest way is put it in your active theme `functions.php`

In this example, we'll send a random text to people when they say: *"help me pick some fruit tonight"*. It will pick a random fruit from *Orange*, *Apple*, *Banana*, *Kiwi*.

```
// twentysixteen\functions.php
add_action('giga_pre_seed', function ($bot) {

    // We'll create Nodes by using $bot->answer() method
    $bot->answers('help me pick some fruit tonight', function () {
        $fruits = ['Orange', 'Apple', 'Banana', 'Kiwi'];

        return $fruits[array_rand($fruits)];
    });

});
```
> After editing code, you should open **WP Admin / Giga AI / Bot Builder** to refresh the cache.

<a name="laravel"></a>
### Laravel
If you're using [Messenger Storm](/docs/messenger-storm), the project is already ships with `routes/bot.php` so you can start writing bot in side `Route::get('dashboard/seed', fn...)`. Back with previous example, you can write exactly same code in Laravel.

```
// routes/bot.php
Route::get('dashboard/seed', function (MessengerBot $bot) {
    
    // We'll create Nodes by using $bot->answer() method
    $bot->answers('help me pick some fruit tonight', function () {
        $fruits = ['Orange', 'Apple', 'Banana', 'Kiwi'];

        return $fruits[array_rand($fruits)];
    });

    return redirect('dashboard/builder')->withMessage('Nodes seeded!');
});
```

> As you can see, when we open `dashboard/seed` URL. It basically runs the function callback which contains `MessengerBot` service provider. So actually, you can put in any file of the project, not only in `routes/bot.php`, for example, you can see we use it in `BuilderController` and `SubscriptionController`. 

**If you don't understand what `$bot->answers()` does. Don't be panic. We'll learn it in the next chapter.**