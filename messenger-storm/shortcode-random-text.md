# Random Text
---
Your bot will looks dummy when it's only can say "Hi!" when greeting people. You'll want to pick a random text, like "Hello!", "Hola!", "Howdy!" so the bot will look smarter. To do so, you can either use our API, or just using a simple but powerful shortcode.

## Adding Dynamic Shortcode
> This shortcode is one of our dynamic shortcodes. To add Dynamic shortcode, follow the steps below:
- In your Node, click **+ Add Response**
- In the **Bot answer with** dropdown, select **Dynamic Shortcode**
- A Text box will show up allows you place the shortcode

## Usage
To define a random text pool, add them between `[random-text]` and `[/random-text]`, keep each item in one line.

```
[random-text]
Hi!
Hello!
Hola!
Howdy!
[/random-text]
```

Of course, it works with profile shortcode!

```
[random-text]
Hi [first_name]!
Hello [first_name]!
Hola [first_name]!
Howdy [first_name]!
[/random-text]
```

**Did someone say it's powerful?**

A pool can be a list of string between `()` and separated by pipe. The above example can be rewrite like so:
```
[random-text]
(Hi|Hello|Hola|Howdy) [first_name]!
[/random-text]
```

You can create many pool as you want, awesome huh?
```
[random-text]
(Hi|Hello|Hola|Howdy) [first_name], have a (nice|good|great|awesome) day!
[/random-text]
```