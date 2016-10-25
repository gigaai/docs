# Shortcodes
---

When you open `/public/seeder.php`, you'll see we use `Hi [first_name]!` message, this will print out *Hi Andrew!* if your name is *Andrew*. This feature called *Shortcode*

You can use shortcode for your bot content. Of course, just add that shortcode to what string which you want. Currently, we have some shortcode available:

- [first_name]
- [last_name]
- [profile_pic]
- [locale]
- [timezone]
- [gender]

Example:

```
// Bot send [first_name] [last_name] when people text: 'say my name'
$bot->answer('say my name', '[first_name] [last_name]')
```