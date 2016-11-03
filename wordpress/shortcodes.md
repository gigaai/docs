# Shortcodes
---

When you open Bot Buider, you'll see we use `Hi [first_name]!` message, this will response *Hi Gustavo!* if lead's name is *Gustavo*. This feature called *Shortcode*

You can use shortcode for your bot content. Of course, just add that shortcode to what string which you want. Currently, we have some shortcode available:

- [first_name]
- [last_name]
- [profile_pic]
- [locale]
- [timezone]
- [gender]

For example. If you change `Hi [first_name]!` to `Hi [first_name] [last_name]!`, Giga will response **Hi Gustavo Fring!** if lead's full name is **Gustavo Fring**

## Dynamic Shortcodes Response

Since 2.0, we've created new shortcode called `[post-generic]` which generates a posts carousel. Since WooCommerce Products are basically Posts. This feature works with WooCommerce also. See: [Dynamic Shortcodes](/docs/wordpress/dynamic-shortcodes)