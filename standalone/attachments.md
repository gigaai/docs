# Handling Attachments
---
> This section show you how to handling people sent attachment. An attachment can be an `image`, `video`, `audio`, `file` or `location`.

## Handling Incoming Attachment
To let the bot handle the incoming attachment, use `$bot->answer('attachment:ATTACHMENT_TYPE')` method. For example:

```
$bot->answer('attachment:image', 'Thanks for sending us your image');
```

Of course, you can use callback to process the incoming attachment

```
$bot->answer('attachment:image', function ($bot, $user_id) {
    
    $attachments = $bot->getAttachments();
   
   dd($attachment);
});
```

## Location
Giga AI supports Location on the fly. This section show you how to works with Location:

### Handling Location
Just like normal attachment, to set action when people sent their location, use `$bot->answer('attachment:location', $answers)` method. Just like normal text message. For example:

```
$bot->answer('attachment:location', function ($bot) {
    $location = $bot->getLocation();
    	
    $lat = $location->lat;

    $long = $location->long;
    
    $bot->say('Your latitude is ' . $lat);
});
```

## Getting People Location

In the above example, we've used custom callback with `$bot->getLocation()` method, this method returns an object of Coordinate with `lat` and `long` properties.

To get either `lat` or `long`, you can pass the property to `$bot->getLocation()` method. For example:

```
$lat    = $bot->getLocation('lat');

$long   = $bot->getLocation('long');
```

### Saving People Location

To saving people location, just use `$bot->storage->set()` method:

```
$bot->answer('location:', function ($bot, $user_id) {
	$location = $bot->getLocation();

	$bot->storage->set($user_id, 'location', json_encode($location));
});
```
