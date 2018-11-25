# Get Location Method
---
The getLocationMethod() will takes 0 or 1 argument. Use inside function callback after retrieve location from people.

### getLocation()
Returns Coordinate Object with `lat` and `long` properties.

**Example**

```
$bot->answers('attachment:location', function ($bot) {
    $location = $bot->getLocation();

    $lat = $location->lat;

    $long = $location->long;

    return 'Your latitude is ' . $lat;
});
```

### getLocation(String $property)
Returns either latitude or longitude based on `$property` value.

**Field**
- `String $property`: Either `lat` or `long`

**Example**

```
$bot->answers('attachment:location', function ($bot) {
    return 'Your latitude is ' . $bot->getLocation('lat');
});
```