# Giga API
---
> In the previous section, we've learn how to send dynamic data by using `giga_pre_run` hook and use `$bot` instance with `$bot->answers()` method. Now we'll learn more about that class and use some more advanced usage:

## Response an Action (Create a Node)
As the previous section, we can use `$bot->answers($action, $responses)` to response an action. The first argument is the **action** and the second argument is a/some **responses**. Let's back with previous example:

```
add_action( 'giga_pre_run', function ($bot) {
	// My bot loves Spanish and it say hola! when people greeting her.
	$bot->answers( 'hello', 'hola!' );
} );
```

### Click, Default, and Welcome action
In above example, we use bot to response **Text** action. To response Click, Default and Welcome actions, we can define them by using `click:`, `default:`, and `welcome:` keyword.

Let's say *Ni hao!* to welcome people:

```
// Bot knows Chinese also
$bot->answers('welcome:', '你好!');
```

Create default action simply as:
```
$bot->answers('default:', "Hmm, to be clear. I'm just 3 days old and I'm not smart enough to understand human.");
```

## Send Image Message
We've just send Text messages in above examples. Let's try with Image, just give it a link:

```
$bot->answers('who are you?', 'http://bettercallsaul.com/saul-goodman.jpg');
```

## Send Button Message
Do you remember [Message Types](message-types), it's time to quick look about it. We have to remember attributes to pass to button message.

To send buttons to people. Just pass it to an array:
```
// Answer `Who are you?` question with a button
$bot->answers( 'Who are you?', [

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
] );
```

## Send Generic Message

Send a Generic Message is same as Button Message. You can pass it to an array:
```
// Answer `Show me your new product` question with a button
$bot->answers( 'Show me your new product', [
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
                "payload" => "BuyLamborghiniTomorrow",
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
                "payload" => "BuyRollsRoyceTomorrow",
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
                "payload" => "BuyFerrariTomorrow",
                "title"   => "Buy Tomorrow"
            ]
        ]
    ]
] );
```

## Multiple Responses per Action
You can set multiple response per action. To do so, instead of `String`, use `Array` for `$responses`
```
$bot->answers('Say My Name', [
	'Jesse Pinkman', // Response Text 1
	'http://breakingbad.dev/gustavo-fring.jpg', // Response Image 2
	'Heisenberg' // Response Text 3
]);
```

## Multiple Nodes
You can also create multiple nodes at one time. To do so, use only 1 `Array` parameter:

```
$bot->answers([
	'payload:USER_CLICKED_HEISENBERG_BUTTON' => 'You clicked Heisenberg button',
	'default:'			=> 'Default action',
	'tell me your name' => 'My name is FMB'
]);
```