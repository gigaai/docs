# Templates
- [Button Group](#button-group)
- [Generic](#generic)
- [List](#list)
- [Receipt](#receipt)

---

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

In the above example, we've used [web_url](#web-url-button) and [postback](#postback-button) buttons. These buttons are not only can be used in Button Group but also can be used in other template message types.

There're many button types, to see usage of them, go to [Buttons](/docs/wordpress/buttons) reference.

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