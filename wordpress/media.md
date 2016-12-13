#Media
- [Image](#image)
- [Audio and Video](#audio-and-video)
- [File](#file)
- [Force Detection](#force-detection)
- [Handling Incoming Attachment](#handling-incoming-attachment)
- [Location](#location)
    - [Getting Lead Location](#getting-lead-location)
    - [Saving Lead Location](#saving-lead-location)
    - [Location and Intended Actions](#location-and-intended-actions)

---

<a name="image"></a>
## Image

Let's send your image when people says: *show me your photo*, just provide your photo URL instead of text.

```
// Bot sends photo when people asked for it
$bot->answer('show me your photo', 'http://www.gstatic.com/webp/gallery/1.jpg');
```

<a name="audio-and-video"></a>
## Audio and Video

Bot can sends Audio or Video message also, just provide URLs like Image

```
// Send an audio when people say: 'show me your voice'
$bot->answer('show me your voice', 'http://www.noiseaddicts.com/samples_1w72b820/181.mp3');

// Send a video when people say: 'show me your video'
$bot->answer('show me your video', 'http://clips.vorwaerts-gmbh.de/big_buck_bunny.mp4');
```

<a name="file"></a>
## File

If you give URL for bot, which neither Image, Audio nor Video, it will send File

```
// Send File for user
$bot->answer('send me your file', 'http://www.pdf995.com/samples/pdf.pdf');
```

<a name="force-detection"></a>
## Force Detection

Sometimes, you'll want to send Image, Audio, or Video as File. And sometimes, your URL doesn't contains file extension, so you'll want to tell the bot which exactly media type to send to user. Just prepend your extension before your URL. For example:

```
// Send Image as File
$bot->answer('send me your image as file', 'file:http://www.gstatic.com/webp/gallery/1.jpg');

// Send URL which doesn't have image extension as image
$bot->answer('image', 'image:https://placeholdit.imgix.net/~text?txtsize=33&txt=350%C3%97150&w=350&h=150')
```

<a name="handling-incoming-attachment"></a>
## Handling Incoming Attachments
---
> This section show you how to handling lead sent attachment. An attachment can be an `image`, `video`, `audio`, `file` or `location`.

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

<a name="location"></a>
## Location
Giga AI supports Location on the fly. This section show you how to works with Location:

<a name="handling-location"></a>
### Handling Location
Just like normal attachment, to set action when people sent their location, use `$bot->answer('attachment:location', $answers)` method. Just like normal text message. For example:

```
$bot->answer('attachment:location', function ($bot) {
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
$bot->answer('location:', function ($bot, $user_id) {
	$location = $bot->getLocation();

	$bot->storage->set($user_id, 'location', json_encode($location));
});
```

<a name="location-and-intended-actions"></a>
### Location and Intended Actions

It's great to combine Location and Intended Actions, this example show you how to get people location to ship your pizza:

```
$bot->answer('order pizza', 'Please send us your location')->wait('location');

$bot->answer('@location', function ($bot, $user_id) {
    
    $location = $bot->getLocation();
    
    // Store it for future use
    $bot->storage->set($user_id, 'location', json_encode($location));
    
    return 'Thanks for ordering. We are processing your order and will ship to you shortly';
});
```