# Giga API
---
> It's time to teach your bot now. In this section, you'll learn how to teach her with powerful Giga API.

## Start Point
In the [Setup Messenger](/docs/standalone/setup-messenger) section, you see that when we say `hi`, bot says `Hi [first_name]!`, how can she do it?

Start opening `/giga-messenger-bot/public/index.php`, you'll see this row:

```
$bot->answer('hi', 'Hi [first_name]!');
```

Now, try to change both parameter and experience it yourself.

## Sending Message

In the previous step, you've knew that in order to sending a message, we'll use `$bot->answer();` method.

Another example:
```
// My bot loves Spanish and it say hola! when people say hello
$bot->answer( 'hello', 'hola!' );
```

## Sending Media

### Image

Let's send your image when people says: *show me your photo*, just provide your photo URL instead of text.

```
// Bot sends photo when people asked for it
$bot->answer('show me your photo', 'https://foo.bar/image.jpg');
```

### Audio and Video

Bot can sends Audio or Video message also, just provide URLs like Image

```
// Send an audio when people say: 'show me your voice'
$bot->answer('show me your voice', 'https://foo.bar/voice.mp3');

// Send a video when people say: 'show me your video'
$bot->answer('show me your video', 'https://foo.bar/video.avi');
```

### File

If you give URL for bot, which neither Image, Audio nor Video, it will send File

```
// Send File for user
$bot->answer('send me your file', 'https://foo.bar/doc.pdf');
```

### Force Detection

Sometimes, you'll want to send Image, Audio, or Video as File. And sometimes, your URL doesn't include file extension, so you'll want to tell the bot which exactly media type to send to user. Just prepend your extension before your URL. For example:

```
// Send Image as File
$bot->answer('send me your image as file', 'file:http://foo.bar/image.jpg');

// Send URL which doesn't have image extension as image
$bot->answer('image', 'image:https://placeholdit.imgix.net/~text?txtsize=33&txt=350%C3%97150&w=350&h=150')
```

## Sending Structured Message

### Button

Do you remember [Message Types](message-types), it's time to quick look about it. We have to remember attributes to pass to button message.

To send buttons to people. Just pass its attributes to an array:

```
// Answer `Who are you?` question with a button
$bot->answer('Who are you?', [

    'text' => 'I am the one of those guys',

    'buttons' => [
        [
            'type' => 'web_url',
            'url' => 'http://breakingbad.com',
            'title' => 'Jesse Pinkman'
        ],
        [
            'type' => 'postback',
            'payload' => 'USER_CLICKED_HEISENBERG_BUTTON',
            'title' => 'Heisenberg'
        ]
    ]
]);
```

### Generic

Send a Generic Message is same as Button Message. You can pass their elements to an array of elements:

```
// Answer `Show me your new product` question with a button
$bot->answer('Show me your new product', [
    // A generic bubble
    [
        "title"     => "Lamborghini",
        "image_url" => "http://pictures.topspeed.com/IMG/crop/201603/2016-lamborghini-centenar-5_800x0w.jpg",
        "subtitle"  => "Amazing speed",
        "buttons"   => [
            [
                "type"  => "web_url",
                "url"   => "https://lamborghini.com",
                "title" => "Buy Now"
            ],
            [
                "type"    => "postback",
                "payload" => "BUY_LAMBORGHINI_TOMORROW",
                "title"   => "Buy Tomorrow"
            ]
        ]
    ],

    // Another generic bubble
    [
        "title"     => "Rolls Royce",
        "image_url" => "http://static.robbreport.com/sites/default/files/images/articles/2015Sep/1642581//rolls-royce-dawn-02.jpg",
        "subtitle"  => "Most Luxury Car",
        "buttons"   => [
            [
                "type"  => "web_url",
                "url"   => "https://www.rolls-roycemotorcars.com/en-GB/home.html",
                "title" => "Buy Now"
            ],
            [
                "type"    => "postback",
                "payload" => "BUY_ROLLSROYCE_TOMORROW",
                "title"   => "Buy Tomorrow"
            ]
        ]
    ],

    // Yet another generic bubble
    [
        "title"     => "Ferrari",
        "image_url" => "https://cdn1.vox-cdn.com/thumbor/-pG8Dcb_qtRf6te3ug12FHhqUDs=/1020x0/cdn0.vox-cdn.com/uploads/chorus_asset/file/4156848/Ferrari_F12tdf_3low.0.jpg",
        "subtitle"  => "I like the horse",
        "buttons"   => [
            [
                "type"  => "web_url",
                "url"   => "http://www.ferrari.com/en_en/",
                "title" => "Buy Now"
            ],
            [
                "type"    => "postback",
                "payload" => "BUY_FERRARI_TOMORROW",
                "title"   => "Buy Tomorrow"
            ]
        ]
    ]
]);
```

