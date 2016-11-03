# Dynamic Shortcodes
---
Since 2.0, Giga AI added new feature which let you show the generic template (carousel) of Posts without touching to the code but still powerful. This works perfectly with WooCommerce Product also since Products are basically Posts.
 
## Adding Dynamic Shortcode
- In your Node, click **+ Add Response**
- In the **Bot answer with** dropdown, select **Dynamic Shortcode**
- A Text box will show up allows you place the shortcode

## Usage
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

Instead of showing `post_title`, `excerpt`, `post_thumbnail`, you can tell Giga to display other field of post.

...