# Generic Shortcode
---
Since 2.0, Giga AI added new feature which let you fetch the posts and show generic templates (carousels) of Posts without touching to the code. This works perfectly with WooCommerce Product also since Products are basically Posts.
 
## Adding Dynamic Shortcode
> This shortcode is one of our dynamic shortcodes. To add Dynamic shortcode, follow the steps below:
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
 
### Set Bubble Title
By default, the bubble title matches with your post title. In most case, you don't have to change this property. But the Giga still allows you to set the bubble title by using `title="field_name"` property. While `field_name` is the post field or post meta. For example:

**Bind a custom field named `facebook_title` to bubble title** 
```
[post-generic title="facebook_title"]
```

**Bind except field to bubble title**
```
[post-generic title="excerpt"]
```

### Set Bubble Subtitle
Like title, by default, the bubble subtitle matches with your excerpt. You can also set the subtitle by using same syntax with title `subtitle="field_name"`, while field name is the post field or post meta field. For example:

**Set bubble subtitle as WooCommerce `_regular_price`**
```
[post-generic subtitle="_regular_price"]
```

### Set Bubble Image
By default, the bubble will use your post thumbnail (featured image) as the image. In most case, you don't need to change it. Of course, you can change this property also by using `image_url="field_name"`. The field name should returns an URL. For example:

```
[post-generic image_url="product_thumbnail"]
```

### Adding Buttons
By default, we'll have a `web_url` button with "View" title which link to your post in your bubble. You can change the buttons by using `buttons="button_title, button_type, permalink"` property. If you want to add more than one button, just use `|` pipe to separate each button. For example:

**Create a 'Buy Now' button which link to your post**
```
[post-generic buttons="Buy Now, web_url, permalink"]
```

Currently, we don't support postback button, but it will available on the next update.

## Query Parameters
Dynamic shortcode can't be powerful without query parameters. If you're familiar with [WP_Query](https://codex.wordpress.org/Class_Reference/WP_Query), it takes no time to know this section. Let's digging in.

### Limit Parameter
By default, the Generic Carousel will displays up to `6` Bubbles. You can change the limit by using `limit="num_of_bubbles"` property. Maximum is `10`. For example:

```
[post-generic limit="3"]
```

### Category Parameters
In order to display product in specified category, we have more than 1 option for you. Just like `WP_Query` API.
 
**Display posts that have this category (and any children of that category), using category id:**
```
[post-generic cat="4"]
```

**Display posts that have this category (and any children of that category), using category slug:**
```
[post-generic category_name="staff"]
```

**If you need to set complex categories, go to [Query Array](#query-array) section**

### Tag Parameters
Like Category parameters, we have tag parameters for you
- `tag="tag_slugs"`
- `tag_id="tag_id"`

**Show Posts for One Tag**

Display posts that have this tag, using tag slug:
```
[post-generic tag="cooking"]
```

Display posts that have this tag, using tag id:
```
[post-generic tag_id="13"]
```

**Show Posts From Many Tags**

Display posts that have "either" of these tags:

```
[post-generic tag="bread,baking"]
```

Display posts that have "all" of these tags:
```
[post-generic tag="bread+baking+recipe"]
```

### Post Type Parameters
Post Type parameter lets you select the post to be display. For example WooCommerce Product:
```
[post-generic post_type="product"]
```


### Order Parameters
...

### Query Array
These above query properties is using `key="value"` syntax. It's easy but has a limitation, it can't pass an array so you can't do something complex. In that case, we support `query_args` property which you can put exactly same property as you do with **WP_Query** class.

Syntax:

```
[post-generic query_args="json"]
```

While JSON is your query args array which json encoded.