### Receipt

This example show you how to send receipt. Please note that receipt requires unique order number, we use `rand(0,100000)` just for demo purpose. If you set static value, it won't work.

```
$bot->answer('receipt', [
    "recipient_name" => "Stephane Crozatier",
    "order_number" => rand(0, 100000),
    "currency" => "USD",
    "payment_method" => "Visa 2345",
    "order_url" => "http://petersapparel.parseapp.com/order?order_id=123456",
    "timestamp" => "1428444852",
    "elements" => [
        [
            "title" => "Classic White T-Shirt",
            "subtitle" => "100% Soft and Luxurious Cotton",
            "quantity" => 2,
            "price" => 50,
            "currency" => "USD",
            "image_url" => "http://petersapparel.parseapp.com/img/whiteshirt.png"
        ],
        [
            "title" => "Classic Gray T-Shirt",
            "subtitle" => "100% Soft and Luxurious Cotton",
            "quantity" => 1,
            "price" => 25,
            "currency" => "USD",
            "image_url" => "http://petersapparel.parseapp.com/img/grayshirt.png"
        ]
    ],
    "address" => [
        "street_1" => "1 Hacker Way",
        "street_2" => "",
        "city" => "Menlo Park",
        "postal_code" => "94025",
        "state" => "CA",
        "country" => "US"
    ],
    "summary" => [
        "subtotal" => 75.00,
        "shipping_cost" => 4.95,
        "total_tax" => 6.19,
        "total_cost" => 56.14
    ],
    "adjustments" => [
        [
            "name" => "New Customer Discount",
            "amount" => 20
        ],
        [
            "name" => "$10 Off Coupon",
            "amount" => 10
        ]
    ]
]);
```

## Response Click Event
In above examples, we've only tried to response Text event, what about Click? 

If user click on a `web_url` button, it will automatically redirect to that URL. Otherwise, to handle Click event on payload button. Just do the same as Text but append `payload:` before

```
// When user clicked Heisenberg button which has USER_CLICKED_HEISENBERG_BUTTON payload
$bot->answer('payload:USER_CLICKED_HEISENBERG_BUTTON', 'You are Heisenberg?');
```

## Multiple Responses per Event
You can send multiple responses per event, just pass them to array instead of simple string. Of course, you can send any message types which you want:

```
$bot->answer('What does the fox says?', [
    // Send 3 texts
    'Dog goes woof',
    'Cat goes meow',
    'Bird goes tweet',

    // Also, send video
    'https://thefox.com/video.avi'
]);
```

## Multiple Nodes
You can also create multiple nodes at one time. To do so, pass an array to first parameter on `$bot->answer()` method:

```
$bot->answer([
    'payload:USER_CLICKED_HEISENBERG_BUTTON' => 'You clicked Heisenberg button',
    'default:'          => 'Default action',
    'tell me your name' => 'My name is FMB'
]);
```

## Default Answer
Of course, Bot can't answer all people questions or click events if they haven't been defined by you. To create responses for unexpected events, you can use default answer. The syntax is:

```
$bot->answer('default:', 'Sorry, bot cannot answer this question right now');
```