# Dynamic Shortcodes
---
Since 2.0, Giga AI added new feature which let you show the generic template (carousel) of Posts without touching to the code but still powerful. This works perfectly with WooCommerce Product also since Products are basically Posts.
 
## Adding Dynamic Shortcode
- In your Node, click **+ Add Response**
- In the **Bot answer with** dropdown, select **Dynamic Shortcode**
- A Text box will show up allows you place the shortcode

## Syntax
Basically, the shortcode usage is:

```
[post-generic]
```

It will displays `6` bubbles of latest posts in whole site, which contains 

- An image thumbnail of your post
- A post title
- Post excerpt
- A `web_url` button which let leads redirect to your post url.
 
### Binding Bubble Field

Instead of showing `post_title`, `excerpt`, `post_thumbnail`, you can tell Giga to display other fields of post. Just link the bubble parameter with both parameter, like so:

```
[post-generic title="post_title" subtitle="price" thumbnail="product_image"] 

```

In the above example, we link the title of bubble with the `post_title` field of post, we also link the subtitle of bubble and thumbnail of bubble with other post fields. If cannot found, it will look at meta key of `wp_postmeta` table.

### Adding Buttons
By default, we have a `web_url` button with View title.

....