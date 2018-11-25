# Profile Shortcodes
- [Basic Profile Shortcodes](#basic-profile-shortcodes)
- [Target Lead](#target-lead)
- [Update Lead](#update-lead)

***

When you open Bot Buider, you'll see we use `Hi [first_name]!` message, this will response *Hi Gustavo!* if lead's name is *Gustavo*. This feature called *Shortcode*

Since 3.0, you can use shortcodes in any message types, at any position, not only text message. All profile fields can become a shortcode even leads custom meta data.

<a name="basic-profile-shortcodes"></a>
## Basic Profile Shortcodes
As mentioned above, all profile fields can become shortcode, here is the list:

- `[user_id]`
- `[first_name]`
- `[last_name]`
- `[profile_pic]`
- `[locale]`
- `[timezone]`
- `[email]`
- `[phone]`
- `[country]`
- `[location]`
- `[birthday]`
- `[linked_account]`
- `[subscribe]`
- `[...$any-meta-field]`

<a name="target-lead"></a>
## Target Lead
In order to retrieve profile field of the target lead, use `[lead]` shortcode with `id` (Page Scoped ID) and your field as parameter. For example:

```
[lead id="123112313233" email]
```

This will receive email of the given lead id.

<a name="update-lead"></a>
## Update Lead
The shortcode can also used to update lead, this is useful when you using it in the Bot Builder. To do so, set the field as parameter name as your value as parameter value.

```
[lead will_join="Kouloon, HK"]
```

This will update `will_join` field of current lead as *Kouloon, HK*.

**Note that id field won't affected**

```
[lead id="1231123113123" will_join="Bangkok, TH"]
```

This will update the `will_join` field of the lead id, it isn't update lead id.