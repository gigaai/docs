# Giga API
- [Sending Text Message](#sending-message)
- [Sending Media](#sending-media)
    - [Image](#image)
    - [Audio and Video](#audio-and-video)
    - [File](#file)
    - [Force Detection](#force-detection)
- [Templates](#templates)
    - [Button Group](#button-group)
    - [Generic](#generic)
    - [List](#list)
    - [Receipt](#receipt)
- [Buttons](#buttons)
    - [Call Button](#call-button)
    - [Share Button](#share-button)
    - [Login Button](#login-button)
    - [Logout Button](#logout-button)
- [Handling Payload](#handling-payload)
- [Multiple Responses per Event](#multiple-responses)
- [Multiple Nodes](#multiple-nodes)
- [Default Answer](#default-answer)

---

> In the previous section, we've learn how to send dynamic data by using `giga_pre_seed` hook and use `$bot` instance with $bot->answer() method. Now we'll learn more about that class and use more advanced usages:


<a name="sending-message"></a>
## Sending Text Message

In the previous guide, you've knew that in order to response a message, we'll have to create a node by using `$bot->answer()` method.

Another example:
```
// My bot loves Spanish and it say hola! when people say hello
$bot->answer('hello', 'hola!');
```

<a name="sending-media"></a>
## Sending Media

<a name="image"></a>
### Image

Let's send your image when people says: *show me your photo*, just provide your photo URL instead of text.

```
// Bot sends photo when people asked for it
$bot->answer('show me your photo', 'http://www.gstatic.com/webp/gallery/1.jpg');
```

<a name="audio-and-video"></a>
### Audio and Video

Bot can sends Audio or Video message also, just provide URLs like Image

```
// Send an audio when people say: 'show me your voice'
$bot->answer('show me your voice', 'http://www.noiseaddicts.com/samples_1w72b820/181.mp3');

// Send a video when people say: 'show me your video'
$bot->answer('show me your video', 'http://clips.vorwaerts-gmbh.de/big_buck_bunny.mp4');
```

<a name="file"></a>
### File

If you give URL for bot, which neither Image, Audio nor Video, it will send File

```
// Send File for user
$bot->answer('send me your file', 'http://www.pdf995.com/samples/pdf.pdf');
```

<a name="force-detection"></a>
### Force Detection

Sometimes, you'll want to send Image, Audio, or Video as File. And sometimes, your URL doesn't contains file extension, so you'll want to tell the bot which exactly media type to send to user. Just prepend your extension before your URL. For example:

```
// Send Image as File
$bot->answer('send me your image as file', 'file:http://www.gstatic.com/webp/gallery/1.jpg');

// Send URL which doesn't have image extension as image
$bot->answer('image', 'image:https://placeholdit.imgix.net/~text?txtsize=33&txt=350%C3%97150&w=350&h=150')
```

<a name="templates"></a>
## Template

<a name="button-group"></a>
### Button Group
Button Group contains text with a set of button (maximum is 3). 

To send Button Group to people, just pass its attributes to an array:

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

In the above example, we've used [web_url](#web-url-button) and [postback](#postback-button) buttons. These buttons is not only can be used in Button Group but also can be used in other template message types.

<a name="generic"></a>
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
**Bubbles is limited to 10**

<a name="list"></a>
### List
The List Template is a template that allows you to present a set of items vertically. It can be rendered in two different ways.

The first way renders the first item with a cover image with text overlaid. This is good to making the first item appear prominently above the other items.

![List Template](https://scontent.fhan2-1.fna.fbcdn.net/t39.2365-6/14858155_1136082199802015_362293724211838976_n.png)

The second way renders each item identically and is useful for presenting a list of items where no item is shown prominently.

![List Template Compact](https://scontent.fhan2-1.fna.fbcdn.net/t39.2365-6/14850002_611227872394847_984878022932824064_n.png)

Each item may render a button which can be used as a call-to-action. You can also provide a URL to be opened when an item is tapped.

Each list template message can also have up to 1 global button which will be rendered below the item list.

**Usage**
The list template can be sent with a call to the Send API with a new template_type list.

The first item style is controlled by a new field called `top_element_style`. The value can be `large` or `compact`. To send a list view as a plain list (with no cover item), set the `top_element_style` to compact; otherwise, the first element will be rendered as the cover item and the `image_url` is required for the first element.

Each element also supports a `default_action`. Using this, you can enable people to open a URL when the row of the list item is tapped.

Please take note of the following limitations:

1. You may send at least 2 elements and at most 4 elements.
1. Adding a button to each element is optional. You may only have up to 1 button per element.
1. You may have up to 1 global button.

**Example**

A List with Cover:
```
'elements' =>  [
    [
        'title' =>  'Classic T-Shirt Collection',
        'image_url' =>  'https://peterssendreceiveapp.ngrok.io/img/collection.png',
        'subtitle' =>  'See all our colors',
        'default_action' =>  [
            'type' =>  'web_url',
            'url' =>  'https://peterssendreceiveapp.ngrok.io/shop_collection'
        ],
        'buttons' =>  [
            [
                'title' =>  'View',
                'type' =>  'web_url',
                'url' =>  'https://peterssendreceiveapp.ngrok.io/collection'
            ]
        ]
    ],
    [
        'title' =>  'Classic White T-Shirt',
        'image_url' =>  'https://peterssendreceiveapp.ngrok.io/img/white-t-shirt.png',
        'subtitle' =>  '100% Cotton, 200% Comfortable',
        'default_action' =>  [
            'type' =>  'web_url',
            'url' =>  'https://peterssendreceiveapp.ngrok.io/view?item=100',
        ],
        'buttons' =>  [
            [
                'title' =>  'Shop Now',
                'type' =>  'web_url',
                'url' =>  'https://peterssendreceiveapp.ngrok.io/shop?item=100'              
            ]
        ]
    ],
    [
        'title' =>  'Classic Blue T-Shirt',
        'image_url' =>  'https://peterssendreceiveapp.ngrok.io/img/blue-t-shirt.png',
        'subtitle' =>  '100% Cotton, 200% Comfortable',
        'default_action' =>  [
            'type' =>  'web_url',
            'url' =>  'https://peterssendreceiveapp.ngrok.io/view?item=101'
        ],
        'buttons' =>  [
            [
                'title' =>  'Shop Now',
                'type' =>  'web_url',
                'url' =>  'https://peterssendreceiveapp.ngrok.io/shop?item=101'                     
            ]
        ]                
    ],
    [
        'title' =>  'Classic Black T-Shirt',
        'image_url' =>  'https://peterssendreceiveapp.ngrok.io/img/black-t-shirt.png',
        'subtitle' =>  '100% Cotton, 200% Comfortable',
        'default_action' =>  [
            'type' =>  'web_url',
            'url' =>  'https://peterssendreceiveapp.ngrok.io/view?item=102'
        ],
        'buttons' =>  [
            [
                'title' =>  'Shop Now',
                'type' =>  'web_url',
                'url' =>  'https://peterssendreceiveapp.ngrok.io/shop?item=102'                   
            ]
        ]                
    ]
],
'buttons' =>  [
    [
        'title' =>  'View More',
        'type' =>  'postback',
        'payload' =>  'payload'
    ]
]
```

Without Cover:
```
'top_element_style' => 'compact',
'elements' =>  [
    [
        'title' =>  'Classic T-Shirt Collection',
        'image_url' =>  'https://peterssendreceiveapp.ngrok.io/img/collection.png',
        'subtitle' =>  'See all our colors',
        'default_action' =>  [
            'type' =>  'web_url',
            'url' =>  'https://peterssendreceiveapp.ngrok.io/shop_collection'
        ],
        'buttons' =>  [
            [
                'title' =>  'View',
                'type' =>  'web_url',
                'url' =>  'https://peterssendreceiveapp.ngrok.io/collection'
            ]
        ]
    ],
    [
        'title' =>  'Classic White T-Shirt',
        'image_url' =>  'https://peterssendreceiveapp.ngrok.io/img/white-t-shirt.png',
        'subtitle' =>  '100% Cotton, 200% Comfortable',
        'default_action' =>  [
            'type' =>  'web_url',
            'url' =>  'https://peterssendreceiveapp.ngrok.io/view?item=100',
        ],
        'buttons' =>  [
            [
                'title' =>  'Shop Now',
                'type' =>  'web_url',
                'url' =>  'https://peterssendreceiveapp.ngrok.io/shop?item=100'              
            ]
        ]
    ],
    [
        'title' =>  'Classic Blue T-Shirt',
        'image_url' =>  'https://peterssendreceiveapp.ngrok.io/img/blue-t-shirt.png',
        'subtitle' =>  '100% Cotton, 200% Comfortable',
        'default_action' =>  [
            'type' =>  'web_url',
            'url' =>  'https://peterssendreceiveapp.ngrok.io/view?item=101'
        ],
        'buttons' =>  [
            [
                'title' =>  'Shop Now',
                'type' =>  'web_url',
                'url' =>  'https://peterssendreceiveapp.ngrok.io/shop?item=101'                     
            ]
        ]                
    ],
    [
        'title' =>  'Classic Black T-Shirt',
        'image_url' =>  'https://peterssendreceiveapp.ngrok.io/img/black-t-shirt.png',
        'subtitle' =>  '100% Cotton, 200% Comfortable',
        'default_action' =>  [
            'type' =>  'web_url',
            'url' =>  'https://peterssendreceiveapp.ngrok.io/view?item=102'
        ],
        'buttons' =>  [
            [
                'title' =>  'Shop Now',
                'type' =>  'web_url',
                'url' =>  'https://peterssendreceiveapp.ngrok.io/shop?item=102'                   
            ]
        ]                
    ]
],
'buttons' =>  [
    [
        'title' =>  'View More',
        'type' =>  'postback',
        'payload' =>  'payload'
    ]
]
```

<a name="receipt"></a>
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

<a name="buttons"></a>
### Buttons
As above examples in Templates section, we've included buttons in Button Group, Generic, List, it works with [Persistent Menu](/docs/wordpress/thread-settings#persistent-menu) also.

<a name="web-url-button"></a>
### Web URL Button
The Web URL button can be used to redirect leads to an URL, or open an URL in the in-app browser.

To create URL button, set the button `type` to `web_url`, `url` to your URL and `title` for button title:
```
...
'buttons' => [
    [
        'type' => 'web_url',
        'url' => 'https://giga.ai',
        'title' => 'Go to Giga AI'
    ]
]
...
```

### Postback Button
Sometimes, you'll want to let leads click on the button and response instead of redirect, in that case, we'll use Postback button.

To create Postback button, set the button `type` to `postback`, `title` for button title, and `payload` to any payload name. We'll use payload name to handle. See [Handling Postback](#handling-postback) section for more detail:

```
'buttons' => [
    [
        'type' => 'postback',
        'title' => 'Bookmark Item',
        'payload' => 'DEVELOPER_DEFINED_PAYLOAD'
    ]
]
```

<a name="call-button"></a>
### Call Button
Call Button is a quick way to make a phone call. It can be used with the Button or Generic Templates.
![Call Button](https://scontent-hkg3-1.xx.fbcdn.net/t39.2365-6/14174889_175312432876430_128371202_n.png)

To create Call Button, just set type to `phone_number` and payload to the target phone number. For example:

```
...
'buttons' => [
    [
        'type'      => 'phone_number',
        'title'     => 'Call Saul Goodman',
        'payload'   => '+123456789'
    ]
]
...
```

<a name="share-button"></a>
### Share Button
Share Button enables people to share message bubbles with their contacts using a native share dialog in Messenger.
![Share Button](https://scontent-hkg3-1.xx.fbcdn.net/t39.2365-6/14235587_623632261149104_420720127_n.png)
Messages that are shared display the page name and profile pic, indicating the origin of the message. 
This attribution can be tapped, enabling friends to start their own conversations from shared content.
![Share Bubble](https://scontent-hkg3-1.xx.fbcdn.net/t39.2365-6/14130007_1097233913704658_67138787_n.png)

Notes: 
- Only individual message bubbles can be shared.
- If your message bubble has a URL Button using Messenger Extensions, Postback, Buy Button, the behavior of those buttons will change such that tapping on them will start a new thread with your bot. Share, URL (without Messenger Extensions) and Phone number buttons will behave normally.

The Share Button only works with the Generic Template. In the Send API, set the button type to `element_share`. This will generate a Share Button with title set as "Share".

```
...
'buttons' => [
    [
        'type' => 'element_share'
    ]            
]
...
```

<a name="login-button"></a>
### Log In Button
As the button name, when leads click on this button, it will open a window to let them login to your website. 

To create Log In button, just the button `type` to `account_link` and `url` to your login URL. Please note that this button doesn't have the `title` property.

```
'buttons': [
    [
        'type': 'account_link',
        'url': 'https://giga.ai/authorize'
    ]
]
```

<a name="logout-button"></a>
### Log Out Button
As the button name, when leads click on this button, it will logout your website.

To create Log Out button, just the button `type` to `account_unlink`

```
'buttons': [
    [
        'type': 'account_unlink'
    ]
]
```

<a name="handling-postback"></a>
## Handling Postback
In above examples, we've only tried to response Text event, what about Postback? 

If user click on a `web_url` button, it will automatically redirect to that URL. Otherwise, to handle Click/Tap event on payload button. Just do the same as Text but append `payload:` before

```
// When user clicked Heisenberg button which has USER_CLICKED_HEISENBERG_BUTTON payload
$bot->answer('payload:USER_CLICKED_HEISENBERG_BUTTON', 'You are Heisenberg?');
```

<a name="multiple-responses"></a>
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

<a name="multiple-nodes"></a>
## Multiple Nodes
You can also create multiple nodes at one time. To do so, pass an array to first parameter on `$bot->answer()` method:

```
$bot->answer([
    'payload:USER_CLICKED_HEISENBERG_BUTTON' => 'You clicked Heisenberg button',
    'default:'          => 'Default action',
    'tell me your name' => 'My name is FMB'
]);
```
<a name="default-answer"></a>
## Default Answer
Of course, Bot can't answer all people questions or click events if they haven't been defined by you. To create responses for unexpected events, you can use default answer. The syntax is:

```
$bot->answer('default:', 'Sorry, bot cannot answer this question right now');
```