# Handling Attachments
---
## Location
Giga AI supports Location on the fly. This section show you how to works with location:

## Handling Location
To set action when people sent their location, use `$bot->answer('location:', $answers)` method. Just like normal text message. For example:

```
$bot->answer('location:', 'Thanks for sent us your location');
```

## Getting People Location

To get people location, use custom callback with `$bot->getLocation()` method, this method returns an object of Coordinate with `lat` and `long` properties. For example:

```
$bot->answer('location:', function ($bot) {
	$location = $bot->getLocation();
	
	$lat = $location->lat;

	$long = $location->long;
});
```

To get either `lat` or `long`, you can pass the property to `$bot->getLocation()` method. For example:

```
$lat = $bot->getLocation('lat');

$long = $bot->getLocation('long');
```

### Saving People Location

### Quick Save

To saving people location, just use `$bot->storage->set()` method in the storage driver:

```
$bot->answer('location:', function ($bot, $user_id) {
	$location = $bot->getLocation();

	$bot->storage->set($user_id, 'location', $location);
});
```
