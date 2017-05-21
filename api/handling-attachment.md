# Handling Attachment

- [Handling Location](#handling-location)

---
Sometimes, you'll want to retrieve different content from people, not only text or postback. For example: **image**, **video**, **audio**, **file**, or **location**.

To let the bot handle the incoming attachment, use $bot->answers('attachment:{ATTACHMENT_TYPE}', ...) method. For example:

```
$bot->answers('attachment:image', 'Thanks for sending us your image');
```

The code above only detect current message is an image and send a message back, in a real life application, you'll want to retrieve the image and save to other location, you can use [Function Callback](/docs/api/callback) to do so:

```
$bot->answers('attachment:image', function ($bot) {
    $attachments = $bot->getAttachments();

    dd($attachments);
});
```

<a name="handling-location"></a>
## Handling Location
Giga AI supports Location on the fly. This section show you how to works with Location:

Just like other attachment types, to set action when people sent their location, use `$bot->answers('attachment:location', ...) method.

**Example**
```
$bot->answers('attachment:location', function ($bot) {
    $location = $bot->getLocation();

    $lat = $location->lat;

    $long = $location->long;

    return 'Your latitude is ' . $lat;
});
```

<a name="getting-lead-location"></a>
### Getting Lead Location

In the above example, we've used custom callback with `$bot->getLocation()` method, this method returns an object of Coordinate with `lat` and `long` properties.

To get either `lat` or `long`, you can pass the property to `$bot->getLocation()` method. For example:

```
$lat    = $bot->getLocation('lat');

$long   = $bot->getLocation('long');
```

<a name="saving-lead-location"></a>
### Saving Lead Location

To saving people location, just use `$bot->storage->set()` method:

```
$bot->answers('location:', function ($bot, $user_id) {
	$location = $bot->getLocation();

	$bot->storage->set($user_id, 'location', json_encode($location));
});
```

<a name="location-and-intended-actions"></a>
### Location and Intended Actions

It's great to combine Location and Intended Actions, this example show you how to get people location to ship your pizza:

```
$bot->answers('order pizza', 'Please send us your location')->wait('location');

$bot->answers('@location', function ($bot, $user_id) {
    
    $location = $bot->getLocation();
    
    // Store it for future use
    $bot->storage->set($user_id, 'location', json_encode($location));
    
    return 'Thanks for ordering. We are processing your order and will ship to you shortly';
});
```