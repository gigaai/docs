# Shortcode
---

In the previous examples, we've sent `Hi [first_name]!` message, this will response *Hi Jesse!* if lead's name is *Jesse*. This feature called *Shortcode*

You can use shortcode for your bot content. Of course, just add that shortcode to what string which you want. Currently, we have some shortcode available:

- [first_name]
- [last_name]
- [profile_pic]
- [locale]
- [timezone]
- [gender]

For example. If you change `Hi [first_name]!` to `Hi [first_name] [last_name]!`, your bot will response **Hi Jesse Pinkman!** if lead's full name is **Jesse Pinkman**